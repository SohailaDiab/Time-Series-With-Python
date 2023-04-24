# How to use dates & times with pandas
Pandas has data types tailored to manage date and time information:
- These data types either represent points in time, or periods of time.
- They have attributes and methods that allow you to access and manipulate the time dimention of your data.
- Any column can contain date and time information. However, in time-series, it is most important to have it as a DataFrame index, as this converts the entire DataFrame into a time series

## Data types:
### pd.Timestamp
To represent a point in time.

```py
from datetime import datetime # To manually create dates
time_stamp1 = pd.Timestamp(datetime(2017, 1, 1)) # Method 1
time_stamp2 = pd.Timestamp('2017-01-01') # Method 2

time_stamp1 == time_stamp2

>> Output:
True
```
2 methods to create a pandas `Timestamp` data type:
- Using the `pandas` library, and Python's `datetime` class.
- Using the `pandas` library, and passing a date `string`.
```py
time_stamp1 # type: pandas.tslib.Timestamp

>> Output:
Timestamp('2017-01-01 00:00:00')
```
> If you display the timestamp, you will notice that the time has been automatically set to midnight.

#### pd.Timestamp attributes
- Year
```py
time_stamp1.year

>> Output: 
2017
```

- Name of weekday
```py
time_stamp1.day_name()

>> Output: 
'Sunday'
```
### pd.Period
To represent periods of time.

- To define the period:
```py
period = pd.Period('2017-01')
period # defauly: month-end

>> Output:
Period('2017-01', 'M')
```
> The period object always has a frequency, with months as the default. *(Meaning the period is over months).*

- Change frequency from monthly ('M') to daily ('D'):
```py
period.asfreq('D')

>> Output:
Period('2017-01-31', 'D')
```
- Convert `Period` to `Timestamp` object, and back to a `Period` object:
```py
period.to_timestamp().to_period('M')

>> Output:
Period('2017-01', 'M')
```
## Data arithmetic:
Starting out with:
```py
period = Period('2017-01', 'M')
```

- Addition:
```py
period + 2

>> Output:
Period('2017-03', 'M')
```
> Since it is a monthly frequency, adding 2 goes from January 2017 to March 2017.

```py
pd.Timestamp('2017-01-31', 'M') + 1

>> Output:
Timestamp('2017-02-28 00:00:00', freq='M')
```
> Timestamps can also have frequency information.

## Creating a time series
You need a sequence of dates to create a time series. For that, we will create a sequence of Timestamps using the pandas function `date_range`.
- `pd.date_range`:`start`, `end`, `periods`, `freq`.<br> Specify start date, end date/# of periods, and the frequency.
```py
index = pd.date_range(start='2017-01-01', periods=12, freq='M')
index

>> Output:
DatetimeIndex(['2017-01-31', '2017-02-28', '2017-03-31', ...,
              ['2017-09-30', '2017-10-31', '2017-11-30', '2017-12-31'],
              dtype='datetime64[ns]', freq='M')
```
> The default is daily frequency 'D'.
> The function returns the sequence of dates as a DateTimeindex with frequency information.

```py
index[0]

>> Output:
Timestamp('2017-01-31 00:00:00', freq='M')
```
> The first element is a pandas Timestamp.

### Convert DatimetimeIndex to PeriodIndex
```py
index.toPeriod()

>> Output:
PeriodIndex(['2017-01', '2017-02', '2017-03', ...,
              ['2017-09', '2017-10', '2017-11', '2017-12'],
              dtype='period[ns]', freq='M')
```

## Create a time series by setting the `DatimeTimeIndex`, as the index of the DataFrame.

```py
pd.DataFrame({data=data, index:index})
```

## Aliases and Attributes
![image](https://user-images.githubusercontent.com/70928356/233877480-e28731fd-cca5-426d-b7ce-8e3e16c9fb4c.png)
