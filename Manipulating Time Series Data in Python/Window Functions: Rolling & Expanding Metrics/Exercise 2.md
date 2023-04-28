# Rolling 360-day median & std. deviation for nyc ozone data since 2000
The last video also showed you how to calculate several rolling statistics using the .agg() method, similar to .groupby().

Let's take a closer look at the air quality history of NYC using the Ozone data you have seen before. The daily data are very volatile, so using a longer term rolling average can help reveal a longer term trend.

You'll be using a 360 day rolling window, and .agg() to calculate the rolling mean and standard deviation for the daily average ozone values since 2000.

## Instructions
We have already imported pandas as pd, and matplotlib.pyplot as plt.

- Use pd.read_csv() to import 'ozone.csv', creating a DateTimeIndex from the 'date' column using parse_dates and index_col, assign the result to data, and drop missing values using .dropna().
- Select the 'Ozone' column and create a .rolling() window using 360 periods, apply .agg() to calculate the mean and std, and assign this to rolling_stats.
- Use .join() to concatenate data with rolling_stats, and assign to stats.
- Plot stats using subplots.

## Answer
```py
# Import and inspect ozone data here
data = pd.read_csv('ozone.csv', parse_dates=['date'], index_col='date').dropna()

print(data.info())
print(data.head())
print()
# Calculate the rolling mean and std here
rolling_stats = data.Ozone.rolling(window=360).agg(['mean','std'])

# Join rolling_stats with ozone data
stats = data.join(rolling_stats)
print(stats.head())
# Plot stats
stats.plot(subplots=True)
plt.show()
```

```py
>> Output:
<class 'pandas.core.frame.DataFrame'>
DatetimeIndex: 6167 entries, 2000-01-01 to 2017-03-31
Data columns (total 1 columns):
 #   Column  Non-Null Count  Dtype  
---  ------  --------------  -----  
 0   Ozone   6167 non-null   float64
dtypes: float64(1)
memory usage: 96.4 KB
None
            Ozone
date             
2000-01-01  0.004
2000-01-02  0.009
2000-01-03  0.006
2000-01-04  0.009
2000-01-05  0.014

            Ozone  mean  std
date                        
2000-01-01  0.004   NaN  NaN
2000-01-02  0.009   NaN  NaN
2000-01-03  0.006   NaN  NaN
2000-01-04  0.009   NaN  NaN
2000-01-05  0.014   NaN  NaN
```


![image](https://user-images.githubusercontent.com/70928356/235015246-49c99d43-0f80-4e5f-9d57-2d095fcf65df.png)
