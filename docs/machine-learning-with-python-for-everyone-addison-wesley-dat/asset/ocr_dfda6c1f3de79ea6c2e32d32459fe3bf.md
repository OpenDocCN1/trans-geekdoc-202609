clustering, which we used to gather similar visual words together into a common visual vocabulary, we were able to classify images.

# 14.4.2 Notes

If you'd like to see the exact stop words used by `sklearn`, go to the `sklearn` source code (for example, on github) and find the following file: `sklearn/feature_extraction/stop_words.py`.

If we cluster over all of the features, we will get a single group (one cluster label) for each example—a single categorical value. You could consider performing clustering on different subsets of features. Then, we might get out several new quasi-columns containing our clusters with respect to the different subsets. Conceptually, using a few of these columns—several different views of data—might get us better predictive power in a learning problem.

# Helpers

There are two quick utilities we made use of in our bag-of-visual-words system. The first is similar to Python's built-in `enumerate` which augments the elements of a Python iterable with their numeric indices. Our `enumerate_outer` takes an iterable of sequences—things with lengths—and adds numeric labels indicating the position in the outer sequence that the inner element came from. The second helper takes you from an iterable of example-like things with the same number of features to an `np.array` of those rows. `numpy` has a built-in `np.fromiter` but that only works when the output is a single conceptual column.

In [41]:

```
def enumerate_outer(outer_seq):
    '''repeat the outer idx based on len of inner'''
    return np.repeat(*zip(*enumerate(map(len, outer_seq))))

def np_array_fromiter(itr, shape, dtype=np.float64):
    '''helper since np.fromiter only does 1D'''
    arr = np.empty(shape, dtype=dtype)
    for idx, itm in enumerate(itr):
        arr[idx] = itm
    return arr
```

Here are some quick examples of using these helpers:

In [42]:

```
enumerate_outer([[0, 1], [10, 20, 30], [100, 200]])
```