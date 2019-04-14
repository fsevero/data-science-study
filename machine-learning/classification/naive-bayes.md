# Naive Bayes

## Using R

```R
install.packages("e1071", dependencies=T)
library(e1071)

credit = read.csv(file.choose(), sep=",", header=T)
head(credit)
dim(credit)

test_train = sample(2,1000,replace=T,prob=c(0.7,0.3))
credit_training = credit[test_train==1,]
credit_testing = credit[test_train==2,]

model = naiveBayes(class~., credit_training)
predictions = predict(model, credit_testing)

confusion = table(credit_testing$class, predictions)
success_rate = (confusion[1] + confusion[4]) / sum(confusion)
error_rate = (confusion[2] + confusion[3]) / sum(confusion)

new_credit = read.csv(file.choose(), sep=",", header=T)
predict(model, new_credit)
```