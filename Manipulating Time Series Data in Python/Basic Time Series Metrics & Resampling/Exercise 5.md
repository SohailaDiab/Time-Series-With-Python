# Create weekly from monthly unemployment data
The civilian US unemployment rate is reported monthly. You may need more frequent data, but that's no problem because you just learned how to upsample a time series.

You'll work with the time series data for the last 20 years, and apply a few options to fill in missing values before plotting the weekly series.

## Instructions
We have already imported pandas as pd and matplotlib.pyplot as plt.

- Use pd.read_csv() to import 'unemployment.csv', creating a DateTimeIndex from the 'date' column using parse_dates and index_col, and assign the result to data.
- Convert data to weekly frequency using .asfreq() with the alias 'W' and show the first five rows.
- Convert again to weekly frequency, adding the option 'bfill' and show the first five rows.
- Create weekly series, now adding the option 'ffill', assign to weekly_ffill and show the first five rows.
- Plot weekly_ffill starting in 2015.

## Answer
```py
# Import data here
data = pd.read_csv('unemployment.csv', parse_dates=['date'], index_col='date')

# Show first five rows of weekly series
print(data.asfreq('W').head())

# Show first five rows of weekly series with bfill option
print(data.asfreq('W', method='bfill').head())

# Create weekly series with ffill option and show first five rows
weekly_ffill = data.asfreq('W', method='ffill')
print(weekly_ffill.head())

# Plot weekly_fill starting 2015 here 
weekly_ffill.loc['2015':,:].plot()
plt.show()
```

```py
>> Output:
                UNRATE
    date              
    2000-01-02     NaN
    2000-01-09     NaN
    2000-01-16     NaN
    2000-01-23     NaN
    2000-01-30     NaN
                UNRATE
    date              
    2000-01-02     4.1
    2000-01-09     4.1
    2000-01-16     4.1
    2000-01-23     4.1
    2000-01-30     4.1
                UNRATE
    date              
    2000-01-02     4.0
    2000-01-09     4.0
    2000-01-16     4.0
    2000-01-23     4.0
    2000-01-30     4.0
```
![image](https://user-images.githubusercontent.com/70928356/234702167-75f1ee40-ad8d-478c-80bf-0710f9490273.png)
