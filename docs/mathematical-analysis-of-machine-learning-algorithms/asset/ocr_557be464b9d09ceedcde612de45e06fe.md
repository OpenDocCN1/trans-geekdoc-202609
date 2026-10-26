$Λ(ρ,f) = -\frac{1}{ρ} \ln 𝔼_Z e^{-ρφ(f,Z)}$  (definition of Λ in Theorem 10.18)  
$= -\frac{1}{ρ} \ln 𝔼_X e^{-ρ(f(X)-f_D(X))^2+2ρ(f(X)-f_D(X))(Y-f_D(X))}$  (definition of φ)  
$≥ -\frac{1}{ρ} \ln 𝔼_X e^{(-ρ+2ρ^2b^2)(f(X)-f_D(X))^2}$  (sub-Gaussian noise assumption)  
$≥ \frac{1}{ρ}\left[1-𝔼_X e^{-0.5ρ(f(X)-f_D(X))^2}\right]$  ($-\ln z ≥ 1-z$)  
$≥ \frac{1}{ρ}𝔼_X e^{-2ρb^2}\,0.5ρ(f(X)-f_D(X))^2$  ($1-e^{-z} ≥ e^{-az}z$ for $z∈[0,a]$)  
$≥ 0.3𝔼_X(f(X)-f_D(X))^2.$  ($2ρb^2=0.5$)

It follows from Theorem 10.18 by setting $1/(λn)=ρ=b^{-2}/4$ (which implies that $λ=4b^2/n$) that for any random estimator $\hat q$ on $𝓕_n$,

$0.3𝔼_{S_n}𝔼_{f∼\hat q(·|S_n)}𝔼_X(f(X)-f_D(X))^2$  
$≤ 𝔼_{S_n}𝔼_{f∼\hat q(·|S_n)}\frac{1}{n}\sum_{i=1}^{n}φ(f,Z_i)+\frac{4b^2}{n}𝔼_{S_n}\operatorname{KL}(\hat q\|q_0).$  (12.1)

Let $\hat q$ correspond to the deterministic estimator $\hat f_{𝓕_n}$, and let $q_0$ be the uniform distribution on $𝓕_n$. Then $\operatorname{KL}(\hat q\|q_0)≤\ln|𝓕_n|$. Therefore we obtain

$0.3𝔼_{S_n}Q_{LS}(\hat f_{𝓕_n},𝓓)≤𝔼_{S_n}\frac{1}{n}\sum_{i=1}^{n}φ(\hat f_{𝓕_n},Z_i)+\frac{4b^2}{n}\ln|𝓕_n|$  
$≤\inf_{f∈𝓕_n}𝔼_{S_n}\frac{1}{n}\sum_{i=1}^{n}φ(f,Z_i)+\frac{4b^2}{n}\ln|𝓕_n|$  
$≤\inf_{f∈𝓕_n}Q_{LS}(f,𝓓)+\frac{4b^2}{n}\ln|𝓕_n|≤ε^2+\frac{4b^2}{n}\ln|𝓕_n|.$

( $\hat f_{𝓕_n}$ is empirical risk minimizer on $𝓕_n$ )

The last inequality used the fact that $𝓕_n$ is an $ε$ packing of $𝓕$ and $f_D∈𝓕$. This implies the desired bound.

# **Example 12.22**  Consider the covering number condition of Corollary 12.20.

We note that

$\inf_{ε>0} O\left(ε^2+\frac{1}{n}\ln M(ε,𝓕,L_2(D_X))\right)=O(n^{-2/(2+q)}).$

Therefore the upper bound of Proposition 12.21 matches the lower bound of Corollary 12.20.

The method of sieves can be regarded as a regularization method for ERM. The optimality of using a sieve versus ERM on the original function class implies that ERM can overfit if not used properly, which leads to suboptimality. It is suitable only for certain function classes but not others.