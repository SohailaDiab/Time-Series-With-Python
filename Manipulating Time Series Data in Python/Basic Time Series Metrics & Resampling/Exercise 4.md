# Convert monthly to weekly data
You have learned in the video how to use .reindex() to conform an existing time series to a DateTimeIndex at a different frequency.

Let's practice this method by creating monthly data and then converting this data to weekly frequency while applying various fill logic options.

## Instructions
We have already imported pandas as pd for you. We have also defined start and end dates.

- Create monthly_dates using pd.date_range with start, end and frequency alias 'M'.
- Create and print the pd.Series monthly, passing the list [1, 2] as the data argument, and using monthly_dates as index.
- Create weekly_dates using pd.date_range with start, end and frequency alias 'W'.
- Apply .reindex() to monthly three times: first without additional options, then with bfill and then with ffill, print()-ing each result.

## Answer
```py
# Set start and end dates
start = '2016-1-1'
end = '2016-2-29'

# Create monthly_dates here
monthly_dates = pd.date_range(start=start, end=end, freq='M')
 
# Create and print monthly here
monthly = pd.Series(data=[1,2], index=monthly_dates)
print(monthly)
print()
# Create weekly_dates here
weekly_dates = pd.date_range(start=start, end=end, freq='W')

# Print monthly, reindexed using weekly_dates
print(monthly.reindex(weekly_dates))
print(monthly.reindex(weekly_dates, method='bfill'))
print(monthly.reindex(weekly_dates,  method='ffill'))
```

```py
>> Output:

2016-01-31    1
2016-02-29    2
Freq: M, dtype: int64

2016-01-03    NaN
2016-01-10    NaN
2016-01-17    NaN
2016-01-24    NaN
2016-01-31    1.0
2016-02-07    NaN
2016-02-14    NaN
2016-02-21    NaN
2016-02-28    NaN
Freq: W-SUN, dtype: float64
2016-01-03    1
2016-01-10    1
2016-01-17    1
2016-01-24    1
2016-01-31    1
2016-02-07    2
2016-02-14    2
2016-02-21    2
2016-02-28    2
Freq: W-SUN, dtype: int64
2016-01-03    NaN
2016-01-10    NaN
2016-01-17    NaN
2016-01-24    NaN
2016-01-31    1.0
2016-02-07    1.0
2016-02-14    1.0
2016-02-21    1.0
2016-02-28    1.0
Freq: W-SUN, dtype: float64
```
