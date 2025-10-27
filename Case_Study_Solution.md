Q1. Import the dataset into Python and verify that it has been imported correctly.

``` python
happy_df = pd.read_csv(r'C:\Users\shrey\Downloads\happiness_report.csv')
happy_df
```
<img width="1689" height="382" alt="image" src="https://github.com/user-attachments/assets/39ad9e3a-066f-433c-96e0-590b12e85ac0" />
<img width="1250" height="389" alt="image" src="https://github.com/user-attachments/assets/df20fe52-1e81-4950-b64e-2697368d4ea2" />

List the top 10 countries (out of 156) along with their ranking and factors affecting the rank.

Q2.Examine the key happiness factors for the countries ranked 1st and 2nd in the report.

``` python
happy_df.iloc[0:2]
```
<img width="1560" height="107" alt="image" src="https://github.com/user-attachments/assets/19a1f248-f688-4477-a2c2-4032177dfe28" />
<img width="1250" height="106" alt="image" src="https://github.com/user-attachments/assets/a24bb385-260e-45ff-b0ee-68e11c723cf5" />


Finland (Rank 1) performs better than Denmark in Score, Social Support, Freedom to make choices, and Perception of corruption. Denmark, however, leads in GDP per Capita, Healthy Life Expectancy, and Generosity.

Q3. Retrieve and review the overall structure and summary information of the dataset.

``` python
happy_df.info()
```
<img width="726" height="488" alt="image" src="https://github.com/user-attachments/assets/d0edc55c-9d78-4c6e-853c-020b894ebd2e" />



Displays the data types and total number of non-null values for each column.

Q4. Identify and handle any null or missing values in the dataset columns.

``` python
happy_df.isnull().sum()
```
<img width="438" height="351" alt="image" src="https://github.com/user-attachments/assets/2ff29dff-b7b7-497d-9e3d-c3e788a69215" />


No null values were found in the dataframe.

Q5. Compute summary statistics for each numeric column.

``` python
happy_df.describe()
```
<img width="1689" height="320" alt="image" src="https://github.com/user-attachments/assets/bfe8e6bf-ee42-48b7-bc40-8c841f656a2f" />
<img width="935" height="316" alt="image" src="https://github.com/user-attachments/assets/22e183f0-f556-4ab3-9eab-0237071be02f" />


Provides statistical insights like count, mean, standard deviation, minimum, maximum, and quartiles for all numeric columns.

Q6. Detect and remove duplicate records.

``` python
happy_df.duplicated().sum()
```
<img width="188" height="72" alt="image" src="https://github.com/user-attachments/assets/47fe56a7-e0eb-4e9f-87a8-38d056e901c5" />


No duplicate records were found.

Q7. Identify the perception of corruption for the country with the highest happiness score.

``` python
happy_df.loc[happy_df['Score']== happy_df['Score'].max()]
```
<img width="1691" height="75" alt="image" src="https://github.com/user-attachments/assets/f5e17ecd-98f6-4a00-b71d-b7dc976c9ac9" />
<img width="1247" height="73" alt="image" src="https://github.com/user-attachments/assets/55ebd817-06e6-41b6-8807-f0725edf6868" />


The top-ranked country is Finland, with a perception of corruption score of 0.393.

📊 Visualization Tasks

Q8. Display the top 10 happiest countries based on the Happiness Score.

``` python
happy_df.set_index('Country or region')['Score'].head(10).plot(kind='bar')
plt.title('Top 10 Happiest Countries')
plt.xlabel('Countries')
plt.ylabel('Happiness Score')
```
<img width="398" height="382" alt="image" src="https://github.com/user-attachments/assets/51cf6700-69a8-402b-b3bd-3ccfa29ed439" />


The bar chart shows the Happiness Scores of the top 10 countries.

Q9. Visualize the distribution of Happiness Scores across all countries.

``` python
happy_df['Score'].plot(kind='hist')
plt.show()
plt.title("Happiness Score Distribution")
plt.xlabel("Happiness Score")
```
<img width="883" height="711" alt="image" src="https://github.com/user-attachments/assets/fc16d099-d494-4cb0-8f8c-ffa8695821b3" />


Highest frequency: Score 4.5 = 32 and 6.5 = 27.
Lowest frequency: Score 3 = 5.

Q10. Compare the average Happiness Score and average GDP per capita across all countries.

``` python
happy_df[['Score', 'GDP per capita']].mean().plot(kind='bar')
plt.title('Comparison of Average Score and GDP per capita')
plt.xlabel('Parameters')
plt.ylabel('Average Value')
plt.show()
```
<img width="866" height="853" alt="image" src="https://github.com/user-attachments/assets/a0822160-c6d8-4434-a554-7e5f4a991862" />


Average Score = 5.5, Average GDP per Capita = 0.9.
Average score is much higher compared to GDP per capita.

Q11. Visualize the relationship between GDP per capita and Happiness Score.

``` python
happy_df.plot.scatter(x='GDP per capita', y='Score')
plt.title('GDP vs Happiness Score')
```
<img width="881" height="711" alt="image" src="https://github.com/user-attachments/assets/af634162-b291-40b9-ace3-78d9ca36eeb9" />

The scatter plot shows a clear positive correlation between GDP per capita and happiness. Wealthier countries tend to report higher happiness scores, though some nations achieve good happiness even with moderate GDP. This suggests that while income boosts well-being, factors like social support and freedom also play key roles.


Q12. Create a line or bar chart to observe how Healthy Life Expectancy changes from the happiest to the least happy countries.

``` python
happy_df.plot(kind='line', x='Overall rank', y='Healthy life expectancy', marker='o')
plt.title("Life Expectancy in Different Countries")
plt.xlabel("Countries Rank")
plt.ylabel("Life Expectancy Measure")
```
<img width="889" height="711" alt="image" src="https://github.com/user-attachments/assets/1782c91e-2671-4fb9-a572-99d75ada571a" />



An inverse relationship is observed—life expectancy decreases as country rank increases.

Q13. Examine the spread and variability of Happiness Scores using a box plot.

``` python
happy_df.plot(kind='box', y='Score')
plt.show()
plt.title('Box plot of Happiness Score')
plt.ylabel('Measures')
```
<img width="866" height="680" alt="image" src="https://github.com/user-attachments/assets/c1f6d456-3a28-4603-af33-c516c8d35db7" />


The box plot summarizes the distribution of Happiness Scores across 156 countries:

Minimum: ~2.9

Q1: ~4.5

Median: ~5.4

Q3: ~6.2

Maximum: ~7.9

Outliers: None

🧩 Interpretation:
Most countries have moderate happiness levels between 4.5 and 6.2.
The median score of 5.4 indicates a balanced global distribution.
Scores range from 2.9 to 7.9, showing moderate variation.
No extreme outliers indicate consistent global happiness trends.
