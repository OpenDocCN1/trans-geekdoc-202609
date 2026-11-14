values of the score are less likely, so it is better to think of it as a non-conformity score.) Next we apply this score to a **calibration set** of $n$ labeled examples, that was not used to train $f$, to get $\mathcal{S} = \{s_i = s(\mathbf{x}_i, y_i) : i = 1 : n\}$. The user specifies a desired confidence threshold $\alpha$, say 0.1, and we then compute the $(1-\alpha)$ quantile $\hat{q}$ of $\mathcal{S}$. (In fact, we should replace $1-\alpha$ with $\frac{\lceil(n+1)(1-\alpha)\rceil}{n}$, to account for the finite size of $\mathcal{S}$.) Finally, given a new test input, $\mathbf{x}_{n+1}$, we compute the prediction set to be

```
$$\mathcal{T}(\mathbf{x}_{n+1}) = \{y : s(\mathbf{x}_{n+1}, y) \le \hat{q}\}$$ (14.49)
```

Intuitively, we include all the outputs $y$ that are plausible given the input. See Figure 14.4 for an illustration.

Remarkably, one can show the following general result

```
$$1 - \alpha \le P^*(y^{n+1} \in \mathcal{T}(\mathbf{x}_{n+1})) \le 1 - \alpha + \frac{1}{n+1}$$ (14.50)
```

where the probability is wrt the true distribution $P^*(\mathbf{x}_{n+1}, y_{n+1})$. We say that the prediction set has a **coverage** level of $1 - \alpha$. This holds for any value of $n \ge 1$ and $\alpha \in [0, 1]$. The only assumption is that the values $(\mathbf{x}_i, y_i)$ are exchangeable, and hence the calibration scores $s_i$ are also exchangeable. To see why this is true, let us sort the scores so $s_1 < \cdots < s_n$, so $\hat{q} = s_i$, where $i = \frac{\lceil(n+1)(1-\alpha)\rceil}{n}$. (We assume the scores are distinct, for simplicity.) The score $s_{n+1}$ is equally likely to fall in anywhere between the calibration points $s_1, \dots, s_n$, since the points are exchangeable. Hence

```
$$P^*(s_{n+1} \le s_k) = \frac{k}{n+1}$$ (14.51)
```

for any $k \in \{1, \dots, n+1\}$. The event $\{y_{n+1} \in \mathcal{T}(\mathbf{x}_{n+1})\}$ is equivalent to $\{s_{n+1} \le \hat{q}\}$. Hence

```
$$P^*(y_{n+1} \in \mathcal{T}(\mathbf{x}_{n+1})) = P^*(s_{n+1} \le \hat{q}) = \frac{\lceil(n+1)(1-\alpha)\rceil}{n+1} \ge 1 - \alpha$$ (14.52)
```

For the proof of the upper bound, see [Lei+18]. Although this result may seem like a “free lunch”, it is worth noting that we can always achieve a desired coverage level by defining the prediction set to be all possible labels. In this case, the prediction set will be independent of the input, but it will cover the true label $1 - \alpha$ of the time. To rule out some degenerate cases, we seek prediction sets that are as small as possible (although we allow for the set to be larger for harder examples), while meeting the coverage requirement. Achieving this goal requires that we define suitable conformal scores. Below we give some examples of how to compute conformal scores $s(\mathbf{x}, y)$ for different kinds of problem. It is also important to note that the coverage guarantees are frequentist in nature, and refer to average behavior, rather than representing per-instance uncertainty, as in the Bayesian approach.

3. Using a calibration set is called **split conformal prediction**. If we don’t have enough data to adopt this splitting approach, we can use **full conformal prediction** [VGS05], which requires fitting the model $n$ times using a leave-one-out type procedure.
4. It is also possible to learn conformal scores in an end-to-end way, jointly with the predictive model, as discussed in [Stu+22].