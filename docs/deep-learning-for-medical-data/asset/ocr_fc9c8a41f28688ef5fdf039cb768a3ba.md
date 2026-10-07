# 40 | CONTRAST PERTURBATIVE PREDICTIVE CODING

| Method | All labels | $1/128$th of labels | $1/512$th of labels |
| C2PC Same WSI | 84.3% | 85.2% | 85.2% |
| C2PC | 83.5% | 84.3% | 82.4% |
| CPC Same WSI | 76.8% | 76.0% | 75.2% |
| CPC | 76.0% | 75.6% | 75.7% |
| CAE | 75.2% | 74.7% | 74.7% |
| $eta$-CVAE($eta = 0.01$) 72.0% | 72.2% | 74.7% |
| Random | 74.5% | 68.8% | 72.2% |
| Fully Supervised | **87.1%** | 83.9% | 80.3% |
| $P_4M$-DenseNetVeeling et al., 2018 | 89.8% | - | - |
| DenseNetVeeling et al., 2018 | 88.1% | - | - |

**Table 4.1:** PCam classification accuracy on test set. C2PC achieves near-supervised performance, while the prediction model is simply a linear logistic regression model on top of unsupervised-extracted features. On small label regimes, the method outperforms fully supervised training. Results reported from a logistic model trained using the frozen pretrained feature model as input, with full data-augmentation. We evaluate the test performance by training a logistic regression model on varying fractions of the 131,072 train labels, evaluating test performance using weights with the highest validation accuracy.