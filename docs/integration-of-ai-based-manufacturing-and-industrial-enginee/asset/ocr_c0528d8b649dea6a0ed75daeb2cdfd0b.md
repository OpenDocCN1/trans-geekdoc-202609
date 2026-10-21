M(Θ₁)Z(Θ₁)¨Θ₁ + M(Θ₁)Ż(Θ₁)˙Θ₁ + V(Θ₁,˙Θ₁)˙Θ₁
+G(Θ₁)+F(˙Θ₁)+D_d = U + τ  (18.10)

After simplification, the equation above becomes:

M₁(Θ₁)¨Θ₁ + V₁(Θ₁,˙Θ₁)˙Θ₁ + G(Θ₁) + F(˙Θ₁) + D_d = U + J_φ^T(Θ₁)η  (18.11)

Here

M(Θ₁)Z(Θ₁) = M₁(Θ₁);  M(Θ₁)Ż(Θ₁) + V(Θ₁,˙Θ₁)Z(Θ₁) = V₁(Θ₁,˙Θ₁)

When we multiply (18.11) by Z^T(Θ₁) both its sides and in view of (18.9), we get:

M̄(Θ₁)¨Θ₁ + V̄(Θ₁,˙Θ₁)˙Θ₁ + F̄(˙Θ₁) + Ḡ(Θ₁) + D̄_d = Z^T(Θ₁)U  (18.12)

Where

M̄(Θ₁) = Z^T(Θ₁)M₁(Θ₁); V̄(Θ₁,˙Θ₁) = Z^T(Θ₁)V(Θ₁,˙Θ₁); Ḡ(Θ₁) = Z^T(Θ₁)G(Θ₁); F̄(Θ₁) = Z^T(Θ₁)F(Θ₁); D̄_d(Θ₁) = Z^T(Θ₁)D_d(Θ₁)

At the same time, we suppose that the constrained manipulator system will be subject to the following attributes and assumptions for further study.

# Assumption 1

The kinematic constraint is supposed to be a rigid, frictionless surface, and it states that the end-effector must follow a predetermined desired position without losing contact with it.

# Assumption 2

It is assumed that any singularities should be kept at a distance from the reconfigurable manipulator so that the Jacobian matrix can continue to exist as a full rank matrix.

# Assumption 3

The desirable terms, such as the desired joint position, wanted velocity, and intended acceleration, are all bounded, ensuring the closed-loop system's asymptotic stability.