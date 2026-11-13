previous two sections. A spatial pattern induced by exogenous processes is the function of other factors independent of the variable or characteristics of interest. For example, the precipitation pattern may be a function of altitude and distance from the sea. The spatial pattern of the plants may be response to soils, as they may only grow on a specific type of soil. The spatial distribution of wildlife animals may be restricted by or actively respond to environmental factors, such as rainfall, temperature or habitat type, which themselves are spatially autocorrelated. Such spatial patterns can be investigated and modelled by means of regression.

# Regression.

Regression is a statistical tool used to investigate and estimate the relationships among variables. It has been used as a major means of evaluating spatial relationships in order to explain the factors behind the observed spatial patterns. Traditional simple or multiple regression is used to explore, examine and model spatial relationships by assuming that the relationships are static and uniform across the entire study area. Geographically weighted regression takes into account spatial or regional variations of the relationships.

# 6.6.1 Simple Regression

**Simple regression** models relationships between two variables using the following linear equation:

$y = a + bx + \varepsilon$ (6.28)

In this regression equation, $y$ is the dependent variable, $x$ is the independent or explanatory variable, $a$ and $b$ are regression coefficients and $\varepsilon$ is the error term.

**Regression coefficients** represent the form and strength of relationship the explanatory variable has to the dependent variable. As a perfect linear relationship is unlikely to be encountered when investigating real-world phenomena, $\varepsilon$ always exists. The goal of simple regression analysis is to obtain estimates of the unknown parameters $a$ and $b$ and to assess the residuals. Once the regression coefficients are known, the values of $y$ can be estimated from the values of $x$ by:

\(\hat{y} = a + bx\) (6.29)

where \(\hat{y}\) is the estimated or predicated $y$ value. For example, suppose a regression of the annual rainfall ($y$) on the annual number of rain days ($x$) produced the following model:

\(\hat{y} = -9.172 + 0.4562x\) (6.30)

Assume the total number of rain days next year is forecast to be 50. Then the predicted annual rainfall is $-9.172 + 0.4562 \times 50 = 13.638$ in. If the number of rain days next year is revised to 70, then the annual rainfall estimate is $-9.172 + 0.4562 \times 70 = 22.762$ in.

Regression coefficients are estimated based on a collection of paired sample data of the dependent and explanatory variables. The form of relationship between two variables can be portrayed graphically by plotting the sample data (paired measurements of $x$ and $y$ for each observation) in a scatterplot, as shown in Figure 6.16. Each point in the plot represents an observation with an $x$ value and a $y$ value. Simple regression involves fitting a straight line to the set of the points so that the sum of