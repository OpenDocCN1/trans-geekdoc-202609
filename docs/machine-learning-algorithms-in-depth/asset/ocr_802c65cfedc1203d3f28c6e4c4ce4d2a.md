```
self.feature_idx = 0
self.threshold = 0
self.left = None
self.right = None

class DecisionTreeClassifier():
    def __init__(self, max_depth = None):
        self.max_depth = max_depth

    def best_split(self, X_train, y_train):
        m = y_train.size
        if (m <= 1):
            return None, None

        mk = [np.sum(y_train == k) for k in range(self.num_classes)]

        best_gini = 1.0 - sum((n / m) ** 2 for n in mk)
        best_idx, best_thr = None, None

        #iterate over all features
        for idx in range(self.num_features):

            thresholds, classes = zip(*sorted(zip(X[:, idx], y)))

            num_left = [0]*self.num_classes
            num_right = mk.copy()

            for i in range(1, m):
                k = classes[i-1]

                num_left[k] += 1
                num_right[k] -= 1

                gini_left = 1.0 - sum(
                    (num_left[x] / i) ** 2 for x in range(self.num_classes)
                )

                gini_right = 1.0 - sum(
                    (num_right[x] / (m - i)) ** 2 for x in
                    range(self.num_classes)
                )

                gini = (i * gini_left + (m - i) * gini_right) / m

                if thresholds[i] == thresholds[i - 1]:
                    continue

                if (gini < best_gini):
                    best_gini = gini
                    best_idx = idx
                    best_thr = (thresholds[i] + thresholds[i - 1]) / 2
```

Best threshold to split on

idx of the feature to split on

Left subtree pointer

Right subtree pointer

Number of points of class k

Gini of the current node

Sorts data along a selected feature

Iterate over all possible split positions

Midpoint