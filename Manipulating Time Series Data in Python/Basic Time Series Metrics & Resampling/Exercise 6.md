# Use interpolation to create weekly employment data
You have recently used the civilian US unemployment rate, and converted it from monthly to weekly frequency using simple forward or backfill methods.

Compare your previous approach to the new .interpolate() method that you learned about in this video.

## Instructions
```py
We have imported pandas as pd and matplotlib.pyplot as plt for you. We have also loaded the monthly unemployment rate from 2010 to 2016 into a variable monthly.

Inspect monthly using .info().
Create a pd.date_range() with weekly dates, using the .min() and .max() of the index of monthly as start and end, respectively, and assign the result to weekly_dates.
Apply .reindex() using weekly_dates to monthly and assign the output to weekly.
Create new columns 'ffill' and 'interpolated' by applying .ffill() and .interpolate() to weekly.UNRATE.
Show a plot of weekly.
```

## Answer
```py
# Inspect data here
print(monthly.info())

# Create weekly dates
weekly_dates = pd.date_range (start=monthly.index.min(), end=monthly.index.max(), freq='W')

# Reindex monthly to weekly data 
weekly = monthly.reindex(weekly_dates)
print(weekly)
# Create ffill and interpolated columns
weekly['ffill'] = weekly.UNRATE.ffill()
weekly['interpolated'] = weekly.UNRATE.interpolate()

# Plot weekly
weekly.plot()
plt.show()
```

```py
>> Output:
    <class 'pandas.core.frame.DataFrame'>
    DatetimeIndex: 85 entries, 2010-01-01 to 2017-01-01
    Data columns (total 1 columns):
     #   Column  Non-Null Count  Dtype  
    ---  ------  --------------  -----  
     0   UNRATE  85 non-null     float64
    dtypes: float64(1)
    memory usage: 1.3 KB
    None
                UNRATE
    2010-01-03     NaN
    2010-01-10     NaN
    2010-01-17     NaN
    2010-01-24     NaN
    2010-01-31     NaN
    ...            ...
    2016-12-04     NaN
    2016-12-11     NaN
    2016-12-18     NaN
    2016-12-25     NaN
    2017-01-01     4.8
    
    [366 rows x 1 columns]
```

![image](https://user-images.githubusercontent.com/70928356/234723181-eea188ad-7169-4781-8a20-3ec41b695b60.png)
