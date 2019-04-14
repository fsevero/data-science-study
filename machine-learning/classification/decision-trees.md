# Decision Trees

## Using R

```R
install.packages("rpart", dependecies=T)
library(rpart)

credit = read.csv(file.choose(), sep=",", header=T)
test_train = sample(2,1000,replace=T,prob=c(0.7,0.3))
credit_training = credit[test_train==1,]
credit_testing = credit[test_train==2,]

tree = rpart(class~., data=credit_training, method="class")
plot(tree)
text(tree, use.n=T, all=T, cex=.8)

predictions = predict(tree, newdata=credit_testing)
validation = cbind(credit_testing, predictions)
validation["Result"] = ifelse(validation$bad >= 0.5, "bad", "good")

confusion = table(validation$class, validation$Result)
success_rate = (confusion[1] + confusion[4]) / sum(confusion)
error_rate = (confusion[2] + confusion[3]) / sum(confusion)
```