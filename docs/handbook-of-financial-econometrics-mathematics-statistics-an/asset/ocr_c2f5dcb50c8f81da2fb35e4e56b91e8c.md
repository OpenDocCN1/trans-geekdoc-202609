Using (41.37), (41.38), and $G_s(0)=H_s(0)=1$ in (41.40) and (41.41), we get higher-order derivatives of $G_s$ and $H_s$ at zero. Then, by Theorem 41.3.7, we compute the constant vector $Q$ and, hence, obtain solutions for $G_s(x)$ and $H_s(x)$.

To illustrate our method, we consider the particular case $\mathrm{dF}(x)=\eta e^{-\eta x}1_{x>0}\mathrm{d}x$. Then $\psi(\xi)=D\xi^2+c\xi+\lambda\frac{\eta}{\eta+\xi}-\lambda$ and, for every $s>0$, there exist $\rho_1<\eta<\rho_2<0<\rho^*$ such that $\psi(\rho_1)=\psi(\rho_2)=\psi(\rho^*)=s$ (i.e., $Z^s_-=\{\rho_1,\rho_2\}$), and we write $\rho^*$ for $\rho_s^*$. Recall that $G'_s(0)=\frac{s}{D\rho^*}$. Hence $G_s(x)=Q_1e^{\rho_1x}+Q_2e^{\rho_2x}$, where $Q$ is the unique column vector satisfying the equation

$$\begin{bmatrix}1&1\\\rho_1&\rho_2\end{bmatrix}\begin{bmatrix}Q_1\\Q_2\end{bmatrix}=\begin{bmatrix}1\\\frac{-s}{D\rho^*}\end{bmatrix}.$$

Simple algebra shows that
$$\begin{bmatrix}Q_1\\Q_2\end{bmatrix}=\frac{1}{\rho_1-\rho_2}\begin{bmatrix}\rho_2+\frac{s}{D\rho^*}\\\ -\rho_1-\frac{s}{D\rho^*}\end{bmatrix}.$$

Since $\rho_1\rho_2\rho^*=\frac{s\eta}{D}$, we get
$$G_s(x)=\frac{\rho_2+\frac{s}{D\rho^*}}{\rho_2-\rho_1}e^{\rho_1x}+\frac{-\rho_1-\frac{s}{D\rho^*}}{\rho_2-\rho_1}e^{\rho_2x}$$
$$=\frac{\rho_s(\eta+\rho_1)}{\eta(\rho_2-\rho_2)}e^{\rho_1x}+\frac{-\rho_1(\eta+\rho_2)}{\eta(\rho_2-\rho_1)}e^{\rho_1x}.\qquad(41.42)$$

Recall that $H'(0)=\frac{s-\psi(1)}{D(1-\rho^*)}+1$. Hence $H_s(x)=P_1e^{\rho_1x}+P_2e^{\rho_2x}$, where $P$ is the unique column vector satisfying the equation
$$\begin{bmatrix}1&1\\\rho_1&\rho_2\end{bmatrix}\begin{bmatrix}P_1\\P_2\end{bmatrix}=\begin{bmatrix}1\\\frac{s-\psi(1)}{D(1-\rho^*)}+1\end{bmatrix}.$$
Simple algebra shows that
$$\begin{bmatrix}P_1\\P_2\end{bmatrix}=\frac{1}{\rho_1-\rho_2}\begin{bmatrix}\rho_2-1-\frac{s-\psi(1)}{D(1-\rho^*)}\\\1-\rho_1+\frac{s-\psi(1)}{D(1-\rho^*)}\end{bmatrix}.$$

Using the fact that $(1+\eta)(\psi(1)-s)=D(1-\rho_1)(1-\rho_2)(1-\rho^*)$. We obtain
$$H_s(x)=\frac{\rho_2-1-\frac{s-\psi(1)}{D(1-\rho^*)}}{\rho_2-\rho_1}e^{\rho_1x}+\frac{1-\rho_1+\frac{s-\psi(1)}{D(1-\rho^*)}}{\rho_2-\rho_1}$$
$$=\frac{(\rho_2-1)(\eta+\rho_1)}{(1+\eta)(\rho_2-\rho_2)}e^{\rho_1x}+\frac{(1-\rho_1)(\eta+\rho_2)}{(1+\eta)(\rho_2-\rho_1)}e^{\rho_2x}.\qquad(41.43)$$