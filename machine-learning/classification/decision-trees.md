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

## Using Python

```python
import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.preprocessing import LabelEncoder
from sklearn.metrics import confusion_matrix, accuracy_score
from sklearn.tree import DecisionTreeClassifier

credit = pd.read_csv('credit.csv')
forecasters = credit.iloc[:,0:20].values
classes = credit.iloc[:,20].values

# transform all categoric strings into numeric indexes
label_encoder = LabelEncoder()
for i in (0, 2, 3, 5, 6, 8, 9, 11, 13, 14, 16, 18, 19):
    forecasters[:,i] = label_encoder.fit_transform(forecasters[:,i])

X_train, X_test, y_train, y_test = train_test_split(forecasters, classes, test_size=0.3, random_state=0)

tree = DecisionTreeClassifier()
tree.fit(X_train, y_train)

# pip install graphviz
import graphviz
from sklearn.tree import export_graphviz
export_graphviz(tree, out_file='tree.dot')

predictions = tree.predict(X_test)
confusion = confusion_matrix(y_test, predictions)
success_rate = accuracy_score(y_test, predictions)
```