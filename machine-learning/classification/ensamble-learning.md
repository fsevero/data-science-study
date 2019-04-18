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

## Using python

```python
import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.preprocessing import LabelEncoder
from sklearn.metrics import confusion_matrix, accuracy_score
from sklearn.ensemble import RandomForestClassifier

credit = pd.read_csv('credit.csv')
forecasters = credit.iloc[:,0:20].values
classes = credit.iloc[:,20].values

# transform all categoric strings into numeric indexes
label_encoder = LabelEncoder()
for i in (0, 2, 3, 5, 6, 8, 9, 11, 13, 14, 16, 18, 19):
    forecasters[:,i] = label_encoder.fit_transform(forecasters[:,i])

X_train, X_test, y_train, y_test = train_test_split(forecasters, classes, test_size=0.3, random_state=0)

forest = RandomForestClassifier(n_estimators=100)
forest.fit(X_train, y_train)

predictions = forest.predict(X_test)
confusion = confusion_matrix(y_test, predictions)
success_rate = accuracy_score(y_test, predictions)
```