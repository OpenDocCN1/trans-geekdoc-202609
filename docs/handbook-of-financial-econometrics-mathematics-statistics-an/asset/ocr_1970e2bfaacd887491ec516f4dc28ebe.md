n_i = n_{1i} + n_{2i}. Assume k ≤ n, and let d_{1i} and d_{2i} be the number of observed events at time t_i (1 ≤ i ≤ k) in each group, where d_i = d_{1i} + d_{2i}.

Under the null hypothesis, for given parameter n_i, n_{1i} and d_i, the number of observed events in the first group, D_{1i}, is a random variable following a hypergeometric distribution. It can be written as

Pr(D_{1i} = d_{1i} | n_i, n_{1i}, d_i) = [C(d_i, d_{1i}) C(n_i - d_i, n_{1i} - d_{1i})] / C(n_i, n_{1i}).

Denote the expected value by e_{1i} = E(D_{1i} = d_{1i} | n_i, n_{1i}, d_i) and variance by v_{1i} = var(D_{1i} = d_{1i} | n_i, n_{1i}, d_i), we get

e_{1i} = d_i n_{1i} / n_i

and

v_{1i} = d_i (n_i - d_i) n_{1i} (n_i - n_{1i}) / [n_i^2 (n_i - 1)].

For group 1, Mantel and Haenszel (1959) proposed to sum up the differences between d_{1i} and e_{1i} for all observed survival times,

Sum_{i=1}^k (d_{1i} - e_{1i}).

Its standardized form is the following

[Sum_{i=1}^k (d_{1i} - e_{1i})] / sqrt[Sum_{i=1}^k v_{1i}].

The logrank statistic developed by Peto and Peto (1972) is the following:

Chi^2_logrank = {Sum_{i=1}^k (d_{1i} - d_i n_{1i} / n_i)}^2 / Sum_{i=1}^k [d_i (n_i - d_i) n_{1i} (n_i - n_{1i}) / (n_i^2 (n_i - 1))] ~ Chi^2_1,

which follows the standard normal distribution asymptotically.

To illustrate the application of the logrank test, we use a sample of 232 Nasdaq firms whose stock price fell below $1 for 30 consecutive trading days in 2010. We track these firms to June 29, 2018 to check how many of them are delisted or merged by the end of sample period.