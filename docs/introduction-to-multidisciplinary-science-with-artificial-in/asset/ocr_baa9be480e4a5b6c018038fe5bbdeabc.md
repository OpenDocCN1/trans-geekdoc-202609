where $\varepsilon^{(1)} = 1 + \chi^{(e;1)}$ and

$\boldsymbol{P}_{\mathrm{NL}} = \chi^{(e;2)} \boldsymbol{E}^2 + \chi^{(e;3)} \boldsymbol{E}^3 + \dots \tag{3.72}$

Using the relation $\nabla \times \nabla \times \boldsymbol{E} = -\nabla^2 \boldsymbol{E} + \nabla (\nabla \cdot \boldsymbol{E})$ and assuming that there are no free charges or currents (i.e., assuming (i.e., $\nabla \cdot \boldsymbol{E} = 0$), we obtain

$\nabla^2 \boldsymbol{E} - \frac{\varepsilon^{(1)}}{c_0^2} \frac{\partial^2 \boldsymbol{E}}{\partial t^2} = \mu_0 \frac{\partial^2 \boldsymbol{P}_{\mathrm{NL}}}{\partial t^2} . \tag{3.73}$

# Noncentrosymmetric and centrosymmetric media.

Here is the 1D equation of motion of the electron position, $x$, when an electric field, $E$:

$m \frac{d^2 x}{dt^2} = -2 m \gamma \underbrace{\frac{dx}{dt}}_{\text{damping}} - \underbrace{m \omega_0^2 x - m a x^2 + m b x^3}_{\text{restoring force}} - e E \tag{3.74}$

and by using $P = -N e x$ as

$\frac{d^2 P}{dt^2} = -2 \gamma \frac{dP}{dt} - \omega_0^2 P + \frac{a}{N e} P^2 + \frac{b}{N^2 e^2} P^3 + \frac{N e^2}{m} E , \tag{3.75}$

where $a$ and $b$ are parameters that characterize the strength of the nonlinearity, $-e$ is the charge of the electron, $\gamma$ is the damping parameter, and $N$ is the number of dipoles per unit volume. We arrived at this equation by assuming that the restoring force is a nonlinear function of the displacement of the electron from its equilibrium position. We also retained the linear and nonlinear terms in the Taylor series expansion of the restoring force in the displacement $x$. The potential energy function corresponding to this form of the restoring force is

$U(x) = - \int \tilde{F}_{\text{restoring}} dx = \frac{1}{2} m \omega_0^2 x^2 + \frac{1}{2} m a x^3 - \frac{1}{4} m b x^4 . \tag{3.76}$

This potential function is illustrated in the Figure 3.12. When $a = b = 0$, the potential that the atomic electron feels is perfectly parabolic. When $a \neq 0$ and $b = 0$, the electron is no longer in a perfect parabola. This model describes noncentrosymmetric crystals. When $a = 0$ and $b \neq 0$, the potential function is symmetric (i.e., $U(x) = U(-x)$) and the potential energy function contains even powers of $x$. This model illustrates centrosymmetric. When $a \neq 0$ and $b \neq 0$, (3.74) describes noncentrosymmetric media. Let us now derive $\chi^{(e;1)}$, $\chi^{(e;2)}$, and $\chi^{(e;3)}$.

# *Linear susceptibility.*

This case corresponds to $a = b = 0$ in (3.74). By taking the Fourier transform of this equation, we obtain

$[(\omega_0^2 - \omega^2) x + 2 i \omega \gamma] x = -\frac{e}{m} E \quad \text{or} \quad x(\omega) = \frac{-e E}{m D(\omega)} , \tag{3.77}$

where

$D(\omega) = \omega_0^2 - \omega^2 + 2 i \omega \gamma . \tag{3.78}$