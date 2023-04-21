# How to use dates & times with pandas
Pandas has data types tailored to manage date and time information:
- These data types either represent points in time, or periods of time.
- They have attributes and methods that allow you to access and manipulate the time dimention of your data.
- Any column can contain date and time information. However, in time-series, it is most important to have it as a DataFrame index, as this converts the entire DataFrame into a time series

## Data types:
### pd.Timestamp
```py
from datetime import datetime # To manually create dates
time_stamp = pd.Timestamp(datetime(2017, 1, 1)) # Method 1
pd.Timestamp('2017-01-01') == time_stamp

>> Output:
True
```
To create a pandas `Timestamp`:
- Using the `pandas` library, and Python's `datetime` class, you can create a pandas `Timestamp` data type.
- 
```py
time_stamp # type: pandas.tslib.Timestamp

>> Output:
Timestamp('2017-01-01 00:00:00')
```
