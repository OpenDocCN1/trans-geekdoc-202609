# ## 3 Background

TPPs are widely used to interpret complex event sequences over time. For example, in intensive care unit (ICU) monitoring, physicians analyze the progression of symptoms and lab results to make decisions. Understanding the logic rules among medical events is crucial for accurate diagnosis and treatment. This section briefly reviews temporal point processes and temporal logic rules.

# ### 3.1 Temporal Point Processes

Temporal Point Process (TPP) is mathematically defined as a stochastic process $\{t_i\}_{i=1}^N$ where each $t_i$ denotes the timestamp of an event, and $N$ is the number of observed events. The core component of TPPs is the conditional intensity function $\lambda(t)$, which defines the instantaneous rate of event occurrence at time $t$, conditioned on the history $\mathcal{H}_t = \{t_1, t_2, \dots, t_i\}$ up to but not including $t$:

\(\lambda(t|\mathcal{H}_t) = \lim_{\Delta t \to 0} \frac{\mathbb{P}(N(t+\Delta t) - N(t) = 1 | \mathcal{H}_t)}{\Delta t}.\) (1)

Here, $\Delta t$ is a small time interval, and $N(t)$ denotes the counting process up to $t$. This intensity function governs the likelihood of an event happening at a particular time. The overall dynamics are characterized by the joint distribution. By modeling $\lambda(t|\mathcal{H}_t)$, TPPs can describe a wide range of event patterns, including those influenced by past occurrences, external features, or domain-specific rules.

# ### 3.2 Temporal Logic Rules

Temporal logic rules consist of two parts: temporal predicates and relations. Define a set of predicates as $\mathcal{X} = \{X_1, X_2, \dots, X_n, Y\}$, where each predicates $X_u$ is an independent variable, $Y$ is a target variable. Define a set of temporal relations as $\mathcal{C}$, which define how the variables are related over time. Rules are in the form of "if-then". A generalized temporal logic rule $R$ can be expressed as:

\(R: C_i(\psi_1, \psi_2) \to Y,\) (2)

where \(C_i \in \mathcal{C}\) represents a temporal relation, and \(\psi_1, \psi_2\) are expressions that can either be variables from $\mathcal{X}$ or recursively defined temporal rules. For example, \(\psi\) can represent the variable "high heart rate" or the rule "high heart rate before hypertension". The temporal relations between two temporal points can be divided into four types: *and, before, equal, after* [2]. Actually, "\(X_1\) *before* \(X_2\)" and "\(X_2\) *after* \(X_1\)" are equivalent, so the final set of temporal relations is \(\mathcal{C} = \{and, before, equal\}\).

# ## 4 Methodology

This section introduces the framework of Hybrid-Rule Temporal Point Processes (HRTPP), shown in Fig. 1. Given an event sequence $\mathcal{S} = \{(t_i, k_i, v_i)\}_{i=1}^N$ consisting of $N$ events, each event type \(k_i \in \{1, 2, \dots, K\}\) is associated with an