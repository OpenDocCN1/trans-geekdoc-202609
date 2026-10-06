# The Practices of Machine Learning

(dark grey blocks), take this model and create predictions on the 1 holdout subset (light grey block). This gives us a first estimate of holdout performance, using a group of observations the model "did not see." In the second step, this procedure is repeated by selecting an additional 4 subsets to run the model and then creating predictions using the holdout subset (each holdout subset can only be used once). This is 3 more times, resulting in 5 estimates of model performance. These 5 metrics are aggregated to create a 5-fold CV metric. One point in this procedure is that reiterating, and is common to other forms of CV (and bootstrapping), while the model is run on the k-1 partitions of the dataset, it is not rerun on the holdout partition. Instead the model is kept fixed and to create predicted responses for the observations. Using the MSE as an example, this manifests itself as

```
$$MSE_{holdout} = \frac{1}{n} \sum_{i=1}^{n} (y_{holdout} - \hat{f}_{training}(x_{holdout}))^2, \quad (3.6)$
```

where n is the number of observations in the holdout partition, x and y are the values for observation i in the holdout sample, and $\hat{f}_{training}$ is the prediction from the model already trained on the training sample (e.g. k-1 partitions). We then have this estimate for each of the k holdout samples, we can then compute the k-fold MSE,

```
$$MSE_{k-fold} = \frac{1}{k} \sum_{i=1}^{k} (MSE_k). \quad (3.7)$
```

Common practice when using k-fold CV is to repeat the process, repeating the partitioning process can remove the potential for aberrant results due to chance. Specifically, repeated (i.e., 100) 10-fold cross-validation is often recommended (Borra & Di Ciaccio, 2010; Krastagic, Buturovic, Leahy, & Thomas, 2014; Kuhn & Johnson, 2013). However, one drawback of this approach is the increase in runtime, as even 10 repeats increases the amount of time by 10x.

# 3.5.2 Nested CV

Often in using resampling for comparing algorithms the same process is used for both model selection and assessment, with practitioners reporting the resampling based fit metric for the final model. Confating both sets of assessment can lead to overoptimistic estimates of model assessment (Bouleix & Strobl, 2009; Varma & Simon, 2006). Particularly when examining a larger number of models, there is insufficient randomness imputed