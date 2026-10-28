First, by Cauchy–Schwarz inequality, as $2a_1a_2 \le \frac{1}{a_3}(a_1)^2 + a_3(a_2)^2$, $\forall a_3 > 0$, we obtain that

$$2|\langle \xi_{t-1}, \nabla \mathcal{L}_H(\theta_{t-1})\rangle| \le 2\|\xi_{t-1}\|\|\nabla \mathcal{L}_H(\theta_{t-1})\| \le 2\|\xi_{t-1}\|^2 + \frac12\|\nabla \mathcal{L}_H(\theta_{t-1})\|^2. \tag{6.21}$$ 

Second, similarly to (6.21), we obtain that

$$2|\langle \delta_{t-1}, \nabla \mathcal{L}_H(\theta_{t-1})\rangle| \le 2\|\delta_{t-1}\|^2 + \frac12\|\nabla \mathcal{L}_H(\theta_{t-1})\|^2. \tag{6.22}$$ 

Last, using the triangle and Jensen’s inequalities, we obtain that

$$\|\mathbf{m}_{t-1}^H + \delta_{t-1}\|^2 \le 2\|\mathbf{m}_{t-1}^H\|^2 + 2\|\delta_{t-1}\|^2.$$

Substituting $\mathbf{m}_{t-1}^H = \nabla \mathcal{L}_H(\theta_{t-1}) + \xi_{t-1}$, and repeating the above reasoning due to the triangle and Jensen’s inequalities, we obtain that

$$\|\mathbf{m}_{t-1}^H + \delta_{t-1}\|^2 \le 4\|\xi_{t-1}\|^2 + 4\|\nabla \mathcal{L}_H(\theta_{t-1})\|^2 + 2\|\delta_{t-1}\|^2. \tag{6.23}$$ 

From (6.21), (6.22), and (6.23), we obtain that

$$-\langle \xi_{t-1}, \nabla \mathcal{L}_H(\theta_{t-1})\rangle - \langle \delta_{t-1}, \nabla \mathcal{L}_H(\theta_{t-1})\rangle + \gamma_{t-1}\frac{L}{2}\|\mathbf{m}_{t-1}^H + \delta_{t-1}\|^2 \le$$

$$(1 + 2\gamma_{t-1}L)\|\xi_{t-1}\|^2 + (1 + \gamma_{t-1}L)\|\delta_{t-1}\|^2$$

$$+ \left(\frac12 + 2\gamma_{t-1}L\right)\|\nabla \mathcal{L}_H(\theta_{t-1})\|^2.$$

Multiplying both sides by $\gamma_{t-1}$ and then plugging the resulting inequality in (6.20) conclude the proof.

# Complications Due to Momentum Deviation

We note that, compared to the case of Robust DMGD, the loss function growth in Robust DMHB depends on an additional quantity that is the momentum deviation $\xi_t$. Recall, from Lemma 6.3, that we do not have, unlike the aggregation error in Lemma 6.2, a uniform bound on momentum deviation at our disposal, which makes the convergence analysis of Algorithm 6 more intricate. To overcome this challenge, we resort to the general technique of Lyapunov analysis. Essentially, in Lyapunov