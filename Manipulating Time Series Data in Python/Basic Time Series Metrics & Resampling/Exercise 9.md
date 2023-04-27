# Compare monthly average stock prices for Facebook and Google
Now, you'll apply your new resampling skills to daily stock price series for Facebook and Google for the 2015-2016 period to compare the trend of the monthly averages.

## Instructions
We have again imported pandas as pd and matplotlib.pyplot as plt for you.

- Use pd.read_csv() to import 'stocks.csv' and set a DateTimeIndex based on the 'date' column using parse_dates and index_col, assign the result to stocks and inspect using .info().
- Create monthly_average by applying .resample() with monthly frequency to data, using .mean() to aggregate. Plot the result using subplots.

## Answer

```py
# Import and inspect data here
stocks = pd.read_csv('stocks.csv', parse_dates=['date'], index_col='date')
print(stocks.info())

# Calculate and plot the monthly averages
monthly_average = stocks.resample('M').mean()

monthly_average.plot(subplots=True)
plt.show()
```

```py
>> Output:
    <class 'pandas.core.frame.DataFrame'>
    DatetimeIndex: 504 entries, 2015-01-02 to 2016-12-30
    Data columns (total 2 columns):
     #   Column  Non-Null Count  Dtype  
    ---  ------  --------------  -----  
     0   FB      504 non-null    float64
     1   GOOG    504 non-null    float64
    dtypes: float64(2)
    memory usage: 11.8 KB
```

![image](https://user-images.githubusercontent.com/70928356/234738747-f893096e-6811-4484-afc2-4c5b301d2981.png)
