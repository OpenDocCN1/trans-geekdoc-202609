(1) Kernel mapping:
x → K(x_i, x) = exp( -||x_i - x||² / (2σ²) )

(2) Learn the decision function:
f(x) = sign( Σ_{i ∈ SV} α_i y_i exp( -||x - x_i||² / (2σ²) ) )

![](bbox=[0.15, 0.12, 0.88, 0.34])

Fig. 14.1: Support Vector Machines.

Non linear SVM also exists for regression problems.

```
%matplotlib inline
import warnings
warnings.filterwarnings(action='once')
```

```
import numpy as np
from sklearn.svm import SVC
from sklearn import datasets
import matplotlib.pyplot as plt

# dataset
X, y = datasets.make_classification(n_samples=10, n_features=2,n_redundant=0,
                                    n_classes=2,
                                    random_state=1,
                                    shuffle=False)
clf = SVC(kernel='rbf')#, gamma=1)
clf.fit(X, y)
print("#Errors: %i " % np.sum(y != clf.predict(X)))

clf.decision_function(X)

# Usefull internals:
# Array of support vectors
clf.support_vectors_

# indices of support vectors within original X
np.all(X[clf.support_,:] == clf.support_vectors_)
```

/home/edouard/anaconda3/lib/python3.6/site-packages/_pytest/fixtures.py:844:
DeprecationWarning: The convert argument is deprecated in favor of converter.
It will be removed after 2019/01.
    params = attr.ib(convert=attr.converters.optional(tuple))