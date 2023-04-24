# Your first time series

You have learned in the video how to create a sequence of dates using `pd.date_range()`. You have also seen that each date in the resulting `pd.DatetimeIndex` is a `pd.Timestamp` with various attributes that you can access to obtain information about the date.

Now, you'll create a week of data, iterate over the result, and obtain the `dayofweek` and `day_name()` for each date.

## Instructions
We have already imported pandas as pd for you.

- Use `pd.date_range` to create seven dates starting from '2017-1-1' at (default) daily frequency. Use the arguments `start` and `periods`. Assign the result to `seven_days`.
- Iterate over each date in seven_days and in each iteration, print the `.dayofweek` and `.day_name()` attributes.

## Answer
```py
# Create the range of dates here
seven_days = pd.date_range(start='2017-1-1', periods=7)

# Iterate over the dates and print the number and name of the weekday
for day in seven_days:
    print(day.dayofweek, day.day_name())
```

```py
>> Output:
    6 Sunday
    0 Monday
    1 Tuesday
    2 Wednesday
    3 Thursday
    4 Friday
    5 Saturday
```
