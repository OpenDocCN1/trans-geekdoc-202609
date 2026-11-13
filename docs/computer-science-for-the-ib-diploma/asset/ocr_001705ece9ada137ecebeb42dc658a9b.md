```
np.random.seed(42)
# Students who spend little time but perform variably
group1 = np.random.normal(loc=[5, 60], scale=[2, 10], size=(50, 2))
# Students who spend a moderate amount of time and perform moderately
group2 = np.random.normal(loc=[10, 75], scale=[2, 5], size=(50, 2))
# Students who spend a lot of time and perform well
group3 = np.random.normal(loc=[15, 90], scale=[2, 5], size=(50, 2))
# Combine the groups into a single data set
data = np.vstack([group1, group2, group3])
# Apply k-means clustering
kmeans = KMeans(n_clusters=3, random_state=42)
kmeans.fit(data)
labels = kmeans.labels_
# Plot results
plt.figure(figsize=(10, 6))
colors = ["red", "green", "blue"]
for i in range(3):
    plt.scatter(data[labels == i, 0], data[labels == i, 1], color=colors[i],
                label=f"Cluster {i+1}")
plt.title("Cluster of Students Based on Study Habits and Test Performance")
plt.xlabel("Hours Spent on Homework per Week")
plt.ylabel("Test Performance (%)")
plt.legend()
plt.grid(True)
plt.show()
```

# Common mistake

Assuming clusters are globular; k-means does not work well with non-spherical clusters.

# See also

Reference the scikit-learn documentation for k-means clustering by searching online for scikit-learn's section 2.3.2 "K-means" (https://scikit-learn.org/stable/modules/clustering.html#k-means).

# Spectral clustering

![](bbox=[0.123, 0.692, 0.488, 0.858])

Spectral clustering is another technique that is useful where clusters are not linearly separable. To classify any new data point, it will look at where the new point fits best among the groups already made, like finding which circle of friends a new student would fit into at school.

Spectral clustering