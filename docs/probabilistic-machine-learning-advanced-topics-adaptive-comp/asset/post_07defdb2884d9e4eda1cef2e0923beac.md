
If $\mathcal{D}^t$ is large enough, we can directly optimize this using standard empirical risk minimization (ERM). However, if $\mathcal{D}^t$ is small, we might want to use $\mathcal{D}^s$ somehow as a regularizer. This is called **transfer learning**, since we hope to "transfer knowledge" from $p$ to $q$. There are many approaches to transfer learning (see e.g., [Zhu+21] for a review). We briefly mention a few below.

## 19.5.1.1 Pre-train and fine-tune

The simplest and most widely used approach to transfer learning is the **pre-train and fine-tune** approach. We first fit a model to the source distribution by computing $f^s = \text{argmin}_f \hat{R}(f, \mathcal{D}^s)$. (Note that the source data may be unlabeled, in which case we can use self-supervised learning methods.) We then adapt the model to work on the target distribution by computing

\(f^t = \text{argmin}_f \hat{R}(f, \mathcal{D}^t) + \lambda ||f - f^s||\) (19.10)

where $||f - f^s||$ is some distance between the functions, and $\lambda \ge 0$ controls the degree of regularization. Since we assume that we have very few samples from the target distribution, we typically “freeze” most of the parameters of the source model. (This makes an implicit assumption that the features that are useful for the source distribution also work well for the target.) We can then solve Equation (19.10) by “chopping off the head” from $f^s$ and replacing it with a new linear layer, to map to the new set of labels for the target distribution, and then compute a new MAP estimate for the parameters on the target distribution. (We can also compute a prior for the parameters of the source model, and use it to compute a posterior for the parameters of the target model, as discussed in Section 17.2.3.)

This approach is very widely used in practice, since it is simple and effective. In particular, it is common to take a large pre-trained model, such as a transformer, that has been trained (often using self supervised learning, Section 32.3.3) on a lot of data, such as the entire web, and then to use this model as a feature extractor (see e.g., [Kol+20]). The features are fed to the downstream model, which may be a linear classifier or a shallow MLP, which is trained on the target distribution.

## 19.5.1.2 Prompt tuning (in-context learning)

Recently another approach to transfer learning has been developed, that leverages large models, such as transformers (Section 22.4), which are trained on massive web datasets, usually in an unsupervised way, and then adapted to a small, task-specific target distribution. The interesting thing about this approach is the parameters of the original model are not changed; instead, the model is simply “conditioned” on new training data, usually in the form of a text **prompt** $\boldsymbol{z}$. That is, we compute

\(f^t(x) = f^s(x \cup z)\) (19.11)

where we (manually or automatically) optimize $\boldsymbol{z}$ while keeping $f^s$ frozen. This approach is called **prompt tuning** or **in-context learning** (see e.g., [Liu+21a]), and is an instance of **few-shot learning** (see Figure 22.4 for an example).

Here $\boldsymbol{z}$ acts like a small training dataset, and $f^s$ uses attention (Section 16.2.7) to “look at” all its inputs, comparing $\boldsymbol{x}$ with the examples in $\boldsymbol{z}$, and uses this to make a prediction. This works because the text training data often has a similar hierarchical structure (see [Xie+22] for a Bayesian interpretation).

## 19.5.2 Weighted ERM for covariate shift

In this section we reconsider the risk minimization objective in Equation (19.8), but leverage unlabeled data from the target distribution to estimate it. If we make the covariate shift assumption (i.e., $q(\boldsymbol{x}, \boldsymbol{y}) = q(\boldsymbol{x})p(\boldsymbol{y}|\boldsymbol{x})$), then we have

$R(f, q) = \int q(\boldsymbol{x})q(\boldsymbol{y}|\boldsymbol{x})\ell(\boldsymbol{y}, f(\boldsymbol{x}))dxdy$
$= \int q(\boldsymbol{x})p(\boldsymbol{y}|\boldsymbol{x})\ell(\boldsymbol{y}, f(\boldsymbol{x}))dxdy$
$= \int \frac{q(\boldsymbol{x})}{p(\boldsymbol{x})}p(\boldsymbol{x})p(\boldsymbol{y}|\boldsymbol{x})\ell(\boldsymbol{y}, f(\boldsymbol{x}))dxdy$
$\approx \frac{1}{N} \sum_{(\boldsymbol{x}_n, \boldsymbol{y}_n) \in \mathcal{D}_L^t} w_n \ell(\boldsymbol{y}_n, f(\boldsymbol{x}_n))$

where the weights are given by the ratio

$w_n = w(\boldsymbol{x}_n) = \frac{q(\boldsymbol{x}_n)}{p(\boldsymbol{x}_n)}$

Thus we can solve the covariate shift problem by using **weighted ERM** [Shi00a; SKM07].

However, this raises two questions. First, why do we need to use this technique, since a discriminative model $p(\boldsymbol{y}|\boldsymbol{x})$ should work for any input $\boldsymbol{x}$, regardless of which distribution it comes from? Second, given that we do need to use this method, in practice how should we estimate the weights $w_n = w(\boldsymbol{x}_n) = \frac{q(\boldsymbol{x}_n)}{p(\boldsymbol{x}_n)}$? We discuss these issues below.

### 19.5.2.1 Why is covariate shift a problem for discriminative models?

