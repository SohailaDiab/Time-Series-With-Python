# Shifting stock prices across time
The first method to manipulate time series that you saw in the video was `.shift()`, which allows you shift all values in a `Series` or `DataFrame` by a number of periods to a different time along the `DateTimeIndex`.

Let's use this to visually compare a stock price series for Google shifted 90 business days into both past and future.

## Instructions
We have already imported `pandas` as `pd` and `matplotlib.pyplot` as `plt`.

- Use `pd.read_csv()` to import `'google.csv'`, parsing the `'Date'` as dates, setting the result as index and assigning to google.
- Use `.asfreq()` to set the frequency of `google` to business daily.
- Add new columns `lagged` and `shifted` to `google` that contain the `Close` shifted by 90 business days into past and future, respectively.
- Plot the three columns of `google`.

## Answer
```py
# Import data here
google = pd.read_csv('google.csv', parse_dates=['Date'], index_col='Date')

print(google.head(3))
print()

# Set data frequency to business daily
google = google.asfreq('B')

# Create 'lagged' and 'shifted'
google['lagged'] = google.Close.shift(periods=-90)
google['shifted'] = google.Close.shift(periods=90)

print(google.head(3))
# Plot the google price series
google.plot()
plt.show()
```
```py
>> Output:
                 Close
    Date              
    2014-01-02  556.00
    2014-01-03  551.95
    2014-01-04     NaN
    
                 Close  lagged  shifted
    Date                               
    2014-01-02  556.00  511.00      NaN
    2014-01-03  551.95  518.73      NaN
    2014-01-06  558.10  529.92      NaN
```

![image](https://user-images.githubusercontent.com/70928356/234349281-8d0266a8-847d-4a51-856e-cdec37c2b329.png)
