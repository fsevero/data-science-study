# Poisson Distribution

# Using R

```R
dpois(x, lambda)
dpois(x, lambda, lower.tail=F)
ppois(x, lambda)
ppois(x, lambda, lower.tail=F)
```

# Using Python

```python
from scipy.stats import poisson

poisson.pmf(x, lambda_) # probability
poisson.cdf(x, lambda_) # cumulative
posson.sf(x, lambda_)   # lower tail
```