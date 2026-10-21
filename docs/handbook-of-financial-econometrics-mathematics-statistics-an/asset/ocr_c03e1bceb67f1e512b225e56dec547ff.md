which shows that the discount factor might be a linear combination of factors f with weights that vary as a vector of instrument z varies across different information set. Scaling the factors f by the instrument z achieves the same result. So equation (122.55) is equivalent to

M_{t+1} = b_0 f_{t+1} + b_1 (f_{t+1} × z_{t+1}). (122.56)

Here f_{t+1} denotes the investment return, functions of investment and capital only, that is, f_{t+1} = f(I_{t+1}^i / K_{t+1}^i, I_t^i / K_t^i); therefore, given the choice of instruments, performing the GMM estimation and testing with scaled factors is a completely general test of a dynamic, conditional factor pricing model based on the instruments.

Balvers and Huang (2007) derive the stochastic discount factor in which the productivity shock is the single factor in asset pricing model. The social planner maximizes

V(k_t, θ_t) = Max_{n_t,k_{t+1}} { u(c_t, \bar{n} - n_t) + δ E_t[ V(k_{t+1}, θ_{t+1}) ] }, (122.57)

subject to

θ_{t+1} = H(θ_t, ε_{t+1}) (122.58)
c_t = f(θ_t, n_t, k_t) - k_{t+1}. (122.59)

The lifetime utility of the representative consumer is maximized subject to a standard production function f(θ_t, n_t, k_t), where the inputs are labor n_t and capital k_t and an exogenous technology level θ_t. The productivity level is assumed to follow a Markov process as given by equation (122.58) with ε_t representing the zero-mean white noise productivity shock. Per-capita consumption is given in equation (122.59) as the part of capita production that is not invested. Through equation (122.57) to equation (122.59) and the stochastic discount factor, M_{t+1} = δ[ u_c(c_{t+1}, \bar{n} - n_{t+1}) / u_c(c_t, \bar{n} - n_t) ] to obtain

M_{t+1} = η_{t+1} / f_k(θ_{t+1}, n_{t+1}, k_{t+1}), (122.60)

with η_{t+1} = V_k(k_{t+1}, θ_{t+1}) / E_t[ V_k(k_{t+1}, θ_{t+1}) ]. The η_{t+1} represents a fundamental, nondiversifiable risk inherent in capital accumulation that cannot be ignored and should be needed for asset pricing. Balvers and Huang (2007), therefore, relate η_{t+1} to shocks in the marginal value of capital to obtain an explicit production-based expression for the asset pricing model. They