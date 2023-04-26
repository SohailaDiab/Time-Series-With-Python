# Interpolate debt/GDP and compare to unemployment
Since you have learned how to interpolate time series, you can now apply this new skill to the quarterly debt/GDP series, and compare the result to the monthly unemployment rate.

## Instructions
We have imported pandas as pd and matplotlib.pyplot as plt for you.

- Use pd.read_csv() to import 'debt_unemployment.csv', creating a DateTimeIndex from the 'date' column using parse_dates and index_col, and assign the result to data. print() the .info() of the data.
- Apply .interpolate() to data and assign this to interpolated, then inspect the result.
- Plot interpolated with 'Unemployment' on the secondary_y axis.

## Answer
```py
# Import & inspect data here
data = pd.read_csv('debt_unemployment.csv', parse_dates=['date'], index_col='date')
print(data.info())
print()
print(data.head())
print()
# Interpolate and inspect here
interpolated = data.interpolate()
print(interpolated.info())
print()
print(interpolated.head())

# Plot interpolated data here
interpolated.plot(secondary_y='Unemployment')
plt.show()
```
```py
>> Output:
<class 'pandas.core.frame.DataFrame'>
DatetimeIndex: 89 entries, 2010-01-01 to 2017-05-01
Data columns (total 2 columns):
 #   Column        Non-Null Count  Dtype  
---  ------        --------------  -----  
 0   Debt/GDP      29 non-null     float64
 1   Unemployment  89 non-null     float64
dtypes: float64(2)
memory usage: 2.1 KB
None

            Debt/GDP  Unemployment
date                              
2010-01-01    87.004           9.8
2010-02-01       NaN           9.8
2010-03-01       NaN           9.9
2010-04-01    88.670           9.9
2010-05-01       NaN           9.6

<class 'pandas.core.frame.DataFrame'>
DatetimeIndex: 89 entries, 2010-01-01 to 2017-05-01
Data columns (total 2 columns):
 #   Column        Non-Null Count  Dtype  
---  ------        --------------  -----  
 0   Debt/GDP      89 non-null     float64
 1   Unemployment  89 non-null     float64
dtypes: float64(2)
memory usage: 2.1 KB
None

            Debt/GDP  Unemployment
date                              
2010-01-01    87.004           9.8
2010-02-01    87.559           9.8
2010-03-01    88.115           9.9
2010-04-01    88.670           9.9
2010-05-01    89.135           9.6
```

![image](https://user-images.githubusercontent.com/70928356/234724502-3fb2de3f-57c2-43c8-878e-e7bb7fe92f84.png)
