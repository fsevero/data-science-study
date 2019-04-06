# Linear Regression

`f(x) = intersection + (x * coef)`

## Using R

```R
head(cars) # speed dist
cor(cars) # 0.8 strong correlation

model = lm(speed ~ dist, data=cars)
summary(model)
model
model$coefficients # intercept, dist
model$residuals
model$fitted.values

plot(model)

plot(speed ~ dist, data=cars)
abline(model)

predict(model, data.frame(dist=22)) # 11.92639 

```

## Using Python

```python
# python
```