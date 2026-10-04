# 240 CHAPTER 6 Advanced feature processing methods

```
llvm_model.compile ()
X = model_pipeline("processing").transform(data)
llvm_model.predict (X)
```

Compiles the loaded LightGBM model into LLVM representation
Transforms the input data using the preprocessing steps defined in the pipeline

Also, in this case, the model is compiled and can run in a faster way inside a Python script. From a general point of view, leaves, though limited only to LightGBM, is a compiling solution that requires fewer settings and specifications from the user, resulting in a much simpler and straightforward usage.

# Summary

+   * Among processing problems, missing data is one of the most problematic. If your data is MCR or is just MAR because missing patterns are related to the other features, multivariate imputation can use the correlations among predictors in a dataset to impute missing values.
* XGBoost and LightGBM algorithms automatically handle missing data by assigning them to the split that minimizes the loss function in each split.
* When a categorical presents has high cardinality of its labels, you can use target encoding, which gained popularity in Kaggle competitions. Target encoding is a way to transform the values in a categorical feature into their corresponding expected values.
* PDP is a model-agnostic technique that explains how features and the target get related by means of the model you have trained. It is beneficial because it helps you better model the relationship between the predictive feature and the target if you notice it is nonlinear and complex.
* XGBFIR, to packages such as, can inform you about the most important interactions between predictive features.
* employing effective feature selection techniques, you can pinpoint and retain the most relevant features that contribute significantly to the machine learning process. Standard techniques to handle feature selection are stability selection based on L1 regularization for linear models, iterative selection, and Boruta for trees ensembles.

+   - Based on L1 regularization, stability selection aims to identify features that consistently appear as important across multiple subsets, indicating their robustness and reducing the likelihood of selecting features by chance or noise.
- Boruta is a procedure to determine if a feature is relevant in a machine learning problem by relying on the internal parameters of the model, such as coefficients in linear models or importance values based on gain, such as decision trees and their ensembles.