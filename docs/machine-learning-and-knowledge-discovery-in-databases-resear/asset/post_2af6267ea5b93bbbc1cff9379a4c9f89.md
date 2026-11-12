
- A two-phase rule mining strategy is introduced to balance search space complexity and predictive performance.

- A comprehensive evaluation paradigm for interpretable temporal point process models is established, incorporating multiple criteria to assess both predictive performance and rule reliability.

## 2 Related Work

Temporal Point Processes. Temporal Point Process (TPP) models provide a probabilistic framework for capturing event sequences in continuous time. A key challenge in TPP research lies in designing intensity functions that are both expressive and interpretable. Efforts to improve interpretability in TPPs have led to the development of attention-based and rule-based approaches. Attention-based approaches such as SA-HP [28] and THP [29] incorporate self-attention mechanisms to capture long-range dependencies in event sequences. ITHP [19] further explains THP by algebraic operations. Although these methods improve flexibility, the trade-off between accuracy and interpretability remains an open problem. Rule-based TPP models focus on enhancing interpretability through structured rule sets. TLPP [16] first introduces logic rules to model event intensities and defines temporal rules as a combination of temporal predicates and relations. TELLER [15] introduces a principled approach to mine rules that explain temporal dependencies. Based on this, CLUSTER [14] and NS-TPP [27] design different deep neural network structures to accelerate rule mining. Clock Logic Neural Network (CLNN) [24] incorporates weighted clock logic formulas as rules to model event interactions. The recent trend in TPP research highlights the need to balance both explainable and effective aspects, integrating structured rule-based approaches with deep learning models for more explainable and effective event modeling.

Rule Mining. Rule mining focuses on automatically discovering logical rules from event sequence data to explain event occurrence patterns. Traditional methods for rule discovery primarily identify frequent patterns, but struggle with capturing temporal dependencies. Apriori [1] efficiently extracts frequent event sets but fails to model event order. Sequential pattern mining techniques, such as CM-SPADE [7] and VGEN [8], attempt to incorporate temporal orders but face difficulties in handling fine-grained timestamps. To overcome these limitations, TELLER [15] formulates rule discovery as a maximum likelihood problem to generate high quality rules, but requires a lot of computation. CLUSTER [14] introduces an iterative framework based on the Expectation-Maximization algorithm to improve rule mining efficiency. NS-TPP [27] represents predicates and logic rules as vector embeddings and introduces a neural-symbolic framework for rule mining. Clock Logic Neural Network (CLNN) [24] utilizes weighted clock logic formulas to introduce three novel rule forms and incorporate numerical values into the rules. HyperLogic [26] proposes the integration of if-then logic rules within neural network architectures.

## 3 Background

TPPs are widely used to interpret complex event sequences over time. For example, in intensive care unit (ICU) monitoring, physicians analyze the progression of symptoms and lab results to make decisions. Understanding the logic rules among medical events is crucial for accurate diagnosis and treatment. This section briefly reviews temporal point processes and temporal logic rules.

### 3.1 Temporal Point Processes

Temporal Point Process (TPP) is mathematically defined as a stochastic process $\{t_i\}_{i=1}^N$ where each $t_i$ denotes the timestamp of an event, and $N$ is the number of observed events. The core component of TPPs is the conditional intensity function $\lambda(t)$, which defines the instantaneous rate of event occurrence at time $t$, conditioned on the history $\mathcal{H}_t = \{t_1, t_2, \dots, t_i\}$ up to but not including $t$:

\(\lambda(t|\mathcal{H}_t) = \lim_{\Delta t \to 0} \frac{\mathbb{P}(N(t+\Delta t) - N(t) = 1 | \mathcal{H}_t)}{\Delta t}.\) (1)

Here, $\Delta t$ is a small time interval, and $N(t)$ denotes the counting process up to $t$. This intensity function governs the likelihood of an event happening at a particular time. The overall dynamics are characterized by the joint distribution. By modeling $\lambda(t|\mathcal{H}_t)$, TPPs can describe a wide range of event patterns, including those influenced by past occurrences, external features, or domain-specific rules.

### 3.2 Temporal Logic Rules

Temporal logic rules consist of two parts: temporal predicates and relations. Define a set of predicates as $\mathcal{X} = \{X_1, X_2, \dots, X_n, Y\}$, where each predicates $X_u$ is an independent variable, $Y$ is a target variable. Define a set of temporal relations as $\mathcal{C}$, which define how the variables are related over time. Rules are in the form of "if-then". A generalized temporal logic rule $R$ can be expressed as:

\(R: C_i(\psi_1, \psi_2) \to Y,\) (2)

where \(C_i \in \mathcal{C}\) represents a temporal relation, and \(\psi_1, \psi_2\) are expressions that can either be variables from $\mathcal{X}$ or recursively defined temporal rules. For example, \(\psi\) can represent the variable "high heart rate" or the rule "high heart rate before hypertension". The temporal relations between two temporal points can be divided into four types: *and, before, equal, after* [2]. Actually, "\(X_1\) *before* \(X_2\)" and "\(X_2\) *after* \(X_1\)" are equivalent, so the final set of temporal relations is \(\mathcal{C} = \{and, before, equal\}\).

## 4 Methodology

