
# APPENDIX: A PHASE TRANSITION IN THE DIFFUSION PROCESS

and the initialization condition

```
$$$p_t^{(0)} = 1-\epsilon/v, \quad (324)$$
$$p_t^{(L)} = 1/v. \quad (325)$$
```

From $p_t^{(0)}$ and $p_t^{(l)}$, at layer $l$, the average probability of the correct value $p_t^{(l)}$ is given by

```
$$$p_t^{(l)} = \frac{p_t^{(l-1)} + (1-p_t^{(l-1)})}{v-1} \quad (326)$$
```

### C.2.1.3 Validity of the mean-field theory

Due to the randomness of the production rules, the messages $v_i(x)$, $v_j(x)$ are random variables that depend on the specific realization of the rules. Their fluctuations are not captured by the averages computed in Equation 321, we observe that $p_t^{(l)}$ and $p_t^{(l)}$ capture the average behavior of the messages at layer $l$. In Figure 44, the values of $v_i^{(l)}(x)$ are reported on the bottom 5 levels of a Random Hierarchical Model with $L=10, s=2, v=3, m=8$, and noise level $\epsilon=0.5$. At each layer $l$, the index $i$ of the nodes from $s$ to $l$ and for each of them, there are $v=3$ messages $v_i^{(l)}$ for each entry of the alphabet. At layer $l=0$, the messages $v_i^{(0)}$ are initialized according to Equation 285. After one iteration, at layer $l=1$, we observe that the largest messages at each node, those corresponding to the most probable features $x_i$, are spread around some mean value that is captured by the theoretical prediction of Equation 321. We observe also for the upper layers, the average behavior of the largest messages is well captured by the theory.

The comparison between the theory and the BP algorithm for every $\epsilon$ is reported in Figure 45 and Figure 46. The upward iteration is reported in Figure 45 and shows an excellent agreement with the prediction of Equation 321. In particular, from the input layer $l=0$ to the class variable $l=L$ ($L=10$ in Figure 45), the messages for the most probable features show a sharper transition at a threshold value $\epsilon^*$, which corresponds to the phase transition of the theoretical iteration in Equation 305 when $L \to \infty$. The downward iteration in Figure 46 shows that the theory also captures the trend in $\epsilon$ of the downward messages. However, we observe that the messages have large fluctuations around their mean value. The reason for this behavior is that, in the Random Hierarchical Model, there is a number $m$ of synonyms $(x_1, \dots, x_s)$ that code for the higher level feature $y$. Therefore, having perfect information on $y$ and $x_2, \dots, x_s$ is not enough to perfectly reconstruct the value of $x_1$, thereby resulting in large fluctuations of the messages at small noise level $\epsilon$. This is different from the upward process where perfect information on $(x_1, \dots, x_n)$ allows the perfect reconstruction of $y$. As a result, the messages in the upward process are more concerned around their downward messages.

## C.3 MAPPING FROM TIME DIFFUSION TO E NOISE

In the diffusion process for the Robust Hierarchy Model defined in Section 4.4, the beliefs $v^{(0)}$ at the input vary stochastically in time, according to Equation 60. Instead, in the simplified model of noise considered in Section 4.5, these beliefs are fixed to two possible values (cf. Equation 72). To study whether the e-process is an effective approximation of the time diffusion process, we define an effective $\epsilon(t)$ depending on the reverse time of diffusion. At each input node $X_i^{(0)}$, we consider the upward messages $v_i^{(0)}(x)$ associated to the variables $x$ that are from the value of $X_i^{(0)}$ at time $t$. Denoting by $v_t$, we define

> $$\frac{\epsilon(t)}{v} = (v_t)$$

where the average $(\cdot)$ is performed over all the variables $i$ and the realizations of the dynamics. $\epsilon(t)$ increases exponentially in time, according to the noise schedule used in the diffusion process, as shown in the left panel of Figure 48. The probability of correct reconstruction of a given node in the diffusion process is reported as a function of $\epsilon(t)$ in the right panel of Figure 48. We observe that the curves for different layers have similar behavior to those of the e-process presented in Figure 10, confirming that the latter is an effective approximation of denoising.

![](img/86150bd6d44cb578b97e3eba954b7be2_228_0.png)

