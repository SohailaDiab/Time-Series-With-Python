# Calculating stock price changes
You have learned in the video how to calculate returns using current and shifted prices as input. Now you'll practice a similar calculation to calculate absolute changes from current and shifted prices, and compare the result to the function `.diff()`.

## Instructions
We have already imported pandas as pd and matplotlib.pyplot as plt. We have also loaded Yahoo stock prices for the years 2013 to 2015, set the frequency to business daily, and assigned the result to yahoo.

- Create a new column called `shifted_30` that contains the `'price'` shifted by 30 business days into the future.
- Subtract `'shifted_30'` from `'price'`, and assign the result to a new column, `'change_30'`.
- Apply `.diff()`, setting periods to 30, and assign the result to a new column, `'diff_30'`.
- Inspect the last five rows of `yahoo` to verify the calculation.
- Subtract `diff_30` from `change_30` using the `.sub()` method and print the `.value_counts()` of the result to show both columns are equal.

## Answer
```py
# Created shifted_30 here
yahoo['shifted_30'] = yahoo.price.shift(periods=30)

# Subtract shifted_30 from price
yahoo['change_30'] = yahoo.price-yahoo.shifted_30

# Get the 30-day price difference
yahoo['diff_30'] = yahoo.price.diff(periods=30)

# Inspect the last five rows of price
print(yahoo.tail())

# Show the value_counts of the difference between change_30 and diff_30
print(yahoo.diff_30.sub(yahoo.change_30).value_counts())
```
```py
>> Output:
                price  shifted_30  change_30  diff_30
    date                                             
    2015-12-25    NaN       32.19        NaN      NaN
    2015-12-28  33.60       32.94       0.66     0.66
    2015-12-29  34.04       32.86       1.18     1.18
    2015-12-30  33.37       32.98       0.39     0.39
    2015-12-31  33.26       32.62       0.64     0.64
    0.0    703
    dtype: int64
```
