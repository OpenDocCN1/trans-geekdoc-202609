# Appendix 109A  Proof of Feller’s Lemma

We need some preliminary results in order to prove equation (109.6).

**Proposition 109A.1.** $f(z)=e^{Av/z}z^{-1}$ is the Laplace transformation of $I_0(2(Avx)^{1/2})$, where $I_k(x)$ is the Bessel function

$$I_k(x)=\sum_{r=0}^{\infty}\frac{(x/2)^{2r+k}}{r!\,\Gamma(r+1+k)}.$$

**Proof.** By the definition of Laplace transformation and the monotone convergence theorem, we have

$$\begin{aligned}
f(z)&=\int_0^{\infty}e^{-zx}I_0\bigl(2(Avx)^{1/2}\bigr)\,dx\\
&=\int_0^{\infty}e^{-zx}\sum_{r=0}^{\infty}\frac{(Avx)^r}{r!\,\Gamma(r+1)}\,dx\\
&=\int_0^{\infty}e^{-zx}\left\{1+\frac{Avx}{\Gamma(2)}+\frac{(Avx)^2}{2!\,\Gamma(3)}+\cdots+\frac{(Avx)^n}{n!\,\Gamma(n+1)}+\cdots\right\}\,dx\\
&=\frac{1}{z}+\frac{Av}{z^2}+\frac{(Av)^2}{2!z^3}+\cdots+\frac{(Av)^n}{n!z^{n+1}}+\cdots\\
&=\frac{1}{z}\left\{1+\frac{Av}{z}+\frac{(Av)^2}{2!z^2}+\cdots+\frac{(Av)^n}{n!z^n}\right\}\\
&=e^{Av/z}z^{-1}.
\end{aligned}$$

**Proposition 109A.2.** *Consider the parabolic differential equation*

$$P_t=(axP)_{xx}-((bx+h)P)_x,\qquad 0<x<\infty \tag{109A.1}$$

where $a,b,h$ are constants, $0<h<a$, then the Laplace transformation of $f(t,x,x_0)$ with respect to $x$ takes the form

$$\begin{aligned}
w(t,s;x_0)&=\int_0^{\infty}e^{-sx}f(t,x;x_0)\,dx\\
&=\left(\frac{b}{sa(e^{bt}-1)+b}\right)^{h/a}\exp\left\{\frac{-sbx_0e^{bt}}{sa(e^{bt}-1)+b}\right\}\\
&\quad\times\Gamma\left(1-\frac{h}{a};\frac{b^2x_0e^{bt}}{a(e^{bt}-1)\bigl(sa(e^{bt}-1)+b\bigr)}\right),\tag{109.50}
\end{aligned}$$

where $\Gamma(n;z)=\Gamma^{-1}(n)\int_0^z e^{-x}x^{n-1}\,dx$.