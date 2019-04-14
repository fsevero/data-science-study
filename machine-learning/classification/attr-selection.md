# Attribute selection

## Using R

```R
install.packages("e1071", dependencies=T)
library(e1071)

credit = read.csv(file.choose(), sep=",", header=T)
test_train = sample(2,1000,replace=T,prob=c(0.7,0.3))
credit_training = credit[test_train==1,]
credit_testing = credit[test_train==2,]

model = svm(class~., credit_training)
predictions = predict(model, credit_testing)
confusion = table(credit_testing$class, predictions)
success_rate = (confusion[1] + confusion[4]) / sum(confusion)
error_rate = (confusion[2] + confusion[3]) / sum(confusion)
# 76% success rate

install.packages("FSelector", dependencies=T)
library(FSelector)
random.forest.importance(class~., credit)

model = svm(class~checking_status+duration+credit_history+purpose, credit_training)
predictions = predict(model, credit_testing)
confusion = table(credit_testing$class, predictions)
success_rate = (confusion[1] + confusion[4]) / sum(confusion)
error_rate = (confusion[2] + confusion[3]) / sum(confusion)
# 77% success rate
```

## Using Python

```python
import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.preprocessing import LabelEncoder
from sklearn.metrics import confusion_matrix, accuracy_score
from sklearn.svm import SVC
from sklearn.ensemble import ExtraTreesClassifier

credit = pd.read_csv('credit.csv')
forecasters = credit.iloc[:,0:20].values
classes = credit.iloc[:,20].values

# transform all categoric strings into numeric indexes
label_encoder = LabelEncoder()
for i in (0, 2, 3, 5, 6, 8, 9, 11, 13, 14, 16, 18, 19):
    forecasters[:,i] = label_encoder.fit_transform(forecasters[:,i])

X_train, X_test, y_train, y_test = train_test_split(forecasters, classes, test_size=0.3, random_state=0)

svm = SVC()
svm.fit(X_train, y_train)
predictions = svm.predict(X_test)
success_rate = accuracy_score(y_test, predictions)

forest = ExtraTreesClassifier()
forest.fit(X_train, y_train)
forest.feature_importances_

X_train = X_train[:,[0,1,2,3]]
X_test = X_test[:,[0,1,2,3]]
svm = SVC()
svm.fit(X_train, y_train)
predictions = svm.predict(X_test)
success_rate = accuracy_score(y_test, predictions)
```