For a discriminative model of the form $p(\boldsymbol{y}|\boldsymbol{x})$, it might seem that such a change in $p(\boldsymbol{x})$ will not affect the predictions. If the predictor $p(\boldsymbol{y}|\boldsymbol{x})$ is the correct model for all parts of the input space $\boldsymbol{x}$, then this conclusion is warranted. However, most models will only be accurate in certain parts of the input space. This is illustrated in Figure 19.10b, where we show that a linear model fit to the source distribution may perform much worse on the target distribution than a model that weights target points more heavily during training.

### 19.5.2.2 How should we estimate the ERM weights?

One approach to estimating the ERM weights $w_n = w(\boldsymbol{x}_n) = \frac{q(\boldsymbol{x}_n)}{p(\boldsymbol{x}_n)}$ is to learn a density model for the source and target. However, density estimation is difficult for high dimensional features. An alternative approach is to try to approximate the density ratio, by fitting a binary classifier to distinguish the two distributions, as discussed in Section 2.7.5. In particular, suppose we have an equal number of samples from $p(\boldsymbol{x})$ and $q(\boldsymbol{x})$. Let us label the first set with $c = -1$ and the second set with $c = 1$. Then we have

$p(c = 1|\boldsymbol{x}) = \frac{q(\boldsymbol{x})}{q(\boldsymbol{x}) + p(\boldsymbol{x})}$

![](img/ca72c1626f4850f058a9edc138c1ac73_772_0.png)

Figure 19.10: (a) Illustration of covariate shift. Light gray represents training distribution, dark gray represents test distribution. We see the test distribution has shifted to the right but the underlying input-output function is constant. (b) Dashed line: fitting a linear model across the full support of X. Solid black line: fitting the same model only on parts of input space that have high likelihood under the test distribution. From Figures 1–2 of [Sto09]. Used with kind permission of Amos Storkey.

and hence \(\frac{p(c=1|\boldsymbol{x})}{p(c=-1|\boldsymbol{x})} = \frac{q(\boldsymbol{x})}{p(\boldsymbol{x})}\). If the classifier has the form \(f(\boldsymbol{x}) = p(c=1|\boldsymbol{x}) = \sigma(h(\boldsymbol{x})) = \frac{1}{1+\exp(-h(\boldsymbol{x}))}\), where \(h(\boldsymbol{x})\) is the prediction function that returns the logits, then the importance weights are given by

\(w_n = \frac{1/(1+\exp(-h(\boldsymbol{x}_n)))}{\exp(-h(\boldsymbol{x}_n))/(1+\exp(-h(\boldsymbol{x}_n)))} = \exp(h(\boldsymbol{x}_n))\)

Of course this method requires that \(\boldsymbol{x}\) values that may occur in the test distribution should also be possible in the training distribution, i.e., \(q(\boldsymbol{x}) > 0 \Longrightarrow p(\boldsymbol{x}) > 0\). Hence there are no guarantees about this method being able to interpolate beyond the training distribution.

## 19.5.3 Unsupervised domain adaptation for covariate shift

We now turn to methods that only need access to unlabeled examples from the target distribution. The technique of **unsupervised domain adaptation** or **UDA** assumes access to a labeled dataset from the source distribution, \(\mathcal{D}_1 = \mathcal{D}_L^s \sim p(\boldsymbol{x}, \boldsymbol{y})\) and an unlabeled dataset from the target distribution, \(\mathcal{D}_2 = \mathcal{D}_L^t \sim q(\boldsymbol{x})\). It then uses the unlabeled target data to improve robustness or invariance of the predictor, rather than using a weighted ERM method.

There are many forms of UDA (see e.g., [KL21; CB20] for reviews). Here we just focus on one method, called **domain adversarial learning** [Gan+16a]. Let \(f_\boldsymbol{\alpha}: \mathcal{X}_1 \cup \mathcal{X}_2 \rightarrow \mathcal{H}\) be a feature extractor defined on the two input domains, let \(c_\boldsymbol{\beta}: \mathcal{H} \rightarrow \{1, 2\}\) be a classifier that maps from the feature space to the domain from which the input was taken, either domain 1 or 2 (source or target), and let \(g_\boldsymbol{\gamma}: \mathcal{H} \rightarrow \mathcal{Y}\) be a classifier that maps from the feature space to the label space. We want to train the feature extractor so that it cannot distinguish whether the input is coming from the source or target distribution; in this case, it will only be able to use features that are common to both domains. Hence we optimize

\(\min_\boldsymbol{\gamma} \max_{\boldsymbol{\alpha}, \boldsymbol{\beta}} \frac{1}{N_1 + N_2} \sum_{\boldsymbol{x}_n \in \mathcal{D}_1, \mathcal{D}_2} \ell(d_n, c_\boldsymbol{\beta}(f_\boldsymbol{\alpha}(\boldsymbol{x}_n))) + \frac{1}{N_1} \sum_{(\boldsymbol{x}_n, \boldsymbol{y}_n) \in \mathcal{D}_1} \ell(\boldsymbol{y}_n, g_\boldsymbol{\gamma}(f_\boldsymbol{\alpha}(\boldsymbol{x}_n)))\)

The objective in Equation (19.19) minimizes the loss on the desired task of classifying \(y\), but *maximizes*
