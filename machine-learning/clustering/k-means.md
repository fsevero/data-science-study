# K-Means

## Using R

```R
cluster = kmeans(iris[1:4],center=3)
table(iris$Species, cluster$cluster)
plot(iris[,1:4], col=cluster$cluster)
```