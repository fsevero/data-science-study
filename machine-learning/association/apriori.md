# Apriori

## Using R

```R
install.packages("arules")
library(arules)
transactions = read.transactions(file.choose(),
                                 format="basket",
                                 sep=",")
transactions
inspect(transactions)
image(transactions)

rules = apriori(transactions, parameter=list(supp=0.5, conf=0.5))

inspect(rules)

install.packages("arulesViz")
library(arulesViz)
plot(rules)
plot(rules, method="graph", control=list(type="items"))
```

## Using python

```python
import pandas as pd
# pip install apyori
from apyori import apriori

data = pd.read_csv('transactions.txt', header=None)

# this doesn't seems right :/
transactions = []
for i in range(6):
    transactions.append([str(data.values[i,j]) for j in range(3)])

rules = apriori(transactions, min_support=0.5, min_confidence=0.5)
# how to use it?
```