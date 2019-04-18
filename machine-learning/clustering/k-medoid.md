# K Medoid

## Using R

```R
install.packages("cluster", dependencies=T)
library(cluster)

cluster = pam(iris[,1:4], k=3)
plot(cluster)
table(iris$Species, cluster$clustering)
```

## Using python

```python
from sklearn import datasets
from sklearn.metrics import confusion_matrix
import numpy as np
# pip install pyclustering
from pyclustering.cluster.kmedoids import kmedoids
from pyclustering.cluster import cluster_visualizer

iris = datasets.load_iris()

cluster = kmedoids(iris.data[:, 0:2], # something about visualization problem with more than 2 attributes, but it can be done
                   [3, 12, 20]) # random indexes
cluster.get_medoids()
cluster.process()

predictions = cluster.get_clusters()
medoids = cluster.get_medoids()

visualizer = cluster_visualizer()
visualizer.append_clusters(predictions, data=iris.data[:,0:2])
visualizer.append_clusters(medoids, data=iris.data[:,0:2], marker='*', markersize=15)
visualizer.show()

# This is very odd
prediction_list = []
real_list = []
for i n range(len(predictions)):
    for j in range(len(predictions[i]))
        prediction_list.append(i)
        real_list.append(iris.target[predictions[i][j]])
prediction_list = np.asarray(prediction_list)
real_list = np.asarray(real_list)

confusion_matrix(real_list, prediction_list)
```