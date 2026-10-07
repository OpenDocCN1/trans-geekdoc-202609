# Mastering Classification Algorithms for Machine Learning

As these are many calculations, the following is a Python program to do all the math\and provide the result:

```
A = [4, 6, 3, 7, 2, 3, 4]
B = [2, 6, 9, 5, 12, 9, 7]
C = [4.45, 8.5, 9.5, 8.6, 12.2, 9.4, 8]

import pandas as pd

df = pd.DataFrame({'A':A, 'B':B, 'C':C})

b0 = 2
b1 = 2
b2 = 2
alpha = 0.001
threshold = 0

for c in range(1000):
    # Compute the Cost
    J = 0
    for i in range(len(df)):
        yhat = (b0 +
            (b1 * ((df.loc[i, 'A'])**2)) +
            (b2 * ((df.loc[i, 'B'])**2))
        )
        y = ((df.loc[i, 'C'])**2)
        J += ((yhat - y)**2)

J *= (1 / (len(df)))
print("Iteration: %d, Cost - %f % %f" % (c, J))
print("\tb0 - %f, b1 - %f, b2 - %f" % (b0, b1, b2))
if abs(J) < threshold:
    break

# Partial Derivatives
sumdiff = 0
```