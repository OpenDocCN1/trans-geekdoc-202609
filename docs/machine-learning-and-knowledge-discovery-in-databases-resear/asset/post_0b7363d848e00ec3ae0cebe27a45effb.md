
denotes the collection of all variables appearing in the rules. The mask function is defined as \( m_k = 1 \) if \( X_k \in \mathcal{X}_V \), and \( m_k = 0 \) otherwise. Using this masking mechanism and the sequence \( \{(t_i, k_i, v_i)\}_{k_i=k} \), we define the numerical feature encoding function for predicate \( X_k \) as:

\( g_k(t) = m_k \sum_{i:k_i=k} v_i d_{\text{num}}(t - t_i), \)

where \( d_{\text{num}} \) is a time decay function, that models the influence of past numerical observations. The mask \( m_k \) ensures consistency within the HRTPP framework.

## 4.2 Hybrid-Rule Temporal Point Processes

HRTPP extends classical TPP by integrating rule-based dependencies and numerical features. The overall intensity function is composed of three key components. First, basic intensity models fundamental event patterns. Second, rule-based intensity encodes temporal logic rules. Third, numerical feature intensity incorporates clinical measurements to refine event prediction.

### Basic Intensity.

The basic intensity component \( \lambda_{\text{base}} \) captures the time-independent information. This component reflects the inherent likelihood of events occurring. Mathematically, the basic intensity is expressed as: \( \lambda_{\text{base}} = \lambda_0 \), where \( \lambda_0 \) is a learnable parameter.

### Rule-Based Intensity.

The rule-based intensity component integrates domain expertise and temporal dependencies into the event modeling process. Given a predefined set of temporal rules \( \mathcal{R} \), the rule-based intensity function is defined as:

\( \lambda_{\text{rule}}(t) = \sum_{R_j \in \mathcal{R}} \alpha_j e_j(t), \)

where \( \alpha_j \) is a learnable parameter representing the weight associated with rule \( R_j \). \( e_j(t) \) denotes the encoding function, shown in Eq. (4). By incorporating rule-based intensity, HRTPP ensures that predictions align with medically interpretable dependencies rather than relying solely on data-driven patterns.

### Numerical Feature Intensity.

Numerical features such as heart rate and blood pressure provide an essential context for event predictions. The numerical feature intensity component modulates event occurrence probabilities based on these continuously valued attributes. The intensity function is defined as:

\( \lambda_{\text{num}}(t) = \sum_{k=1}^K \beta_k g_k(t), \)

where \(\beta_k\) is a learnable parameter representing the weight associated with predicate \(X_k\). \(g_k(t)\) is the numerical feature encoder, which is shown in Eq. (5). For example, if a patient's blood pressure remains high, it may increase the likelihood of a hypertension-related event. The numerical feature dynamically modulates event probabilities, providing a richer representation of patient status.

The overall intensity function integrates all three intensity components. In order to ensure that the overall intensity function remains positive, we apply the softplus transformation. The softplus function is defined as: \(\text{Softplus}(x) = \gamma \log(1 + \exp(x/\gamma))\), where \(\gamma > 0\) is a learnable parameter. By incorporating Eqs. (4)-(7), the final expression for the overall intensity function is as follows:

$$
\lambda(t|\mathcal{H}_t) = \text{Softplus} \left( \lambda_{\text{base}}(t) + \lambda_{\text{rule}}(t) + \lambda_{\text{num}}(t) \right)
= \text{Softplus} \left( \lambda_0 + \sum_{R_j \in \mathcal{R}} \alpha_j \sum_{t_j \in T_j} d_{\text{rule}}(t - t_j) + \sum_{k=1}^K \beta_k m_k \sum_{i:k_i=k} v_i d_{\text{num}}(t - t_i) \right).
$$

where \(\boldsymbol{\alpha} = \{\alpha_j\}_{j=1}^{|\mathcal{R}|}\) is the set of weights associated with temporal rules, \(\boldsymbol{\beta} = \{\beta_i\}_{i=1}^K\) is the set of weights associated with numerical features. The learnable parameters set is denoted as \(\Theta = \{\boldsymbol{\alpha}, \boldsymbol{\beta}, \gamma, \lambda_0\}\). This overall intensity function serves as the foundation for modeling event occurrences in HRTPP framework, enabling robust modeling in event prediction and rule mining.

