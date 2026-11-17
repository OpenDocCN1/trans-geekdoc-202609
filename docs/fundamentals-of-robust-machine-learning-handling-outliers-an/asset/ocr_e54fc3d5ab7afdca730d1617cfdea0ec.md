```
mini_cluster[j,l], marker='.', \\
color='black')
print("Total outliers:",count_outliers)
plt.title('MADmax Anomalies Detected', fontsize=15)
plt.show()
```

+   e) Use the following new data to rerun all three anomaly detection methods: DBSCAN, IF, and MADmax. Do not adjust the parameter values. Compare the results.

```
dataset = 2
m1 = [0,3]
m2 = [7,7]
m3 = [3,7]
cov1 = [[6, 2], [2, 6]]
cov2 = [[5, -1], [-1, 5]]
cov3 = [[7,1.0],[1.0,7]]
np.random.seed(np.random.randint(100))
x = np.random.multivariate_normal(m1, \\
cov1, size=(150,))
y = np.random.multivariate_normal(m2, \\
cov2, size=(300,))
z = np.random.multivariate_normal(m3, \\
cov3, size=(120,))
traininx = np.concatenate((x, y,z), axis=0)
trainx[0] = [20, -1]
trainx[1] = [21,-1]
trainx[2] = [-5,15]
trainx[3] = [15,15]
print("Re-run DBSCAN, IF and MADmax")
```

+   f) Use the following new data to rerun all three anomaly detection methods: DBSCAN, IF, and MADmax. Do not adjust the parameter values. Compare the results.

```
dataset = 3
m1 = [3,5]
m2 = [10,10]
m3 = [15,15]
cov1 = [[6, 3], [3, 3]]
cov2 = [[6, 3], [3, 3]]
cov3 = [[6, 3], [3, 3]]
np.random.seed(np.random.randint(100))
x = np.random.multivariate_normal(m1, \\
cov1, size=(1200,))
y = np.random.multivariate_normal(m2, \\
cov2, size=(1500,))
```