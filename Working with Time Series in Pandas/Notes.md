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
