# Rolling quantiles for daily air quality in nyc
You learned in the last video how to calculate rolling quantiles to describe changes in the dispersion of a time series over time in a way that is less sensitive to outliers than using the mean and standard deviation.

Let's calculate rolling quantiles - at 10%, 50% (median) and 90% - of the distribution of daily average ozone concentration in NYC using a 360-day rolling window.

## Instructions
We have already imported pandas as pd and matplotlib.pyplot as plt. We have also loaded the ozone data from 2000-2017 into the variable data.

- Apply .resample() with daily frequency 'D' to data and apply .interpolate() to fill missing values, and reassign to data.
- Inspect the result using .info().
- Create a .rolling() window using 360 periods, select the column 'Ozone', and assign the result to rolling.
- Insert three new columns, 'q10', 'q50' and 'q90' into data, calculating the respective quantiles from rolling.
- Plot data.

## Answer
```py
# Resample, interpolate and inspect ozone data here
data = data.resample('D').interpolate()
data.info()

# Create the rolling window
rolling = data.Ozone.rolling(window=360)

# Insert the rolling quantiles to the monthly returns
data['q10'] = rolling.quantile(0.1)
data['q50'] = rolling.quantile(0.5)
data['q90'] = rolling.quantile(0.9)

# Plot the data
data.plot()
plt.show()
```
```py
>> Output:
<class 'pandas.core.frame.DataFrame'>
DatetimeIndex: 6300 entries, 2000-01-01 to 2017-03-31
Freq: D
Data columns (total 1 columns):
 #   Column  Non-Null Count  Dtype  
---  ------  --------------  -----  
 0   Ozone   6300 non-null   float64
dtypes: float64(1)
```

![image](https://user-images.githubusercontent.com/70928356/235016147-73847edc-336c-48fe-94d1-46d7df5adb09.png)
