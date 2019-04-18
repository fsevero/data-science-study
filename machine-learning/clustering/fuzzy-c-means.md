# Fuzzy C Means

## Using R

```R
# install.packages('e1071')
library(e1071)

cluster = cmeans(iris[,1:4], center=3)
table(iris$Species, cluster$cluster)
```

## Using python

```python
from sklearn import datasets
import numpy as np
from sklearn.metrics import confusion_matrix
import skfuzzy  # pip install scikit-fuzzy

iris = datasets.load_iris()

# iris.data.T = transform lines to columns
result = skfuzzy.cmeans(data=iris.data.T, c=3, m=2, error=0.005, maxiter=1000, init=None)

percentage_predictions = result[1]
predictions = percentage_predictions.argmax(axis=0)

confusion_matrix(iris.target, predictions)
```