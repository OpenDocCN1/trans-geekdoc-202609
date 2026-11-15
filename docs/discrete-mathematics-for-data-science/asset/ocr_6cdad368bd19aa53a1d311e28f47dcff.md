predictors. VIFs range from 1 (no correlation) on up, with values between 4 and 10 being suspect and values greater than 10 generally indicative of multicollinearity.

Using the independent data fields, we find the VIF for every field \( i \) relative to every other field \( j \). The VIF calculation entails first obtaining the coefficient of determination \( R^2_{ij} \) between the two fields. Then, the VIF calculation is:

\( VIF_{ij} = 1/(1 - R^2_{ij}) \)

Despite a low VIF and low correlations between independent variables, multicollinearity may still be present in the form of joint dependencies. Testing for such requires the generation of synthetic data fields in the form of all pairs of dependent and joint-independent sets. That is, given a model of three independent variables:

\( y = x_1 + x_2 + x_3 \)

Based on the above model, a VIF would be computed for the following distinct pairs of independent variables:

\( (x_1, x_2), (x_1, x_3), (x_2, x_3) \)

With several data sets representing independent variables, one can manually remove factors and then retest the regression model. However, a large number of data sets may make this impractical, as when processing Big Data. Thus, it may be advisable to programmatically test randomly sampled fields while ensuring that the number of records always exceeds the number of fields.