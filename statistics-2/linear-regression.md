# Linear Regression

`f(x) = intersection + (x * coef)`

## Using R

```R
head(cars) # speed dist
cor(cars) # 0.8 strong correlation

model = lm(speed ~ dist, data=cars)
summary(model)
model
model$coefficients # intercept, dist
model$residuals
model$fitted.values

plot(model)

plot(speed ~ dist, data=cars)
abline(model)

predict(model, data.frame(dist=22)) # 11.92639 

```

## Using Python

```python
import pandas as pd
import numpy as pd
import matplotlib.pyplot as plt
from sklearn.linear_model import LinearRegression

# Yellowbrick - Machine Learning Visualization
# pip install yellowbrick
from yellowbrick.regressor import ResidualsPlot

base = pd.read_csv('cars.csv')
base = base.drop(['Unnamed: 0'], axis=1)  # remove unwanted data

X = base.iloc[:, 1].values # dist
y = base.iloc[:, 0].values # speed
corr = np.corrcoef(X, y)

X = X.reshape(-1, 1)
model = LinearRegression()
model.fit(X, y)
model.intercept_  # 8.2839...
model.coef_       # 0.1655...

plt.scatter(X, y)
plt.plot(X, model.predict(X), color='red')

model.predict(22) # 11.9263...

model._residues # 478.0212...

vis = ResidualsPlot(model)
vis.fit(X, y)
vis.poof()
```