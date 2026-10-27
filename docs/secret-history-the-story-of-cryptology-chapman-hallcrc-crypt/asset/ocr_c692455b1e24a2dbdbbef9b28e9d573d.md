![](bbox=[0.23, 0.11, 0.73, 0.44])

Figure 20.5 Elliptic curve point addition.

If we wish to add a point to itself, we draw a tangent line to the curve at the given point, and then continue as above.

There’s still one more case that needs to be considered. Adding two points that lie on a vertical line (or adding a point at which the curve has a vertical tangent line to itself) provides no other point of intersection with our curve. To “patch” this problem, we introduce an extra point, ∞. This is a common trick in algebraic geometry. Reflecting ∞ about the x-axis still gives ∞; that is, we do not want a second −∞. With these definitions, the points on an elliptic curve (together with ∞) form a commutative group. The identity element is ∞, because P + ∞ = P for any point P.

The addition can be carried out algebraically, as follows. P₁ = (x₁, y₁) and P₂ = (x₂, y₂) implies P₁ + P₂ = (m² − x₁ − x₂, m(2x₁ − (m² − x₂)) − y₁), where

m = (y₂ − y₁)/(x₂ − x₁), if P₁ ≠ P₂

and

m = (3x₁² + a)/2y₁, if P₁ = P₂

The proof is left as an exercise.

The graphs given above show elliptic curves where the solutions are real numbers, but we may instead examine the same equations modulo n. For example, consider

y² = x³ + 3x + 4 (mod 7)