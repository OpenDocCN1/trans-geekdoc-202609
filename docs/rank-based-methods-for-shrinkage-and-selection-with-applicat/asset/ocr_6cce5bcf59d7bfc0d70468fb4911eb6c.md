# 10

# High-Dimensional Models

# 10.1 Introduction

In this chapter, we consider robust rank-based high-dimensional data analysis, where the data may arise from biological, medical, social and economical studies. High-dimensional problems are typically characterized by \( p \gg n \), that is, the number of variables, \( p \), greatly exceeds the number of observations, \( n \). They also pertain to cases when \( p \approx n \). In either of these domains, the nature of the problem changes significantly. We cannot simply apply the techniques described in the previous chapters without modification. Instead, we must rely on the fact that there is a high degree of sparsity in the parameter set. Under this assumption, we can perform subset selection to identify variables that are clearly zero, those that are clearly non-zero and those that lie between these two sets. Due to complexity and model prediction in the presence of outliers, statistical theory is very important using rank-based methodology. This chapter is an extension of chapter 11 of Saleh et al. (2019), where they studied the \( p_n \)-dimensional ridge regression from a post-selection viewpoint. The notation of \( p_n \) is used to show that the dimension of the coefficient set depends on \( n \).

In the high-dimensional problem addressed in this chapter, we assume the model is sparse. As such we consider a multiple regression model for the ith response with covariate \( x_{ij} \) as follows,

\( y_i = \sum_{j=1}^{p_n} x_{ij} \beta_j^* + \varepsilon_i, 1 \le i \le n. \) (10.1.1)

In matrix form, the model is given by

\( \mathbf{y} = \mathbf{X} \boldsymbol{\rho}^* + \boldsymbol{\varepsilon}, \boldsymbol{\rho}^* = (\beta_1^*, ..., \beta_{p_n}^*)^\top, \) (10.1.2)