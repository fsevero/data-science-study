# Statistics

## Sample data

```R
# Using R
data = sample(c(0,1), 150, replace = TRUE, prob=c(0.5,0.5))
length(data[data==1])
sample(c(1000), 1)

install.packages("sampling")
library("sampling")
data=strata(iris,c("Species"),size=c(25,25,25), method="srswor")
sumary(data)

install.packages("TeachingSampling")
library("TeachingSampling")

indexes = S.SY(150, 10)
data = iris[indexes,]
```

```python
# Using python
import pandas as pd
import numpy as np
from scipy import stats
from sklearn.model_selection import train_test_split

base = pd.read_csv('iris.csv')
base
base.shape

sample = np.random.choice(a=[0, 1], size=150, replace=True, p=[0.5, 0.5])
len(sample)
len(sample[sample == 1])

X, _, y, _ = train_test_split(iris.iloc[:, 0:4], iris.iloc[:, 4],
                              test_size=0.5, stratify=iris.iloc[:,4])
y.value_counts()
```

## Variability

```R
# Using R
# x = c(...)
quantile(x)
sd(x)
var(x)
mean(x)
median(x)
```

```python
# Using python
import numpy as np
from scipy import stats

np.mean(x)
np.median(x)
np.quantile(x, [0, 0.25, 0.5, 0.75, 1])
np.std(x, ddof=1)
stats.describe(x)
```

## Probability

`P = expected / possibilities`

## Binomial Distribution

* Fixed number of experiments
* Only 2 results
* Fixed probability 
* Independent experiments

```R
# Using R
# dbinom(success, experiments, probability of success)
dbinom(1, 4, 0.25) # probability
pbinom(1, 4, 0.25) # cummulative
```

```python
# Using Python
from scipy.stats import binom

# (success, experiments, probability of success)
binom.pmf(3, 5, 0.5)  # probability
binom.cdf(4, 4, 0.25) # cummulative
```

## Normal Distribution

Bell curve with 10-40-90-10 probability distribution.

```R
# Using R
# pnorm(value, mean, deviation, lower.tail=T|F)
pnorm(6, 8, 2, lower.tail=T) # probability
qnorm() # cummulative

x = rnorm(100)
qqnorm(x)
qqline(x)
shapiro.test(x)
```

```python
# Using python
from scipy import stats
from scipy.stats import norm
import matplotlib.pyplot as plt

# (value, mean, deviation)
norm.cdf(6, 8, 2) # left tail
norm.sf(6, 8, 2)  # right tail (1 - cdf)

data = norm.rvs(size=100)
stats.probplot(data, plot=plt)
stats.shapiro(data)
```

## T Student

Normal distribution with very low dataset

```R
# Using R
pt(1.5, 8, lower.tail=F)
```

```python
# Using Python
from scipy.stats import t

t.cdf(1.5, 8) # left tail
t.sf(1.5, 8)  # right tail 1 - cdf
```