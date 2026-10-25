```
[4, 1],
[1, 6],
[2, 4],
[6, 2]
])
y = np.array([-1,-1,1,1,1])
clf = LogisticRegression(random_state=0).fit(X, y)
pred=clf.predict([[ 4,1],[1,6] ]) # predict 2 examples with feature values [4,1] and [1,6]
print('Prediction=',pred)
Output:
Prediction= [-1 1]
```

Example using Decision Tree algorithm:

```
import numpy as np
from sklearn.tree import DecisionTreeClassifier
X = np.array([
[-2, 4],
[4, 1],
[1, 6],
[2, 4],
[6, 2]
])
y = np.array([-1,-1,1,1,1])
clf = DecisionTreeClassifier(random_state=0)
clf.fit(X, y)
pred=clf.predict([[ -2,4],[4,1], [1,6] ]) # predict 3 examples with feature values [-2,4], [4,1] and [1,6]
print('Prediction=',pred)
Output:
Prediction= [-1 -1 1]
```

Example using Support Vector Machine algorithm:

```
from sklearn.svm import SVC
import numpy as np
X = np.array([
[-2, 4],
[4, 1],
[1, 6],
[2, 4],
[6, 2]
])
y = np.array([-1,-1,1,1,1])
clf = SVC(random_state=56)
```