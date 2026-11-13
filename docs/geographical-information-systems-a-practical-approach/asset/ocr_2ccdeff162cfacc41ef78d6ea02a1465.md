![](bbox=[0.146, 0.092, 0.902, 0.446])

Figure 5.27 Rainfall surfaces interpolated by trend surfaces of different orders: (a) first-order, (b) second-order, (c) third-order and (d) fourth-order (using the same dataset and same legend as in Figure 5.25).

sample points compared with the rapid increase in number of coefficients attached to high-order polynomials. Once the coefficients have been estimated using the least-squares method described earlier, the polynomial function can be evaluated at any point within the area of interest. Because of the least-squares fitting procedure, no other polynomial equation of the same order can provide a better approximation of the data.

Trend surface interpolation creates a smooth surface, representing the global trend of the distribution of a variable. Therefore, it is often used to fit a surface to the sample points when the value of the variable changes slowly across the area. It is also used as a way of removing broad

features of the data prior to using some other interpolation methods. Low-order polynomials can be used to characterise slowly varying physical process, such as pollution and wind direction. However, the higher the order it is of the polynomial, the more difficult it is to ascribe physical meaning to it. The most common order of polynomials is 1–4. Furthermore, the interpolated surfaces are highly susceptible to outliers (that is, extremely high and low values), especially at the edges.

# 5.5.4 Spline

The spline method estimates values at unsampled locations using a mathematical function that minimises overall surface