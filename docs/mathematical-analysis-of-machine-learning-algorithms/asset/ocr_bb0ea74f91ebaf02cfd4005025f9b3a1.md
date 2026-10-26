Using this inequality, we obtain:

$(\tilde w_t - w)^\top A_t (\tilde w_t - w)$
$= (w_{t-1} - \eta A_t^{-1} g_t - w)^\top A_t (w_{t-1} - \eta A_t^{-1} g_t - w)$
$= (w_{t-1} - w)^\top A_t (w_{t-1} - w) - 2\eta (w_{t-1} - w)^\top g_t + \eta^2 g_t^\top A_t^{-1} g_t$
$\le (w_{t-1} - w)^\top A_t (w_{t-1} - w) + 2\eta[\ell_t(w) - \ell_t(w_{t-1})] - [(w - w_{t-1})^\top g_t]^2$
$\quad + \eta^2 g_t^\top A_t^{-1} g_t$
$\stackrel{(a)}{\equiv} (w_{t-1} - w)^\top A_{t-1} (w_{t-1} - w) + 2\eta[\ell_t(w) - \ell_t(w_{t-1})]$
$\quad + \eta^2 \text{trace}(A_t^{-1}(A_t - A_{t-1}))$
$\stackrel{(b)}{\le} (w_{t-1} - w)^\top A_{t-1} (w_{t-1} - w) + 2\eta[\ell_t(w) - \ell_t(w_{t-1})]$
$\quad + \eta^2[\ln|A_t| - \ln|A_{t-1}|]$.

The first inequality used (15.8). We used $g_t g_t^\top = A_t - A_{t-1}$ twice for the last two terms in $(a)$. In $(b)$, we used the concavity of the log-determinant function $\ln|A| = \text{trace}(\ln(A))$ and Theorem A.18.

Now, by using the fact that $(w_t - w)^\top A_t (w_t - w) \le (\tilde w_t - w)^\top A_t (\tilde w_t - w)$, we obtain

$(w_t - w)^\top A_t (w_t - w) \le (w_{t-1} - w)^\top A_{t-1} (w_{t-1} - w)$
$\quad + 2\eta[\ell_t(w) - \ell_t(w_{t-1})] + \eta^2[\ln|A_t| - \ln|A_{t-1}|]$.

We can now sum over $t = 1$ to $t = T$:

$(w_T - w)^\top A_T (w_T - w) \le (w_0 - w)^\top A_0 (w_0 - w)$
$\quad + 2\eta \sum_{t=1}^{T}[\ell_t(w) - \ell_t(w_{t-1})] + \eta^2[\ln|A_T| - \ln|A_0|]$. 

This implies the desired bound.

Using Proposition 15.8, we obtain a regret bound that is logarithmic in $T$ for ONS. If we let $A_0 = \lambda I$, then

$\sum_{t=1}^{T} \ell_t(w_{t-1}) \le \inf_{w \in \Omega} \left[ \sum_{t=1}^{T} \ell_t(w) + \frac{\lambda}{2\eta} \|w - w_0\|_2^2 \right] + \frac{\eta d}{2} \ln\left(1 + \frac{T G^2}{d \lambda}\right)$.

If $\ell_t(w) = L(f(w, X_t), Y_t)$ with $(X_t, Y_t) \sim \mathcal{D}$, then this implies the following online to batch conversion bound for $s$ randomly chosen from $0$ to $T-1$:

$\mathbb{E}_{S_T} \mathbb{E}_s \mathbb{E}_{\mathcal{D}} L(f(w_s, X), Y) \le \inf_{w \in \Omega} \left[ \mathbb{E}_{\mathcal{D}} L(f(w, X), Y) + \frac{\lambda}{2\eta T} \|w - w_0\|_2^2 \right]$ 
$\quad + \frac{\eta d}{2T} \left(1 + \frac{T G^2}{d \lambda}\right)$.