with
$a_1(\boldsymbol{u}) = 2\mathbb{E}_\mathcal{D}\big[\{\Re\big[(\boldsymbol{H}\boldsymbol{x}_\mathcal{M})^\mathrm{H}\boldsymbol{u}\big]\}^2\big] - \mathbb{E}_\mathcal{D}\big[\|\boldsymbol{H}\boldsymbol{x}_\mathcal{M}\|^2\big],\quad(20)$
$a_2(\boldsymbol{u}) = \tfrac12\mathbb{E}_\mathcal{D}\big[\|\boldsymbol{H}\boldsymbol{x}_\mathcal{M}\|^4\big] + \tfrac23\mathbb{E}_\mathcal{D}\big[\{\Re\big[(\boldsymbol{H}\boldsymbol{x}_\mathcal{M})^\mathrm{H}\boldsymbol{u}\big]\}^4\big] - 2\mathbb{E}_\mathcal{D}\big[\{\Re\big[(\boldsymbol{H}\boldsymbol{x}_\mathcal{M})^\mathrm{H}\boldsymbol{u}\big]\}^2\|\boldsymbol{H}\boldsymbol{x}_\mathcal{M}\|^2\big].\quad(21)$

In order to evaluate (19), we use the two properties
$\mathbb{E}_{\boldsymbol{u}}\big[\{\Re[\boldsymbol{a}^\mathrm{H}\boldsymbol{u}]\}^2\big]=\tfrac12\|\boldsymbol{a}\|^2,\quad \mathbb{E}_{\boldsymbol{u}}\big[\{\Re[\boldsymbol{a}^\mathrm{H}\boldsymbol{u}]\}^4\big]=\tfrac34\|\boldsymbol{a}\|^4,\quad(22)$
for any $\boldsymbol{a}\in\mathbb{C}^N$. Exchanging the two expectations $\mathbb{E}_\mathcal{D}[\cdot]$ and $\mathbb{E}_{\boldsymbol{u}}[\cdot]$ in (19), we find $\mathbb{E}_{\boldsymbol{u}}[a_i(\boldsymbol{u})]=0$ for $i=1,2.$

