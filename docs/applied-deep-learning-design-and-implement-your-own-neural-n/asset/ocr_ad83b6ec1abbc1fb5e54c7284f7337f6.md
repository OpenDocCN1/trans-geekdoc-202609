The preceding equation represents that _a_ is more similar to _c_ than _b_. The value of the similarity measure varies from _0 to 1_. So, if two objects have a low or less similarity measure means they are not similar, and if the similarity measure value is greater or closer to 1, that means they are almost similar.

Now, there are certain mathematical measures where we estimate the similarity measures in the clustering process. Let us discuss some of them.

# Euclidean distance or L2 distance norm

Say the data set we are using is dense and continuous [0, 1..... , _n_]. In these types of cases, we use the Euclidean distance as a parameter here while doing the clustering.

Euclidean distance is defined as the length of the path connecting two points, say _p_ and _q_. Say we have the two points as given in _figure 7.27_:

![](bbox=[0.383, 0.402, 0.686, 0.572])

**Figure 7.27:** Euclidean distance metric

So, here we use Pythagoras’ theorem to calculate the Euclidean distance, which is given as follows:

```
d(x, y) = \sqrt{\sum_{i=1}^{N} (x_i - y_i)^2}
```