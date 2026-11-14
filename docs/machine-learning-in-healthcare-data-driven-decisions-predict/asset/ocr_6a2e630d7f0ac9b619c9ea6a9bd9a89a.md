![](bbox=[0.174, 0.098, 0.542, 0.695])

Step 9: Update predictions

\( y^{\hat{t}_i} = y^{\hat{t}_{(t-1)i}} + \eta \cdot T_t(x_i) \) (5)

Step 10: Apply sigmoid for classification output

\( p^{\hat{t}_i} = \frac{1}{1 + e^{-y^{\hat{t}_i}}} \) (6)