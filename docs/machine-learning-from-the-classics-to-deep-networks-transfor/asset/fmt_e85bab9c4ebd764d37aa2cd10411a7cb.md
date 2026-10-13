
𝔼\[*x*[*n*, *k*]\] = *γ*(*x*[*n*, *k*] = 1; *Θ*^((*t*))).

![Equation](images/B9780443292385000226/si287.png)(16.53)

Recall that given *Θ*^((*t*)), *γ*(⋅;*Θ*^((*t*))) can be efficiently computed via the sum-product algorithm described before. In a similar spirit and mobilizing the definition in Eq. [(16.51)](#Chp016_805-853_B9780443292385000226.xhtml#deq88), we can write

```
𝔼[x_{n-1,j}x_{n,i}] = ∑_{x_n}∑_{x_{n-1}}P(x_n,x_{n-1}|Y;Θ^{(t)})x_{n-1,j}x_{n,i}
                   = ∑_{x_n}∑_{x_{n-1}}ξ(x_n,x_{n-1};Θ^{(t)})x_{n-1,j}x_{n,i}
                   = ξ(x_{n-1,j}=1,x_{n,i}=1;Θ^{(t)}).
```

![Equation](images/B9780443292385000226/si290.png)(16.54)

Note that *ξ*(⋅,⋅;*Θ*^((*t*))) can also be efficiently computed as a by-product of the sum-product algorithm, given *Θ*^((*t*)). Thus, we can summarize the E-step as
