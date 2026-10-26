
Proof Note that by employing the moment estimation of Bennett’s inequality in Lemma 2.20, we obtain

$$\frac{1}{\lambda}\ln\mathbb{E}_{Z_t^{(y)}}e^{-\lambda f(Z_t)}\le -\mathbb{E}_{Z_t^{(y)}}[f(Z_t)]+\lambda\phi(\lambda b)\mathrm{Var}_{Z_t^{(y)}}[f(Z_t)]$$ $$\le -\mathbb{E}_{Z_t^{(y)}}[f(Z_t)]+\lambda\phi(\lambda b)[c_0^2+c_1\mathbb{E}_{Z_t^{(y)}}[f(Z_t)]]$$

We can now obtain the desired bound from Theorem 13.11.

## Example 13.13

We consider least squares regression of Example 3.18, with $(x,y)=(Z^{(x)},Z^{(y)})$. In the realizable case, the variance condition is satisfied with $c_0=0$, $c_1=2M^2$, and $b=2M^2$. If we choose $\lambda=0.2M^{-2}$, then $\lambda c_1\phi(\lambda b)<0.5$. Corollary 13.12 implies that with probability $1-\delta$, for all $\phi\in\mathcal{G}$,

$$\sum_{i=1}^n\mathbb{E}_{Z_t^{(y)}}[\phi(Z_t)]\le 2\sum_{i=1}^n\phi(Z_t)+\inf_{\epsilon>0}\left[4n\epsilon+10M^2\ln\left(M(\epsilon,\mathcal{G},\|\cdot\|_\infty)/\delta\right)\right]$$

Since $(f(x)-y)^2$ is a $2M$ Lipschitz in $f(x)$, we obtain

$$\sum_{i=1}^n\mathbb{E}_{Z_t^{(y)}}[\phi(Z_t)]\le 2\sum_{i=1}^n\phi(Z_t)+\inf_{\epsilon>0}\left[8nM\epsilon+10M^2\ln\left(M(\epsilon,\mathcal{F},\|\cdot\|_\infty)/\delta\right)\right]$$

Note that the result of Theorem 13.11 can be improved using chaining with $L_\infty$ cover. Similar to Proposition 4.20, we have the following result (see Exercise 13.4).

## Proposition 13.14

Consider a bounded function class $\mathcal{F}$ such that $|f(Z)|\le b$ for all $f\in\mathcal{F}$. Then with probability $1-\delta$, for all $f\in\mathcal{F}$, we have

$$\frac{1}{n}\sum_{i=1}^n\mathbb{E}_{Z_i^{(y)}}[f(Z_i)]\le\frac{1}{n}\sum_{i=1}^n f(Z_i)+C\inf_{\epsilon_0>0}\left[\epsilon_0+\int_0^\infty\sqrt{\frac{\ln(M(\epsilon,\mathcal{F},\|\cdot\|_\infty))}{n}}d\epsilon\right]+b\sqrt{\frac{\ln(1/\delta)}{n}}$$ where $C$ is an absolute constant.

## Theorem 13.15

Let $\{(X_t,\epsilon_t)\}$ be a filtered sequence in $\mathcal{X}\times\mathbb{R}$ so that $\epsilon_t$ is conditional zero-mean sub-Gaussian noise: for all $\lambda\in\mathbb{R}$, $\ln\mathbb{E}[e^{\lambda\epsilon_t}|X_t,\mathcal{S}_{t-1}]\le\frac{\lambda^2\sigma^2}{2}$

where $\mathcal{S}_{t-1}$ denotes the history data. Assume that $Y_t = f_*(X_t) + \epsilon_t$, with $f_*(x) \in \mathcal{F}: \mathcal{X} \to \mathbb{R}$. Let $\hat f_t$ be an approximate ERM solution for some $\epsilon' > 0$:

$$\left(\sum_{s=1}^{t}(\hat f_t(X_s)-Y_s)^2\right)^{1/2} \le \min_{f\in\mathcal{F}}\left(\sum_{s=1}^{t}(f(X_s)-Y_s)^2\right)^{1/2} + \sqrt{t}\epsilon' .$$

Then with probability at least $1 - \delta$, for all $t \ge 0$,

$$\sum_{s=1}^{t}(\hat f_t(X_t)-f_*(X_t))^2 \le \inf_{\epsilon>0}\Big[8t(\epsilon+\epsilon')(\sigma+2\epsilon+2\epsilon')+12\sigma^2\ln\frac{2N(\epsilon,\mathcal{F},\|\cdot\|_\infty)}{\delta}\Big].$$

Proof Let $\eta = \sigma^{-2}/4$, and for $f \in \mathcal{F}$, let

