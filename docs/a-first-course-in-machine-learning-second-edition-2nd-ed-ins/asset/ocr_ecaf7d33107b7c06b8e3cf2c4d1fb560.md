```
```matlab
% Note that the non log value may be numerically instable.
ml(i) = exp(logml(i));
end
```
```

EX 3.12. Assuming **w** is fixed, and the following inverse gamma prior on σ²:

$$p(\sigma^2\mid\alpha,\beta)=\frac{\beta^\alpha}{\Gamma(\alpha)}(\sigma^2)^{-\alpha-1}\exp\left\{-\frac{\beta}{\sigma^2}\right\}.$$

The likelihood is the standard Gaussian likelihood:

$$p(\mathbf{t}\mid\mathbf{w},\mathbf{X},\sigma^2)=\frac{1}{(2\pi)^{N/2}(\sigma^2)^{N/2}}\exp\left\{-\frac{1}{2\sigma^2}(\mathbf{t}-\mathbf{Xw})^{\mathsf T}(\mathbf{t}-\mathbf{Xw})\right\}.$$

The posterior density over σ² is therefore proportional to the product of these two densities. Collecting similar terms:

$$p(\sigma^2\mid\mathbf{w},\mathbf{X},\alpha,\beta)\propto(\sigma^2)^{-\alpha-N/2-1}\exp\left\{-\frac{1}{\sigma^2}\left(\beta+\frac{1}{2}(\mathbf{t}-\mathbf{Xw})^{\mathsf T}(\mathbf{t}-\mathbf{Xw})\right)\right\}.$$

This is another inverse gamma with parameters α* and β* given by:

$$\alpha^*=\alpha+\frac{N}{2}$$
$$\beta^*=\beta+\frac{1}{2}(\mathbf{t}-\mathbf{Xw})^{\mathsf T}(\mathbf{t}-\mathbf{Xw}).$$