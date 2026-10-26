
## Outline

- Probabilistic Graphical Models: Basics
- An overview of DL components
  - Historical remarks: early days of neural networks
  - Modern building blocks: units, layers, activation functions, loss functions, etc.
  - Reverse-mode automatic differentiation (aka backpropagation)
- Similarities and differences between GMs and NNs
  - Graphical models vs. computational graphs
  - Sigmoid Belief Networks as graphical models
  - Deep Belief Networks and Boltzmann Machines
- Combining DL methods and GMs
  - Using outputs of NNs as inputs to GMs
  - GMs with potential functions represented by NNs
  - NNs with structured outputs
- Bayesian Learning of NNs
  - Bayesian learning of NN parameters
  - Deep kernel learning

## Combining sequential NNs and GMs

### Hybrid: RNN + HMM

![](img/cb490ed30bca4eda5fbba81c52a2c173_62_0.png)

The model, inference, and learning can be analogous to our NN + HMM hybrid

- **Objective:** log-likelihood
- **Model:** HMM/Gaussian emissions
- **Inference:** forward-backward algorithm
- **Learning:** SGD with gradient by backpropagation

(Graves et al., 2013)

![](img/cb490ed30bca4eda5fbba81c52a2c173_63_0.png)

## Hybrid NNs + conditional GMs

### Hybrid: Neural Net + CRF

*Forward computation*

![](img/cb490ed30bca4eda5fbba81c52a2c173_65_0.png)

### Hybrid: CNN + CRF

- **"NN + SLL"**
- Model: Convolutional Neural Network (CNN) with **linear-chain CRF**
- Training objective: maximize **sentence-level likelihood (SLL)**

![](img/cb490ed30bca4eda5fbba81c52a2c173_66_0.png)

Figure from (Collobert & Weston, 2011)

## Using GMs as Prediction Explanations

### Satellite imagery

![](img/cb490ed30bca4eda5fbba81c52a2c173_67_0.png)

### Meaningful attributes

- 01 Nightlight intensity
- 02 Is urban
- 03 Has electricity
- 04 Has generator
- 05 Avg. temperature
- 06 Avg. precipitation
- 07 Vegetation
- 08 Avg. vegetation inc.
- 09 Avg. vegetation dec.
- 10 Avg. dist. to market
- 11 Avg. dist. to road
- 12 Num. of rooms
- 13 Dist. to water src.
- 14 Water usage p/ day
- 15 Is water paid
- 16 HH type: BQ

### Area attributes

![](img/cb490ed30bca4eda5fbba81c52a2c173_68_0.png)

How do we build a powerful predictive model whose predictions we can interpret in terms of semantically meaningful features?

| Attribute | Attribute |
|---|---|
| 01 Nightlight intensity | 09 Avg. vegetation dec. |
| 02 Is urban | 10 Avg. dist. to market |
| 03 Has electricity | 11 Avg. dist. to road |
| 04 Has generator | 12 Num. of rooms |
| 05 Avg. temperature | 13 Dist. to water src. |
| 06 Avg. precipitation | 14 Water usage p/ day |
| 07 Vegetation | 15 Is water paid |
| 08 Avg. vegetation inc. | 16 HH type: BQ |

## Contextual Explanation Networks (CENs)

**Context**  
**Explanation**  
**Prediction**  

Instance 1  
Instance 2  

![](img/cb490ed30bca4eda5fbba81c52a2c173_69_0.png)

![](img/cb490ed30bca4eda5fbba81c52a2c173_69_1.png)

Encoder  
Attributes  

| | Unreliable water | Water src: Public tap | Walls: Unburnt bricks | Roof: Thatch, Straw | Has electricity |
|---|---|---|---|---|---|
| Instance 1 | 0 | 1 | 1 | 0 | 1 |
| Instance 2 | 0 | 0 | 0 | 1 | 0 |

0.9 -0.6 0.3 0.5 -0.2  
-0.4 -1.2 -0.2 0.2 -0.8  

Not poor  
Poor  

Parametric as a graphical model

- Notes:
  - The final prediction is made by a linear GM.
  - Each coefficient assigns a weight to a meaningful attribute.
  - Allows us to judge predictions in terms of GMs produced by the context encoder.

![](img/cb490ed30bca4eda5fbba81c52a2c173_70_0.png)

- **General idea:** Use deep neural nets to **generate parameters** for graphical models applicable in a given context (e.g., for a given patient).
- Produced GMs are used to make the final prediction ⇒ 100% fidelity and consistency.
- GMs are built on top of semantically meaningful variables (not deep embeddings!) and can be used as **explanations** for each prediction.

### CEN: Implementation Details

![](img/cb490ed30bca4eda5fbba81c52a2c173_71_0.png)

**Workflow:**

