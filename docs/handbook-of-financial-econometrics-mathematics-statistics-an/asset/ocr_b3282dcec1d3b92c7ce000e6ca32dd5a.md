On the other hand, we have $P_0(\xi)=\eta+\xi$ and

$P_1(\xi)=D\xi^2(\xi+\eta)+c\xi(\xi+\eta)+\lambda\eta-(\lambda+r)(\xi+\eta)$
$=D\xi^3+(D\eta+c)\xi^2+(c\eta-\lambda-r)-r\eta.$

Therefore $\phi$ satisfies an ODE with the characteristic polynomial $P_1$.

# Theorem 41.3.5: Let $D_1$ be the differential operator with the characteristic polynomial

$P_1$ given by (41.19). Then $D_1\Phi\equiv0$ on $R_{++}$.

Proof. Let $L_2=L_2(R)$ be the space of square-integrable functions defined on $R$, and set $(f_1,f_2)=\int f_1(x)f_2(x)dx$. For an operator $A$ on $L_2$, write $A^*$ for its adjoint (i.e., $\langle Ak,h\rangle=\langle kA^*h\rangle$ for all $k$, $h$ in $L_2$). By integration by parts, we have $\langle k',h\rangle=-\langle k h'\rangle$ whenever $k$ or $h$ has compact support. Write $Th(x)=\int h(x-y)f(y)dy$. By a change of variables and Fubini's theorem, we have

$\langle Th,k\rangle=\int k(x)\int h(x-y)f(y)dydx=\int h(z)\int k(z-y)f(-y)dydz=\langle h,T^*k\rangle$

where $T^*k(x)\equiv\int k(x-y)f(-y)dy$.

Let $D_0$ be the differential operator with the characteristic polynomial $P_0$ and $\phi\in C_c^\infty(R_{++})$ a test function. Recall that, by Theorem 41.2.4, $(L-r)\phi\equiv0$ on $R_{++}$. Therefore, we have

$0=\langle D_0(L-r)\phi,\phi\rangle=\langle\phi(L^*-r)D_0^*\phi\rangle.\quad(41.24)$

Here $L^*$ is given by

$L^*h(x)=dh''(x)-xh'(x)+\lambda T^*h(x)-\lambda h(x).$

Set $L_D=L-r-\lambda T$. Then $(L^*-r)D_0^*\phi=\lambda T^*D_0^*\phi+L_D^*D_0^*\phi=\lambda T^*D_0^*\phi+(D_0L_D)^*\phi.\quad(41.25)$

Write $D_2$ as the differential operator corresponding to the polynomial $P_2(\xi)=P_0(\xi)\psi(\xi)$. We prove that $T^*D_0^*\phi=D_2\phi$ a.e. by showing that both $T^*D_0^*\phi$ and $D_2^*\phi$ are in $L_2\cap L_1$ and have the same Fourier transforms. (Here $L_1=L_1(R)$ is the space of integrable functions on $R$.)

First, we show that $T^*D_0^*\phi$ and $D_2^*\phi$ are in $L_1\cap L_2$. Since $\phi\in C_c^\infty(R_{++})$, we obtain $D_2^*\phi\in L_1\cap L_2$. Also, $\int|T^*D_0^*\phi(x)|dx\le\iint|D_0^*\phi(x-y)|dx f(-y)dy\le\|D_0^*\phi\|_{L_1}\|f\|_{L_1}<\infty.$