Calculating the expectation in (20) with respect to $\boldsymbol{x}_\mathcal{M}$ with $\mathbb{E}[x_m x_{m'}]=0$ for all $m$ and $m'$ yields
$a_1(\boldsymbol{u}) = \operatorname{Tr}\big\{\boldsymbol{H}\mathbb{E}_{\mathcal{M}_t}[\boldsymbol{\Sigma}_\mathcal{M}]\boldsymbol{H}^\mathrm{H}(\boldsymbol{u}\boldsymbol{u}^\mathrm{H}-\boldsymbol{I}_N)\big\}.\quad(23)$

Evaluating$^1$ the average of $a_1(\boldsymbol{u})^2$ over $\boldsymbol{u}\sim\mathcal{CN}(\boldsymbol{0},\boldsymbol{I}_N)$, we obtain $\mathbb{E}_{\boldsymbol{u}}[a_1(\boldsymbol{u})^2]=\operatorname{Tr}\{\big(\boldsymbol{H}\mathbb{E}_{\mathcal{M}}[\boldsymbol{\Sigma}_\mathcal{M}]\boldsymbol{H}^\mathrm{H}\big)^2\}$. From these observations, we find that (19) reduces to (18) to be proved.

# APPENDIX B

# PROOF OF THEOREM 2

The proof is an application of [14]. Using the chain rule [15] for mutual information, from (9) we obtain
$C_{\mathrm{FGSM}}(\gamma)=(\delta(\gamma)/T)\{I(\{\mathcal{D}_t\},\boldsymbol{H};\boldsymbol{Y})-I(\boldsymbol{H};\boldsymbol{Y}|\{\mathcal{D}_t\})\}$
$=\delta(\gamma)\big\{C_{\mathrm{GSM}}^{\mathrm{CSI}}(\gamma')+T^{-1}[I(\boldsymbol{H};\boldsymbol{Y})-I(\boldsymbol{H};\boldsymbol{Y}|\{\mathcal{D}_t\})]\big\}$
$\ge \delta(\gamma)C_{\mathrm{GSM}}(\gamma'),\quad(25)$
with
$C_{\mathrm{GSM}}(\gamma')=C_{\mathrm{GSM}}^{\mathrm{CSI}}(\gamma')-\tfrac1T I(\boldsymbol{H};\boldsymbol{Y}|\{\mathcal{D}_t\}),\quad(26)$
where $C_{\mathrm{GSM}}^{\mathrm{CSI}}(\gamma')$ denotes the ergodic coherent achievable rate $T^{-1}I(\{\mathcal{D}_t\};\boldsymbol{Y}|\boldsymbol{H})$ for SNR $\gamma'$. In (26), the second term is interpreted as the penalty due to channel uncertainty.

The upper bound (28) is $o(\gamma'^2)$ if (3) holds for some $\epsilon>0$ [14, Eq. (9)]. From (25) and (26) we obtain the lower bound $C_{\mathrm{FGSM}}(\gamma)\ge C_{\mathrm{GSM}}^{\mathrm{CSI}}(\gamma)+o(\gamma'^2)$. Combining the lower bound and the trivial upper bound $C_{\mathrm{FGSM}}(\gamma)\le C_{\mathrm{opt}}(\gamma)$ given by (2), from Corollary 1 we arrive at (10) for $\alpha=1.$

Assume $\alpha\in(0,1)$. We have already proved that
$C_{\mathrm{GSM}}(\gamma')=N\gamma'-\dfrac{N(M+N)}{2M}\gamma'^2+o(\gamma'^2),\quad(29)$
if $T=M^2(M+N)^{-2}\gamma'^{-2(1+\epsilon)}$ for some $\epsilon>0$. From $\delta(\gamma)=\gamma^{1-\alpha}$ and $\gamma'=\gamma/\delta(\gamma)$, this is equivalent to
$\delta(\gamma)C_{\mathrm{GSM}}(\gamma')=N\gamma-\dfrac{N(M+N)}{2M}\gamma^{1+\alpha}+o(\gamma^{1+\alpha}),\quad(30)$
if $T=M^2(M+N)^{-2}\gamma^{-2\alpha(1+\epsilon')}$. Thus, from (25) we obtain Theorem 2 by letting $\epsilon=\alpha\epsilon'.$

# REFERENCES

+   [1] R. Y. Mesleh, H. Haas, S. Sinanović, C. W. Ahn, and S. Yun, “Spatial modulation,” IEEE Trans. Veh. Technol., vol. 57, no. 4, pp. 2228–2241, Jul. 2008.
+   [2] A. Stavridis, S. Sinanović, M. Di Renzo, and H. Haas, “Energy evaluation of spatial modulation at a multi-antenna base station,” in Proc. IEEE 78th Veh. Technol. Conf., Las Vegas, NV, USA, Sep. 2013, pp. 1–5.
+   [3] M. Di Renzo, H. Haas, A. Ghrayeb, S. Sugiura, and L. Hanzo, “Spatial modulation for generalized MIMO: Challenges, opportunities, and implementation,” Proc. IEEE, vol. 102, no. 1, pp. 56–103, Jan. 2014.
+   [4] K. Takeuchi, “Spatial modulation achieves information-theoretically optimal energy efficiency,” IEEE Commun. Lett., vol. 19, no. 7, pp. 1133–1136, Jul. 2015.
+   [5] J. Jeganathan, A. Ghrayeb, and L. Szczecinski, “Generalized space shift keying modulation for MIMO channels,” in Proc. IEEE 19th Int. Symp. Pers., Indoor, Mobile Radio Commun., Cannes, France, Sep. 2008, pp. 1–5.
+   [6] A. Younis, N. Serafimovski, R. Mesleh, and H. Haas, “Generalised spatial modulation,” in Proc. 44th Asilomar Conf. Signals, Syst., Comput., Pacific Grove, CA, USA, Nov. 2010, pp. 1498–1502.
+   [7] S. Sugiura, S. Chen, and L. Hanzo, “Coherent and differential space-time shift keying: A dispersion matrix approach,” IEEE Trans. Commun., vol. 58, no. 11, pp. 3219–3230, Nov. 2010.
+   [8] M. Di Renzo, D. D. Leonardis, F. Graziosi, and H. Haas, “Space Shift Keying (SSK-) MIMO with practical channel estimates,” IEEE Trans. Commun., vol. 60, no. 4, pp. 998–1012, Apr. 2012.
+   [9] P. Zhang, S. Chen, and L. Hanzo, “Reduced-complexity near-capacity joint channel estimation and three-stage turbo detection for coherent space-time shift keying,” IEEE Trans. Commun., vol. 61, no. 5, pp. 1902–1913, May 2013.
+   [10] X. Wu, H. Claussen, M. Di Renzo, and H. Haas, “Channel estimation for spatial modulation,” IEEE Trans. Commun., vol. 62, no. 12, pp. 4362–4372, Dec. 2014.
+   [11] Y. Yang and B. Jiao, “Information-guided channel-hopping for high data rate wireless communication,” IEEE Commun. Lett., vol. 12, no. 4, pp. 225–227, Apr. 2008.
+   [12] S. Verdú, “Spectral efficiency in the wideband regime,” IEEE Trans. Inf. Theory, vol. 48, no. 6, pp. 1319–1343, Jun. 2002.
+   [13] V. V. Prelov and S. Verdú, “Second-order asymptotics of mutual information,” IEEE Trans. Inf. Theory, vol. 50, no. 8, pp. 1567–1580, Aug. 2004.
+   [14] S. Ray, M. Médard, and L. Zheng, “On noncoherent MIMO channels in the wideband regime: Capacity and reliability,” IEEE Trans. Inf. Theory, vol. 53, no. 6, pp. 1983–2009, Jun. 2007.
+   [15] T. M. Cover and J. A. Thomas, Elements of Information Theory, 2nd ed. Hoboken, NJ, USA: Wiley, 2006.
+   [16] T. L. Marzetta and B. M. Hochwald, “Capacity of a mobile multiple-antenna communication link in Rayleigh flat fading,” IEEE Trans. Inf. Theory, vol. 45, no. 1, pp. 139–157, Jan. 1999.
+   [17] M. Di Renzo and H. Haas, “Bit error probability of SM-MIMO over generalized fading channels,” IEEE Trans. Veh. Technol., vol. 61, no. 3, pp. 1124–1144, Mar. 2012.
+   [18] M. Maleki, H. R. Bahrami, A. Alizadeh, and N. H. Tran, “On the performance of spatial modulation: Optimal constellation breakdown,” IEEE Trans. Commun., vol. 62, no. 1, pp. 144–157, Jan. 2014.