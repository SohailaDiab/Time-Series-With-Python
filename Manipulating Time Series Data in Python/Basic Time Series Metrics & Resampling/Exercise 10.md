# Compare quarterly GDP growth rate and stock returns
With your new skill to downsample and aggregate time series, you can compare higher-frequency stock price series to lower-frequency economic time series.

As a first example, let's compare the quarterly GDP growth rate to the quarterly rate of return on the (resampled) Dow Jones Industrial index of 30 large US stocks.

GDP growth is reported at the beginning of each quarter for the previous quarter. To calculate matching stock returns, you'll resample the stock index to quarter start frequency using the alias 'QS', and aggregating using the .first() observations.

## Instructions
As usual, we have imported pandas as pd and matplotlib.pyplot as plt for you.

- Use pd.read_csv() to import 'gdp_growth.csv' and 'djia.csv', for both set a DateTimeIndex based on the 'date' column using parse_dates and index_col, and assign the results to gdp_growth and djia respectively, then inspect using .info().
- Resample djia using frequency alias 'QS', aggregate using .first(), and assign to djia_quarterly.
- Apply .pct_change() to djia_quarterly and .mul() by 100 to obtain djia_quarterly_return.
- Use pd.concat() to concatenate gdp_growth and djia_quarterly_return along axis=1, and assign to data. Rename the columns using .columns and the new labels 'gdp' and 'djia', then .plot() the results.

## Answer
```py
# Import and inspect gdp_growth here
gdp_growth = pd.read_csv('gdp_growth.csv', parse_dates=['date'], index_col='date')
gdp_growth.info()

# Import and inspect djia here
djia = pd.read_csv('djia.csv', parse_dates=['date'], index_col='date')
djia.info()

# Calculate djia quarterly returns here 
djia_quarterly = djia.resample('QS').first()
djia_quarterly_return = djia_quarterly.pct_change().mul(100)

# Concatenate, rename and plot djia_quarterly_return and gdp_growth here 
data = pd.concat([gdp_growth, djia_quarterly_return], axis=1)
data.columns = ['gdp', 'djia']

data.plot()
plt.show()
```
```py
>> Output:
    <class 'pandas.core.frame.DataFrame'>
    DatetimeIndex: 41 entries, 2007-01-01 to 2017-01-01
    Data columns (total 1 columns):
     #   Column      Non-Null Count  Dtype  
    ---  ------      --------------  -----  
     0   gdp_growth  41 non-null     float64
    dtypes: float64(1)
    memory usage: 656.0 bytes
    <class 'pandas.core.frame.DataFrame'>
    DatetimeIndex: 2610 entries, 2007-06-29 to 2017-06-29
    Data columns (total 1 columns):
     #   Column  Non-Null Count  Dtype  
    ---  ------  --------------  -----  
     0   djia    2519 non-null   float64
    dtypes: float64(1)
    memory usage: 40.8 KB
```

![image](https://user-images.githubusercontent.com/70928356/234742426-424349e6-e27e-4c28-8080-aac9db2312b2.png)
