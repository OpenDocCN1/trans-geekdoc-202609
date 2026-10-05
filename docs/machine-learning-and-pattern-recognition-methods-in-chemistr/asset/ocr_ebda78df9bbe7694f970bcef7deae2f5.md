Eq. (2.44) clearly shows the main disadvantage of LDA, i.e., the fact S is to be an invertible matrix. This condition is rarely met, in particular working with instrumental data, because, among the other constraints, it requires the number of the objects to be higher than the number of the variables; nevertheless, efficient alternatives have been proposed. By the discriminant approaches proposed to overcome this issue, partial least-squares discriminant analysis (PLS-DA) is probably one of the most commonly used and well-known approaches.

# 2.2 Partial least-squares discriminant analysis (PLS-DA)

One of the possible solutions conceived to overcome the invertibility issues associated with LDA is to include a feature reduction step prior to the application of this classifier. This can be achieved by exploiting a selective method (for instance, a stepwise procedure) before calculating the LDA model. Another alternative is the application of methods based on latent variables (for example, PCA), which compress the information into a restricted set of orthogonal features and make the calculation of LDA decision boundaries possible.

Eventually, PLS-DA exploits a further strategy; the classification problem is transformed into a regression one, which can be solved by PLS (Barker & Rayens, 2003; Sjöström, Wold, & Söderström, 1986; Stähle & Wold, 1987). This transition is made possible by the introduction of a dummy Y, i.e., a Y-response which binary codes the class-membership of training samples. The codification is easy: each sample is represented by a row-vectors made of zeros except for the column corresponding to its classmembership. For a three-class case, samples belonging to class A, class B, and class C can be represented by the row-vectors $Y_A^T = [1 0 0]$ and $Y_B^T = [0 1 0]$, respectively.

Once Y is created, the general regression equation (Eq. 2.6) can be solved by PLS and the calibration model build. This step includes the estimation of the regression coefficient matrix B, which allows the prediction of unknown samples. In this case, new observations can be collected in a novel data matrix $X_{new}$ and the response matrix $\hat{Y}_{new}$ estimated (as already described in Section 1.3) by:

```
$$\hat{Y}_{new} = X_{new} B \quad (2.45)$
```

Contrarily to the target responses Y, the predicted $\hat{Y}$ are not binary, but of continuous variables, and a classification rule has to