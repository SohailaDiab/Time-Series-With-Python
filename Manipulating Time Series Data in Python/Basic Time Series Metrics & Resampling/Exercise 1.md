# Compare the performance of several asset classes
You have seen in the video how you can easily compare several time series by normalizing their starting points to 100, and plot the result.

To broaden your perspective on financial markets, let's compare four key assets: stocks, bonds, gold, and oil.


## Instructions
We have already imported pandas as pd and matplotlib.pyplot as plt.

Import 'asset_classes.csv', using .read_csv() to parse dates in the 'DATE' column and set this column as the index, then assign the result to prices.
Select the first price for each series using .iloc[0] on prices and assign the result to first_prices.
Divide prices by first_prices, multiply by 100 and assign the result to normalized.
Plot normalized.

## Answer
```py
# Import data here
prices = pd.read_csv('asset_classes.csv', parse_dates=['DATE'], index_col='DATE')

# Inspect prices here
print(prices.head())
print()
print(prices.info())

# Select first prices
first_prices = prices.iloc[0]

# Create normalized
normalized = prices.div(first_prices).mul(100)

# Plot normalized
normalized.plot()
plt.show()
```

```py
>> Output:
                  SP500   Bonds    Gold    Oil
    DATE                                      
    2007-06-29  1503.35  402.15  648.50  70.47
    2007-07-02  1519.43  402.96  650.50  71.11
    2007-07-03  1524.87  402.02  657.25  71.41
    2007-07-05  1525.40  400.15  655.90  71.81
    2007-07-06  1530.44  399.31  647.75  72.80
    
    <class 'pandas.core.frame.DataFrame'>
    DatetimeIndex: 2469 entries, 2007-06-29 to 2017-06-26
    Data columns (total 4 columns):
     #   Column  Non-Null Count  Dtype  
    ---  ------  --------------  -----  
     0   SP500   2469 non-null   float64
     1   Bonds   2469 non-null   float64
     2   Gold    2469 non-null   float64
     3   Oil     2469 non-null   float64
    dtypes: float64(4)
    memory usage: 96.4 KB
```

![image](https://user-images.githubusercontent.com/70928356/234434201-f0a27920-2482-43b8-9443-28846fea9692.png)