## 4.3 Training and Prediction

To effectively learn the parameters of the HRTPP model and enable accurate event prediction, we design a training framework based on likelihood maximization and employ our learned intensity function for future event forecasting.

### Loss Function.

The HRTPP model is trained by maximizing the likelihood of observed event sequences within the temporal point process framework. Given an event sequence \(\mathcal{S} = (t_i, k_i, v_i)_{i=1}^N\) and a rule set \(\mathcal{R}\), the likelihood function is formulated as \(\mathcal{L}(\Theta) = \prod_{i=1}^N \lambda(t_i|\mathcal{H}_{t_i}) \exp \left( - \int_0^{t_N} \lambda(t|\mathcal{H}_t) dt \right)\), where \(\Theta\) is the set of learnable model parameters. To facilitate optimization, we minimize the negative log-likelihood (NLL) as the loss function:

$$
\mathcal{L}_{\text{NLL}}(\Theta) = - \sum_{i=1}^N \log \lambda(t_i|\mathcal{H}_{t_i}) + \int_0^{t_N} \lambda(t|\mathcal{H}_t) dt.
$$

This loss function ensures that the model learns to assign higher intensities to observed events while also maintaining proper event distributions over time.

### Event Prediction.

HRTPP model can be used to predict the timing of future events based on the learned intensity function. Given a history \(\mathcal{H}_t\) up to time \(t\), the next event time \(\hat{t}\) is sampled from the conditional density function:

$$
p(\hat{t}|\mathcal{H}_t) = \lambda(\hat{t}|\mathcal{H}_t) \exp \left( - \int_t^\hat{t} \lambda(s|\mathcal{H}_s) ds \right). \quad (10)
$$

By minimizing the loss function, HRTPP effectively learns the underlying intensity function of event occurrences. By predicting the timing of the next event, HRTPP can capture the evolving dynamics of the sequence, offering valuable insights and data-driven support for medical diagnosis.

## 4.4 Rule Mining and Optimization

To efficiently extract temporal logic rules, a two-phase rule mining strategy is employed, incorporating rule candidate generation and Bayesian optimization.

### Rule Candidate Generation.

Temporal rules are derived from historical event sequences to construct a structured search space. Without constraints, the combination of predicates and relations can be excessively large. For instance, any rule containing \(m\) predicates and relations interconnected by \((m-1)\) relations yields a combinatorial space of \(K^m C^{m-1}\) possible configurations, with \(K\) and \(C\) being the total number of the predicates and relations respectively. To address this, rule length is restricted, and predicate filtering is applied. Firstly, rule length significantly impacts interpretability. Overly complex rules hinder comprehension, whereas single-predicate rules lack temporal expressiveness. Based on medical guidelines, a maximum of two or three predicates is imposed. Secondly, predicate filtering is conducted via pre-training using a rule-free TPP model as a baseline. Each predicate is evaluated individually, and those reducing model loss are retained. The resulting filtered predicates are used to generate candidate rules, ensuring that each rule contains at least one valid predicate. This process refines the search space, facilitating efficient rule selection.

### Rule Optimization via Bayesian Optimization.

Following candidate generation, Bayesian optimization is utilized to refine the rule set and maximize predictive performance, avoiding the infeasibility of exhaustive searches. The objective is to identify the optimal rule subset \(\mathcal{R}^*\) that maximizes the model log-likelihood:

$$
\mathcal{R}^* = \arg \max_{\mathcal{R}} \log \mathcal{L}(\mathcal{R}; \Theta), \quad (11)
$$

where \(\log \mathcal{L}(\mathcal{R}; \Theta)\) denotes the model likelihood given the rule set \(\mathcal{R}\). To maintain efficiency and interpretability, the rule set size \(|\mathcal{R}|\) is constrained to a fixed constant.

Bayesian optimization iteratively updates the rule set in three steps:
- sampling candidate subsets using a probabilistic acquisition function,
- evaluating
