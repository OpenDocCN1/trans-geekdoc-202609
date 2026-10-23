![](bbox=[0.44, 0.13, 0.66, 0.35])

Figure 10.18: A dynamic logistic regression model. w_t are the regression weights at time t, and a_t = w_t^⊤ x_t.

model using a Gaussian prior, where D_{1:t} = {(x_n, y_n) : n = 1 : t} is all the data we have seen so far. This is particularly useful in cases where the data is arriving in a continual stream, such as online advertising (see e.g., [Gra+10]) and recommender systems (see e.g., [Aga+14]). We follow the presentation of [Zoc07].

We assume our model has the following form:

p(y_t | x_t, w_t) = Ber(y_t | σ(x_t^⊤ w_t)) (10.166)
p(w_t | w_{t-1}) = N(w_t | w_{t-1}, σ^2 I) (10.167)

where σ^2 is some process noise which allows the parameters to change slowly over time. (This can be set to 0, as in the recursive least squares method (Sec. 11.6.7), if desired.) See Fig. 10.18 for an illustration. As our approximating family, we will use diagonal Gaussians, for computational efficiency. Thus the prior is the posterior from the previous timestep, and has the form

q_{t-1}(w_{t-1}) = ∏_j N(w_{t-1,j} | μ_{t-1,j}, τ_{t-1,j}) (10.168)

Now we discuss how to update this prior.

Define the logits as a_t = w_t^⊤ x_t. If q_{t|t-1}(w_t) = ∏_j N(w_{t,j} | μ_{t|t-1,j}, τ_{t|t-1,j}), then we can compute the predictive distribution for a_t as follows:

q_{t|t-1}(a_t) = N(a_t | m_{t|t-1}, v_{t|t-1}) (10.169)
m_{t|t-1} = Σ_j x_{t,j} μ_{t|t-1,j} (10.170)
v_{t|t-1} = Σ_j x_{t,j}^2 τ_{t|t-1,j} (10.171)