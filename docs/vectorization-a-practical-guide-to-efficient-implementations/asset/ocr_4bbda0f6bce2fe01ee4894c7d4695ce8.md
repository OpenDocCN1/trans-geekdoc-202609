[..., -k]. Then, [..., ::-1] reverses the top-k indices so that it is now arranged from largest to smallest.

+   • Line 6: np.take_along_axis applies the sorting order obtained from top_indices to the input, along the last dimension.

However, this would involve sorting the entire sequence. The time complexity of this approach is O(n log n), where n is the size of the sequence. In contrast, another strategy to retrieve top-k values is using np.argpartition to return the unordered top-k values first, and then sort the top-k values and indices using np.argsort. Since np.argpartition runs in O(n) [Harris et al., 2023] time complexity, the overall time complexity is then O(n + k log k), where k << n.

```
import numpy as np

def top_k_argpartition(X, k=3):
    """Get top-k values and indices along the last dimension."""
    # Unsorted top k values and indices
    top_indices = np.argpartition(X, -k, axis=-1)[..., -k:]
    top_values = np.take_along_axis(X, top_indices, axis=-1)

    # Sort based on top_values
    indices = np.argsort(top_values, axis=-1)[..., ::-1]
    top_indices = np.take_along_axis(top_indices, indices, axis=-1)
    top_values = np.take_along_axis(top_values, indices, axis=-1)

    return top_values, top_indices

X = np.array([1, 3, 2, 5, 9, 8, 4])
top_values, top_indices = top_k_argpartition(X)
# top_values: array([9, 8, 5])
# top_indices: array([4, 5, 3])
```

+   • Line 6 partitions the array by the kth largest value. np.argpartition will get the indices of the array after the partitioning. Here, we use -k to specify the kth largest value instead of the kth smallest value. See Figure 10.1 for an illustration

![](bbox=[0.143, 0.69, 0.85, 0.77])

Figure 10.1. Schematic illustration of the effect of partitioning the array. The algorithm first determines the kth largest value as specified, which we denote as the "pivot" (as in quicksort). Then, it moves any value less than the pivot to the left of the pivot and moves any value greater than the pivot to the right of the pivot. As a result, all values to the left of the pivot are smaller than the pivot, and all values to the right of the pivot are greater than the pivot. Within the two partitions, however, the values are not ordered.