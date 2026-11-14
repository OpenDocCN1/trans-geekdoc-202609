[26, 34, 35]. Therefore, in the presented model \( F_2\left(\nabla \mu, \nabla v\right) \) is replaced by a fractional-order-derivative-based term \( F_2\left(D_+^\alpha \mu, D_+^\alpha v\right) \).

# 10.3.1.1 Nonlinear Fractional Order Variational Model

This chapter proposes the following nonlinear fractional order variational model by embedding the Charbonnier norm [36] and Marchaud fractional [37] derivative to make the estimated optical flow accurate and robust.

```
\( E(\boldsymbol{w}) = \int_\Omega \left[ \psi\left(\nabla \mathcal{J}^T \boldsymbol{w} + \mathcal{J}_T\right) + F_1\left(\mu, v\right) + F_2\left(D_+^\alpha \mu, D_+^\alpha v\right) \right] d\boldsymbol{X} \quad (10.5) \)
```

where \( \psi\left(z\right) = \sigma \sqrt{1 + \left(\frac{z}{\sigma}\right)^2} \) describes Charbonnier norm in \( z \), and \( \sigma \) denotes a small positive parameter selected as per Bruhn et al. [36]. The functions \( F_1 \) and \( F_2 \) are given by \( F_1\left(\mu, v\right) = \beta^2 \boldsymbol{w}^T \boldsymbol{w} \) and \( F_2\left(D_+^\alpha \mu, D_+^\alpha v\right) = \lambda e^T \left(D_+^\alpha \boldsymbol{w}^T \odot D_+^\alpha \boldsymbol{w}^T\right)e \), where \( \beta, \lambda \in \mathbb{R}^+ \) and \( D_+^\alpha \mathcal{Z} = \left(D_\mathcal{X}^\alpha \mathcal{Z}, D_\mathcal{Y}^\alpha \mathcal{Z}\right)^T \). Here, \( D_\mathcal{X}^\alpha \mathcal{Z} \) and \( D_\mathcal{Y}^\alpha \mathcal{Z} \) denote the Marchaud differentiation of \( \mathcal{Z} \) related with \( \mathcal{X} \) and \( \mathcal{Y} \), respectively, for \( \alpha \in (0, 1) \). The symbol \( \odot \) denotes the Hadamard product, and \( e \in \mathbb{R}^{2 \times 1} \) is the column vector with all entries as 1. It is observed that as \( \sigma \to 0 \), model (5) tends to demonstrate an \( L_1 \)-norm based model, and wherever \( \alpha \in \mathbb{Z}^+ \), the presented model describes an integer-order-based model. In addition, the use of Charbonnier norm and Marchaud derivative in the presented work is motivated by the following:

+   • Charbonnier norm is a well-known robust statistic that is less sensitive to outliers than quadratic approaches [36].
+   
+   • Since the Charbonnier norm is non-quadratic in nature, nonlinear models are capable of producing satisfactory results in the presence of flow discontinuities [36].
+   
+   • Its convex nature ensures a unique solution for the minimization problem. This makes it superior to the non-convex Lorentzian norm [38].
+   
+   • The Charbonnier norm can be scaled to the \( L_1 \)-norm through the use of \( \sigma \) [36].
+   
+   • The Marchaud derivative is useful as it can be used also with those functions that are not continuous (such as images).