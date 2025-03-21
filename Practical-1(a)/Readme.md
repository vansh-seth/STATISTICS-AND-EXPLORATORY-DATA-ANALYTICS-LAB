# Practical-1

This repository contains practical work to analyze IPL matches data using Python and pandas, demonstrating skills in data manipulation, visualization, and analysis.

## Steps

### 1. Setup
- Clone the repository:
  ```bash
  !git clone https://github.com/vansh-seth/Detection-and-traking-using-yolov5.git
  ```

- Import required libraries:
  ```python
  import pandas as pd
  import matplotlib.pyplot as plt
  ```

---

### 2. Data Loading
- Load the `matches.csv` file and explore:
  ```python
  data = pd.read_csv('matches.csv')
  data.head()
  data.info()
  data.describe()
  ```

- Example operations:
  - Display specific columns:
    ```python
    data[['team1', 'team2', 'winner']]
    ```
  - Filter data by conditions:
    ```python
    data[data['city'] == 'Hyderabad']
    ```

---

### 3. Data Analysis Functions
- **Count matches in Hyderabad**:
  ```python
  def count_hyderabad(data):
      return data[data['city'] == 'Hyderabad'].shape[0]
  
  print("Count of Hyderabad:", count_hyderabad(data))
  ```

- **Count matches in a specific city after 2017**:
  ```python
  def count_matches_in_city(city_name):
      return data[(data['city'] == city_name) & (data['date'] > '2017-01-01')].shape[0]
  
  city = input("Enter the city: ")
  print(count_matches_in_city(city))
  ```

- **Count wins for a specific team**:
  ```python
  def count_wins_for_team(team_name):
      return data[data['winner'] == team_name].shape[0]
  
  print(count_wins_for_team("Mumbai Indians"))
  ```

---

### 4. Visualizations
- **Toss decision distribution**:
  ```python
  def toss_decision_pie_chart():
      data['toss_decision'].value_counts().plot(kind='pie', title='Toss Decision Distribution')
      plt.show()
  toss_decision_pie_chart()
  ```

- **Win by runs histogram**:
  ```python
  def win_by_runs():
      data['win_by_runs'].plot(kind='hist', title='Win by Runs')
      plt.show()
  win_by_runs()
  ```

---

### 5. Batsman Analysis
- Load `deliveries.csv`:
  ```python
  df = pd.read_csv('deliveries.csv')
  ```

- **Top 5 run-scorers**:
  ```python
  def top_5_runs():
      return df.groupby('batsman')['batsman_runs'].sum().sort_values(ascending=False).head(5)
  
  print(top_5_runs())
  ```

- **Most fours and sixes**:
  ```python
  def most_fours():
      return df[df['batsman_runs'] == 4].groupby('batsman')['batsman_runs'].count().sort_values(ascending=False).head(5)
  
  def most_sixs():
      return df[df['batsman_runs'] == 6].groupby('batsman')['batsman_runs'].count().sort_values(ascending=False).head(5)
  
  print(most_fours())
  print(most_sixs())
  ```
### 6. Most Dangerous Batsman
- **Most dangerous batsman by Strike rate in death over**:
  ```python
  df_filtered = df[df['over'].between(16, 20)]
  batsman_stats = df_filtered.groupby('batsman').agg(
      total_runs=('batsman_runs', 'sum'),
      balls_faced=('ball', 'count')
  )
  batsman_stats['strike_rate'] = (batsman_stats['total_runs'] / batsman_stats['balls_faced']) * 100
  most_dangerous_batsman = batsman_stats[batsman_stats['balls_faced'] > 200].sort_values(by='strike_rate', ascending=False).head(1)
  print(most_dangerous_batsman)
  ```

---

### 7. Leading Run Scorers by Season
- **Find leading run-scorers for each season**:
  ```python
  def get_leading_run_scorers(matches_file, deliveries_file):
      matches_df = pd.read_csv(matches_file)
      deliveries_df = pd.read_csv(deliveries_file)
      batsman_runs_per_match = deliveries_df.groupby(['match_id', 'batsman'])['batsman_runs'].sum().reset_index()
      batsman_with_season = batsman_runs_per_match.merge(matches_df[['id', 'season']], left_on='match_id', right_on='id')
      batsman_runs_per_season = batsman_with_season.groupby(['season', 'batsman'])['batsman_runs'].sum().reset_index()
      leading_run_scorers = batsman_runs_per_season.loc[batsman_runs_per_season.groupby('season')['batsman_runs'].idxmax()]
      return leading_run_scorers.reset_index(drop=True)
  
  leading_scorers = get_leading_run_scorers('matches.csv', 'deliveries.csv')
  print(leading_scorers)
  ```

---

## Conclusion
This project showcases how to analyze and visualize cricket data using Python, pandas, and matplotlib. It provides insights into player performance, match outcomes, and trends across seasons.
