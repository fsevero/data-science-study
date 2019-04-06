# Logistic Regression

Binary probability response (percentage of success)

## Using R

```R
elections = read.csv(file.choose(), sep=";", header=T)
fix(elections) # candidate, elected, expenses
plot(elections$ELECTED, elections$EXPENSES)

model = glm(ELECTED ~ EXPENSES, data=elections, family="binomial")
summary(model)

plot(elections$ELECTED, elections$EXPENSES, color="red", pch=20)
points(elections$EXPENSES, modelo$fitted, pch=4)

preview = read.csv(file.choose(), sep=";", header=T)
fix(preview) # candidate, expenses
preview$RESULT = predict(model, newdata=preview, type="response")
fix(preview) # candidate, expenses, result (%)
```

## Using Python

```python
import pandas as pd
import matplotlib.pyplot as plt
import numpy as np
from sklear.linear_model import LogisticRegression

base = pd.read_csv('elections.csv')
plt.scatter(base.expenses, base.elected)

X = base.iloc[:, 2].values
X = X[:, np.newaxis]
y = base.iloc[:, 1].values

model = LogisticRegression()
model.fit(X, y)

preview = pd.read_csv('new_candidates.csv')
expenses = preview.iloc[:, 1].values
expenses = expenses.reshape(-1, 1)
test = model.predict(expenses)
```