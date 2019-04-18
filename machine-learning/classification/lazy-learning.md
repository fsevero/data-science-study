# Lazy Learning

K-nn: Nearest Neighbor

## Using R

```R
install.packages("class", dependencies=T)
library("class")

summary(iris)

split = sample(2, 150, replace=T, prob=c(0.7, 0.3))
iris_train = iris[split==1,]
iris_test = iris[split==2,]

predictions = knn(iris_train[,1:4], iris_test[,1:4], iris_train[,5], k=3)

table(iris_test[,5], predictions)
```

## Using Python

```python
from sklearn.model_selection import train_test_split
from sklearn.metrics import confusion_matrix, accuracy_score
from sklearn.neighbors import KNeighborsClassifier
from sklearn import datasets
from scipy import stats

iris = datasets.load_iris()
stats.describe(iris.data)

X_train, X_test, y_train, y_test = train_test_split(iris.data, iris.target, test_size=0.3, random_state=0)

knn = KNeighborsClassifier(n_neighbors=3)
knn.fit(X_train, y_train)

predictions = knn.predict(X_test)
confusion = confusion_matrix(y_test, predictions)
success_rate = accuracy_score(t_test, predictions)
```