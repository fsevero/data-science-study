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

## Using Python

```python
import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.naive_bayes import GaussianNB
from sklearn.preprocessing import LabelEncoder
from sklearn.metrics import confusion_matrix, accuracy_score

credit = pd.read_csv('credit.csv')
forecasters = credit.iloc[:,0:20].values
classes = credit.iloc[:,20].values

# transform all categoric strings into numeric indexes
label_encoder = LabelEncoder()
for i in (0, 2, 3, 5, 6, 8, 9, 11, 13, 14, 16, 18, 19):
    forecasters[:,i] = label_encoder.fit_transform(forecasters[:,i])

X_train, X_test, y_train, y_test = train_test_split(forecasters, classes, test_size=0.3, random_state=0)

naive_bayes = GaussianNB()
naive_bayes.fit(X_train, y_train)

predictions = naive_bayes.predict(X_test)
confusion = confusion_matrix(y_test, predictions)
success_rate = accuracy_score(y_test, predictions)

from yellowbrick.classifier import ConfusionMatrix
v = ConfusinoMatrix(GaussianNB())
v.fit(X_train, y_train)
v.score(X_test, y_test)
v.poof()

new_credit = pd.read_csv('new_credit.csv')
new_credit = new_credit.iloc[:,0:20].values
# Must use the same label_encoder to use the same values
for i in (0, 2, 3, 5, 6, 8, 9, 11, 13, 14, 16, 18, 19):
    new_credit[:,i] = label_encoder.fit_transform(new_credit[:,i])
naive_bayes.predict(new_credit)
```