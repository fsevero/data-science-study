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