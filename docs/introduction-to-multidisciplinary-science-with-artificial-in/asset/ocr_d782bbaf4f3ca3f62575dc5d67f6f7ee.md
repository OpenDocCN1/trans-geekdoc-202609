![](bbox=[0.2, 0.12, 0.78, 0.3])

Figure 4.15. A quantum system interacts with a classical physics measuring device in the presence of its surrounding environment. The outcome of the measurement is recorded by the measuring apparatus.

where σ₁, σ₂, and σ₃ are the observables of spin particles along x-, y-, and z-axes, respectively. We can verify the eigenvectors of σ₁ are: [1/√2,1/√2]ᵀ with eigenvalue λ = 1 and [1/√2,−1/√2]ᵀ with eigenvalue λ = −1. We can also verify that the eigenvectors of σ₂ are: [1/√2,i/√2]ᵀ with eigenvalue λ = −1 and [1/√2,−i/√2]ᵀ with eigenvalue λ = +1; the eigenvectors of σ₃ are: [1,0]ᵀ with eigenvalue λ = 1 and [0,1]ᵀ with eigenvalue λ = −1. We also have σ₁² = σ₂² = σ₃² = I, where I is the identity matrix. Moreover, the three matrices share the same eigenvalues and the square of each eigenvalue is 1. Because eigenvalue is a measurement and the fact that the square of each eigenvalue is 1 means that we can only measure +1 and -1. There is no eigenvectors in common between σ₁, σ₂, and σ₃ which basically means that we cannot simultaneously make two measurements along two directions. In other words, the condition to measure two quantities simultaneously is that observables share the same eigenvectors. The eigenvalues are Note that for any given arbitrary vector a = [a₁,a₂]ᵀ with |a₁|²+|a₂|² = 1, there exist a normal vector n = [n₁,n₂,n₃]ᵀ (i.e., a direction) with n₁²+n₂²+n₃² = 1, such that

(σ · n) ( a₁ \ a₂ ) = ( a₁ \ a₂ ) ,  (4.69)

or

(n₁σ₁ + n₂σ₂ + n₃σ₃) ( a₁ \ a₂ ) = ( a₁ \ a₂ ) ,  (4.70)

and the eigenvalue is 1. Consequently, the spin will only go up or down in the direction indicated by n if the above condition is met. Note also that, for n = [cosθ,0,sinθ]ᵀ, we have

σ · n = ( cosθ  sinθ \ sinθ  −cosθ ) .  (4.71)

You get an answer when you measure a certain quantity. That answer corresponds to some eigenvalue. You leave the system with that eigenvalue and eigenvector. So