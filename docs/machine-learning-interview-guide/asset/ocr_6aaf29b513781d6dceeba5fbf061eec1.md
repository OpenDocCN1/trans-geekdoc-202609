+   ○ **Addressing**: It is recommended to include interaction terms in your analysis or use a technique where the interaction terms are taken care of by the ML algorithms.
+   
+   - **Assumption of independence of errors**: Also, it assumes that errors are independent, which can be incorrect in time series or spatial data. We can address it by:
+     ○ **Addressing**: If core and shell variables are temporal or spatial variables, then address the temporal or spatial autocorrelation, or use models that have been devised for such structures.
+   
+   - **Difficulty with non-linear decision boundaries**: In feature space, logistic regression models form linear decision boundaries. We can address it by:
+     ○ **Addressing**: For more complex problems, use **support vector machines** (**SVMs**) or decision tre3es to find non-linear decision boundaries.
+   
+   - **Sensitive to collinearity**: Multicollinearity among the predictor variables can be a major influence to logistic regression. We can address it by:
+     ○ **Addressing**: Check for multicollinearity and perhaps solve it through the deletion of a variable thought to be collinear or using some techniques of regularization.
+   
+   - **Limited expressiveness for complex patterns**: Logistic regression itself might not be as good as flexible levels of the random components in terms of detecting patterns or interactions. We can address it by:
+     ○ **Addressing**: One may consider taking advantage of a more complex ensemble of methods or deep