This section introduces the framework of Hybrid-Rule Temporal Point Processes (HRTPP), shown in Fig. 1. Given an event sequence $\mathcal{S} = \{(t_i, k_i, v_i)\}_{i=1}^N$ consisting of $N$ events, each event type \(k_i \in \{1, 2, \dots, K\}\) is associated with an

### Hybrid-Rule Temporal Point Processes (HRTPP)

![](img/f56761e6196132d5b74909d98468408f_506_0.png)

Fig. 1. The framework of model. In the HRTPP component, given a candidate rule set and event sequences, the model can compute the likelihood of the intensity function. The model integrates three key intensity components: basic intensity, rule-based intensity, and numerical feature intensity, which together determine the overall event intensity function \(\lambda(t|\mathcal{H}_t)\). The numerical feature intensity captures the influence of continuous-valued attributes using a numerical feature encoder and a masking mechanism. The rule-based intensity encodes temporal dependencies through predefined rule set. In the rule set mining and optimizing component, Bayesian optimization iteratively refines the rule set by utilizing HRTPP computed likelihoods to guide the sampling distribution over the search space. The selected rules provide interpretable explanations of critical events via their impact on the intensity function dynamics.

independent variable \(X_k\) and a numerical feature \(v_i\), providing contextual information. For instance, in ICU monitoring, an event \(k_i\) “elevated heart rate” at \(t_i = 2\) hours may have \(v_i = 120\) bpm. The conditional intensity function \(\lambda(t|\mathcal{H}_t)\) is extended to incorporate temporal logic rules alongside numerical attributes, formulated as follows:

\(\lambda(t|\mathcal{H}_t) = f(\mathcal{S}_t; \Theta, \mathcal{R}), \quad (3)\)

where \(\mathcal{H}_t\) represents the historical event information, \(\mathcal{S}_t = \{(t_i, k_i, v_i)\}_{t_i < t}\) denotes the observed event sequence, \(\Theta\) is the set of model parameters, and \(\mathcal{R}\) comprises the extracted temporal logic rules that govern event dependencies.

### 4.1 Rule-Based Feature Construction

Temporal logic rules are essential in medical diagnosis, particularly in ICU monitoring, where capturing symptom progression is crucial for informed clinical decision-making. We propose a rule-based feature construction framework that integrates structured temporal rules with numerical features. This approach encodes event dependencies into numerical representations, ensuring a balance between explainability and data-driven modeling.

#### Definitions of Temporal Rules.

Temporal rules formally define the logical relationships between different events over time, which consists of temporal predicates and temporal relations. In this study, we categorize the temporal relations between two time points into three types: before, equal, and.

Given two predicates $X_u$ and $X_v$ with timestamps $t_u$ and $t_v$, along with a target event $Y$ occurring at $t_y > \max(t_u, t_v)$ and the indicator function $\mathbb{I}(\cdot)$, the three types of temporal rules are mathematically defined as follows. Before, where $X_u$ occurs before $X_v$ within a small time tolerance $\delta$, formulated as $\mathcal{C}_{before}(X_u, X_v) = \mathbb{I}(t_u - t_v < -\delta)$. Equal, where $X_u$ and $X_v$ occur approximately at the same time, formulated as $\mathcal{C}_{equal}(X_u, X_v) = \mathbb{I}(|t_u - t_v| \le \delta)$. And, which simply states that both events occur without temporal constraints, formulated as $\mathcal{C}_{and}(X_u, X_v) = 1$. These temporal rules provide a structured mechanism for capturing event dependencies.

#### Rule Encoder.

To effectively incorporate temporal rules into the TPP framework, we encode hybrid-rule information into a continuous vector space. Based on the definitions of temporal rules, we construct hybrid-rule event sequences. For instance, consider the temporal rule "$X_u$ before $X_v \rightarrow Y$". The corresponding hybrid-rule event sequence records the timestamps when the condition $X_u$ before $X_v$ is satisfied. Specifically, this sequence tracks each moment where the constraint $\mathcal{C}_{before}(X_u, X_v)$ transitions from 0 to 1. The encoding function for a rule $R_j$ is defined as:

```
$e_j(t) = \sum_{t_j \in \mathcal{T}_j} d_{\text{rule}}(t - t_j),$ (4)
```

where $d_{\text{rule}}$ is the decay function, and $\mathcal{T}_j$ denotes the set of timestamps when rule $R_j$ is triggered. The choice of the decay function depends on real-world dynamics. For example, an exponential decay function, defined as $d_{rule}(t) = e^{-t}$ for $t \ge 0$, can model the diminishing influence of past rule activations over time.

#### Numerical Feature Encoder.

Numerical features provide quantitative insight into the condition of a patient. The numerical feature encoder captures the dynamic influence of numerical attributes over time. Given an event sequence $\mathcal{S} = \{(t_i, k_i, v_i)\}_{i=1}^N$, the sequence corresponding to the predicate $X_k$ is expressed as $\{(t_i, k_i, v_i)\}_{k_i=k}$. Generally, not all predicates directly influence the target event. Therefore, we introduce a masking mechanism to filter out irrelevant predicates. The mask is defined according to the given rule set, where only the predicates appearing in rules associated with the target event remain active, ensuring that the retained variables are indeed the relevant ones. Formally, the mask set is denoted as $\mathcal{M} = \{m_k\}_{k=1}^K$, and the valid predicate set $\mathcal{X}_V \subset \mathcal{X}$
