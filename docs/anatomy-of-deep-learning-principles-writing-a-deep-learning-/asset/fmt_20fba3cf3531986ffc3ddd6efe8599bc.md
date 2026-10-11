
```python
import math
import matplotlib.pyplot as plt
import numpy as np

# if using a jupyter notebook
%matplotlib inline

def KL(mu1, sigma1, mu2, sigma2):
    return math.log(sigma2 / sigma1) + (sigma1**2 + (mu1 - mu2)**2) / (2 * sigma2**2) - 1 / 2

mus = np.arange(-12, 12, 0.1)
kl_values = [KL(mu, 2, 0, 2) for mu in mus]

plt.plot(mus, kl_values)
plt.xlabel('$\mu$')
plt.ylabel('KL')
plt.legend(['KL Value'], loc='upper center')
plt.show()
```
