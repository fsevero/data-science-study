# Ensamble Learning

## Using R

```R
install.packages("randomForest", dependencies=T)
library(randomForest)

credit = read.csv(file.choose(), sep=",", header=T)
test_train = sample(2,1000,replace=T,prob=c(0.7,0.3))
credit_train = credit[test_train==1,]
credit_test = credit[test_train==2,]

forest = randomForest(class~., data=credit_train, ntree=100, importance=T)
varImpPlot(forest)

predictions = predict(forest, credit_test)
confusion = table(predictions, credit_test$class)
success_rate = (confusion[1] + confusion[4]) / sum(confusion)
```