By contrast, assume now that the scatterplot of waiting duration and its associated residual plot are shown in Figure 10.7. We are not using the real data here, but simulated data. A quick at the scatterplot and regression line (left plot) could lead us to believe that the regression line is an appropriate summary of the relationship. But if we look carefully, you may notice that the residuals for duration are mostly below the regression line, residuals for values in the middle range of duration are mostly above the regression line, and residuals for large values of duration are again below the regression line.

This is the reason we prefer to use plots of residuals against fitted values (right plot) as we have removed the effect of the regression and can focus entirely on the residuals. The points clearly do not form a line, but rather a U-shaped curve. If this was the real data observed, using the linear regression with these data would produce results that are not valid or adequate.

![](bbox=[0.123, 0.347, 0.882, 0.622])

Figure 10.7: Example of a non-linear relationship.

Independence of the error terms and the response

Another assumption we want to check is the Independence of the response values. If they are not independent, some patterns of dependency may appear in the observed data.

The residuals could be used for this purpose too as they are a rough approximation of the error terms. If data was collected in a time sequence or other type of sequence, the residuals may also help us determine lack of independence by plotting the residuals against time. As it happens, the Old Faithful geyser eruption example does have a time component we can use: the old_faithful_2024 dataset contains the date variable. We show the plot of residuals against date (time):