
RBM is the energy-based model, and the state of a visible layer or hidden layer is treated as a stochastic variable. We’ll look at the equations in order. First of all, each visible unit is propagated to the hidden units throughout a network. At this time, each hidden unit takes a binary value based on the probability distribution generated in accordance with its propagated inputs:

$$p(h_j=1|v)=\sigma\left(\sum_{i=1}^{D} w_{ij} v_i + c_j\right)$$

Here, $c_j$ is the bias in a hidden layer and $\sigma$ denotes the sigmoid function.

This time, it was conversely propagated from a hidden layer to a visible layer through the same network. As in the previous case, each visible unit takes a binary value based on probability distribution generated in accordance with propagated values.

$$p(v_i=1|h)=\sigma\left(\sum_{j=1}^{M} w_{ij} h_j + b_i\right)$$

Here, $b_i$ is the bias of the visible layer. This value of visible units is expected to match the original input values. This means if $W$, the weight of the network as a model parameter, and $b$, $c$, the bias of a visible layer and a hidden layer, are shown as a vector parameter, $\theta$, it learns $\theta$ in order for the probability $p(v|\theta)$ that can be obtained above to get close to the distribution of $v$.

For this learning, the energy function, that is, the evaluation function, needs to be defined. The energy function is shown as follows:

$$E(v,h) = -b^T v - c^T h - h^T W v$$

$$= -\sum_{i=1}^{D} b_i v_i - \sum_{j=1}^{M} c_j h_j - \sum_{j=1}^{M}\sum_{i=1}^{D} h_j w_{ij} v_i$$

Also, the joint probability density function showing the demeanor of a network can be shown as follows:

$$p(v,h)=\frac{1}{Z}\exp(-E(v,h))$$

$$Z=\sum_{v,h}\exp(-E(v,h))$$

From the preceding formulas, the equations for the training of parameters will be determined. We can get the following equation:

$$p(v\mid\theta)=\sum_{h}p(v,h)=\frac{1}{Z}\sum_{h}\exp(-E(v,h))$$

Hence, the **log likelihood** can be shown as follows:

$$\ln L(\theta\mid v)=\ln p(v\mid\theta)$$

$$=\ln\left(\frac{1}{Z}\sum_{h}\exp(-E(v,h))\right)$$

$$=\ln\sum_{h}\exp(-E(v,h))-\ln\sum_{v,h}\exp(-E(v,h))$$

Then, we’ll calculate each gradient against the model parameter. The derivative can be calculated as follows:

$$\frac{\partial \ln L(\theta | v)}{\partial \theta} = \frac{\partial}{\partial \theta}\left( \ln \sum_h \exp(-E(v,h)) \right) - \frac{\partial}{\partial \theta}\left( \ln \sum_{v,h} \exp(-E(v,h)) \right)$$

$$= -\frac{1}{\sum_h \exp(-E(v,h))} \sum_h \exp(-E(v,h)) \frac{\partial E(v,h)}{\partial \theta}$$

$$= +\frac{1}{Z} \sum_{v,h} \exp(-E(v,h)) \frac{\partial E(v,h)}{\partial \theta}$$

$$= -\sum_h p(h|v) \frac{\partial E(v,h)}{\partial \theta} + \sum_{v,h} p(v,h) \frac{\partial E(v,h)}{\partial \theta}$$

Some equations in the middle are complicated, but it turns out to be simple in terms of the probability distribution of the model and the original data.

Therefore, the gradient of each parameter is shown as follows:

$$\frac{\partial \ln L(\theta | v)}{\partial w_{ij}} = -\sum_h p(h|v) \frac{\partial E(v,h)}{\partial w_{ij}} + \sum_{v,h} p(v,h) \frac{\partial E(v,h)}{\partial w_{ij}}$$

$$= \sum_h p(h|v) h_j v_i - \sum_v p(v) \sum_h p(h|v) h_j v_i$$

$$= p(H_j=1|v) v_i - \sum_v p(v) p(H_j=1|v) v_i$$

$$\frac{\partial \ln L(\theta | v)}{\partial b_i} = v_i - \sum_v p(v) v_i$$

$$\frac{\partial \ln L(\theta | v)}{\partial c_j} = p(H_j=1|v) - \sum_v p(v) p(H_j=1|v)$$

Now then, we could find the equation of the gradient, but a problem occurs when we try to apply this equation as it is. Think about the term of $\sum_v p(v)$. This term implies that we have to calculate the probability distribution for all the $\{0, 1\}$ patterns, which can be assumed as input data that includes patterns that don’t actually exist in the data.

We can easily imagine how this term can cause a combinatorial explosion, meaning we can’t solve it within a realistic time frame. To solve this problem, the method for approximating data using Gibbs sampling, called **Contrastive Divergence (CD)**, was introduced. Let’s look at this method now.

Here, $v^{(0)}$ is an input vector. Also, $v^{(k)}$ is an input (output) vector that can be obtained by sampling for k-times using this input vector.

Then, we get:

$$h_j^{(k)} \sim p\big(h_j \mid v^{(k)}\big)$$

