# Decision Trees

## Using R

```R
install.packages("rpart", dependecies=T)
library(rpart)

credit = read.csv(file.choose(), sep=",", header=T)
test_train = sample(2,1000,replace=T,prob=c(0.7,0.3))
credit_training = credit[test_train==1,]
credit_testing = credit[test_train==2,]


```