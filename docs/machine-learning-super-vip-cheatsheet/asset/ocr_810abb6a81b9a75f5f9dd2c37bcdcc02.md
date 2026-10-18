![](bbox=[0.054, 0.088, 0.485, 0.294])

\(k=1\qquad\qquad\qquad k=3\qquad\qquad\qquad k=11\)

\[\exists h\in\mathcal{H},\quad \forall i\in[1,d],\quad h(x^{(i)})=y^{(i)}\]

**Upper bound theorem** — Let \(\mathcal{H}\) be a finite hypothesis class such that \(|\mathcal{H}|=k\) and let \(\delta\) and the sample size \(m\) be fixed. Then, with probability of at least \(1-\delta\), we have:

\[\epsilon(\hat h)\leq \left(\min_{h\in\mathcal{H}}\epsilon(h)\right)+2\sqrt{\frac{1}{2m}\log\left(\frac{2k}{\delta}\right)}\]

# 1.8 Learning Theory

**Union bound** — Let \(A_1,\ldots,A_k\) be \(k\) events. We have:

\[P(A_1\cup\cdots\cup A_k)\leq P(A_1)+\cdots+P(A_k)\]

![](bbox=[0.067, 0.419, 0.446, 0.498])

\(A_1\cup A_2\cup A_3\qquad\qquad A_1\qquad\qquad A_2\qquad\qquad A_3\)

**Hoeffding inequality** — Let \(Z_1,\ldots,Z_m\) be \(m\) iid variables drawn from a Bernoulli distribution of parameter \(\phi\). Let \(\hat\phi\) be their sample mean and \(\gamma>0\) fixed. We have:

\[P(|\phi-\hat\phi|>\gamma)\leq 2\exp(-2\gamma^2m)\]

*Remark:* this inequality is also known as the Chernoff bound.

**Training error** — For a given classifier \(h\), we define the training error \(\hat\epsilon(h)\), also known as the empirical risk or empirical error, to be as follows:

\[\hat\epsilon(h)=\frac{1}{m}\sum_{i=1}^{m}\mathbf{1}_{\{h(x^{(i)})\neq y^{(i)}\}}\]

**Probably Approximately Correct (PAC)** — PAC is a framework under which numerous results on learning theory were proved, and has the following set of assumptions:

+   - the training and testing sets follow the same distribution
+   - the training examples are drawn independently

**Shattering** — Given a set \(S=\{x^{(1)},\ldots,x^{(d)}\}\), and a set of classifiers \(\mathcal{H}\), we say that \(\mathcal{H}\) shatters \(S\) if for any set of labels \(\{y^{(1)},\ldots,y^{(d)}\}\), we have:

**VC dimension** — The Vapnik-Chervonenkis (VC) dimension of a given infinite hypothesis class \(\mathcal{H}\), noted \(VC(\mathcal{H})\), is the size of the largest set that is shattered by \(\mathcal{H}\).

*Remark:* the VC dimension of \(\mathcal{H}=\{\text{set of linear classifiers in 2 dimensions}\}\) is 3.

![](bbox=[0.522, 0.333, 0.939, 0.377])

**Theorem (Vapnik)** — Let \(\mathcal{H}\) be given, with \(VC(\mathcal{H})=d\) and \(m\) the number of training examples. With probability at least \(1-\delta\), we have:

\[\epsilon(\hat h)\leq\left(\min_{h\in\mathcal{H}}\epsilon(h)\right)+O\left(\sqrt{\frac{d}{m}\log\left(\frac{m}{d}\right)+\frac{1}{m}\log\left(\frac{1}{\delta}\right)}\right)\]