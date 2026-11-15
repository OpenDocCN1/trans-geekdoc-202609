the objective function to enforce small perturbation:

\(\underset{\mathbf{x}}{\arg\min} -g(\mathbf{x}) + \lambda \cdot \|\mathbf{x} - \mathbf{x}_0\|_p,\) (2.9)

where \(\lambda > 0\) is a constant to control the balance between the two terms. A larger \(\lambda\) will lead to a smaller perturbation in \(\ell_p\) norm but lower attack successfulness, whereas a smaller \(\lambda\) will find larger perturbations with higher attack success rate.

Note that we can find adversarial examples within a certain \(\epsilon\) perturbation constraint by solving a series of unconstrained problems (2.9). Let \(\mathbf{x}^*(\lambda)\) be the solution of (2.9) with a constant \(\lambda\); then the perturbation \(\|\mathbf{x}^*(\lambda) - \mathbf{x}_0\|_p\) will be a decreasing function of \(\lambda\). Therefore we can find the ideal \(\lambda\) that produces \(\|\mathbf{x}^*(\lambda) - \mathbf{x}_0\|_p = \epsilon\) by binary search. This approach has been used in the Carlini and Wagner (C&W) attack (Carlini and Wagner, 2017b), which solves the unconstrained form with a different loss function defined below.

# ## 2.5 Another way to define attack objective

Defining the attack successfulness \(g(\mathbf{x})\) by cross-entropy loss is intuitive, but it has been found that sometimes the nonconvexity introduced by cross- entropy loss makes PGD attack converge slowly and sometimes result in a bad local minimum. Therefore several alternative definitions of \(g(\mathbf{x})\) have been studied in the literature. Among them, Carlini and Wagner (2017b) showed that defining \(g(\mathbf{x})\) with a so-called “hinge loss” is most effective. Attacks using this approach are called C&W attack. For untargeted attack, the C&W loss can be written as

\(\text{Untargeted C\&W loss:} g(\mathbf{x}) = -\max\{f_{y_0}(\mathbf{x}) - \max_{j \neq y_0} f_j(\mathbf{x}), -\kappa\},\) (2.10)

where \(y_0\) is the ground truth class, and \(\kappa \ge 0\) is a constant. For \(\kappa = 0\), this function will be negative if the model predicts the original class (\(f_{y_0}(\mathbf{x}) \ge \max_{j \neq y_0} f_j(\mathbf{x})\)) and zero when the model gives any top-1 prediction other than \(y_0\) (i.e., the “wrong” prediction). Therefore maximizing this function will obtain a successful attack. Setting \(\kappa\) to be some positive value can enforce a margin between \(f_{y_0}(\mathbf{x})\) and \(\max_{j \neq y_0} f_j(\mathbf{x})\), but this is usually only used in special circumstances when we want to have stronger adversarial examples that are further away from the decision boundary. With a similar