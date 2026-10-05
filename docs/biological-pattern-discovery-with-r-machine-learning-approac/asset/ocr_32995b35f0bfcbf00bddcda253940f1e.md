# Biological Pattern Discovery with R

The following code was used for estimating the density function for the malignant tumours supposing the data was saved in a matrix x the malignant tumours were labelled by M in the class label x$class,

```
malignant=x$radius [which (xclass=='M')]
mu=mean(malignant)
sigma=sd(malignant)
y=dnorm(sort(malignant),mean=mu,sd=sigma)
hist(malignant,nclass=50,prob=TRUE)
lines(sort (malignant), y)
```

Here y a y-coordinate vector representing a density function estimated using the dnorm function. The histogram approach was used at first to generate a density function with the prob parameter switched on. Next a smooth density curve was added using the parametric density estimation approach. Figure 2.8 shows the densities of the malignant tumour radius and the benign tumour estimated using the above code.

![](bbox=[0.19, 0.478, 0.809, 0.658])

Figure 2.8. The densities of two types of tumours estimated using the parametric approach for the tumour radius of the breast cancer data. (a) The malignant tumour density. (b) The benign tumour density.

Using the dnorm function for the parametric density estimation is under the assumption that a data set follows a Gaussian distribution. The data interval of a Gaussian distribution is between $-\infty$ and $\infty$ comprising all real numbers. In fact, some feature of this breast cancer data will not be negative such as the tumour area. In order to estimate a better density for such a feature, the Gamma distribution can be used. The R function for estimating a Gamma density function for a data set is dgamma. The format