$$\phi(f,Z_t)=[(f(X_t)-Y_t)^2-(f_*(X_t)-Y_t)^2].$$

Let $\mathcal{F}_\epsilon$ be an $\epsilon \|\cdot\|_\infty$ cover of $\mathcal{F}$ with $N = N(\epsilon,\mathcal{F},\|\cdot\|_\infty)$ members.

Given any $f \in \mathcal{F}_\epsilon$,

$$\begin{aligned}
\ln \mathbb{E}_{Y_t|X_t,\mathcal{S}_{t-1}} \exp(-\eta\phi(f,Z_t)) &= -\eta(f(X_t)-f_*(X_t))^2 \\
&+ \ln \mathbb{E}_{Y_t|X_t,\mathcal{S}_{t-1}} \exp(-2\eta(f(X_t)-f_*(X_t))(f_*(X_t)-Y_t)) \\
&\le -\eta(f(X_t)-f_*(X_t))^2 + \frac{4\eta^2\sigma^2}{2}(f(X_t)-f_*(X_t))^2 \\
&= -\frac{(f(X_t)-f_*(X_t))^2}{8\sigma^2}.
\end{aligned}$$

The inequality used the sub-Gaussian noise assumption. It follows from Theorem 13.11 that with probability at least $1 - \delta/2$, for all $f \in \mathcal{F}_\epsilon$ and $t \ge 0$,

$$\sum_{i=1}^{t} -\eta\phi(f,Z_i) \le -\sum_{i=1}^{t}\frac{(f(X_i)-f_*(X_i))^2}{8\sigma^2} + \ln(2N/\delta). \qquad (13.5)$$

Using Exercise 13.3, we have with probability at least $1 - \delta/2$, for all $t \ge 0$,

$$\underbrace{\sum_{i=1}^{t}(f_*(X_i)-Y_i)^2}_{A} \le 2t\sigma^2 + 3\sigma^2\ln(2/\delta). \qquad (13.6)$$

It follows that with probability at least $1 - \delta$, for all $t \ge 0$ and $f \in \mathcal{F}_\epsilon$, both $(13.5)$ and $(13.6)$ hold. Now, let $f \in \mathcal{F}_\epsilon$ so that $\|\hat f_t - f\|_\infty \le \epsilon$. This implies that

