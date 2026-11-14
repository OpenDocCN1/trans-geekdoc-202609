rule gives \(\mathbf{J}(\mathbf{F}) = \mathbf{J}(\mathbf{F}_2)\mathbf{J}(\mathbf{F}_1)\), where \(\mathbf{J}(\mathbf{F}_2)\) is \(D \times M\) and \(\mathbf{J}(\mathbf{F}_1)\) is \(M \times D\). Now we can apply our determinant formula as follows:
\(\det \mathbf{J}(\mathbf{f}) = \det(\mathbf{I}_D + \mathbf{J}(\mathbf{F})) = \det(\mathbf{I}_D + \mathbf{J}(\mathbf{F}_2)\mathbf{J}(\mathbf{F}_1)) = \det(\mathbf{I}_M + \mathbf{J}(\mathbf{F}_1)\mathbf{J}(\mathbf{F}_2)).\) (23.38)

Since the final determinant costs \(O(M^3)\), we can make the Jacobian determinant efficient by reducing \(M\), that is, by narrowing the bottleneck.

An example of the above is the planar flow of [RM15]. In this model, each residual block is an MLP with one hidden layer and one hidden unit. That is,
\(\mathbf{f}(\mathbf{u}) = \mathbf{u} + \mathbf{v}(\sigma(\mathbf{w}^\top \mathbf{u} + b)),\) (23.39)

where \(\mathbf{v} \in \mathbb{R}^D\), \(\mathbf{w} \in \mathbb{R}^D\) and \(b \in \mathbb{R}\) are the parameters, and \(\sigma\) is the activation function. The residual block is the composition of \(\mathbf{F}_1(\mathbf{u}) = \mathbf{w}^\top \mathbf{u} + b\) and \(\mathbf{F}_2(z) = \mathbf{v}\sigma(z)\), so \(M = 1\). Their Jacobians are \(\mathbf{J}(\mathbf{F}_1)(\mathbf{u}) = \mathbf{w}^\top\) and \(\mathbf{J}(\mathbf{F}_2)(z) = \mathbf{v}\sigma'(z)\). Substituting these in the formula for the Jacobian determinant we obtain:

\(\det \mathbf{J}(\mathbf{f})(\mathbf{u}) = 1 + \mathbf{w}^\top \mathbf{v} \sigma'(\mathbf{w}^\top \mathbf{u} + b),\) (23.40)

which can be computed efficiently in \(O(D)\). Other examples include the circular flow of [RM15] and the Sylvester flow of [Ber+18].

This technique gives an efficient way of computing determinants of residual connections with bottlenecks, but in general there is no guarantee that such functions are invertible. This means that invertibility must be satisfied on a case-by-case basis. For example, the planar flow is invertible when \(\sigma\) is the hyperbolic tangent and \(\mathbf{w}^\top \mathbf{v} > -1\), but otherwise it may not be.

# 23.2.6 Continuous-time flows

So far we have discussed flows that consist of a sequence of bijections \(\mathbf{f}_1, \dots, \mathbf{f}_N\). Starting from some input \(\mathbf{x}_0 = \mathbf{u}\), this creates a sequence of outputs \(\mathbf{x}_1, \dots, \mathbf{x}_N\) where \(\mathbf{x}_n = \mathbf{f}_n(\mathbf{x}_{n-1})\). However, we can also have flows where the input is transformed into the final output in a continuous way. That is, we start from \(\mathbf{x}_0 = \mathbf{x}(0)\), create a continuously-indexed sequence \(\mathbf{x}(t)\) for \(t \in [0, T]\) with some fixed \(T\), and take \(\mathbf{x}(T)\) to be the final output. Thinking of \(t\) as analogous to time, we refer to these as continuous-time flows.

The sequence \(\mathbf{x}(t)\) is defined as the solution to a first-order ordinary differential equation (ODE) of the form:
\(\frac{d\mathbf{x}}{dt}(t) = \mathbf{F}(\mathbf{x}(t), t).\) (23.41)

The function \(\mathbf{F} : \mathbb{R}^D \times [0, T] \to \mathbb{R}^D\) is a time-dependent vector field that parameterizes the ODE. If we think of \(\mathbf{x}(t)\) as the position of a particle in \(D\) dimensions, the vector \(\mathbf{F}(\mathbf{x}(t), t)\) determines the particle's velocity at time \(t\).

The flow (for time \(T\)) is a function \(\mathbf{f} : \mathbb{R}^D \to \mathbb{R}^D\) that takes in an input \(\mathbf{x}_0\), solves the ODE with initial condition \(\mathbf{x}(0) = \mathbf{x}_0\), and returns \(\mathbf{x}(T)\). The function \(\mathbf{f}\) is a well-defined bijection if the solution to the ODE exists for all \(t \in [0, T]\) and is unique. These conditions are not generally satisfied for arbitrary \(\mathbf{F}\), but they are if \(\mathbf{F}(\cdot, t)\) is Lipschitz continuous with a Lipschitz constant that does not