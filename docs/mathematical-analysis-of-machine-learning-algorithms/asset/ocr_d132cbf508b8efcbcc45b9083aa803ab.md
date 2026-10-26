criterion by Schwarz (1978) (also referred to as BIC). Both considered the parametric density estimation problem (negative-log likelihood loss) with φ(w, z) = − ln p(y|w, x) in the asymptotic statistical setting, where n → ∞. If the models are well specified, one can employ well-known classical asymptotic statistical techniques to derive these methods.

For AIC, one considers the ERM method (maximum-likelihood method) f̂θ. If the model class F(θ) is parametric, then one can show the following expected generalization bound

φ(f̂, D) = [ φ(f̂θ, S_n) + d(θ)/n + o_p( 1/n ) ] .

The leading excess risk term d(θ)/n on the right-hand side is AIC.

For BIC, one considers Bayesian model selection, and it can be shown using Laplace approximation that

−Γ(θ|S_n) = φ(f̂θ, S_n) + d(θ) ln n / (2n) + O_p( 1/n ) ,

where f̂θ is the maximum likelihood estimate over F(θ). The leading excess term d(θ) ln n / (2n) on the right-hand side is BIC.

While simple, both AIC and BIC can only be applied in the asymptotic setting, and only for parametric models because both criteria depend linearly on the model parameter dimension d(θ). For nonparametric density estimation, one can employ a different criterion from information theory which may be regarded as a generalization of BIC, referred to as minimum description length (MDL) (see Rissanen, 1978; Barron et al., 1998; Grünwald, 2007). The MDL method, while not as easy to apply as BIC, is more consistent with the learning theory analysis which we investigated in this chapter. In fact, with our choice of q(θ) so that Σθ q(θ) ≤ 1, the penalty − ln q(θ) (which appears as model selection penalty) can be regarded as a coding length. Therefore the method considered in this chapter may be regarded as a generalized version of MDL.

Model selection has also been considered by Vapnik in his statistical learning approach, and was referred to as structural risk minimization (see Vapnik, 1999, 2013). The technique employs sample-dependent generalization bounds similar to those we considered in Section 8.3, with nested function classes.

Both Bayesian model selection and Bayesian model averaging have been used in practice (Raftery, 1995; Raftery et al., 1997; Wasserman, 2000; Robert, 2007).

The asymptotic analysis of Bayesian model selection for parametric models leads to BIC. For nonparametric models, as we have shown, the theoretical analysis of Bayesian model selection can be done either via the Gibbs algorithm or via MDL, and Bayesian model averaging can be analyzed using aggregation techniques studied in Chapter 15.

The concept of model selection is related to adaptive estimation in statistics (see Bickel, 1982; Birgé and Massart, 1997), which aims at optimal estimation across a family of models. This requires oracle inequalities similar to those of Sec-