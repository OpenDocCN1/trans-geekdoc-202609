```
residual_y = y-np.matmul(x,b)
return residual_y
def LC(beta):
    ri = residual(beta,x,y)
    rho = (1/a)*logcosh(a*ri)
    loss = np.sum(rho)
    return loss
```

+   d) Create a column of 1's in the x matrix.

```
column_ones = np.ones((24, 1))
x = np.hstack((column_ones, X))
```

+   e) Find the slope and intercept using log-cosh.

```
initbeta = np.array([0., 0.])
a = 2
minval = minimize(LC,initbeta)
beta = minval.x
```

+   f) Plot the results.

```
abline = np.zeros(x.shape[0])
for i in range(x.shape[0]):
    abline[i] = beta[0]+beta[1]*x[i,1]
plt.plot(x[:,1],abline)
plt.scatter(x[:,1],y)
plt.show()
```

+   g) Rerun with different values of the robustness coefficient a. Comment on the results.

+   h) Run the Huber regressor. Adjust \(\delta\) (which is called epsilon) starting from 4.0 down to 0.1 to determine its effect. Is this implementation of Huber's method satisfactory?

```
X = np.linspace(0, 23, 24).reshape(-1, 1)
huber = HuberRegressor(epsilon=4.0)
huber.fit(X, y)
y_pred = huber.predict(X)
plt.scatter(X+1950, y, color='blue', \
    label='Data points')
plt.plot(X+1950, y_pred, color='red', \
    label='Huber Regressor')
plt.xlabel('X')
plt.ylabel('y')
plt.legend()
plt.title('Huber Regressor with Outliers')
plt.show()
```