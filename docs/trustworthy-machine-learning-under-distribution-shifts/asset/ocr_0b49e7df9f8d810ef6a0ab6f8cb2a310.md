# 5.3 METHODOLOGY

Learning, and Fine-Tuning of vision models. Next, we demonstrate problem setting and framework overview.

# 5.3.1 Problem Out-of-Distribution Formulation and Overview

Generalizing to Out-of-Distribution tasks is a challenging topic in computer vision problems, where we normally have a vision model parameterized by $\theta_{ev}=\theta_{cv}$ pre-trained on massive labeled in-distribution (ID) data $D^{id} = \{x^{id}, y^{id}\}_{id=0}^n \in \mathcal{X} \times \mathcal{Y}$, where $\mathcal{Y} = \mathbb{R}^C$. Here each $id$ example is sampled from a joint distribution, i.e., $(X^{id}, Y^{id}) \sim p^{id}$, where $X^{id}$ and $Y^{id}$ stand for variables. After pretraining, we can assume the conditional distribution $P(Y^{id}|X^{id})$ can be perfectly captured by the inference function $\hat{y}^{id} = f_{	heta_{cv}}(x^{id})$, where $\hat{y}^{id}$ is the prediction. In OOD tasks, we are given a set of unlabeled examples $D^{ood} = \{x^{ood}\}_{i=0}^n$ whose element $x^{ood} \in \mathcal{X}$ is drawn from an unknown data distribution $p^{ood}$. Due to the change of distribution, factors that affect the data generating process are shifted, causing a difference between $p^{ood}$ and $p^{id}$, further hindering the label prediction, i.e., $\hat{y}^{ood} = f_{	heta_{cv}}(x^{ood}) \nneq P(Y^{ood}|X^{ood})$, where $Y^{ood}$ is the unknown ground truth. Fortunately, having been observed with extraordinary low-shot generalization capability, leveraging LLM with parameters $\theta_{llm}\in \Theta_{llm}$ to enhance the OOD robustness of vision models.

Our framework is illustrated in Figure 5.2 and our problem can be formulated as follows:

```
$$\min_{\theta_{cv}} \mathcal{L}(f_{\theta_{cv}}, z); z = [\theta_{llm}, (X_i^+, Y_i^+); (X_i^-, Y_i^-); X_i)]_i^N;\nY_C = T[c]; \argmax f_{\theta_{cv}}(X_i)]$
```

where $X_i^+$ and $X_i^-$ denote the positive and negative examples, respectively, $X_i$ is the query image, and $T$ is the transition matrix. Intuitively, when a distribution shift occurs, the emerging prediction errors are essentially noisy labels that can be captured by estimating a transition matrix. Hence, by focusing on calibrating the examples with high noise probabilities, the visual robustness of downstream tasks can be improved effectively. In particular, we feed all OOD data into the vision model to obtain the noisy prediction $P(Y^{ood}|X^{ood})$,