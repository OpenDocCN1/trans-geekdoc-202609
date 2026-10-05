# Genetic-Epigenetic Interplay Discovery

However, the relationship between the independent variable $x$ and the dependent variable $y$ becomes nonlinear in Figure 4.4. When the $x$ variable is changed by one unit at three positions, the $y$ variable does not change proportionally in a constant. This means that the proportional and linear relationship between the $x$ variable and the $y$ variable is no longer valid in a nonlinear regression model. In other words, the relationship between variables in a nonlinear model will not be held as a constant.

Regression analysis has been widely used in pattern discovery for many decades. The earliest record of regression analysis in PubMed was a sampling research [Orcutt and Cochrane, 1949]. In spite of this, regression analysis still pays an important role for biological/medical pattern analysis [Kumaran, et al., 2020; Kwon, et al., 2020].

# 4.3 The ordinary linear regression analysis algorithm

The simplest analysis approach is the ordinary linear regression algorithm (OLR). Without using any constraint, the parameters of an OLR model are estimated using the simplest approach, i.e., the least squared error approach. The approach estimates model parameters through minimising the total regression error.

# 4.3.1 The least squared error approach

Establishing an OLR model requires the model parameters $(\alpha$ and $eta)$ to be estimated using the least squared error approach (LSE). In a regression model, an error is defined as the distance between an observed outcome $y$ and a predicted outcome $\hat{y}$ from a regression model. $\hat{y}$ is also called the regressed mean variable or the model output variable or the regression prediction variable. In order to use LSE to estimate model parameters, the property of regression errors should be introduced at first.

First, $\hat{y}$ is obtained or predicted from a regression model after the model parameters $(\alpha$ and $eta)$ have been accurately estimated. The distance between $\hat{y}$ and $y$ is named as the regression error, which is defined below, where the regressed mean function is as $\hat{y} = \alpha + eta x$,