$$v_i^{(k+1)} \sim p\big(v_i \mid h^{(k)}\big)$$

Hence, when approximating $p(v)$ after reiterating Gibbs sampling, the derivative of the log likelihood function can be represented as follows:

$$\frac{\partial \ln L(\theta \mid v)}{\partial \theta} = -\sum_h p(h \mid v)\frac{\partial E(v,h)}{\partial \theta} + \sum_{v,h} p(v,h)\frac{\partial E(v,h)}{\partial \theta}$$

$$\approx -\sum_h p(h \mid v^{(0)})\frac{\partial E(v^{(0)},h)}{\partial \theta} + \sum_h p(h \mid v^{(k)})\frac{\partial E(v^{(k)},h)}{\partial \theta}$$

Therefore, the model parameter can be shown as follows:

$$w_{ij}^{(\tau+1)} = w_{ij}^{(\tau)} + \eta\big(p\big(H_j = 1 \mid v^{(0)}\big)v_i^{(0)} - p\big(H_j = 1 \mid v^{(k)}\big)v_i^{(k)}\big)$$

$$b_i^{(\tau+1)} = b_i^{(\tau)} + \eta\big(v_i^{(0)} - v_i^{(k)}\big)$$

$$c_j^{(\tau+1)} = c_j^{(\tau)} + \eta\big(p\big(H_j = 1 \mid v^{(0)}\big) - p\big(H_j = 1 \mid v^{(k)}\big)\big)$$

Here, τ is the number of iterations and η is the learning rate. As shown in the preceding formulas, generally, CD that performs sampling k-times is shown as CD-k. It’s known that CD-1 is sufficient when applying the algorithm to realistic problems.

Now, let’s go through the implementation of RBM. The package structure is as shown in the following screenshot:

![](img/9315e45972ec0fbaf15f9144035bca79_100_0.png)

Let’s look through the RestrictedBoltzmannMachines.java file. Because the first part of the main method just defines the variables needed for a model and generates demo data, we won’t look at it here.

So, in the part where we generate an instance of a model, you may notice there are many null values in arguments:

```java
// construct RBM
RestrictedBoltzmannMachines nn = new
RestrictedBoltzmannMachines(nVisible, nHidden, null, null, null,
rng);
```

When you look at the constructor, you might know that these null values are the RBM’s weight matrix, bias of hidden units, and bias of visible units. We define arguments as null here because they are for DBN’s implementation. In the constructor, these are initialized as follows:

```java
if (W == null) {
    W = new double[nHidden][nVisible];
    double w_ = 1. / nVisible;

    for (int j = 0; j < nHidden; j++) {
        for (int i = 0; i < nVisible; i++) {
            W[j][i] = uniform(-w_, w_, rng);
        }
    }
}

if (hbias == null) {
    hbias = new double[nHidden];

    for (int j = 0; j < nHidden; j++) {
        hbias[j] = 0.;
    }
}

if (vbias == null) {
    vbias = new double[nVisible];

    for (int i = 0; i < nVisible; i++) {
        vbias[i] = 0.;
    }
}
```

The next step is training. CD-1 is applied for each mini-batch:

```java
// train with contrastive divergence
for (int epoch = 0; epoch < epochs; epoch++) {
    for (int batch = 0; batch < minibatch_N; batch++) {
        nn.contrastiveDivergence(train_X_minibatch[batch],
minibatchSize, learningRate, 1);
    }
    learningRate *= 0.995;
}
```

Now, let’s look into the essential point of RBM, the contrastiveDivergence method. CD-1 can obtain a sufficient solution when we actually run this program (and so we have k = 1 in the demo), but this method is defined to deal with CD-k as well:

```java
// CD-k : CD-1 is enough for sampling (i.e. k = 1)
sampleHgivenV(X[n], phMean_, phSample_);

for (int step = 0; step < k; step++) {

    // Gibbs sampling
    if (step == 0) {
        gibbsHVH(phSample_, nvMeans_, nvSamples_, nhMeans_,
nhSamples_);
    } else {
        gibbsHVH(nhSamples_, nvMeans_, nvSamples_, nhMeans_,
nhSamples_);
    }

}
```

It appears that two different types of method, sampleHgivenV and gibbsHVH, are used in CD-k, but when you look into gibbsHVH, you can see:

```java
public void gibbsHVH(int[] h0Sample, double[] nvMeans, int[]
nvSamples, double[] nhMeans, int[] nhSamples) {
    sampleVgivenH(h0Sample, nvMeans, nvSamples);
    sampleHgivenV(nvSamples, nhMeans, nhSamples);
}
```

So, CD-k consists of only two methods for sampling, sampleVgivenH and sampleHgivenV.

As the name of the method indicates, sampleHgivenV is the method that sets the probability distribution and sampling data generated in a hidden layer based on the given value of visible units and vice versa:

```java
public void sampleHgivenV(int[] v0Sample, double[] mean, int[] sample)
{

    for (int j = 0; j < nHidden; j++) {
        mean[j] = propup(v0Sample, W[j], hbias[j]);
        sample[j] = binomial(1, mean[j], rng);
    }

}
```
