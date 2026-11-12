where

```
\(K_3 = -\frac{4(q+2)(q+1)}{(p+q+2)(p-q)}\)
\(K_2 = \frac{K_3(p+q+4)(p-q-2)}{4(q+3)} + (q+2)\)
\(K_1 = \frac{(q+4)(q+3)}{2} - (q+4)K_2 + \frac{K_3(p+q+6)(p-q-4)}{8}\)
```

# 7.3.1.2 Recurrence Relation for Trigonometric Functions [39]

Evaluate \(\cos(q\theta)\) and \(\sin(q\theta)\) using recurrence relation and store them in two tables \(\cos \, t \,[M]\) and \(\sin \, t \,[M]\), where \(M\) is the total number of moments.

+   I. Let

```
\(r = (x_i^2 + y_k^2)^{1/2}, \, a = C_0 = \frac{x_i}{r}, \, b = S_0 = \frac{y_k}{r}, \, \cos[t][0] = a, \sin[t][0] = b\)
```

+   II. for \(q = 1 \text{ to } p_{\max}\)

```
C_q = aC_{q-1} - bS_{q-1}
S_q = aS_{q-1} + bC_{q-1}
\cos[t][q] = C_q \, \sin[t][q] = S_q
end for
```

The extra cost involved is the space required for the tables \(\sin \, t[p_{\max} + 1]\) and \(\cos \, t[p_{\max} + 1]\) with \(2(p_{\max} + 1)\) words.

# 7.3.2 Local Feature Extraction Using Hough Transform

As specified earlier, local features are extracted using Hough transform, the complete detail can be seen in Singh and Pooja [42–44], which are rotation, scale and, noise invariant.

# 7.3.3 Features Dimension

Since ZMs provide a large number of moments, optimal and effective set of features is an essential requirement for the satisfactory performance of a retrieval system. Very high or very low size of features set leads to over training or under training, respectively, which degrades the performance of the retrieval system. Normally higher is the order of moments, better should be the performance of ZMs features. However, the computation complexity increases rapidly and higher order moments lead to numerical instability and noise [44]. The selection of order \(p_{\max} = 12\) is a tradeoff between the computational complexity,