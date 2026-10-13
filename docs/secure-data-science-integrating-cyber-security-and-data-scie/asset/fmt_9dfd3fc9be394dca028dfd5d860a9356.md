
# 10.5 Adversarial SVM Learning

We now present an adversarial support vector machine model (AD-SVM) against each of the two attack models discussed in the previous section. We assume the adversary cannot modify the innocuous data. Note that this assumption can be relaxed to model cases where the innocuous data may also be altered.

## 10.5.1 AD-SVM against Free-range Attack Model

We first consider the free-range attack model. The hinge loss model is given as follows:

```
h(w, b, x_i) = {
    max_δ_i ⌊1 - (w · (x_i + δ_i) + b)⌋ +   if y_i = 1
    ⌊1 + (w · x_i + b)⌋ +                   if y_i = -1
}
s.t.    δ_i ≺ C_f (x^max - x_i)
        δ_i ≻ C_f (x^min - x_i)
```

where `δ_i` is the displacement vector for `x_i`, and `≺`, `≻` denote component-wise inequality.

Following the standard SVM risk formulation, we have:

```
arg min_{w,b}  Σ_{i|y_i=1} max_δ_i ⌊1 - (w · (x_i + δ_i) + b)⌋ +
               Σ_{i|y_i=-1} ⌊1 + (w · x_i + b)⌋ +
               μ ||w||^2
```

Combining cases for positive and negative instances, this is equivalent to:

```
arg min_{w,b}  Σ_i max_δ_i ⌊1 - y_i(w · x_i + b) - ½(1 + y_i)w · δ_i⌋ +
               μ ||w||^2
```

Note that the worst-case hinge loss of `x_i` is obtained when `δ_i` is chosen to minimize its contribution to the margin, that is,

```
f_i = min_δ_i ½(1 + y_i)w · δ_i
s.t.    δ_i ≺ C_f (x^max - x_i)
        δ_i ≻ C_f (x^min - x_i)
```

where `δ_i` is the displacement vector for `x_i`, and `≺`, `≻` denote component-wise inequality.

This is a disjoint bilinear problem with respect to `w` and `δ_i`. Here, we are interested in discovering optimal assignment to `δ_i` with a given `w`. We can reduce the bilinear problem to the following asymmetric dual problem over `u_i ∈ ℝ^d`, `v_i ∈ ℝ^d` where `d` is the dimension of the feature space:

```
g_i = max - Σ_j C_f (v_ij (x_j^max - x_ij) - u_ij (x_j^min - x_ij))
or
g_i = min Σ_j C_f (v_ij (x_j^max - x_ij) - u_ij (x_j^min - x_ij))
s.t.    (u_i - v_i) = ½(1 + y_i)w
        u_i ≻ 0
        v_i ≻ 0
s.t.    (u_i - v_i) = 1(1 + y_i)w
```

The SVM risk minimization problem can be rewritten as follows:

```
arg min_{w,b,t_i,u_i,v_i}  ½||w||^2 + C Σ_i ⌊1 - y_i · (w · x_i + b) + t_i⌋ +
s.t.    t_i ≥ Σ_j C_f (v_ij (x_j^max - x_ij) - u_ij (x_j^min - x_ij))
        u_i - v_i = ½(1 + y_i)w
        u_i ≻ 0
        v_i ≻ 0
```

Adding a slack variable and linear constraints to remove the non-differentiability of the hinge loss, we can rewrite the problem as follows:

```
arg min_{w,b,ξ_i,t_i,u_i,v_i}  ½||w||^2 + C Σ_i ξ_i
s.t.    ξ_i ≥ 0
        ξ_i ≥ 1 - y_i · (w · x_i + b) + t_i
        t_i ≥ Σ_j C_f (v_ij (x_j^max - x_ij) - u_ij (x_j^min - x_ij))
        u_i - v_i = ½(1 + y_i)w
        u_i ≻ 0
        v_i ≻ 0
```

## 10.5.2 AD-SVM against Restrained Attack Model

With the restrained attack model, we modify the hinge loss model and solve the problem following the same steps:

```
h(w, b, x_i) = {
    max_δ_i ⌊1 - (w · (x_i + δ_i) + b)⌋ +   if y_i = 1
    ⌊1 + (w · x_i + b)⌋ +                   if y_i = -1
}
s.t.
(x_i^t - x_i) ∘ δ_i ≺ C_ξ (1 - C_δ |x_i^t - x_i| / (|x_i| + x_i^t)) ∘ (x_i^t - x_i)^∘2
(x_i^t - x_i) ∘ δ_i ≻ 0
```

where `δ_i` denotes the modification to `x_i`, `≺` is component-wise inequality, and `∘` denotes component-wise operations.

The worst case hinge loss is obtained by solving the following minimization problem:

```
f_i = min_δ_i ½(1 + y_i)w · δ_i
s.t.    (x_i^t - x_i) ∘ δ_i ≺ C_ξ (1 - C_δ |x_i^t - x_i| / (|x_i| + |x_i^t|)) ∘ (x_i^t - x_i)^∘2
        (x_i^t - x_i) ∘ δ_i ≻ 0
```
