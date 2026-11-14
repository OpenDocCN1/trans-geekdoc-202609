```
31 # Apply the reordering index
32 y = np.take_along_axis(X, reorder_index, axis=1)
33
34 # Examine the results one matrix at a time
35 print(y[:, :, 0])
36 # array([[3, 1, 0, 4, 2],
37 #        [3, 5, 4, 1, 2],
38 #        [5, 2, 6, 3, 4],
39 #        [3, 5, 4, 7, 6]])
40 print(y[:, :, 1])
41 # array([[30, 10, 0, 40, 20],
42 #        [30, 50, 40, 10, 20],
43 #        [50, 20, 60, 30, 40],
44 #        [30, 50, 40, 70, 60]])
45 print(y[:, :, 2])
46 # array([[-1, -3, -4, 0, -2],
47 #        [-3, -1, -2, -5, -4],
48 #        [-3, -6, -2, -5, -4],
49 #        [-7, -5, -6, -3, -4]])
```

In this case, both axis=0 and axis=2 are treated as the batch dimensions. The input X can also be broadcasted to the indices at the singleton dimensions. For example,

```
1 import numpy as np
2
3 X = np.array([[0, 1, 2, 3, 4]])[:, :, None] # (1, 5, 1)
4 reorder_index = np.array([
5     [3, 1, 0, 4, 2],
6     [2, 4, 3, 0, 1],
7     [3, 0, 4, 1, 2],
8     [0, 2, 1, 4, 3],
9 ])[..., None] # (4, 5, 1)
10 # Apply the reordering index
11 y = np.take_along_axis(X, reorder_index, axis=1)
12 assert np.allclose(
13     y.shape,
14     (4, 5, 1)
15 )
16
17 assert np.allclose(
18     y,
19     np.array([[[3, 1, 0, 4, 2],
20                [2, 4, 3, 0, 1],
21                [3, 0, 4, 1, 2],
22                [0, 2, 1, 4, 3]]])[:, :, None]
23 )
```