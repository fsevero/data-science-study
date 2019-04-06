# Multiple Linear Regression

Simple: `Y ~ X`
Multiple: `Y ~ X1 + X2 + ... + Xn`

# Using R

```R
head(mtcars)
cor(mtcars)

model = lm(mpg ~ disp, data=mtcars)
summary(model)$r.squared # R²
summary(model)$adj.r.squared # adjusted R²
predict(model, data.frame(disp=200))

model = lm(mpg ~ disp + hp + cyl, data=mtcars)
summary(model)$r.squared # R²
summary(model)$adj.r.squared # adjusted R²
predict(model, data.frame(disp=200, hp=100, cyl=4))
```

# Using Python

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from sklearn.linear_model import LinearRegression
import statsmodels.formula.api as sm

base = pd.read_csv('mt_cars.csv')
base = base.drop(['Unnamed: 0'], axis=1)

X = base.iloc[:, 2].values
y = base.iloc[:, 0].values
corr = np.corrcoef(X, y) # -0.84

X = X.reshape(-1, 1)

model = LinearRegression()
model.fit(X, y)
model.score(X, y) # R²

adjusted_model = sm.ols(formula='mpg ~ disp', data=base)
trained_model = adjusted_model.fit()
trained_model.summary()

X = base.iloc[:, 1:4].values
y = base.iloc[:, 0].values
model = LinearRegression()
model.fit(X, y)
model.score(X, y) # R²

adjusted_model = sm.ols(formula='mpg ~ cyl + disp + hp', data=base)
trained_model = adjusted_model.fit()
trained_model.summary()

test = np.array([4, 200, 100])
test.reshape(1, -1)
model.predict(test)
```