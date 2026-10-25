![](bbox=[0.116, 0.092, 0.88, 0.175])

$$F(B, C) = 0.5$$

$$F(A, C) = \min \{F(A, B), F(B, C)\} = \min \{0.6, 0.5\} = 0.5$$

This indicates that A dominates C with a fuzzy membership value of 0.5, satisfying the transitivity property.

+   - **Anti-symmetry:** Domination in fuzzy graphs is anti-symmetric, meaning that if vertex u dominates vertex v, then v cannot dominate u unless u = v, i.e. if F(v, u) > α, then F(v, u) = 1 or F(v, u) < α, where α is the threshold value. This property indicates that domination in fuzzy graphs is directional and asymmetrical.
+   
+   **Example:** Let's consider a fuzzy graph with two vertices A and B, and the following fuzzy membership values (Figure 3.12).
+   
+   Here, A dominates B with a fuzzy membership value of 0.8, but B does not dominate A as F(B, A) = 0.4, which is less than 1. This satisfies the anti-symmetry property, indicating that domination in fuzzy graphs is anti-symmetric.

+   - **Partial domination:** In fuzzy graphs, a vertex may not have full or total control over another vertex. Instead, it may only have a certain amount of control or effect, which is shown by fuzzy membership values that range from 0 to 1.
+   
+   **Example:** Let's consider a fuzzy graph with two vertices A and B, and the following fuzzy membership values (Figure 3.13).

![](bbox=[0.116, 0.705, 0.88, 0.77])

![](bbox=[0.116, 0.815, 0.88, 0.88])