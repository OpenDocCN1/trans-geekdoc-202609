
## 经验风险最小化与随机近似

*J*(**θ**) = 𝔼 [ℒ(*y*, *f*[**θ**](**x**))] := 𝔼 [ℒ(**θ**, *y*, **x**)].

![Equation](images/B9780443292385000147/si368.png) (8.64)

Instead, the corresponding empirical risk function is minimized, given a set of *N* training points,

$$J_{N}(\mathbf{\theta}) = \frac{1}{N}\sum\limits_{n = 1}^{N}\mathcal{L}(\mathbf{\theta}, y_{n}, \mathbf{x}_{n}).$$

![Equation](images/B9780443292385000147/si369.png) (8.65)

In this context, the subgradient scheme would take the form

$$\mathbf{\theta}^{(i)} = \mathbf{\theta}^{(i - 1)} - \frac{\mu_{i}}{N}\sum\limits_{n = 1}^{N}\mathcal{L}_{n}^{\prime}\left( \mathbf{\theta}^{(i - 1)} \right),$$

![Equation](images/B9780443292385000147/si370.png)

where for notational simplicity we used

ℒ[*n*](**θ**) := ℒ(**θ**, *y*[*n*], **x**[*n*]).

![Equation](images/B9780443292385000147/si371.png) (8.66)

Thus, at each iteration, one has to compute *N* subgradient values, which for large values of *N* is computationally cumbersome. One way out is to adopt stochastic approximation arguments, as explained in Chapter [5](#Chp005_177-248_B9780443292385000111.xhtml), and come with a corresponding online version,

**θ**[*n*] = **θ**[*n* − 1] − *μ*[*n*]ℒ[*n*]^′(**θ**[*n* − 1]),

![Equation](images/B9780443292385000147/si372.png) (8.67)
