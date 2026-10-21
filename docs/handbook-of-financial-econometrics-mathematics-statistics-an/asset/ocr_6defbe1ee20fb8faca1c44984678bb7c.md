Following the definition of $M_t^{t+1}$ and some derivative calculations, the marginal rate of substitution $M_t^{t+1}$ is

$$M_t^{t+1}(l,m,n)=\frac{e^{-\beta\phi_{t+1}(c_{t+1}-v_{t+1})}-\delta wE_t[e^{-\beta\phi_{t+2}(c_{t+2}-v_{t+2})}]}{e^{-\beta\phi_t(c_t-v_t)}-\delta wE_t[e^{-\beta\phi_{t+1}(c_{t+1}-v_{t+1})}]}\tag{48.11}$$

Following equation (48.11) and equations (48.9) and (48.10), the pricing equations of the returns of assets can be rewritten as follows⁹:

$$R_{t+1}^{B}E_t[\delta M_t^{t+1}(l,m,n)]=1,\tag{48.12}$$

$$E_t\left[\delta\frac{D_{t+1}}{D_t}\left(1+\frac{P_{t+1}^{s}}{D_{t+1}}\right)M_t^{t+1}(l,m,n)\right]=\frac{P_t^{s}}{D_t}.\tag{48.13}$$

Like the original consumption-based asset pricing model, we assume the growth rate of both individual consumption and aggregate consumption per capita follow the same distribution:

$$\ln\frac{c_{t+1}}{c_t}=\ln\frac{\overline{c}_{t+1}}{\overline{c}_t}=g_t^{t+1}=\mu_{g_t}^{t+1}+z_g,\quad z_g\sim\mathcal{N}(0,\sigma_{g_t}^{t+1}).\tag{48.14}$$

In Mehra and Prescott (1985), they use not only $\mu_{g_t}^{t+1}$ and $z_g$ to describe the consumption process, but also the correlation between $g_t^{t+1}$ and $g_{t-1}^{t}$. Following their approach, we also take $\operatorname{corr}(g_t^{t+1},g_{t-1}^{t})=\rho_{gg}$ into consideration.

In our model, dividend growth is not assumed to follow the same distribution as consumption growth, so another lognormal distribution for dividend growth process is assumed. In addition, it is assumed that there is an imperfect correlation between consumption and dividend growth processes. We assume

$$\ln\frac{D_{t+1}}{D_t}=y_t^{t+1}=\mu_{t}^{t+1}+z_y,\quad z_y\sim\mathcal{N}(0,\sigma_{y_t}^{t+1}),\quad\text{and}\quad\operatorname{corr}(z_y,z_g)=\rho_{yg}.\tag{48.15}$$

In the equation (48.15), the means of the consumption growth and dividend growth are the same, but the standard deviations of these two processes are different. This is because the consumption and dividend streams will ultimately share the same trend in the long run, but the volatilities of these two streams are not the same.

⁹ If treating the risky security as a pure consumption stream, the corresponding equation is

$$E_t\left[\delta\frac{c_{t+1}}{c_t}\left(1+\frac{P_{t+1}^{s}}{c_{t+1}}\right)M_t^{t+1}(l,m,n)\right]=\frac{P_t^{s}}{c_t}.$$