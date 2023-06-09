# Plotting multi-period returns
The last time series method you have learned about in the video was `.pct_change()`. Let's use this function to calculate returns for various calendar day periods, and plot the result to compare the different patterns.

We'll be using Google stock prices from 2014-2016.

## Instructions
We have already imported `pandas` as `pd`, and `matplotlib.pyplot` as plt. We have also loaded `'GOOG'` stock prices for the years 2014-2016, set the frequency to calendar daily, and assigned the result to `google`.

- Create the columns `'daily_return'`, `'monthly_return'`, and `'annual_return'` that contain the `pct_change()` of `'Close'` for 1, 30 and 360 calendar days, respectively, and multiply each by 100.
- Plot the result using `subplots=True`.

## Answer
```py
# Create daily_return
google['daily_return'] = google.Close.pct_change(periods=1).mul(100)

# Create monthly_return
google['monthly_return'] = google.Close.pct_change(periods=30).mul(100)

# Create annual_return
google['annual_return'] = google.Close.pct_change(periods=360).mul(100)

# Plot the result
google.plot(subplots=True)
plt.show()
```

![image](https://user-images.githubusercontent.com/70928356/234419374-83b4cd6e-b08f-4c14-8eb4-f8208ddaf643.png)
