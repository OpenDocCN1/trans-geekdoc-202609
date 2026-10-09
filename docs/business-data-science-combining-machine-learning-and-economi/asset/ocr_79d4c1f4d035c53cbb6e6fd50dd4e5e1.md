There is no branddominicks indicator because you need only three variables to represent three categories: when both brandminute.maid and brandtropicana are zero, the intercept gives the value for Dominick's log sales at a log price of zero. Each factor's reference level is absorbed by the intercept and the other coefficients are “change relative to reference” (here, Dominick's). To check the reference level of your factors,3 type levels(myfactor). The first level is reference. To change this, you can do myfactor = relevel (myfactor, "myref").

The fitted values from the regression in Equation 2.12 are shown in Figure 2.5 alongside the original data. You see three lines shifted according to brand identity. At the same price, Tropicana sells more than Minute Maid, which in turn sells more than Dominick's. This makes sense: Tropicana is a luxury product that is preferable at the same price.

![](bbox=[0.335, 0.38, 0.705, 0.66])

FIGURE 2.5: OJ data and the fitted means for each brand under the model in Equation 2.12.