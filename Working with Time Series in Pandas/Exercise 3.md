# Compare annual stock price trends
In the video, you have seen how to select sub-periods from a time series.

You'll use this to compare the performance for three years of Yahoo stock prices.

## Instructions
We have already imported `pandas` as `pd` and `matplotlib.pyplot` as `plt` and we have already loaded the `'yahoo.csv'` file in a variable yahoo with `DateTimeIndex` and a single column `price`.

- Create an empty `pd.DataFrame()` called `prices`.
- Iterate over a list containing the three years, 2013, 2014, and 2015, as `string`, and in each loop:
  - Use the iteration variable to select the data for this year and the column `price`.
  - Use `.reset_index()` with `drop=True` to remove the `DatetimeIndex`.
  - Rename the column `price` to the appropriate `year`.
  - Use `pd.concat()` to combine the yearly data with the data in `prices` along `axis=1`.
- Plot `prices`.

## Answer
```py
# Create dataframe prices here
prices = pd.DataFrame()
print(yahoo.head())
print('------------------------------')
print(yahoo.loc['2013', ['price']].reset_index(drop=True).head())
print('------------------------------')

# Select data for each year and concatenate with prices here 
for year in ['2013', '2014', '2015']:
    price_per_year = yahoo.loc[year, ['price']].reset_index(drop=True)
    price_per_year.rename(columns={'price': year}, inplace=True)
    prices = pd.concat([prices, price_per_year], axis=1)
print(prices.head())

# Plot prices
prices.plot(subplots=True)
plt.show()
```
```
>> Output:
                price
    date             
    2013-01-02  20.08
    2013-01-03  19.78
    2013-01-04  19.86
    2013-01-07  19.40
    2013-01-08  19.66
    ------------------------------
       price
    0  20.08
    1  19.78
    2  19.86
    3  19.40
    4  19.66
    ------------------------------
        2013   2014   2015
    0  20.08    NaN    NaN
    1  19.78  39.59  50.17
    2  19.86  40.12  49.13
    3  19.40  39.93  49.21
    4  19.66  40.92  48.59
```
![image](https://user-images.githubusercontent.com/70928356/234119405-bd1490a6-6dda-4fb7-8029-4d33dbdafc19.png)
