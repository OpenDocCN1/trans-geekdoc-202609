+   - Line 73 converts the dense tensors (after shuffling, if needed) to sparse tensors. Still, the original concatenated dense tensors have zero entries, which become “gaps” when converted to dense tensors.
+   - Lines 76–81 implement indices that are used to left-align the sparse tensors, as we have seen in Chapter 8. The same indices can be applied to both `samples` and `binary_labels`, therefore, I opted to reimplement the logic rather than calling a preexisting function.
+   - Lines 82–86 create the `binary_labels` left-aligned sparse tensor to indicate which entries within the final `samples` tensor will be positive labels, and which ones will be negative samples. We determine the value of the label (1 or 0) based on the sign of the entries in `samples`.
+   - Lines 87–91 create the left-aligned `samples` tensor and convert the sampled class indices to positive values by taking the absolute value. See Figure 10.5 for an illustration.

Finally, we can verify the implementation by examining the sampling frequency of the negative samples via a simulation

```
from collections import Counter
import numpy as np

def simulate_gumbel_max(
    batch_size=1024,
    max_num_pos_samples=5,
    num_neg_samples=10,
    vocab_size=100,
    num_iter=100,
    vocab_freq=None,
):
    """“Get sampling frequency of each negative class.”"""
    """Initialize the counter"""
    neg_sample_freq = Counter()
    for _ in range(num_iter):
        true_labels = []
        # Generate positive samples iteratively
        for num_pos in np.random.choice(
            np.arange(1, max_num_pos_samples+1),
            size=batch_size,
            replace=True
        ):
            pos_samples = np.random.choice(
                np.arange(1, vocab_size+1),
                size=num_pos,
                replace=False,
            )
            true_labels.append(pos_samples)
        # Convert to left aligned sparse
        true_labels = tf.ragged.constant(
            true_labels, dtype=tf.int64
        ).to_sparse()
```