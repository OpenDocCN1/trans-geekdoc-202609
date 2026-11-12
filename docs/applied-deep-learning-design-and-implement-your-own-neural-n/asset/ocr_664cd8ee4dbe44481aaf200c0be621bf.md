```
for item in x:
    a.append(item)
return a
```

![](bbox=[0.25, 0.17, 0.77, 0.45])

Figure 3.47: Plot of a linear function in Python

# ## 2. Plot a sigmoid function in Python.

```
def linear(x):
return 1 / (1 + np.exp(-x))
plot(x)
```

```
import matplotlib.pyplot as plt
import numpy as np
import math
def sigmoid(x):
    a = []
    for item in x:
        a.append(1/(1+math.exp(-item)))
    return a
```