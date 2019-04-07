# Anova

Analysis of Variancy:
* T test
* Analysis of Variancy
* Tukey Test

## Using R

```R
t.test(y~x)
aov(V.Dependent ~ V.Independent, data=x)
aov(V.Dependent ~ V.Independent * V.Independent, data=x)
TukeyHSD(aov)

boxplot(treatment$Hours ~ treatment$Medicine)
anova = aov(Hours ~ Medicine, data=treatment)
summary(anova)
anova = aov(Hours ~ Medicine * Sex, data=treatment)
summary(anova)

tukey = TukeyHSD(anova)
tukey
plot(tukey)
```

## Using Python

```python
import pandas as pd
from scipy import stats
import statsmodels.api as sm
from statsmodels.formula.api import ols
from statsmodels.stats.multicomp import MultiComparison

treatment.boxplot(by='Medicine', grid=False)
model = ols('Hours ~ Medicine', data=treatment).fit()
results = sm.stats.anova_lm(model)

model = ols('Hours ~ Medicine * Sex', data=treatment).fit()
results = sm.stats.anova_lm(model)

mc = MultiComparison(treatment['Hours'], treatment['Medicine'])
tukey = mc.tukeyhsd()
tukey.plot_simultaneous()
```