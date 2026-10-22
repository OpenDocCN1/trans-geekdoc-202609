follows:

$$\tilde{x}_b = x_b + \frac{i}{\omega}\int_0^{x_b} d_b(\eta)d\eta \quad (b=1,2,3), \tag{A.101}$$

where $d_b(x_b)$ is the decay factor. We assume that the decay factor is zero [i.e., $d_b(x_b)=0$] inside the main computational domain and positive [i.e., $d_b(x_b)=0$] in the absorbing region. The typical form of the decay factor is

$$d_b(x_b) = \left(\frac{x_a}{L}\right)^2 d_0 \tag{A.102}$$

with

$$d_0 = \frac{3V_{P,\max}\log(R_c)}{2L}, \tag{A.103}$$

where $L$ is the thickness of the PML layer and $R_c$ is the target theoretical reflection coefficient, generally chosen as 0.001.

By writing the spatial derivatives of the stresses and the particle-velocity equations (A.43) and (A.44), as follows:

$$\frac{\partial}{\partial\tilde{x}_b} = \frac{1}{\varepsilon_b}\frac{\partial}{\partial x_b}, \tag{A.104}$$

with

$$\varepsilon_b(x_b,\omega) = 1 + i\frac{d_b(x_b)}{\omega}, \tag{A.105}$$

and by taking the Fourier transform of equations (A.43) and (A.44) with respect to time, we arrive at

$$-i\omega v_a(\mathbf{x},\omega) = \sigma(\mathbf{x})\frac{1}{\varepsilon_b(x_b,\omega)}\frac{\partial\tau_{ab}(\mathbf{x},\omega)}{\partial x_b} \tag{A.106}$$

$$-i\omega\tau_{\alpha\beta}(\mathbf{x},\omega) = c_{\alpha\beta\eta\zeta}(\mathbf{x})\frac{1}{\varepsilon_\eta(x_\eta,\omega)}\frac{\partial\nu_\zeta(\mathbf{x},\omega)}{\partial x_\eta}. \tag{A.107}$$

Notice that rather than defining a new symbol to express this physical quantity after it has been Fourier-transformed, we have used the same symbol with different arguments, as the context unambiguously indicates the quantity currently under consideration. For example, $v_a(\mathbf{x},\omega)$ is the Fourier transform of $v_a(\mathbf{x},t)$ with respect to time. We will use this convention for the remaining part of this section. Finally, notice that we have not included the source terms here because they are generally zero in the absorbing regions.

To facilitate the algebra of the PML equations in (A.106) and (A.107), we found it convenient to redefine the stress field so that the system of equations in (A.43) and (A.44) and the ones in (A.106) and (A.107) can have the same mathematical structures. In other words, we can rewrite equations (A.106) and (A.106) as follows:

$$-i\omega v_a(\mathbf{x},\omega) = \frac{1}{\varepsilon_1\varepsilon_2\varepsilon_3}\sigma(\mathbf{x})\frac{\partial\tilde{\tau}_{ab}(\mathbf{x},\omega)}{\partial x_b} \tag{A.108}$$