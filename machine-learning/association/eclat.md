# Eclat

## Using R

```R
install.packages("arules")
library(arules)

transactions = read.transactions(file.choose(),
                                 format="basket",
                                 sep=",")

rules = eclat(transactions,
              parameter=list(supp=0.1, maxlen=15))
inspect(rules)

install.packages("arulesViz")
library(arulesViz)
plot(rules, method="graph", control=list(type="items"))
```

## Using Python

```python
```