- Maintain a (sparse) dictionary of GM parameters.
- Process complex inputs (images, text, time series, etc.) using deep nets; use soft attention to either select or combine models from the dictionary.
- Use constructed GMs (e.g., CRFs) to make predictions.
- Inspect GM parameters to understand the reasoning behind predictions.

Al-Shedivat, Dubey, Xing, arXiv, 2017

### Results: imagery as context

**Uganda: Contextual Models**

![](img/cb490ed30bca4eda5fbba81c52a2c173_72_0.png)

![](img/cb490ed30bca4eda5fbba81c52a2c173_72_1.png)

![](img/cb490ed30bca4eda5fbba81c52a2c173_72_2.png)

Based on the imagery, CEN learns to select different models for urban and rural areas

### Results: classical image & text datasets

| Method | Error |
|---|---:|
| Paragraph Vector (Le and Mikolov, 2014) | 7.42% |
| SA-LSTM with joint training (Dai and Le, 2015) | 14.70% |
| LSTM with tuning and dropout (Dai and Le, 2015) | 13.50% |
| LSTM initialized with word2vec embeddings (Dai and Le, 2015) | 10.00% |
| SA-LSTM with linear gain (Dai and Le, 2015) | 9.17% |
| LM-TM (Dai and Le, 2015) | 7.64% |
| SA-LSTM (Dai and Le, 2015) | 7.24% |
| Virtual Adversarial (Miyato et al., 2016) | 5.94 ± 0.12% |
| TopicRNN (Dieng et al., 2017) | 6.28% |
| **CEN-bow** | **5.92 ± 0.05%** |
| **CEN-topic** | **6.25 ± 0.09%** |

Semi-supervised training

Only supervised training (!!)

### CEN architectures for survival analysis

Encode a sequence of observations for a patient (e.g., vitals/tests measured in ICU).

Produce a CRF that predicts a sequence of survival indicators over future time intervals.

![](img/cb490ed30bca4eda5fbba81c52a2c173_75_0.png)

![](img/cb490ed30bca4eda5fbba81c52a2c173_75_1.png)

### Results: survival analysis

**SUPPORT2**

| Model | Acc@25 | Acc@50 | Acc@75 | RAE |
|---|---:|---:|---:|---:|
| Cox | 84.1 | 73.7 | 47.6 | 0.90 |
| Aalen | 87.1 | 66.2 | 45.8 | 0.98 |
| CRF | 84.4 | 89.3 | 79.2 | 0.59 |
| MLP-CRF | 87.7 | 89.6 | 80.1 | 0.62 |
| MLP-CEN | 85.5 | 90.8 | 81.9 | 0.56 |

**PhysioNet Challenge 2012**

| Model | Acc@25 | Acc@50 | Acc@75 | RAE |
|---|---:|---:|---:|---:|
| Cox | 93.0 | 69.6 | 49.1 | 0.24 |
| Aalen | 93.3 | 78.7 | 57.1 | 0.31 |
| CRF | 93.2 | 85.1 | 65.6 | 0.14 |
| LSTM-CRF | 93.9 | 86.3 | 68.1 | 0.11 |
| LSTM-CEN | 94.8 | 87.5 | 70.1 | 0.09 |

![](img/cb490ed30bca4eda5fbba81c52a2c173_76_0.png)

## Outline

![](img/cb490ed30bca4eda5fbba81c52a2c173_77_0.png)

- An overview of DL components
  - Historical remarks: early days of neural networks
  - Modern building blocks: units, layers, activation functions, loss functions, etc.
  - Reverse-mode automatic differentiation (aka backpropagation)
- Similarities and differences between GMs and NNs
  - Graphical models vs. computational graphs
  - Sigmoid Belief Networks as graphical models
  - Deep Belief Networks and Boltzmann Machines
- Combining DL methods and GMs
  - Using outputs of NNs as inputs to GMs
  - GMs with potential functions represented by NNs
  - NNs with structured outputs
- Bayesian Learning of NNs
  - Bayesian learning of NN parameters
  - Deep kernel learning

## Bayesian learning of NNs

- A neural network as a probabilistic model:
  - Likelihood: $p(y|x,\theta)$
    - Categorical distribution for classification $\Rightarrow$ cross-entropy loss
    - Gaussian distribution for regression $\Rightarrow$ squared loss
  - Prior on parameters: $p(\theta)$
- Maximum a posteriori (MAP) solution:
  - $\theta^{MAP}=\arg\max_{\theta}\log p(y|x,\theta)p(\theta)$
  - Gaussian prior $\Rightarrow$ L2 regularization
  - Laplace prior $\Rightarrow$ L1 regularization

![](img/cb490ed30bca4eda5fbba81c52a2c173_78_0.png)

Figure courtesy: Blundell et al, 2016

- Bayesian learning [MacKay 1992, Neal 1996, de Freitas 2003]
  - Posterior: $p(\theta|x,y)$
  - Variational inference with approximate posterior $q(\theta)$
