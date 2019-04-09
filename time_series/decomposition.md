# Decomposition

## Using R

```R
plot(AirPassengers)
dec = decompose(AirPassengers)
dec$x
dec$season
dec$trend
dec$random
plot(dec$random)
plot(dec)
```

## Using Python

```python
import pandas as pd
import numpy as np
import matplotlib.pylab as plt
from statsmodels.tsa.seasonal import seasonal_decompose

ts = base['#Passengers']
plt.plot(ts)

dec = seasonal_decompose(ts)
dec.trend
dec.seasonal
dec.resid
plt.plot(dec.resid)

plt.subplot(4,1,1)
plt.plot(ts, label='Original')
plt.legend(loc='best')
plt.subplot(4,1,2)
plt.plot(ts, label='Trend')
plt.legend(loc='best')
plt.subplot(4,1,3)
plt.plot(ts, label='Seasonal')
plt.legend(loc='best')
plt.subplot(4,1,4)
plt.plot(ts, label='Random')
plt.legend(loc='best')
plt.tight_layout()
```