# Graphical models vs. Deep nets

# Graphical models

# Utility of the graph

+   - A vehicle for synthesizing a global loss function from local structure
+     - potential function, feature function, etc.
+   - A vehicle for designing sound and efficient inference algorithms
+     - Sum-product, mean-field, etc.
+   - A vehicle to inspire approximation and penalization
+     - Structured MF, Tree-approximation, etc.
+   - A vehicle for monitoring theoretical and empirical behavior and accuracy of inference

# Utility of the loss function

+   - A major measure of quality of the learning algorithm and the model

![](bbox=[0.55, 0.23, 0.68, 0.48])

log P(X) = Σ_i log φ(x_i) + Σ_{i,j} log ψ(x_i, x_j)

![](bbox=[0.46, 0.5, 0.64, 0.66])

m_{i→a}(x_i) = ∏_{c∈N(i)\a} m_{c→i}(x_i)
b_a(X_a) ∝ f_a(X_a) ∏_{i∈N(a)} m_{i→a}(x_i)
m_{a→i}(x_i) = Σ_{X_a\x_i} f_a(X_a) ∏_{j∈N(a)\i} m_{j→a}(x_j)

Q(H) ~ P(H|V)

![](bbox=[0.6, 0.7, 0.9, 0.92])

θ = argmax_θ P_θ(V)