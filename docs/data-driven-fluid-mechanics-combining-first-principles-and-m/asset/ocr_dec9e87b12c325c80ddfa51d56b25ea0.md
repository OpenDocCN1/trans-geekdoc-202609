instead it is only possible to evaluate the action of this matrix on an input vector. For example, in many modern fluid dynamics codes the matrix A_d is not actually represented, but because it is sparse, it is possible to implement efficient routines to multiply this matrix by a vector.

It is important to note that the ROM in (12.35) is formulated in discrete time, as it is based on discrete-time empirical snapshot matrices. However, it is simple to obtain the corresponding continuous-time system. In this example, D is the same in continuous time and discrete time, and in the full-order and ROMs.

Note that a BPOD model may not exactly satisfy the upper bound from balanced truncation (see (12.27)) due to errors in the empirical Gramians.

# Output Projection

Often, in high-dimensional simulations, we assume full-state measurements, so that p = n is exceedingly large. To avoid computing p = n adjoint simulations, it is possible instead to solve an output-projected adjoint equation (Rowley 2005),

x_{k+1} = A_d^* x_k + C_d^* \tilde{U} y, (12.36)

where \tilde{U} is a matrix containing the first r singular vectors of C_d. Thus, we first identify a low-dimensional POD subspace \tilde{U} from a direct impulse response, and then only perform adjoint impulse response simulations by exciting these few POD coefficient measurements. More generally, if y is high-dimensional but does not measure the full-state, it is possible to use a POD subspace trained on the measurements, given by the first r singular vectors \tilde{U} of C_d C_d. Adjoint impulse responses may then be performed in these output POD directions.

# Data Collection and Stacking

The powers m_c and m_o in (12.32) signify that data must be collected until the matrices C_d and O_d^* are full rank after which the controllable/observable subspaces have been sampled. Unless we collect data until transients decay, the true Gramians are only approximately balanced. Instead, it is possible to collect data until the Hankel matrix is full rank, balance the resulting model, and then truncate. This more efficient approach is developed in Tu and Rowley (2012) and Luchtenburg and Rowley (2011).

The snapshot matrices in (12.29) are generated from impulse response simulations of the direct (12.28a) and adjoint (12.36) systems. These time-series snapshots are then interleaved to form the snapshot matrices.

# Historical Note

The balanced POD method described earlier originated with the seminal work of Moore (1981), which provided a data-driven generalization of the minimal realization theory of Ho and Kalman (1965). Until then, minimal realizations were defined in terms of idealized controllable and observable subspaces, which neglected the subtlety of degrees of controllability and observability.