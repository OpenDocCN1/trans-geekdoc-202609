# CHAPTER 2

# Multivariate predictive modeling and validation

^aDepartment of Physical and Chemical Sciences, University of L'Aquila, Coppito, Italy
^bDepartment of Chemistry, University of Rome La Sapienza, Rome, Italy

Many problems in chemistry involve the prediction of one or more qualitative or quantitative properties based on the experimental data (Martens & Naes, 1991). Examples of such problems involve, instance, the possibility of predicting protein or lipid content in food matrices by NIR spectra or of diagnosing the onset of a disease through the MS or NMR analysis of serum samples. In the former case, the property to be predicted is of quantitative value, while in the latter, it is discrete (qualitative). This chapter presents the chemometric strategies most used to formulate predictive models, i.e., models that relate one or more dependent variables Y (qualitative or quantitative) to a set of independent variables X.

Irrespective of its specific characteristics, building a predictive model requires only that a relation between the X and the Y exists also, operationally, a reasonable mathematical formulation be postulated to express (or at least approximate) this relation:

```
$y = f(\mathbf{x})$
```

Here, it should be stressed that since the exact form of the function $f(\mathbf{x})$ is unknown, it has to be empirically estimated by making use of known data to approximate the functional relation in Eq. (2.1). Such estimation relies on the availability of a sufficient number of samples (which constitute the so-called training set), for which the values of both $\mathbf{x}$ and $y$ are known. Operationally, model building is accomplished by defining an explicit mathematical formulation of the function $f(\mathbf{x})$, which is expressed in terms of some adjustable parameters (model coefficients), whose values are estimated based on the training data. While these concepts are equally valid for all kinds of predictive models, the techniques used for dealing with quantitative (regression) or qualitative (classification) responses prevent specificities

Machine Learning and Pattern Recognition Methods in
Chemistry from Multivariate and Data Modeling
https://doi.org/10.1016/B978-0-323-90408-7.00011-0

Copyright © 2023 Elsevier Inc,
All rights reserved.

27