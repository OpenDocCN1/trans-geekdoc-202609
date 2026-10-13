
𝔼[**ω**[*n*]**ω**[*n*]^(*T*)] = *Σ*[*ω*].

![Equation](images/B9780443292385000123/si240.png)

Hence, taking into account Eqs. [(6.54)](#Chp006_249-291_B9780443292385000123.xhtml#deq109), [(6.55)](#Chp006_249-291_B9780443292385000123.xhtml#deq110), and the RLS iteration involving the respective random variables, we get

**θ**[*n*] − **θ**[*o*, *n*] = **θ**[*n* − 1] + **k**[*n*]*e*[*n*] − **θ**[*o*, *n* − 1] − **ω**[*n*],

![Equation](images/B9780443292385000123/si241.png)

or

**c**[*n*] := **θ**[*n*] − **θ**[*o*, *n*] = **c**[*n* − 1] + *P*[*n*]**x**[*n*]*e*[*n*] − **ω**[*n*] = (*I* − *P*[*n*]**x**[*n*]**x**[*n*]^(*T*))**c**[*n* − 1] + *P*[*n*]**x**[*n*]**η**[*n*] − **ω**[*n*],

![Equation](images/B9780443292385000123/si242.png)

which is the counterpart of Eq. [(5.74)](#Chp005_177-248_B9780443292385000111.xhtml). Note that the time indices for the input and the noise variables can be omitted, because their statistics are assumed to be time-invariant.

We adopt the same assumptions as in Section [5.12](#Chp005_177-248_B9780443292385000111.xhtml). In addition, we assume that *P*[*n*] is changing slowly compared to **c**[*n*]. Hence, every time *P*[*n*] appears inside an expectation, it is substituted by its mean 𝔼[*P*[*n*]], i.e.,
