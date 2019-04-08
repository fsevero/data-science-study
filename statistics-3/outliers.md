# Outliers

## Using R

```R
boxplot(iris$Sepal.Width)
boxplot(iris$Sepal.Width, outline=F)
boxplot.stats(iris$Sepal.Width)$out

# install.packages('outliers')
library(outliers)
outlier(iris$Sepal.Width)
outlier(iris$Sepal.Width, opposite=T)
```

## Using Python

```python
import matplotlib.pyplot as plt
import pandas as pd

iris = pd.read_csv('iris.csv')

plt.boxplot(iris.iloc[:, 1])
plt.boxplot(iris.iloc[:, 1], showfliers=False)

# PyOD - Python Outlier Detection
# pip install pyod
from pyod.models.knn import KNN

sepal_width = iris.iloc[:, 1]
sepal_width = sepal_width.values.reshape(-1, 1)
detector = KNN()
detector.fit(sepal_width)
previsions = detector.labels_
```