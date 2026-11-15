(c) Money is not the only way to measure the energy cost of a huge computation. Search online to find out how much carbon dioxide (CO2) is placed into the atmosphere per unit of electrical energy produced, under a typical distribution of power production methods. Estimate how many tons of CO2 are produced as a side-effect of computing 2^40, 2^50, ..., 2^120 SHA-256 hashes.

★ (d) Estimate the corresponding CO2 concentration (parts per million) in the atmosphere as a result of computing 2^40, 2^50, ..., 2^120 SHA-256 hashes. If it is possible without a PhD in climate science, try to estimate the increase in average global temperature caused by these computations.

# 4.2. Which of the following are negligible functions in λ? Justify your answers.

\frac{1}{2^{\lambda/2}} \quad \frac{1}{2^{\log(\lambda^2)}} \quad \frac{1}{\lambda^{\log(\lambda)}} \quad \frac{1}{\lambda^2} \quad \frac{1}{2^{(\log \lambda)^2}} \quad \frac{1}{(\log \lambda)^2} \quad \frac{1}{\lambda^{1/\lambda}} \quad \frac{1}{\sqrt{\lambda}} \quad \frac{1}{2\sqrt{\lambda}}

# 4.3. Suppose f and g are negligible.

+   (a) Show that f + g is negligible.

+   (b) Show that f · g is negligible.

+   (c) Give an example f and g which are both negligible, but where f(λ)/g(λ) is not negligible.

# 4.4. Show that when f is negligible, then for every polynomial p, the function p(λ)f(λ) not only approaches 0, but it is also negligible itself.

Hint: Use the contrapositive. Suppose that p(λ)f(λ) is non-negligible, where p is a polynomial. Conclude that f must be non-negligible.

# 4.5. Prove that the ≈ relation is transitive. Let f, g, h: N → R be functions. Using the definition of the ≈ relation, prove that if f ≈ g and g ≈ h then f ≈ h. You may find it useful to invoke the triangle inequality: |a - c| ⩽ |a - b| + |b - c|.

# 4.6. Prove Lemma 4.6.

# 4.7. Prove Lemma 4.7.

# ★ 4.8. A *deterministic* program is one that uses no random choices. Suppose L1 and L2 are two *deterministic* libraries with a common interface. Show that either L1 ≡ L2, or else L1 & L2 can be distinguished with advantage 1.

# 4.9. Algorithm B in Section 4.4 has worst-case running time O(q^2). Can you suggest a way to make it run in O(q log q) time? What about O(q) time?

# 4.10. Assume that the last 4 digits of student ID numbers are assigned uniformly at this university. In a class of 46 students, what is the **exact** probability that two students have ID numbers with the same last 4 digits?

Compare this exact answer to the upper and lower bounds given by Lemma 4.10.