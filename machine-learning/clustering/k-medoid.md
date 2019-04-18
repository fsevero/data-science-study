# K Medoid

## Using R

```R
install.packages("cluster", dependencies=T)
library(cluster)

cluster = pam(iris[,1:4], k=3)
plot(cluster)
table(iris$Species, cluster$clustering)
```