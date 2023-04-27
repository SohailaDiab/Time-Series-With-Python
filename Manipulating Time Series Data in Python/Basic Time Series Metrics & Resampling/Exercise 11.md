# Visualize monthly mean, median and standard deviation of S&P500 returns
You have also learned how to calculate several aggregate statistics from upsampled data.

Let's use this to explore how the monthly mean, median and standard deviation of daily S&P500 returns have trended over the last 10 years.

## Instructions
As usual, we have imported pandas as pd and matplotlib.pyplot as plt for you.

- Use pd.read_csv() to import 'sp500.csv', set a DateTimeIndex based on the 'date' column using parse_dates and index_col, assign the results to sp500, and inspect using .info().
- Convert sp500 to a pd.Series() using .squeeze(), and apply .pct_change() to calculate daily_returns.
- .resample() daily_returns to month-end frequency (alias: 'M'), and apply .agg() to calculate 'mean', 'median', and 'std'. Assign the result to stats.
- .plot() stats.

## Answer
```py
# Import data here
sp500 = pd.read_csv('sp500.csv', parse_dates=['date'], index_col='date')
print(sp500.info())
print(sp500)
# Calculate daily returns here
daily_returns = sp500.squeeze().pct_change()
print(daily_returns)
# Resample and calculate statistics
stats = daily_returns.resample('M').agg(['mean', 'median', 'std'])

# Plot stats here
stats.plot()
plt.show()
```

```py
>> Output:
    <class 'pandas.core.frame.DataFrame'>
    DatetimeIndex: 2395 entries, 2007-06-29 to 2016-12-30
    Data columns (total 1 columns):
     #   Column  Non-Null Count  Dtype  
    ---  ------  --------------  -----  
     0   SP500   2395 non-null   float64
    dtypes: float64(1)
    memory usage: 37.4 KB
    None
                  SP500
    date               
    2007-06-29  1503.35
    2007-07-02  1519.43
    2007-07-03  1524.87
    2007-07-05  1525.40
    2007-07-06  1530.44
    ...             ...
    2016-12-23  2263.79
    2016-12-27  2268.88
    2016-12-28  2249.92
    2016-12-29  2249.26
    2016-12-30  2238.83
    
    [2395 rows x 1 columns]
    date
    2007-06-29          NaN
    2007-07-02    1.070e-02
    2007-07-03    3.580e-03
    2007-07-05    3.476e-04
    2007-07-06    3.304e-03
                    ...    
    2016-12-23    1.252e-03
    2016-12-27    2.248e-03
    2016-12-28   -8.357e-03
    2016-12-29   -2.933e-04
    2016-12-30   -4.637e-03
    Name: SP500, Length: 2395, dtype: float64
```

![image](https://user-images.githubusercontent.com/70928356/234743421-5cd96613-e307-4717-b3b0-a58bf838b073.png)
