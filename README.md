# IPL-Analysis

This project aims to analyze Indian Premier League (IPL) data from 2008-2023 to derive insights on team performances, player statistics, and overall game trends. We will use Python with libraries like Pandas, Seaborn, Numpy, and Matplotlib to clean, merge, and visualize the datasets.


#### Libraries used
```
- pandas: For data manipulation and analysis.
- seaborn: For statistical data visualization.
- numpy: For numerical operations.
- matplotlib: For creating static, animated, and interactive visualizations.
```

#### Data Sets
The dataset consists of two seperate CSV files: matches and deliveries.
These files contain the information of each match summary and ball by ball details, respectively.
<br>
<a href="https://kaggle.com/datasets/patrickb1912/ipl-complete-dataset-20082020">Kaggle Dataset</a>

<br>


Below are the key techniques and methods used:

#### Data Cleaning
<b>Handling Missing Values</b>:
    - Filling missing values with appropriate placeholders (e.g., 'None', 'Unknown', 0).
    - Dropping rows with missing values in certain columns (e.g., `player_of_match`, `winner`).

#### Data Transformation
<b>Renaming Columns</b>:
    - Renaming columns for better clarity and to facilitate merging (e.g., renaming 'id' to 'match_id').

<b>Merging Datasets</b>:
    - Combining two datasets (`deliveries` and `matches`) using an inner join on a common column (`match_id`).

#### Aggregation and Grouping
<b>Grouping Data</b>:
    - Grouping data by certain columns to calculate aggregates (e.g., total runs by batsmen, total wickets by bowlers, total matches played by teams).

<b>Calculating Aggregates</b>:
    - Calculating sums, counts, and other aggregations to derive meaningful statistics (e.g., total runs, total wickets, number of matches won, and winning percentages).

#### Data Analysis
<b>Calculating Winning Percentages</b>:
    - Deriving winning percentages by dividing the number of matches won by the total number of matches played and then multiplying by 100.

<b>Identifying Top Performers</b>:
    - Sorting and filtering data to identify top performers (e.g., top 10 batsmen by total runs, top 10 bowlers by total wickets, players who scored 100 runs in a match).

#### Data Visualization
<b>Bar Plots</b>:
    - Creating bar plots to visualize aggregated data, such as team winning percentages, top batsmen by total runs, and top bowlers by total wickets.
    <br>
    <img width="500" alt="image" src="https://github.com/p-diya/IPL-Analysis/assets/61963099/effbbeb4-4b7b-461b-a73c-ab9c5dcf0794">


<b>Scatter Plots</b>:
    - Plotting scatter plots to visualize relationships between two numerical variables (e.g., runs scored vs. balls faced for top batsmen).

<b>Heat Maps</b>:
    - Creating heat maps to visualize the correlation matrix of numerical features.
    <img width="500" alt="image" src="https://github.com/p-diya/IPL-Analysis/assets/61963099/5dbb9f21-a913-4f12-9c87-af31eceaf350">

#### Statistical and Exploratory Analysis
<b>Correlation Analysis</b>:
    - Using a heat map to analyze and visualize the correlation between numerical features, helping to understand the relationships between different variables.

#### Example Code Snippets for Each Technique

##### Handling Missing Values
```python
deliveries['extras_type'].fillna('None', inplace=True)
matches['city'].fillna('Unknown', inplace=True)
```

##### Renaming Columns
```python
matches.rename(columns={'id': 'match_id'}, inplace=True)
```

##### Merging Datasets
```python
merged_data = pd.merge(deliveries, matches, how='inner', on='match_id')
```

##### Grouping Data
```python
team_matches_played = merged_data.groupby('team1')['match_id'].nunique() + merged_data.groupby('team2')['match_id'].nunique()
```

##### Calculating Aggregates
```python
team_wins = merged_data.groupby('winner')['match_id'].nunique()
```

##### Bar Plot Visualization
```python
plt.figure(figsize=(12, 8))
team_win_percentage.plot(kind='bar', color='skyblue')
plt.title('Team Winning Percentage')
plt.xlabel('Teams')
plt.ylabel('Winning Percentage')
plt.xticks(rotation=90)
plt.grid(axis='y', linestyle='--', alpha=0.7)
plt.show()
```
<img width="500" alt="image" src="https://github.com/p-diya/IPL-Analysis/assets/61963099/4e63209f-8367-4288-9f23-36e0ddf595b8">

#### Scatter Plot Visualization
```python
plt.figure(figsize=(12, 8))
plt.scatter(batsman_runs_balls['ball'], batsman_runs_balls['batsman_runs'], color='purple')
plt.title('Runs vs Balls Faced for Top Batsmen')
plt.xlabel('Balls Faced')
plt.ylabel('Runs Scored')
plt.grid(True)
plt.show
```
<img width="500" alt="image" src="https://github.com/p-diya/IPL-Analysis/assets/61963099/598c5e82-315b-4f4b-92d5-49cfbfd56995">
