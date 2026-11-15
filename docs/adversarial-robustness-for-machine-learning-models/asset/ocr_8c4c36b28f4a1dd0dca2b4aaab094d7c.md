Table 18.3 Performance of BAR on Clarifai.com APIs.

| Orig. Task to New Task | q | # of query | Accuracy | Cost |
|---|---|---|---|---|
| NSFW to ASD | 15 | 12.8k | 64.04% | $14.24 |
| | 25 | 24k | **65.70%** | $23.2 |
| Moderation to ASD | 15 | 11.9k | 65.14% | $13.52 |
| | 25 | 23.8k | **67.32%** | $23.04 |

Table 18.4 Performance of BAR on Microsoft Custom Vision API.

| Orig. Task to New Task | q | # of query | Accuracy | Cost |
|---|---|---|---|---|
| Traffic sign classification to ASD | 1 | 1.86k | 48.15% | $3.72 |
| | 5 | 5.58k | 62.34% | $11.16 |
| | 10 | 10.23k | **67.80%** | $20.46 |

mation can indeed improve the accuracy but at the price of increased query and expense costs.

Microsoft Custom Vision API is used to obtain a black-box traffic sign image recognition model (with 43 classes) trained with GTSRB dataset (Stallkamp et al., 2012). BAR is then applied with different numbers of random vectors q (1, 5, 10) and a fixed number of random label mapping (m = 6 labels) to reprogram it for ASD task. As shown in Table 18.4, the test accuracy achieves 69.15% when q is set to 10 and the overall query cost is $20.46 US dollars.

# 18.3 Theoretical justification of model reprogramming

To provide theoretical justification on the effectiveness of model reprogramming, in what follows, we show a formal population risk analysis and prove that based on reprogramming, the population risk of the target task is upper bounded by the sum of the source population risk and the Wasserstein-1 distance between the logit representations of the source data and the reprogrammed target data. The analysis matches the intuition that a high-accuracy (low population risk) source model with a better source-target data alignment (small Wasserstein-1 distance) should exhibit better reprogramming performance.

Using the mathematical notation summarized in Table 18.1, the source model is a pretrained K-way neural network classifier f_S(·) = η(z_S(·)) with a softmax layer η(·) as the final model output. We omit the notation of the model parameters in our analysis because reprogramming does not change