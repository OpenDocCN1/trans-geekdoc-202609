
By substituting $I^c$ and $I^v$, respectively, with $I_i^c$ and $I_i^v$ in equation (6.20), the z score can be obtained for significance testing of the calculated $I_i$.

A positive $I_i$ value suggests the presence of positive local spatial autocorrelation, indicating that feature $i$ has neighbouring features with similarly high or low attribute values; thus, feature $i$ is part of a cluster. A negative $I_i$ value indicates that a feature has neighbouring features with dissimilar values (that is, negative local spatial autocorrelation), and the feature is an outlier (for example, a location with high values surrounded by neighbours with low values). In either case, the $p$-value associated with $I_i$ must be smaller than the pre-specified significance level for the cluster or outlier to be considered statistically significant.

Figure 6.14 shows spatial clusters identified by applying the local Moran's $I$ tool in ArcGIS to the map in Figure 6.13. The spatial weights are defined on rook's case contiguity. Postcode area 3186 has a positive local Moran's $I$ value of 8.72 and a $p$-value of 0.00001, indicating that this postcode area is part of a spatial cluster of similar values, and it is statistically significant with a significance level $\alpha = 0.05$ (> the $p$-value). The positive local Moran's $I$ and a small $p$-value < 0.05 for postcode area 3981 suggest that it is also part of a significant spatial cluster of similar values at $\alpha = 0.05$. Postcode area 3186 is in a cluster of high aged population density, while postcode area 3981 is part of a cluster of low aged population density. Although postcode area 3799 has a positive local Moran’s \( I \) value, its associated \( p \)-value is greater than 0.05; thus, spatial clustering around the area is not statistically significant. Typically, GIS outputs a map resulting from the local Moran’s \( I \) test, which shows statistically significant (at \( \alpha = 0.05 \)) clusters of high values (HH), spatial clusters of low values (LL), spatial outliers in which a high value is surrounded mainly by low values (HL) and spatial outliers in which a low value is surrounded largely by high values (LH). In Figure 6.14, spatial clusters of HH and LL are detected, but no spatial outliers.

![](img/8aad3fa01ca9db86bd50bb2edb9a3134_325_0.png)

Figure 6.14 Spatial clusters of aged population in Melbourne identified using local Moran's I.

### 6.5.2 Getis–Ord \( G_i^* \) (Hotspot Analysis)

The Getis–Ord \( G_i^* \) **statistic**, or simply \( G_i^* \), is a \( z \) test statistic used to test for the detection of spatial clusters. Like local Moran’s \( I \), it enables us to detect spatial clusters that may not show up when using global spatial statistics. \( G_i^* \) for feature \( i \) is calculated as:

\( G_i^* = \frac{\sum_{j=1}^n \bar{w}_{ij}(d)x_j - \bar{x}\sum_{j=1}^n \bar{w}_{ij}(d)}{s\sqrt{\frac{n\sum_{j=1}^n[\bar{w}_{ij}(d)]^2 - [\sum_{j=1}^n \bar{w}_{ij}(d)]^2}{n-1}}} \) (6.27)

where \(\{w_{ij}\}\) is a symmetric 1 or 0 spatial weights matrix with 1s for all features within distance \( d \) of feature \( i \), including feature \( i \) itself, and 0s for all other features, \( x_j \) is the attribute value associated with feature \( j \) and \( \bar{x} \) and \( s \) are the mean and standard deviation of the attribute values, respectively (Ord and Getis 1995).

\( G_i^* \) tests whether feature \( i \) and its neighbouring features have higher- or lower-than-average values of a particular attribute or variable. A positive \( G_i^* \) value larger than the critical \( z \)-value at a specific significance level indicates that the feature is part of a spatial cluster of particularly high values, while a negative \( G_i^* \) value lower than the minus critical \( z \)-value suggests that the feature is located in a spatial cluster of particularly low values at the corresponding significance level. Therefore, given the set of features, \( G_i^* \) can be used to identify those clusters of features with values of a particular variable higher or lower in magnitude than it might be expected to find by random chance. The clusters of high values are called **hotspots**, and the clusters of low values are referred to as **cold spots**.

