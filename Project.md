# Baby Project
## Players Data Analysis

In this notebook, we’ll explore the **players_data-2024_2025.csv** dataset.


### Loading the Dataset
We will load in all our packages and our dataset all at once in the beginning.


```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

# Loading the dataset
df = pd.read_csv('players_data-2024_2025.csv')

# Display first rows
df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Rk</th>
      <th>Player</th>
      <th>Nation</th>
      <th>Pos</th>
      <th>Squad</th>
      <th>Comp</th>
      <th>Age</th>
      <th>Born</th>
      <th>MP</th>
      <th>Starts</th>
      <th>...</th>
      <th>Att (GK)</th>
      <th>Thr</th>
      <th>Launch%</th>
      <th>AvgLen</th>
      <th>Opp</th>
      <th>Stp</th>
      <th>Stp%</th>
      <th>#OPA</th>
      <th>#OPA/90</th>
      <th>AvgDist</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>Max Aarons</td>
      <td>eng ENG</td>
      <td>DF</td>
      <td>Bournemouth</td>
      <td>eng Premier League</td>
      <td>25.0</td>
      <td>2000.0</td>
      <td>3</td>
      <td>1</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>Max Aarons</td>
      <td>eng ENG</td>
      <td>MF</td>
      <td>Valencia</td>
      <td>es La Liga</td>
      <td>25.0</td>
      <td>2000.0</td>
      <td>1</td>
      <td>0</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>Rodrigo Abajas</td>
      <td>es ESP</td>
      <td>DF</td>
      <td>Valencia</td>
      <td>es La Liga</td>
      <td>21.0</td>
      <td>2003.0</td>
      <td>1</td>
      <td>1</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>James Abankwah</td>
      <td>ie IRL</td>
      <td>DF,MF</td>
      <td>Udinese</td>
      <td>it Serie A</td>
      <td>21.0</td>
      <td>2004.0</td>
      <td>6</td>
      <td>0</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>Keyliane Abdallah</td>
      <td>fr FRA</td>
      <td>FW</td>
      <td>Marseille</td>
      <td>fr Ligue 1</td>
      <td>18.0</td>
      <td>2006.0</td>
      <td>1</td>
      <td>0</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 267 columns</p>
</div>



### Checking for Missing Data
Now we check for null values in the dataset.


```python
df.isnull().sum()
```




    Rk            0
    Player        0
    Nation        3
    Pos           0
    Squad         0
               ... 
    Stp        2514
    Stp%       2514
    #OPA       2514
    #OPA/90    2514
    AvgDist    2516
    Length: 267, dtype: int64



### Summary Statistics
We examine numeric columns.


```python
df.describe()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Rk</th>
      <th>Age</th>
      <th>Born</th>
      <th>MP</th>
      <th>Starts</th>
      <th>Min</th>
      <th>90s</th>
      <th>Gls</th>
      <th>Ast</th>
      <th>G+A</th>
      <th>...</th>
      <th>Att (GK)</th>
      <th>Thr</th>
      <th>Launch%</th>
      <th>AvgLen</th>
      <th>Opp</th>
      <th>Stp</th>
      <th>Stp%</th>
      <th>#OPA</th>
      <th>#OPA/90</th>
      <th>AvgDist</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>2698.000000</td>
      <td>2694.000000</td>
      <td>2694.000000</td>
      <td>2698.000000</td>
      <td>2698.000000</td>
      <td>2698.000000</td>
      <td>2698.000000</td>
      <td>2698.000000</td>
      <td>2698.000000</td>
      <td>2698.000000</td>
      <td>...</td>
      <td>184.000000</td>
      <td>184.000000</td>
      <td>184.000000</td>
      <td>184.00000</td>
      <td>184.000000</td>
      <td>184.000000</td>
      <td>184.000000</td>
      <td>184.000000</td>
      <td>184.000000</td>
      <td>182.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>1349.098592</td>
      <td>25.746845</td>
      <td>1998.445805</td>
      <td>13.001483</td>
      <td>9.238695</td>
      <td>829.211268</td>
      <td>9.211342</td>
      <td>1.171979</td>
      <td>0.823202</td>
      <td>1.995182</td>
      <td>...</td>
      <td>367.027174</td>
      <td>51.065217</td>
      <td>33.592391</td>
      <td>32.87337</td>
      <td>169.076087</td>
      <td>10.358696</td>
      <td>5.965217</td>
      <td>13.538043</td>
      <td>1.147065</td>
      <td>14.029670</td>
    </tr>
    <tr>
      <th>std</th>
      <td>778.573627</td>
      <td>4.395984</td>
      <td>4.398949</td>
      <td>7.671896</td>
      <td>7.728338</td>
      <td>654.392909</td>
      <td>7.270520</td>
      <td>2.300248</td>
      <td>1.389973</td>
      <td>3.238450</td>
      <td>...</td>
      <td>273.469380</td>
      <td>37.529094</td>
      <td>12.928883</td>
      <td>5.31738</td>
      <td>124.513895</td>
      <td>9.383256</td>
      <td>4.119338</td>
      <td>12.874284</td>
      <td>0.847633</td>
      <td>3.644067</td>
    </tr>
    <tr>
      <th>min</th>
      <td>1.000000</td>
      <td>16.000000</td>
      <td>1982.000000</td>
      <td>1.000000</td>
      <td>0.000000</td>
      <td>1.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>...</td>
      <td>7.000000</td>
      <td>0.000000</td>
      <td>6.500000</td>
      <td>20.80000</td>
      <td>2.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>4.700000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>675.250000</td>
      <td>22.000000</td>
      <td>1995.000000</td>
      <td>6.000000</td>
      <td>2.000000</td>
      <td>204.250000</td>
      <td>2.300000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>...</td>
      <td>109.250000</td>
      <td>15.000000</td>
      <td>24.925000</td>
      <td>29.40000</td>
      <td>54.000000</td>
      <td>3.000000</td>
      <td>3.975000</td>
      <td>3.000000</td>
      <td>0.670000</td>
      <td>12.000000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>1349.500000</td>
      <td>25.000000</td>
      <td>1999.000000</td>
      <td>14.000000</td>
      <td>8.000000</td>
      <td>725.500000</td>
      <td>8.100000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>1.000000</td>
      <td>...</td>
      <td>335.000000</td>
      <td>51.500000</td>
      <td>32.050000</td>
      <td>32.20000</td>
      <td>143.500000</td>
      <td>8.000000</td>
      <td>5.600000</td>
      <td>11.000000</td>
      <td>1.000000</td>
      <td>13.650000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>2022.750000</td>
      <td>29.000000</td>
      <td>2002.000000</td>
      <td>20.000000</td>
      <td>16.000000</td>
      <td>1386.000000</td>
      <td>15.400000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>3.000000</td>
      <td>...</td>
      <td>589.250000</td>
      <td>79.000000</td>
      <td>41.350000</td>
      <td>35.87500</td>
      <td>277.000000</td>
      <td>17.000000</td>
      <td>7.700000</td>
      <td>20.000000</td>
      <td>1.470000</td>
      <td>15.475000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>2697.000000</td>
      <td>42.000000</td>
      <td>2008.000000</td>
      <td>25.000000</td>
      <td>25.000000</td>
      <td>2250.000000</td>
      <td>25.000000</td>
      <td>23.000000</td>
      <td>14.000000</td>
      <td>37.000000</td>
      <td>...</td>
      <td>1011.000000</td>
      <td>134.000000</td>
      <td>85.700000</td>
      <td>50.90000</td>
      <td>457.000000</td>
      <td>42.000000</td>
      <td>33.300000</td>
      <td>89.000000</td>
      <td>6.130000</td>
      <td>28.000000</td>
    </tr>
  </tbody>
