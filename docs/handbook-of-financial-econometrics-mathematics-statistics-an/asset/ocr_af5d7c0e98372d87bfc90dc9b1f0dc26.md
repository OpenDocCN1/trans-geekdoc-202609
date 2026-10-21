form (41.4). Then we have

$$D(V,L)=\frac{A(m+b)}{m+r}\bigl(1-G_{m+r}(x)\bigr)+\beta L H_{m+r}(x),\tag{41.32}$$

and

$$v(V,L)=V+\frac{A\delta b}{r}\bigl(1-G_{r}(x)\bigr)-(1-\beta)L H_{r}(x),\tag{41.33}$$

where

$$G_{s}(x)=E_{x}\bigl[e^{-s\tau}\bigr].\tag{41.34}$$

and

$$H_{s}(x)=E_{x}\bigl[e^{-s\tau}e^{X_{\tau}}\bigr].\tag{41.35}$$

Hence, we obtain that

$$\frac{\partial S}{\partial V}(V,L)=\frac{\partial}{\partial V}\bigl(v(V,L)-D(V,L)\bigr)\\=1-\frac{\delta A b}{r}G'_{r}(x)\frac{1}{V}-(1-\beta)L H'_{r}(x)\frac{1}{V}\\ +\frac{A(m+b)}{m+r}G'_{m+r}(x)\frac{1}{V}-\beta L H'_{m+r}(x)\frac{1}{V}.$$

As in Hilberink and Rogers (2002), Leland and Toft (1996), by imposing the smooth-pasting condition (i.e., $\left.\frac{\partial S}{\partial V}(V,L)\right|_{V=L}=0$), we get the optimal default-triggering level

$$L^{*}=\frac{\frac{\delta A b}{r}G'_{r}(0)-\frac{A(m+b)}{m+r}G'_{m+r}(0)}{1-(1-\beta)H'_{r}(0)-\beta H'_{m+r}(0)}.\tag{41.36}$$

Assume further that X has only downward jumps and $\sigma>0$. (Indeed. In this case, Kyprianou and Surya (2007) proved that the optimal default-triggering level does satisfy the condition of smooth-pasting.) By taking $g(y)=e^{y}\mathbf{1}_{y\le0}$ in (41.29), we get

$$H'_{s}(0)=\frac{d}{dx}H_{s}(x)\Big|_{x=0}=-\frac{c}{D}-\rho_{s}^{*}+\frac{\lambda}{D}\int_{0}^{\infty}dv\int_{v}^{\infty}dF(y)e^{-\rho_{s}^{*}v e^{v-y}}$$

$$=-\frac{c}{D}-\rho_{s}^{*}+\frac{\lambda}{D}\int_{0}^{\infty}dF(y)\int_{0}^{y}e^{(1-\rho_{s}^{*})v}e^{-y}dv$$

$$=-\frac{c}{D}-\rho_{s}^{*}+\frac{\lambda}{D(1-\rho_{s}^{*})}\int_{0}^{\infty}\bigl(e^{\rho_{s}^{*}y}-1+1-e^{-y}\bigr)dF(y)$$

$$=-\frac{c}{D}-\rho_{s}^{*}+\frac{1}{D(1-\rho_{s}^{*})}\bigl[-D(\rho_{s}^{*})^{2}-c\rho_{s}^{*}+s-(\psi(1)-D-c)\bigr]$$

$$=\frac{s-\psi(1)}{D(1-\rho_{s}^{*})}+1.\tag{41.37}$$