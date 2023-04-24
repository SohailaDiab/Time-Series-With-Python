# Set and change time series frequency
In the video, you have seen how to assign a frequency to a `DateTimeIndex`, and then change this frequency.

Now, you'll use data on the daily carbon monoxide concentration in NYC, LA and Chicago from 2005-17.

You'll set the frequency to calendar daily and then resample to monthly frequency, and visualize both series to see how the different frequencies affect the data.

## Instructions
We have already imported `pandas` as `pd` and `matplotlib.pyplot` as `plt` and we have already loaded the `co_cities.csv` file in a variable `co`.

- Inspect `co` using `.info()`.
- Use `.asfreq()` to set the frequency to calendar daily.
- Show a plot of `'co'` using `subplots=True`.
- Change the the frequency to monthly using the alias `'M'`.
- Show another plot of `co` using `subplots=True`.

## Answer
```py
# Inspect data
print(co.head(3))
print()
print(co.info())

# Set the frequency to calendar daily
co = co.asfreq('D')

# Plot the data
co.plot(subplots=True)
plt.show()

# Set frequency to monthly
co = co.asfreq('M')

# Plot the data
co.plot(subplots=True)
plt.show()
```
```py
>> Output:
                Chicago  Los Angeles  New York
    date                                      
    2005-01-01    0.318        0.778     0.640
    2005-01-03    0.521        0.350     0.970
    2005-01-04    0.477        0.627     0.905
    
    <class 'pandas.core.frame.DataFrame'>
    DatetimeIndex: 1898 entries, 2005-01-01 to 2010-12-31
    Data columns (total 3 columns):
     #   Column       Non-Null Count  Dtype  
    ---  ------       --------------  -----  
     0   Chicago      1898 non-null   float64
     1   Los Angeles  1898 non-null   float64
     2   New York     1898 non-null   float64
    dtypes: float64(3)
    memory usage: 59.3 KB
```
![image](https://user-images.githubusercontent.com/70928356/234139321-8371ec32-a373-4546-95e6-f8ec9e22ac8c.png)

![image](https://user-images.githubusercontent.com/70928356/234139344-bc69ae63-9798-47e8-bdc3-0979e9367345.png)