</table>
<p>8 rows × 222 columns</p>
</div>



### Cleaning the Duplicate Data
We drop duplicates to keep only unique rows. If there's a timestamp or date column, we can convert it to datetime as well.


```python
# Drop duplicates
df.drop_duplicates(inplace=True)

# Example: if there's a match_date column
# df['match_date'] = pd.to_datetime(df['match_date'])

df.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 2698 entries, 0 to 2697
    Columns: 267 entries, Rk to AvgDist
    dtypes: float64(106), int64(116), object(45)
    memory usage: 5.5+ MB
    

### Creating Data Visualizations
We’ll create some graphs to visually explore the players dataset.

#### Graph 1 (Top 10 Players)
This example looks at the number of times each player appears, though you can change it to sum goals, minutes, etc.


```python
top_players = df['Player'].value_counts().head(10)

plt.figure(figsize=(12,6))
top_players.plot(kind='bar', color='blue')
plt.xlabel('Player Name')
plt.ylabel('Count')
plt.title('Top 10 Players')
plt.xticks(rotation=45)
plt.show()
```


    
![png](output_11_0.png)
    


#### Graph 2 (Distribution of Minutes Played)
We can plot a histogram to see how many minutes players are getting.


```python
plt.figure(figsize=(8,5))
sns.histplot(df['Min'], kde=True, bins=20, color='green')
plt.title('Distribution of Minutes Played')
plt.xlabel('Minutes Played')
plt.ylabel('Frequency')
plt.show()
```


    
![png](output_13_0.png)
    


#### Graph 3 (Correlation Heatmap)
If you have multiple numeric columns like goals, assists, etc., a heatmap is useful.


```python

# 1. Create a pivot table (e.g., average minutes played, by player and team)
heatmap_data = pd.pivot_table(
    df,
    index='Player',         # goes on the rows
    columns='Squad',         # goes on the columns
    values='Min',     # the numeric data for coloring
    aggfunc='mean',              # or 'sum', 'count', etc.
    fill_value=0                 # fill missing values with 0 or any placeholder
)

# 2. Plot the heat map
plt.figure(figsize=(12, 8))
sns.heatmap(heatmap_data, cmap='coolwarm', annot=False)  # set annot=True to see the exact numbers
plt.title('Heatmap of Average Minutes Played (Player vs Team)')
plt.xlabel('Team')
plt.ylabel('Player Name')
plt.tight_layout()
plt.show()


```


    
![png](output_15_0.png)
    



```python

```
