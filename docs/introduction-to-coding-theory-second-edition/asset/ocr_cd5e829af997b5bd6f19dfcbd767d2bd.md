this field: let $q(x)=f(x)/g(x)\in\mathcal{O}_p$. If it is in $\mathcal{P}_p$, it is mapped to 0. If it is not in $\mathcal{P}_p$, then by definition $g(x)$ is coprime with $p(X)$. An important theoretical consequence of the Euclidean algorithm (we recalled and used it in Section 13.3) implies that there are polynomials $a(x),b(x)$ such that

$$1 = a(x)g(x) + b(x)p(x).$$

It follows that $q(x)=q(x)\cdot1 = f(x)a(x)+q(x)b(x)p(x)$. The second summand maps to 0 and the image of $q(x)$ coincides with the image of the polynomial $f(x)a(x)$.

The $v_p$ are examples of **discrete valuations**, the $\mathcal{O}_p$ are called **valuation rings**, the $\mathcal{P}_p$ are **places** and $F_p = \mathcal{O}_p/\mathcal{P}_p$ is known as the **residue class field**. The degree $f = [F_p : K]$ is the degree $deg(P)$ of the place $P$, and in this case we know that the degree of the place defined by the polynomial $p(X)$ coincides with the degree of the polynomial $p(X)$. Aside from the valuations corresponding to irreducible polynomials, there is another valuation $v_\infty$ **at infinity**.

**19.13 Definition.** $v_\infty(f(x)/g(x)) = deg(g(x)) - deg(f(x))$ if $f(x) \neq 0$ and as usual $v_\infty(0) = \infty$.

The places corresponding to $v_p$ and $v_\infty$ are all the places of the rational function field; see [198], Theorem 1.2.2. Clearly $q(x)=f(x)/g(x)\in\mathcal{O}_\infty\setminus\mathcal{P}_\infty$ if $f(x),g(x)$ have the same degree: $f(x)=a_nx^n+\dots,g(X)=b_nx^n+\dots$ The residue class field $\mathcal{O}_\infty/\mathcal{P}_\infty=K$ and the image of the $q(x)$ above is $a_n/b_n$.

Another important observation is that, for each $q(x)$, the sum $\sum_P v_P(q(X))deg(P)$ extended over the $v_p$ and also $v_\infty$ equals 0. In fact, the sum over all $v_p$ equals of course $deg(f(X))-deg(g(X))$, and the valuation at infinity balances this out.

In the next section we start a study of general function fields and their valuations. By definition they can be written as finite-dimensional extensions of rational function fields. The fact that we know precisely what happens in the case of the rational function field will be very helpful for the general theory.

# Exercises 19.2

+   19.2.1. List the 24 solutions of the Klein quartic over $\mathbb{F}_8$.
+   19.2.2. Prove Theorem 19.4, Hilbert's theorem 90 for finite fields.