# Fuzzy C Means

## Using R

```R
# install.packages('e1071')
library(e1071)

cluster = cmeans(iris[,1:4], center=3)
table(iris$Species, cluster$cluster)
```