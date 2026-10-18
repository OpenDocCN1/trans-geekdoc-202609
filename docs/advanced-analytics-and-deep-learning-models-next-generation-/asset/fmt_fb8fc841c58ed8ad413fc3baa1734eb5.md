
From [28], the default values are `ρ1 (β1)` = `0.9` and `ρ2 (β2)` = `0.999` and `δ` = `10^(−8)`. Adam works quite well in DL scenarios and is one of the most favored adaptive learning method algorithms.

## Advantages of Adam

1. (i) No manual tuning required for learning rate and is straight forward as no modifications (alternations) needed to rescale gradients.
2. (ii) Due to less “on-board” memory requirements, algorithm is proficient.
3. (iii) Suitable for gradients having noisy and meagreness (sparsity) characteristics.

### 11.3.4 AdaMax

Extending Adam algorithm with infinity norm yields another variant, known as AdaMax [28]. The idea borrowed here is that, as Adam algorithm updates individual weights with respect to inversely proportional to L[2] norm, this technique is more generalized with Lp norm taken for updating.

Here, at time step “`t`”, we calculate gradient with respect to stochastic way for biased first moment via training infinity norm. Subsequently, the parameters are updated according to Equation (10.12):

(11.12)![](images/eq11-12.jpg)

The basic advantage of using AdaMax is that we need not to make correcting the values of initialization bias and parameter updates a much easier bound in comparison to Adam [28, 29].

### 11.3.5 AMSGrad

In the progression pipeline, can we a technique where the exponential moving averages promises convergence as one of the features? The expected answer is: `yes` and this is exactly what AMSGrad technique stands for [30]. It combines the features of Adam and RMS Prop together and in the present time getting quite a bit of attention in DL scenarios. As noticed from the previous discussions, the first and second order moments variables are modified as per Equation (10.13):

(11.13)![](images/eq11-13.jpg)

The fundamental differentiation from Adam algorithm is as per Equation (10.14):

(11.14)![](images/eq11-14.jpg)

Noting that, it keeps the maximum of all `u[t]` until present time step and takes this value for normalizing averages successively instead of `u[t]` as their counterpart in Adam. By accomplishing this way, `AMSGrad` achieves a non-increasing step size and the parameters are revised as per (14). The most noticeable feature is that `AMSGrad` neither way decreases nor increases the learning rate. In addition to this, it reduces `u[t]`, which guides to non-decreasing rate in the event when gradient is huge in future expected iterations.

## 11.4 Recent Optimizers in the Pipeline

In the recent past, many things in the optimization research have been undertaken by many practitioners and academicians. The research community in ML and DL are striving for more with better parameter tuning and exponential decay rates and using state-of-the-art technology to improve the performance on CNN, GAN, RNN, and other datasets. Here, we enlist a few recent optimizers with different blends which they exhibit close relationships with the optimizers presented so far. It is worth to be aware on this emerging field of research where lots of floruit ideas are taking new heights with statistical techniques [31].

### 11.4.1 EVE

There are two learning rates of paramount interest as depicted in [Figure 11.4](#c11.xhtml#fig11-4) ([Section 11.4](#c11.xhtml#sec11-4)), and these influence the convergence and other virtues of optimizer. Recapturing the thinking toward this, we can have the adaptive gradient feature of SGD where the intended these is well suited too. So, this one is cited as modification of Adam optimizer with coefficient confining two themes—firstly adapting the learning rate locally for each parameter and secondly combining all parameters together and performing an update globally. This sounds great! And in fact, it has shown to be outperforming Adam and others while training deep neural network (DNN)–like CNN for classification of pictures (photographs) and RNN for language translation task [32]. It seems as though a companion of `Adam`— as name suggests.

### 11.4.2 RAdam

The problem of adaptive learning rate and its big variance is usually noticed in the early stage of training the network and the idea of “`warmup`” works as a supplement in order to reduce the variance. The term “`warmup`” step is just a parameter used to lower the learning rate to reduce impact of model deviation from learning on new data suddenly. This implies that we can use a very low learning rate for a set number of training steps, i.e., “`warmup` `steps`”. Afterward, we use our “`regular`” learning rate or better known as “`learning rate scheduler`”. We can also gradually increase your learning rate over the number of warmup steps.

The proposed `R`ectified `Adam` (`RAdam`) is a modification by introducing a term to rectify the variance of the adaptive learning rate. The experimental results on image classification, language modeling, and neural machine translation verify our intuition and demonstrate the efficacy of this new variant [33, 34].

### 11.4.3 MAS^([1](#c11.xhtml#foot1)) (Mixing ADAM and SGD)

Another variant that join together Adam and SGD by weighing the contributions collectively with the task of regular (constant) weights and exploit them at the same time by taking the best of them. This intuitive blending idea is illustrated in [Figure 11.6](#c11.xhtml#fig11-6) with a side caption therein. Recently, various demonstrations are cited with CNN DNN incorporating different images and the conventional classification of text data with MAS optimizer and cited that it produced better results than their single SGD or ADAM counterpart optimizers individually [35].

### 11.4.4 Lottery Ticket Hypothesis

From the passion of gambling world, the inspiration is to select (get) a ticket whose chance of winning is highest! In the same way, the training of DL models is often compared with lottery to buy every possible ticket. However, if we know the winning process, then it seems that we can make a prudence choice about selection process. By the same token, in DL models, the training processes produce large structures of inter-connections of NN equivalent to a large container of lottery tickets. In this hypothesis, the model undergoes optimization techniques-like pruning that remove unnecessary weights from NN in order reduce model size without compromising the performance. Thus, this is, in turn, equivalent to searching of winning tickets from the container leaving the rest. Such pruning process produces structures which are almost 90% smaller than the original NN structure [34]. This idea leads to the hypothesis that a large NN contains a smaller sub-network that, if trained properly, will attain a similar accuracy in counterpart.

![Figure 11.6 A MAS mixing logo.](images/fig11-6.jpg)

[**Figure 11.6**](#c11.xhtml#rfig11-6) A MAS mixing logo.

Thus, looking at the brevity of this hypothesis, it opens more fronts for understanding and research to become one of the most important DL fields as it challenges the conventional wisdom in DL network training. For more insightfulness, one can refer to [33–36].

## 11.5 Experiment and Results

### 11.5.1 Web Resource

`https://scikit-learn.org/stable/modules/generated/sklearn.datasets.make_blobs.html`
