# # Hinge Loss

$$\text{argmin}_{w} ||w||^2_{	ext{regularization}} + C \sum_{i=1}^{N} \max(0, 1 - y_i f(oldsymbol{x}_i))_{	ext{loss function}}$

**Points are in 3 categories:**

+   * $y_i f(oldsymbol{x}_i) > 1$ : Point outside margin, no contribution to loss
* $y_i f(oldsymbol{x}_i) = 1$ : Point is on the margin, no contribution to loss as in hard margin
* $y_i f(oldsymbol{x}_i) \le 1$ : Point violates the margin, contributes to loss

![](bbox=[0.537, 0.305, 0.973, 0.814])