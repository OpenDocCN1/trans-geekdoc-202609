Proof of Corollary 9.11.6. Note that Lemma 9.11.1 demonstrates that for all $t \in [0, \infty)$ it holds that

$$\mathcal { L } ( \Theta _ { t } ) = \mathcal { L } ( \Theta _ { 0 } ) - \int _ { 0 } ^ { t } \| \nabla \mathcal { L } \| ( \Theta _ { s } ) \| _ { 2 } ^ { 2 } \mathrm { d } s .$$

Corollary 9.11.5 therefore establishes that there exist $\vartheta \in \mathbb { R } ^ { \mathrm { g } } , \, \mathcal { C } , \beta \in ( 0 , \infty )$ which satisfy for all $t \in [ 0 , \infty )$ that

$$\| \Theta _ { t } - \vartheta \| _ { 2 } \leq \mathcal { C } ( 1 + t ) ^ { - \beta } \quad \text { a n d } \quad 0 \leq \mathcal { L } ( \Theta _ { t } ) - \mathcal { L } ( \vartheta ) \leq \mathcal { C } ( 1 + t ) ^ { - 1 } .$$

This ensures that

$$\lim _ { t \rightarrow \infty } \operatorname { s u p } \| \Theta _ { t } - \vartheta \| _ { 2 } = 0 .$$

Combining this with the assumption that $\mathcal { L } \in C ^ { 1 } ( \mathbb { R } ^ { \mathrm { g } } , \mathbb { R } )$ establishes that

$$\lim _ { t \rightarrow \infty } \operatorname { s u p } \| ( \nabla \mathcal { L } ) ( \Theta _ { t } ) - ( \nabla \mathcal { L } ) ( \vartheta ) \| _ { 2 } = 0 .$$

Hence, we obtain that

$$\lim _ { t \rightarrow \infty } \operatorname { s u p } \| \| ( \nabla \mathcal { L } ) ( \Theta _ { t } ) \| _ { 2 } - \| ( \nabla \mathcal { L } ) ( \vartheta ) \| _ { 2 } \| = 0 .$$

Furthermore, observe that (9.193) and (9.194) ensure that

$$\int _ { 0 } ^ { \infty } \| ( \nabla \mathcal { L } ) ( \Theta _ { s } ) \| _ { 2 } ^ { 2 } \mathrm { d } s < \infty .$$

This and (9.197) demonstrate that

$$( \nabla \mathcal { L } ) ( \vartheta ) = 0 .$$

Combining this with (9.194) establishes (9.192). The proof of Corollary 9.11.6 is thus complete.

Corollary 9.11.7. Let $\mathrm { g } \in \mathbb { N } , \, \Theta \in C ( [ 0 , \infty ) , \mathbb { R } ^ { \mathrm { g } } ) , $ let $\mathcal { L } : \mathbb { R } ^ { \mathrm { g } } \rightarrow \mathbb { R }$ be analytic, assume for all $t \in [ 0 , \infty )$ that

$$\Theta _ { t } = \Theta _ { 0 } - \int _ { 0 } ^ { t } ( \nabla \mathcal { L } ) ( \Theta _ { s } ) \, \mathrm { d } s ,$$

and assume $\liminf _ { t \rightarrow \infty } \| \Theta _ { t } \| _ { 2 } < \infty$ (cf. Definitions 3.3.4 and 9.7.1). Then there exist $\vartheta \in \mathbb { R } ^ { \mathrm { g } } , \, \, \mathcal { C } , \, \beta \in ( 0 , \infty )$ which satisfy for all $t \in [ 0 , \infty )$ that

$$\| \Theta _ { t } - \vartheta \| _ { 2 } \leq \mathcal { C } ( 1 + t ) ^ { - \beta } , \quad 0 \leq \mathcal { L } ( \Theta _ { t } ) - \mathcal { L } ( \vartheta ) \leq \mathcal { C } ( 1 + t ) ^ { - 1 } , \quad \text { a n d } \quad ( \nabla \mathcal { L } ) ( \vartheta ) = 0 .$$