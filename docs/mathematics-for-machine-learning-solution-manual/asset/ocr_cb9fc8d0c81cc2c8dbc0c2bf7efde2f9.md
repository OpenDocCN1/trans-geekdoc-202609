# Linear Algebra

# Exercises

2.1 We consider (ℝ\{-1}, ★), where

a ★ b := ab + a + b,      a,b ∈ ℝ\{-1}      (2.1)

+   - a. Show that (ℝ\{-1}, ★) is an Abelian group.
+   - b. Solve
+   
+     3 ★ x ★ x = 15
+   
+     in the Abelian group (ℝ\{-1}, ★), where ★ is defined in (2.1).

a. First, we show that ℝ\{-1} is closed under ★: For all a, b ∈ ℝ\{-1}:

a ★ b = ab + a + b + 1 - 1 = (a + 1)(b + 1) - 1 ≠ -1

⇒ a ★ b ∈ ℝ\{-1}

Next, we show the group axioms

+   - **Associativity:** For all a, b, c ∈ ℝ\{-1}:
+     (a ★ b) ★ c = (ab + a + b) ★ c
+     = (ab + a + b)c + (ab + a + b) + c
+     = abc + ac + bc + ab + a + b + c
+     = a(bc + b + c) + a + (bc + b + c)
+     = a ★ (bc + b + c)
+     = a ★ (b ★ c)
+   - **Commutativity:**
+     ∀a, b ∈ ℝ\{-1} : a ★ b = ab + a + b = ba + b + a = b ★ a
+   - **Neutral Element:** n = 0 is the neutral element since
+     ∀a ∈ ℝ\{-1} : a ★ 0 = a = 0 ★ a
+   - **Inverse Element:** We need to find ā, such that a ★ ā = 0 = ā ★ a.
+     ā ★ a = 0 ⟺ āa + a + ā = 0
+     ⟺ ā(a + 1) = -a
+     a≠-1
+     ⟺ ā = - a/(a + 1) = -1 + 1/(a + 1) ≠ -1 ∈ ℝ\{-1}