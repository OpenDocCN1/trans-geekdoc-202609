```
```python
plt.title("LR theta 12 norm")
plt.xlabel('iterations')
plt.ylabel('theta 12 norm')
#plt.savefig('../figures/lrsgd_theta_norm.png')
plt.show()

plt.figure()
plt.plot(self.eta)
plt.title("LR learning rate")
plt.xlabel('iterations')
plt.ylabel('learning rate')
#plt.savefig('../figures/lrsgd_learning_rate.png')
plt.show()

plt.figure()
x1 = np.linspace(np.min(X[:,0])-1,np.max(X[:, 0])+1,10)
plt.scatter(X[:,0], X[:,1])
plt.plot(x1, -(theta[0]/theta[1])*x1)
plt.title('LR decision boundary')
plt.grid(True)
plt.xlabel('X1')
plt.ylabel('X2')
#plt.savefig('../figures/lrsgd_clf.png')
plt.show()

if __name__ == "__main__":
    X, Y = generate_data()
    sgd = sgd lr()
    theta = sgd.fit(X,Y)
```
```

Figure 5.11 shows the stochastic nature of the loss function that decreases with the number of iterations as well as the decision boundary learned by our binary logistic regression.

![](bbox=[0.167, 0.636, 0.872, 0.831])

**Figure 5.11** SGD logistic regression: Cost (left) and decision boundary (right)