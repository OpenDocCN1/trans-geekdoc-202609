
## 6.3 RESULTS

field Gaussian distributions. We evaluate the complementary deep ensembles technique (Lakshminarayanan et al., 2017) for all methods.

### 6.3.1 Main results

We start our analysis by comparing the predictive uncertainty of 2-layer models with 32 latent variables per layer. In figure 6.4 we visualize the risk/coverage trade-off achieved using the predicted uncertainty as a selective threshold, and present coverage results in table 6.1. Overall, we find that SQUAD performs significantly better than plain MLPs and deep Gaussian IB models, and quantitatively attribute this to the increased flexibility of the multinomial distribution. 

Compared to a MCDCDropout model with a similar number of weights, SQUAD appears to have a slight |though not significant| advantage, despite the strong quantization scheme, especially at low risk guarantees. Deep ensembles improves results for all methods, which fits the hypothesis that ensembles integrate over a form of weight uncertainty. When comparing the optimal hyperparameters found for fashionMNIST on the similar notMNIST dataset, we find that SQUAD shows strong performance, as shown in table 6.2. This provides some evidence despite the increase in number of hyperparameters in SQUAD, the optimal settings are more robust to a change in the data distribution.

### 6.3.2 Natural Images

To explore larger models trained on natural image datasets, we re-tune hyperparameters on 256-latent 2-layer models over 100 TPE evaluations. As SVHN contains natural images in color, we anticipate a need for a higher amount of information per variable. We thus explore the effect of the matrix-factorized variant.

As shown in table 6.3, SQUAD-factorized outperforms the non-factorized variant. Considering the computational cost at the optimum of a 4-neuron factorization ($B = 4$) with $C=37$ quantization bins, the model clocks 3.4 million weights. In comparison, the optimum for the presented MCdropout results has $C=11$, using 9.0 million weights. On an NVIDIA Titan X, the dropout baseline takes 13s per epoch on average, while SQUAD-factorized spans just 9s.

# PREDICTIVE UNCERTAINTY THROUGH QUANTIZATION

| Fashion MNIST | cov@risk .5% | cov@risk 1% | cov@risk 2% | NLL | Acc. |
|---|---|---|---|---|---||
| Plain MLP | 29.1 (±20.71) | 45.9 (±4.04) | 60.4 (±3.17) | 0.408 (±0.036) | 87.7 (±42) |
| Maxout MCDropout | 41.9 (±9.86) | 56.5 (±2.30) | 69.9 (±1.48) | 0.299 (±0.008) | 89.5 (±28) |
| DLGM | 0.0 (±0.0) | 33.5 (±2.42) | 47.0 (±1.47) | 0.446 (±0.007) | 84.3 (±15) |
| SQUAD | 42.9 (±7.19) | 58.3 (±3.06) | 69.5 (±1.55) | 0.293 (±0.008) | 89.5 (±35) |

| Deep Ensemble | cov@risk .5% | cov@risk 1% | cov@risk 2% | NLL | Acc. |
|---|---|---|---|---|---||
| Plain MLP Ensemble | 40.6 | 58.3 | 70.2 | 0.296 | 89.3 |
| Max. MCD. Ensemble | 48.2 | 59.1 | 72.2 | 0.271 | 90.2 |
| DLGM Ensemble | 0.0 | 34.3 | 47.8 | 0.435 | 84.7 |
| SQUAD Ensemble | 47.5 | 61.6 | 73.1 | 0.273 | 90.1 |

**Table 6.1: SGR coverage results on Fashion MNIST.** We present coverage percentage of the test dataset for three pre-defined risk-guarantees (one per column), where higher coverage is better, as well as negative-likelihood and overall accuracy. The results indicate that SQUAD possesses competitive uncertainty, especially at low-risk guarantees. Bayesian approximations via deep ensembles improve coverage over the board, and for SQUAD in particular. SGR can guarantee the required risk level at high probability, 0% coverage is reported. (2 std. deviations in parentheses, optimal results in **bold**.)

**Table 6.2:** SQUAD exhibits strong performance on notMNIST using the optimal hyperparameters found for fashionMNIST.

| | MLP K=256 (SVHN) | cov@risk .5% | cov@risk 1% | cov@risk 2% | NLL | Acc. |
|---|---|---|---|---|---|---|
| Plain MLP | 0.0 (±00) | 0.0 (±00) | 36.3 (±2.84) | 0.758 (±065) | 83.1 (±42) |
| Maxout MCDropout | 0.0 (±00) | 50.7 (±1.42) | 65.0 (±2.32) | 0.480 (±020) | 86.4 (±71) |
| SQUAD-factorized | 18.4 (±30.3) | 53.9 (±1.81) | 66.7 (±2.10) | 0.454 (±021) | 86.6 (±88) |
| SQUAD | 1.7 (±6.75) | 42.8 (±2.25) | 59.3 (±1.38) | 0.534 (±005) | 84.6 (±13) |
| Max. MCDropout T=4 | 0.0 (±00) | 38.5 (±3.85) | 57.6 (±2.66) | 0.562 (±016) | 84.9 (±73) |
| SQUAD-factorized T=4 | 10.7 (±2.25) | 49.9 (±3.51) | 64.5 (±2.45) | 0.480 (±024) | 86.2 (±67) |
| SQUAD T=4 | 0.0 (±00) | 38.0 (±1.86) | 55.6 (±2.84) | 0.569 (±019) | 83.7 (±52) |

**Table 6.3:** Results on SVHN indicate that the quantization scheme used by SQUAD might have lower performance, but this is effectively compensated by the SQUAD-factorized variant using a larger area of bins. Even with T=4 samples, SQUAD performs well.

To evaluate the sample efficiency of the methods, we compare results at T = 4. We find that SQUAD's results suffer less from under-sampling the predictive distribution than MCDropout. We tentatively attribute the sample efficiency to the flexible posterior on the activations, which is in stark contrast to the rigid peaked distribution that MCDropout imposes on the weights. In conclusion, SQUAD comes out favorably in resource-constrained environments.

### 6.3.3 Analysis of latent variable distributions

In order to evaluate if the proposed variational distribution does not simply collapse into a single mode, we want to find out what type of distributions the model predicts over the latent variables. We visualize the forms of predicted distributions in figure 6.5. Although this shows only a small subset of potential multi-modal behavior, this demonstrates that the model indeed utilizes the distribution to its full potential. To provide an intuition on how these predicted distributions emerge, we present figure 6.7 in the appendix.

In figure 6.6 we visualize one of the activation functions that the method learns for a 1-dimensional SQUAD-factorized model. The learned activations resemble “peaked” sigmoid activations, which can be interpreted as a combination of an RBF kernel and sigmoid. This provides food for thought on how non-linearities for conventional neural networks can be designed, and the effect of using such a non-linearity can be studied in further work.

## 6.4 DISCUSSION

In this work, we have proposed a new flexible class of variational distributions. To measure the effectiveness for real-world classification, we applied the class to a deep variational information bottleneck model. By placing a quantization-based distribution on the activations, we can compute uncertainty estimates over the outputs. We proposed an evaluation scheme motivated by the need in real-world domains to guarantee a minimal risk. The results present indicate that SQUAD provides an improvement over plain neural networks and Gaussian information bottleneck models. In comparison to a MCDropout model, which approximates a Bayesian neural network, we get competitive performance. Moreover, qualitatively we find that the flexible distribution is used to its full advantage.
