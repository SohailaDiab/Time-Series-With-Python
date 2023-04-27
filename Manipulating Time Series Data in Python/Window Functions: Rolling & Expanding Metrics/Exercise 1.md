# Rolling average air quality since 2010 for new york city
The last video was about rolling window functions. To practice this new tool, you'll start with air quality trends for New York City since 2010. In particular, you'll be using the daily Ozone concentration levels provided by the Environmental Protection Agency to calculate & plot the 90 and 360 day rolling average.

## Instructions
We have already imported pandas as pd and matplotlib.pyplot as plt.

- Use pd.read_csv() to import 'ozone.csv', creating a DateTimeIndex from the 'date' column using parse_dates and index_col, and assign the result to data.
- Add the columns '90D' and '360D' containing the 90 and 360 rolling calendar day .mean() for the column 'Ozone'.
- Plot data starting 2010, setting 'New York City' as title.

## Answer
```py
# Import and inspect ozone data here
data = pd.read_csv('ozone.csv', parse_dates=['date'], index_col='date')
print(data.info())
print()
print(data.head())
print()
# Calculate 90d and 360d rolling mean for the last price
data['90D'] = data.Ozone.rolling(window='90D').mean()
data['360D'] = data.Ozone.rolling(window='360D').mean()
print(data.info())
# Plot data
data.loc['2010':].plot()
plt.title('New York City')
plt.show()
```

```py
>> Output:
    <class 'pandas.core.frame.DataFrame'>
    DatetimeIndex: 6291 entries, 2000-01-01 to 2017-03-31
    Data columns (total 1 columns):
     #   Column  Non-Null Count  Dtype  
    ---  ------  --------------  -----  
     0   Ozone   6167 non-null   float64
    dtypes: float64(1)
    memory usage: 98.3 KB
    None
    
                Ozone
    date             
    2000-01-01  0.004
    2000-01-02  0.009
    2000-01-03  0.006
    2000-01-04  0.009
    2000-01-05  0.014
    
    <class 'pandas.core.frame.DataFrame'>
    DatetimeIndex: 6291 entries, 2000-01-01 to 2017-03-31
    Data columns (total 3 columns):
     #   Column  Non-Null Count  Dtype  
    ---  ------  --------------  -----  
     0   Ozone   6167 non-null   float64
     1   90D     6291 non-null   float64
     2   360D    6291 non-null   float64
    dtypes: float64(3)
    memory usage: 196.6 KB
```

![image](https://user-images.githubusercontent.com/70928356/235014372-5284f60e-89f9-419f-954f-3b283a52c64f.png)
