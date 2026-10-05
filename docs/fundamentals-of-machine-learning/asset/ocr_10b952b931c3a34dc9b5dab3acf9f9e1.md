# 5.2 Error surface and challenges for gradient descent

It is instructive to look at the precise numerical results and details when implementing the whole procedure. We first link our common NumPy and plot routines and then define the data in the table in Fig. 5.1. This figure also shows plot of these data.

# 5.1 LinearRegression.ipynb (part 1)

```
import numpy as np
import matplotlib.pyplot as plt

size= np.array([937,1150,1170,1275,1410,1550,1730,1910])
price= np.array([187, 222, 330, 310, 290, 440, 600, 550, 600])

plt.plot(size,price,'o')
plt.xlabel('Size (Sqft)')
plt.ylabel('Price ($)')
plt.show()
```

![](bbox=[0.218, 0.396, 0.703, 0.688])

Fig. 5.3 (First attempt to implement a gradient descent learning rule for linear regression. We first set the starting values for the parameters $w_1$ and $w_2$, and we initialize an empty array to store the values of the loss function $L$ in each iteration. We also set the update (learning) rate $\alpha$ to a small value. We then perform ten iterations to update the parameters $w_1$ and $w_2$ with the gradient descent. Note that an index of an array with the value $-1$ indicates the last element in a Python array. The result of this program is in Fig. 5.2. The fit of the function shown in Fig. 5.2A does not look right at all. To see what is occurring is good to plot the values of the loss function as shown in Fig. 5.2B. As can be seen, the loss function gets bigger, not smaller as we would have expected, and the values itself are extremely large.