
Let the corresponding norm be denoted as `∥ ⋅ ∥[i]`. For the regularized total squared error cost [93], the optimization task is now cast as

```
minimize with respect to f  1/2 ∑_{n=1}^{N} (y_n - f(x_n))^2 + λ ∑_{i=1}^{l} ‖h_i‖_i,
```

![Equation](images/B9780443292385000172/si502.png)(11.96)

```
s.t.  f(x) = ∑_{i=1}^{l} h_i(x_i).
```

![Equation](images/B9780443292385000172/si503.png)(11.97)

Plugging Eq. [(11.97)](#Chp011_519-582_B9780443292385000172.xhtml#deq220) into [(11.96)](#Chp011_519-582_B9780443292385000172.xhtml#deq219) and following arguments similar to those used in Section [11.6](#Chp011_519-582_B9780443292385000172.xhtml#s0055), it is readily obtained that we can write

```
ĥ_i(·) = ∑_{n=1}^{N} θ_{i,n} κ_i(·, x_{i,n}),
```

![Equation](images/B9780443292385000172/si504.png)(11.98)

where `x_{i,n}` is the *i*th component of **x_n**. Moving along the same path as that adopted in Section [11.7](#Chp011_519-582_B9780443292385000172.xhtml#s0070), the optimization can be rewritten in terms of

```
θ_i = [θ_{i,1}, …, θ_{i,N}]^T,  i = 1, 2, …, l,
```

![Equation](images/B9780443292385000172/si506.png)

as
