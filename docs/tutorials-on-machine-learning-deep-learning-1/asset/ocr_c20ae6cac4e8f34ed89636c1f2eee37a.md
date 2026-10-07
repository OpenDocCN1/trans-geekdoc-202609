# STEP 1: Choose the K of neighbors: K = 5

![](bbox=[0.115, 0.075333, 0.47725, 0.252333])

# STEP 2: Take the K=5 nearest neighbors of the new data point, according to the Euclidean distance

![](bbox=[0.573, 0.075333, 0.83525, 0.252333])

# STEP 3: Among these K neighbors, count the number of data points in each category

![](bbox=[0.115, 0.293333, 0.47725, 0.420333])

# STEP 4: Assign the new data point to the category where you counted the most neighbors

![](bbox=[0.573, 0.293333, 0.83525, 0.420333])

**How to select the value of K in the K-NN Algorithm?** Below some points to remember while selecting the value of K in the K-NN algorithm.

+   - There is **no particular way** to determine the best value for "K", so we need to **try some values** to find the best of them. the most **preferred**value for K is 5.
- A very low value for K such as K=1 or K=2, can be **noisy** and lead to the effects of **outliers** in the model.
- Large values for K are good, but it may find some difficulties.

# **Advantages of K-NN Algorithm:**

+   - It is simple to implement.
- It is robust to the noisy training data
- It can be more effective if the training data is large.

# **Disadvantages of K-NN Algorithm:**

+   - Always needs to determine the value of K which may be complex some.
- The computation cost is high because of calculating the distance between the data points for all training samples.

NOTES:

+   - K-Nearest is one of the simplest Machine Learning algorithms based on **Supervised Learning** technique.

+   - K-NN assumes the **similarity** between the **new case/data** and available cases and put the new case into the **category** that is most similar to the **available categories**.
- K-NN algorithm stores all the available data and classifies a new data point based on the **similarity**. This means when new data appears then it can be easily classified into a **well category** by using K-NN algorithm.

+   - K-NN can be used for **Regression** as well as **Classification** but mostly it is used for the **Classification** problems.

**Parametric Algorithm:** K-NN is a **non-parametric algorithm**, which means it **does not make any assumption** on underlying data.