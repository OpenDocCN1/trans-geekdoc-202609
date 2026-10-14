
我们可以通过使用 $p$ 和 $q$ 的分解来扩展下界（参见 David M. Blei、Andrew Y. Ng 和 Michael I. Jordan 的“潜在狄利克雷分配”，*Journal of Machine Learning Research*，2003）。

$$L(\gamma,\phi;\alpha,\beta)=E_q[\log p(\theta|\alpha)]+E_q[\log p(z|\theta)] +E_q[\log p(x|z,\beta)] -E_q[\log q(\theta)]-E_q[\log q(z)] \tag{9.6}$$

$L(\gamma,\phi;\alpha,\beta)$ 中的五个项可以按如下方式展开。

$$\begin{aligned}
L(\gamma,\phi;\alpha,\beta)={}&\log\Gamma\left(\sum_{j=1}^{k}\alpha_j\right)-\sum_{i=1}^{k}\log\Gamma(\alpha_i)\\
&+\sum_{i=1}^{k}(\alpha_i-1)\left(\Psi(\gamma_i)-\Psi\left(\sum_{j=1}^{k}\gamma_j\right)\right)\\
&+\sum_{n=1}^{N}\sum_{i=1}^{k}\phi_{ni}\left(\Psi(\gamma_i)-\Psi\left(\sum_{j=1}^{k}\gamma_j\right)\right)\\
&+\sum_{n=1}^{N}\sum_{i=1}^{k}\sum_{j=1}^{K}\phi_{ni}x_n^j\log\beta_{ij}\\
&-\log\Gamma\left(\sum_{j=1}^{k}\gamma_j\right)+\sum_{i=1}^{k}\log\Gamma(\gamma_i)\\
&-\sum_{i=1}^{k}(\gamma_i-1)\left(\Psi(\gamma_i)-\Psi\left(\sum_{j=1}^{k}\gamma_j\right)\right)\\
&-\sum_{n=1}^{N}\sum_{i=1}^{k}\phi_{ni}\log\phi_{ni}
\end{aligned}\tag{9.7}$$

这里，$\Psi(x)=d/dx\ \log\Gamma(x)$ 是 digamma 函数。$L(\gamma,\phi;\alpha,\beta)$ 可以通过对变分参数 $\phi$、$\gamma$、$\alpha$ 进行坐标上升来最大化。

$$\begin{aligned}
\phi_{dwk}&\propto\exp\left\{E_q[\log\theta_{dk}]+E_q[\log\beta_{kw}]\right\}\\
\gamma_{dk}&=\alpha+\sum_w n_{dw}\phi_{dwk}\\
\lambda_{kw}&=\eta+\sum_d n_{dw}\phi_{dwk}
\end{aligned}\tag{9.8}$$

这里，q 下 log θ 和 log β 的期望如下。

E_q[log θ_dk] = Ψ(γ_dk) − Ψ(∑_{i=1}^K γ_di)

E_q[log β_kw] = Ψ(λ_kw) − Ψ(∑_{i=1}^W λ_ki)      (9.9)

变分参数更新可以在无需在每次迭代中对整个语料库进行完整遍历的在线设置中使用。变分参数的在线更新使得对非常大的数据集（包括流数据）进行主题分析成为可能。LDA 的在线变分贝叶斯（VB）在图 9.2 的算法中进行了描述。

- 1: 定义 ρ_t = (τ₀ + t)^{-κ}
- 2: 随机初始化 λ
- 3: 对于 t = 1 到 ∞ 执行
- 4: E 步：
- 5: 初始化 γ_ik = 1
- 6: 重复
- 7: 设置 φ_{twk} ∝ exp{E_q[log θ_{tk}] + E_q[log β_{kw}]} ← 主题分配
- 8: 设置 γ_{ik} = α + Σ_{w} φ_{twk} n_{tw} ← 主题比例
- 9: 直到 1/K Σ_k |Δγ_{ik}| < ε
- 10: M 步：
- 11: 计算 \tilde λ_{kw} = η + D n_{tw} φ_{twk}
- 12: 设置 λ = (1 − ρ_t) λ + ρ_t \tilde λ
- 13: 结束循环

## 图 9.2 LDA 算法伪代码

当第 t 个词频向量 n_t 被观测到时，我们执行 E 步，在保持 λ 固定的情况下找到 γ_t 和 φ_t 的局部最优值。然后我们计算 \tilde λ，即如果我们的整个语料库仅由单个文档 n 重复 D 次组成时最优的 \tilde λ。然后我们将 λ 更新为其先前值和 \tilde λ 的加权平均值，其中权重由学习参数 ρ_t 给出，κ ∈ (0.5, 1]，控制旧的 \tilde λ 值被遗忘的速率。我们现在准备从头开始实现 LDA 的变分贝叶斯，代码如下！

## Listing 9.1 变分贝叶斯用于潜在狄利克雷分配

```
import numpy as np
import matplotlib.pyplot as plt
from sklearn.datasets import fetch_20newsgroups
from sklearn.feature_extraction.text import TfidfVectorizer
from wordcloud import WordCloud
from scipy.special import digamma, gammaln
```

