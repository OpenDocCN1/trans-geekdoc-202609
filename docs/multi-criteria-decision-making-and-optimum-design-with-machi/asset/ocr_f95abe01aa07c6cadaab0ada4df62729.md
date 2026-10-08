# Selecting Optimal Electric Vehicle Charging Station Sites

# TABLE 10.1

# The Scale for the Pairwise Comparison of Criteria Weights

| Intensity of Importance | Definition | Explanation |
|---|---|---|
| 1 | Equally significant | The property is equally dependent on two factors. |
| 3 | Medium significant of thing to another | Perceptions as well as expertise on only slightly prefer alternative to the other. |
| 5 | Substantial or vital significance | Perceptions as well as expertise substantially prefer one alternative to the other. |
| 7 | Truly significant | An element is given strong preference, and its dominance is shown in action. |
| 9 | Very High significant | One of the strongest possible orders of confirmations that prefer one to the other. |
| 2,4,6,8 | Values in the middle of two consecutive opinions. | It is necessary to reconcile two opinions. |
| Reciprocals | If activity i is assigned with one nonzero number from 1 to 9 when differentiated from activity j, then j has the reciprocal value differentiated from i. | |
| Rational | Ratios appearing from forcing stability of awareness |

Source: Saaty (1980).

III. In the third step, the eigenvector of matrix B is calculated; the eigenvector is the average of each row element of matrix B and represented by Di. Obviously, Di is a column vector of size m x 1; it is calculated as Equation (10.3):

```
Di = \begin{bmatrix} \sum b_{b1} & \dots & \sum b_{1m} \ \vdots & \ddots & \vdots \ \sum b_{m1} & \dots & \sum b_{mm} \end{bmatrix} (10.3)
```

IV. In the fourth step, the eigenvalue of original matrix B is calculated, which is represented by λmax. To calculate λmax requires another column vector which we get by multiplying matrix B by D (Equations (10.4) and (10.5)):

```
B × D = \begin{bmatrix} b_{11} & b_{12} & \dots & b_{1m} \ \vdots & \ddots & \vdots \ b_{m1} & b_{m2} & \dots & b_{mm} \end{bmatrix} \times \begin{bmatrix} y_1 \ y_2 \ \vdots \ y_m \end{bmatrix} (10.4)
```