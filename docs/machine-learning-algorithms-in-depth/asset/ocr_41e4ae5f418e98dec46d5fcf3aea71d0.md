```
```python
R2 = X**2 + Y**2
inside = R2 < radius**2
outside = ~inside

samples = (2*radius)*(2*radius)*inside

I_hat = np.mean(samples)
pi_hat = I_hat/radius ** 2
pi_hat_se = np.std(samples)/np.sqrt(num_iter)
print("pi est: {} +/- {:f}".format(pi_hat, pi_hat_se))

plt.figure()
plt.scatter(X[inside],Y[inside], c='b', alpha=0.5)
plt.scatter(X[outside],Y[outside], c='r', alpha=0.5)
plt.show()

if __name__ == "__main__":
    pi_est()
```
```

If we execute the code, we get π = 3.1348 ± 0.0164, which is a relatively good result (within the error bounds). Try experimenting with different numbers of samples N to see how fast we converge to π as a function of N. Figure 2.5 shows the accepted Monte Carlo samples in blue, corresponding to samples inside the circle, and the rejected samples in red, corresponding to samples outside the circle.

![](bbox=[0.25, 0.5, 0.6, 0.7])

Figure 2.5 Monte Carlo samples used to estimate pi

In the preceding example, we assumed that samples came from a uniform distribution X, Y ~ Unif(−R, R). In the following section, we will look at simulating a stock price over different time horizons using the binomial tree model.

# 2.3 Binomial tree model

Now, let’s examine how Monte Carlo sampling can be used in finance. In a binomial tree model of a stock price, we assume that at each time step, the stock could be in either up or down states with unequal payoffs characteristic for a risky asset. Assuming the initial stock price at time t = 0 is $1, at the next time step t = 1, the price is u in the up state and d in the down state, with up-state transition probability p. A binomial tree