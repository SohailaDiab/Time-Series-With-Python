# Comparing stock prices with a benchmark
You also learned in the video how to compare the performance of various stocks against a benchmark. Now you'll learn more about the stock market by comparing the three largest stocks on the NYSE to the Dow Jones Industrial Average, which contains the 30 largest US companies.

The three largest companies on the NYSE are:

**Company	Stock -> Ticker**
- Johnson & Johnson	-> JNJ
- Exxon Mobil	-> XOM
- JP Morgan Chase	-> JPM

## Instructions
We have already imported pandas as pd and matplotlib.pyplot as plt.

- Use pd.read_csv() to import 'nyse.csv' and 'dow_jones.csv', creating a DatetimeIndex for each from the 'date' column using parse_dates and index_col, and assign the result to stocks and dow_jones, respectively.
- Use pd.concat() along axis=1 to combine stocks and dow_jones and assign the result to data. Inspect the .info() of data.
- Divide data by the first value for each series, multiply by 100 and plot the result.

## Answers
```py
# Import stock prices and index here
stocks = pd.read_csv('nyse.csv', parse_dates=['date'], index_col='date')
dow_jones = pd.read_csv('dow_jones.csv', parse_dates=['date'], index_col='date')


# Concatenate data and inspect result here
data = pd.concat([stocks,dow_jones],axis=1)
print(data.info())

# Normalize and plot your data here
data.div(data.iloc[0]).mul(100).plot()
plt.show()
```

```py
>> Output:
    <class 'pandas.core.frame.DataFrame'>
    DatetimeIndex: 1762 entries, 2010-01-04 to 2016-12-30
    Data columns (total 4 columns):
     #   Column  Non-Null Count  Dtype  
    ---  ------  --------------  -----  
     0   JNJ     1762 non-null   float64
     1   JPM     1762 non-null   float64
     2   XOM     1762 non-null   float64
     3   DJIA    1762 non-null   float64
    dtypes: float64(4)
    memory usage: 68.8 KB
```

![image](https://user-images.githubusercontent.com/70928356/234437854-c8fbf873-849d-4ffa-bdf6-7826550d0be1.png)
