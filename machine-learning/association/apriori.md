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
```