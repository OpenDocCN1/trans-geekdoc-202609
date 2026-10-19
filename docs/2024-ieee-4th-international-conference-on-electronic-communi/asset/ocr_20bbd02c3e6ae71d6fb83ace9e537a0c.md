# 2.2. Hyperbolic Trigonometry

The inverse hyperbolic functions, denoted as arccosh, arcsinh, and arctanh [1,2], are the function that maps real numbers to hyperbolic angles. For this research, we are interested in the properties of the inverse hyperbolic cosine function (arccosh) defined as

arccosh(x) = ln( x + sqrt(x² − 1) ), {x ∈ ℝ : x ≥ 1} (1)

# 2.3. Hyperbolic Geometry and Distances

In hyperbolic geometry, distances, angles, and geometric properties are based on the hyperbolic metric which defines the distance function between any two points in ℍⁿ. The hyperbolic metric satisfies the properties of a metric space, including non-negativity, the identity of indiscernibles, symmetry, and triangle inequality. Nonlinear distance optimization in hyperbolic space is constrained by boundary conditions, such as the unit disk of the Poincaré model, limiting the range of possible distances. The unit disk models of the hyperbolic space (Poincaré and Beltrami-Klein) [3] provide no direct comparison with the Euclidean space limited by the key issue of distance preservation. Additionally, the boundary conditions of the hyperbolic trigonometric functions constrain arccosh(x)’s x ∈ ℝ : x ≥ 1 boundary.

# 2.4. Transcendental Equation and λ Boundary Conditions in Poincaré and Mader Models

# 2.4.1. Poincaré Model

The Poincaré disk model [4] represents the hyperbolic plane using a unit disk, 𝔻, in the complex plane ℂ. A point, z ∈ 𝔻, is represented by its complex coordinates z = x + yi, where x and y are real numbers, satisfying x² + y² < 1. Applying principles from the Poincaré hyperbolic disk, we construct a novel optimization model consisting of the transcendental arcosh equation bound by the λ boundary function, denoted as λ(r) to represent real values in the complex hyperbolic plane. The equation is defined as

arcosh(x + y) = ln[ (x + y) + sqrt((x + y)² − 1) ] (2)

where x and y are coordinates of points belonging to the Poincaré disk 𝔻. The domain for the function is x + y > 1, and the range is the set of all real numbers. The boundary λ to which this function is constrained is given by the following function:

λ(r) = (1 − r²) / (1 + r²) (3)

where r = sqrt(x² + y²) is the Euclidean norm of the point z in the disk. This function λ provides a mapping between the Poincaré disk and Mader models representing the boundary of the unit disk 𝔻 where the real values of the function arccosh(x + y) lie.

# 2.4.2. Mader Model

The λ boundary function, denoted as λ(r), connects the Poincaré disk model to the Mader model of Euclidean space [5]. The λ boundary function acts as a bijective mapping function 𝔻 → 𝔽 where 𝔽 is a model in Euclidean space. The Mader model, denoted as 𝔽, is defined as the interior of a unit disk ω in the standard Euclidean plane. Points inside the disk are represented by coordinates (x,y). The boundary of the disk (the circle) represents points where x² + y² = 1. The λ boundary function preserves distances between the Euclidean plane 𝔼 and the Poincaré disk 𝔻 via the bijections 𝔼 → 𝔽 and 𝔻 → 𝔽.