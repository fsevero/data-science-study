# Chi Squared

## Using R

```R
x = matrix(c(19,6,43,32), nrow=2, byrow=T)
rownames(x) = c("Male", "Female")
colnames(x) = c("Yes", "No")
chisq.test(x)
```

## Using Python

```python
import numpy as np
from scipy.stats import chi2_contingency

x = np.array([[19,6],[43,32]])
chi2_contingency(x)
```