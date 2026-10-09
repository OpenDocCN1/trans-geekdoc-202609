Suppose that $\alpha \in \Delta$, and there exists $w \in W, \alpha_i \in \Pi_i$, such that $w(\alpha) = \alpha_i$; hence,

$\varphi(\alpha) = \varphi(w^{-1}(\alpha_i)) = \varphi w^{-1} \varphi^{-1}(\varphi(\alpha_i)) = (w^\prime)^{-1}\alpha_i^\prime \in \Delta^\prime$ ,

and $\varphi(\Delta) \subseteq \Delta^\prime$. Similarly, $\varphi^{-1}(\Delta^\prime) \subseteq \Delta$, so $\varphi(\Delta) \subseteq \Delta^\prime$.

By Theorem 1.6, we know that $\Phi$ can be developed for $\mathfrak{g}$ to $\mathfrak{g}^\prime$ of Lie algebra isomorphism, i.e., isomorphism of $\mathfrak{g}$ and $\mathfrak{g}^\prime$.

By contrast, let $\Phi$ be an isomorphism of complex semisimple Lie algebras from $\mathfrak{g}$ to $\mathfrak{g}^\prime$; then,

$ (\Phi(x), \Phi(y))^\prime = (x, y), \forall(x, y) \in \mathfrak{g} . \tag{1.22} $

Let $\eta$ be a Cantan sub-algebra of $\mathfrak{g}$, where $\Delta$, $\Pi$ are the root system and simple root system, respectively; then, $\mathfrak{g} = \eta + \Sigma_{\alpha \in \Delta} \mathfrak{g}_\alpha$. Here, $\eta^\prime = \Phi(\eta)$ is a Cantan sub-algebra of $\mathfrak{g}^\prime$, and $\mathfrak{g}^\prime = \varphi^\prime + \Sigma_{\alpha^\prime \in \Delta^\prime} \mathfrak{g}_\alpha^{\prime}$.

For $h \in \eta$, $e_\alpha \in \mathfrak{g}_\alpha$, we have

$\varphi([h, e_\alpha]) = (\alpha, h)\varphi(e_\alpha)$ ,
$[\varphi(h)\varphi(e_\alpha)] = \varphi([h, e_\alpha])$ ,

Hence, $\Phi(\mathfrak{g}_\alpha) = \mathfrak{g}\Phi(\alpha)$, $\varphi(\Delta) = \Delta^\prime$. Further, $\varphi(\Pi) = \Pi^\prime$ is a simple root system of $\Phi(\eta_R)$ of a certain order, and from (1.21), we know that the Dynkin diagrams of $\Pi$ and $\Pi^\prime$ are the same.

According to the above theorem, we can get the study space isomorphism discriminant algorithm in Lie group machine learning:

```
**Algorithm 1.16**: Study space isomorphism discriminant algorithm in Lie group machine learning

**Initialisation**: $D_1$, $D_2$ are two Dynkin diagrams corresponding to data sets in the study space //
**Input**: $D_1$, $D_2$ //
**Output**: {0, 1} //

procedure ISOMORPHIC($D_1$, $D_2$)
  if EQUAL($D_1$, $D_2$)
    then return 1; // Dynkin diagrams are the same, then the two study spaces have isomorphism//
  else return 0;
  end if
end ISOMORPHIC
```

Through the definition and property of the Dynkin diagram, we can see that in the sense of isomorphism, the input data vector space has its corresponding Dynkin diagram, and only $A_1$, $B_1$, $C_1$, $D_1$, $E_6$, $E_7$, $E_8$, $F_4$, and $G_2$ (a total of 9 types) are possible [1, 6];