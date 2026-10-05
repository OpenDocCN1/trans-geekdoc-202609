# 8.1.2 Advantages

Individual conditional expectation curves are **more intuitive to understand** than partial dependence plots. One line represents the predictions for one instance if we vary the feature of interest.

Unlike partial dependence plots, ICE curves can **uncover heterogeneous relationships.**

# 8.1.3 Disadvantages

ICE curves can **only display one feature** meaningfully, because two features would require the drawing of several overlapping surfaces and you would not see anything in the plot.

ICE curves suffer from the same problem as PDPs: If the feature of interest is correlated with the other features, then **some points in the lines might be invalid data points** according to the joint feature distribution.

If many ICE curves are drawn, the **plot can become overcrowded** and you will not see anything. The solution: Either add some transparency to the lines or draw only a sample of the lines.

In ICE plots it might not be easy to **see the average**. This has a simple solution: Combine individual conditional expectation curves with the partial dependence plot.

# 8.1.4 Software and Alternatives

ICE plots are implemented in the R packages iml (used for these examples), ICEbox², and pdp. Another R package that does something very similar to ICE is condvis. In Python, partial dependence plots are built into scikit-learn starting with version 0.24.0.

> ²Goldstein, Alex, Adam Kapelter, Justin Bleich, and Maintainer Adam Kapelter. “Package ‘ICEbox’” (2017).