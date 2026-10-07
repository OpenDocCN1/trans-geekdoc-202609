The segments can be assigned to the Customer as has been assigned by the Model:

dfCustomerDF['Segment'] = yPredLiveValue

dfCustomerDF.head()

| CustomerID | Frequency | MonetaryValue | Recency | Segment |
|---|---|---|---|--|
| 0 | 12347.0 | 218.20 | 2 | 0 |
| 1 | 12348.0 | 1 | 41.76 | 318 | 10 |
| 2 | 12349.0 | 5 | 112.54 | 18 | 0 |
| 3 | 12353.0 | 2 | 59.70 | 204 | 1 |
| 4 | 12354.0 | 3 | 41.35 | 232 | 1 |

Lastly, we can visualize the Customer Segments of the live data:

```
import numpy as np

# Fixing random state for reproducibility
np.random.seed(19680801)

fig = plt.figure(figsize=(15, 10))
ax = fig.add_subplot(projection = '3d')

xs = dfCustomerDF.Recency
ys = dfCustomerDF.Frequency
zs = dfCustomerDF.MonetaryValue
ax.scatter(xs, ys, zs, marker = 'o', c = dfCustomerDF.Segment)

ax.set_xlabel('Recency')
ax.set_ylabel('Frequency')
ax.set_zlabel('Monetary Value')

plt.show()
```