Figure 6.15 shows the hot and cold spots of aged population in Melbourne identified using \( G_i^* \) at \( \alpha = 0.05 \) based on the data in Figure 6.13. The distance \( d \) used to define the spatial weights was set as 5 km. The critical \( z \)-value at this significance level is 1.96 for hotspots and -1.96 for cold spots.

### Practical 6.6 See the Support Material

In this practical, you are going to learn how to use and interpret the local Moran’s \( I \) statistic in ArcGIS Pro or QGIS.

![](img/8aad3fa01ca9db86bd50bb2edb9a3134_327_0.png)

Figure 6.15 Hot and cold spots of aged population in Melbourne identified using G_i* at α = 0.05.

Case study 13 in Chapter 10 provides an example of the use of G_i* to identify hot-spots with high landscape values in the Murray River region of Victoria, Australia.

## 6.6 Modelling of Spatial Relationships

Spatial patterns result from either exogenous (induced) or endogenous (inherent) processes occurring in space and time. Spatial autocorrelation is largely an effect of endogenous processes. For instance, endogenous processes such as seed dispersal, gene flow and competition tend to make plants within patches resemble each other. Most geographical phenomena exhibit some degree of spatial autocorrelation, which can be measured using Moran's I and other statistics discussed in the previous two sections. A spatial pattern induced by exogenous processes is the function of other factors independent of the variable or characteristics of interest. For example, the precipitation pattern may be a function of altitude and distance from the sea. The spatial pattern of the plants may be response to soils, as they may only grow on a specific type of soil. The spatial distribution of wildlife animals may be restricted by or actively respond to environmental factors, such as rainfall, temperature or habitat type, which themselves are spatially autocorrelated. Such spatial patterns can be investigated and modelled by means of regression.

### Regression.

Regression is a statistical tool used to investigate and estimate the relationships among variables. It has been used as a major means of evaluating spatial relationships in order to explain the factors behind the observed spatial patterns. Traditional simple or multiple regression is used to explore, examine and model spatial relationships by assuming that the relationships are static and uniform across the entire study area. Geographically weighted regression takes into account spatial or regional variations of the relationships.

### 6.6.1 Simple Regression

**Simple regression** models relationships between two variables using the following linear equation:

$y = a + bx + \varepsilon$ (6.28)

In this regression equation, $y$ is the dependent variable, $x$ is the independent or explanatory variable, $a$ and $b$ are regression coefficients and $\varepsilon$ is the error term.

**Regression coefficients** represent the form and strength of relationship the explanatory variable has to the dependent variable. As a perfect linear relationship is unlikely to be encountered when investigating real-world phenomena, $\varepsilon$ always exists. The goal of simple regression analysis is to obtain estimates of the unknown parameters $a$ and $b$ and to assess the residuals. Once the regression coefficients are known, the values of $y$ can be estimated from the values of $x$ by:

\(\hat{y} = a + bx\) (6.29)

where \(\hat{y}\) is the estimated or predicted $y$ value. For example, suppose a regression of the annual rainfall ($y$) on the annual number of rain days ($x$) produced the following model:

\(\hat{y} = -9.172 + 0.4562x\) (6.30)

Assume the total number of rain days next year is forecast to be 50. Then the predicted annual rainfall is $-9.172 + 0.4562 \times 50 = 13.638$ in. If the number of rain days next year is revised to 70, then the annual rainfall estimate is $-9.172 + 0.4562 \times 70 = 22.762$ in.

Regression coefficients are estimated based on a collection of paired sample data of the dependent and explanatory variables. The form of relationship between two variables can be portrayed graphically by plotting the sample data (paired measurements of $x$ and $y$ for each observation) in a scatterplot, as shown in Figure 6.16. Each point in the plot represents an observation with an $x$ value and a $y$ value. Simple regression involves fitting a straight line to the set of the points so that the sum of
