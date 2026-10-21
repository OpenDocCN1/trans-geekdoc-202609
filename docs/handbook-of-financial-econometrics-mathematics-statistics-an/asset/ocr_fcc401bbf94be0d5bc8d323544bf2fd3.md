As $k \to np$, we get $\frac{k}{n} \to p$. Then equation (102A.4) can be approximated as

$$\sqrt{\frac{n^{-1}}{2\pi\frac{k}{n}\left(1-\frac{k}{n}\right)}}\left(1+x\sqrt{\frac{q}{np}}\right)^{-k}\left(1-x\sqrt{\frac{p}{nq}}\right)^{-(n-k)}$$ 
$$\simeq \sqrt{\frac{n^{-1}}{2\pi p q}}\left(1+x\sqrt{\frac{q}{np}}\right)^{-k}\left(1-x\sqrt{\frac{p}{nq}}\right)^{-(n-k)}$$ 
$$= \sqrt{\frac{1}{2\pi n p q}}\exp\left\{\ln\left[\left(1+x\sqrt{\frac{q}{np}}\right)^{-k}\right]+\ln\left[\left(1-x\sqrt{\frac{p}{nq}}\right)^{-(n-k)}\right]\right\}$$ 
$$= \sqrt{\frac{1}{2\pi n p q}}\exp\left\{-k\ln\left(1+x\sqrt{\frac{q}{np}}\right)-(n-k)\ln\left(1-x\sqrt{\frac{p}{nq}}\right)\right\}$$ 
$$= \sqrt{\frac{1}{2\pi n p q}}\exp\left\{-(np+x\sqrt{npq})\ln\left(1+x\sqrt{\frac{q}{np}}\right)\right.$$ 
$$-\left(nq-x\sqrt{npq}\right)\ln\left(1-x\sqrt{\frac{p}{nq}}\right)\right\}. \qquad (102A.5)$$

We are considering the term in exponential function, i.e.,

$$-(np+x\sqrt{npq})\ln\left(1+x\sqrt{\frac{q}{np}}\right)-(nq-x\sqrt{npq})\ln\left(1-x\sqrt{\frac{p}{nq}}\right). \qquad (102A.6)$$

Here, we are using the Taylor series expansions of functions $\ln(1\pm x)$:

$$\ln(1+x)=x-\frac{x^{2}}{2}+\frac{x^{3}}{3}+o(x^{3}),$$ 
$$\ln(1-x)=-x-\frac{x^{2}}{2}-\frac{x^{3}}{3}+o(x^{3}).$$

Then we expand equation (102A.6) with respect to $x$ and obtain

$$-(np+x\sqrt{npq})\left(x\sqrt{\frac{q}{np}}-\frac{x^{2}q}{2np}+\frac{x^{3}q^{\frac{3}{2}}}{3n^{\frac{3}{2}}p^{\frac{3}{2}}}+o(x^{3})\right)$$ 
$$-(nq-x\sqrt{npq})\left(-x\sqrt{\frac{p}{nq}}-\frac{x^{2}p}{2nq}-\frac{x^{3}p^{\frac{3}{2}}}{3n^{\frac{3}{2}}q^{\frac{3}{2}}}+o(x^{3})\right)$$