**Figure 44:** Upward messages for layers 0 to 4 for $\epsilon=0.5, v=3, s=2, L=10, sf=0.5$ messages, one per possible feature. At the input layer (layer 0), messages value $1-\epsilon=0.5$ or $\epsilon/s=0.5/32$. Going upward, the values of the messages fluctuate, they stayed separated into two groups: large messages (i.e., the most probable feature for each node) and small ones. The annealed mean-field computation (represented with a black line) captures the mean value of the large messages well (with dashed line).

![](img/86150bd6d44cb578b97e3eba954b7be2_229_0.png)

**Figure 45:** Largest upward messages, averaged for each layer, for varying $e$. Data for Random Hierarchical Model with $v=3, s=2, L=10, sf=0.5$. Each layer, indicated in the legend, is represented with a different color, and the black dashed line is the theoretical prediction from Equation 321, which shows excellent agreement with the experiments. The top left panel represents all the layers for comparison. Starting from $V_0 = 1-e$ at layer 0, we observe that the largest messages increase as we go to higher levels in the hierarchy only if $e$ is smaller than some threshold value. For $e$ larger than this threshold, instead, the messages become smaller, and it is not possible to reconstruct the highest levels in the hierarchy better than random chance.

![](img/86150bd6d44cb578b97e3eba954b7be2_230_0.png)

**Figure 46:** Largest downward BP messages, averaged for each layer, for varying $\epsilon$. For Random Hierarchical Model with same parameters as Figure 45. Each layer, indicated in the legend, is represented with a different color, while the theoretical prediction from Equation 321 is represented with the black dashed line. Still, we observe that the messages in the downward process have large fluctuations, as represented by their standard deviations, especially for small $\epsilon$. This captures the trend and becomes more accurate for increasing $\epsilon$. The top left panel represents all the layers for comparison. Starting from the initial $v_i = 1/v$ at the top layer (0), we observe that the largest downward messages increase as we go to lower layers in the hierarchy only if $\epsilon$ is smaller than some threshold value.

![](img/86150bd6d44cb578b97e3eba954b7be2_230_1.png)

**Figure 47:** largest marginal probabilities computed by BP, averaged for each layer, for varying $\epsilon$. For Random Hierarchical Model with same parameters as Figure 45. Each layer, indicated in the legend, is represented with a different color, while the black dashed line is the theoretical prediction from Equation 326, which shows excellent agreement with the experiments. The top left panel represents all the layers for comparison, where the inversion between the top and bottom layers can be observed (same curves as Figure 10 in the main text).

![](img/86150bd6d44cb578b97e3eba954b7be2_231_0.png)

**Figure 48:** Mapping between epsilon and the diffusion process.

From the average values of the beliefs at the variables running the diffusion process at time $t$, we compute an effective $e(t)$ as $e(t)/v = \langle v(x) \rangle$, over the $x$ values from the starting, averaging over the realizations of the diffusion process. **Right:** Probability of reconstructing the initial values for the nodes at a given layer during the diffusion process, using the effective $e(t)$ computed in the left panel. We observe that the shape of the curves with respect to the effective noise $e(t)$ is qualitatively similar to that of the simplified-$\epsilon$-process reported in Figure 10, supporting that it represents a good approximation for studying the diffusion process in time.

## C.4 HIDDEN ACTIVATIONS FOR DIFFERENT ARCHITECTURES

We perform the experiments described in Figure 4.2 using the internal representations of deep convolutional architectures trained for classification on ImageNet-tik. We consider the ResNet architecture [He+16] with varying width and depth: a ResNet 50 achieving 95.4% top-5 accuracy, a WideRes 50 having 95.8% top-5 accuracy, and a ResNet 152 having 96.0% top-5 accuracy. The results of the experiments performed with the hidden representations of these architectures are reported in Figure 49 and show the same qualitative behavior as the one observed for the ConvNeXt architecture in Figure 5: the cosine similarity exhibits a sharp transition in the logits, which it decays smoothly for hidden representations at early layers.

## C.5 BI-MODAL DISTRIBUTIONS

In this section, we study the forward-backward experiments discussed in the main text, focusing on a bi-modal distribution without hierarchical and compositional structure. We specifically consider a $d$-dimensional Gaussian mixture with an initial probability density given by:

```
$$q(\mathbf{x}_0) = \frac{1}{2(2\pi\sigma^2)^{d/2}} \left[ \exp\left( -\frac{(\mathbf{x}_0 - \mu)^T(\mathbf{x}_0 - \mu)}{2\sigma^2} \right) + \exp\left( -\frac{(\mathbf{x}_0 + \mu)^T(\mathbf{x}_0 + \mu)}{2\sigma^2} \right) \right].$$
```
