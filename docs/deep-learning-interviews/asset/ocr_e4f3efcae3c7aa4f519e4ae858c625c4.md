```
```
\operatorname {\mathrm {Bin}} (3 \mid 50 ; \theta)=\ %s
posterior_sub s({theta:0.5})
plt.plot(mus, (sp_lambdfy(theta,posterior))(mus),'r')
xlabel("$\ \theta$", size=22)
```
```

![](bbox=[0.28, 0.21, 0.76, 0.49])

# # References

+   1. J. Bradbury et al. JAX: composable transformations of NumPy programs. 2018 (cit. on pp. 123, 136).

+   2. W. K. Clifford. ‘Preliminary Sketch of Bi-quaternions’. In: Proceedings of the London Mathematical Society 4 (1873), pp. 381–95 (cit. on pp. 125, 138).

+   3. R. Frostig et al. JAX: Autograd and XLA. 2018 (cit. on p. 123).

+   4. A. Griewank, D. Juedes and J. Utke. ‘Algorithm 755; ADOL-C: a package for the automatic differentiation of algorithms written in C/C++’. In: ACM Transactions on Mathematical Software 22.2 (June 1996), pp. 131–167 (cit. on pp. 123, 125).

+   5. A. Griewank and A. Walther. Evaluating Derivatives: Principles and Techniques of Algorithmic Differentiation. Second. USA: Society for Industrial and Applied Mathematics, 2008 (cit. on pp. 123, 124).