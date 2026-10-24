![](bbox=[0.28, 0.12, 0.73, 0.39])

Figure 3.5 The chi-square cumulative distribution function for degree of freedom of 1, 2, 3, 4, 5.

with a degree of freedom 2 can be estimated from Figure 3.5 to be about 4.6 (as indicated by the arrow pointing to the 90% quantile value), which is slightly smaller than the observed deviation (4.79). Therefore, the component instance is behaving abnormally for the level of significance of 0.1. However, we can reduce the significance level to make the anomaly detection less sensitive, for example α = 0.05. In this case, the threshold deviation for abnormality would be changed to about 6.0 (as indicated by the arrow pointing to the 95% quantile value), which would not trigger an anomaly report. The arrows point to the 90% and 95% quantile values of the chi-square distribution, respectively.

# 3.2.2 Path Shapes Modeling and Root Cause Analysis

A complementary fault detection method to component interactions monitoring is to monitor the shapes of the runtime paths of the end-user requests. While serving an end-user request, in general multiple component instances are involved, as shown in Figure 3.3. The shape of a runtime path is defined to be the ordered set of component classes instead of component instances for modeling purpose. A path shape is represented as a tree in which a node