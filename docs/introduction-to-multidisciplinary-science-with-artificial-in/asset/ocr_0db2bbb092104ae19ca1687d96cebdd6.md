![](bbox=[0.13, 0.08, 0.88, 0.3])

Figure 1.5. We consider the gravitational field outside a hollow spherical shell of radius R, with a surface density sigma, and a point P at a distance r from the center of the sphere. We can compute the gravitational force using the elemental zone of thickness dη.

# Example #3:

Consider a hollow spherical shell of radius R with surface density σ and a point P at a distance r from the center of the sphere, as illustrated in Figure 1.5. The mass of the spherical shell is m₁ = σ 4π R²; remember that the area of a sphere is A = 4π R². We divided the spherical shell into narrow zones of thickness dη. The mass of this element is δm = σ 2π R dη, where 2π R dη is the area of the rectangle describing the elementary zone. The field due to this zone, in the direction PO is

dg = G δm / s² cos θ . (1.12)

Let us express dg in terms of a single variable, s. By using the law of cosines of a triangle, which describes OQP in Figure 1.5, we have

R² = r² + s² - 2 r s cos θ = r² + s² - 2 r η (1.13)

and

cos θ = (r² - R² + s²) / (2 r s) . (1.14)

We can differentiate (1.13) with respect to η to obtain

ds / dη = r / s . (1.15)

By substituting (1.13), (1.14), and (1.15) into (1.12), the field at P due to the elementary zone, in Figure 1.5 is

dg = G δm / s² cos θ = G σ 2π R dη / s² cos θ = π R G σ / r² ( 1 + (r² - R²) / s² ) ds .