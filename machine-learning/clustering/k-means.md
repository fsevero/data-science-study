# K-Means

## Using R

```R
cluster = kmeans(iris[1:4],center=3)
table(iris$Species, cluster$cluster)
plot(iris[,1:4], col=cluster$cluster)
```

## Using Python

```python
from sklearn import datasets
import numpy as np
from sklearn.metrics import confusion_matrix
import matplotlib.pyplot as plt
from sklearn.cluster import KMeans

iris = datasets.load_iris()
unique, quantity = np.unique(iris.target, return_counts=True)

cluster = KMenas(n_clusters=3)
cluster.fit(iris.data)

centroids = cluster.cluster_centers_
predictions = cluster.labels_
unique, quantity = np.unique(predictions, return_counts=True)

confusion_matrix(iris.target, predictions)

plt.scatter(iris.data[predictions==0, 0],
            iris.data[predictions==0, 1],
            c='green', label='Setosa')
plt.scatter(iris.data[predictions==1, 0],
            iris.data[predictions==1, 1],
            c='red', label='Versicolor')
plt.scatter(iris.data[predictions==2, 0],
            iris.data[predictions==2, 1],
            c='blue', label='Viginica')
plt.legend()
```