$$\sum_{i=1}^t [(f(X_i)-Y_i)^2 - (f_*(X_i)-Y_i)^2] \le \left( \sqrt{\sum_{i=1}^t (\hat f_t(X_i)-Y_i)^2 + \sqrt{t}\epsilon } \right)^2 - A$$
$$\le \left( \sqrt{A} + \sqrt{t}(\epsilon + \epsilon') \right)^2 - A$$
$$\stackrel{(a)}{\le} (\epsilon' + \epsilon)^2 t + 2\sqrt{t}(\epsilon' + \epsilon)\sigma \sqrt{2t + 3\ln(2/\delta)}$$
$$\le 4(\epsilon' + \epsilon)^2 t + 3\sigma t(\epsilon' + \epsilon) + \sigma^2 \ln(2/\delta). \tag{13.7}$$

In the derivations, the first inequality used $|f(X_i)-Y_i| \le |\hat f_t(X_i)-Y_i| + \epsilon$ for all $i$. The second inequality used the fact that $\hat f_t$ is approximate ERM. $(a)$ follows from $(13.6)$. The last inequality used $2a\sigma\sqrt{2b}+3c \le 3a\sigma\sqrt{b}+3a^2+\sigma^2 c$. We thus obtain

$$\left( \sum_{i=1}^t (\hat f(X_i)-f_*(X_i))^2 \right)^{1/2}$$
$$\le \sqrt{\epsilon t} + \left( \sum_{i=1}^t (f(X_i)-f_*(X_i))^2 \right)^{1/2} \quad \text{(triangle inequality)}$$
$$\le \sqrt{\epsilon^2 t} + \left( 8\sigma^2 \ln(2N/\delta) + 8\sigma^2 \sum_{i=1}^t \eta\phi(f,Z_i) \right)^{1/2} \quad \text{(from (13.5))}$$
$$= \sqrt{\epsilon^2 t} + \left( 8\sigma^2 \ln(2N/\delta) + 2 \sum_{i=1}^t [(f(X_i)-Y_i)^2 - (f_*(X_i)-Y_i)^2] \right)^{1/2}$$
$$\le \sqrt{\epsilon^2 t} + (10\sigma^2 \ln(2N/\delta) + 8t(\epsilon' + \epsilon)^2 + 6\sigma t(\epsilon' + \epsilon))^{1/2} \quad \text{(from (13.7))}$$
$$\le (12\sigma^2 \ln(2N/\delta) + 16t(\epsilon + \epsilon')^2 + 8\sigma t(\epsilon + \epsilon'))^{1/2},$$

where the last inequality used $\sqrt{a}+\sqrt{b} \le \sqrt{6a + 1.2b}$. This implies the bound. $\square$

## 13.4 Minimax Analysis for Sequential Statistical Estimation

We may consider a generalization of the statistical estimation problem in Section 12.2 for supervised learning to the sequential decision setting.

Consider a general sequential estimation problem, where we observe data $Z_t \in \mathcal{Z}$ from the environment by interacting with the environment using a sequence of learned policies $\pi_t \in \Pi$. At each time $t$, the observation history is $\mathcal{S}_{t-1} = [(Z_1,\pi_1),..., (Z_{t-1},\pi_{t-1})]$. Based on the history, the player (or learning algorithm), denoted by $\hat q$, determines the next policy $\pi_t \in \Pi$ that can interact with the environment. Based on the policy $\pi_t$, environment generates the next observation $Z_t \in \mathcal{Z}$ according to an unknown distribution $q(Z_t|\pi_t,\mathcal{S}_{t-1})$.

In the sequential decision literature, the symbol $\mathcal{A}$ is often used to denote the action space of the learning algorithm. We will follow this convention, and thus will use the symbol $\hat q$ to denote a learning algorithm. The following definition summarizes the sequential statistical estimation problem in the realizable case.

## **Definition 13.16 (Sequential Statistical Estimation)**

Consider a family of environment distributions $\mathcal P_Z$, where each $q\in\mathcal P_Z$ determines the probability for generating $Z_t$ based on policy $\pi_t$ as $q(Z_t\mid\pi_t,S_{t-1})$. Consider also a family of learning algorithms, represented by $\mathcal P_A$. Each learning algorithm $\hat q\in\mathcal P_A$ maps the history $S_{t-1}$ deterministically to the next policy $\pi_t\in\Pi$ as $\pi_t=\hat q(S_{t-1})$. Given $q\in\mathcal P_Z$, and $\hat q\in\mathcal P_A$, the data generation probability is fully determined as

$$p(S_n\mid\hat q,q)=\prod_{t=1}^{n}q\bigl(Z_t\mid\hat q(S_{t-1}),S_{t-1}\bigr).$$

After observing $S_n$ for some $n$, the learning algorithm $\hat q$ determines a distribution $\hat q(\theta\mid S_n)$, and draw estimator $\theta\in\Theta$ according to $\hat q(\theta\mid S_n)$. The learning algorithm suffers a loss (also referred to as regret) $Q(\theta,q)$. The overall probability of $\theta$ and $S_n$ is

$$p(\theta,S_n\mid\hat q,q)=\hat q(\theta\mid S_n)\prod_{t=1}^{n}q\bigl(Z_t\mid\hat q(S_{t-1}),S_{t-1}\bigr).\tag{13.8}$$

Note that although the notation in Definition 13.16 assumes that $\pi_t$ is a deterministic function of $S_{t-1}$, it can also incorporate randomized algorithms. In such case, a policy is simply a distribution over the random choices. Since a random choice can always be characterized by a distribution (over the random choices) that is a deterministic function of $S_{t-1}$, when we consider *random policies* in subsequent chapters, it should be understood that such policies can be handled by Definition 13.16. An example follows.

## **Example 13.17 (Online Learning (Non-adversarial))**

We consider a parameter space $\Omega$, and at each time $t$, the learning algorithm chooses a parameter $w_t\in\Omega$ according to a probability distribution $\pi_t(\cdot)$ on $\Omega$. This probability distribution is the policy. Given $w_t\sim\pi_t$, we then observe a $Z_t\sim q_t$ from an unknown distribution $q_t$. We assume that the loss function $\ell$ is known. After $n$ rounds, let $\theta(S_n)=[\pi_1,\ldots,\pi_n]$, and we suffer a loss

$$Q(\theta,q)=\sum_{t=1}^{n}\mathbb E_{w_t\sim\pi_t}\mathbb E_{Z_t\sim q_t}\ell(w_t,Z_t)-\inf_{w\in\Omega}\sum_{t=1}^{n}\mathbb E_{Z\sim q_t}\ell(w,Z).$$

In non-adversarial online learning, the policy $\pi_t$ only affects the final loss, but does not affect the observation $Z_t$. However, for some problems, the policy taken by the learning algorithm may affect the next observation. Such problems are usually more complex to analyze.

## **Example 13.18 (MAB)**

We consider the multiarmed bandit problem, where we have $K$ arms from $\mathcal A=\{1,\ldots,K\}$. For each arm $a\in\mathcal A$, we have a probability distribution $q_a$ on $[0,1]$. If we pull an arm $a\in\mathcal A$, we observe a random reward
