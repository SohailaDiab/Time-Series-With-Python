# Compare weekly, monthly and annual ozone trends for NYC & LA
You have seen in the video how to downsample and aggregate time series on air quality.

First, you'll apply this new skill to ozone data for both NYC and LA since 2000 to compare the air quality trend at weekly, monthly and annual frequencies and explore how different resampling periods impact the visualization.

## Instructions
We have again imported pandas as pd and matplotlib.pyplot as plt for you.

- Use pd.read_csv() to import 'ozone.csv' and set a DateTimeIndex based on the 'date' column using parse_dates and index_col, assign the result to ozone and inspect using .info().
- Apply .resample() with weekly frequency ('W') to ozone, aggregate using .mean() and plot the result.
- Repeat with monthly ('M') and annual ('A') frequencies, plotting each result.

## Answer
```py
# Import and inspect data here
ozone = pd.read_csv('ozone.csv', parse_dates=['date'], index_col='date')
print(ozone.info())
# Calculate and plot the weekly average ozone trend
(ozone.resample('W').mean()).plot()
plt.show()

# Calculate and plot the monthly average ozone trend
(ozone.resample('M').mean()).plot()
plt.show()

# Calculate and plot the annual average ozone trend
(ozone.resample('A').mean()).plot()
plt.show()
```

```py
>> Output:
    <class 'pandas.core.frame.DataFrame'>
    DatetimeIndex: 6291 entries, 2000-01-01 to 2017-03-31
    Data columns (total 2 columns):
     #   Column       Non-Null Count  Dtype  
    ---  ------       --------------  -----  
     0   Los Angeles  5488 non-null   float64
     1   New York     6167 non-null   float64
    dtypes: float64(2)
    memory usage: 147.4 KB
```

![image](https://user-images.githubusercontent.com/70928356/234737547-3dc12b0c-003a-41ce-bd24-810f2c57c143.png)

![image](https://user-images.githubusercontent.com/70928356/234737611-b7c656ac-ac7b-4004-91b7-e41d683da994.png)

![image](https://user-images.githubusercontent.com/70928356/234737632-fc40f60c-08c6-4c75-a7ed-b2c5baec0e2b.png)
