# Table 18.10: Notations in our model.

| Notation | Definition |
|---|---|
| ∑ = {Γ} | A set of n Γ |
| S = {G} | A set of n G |
| {Γ} = {C_i}, i ∈ {1,…,t} | Multi-source super group |
| G = {Ξ_i}, i ∈ {1,…,t} | News super group: a set of t “groups” |
| C_i = {X_i, d_i, s_i} | An element of Γ |
| Ξ_i = {x_ij}, j ∈ {1,…,n_i} | An element of G, n_i is the number of instances in group Ξ_i |
| x_ij ∈ R^{V×1} | A V-dimensional vector of news, the jth instance in Ξ_i |
| p_{ij} ∈ [0,1] | The probability of x_ij in group Ξ_i in news super group to be positive |
| p_{m−i} ∈ [0,1] | The probability of news group i in news super group to be positive |
| d_i ∈ R^{3×1} | A 3-dimensional vector of stock market data on day i, (average price, market index change and turnover rate) |
| s_i ∈ R^{2×1} | A 2-dimensional vector of sentiment on day i (positive and negative) |
| p_{d−i} ∈ [0,1] | The probability of stock market data on day i to the multi-source super group label that is positive |
| p_{s−i} ∈ [0,1] | The probability of sentiment on day i to the multi-source super group label to be positive |
| P_i ∈ [0,1] | The probability of multi-source information (i.e., news, stock quantitative data and the sentiment data) on day i to be positive |
| Π ∈ [0,1] | The estimated probability for a multi-source super group |
| Y ∈ {−1,+1} | Label of multi-source super group |

# 18.4.3 Multi-source multiple instance model¹¹

We first state and formulate the problem, and then propose the multi-source multiple instance (M-MI) framework and the corresponding learning process. Before going into details of our framework, we define some important notations as shown in Table 18.10.

# 18.4.3.1 Problem statement

Stock markets are impacted by various factors, such as the trading volume, news events and the investors’ emotions. Thus, replying on a single data source (e.g., historical trading data) is not sufficient to make accurate predictions. The object of our study is to develop a multi-source data integration approach to predict the stock market index movement. Specifically, given a collection of economic news, social posts and historical trading data,