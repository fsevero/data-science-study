# Forecast

## Using R

```R
AirPassengers
mean(AirPassengers)
mean(AirPassengers, start=c(1960,1), end=c(1960,12))

install.packages(forecast)
library(forecast)

moving_average = ma(AirPassengers, order=12)
result = forecast(moving_average, h=12)
result
plot(result)

arima = auto.arima(AirPassengers)
result = forecast(arima, h=12)
result
plot(result)
```

## Using Python

```python
import pandas as pd
import matplotlib.pylab as plt
from statsmodels.tsa.arima_model import ARIMA

ts = base['#Passengers']
plt.plot(ts)

ts.mean()
ts['1960-01-01':'1960-12-01'].mean()

moving_average = ts.rolling(window=12).mean()

plt.plot(ts)
plt.plot(moving_average, color='red')

forecasts = []
for i in range(1, 13):
    sup = len(moving_average) - i
    inf = sup - 11
    forecasts.append(moving_average[inf:sup].mean())
forecasts = forecasts[::-1]
plt.plot(previsoes)

arima = ARIMA(ts, order=(2, 1, 2))
model = arima.fit()
model.summary()

forecasts = model.forecast(steps=12)

axis = ts.plot()
model.plot_predict('1960-01-01', '1962-01-01',
                   ax=axis, plot_insample=True)

# pip install pyramid-arima
from pyramid.arima import auto_arima
model = auto_arima(ts, m=12, seasonal=True, trace=True)
model.summary()
forecasts = model.predict(n_periods=12)
```