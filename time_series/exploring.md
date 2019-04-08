## Using R

```R
AirPassengers
start(AirPassengers)
end(AirPassengers)
plot(AirPassengers)
plot(aggregate(AirPassengers))
monthplot(AirPassengers)
subst = window(AirPassengers, start=c(1960, 1), end=c(1960, 12))
```

## Using Python

```python
import pandas as pd
import numpy as np
import matplotlib.pylab as plt

# base = pd.read_csv()
base = pd.read_csv('AirPassengers.csv',
                   parse_dates=['Month'],
                   index_col='Month',
                   date_parser=lambda x = pd.datetime.strptime(x, "%Y-%m"))

time_serie = base['#Passengers']
time_serie.index.min()
time_serie.index.max()
time_serie['1950']
time_serie['1950-01-01':'1950-07-31']

plt.plot(time_serie)
ts_by_year = ts.resample('A').sum()
plt.plot(ts_by_year)
ts_by_month = ts.groupby([lambda x: X.month]).sum()
plt.plot(ts_by_month)
ts_by_date = time_serie['1960-01-01':'1960-12-01']
plt.plot(ts_by_date)
```