```
np.random.seed(12)

class LDA:
    def __init__(self, A, K):
        self.N = A.shape[0]
        self.D = A.shape[1]
        self.K = K

        self.A = A

        #init word distribution beta
        self.eta = np.ones(self.N)
        self.beta = np.zeros((self.N, self.K))
        for k in range(self.K):
            self.beta[:,k] = np.random.dirichlet(self.eta)
            self.beta[:,k] = self.beta[:,k] + 1e-6 #to avoid zero entries
            self.beta[:,k] = self.beta[:,k]/np.sum(self.beta[:,k])
        #end for

        #init topic proportions theta and cluster assignments z
        self.alpha = np.ones(self.K)
        self.z = np.zeros((self.N, self.D))
        for d in range(self.D):
            theta = np.random.dirichlet(self.alpha)
            wdn_idx = np.nonzero(self.A[:,d])[0]
            for i in range(len(wdn_idx)):
                z_idx = np.argmax(np.random.multinomial(1, theta))
                self.z[wdn_idx[i],d] = z_idx  #topic id
            #end for
        #end for

        #init variational parameters
        self.gamma = np.ones((self.D, self.K))
        for d in range(self.D):
            theta = np.random.dirichlet(self.alpha)
            self.gamma[d,:] = theta
        #end for

        self.lmbda = np.transpose(self.beta)
        #np.ones((self.K, self.N))/self.N

        self.phi = np.zeros((self.D, self.N, self.K))
        for d in range(self.D):
            for w in range(self.N):
                theta = np.random.dirichlet(self.alpha)
                self.phi[d,w,:] = np.random.multinomial(1, theta)
            #end for
        #end for

    def variational_inference(self, var_iter=10):

        llh = np.zeros(var_iter)
        llh_delta = np.zeros(var_iter)
```

```
for iter in range(var_iter):
    print("VI iter: ", iter)
    J_old = self.elbo_objective()
    self.mean_field_update()
    J_new = self.elbo_objective()

    llh[iter] = J_old
    llh_delta[iter] = J_new - J_old
#end for

#update alpha and beta
for k in range(self.K):
    self.alpha[k] = np.sum(self.gamma[:,k])
    self.beta[:,k] = self.lmbda[k,:] / np.sum(self.lmbda[k,:])
#end for

#update topic assignments
for d in range(self.D):
    wdn_idx = np.nonzero(self.A[:,d])[0]
    for i in range(len(wdn_idx)):
        z_idx = np.argmax(self.phi[d,wdn_idx[i],:])
        self.z[wdn_idx[i],d] = z_idx  #topic id
    #end for
#end for

plt.figure()
plt.plot(llh); plt.title('LDA VI');
plt.xlabel('mean field iterations'); plt.ylabel("ELBO")
plt.show()

return llh

def mean_field_update(self):
    ndw = np.zeros((self.D, self.N))
    for d in range(self.D):
        doc = self.A[:,d]
        wdn_idx = np.nonzero(doc)[0]

        for i in range(len(wdn_idx)):
            ndw[d,wdn_idx[i]] += 1
        #end for

        #update gamma
        for k in range(self.K):
            self.gamma[d,k] = self.alpha[k] + np.dot(ndw[d,:],
                                                     self.phi[d,:,k])
        #end for

        #update phi
        for w in range(len(wdn_idx)):
            self.phi[d,wdn_idx[w],:] = np.exp(digamma(self.gamma[d,:])
                                              - digamma(np.sum(self.gamma[d,:])) + digamma(self.lmbda[:,wdn_idx[w]])
                                              - digamma(np.sum(self.lmbda, axis=1)))
            if (np.sum(self.phi[d,wdn_idx[w],:]) > 0): #to avoid 0/0
self.phi[d,wdn_idx[w],:] = self.phi[d,wdn_idx[w],:] /
    np.sum(self.phi[d,wdn_idx[w],:]) #normalize phi
#end if
#end for

#end for

#update lambda given ndw for all docs
for k in range(self.K):
    self.lmbda[k,:] = self.eta
    for d in range(self.D):
        self.lmbda[k,:] += np.multiply(ndw[d,:], self.phi[d,:,k])
    #end for
#end for

def elbo_objective(self):
    #see Blei 2003

T1_A = gammaln(np.sum(self.alpha)) - np.sum(gammaln(self.alpha))
T1_B = 0
for k in range(self.K):
    T1_B += np.dot(self.alpha[k]-1, digamma(self.gamma[:,k]) -
        digamma(np.sum(self.gamma, axis=1)))
T1 = T1_A + T1_B

T2 = 0
for n in range(self.N):
    for k in range(self.K):
        T2 += self.phi[:,n,k] * (digamma(self.gamma[:,k]) -
            digamma(np.sum(self.gamma, axis=1)))

T3 = 0
for n in range(self.N):
    for k in range(self.K):
        T3 += self.phi[:,n,k] * np.log(self.beta[n,k])

T4 = 0
T4_A = -gammaln(np.sum(self.gamma, axis=1)) +
    np.sum(gammaln(self.gamma), axis=1)
T4_B = 0
for k in range(self.K):
    T4_B = -(self.gamma[:,k]-1) * (digamma(self.gamma[:,k]) -
        digamma(np.sum(self.gamma, axis=1)))
T4 = T4_A + T4_B

T5 = 0
for n in range(self.N):
    for k in range(self.K):
        T5 += -np.multiply(self.phi[:,n,k], np.log(self.phi[:,n,k]
            + 1e-6))

T15 = T1 + T2 + T3 + T4 + T5
J = sum(T15)/self.D  #averaged over documents
return J
```
