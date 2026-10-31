
## Mode 1

![](img/ddadb1d3eaa6f9576eea68f95d453bca_225_0.png)

Figure 10.1 The first two POD modes (transverse velocity component) for flow over a circular cylinder at a Reynolds number of 60, on a trajectory going between the unstable equilibrium and limit cycle of the system.

## Mode 2

![](img/ddadb1d3eaa6f9576eea68f95d453bca_225_1.png)

![](img/ddadb1d3eaa6f9576eea68f95d453bca_225_2.png)

Figure 10.2 Evolution of the first two POD mode coefficients, corresponding to modes shown in Figure 10.1. Shown are both the actual coefficients, and those predicted by the identified linear dynamics (10.4). Only the data to the left of the vertical line is used for the identification of the linear model.

Figures 10.1 and 10.2, respectively. As well as showing the true evolution of the POD coefficients (which will be our system states $x_1$ and $x_2$), we also show the evolution predicted by the identified linear model. The linear model accurately captures the true behavior over a region in time substantially larger than that used for system identification, though is unable to capture the eventual saturation of the coefficient amplitudes as the true system converges toward the limit cycle. Note that the portion of the data used for system identification is the same as that used to compute POD for the example in Chapter 6. Using feedback control, we might hope to be able to keep the oscillations seen in Figure 10.2 to small enough amplitudes such that the linear model remains accurate, and that controllers designed using this linear model remain effective.

For this system, we obtain the linearized dynamics

$$A = \begin{bmatrix}0.0438 & -0.7439\\0.7373 & 0.0527\end{bmatrix}.\tag{10.4}$$

This system has two unstable eigenvalues at $0.0483 \pm 0.7406i$, which is expected, since the envelope of the POD coefficient amplitudes plotted in Figure 10.2 is growing in time. The fact that these eigenvalues come as a complex conjugate pair is also expected, since the dynamics of the system are oscillatory.

Note that this linear system is a simplification of the true dynamics not just because we are using a linear model, but also because we are neglecting other states of the system, corresponding to lower-energy, truncated POD modes. For example, identifying a linear system with more states could model (at least in a linear sense) the slow modification of the “mean” as the amplitude of the oscillations increases, as well as dynamics with frequency content at harmonics of the primary oscillation frequency. These dynamics are discussed in further detail in Chapter 14.

We will explore various choices for the B and C matrices in Sections 10.2–10.5, but will typically choose to directly observe and control one of the system states. This also represents a simplification of what measurement and control might look like for the true system in practice, where localized sensors and actuators might be more feasible than directly measuring or controlling an entire POD mode.

## 10.2 Proportional, Integral, and Derivative Feedback Control

Suppose now that we want to manipulate our system to achieve a desired output, y(t). For the example described, perhaps we want to stabilize the unstable system, and thus eventually drive all components of y(t) to zero. For an unstable system such as this, this objective is impossible without the availability of real-time information about the state of the system, and how it is responding to attempts at control. It would be equivalent, for example, trying to balance an inverted pendulum without any visual or tactile measurements.

What we want to do then, is to develop a means for utilizing knowledge of the system output y(t) in order to determine appropriate system inputs to achieve the desired control objective. This general concept is known as feedback control. For example, we could link the output to the input using the following arrangement:

![](img/ddadb1d3eaa6f9576eea68f95d453bca_226_0.png)

Here we refer to K as the controller, which could simply be a constant, or might have its own internal dynamics.

In this section, we will assume that we have a single input to our system (so B has one column), and a single output (so C has one row), and will always assume that there is no direct feedthrough from the input to the output (so D = 0). It will be helpful to look at our system in the frequency domain, which we can obtain from a state-space

![](img/ddadb1d3eaa6f9576eea68f95d453bca_227_0.png)

Figure 10.3 Effect of applying proportional feedback control with K = 1 to the two systems, P1 and P2.

system using (10.3). We will explore two different input and output combinations. First, we have the case where the input uses a different state variable as the output (system P1), using the input and output matrices

$\boldsymbol{B}_1 = \begin{bmatrix}1\\0\end{bmatrix}, \quad \boldsymbol{C}_1 = \begin{bmatrix}0 & 1\end{bmatrix}, \tag{10.5}$

giving the transfer function (see (10.3))

$P_1(s) = \frac{0.7373}{s^2 - 0.09654 s + 0.5508}. \tag{10.6}$

Second, we use the input and output matrices

$\boldsymbol{B}_2 = \begin{bmatrix}0\\1\end{bmatrix}, \quad \boldsymbol{C}_2 = \begin{bmatrix}0 & 1\end{bmatrix}, \tag{10.7}$

giving the transfer function

$P_2(s) = \frac{s - 0.04381}{s^2 - 0.09654 s + 0.5508}. \tag{10.8}$

Note that the denominators of the transfer functions P1(s) and P2(s) are the same quadratic polynomial. This is as expected, since the roots of this polynomial are the poles of the system, which are in turn given by the eigenvalues of A, which is the same for both systems.

To begin with, and before doing any further analysis of this system, suppose that we try to control our systems with the simplest feedback control, where K from our schematic diagram being a multiplicative constant. This is known as proportional control. The results of applying this control to our system with K = 1 is shown in Figure 10.3, where we have the reference set at r = 0. Here, we allow the system to evolve without any inputs, before turning on control at a time t = 15. Note that here we are applying control to the unstable linearized system, rather than the full nonlinear system. We notice that the system P2 seems to be stabilized, while P1 remains unstable.

How might we have predicted this observed behavior? With $r = 0$, the system input is given by law $\boldsymbol{u} = -K \boldsymbol{y} = -K C \boldsymbol{x}$. This means that the system with feedback evolves according to

$$\dot{\boldsymbol{x}} = (\boldsymbol{A} - \boldsymbol{B} K \boldsymbol{C}) \boldsymbol{x}. \tag{10.9}$$

The stability of this system is determined by the eigenvalues of the matrix $\boldsymbol{A} - \boldsymbol{B} K \boldsymbol{C}$. In the frequency domain, it is easy to show that the transfer function of the controlled system is given by

$$G_{CL} = \frac{P}{1 + P K}, \tag{10.10}$$

where $K$ is the transfer function for the controller in the frequency domain (which is a constant for proportional control). Note that more generally, a closed-loop transfer function is given by

$$G_{CL} = \frac{G_{OL}(s)}{1 + G_{FB}(s)}, \tag{10.11}$$

where $G_{OL}$ denotes the open-loop transfer function between $r$ and $y$, and $G_{FB}$ is the transfer function going around the feedback loop. Going back to (10.10), here the poles of the closed-loop system will be the solutions to

$$1 + P K = 0, \tag{10.12}$$

which can be expressed as the roots of a *characteristic polynomial*. To study the systems $P_1$ and $P_2$ in more detail, consider a more general system of the form

$$P(s) = \frac{a_1 s + a_0}{s^2 + b_1 s + b_0}, \tag{10.13}$$

for which $P_1(s)$ and $P_2(s)$ are both special cases. From (10.12), the closed-loop poles of this system for control with a constant $K$ can be found to be the solutions to the polynomial

$$s^2 + (b_1 + a_1 K) s + (b_0 + a_0 K) = 0. \tag{10.14}$$

These solutions are given by

$$s = -\frac{b_1 + a_1 K}{2} \pm \frac{\sqrt{(b_1 + a_1 K)^2 - 4(b_0 + a_0 K)}}{2}. \tag{10.15}$$

From this, we can start to understand why proportional control with $K = 1$ worked for the system $P_2$, but not for $P_1$. The fact that $P_2$ has a nonzero $a_1$ term means that the control is able to shift the real component of the poles by $-a_1 K /2$, thus making them more stable (assuming that $a_1 > 0$). Note also that when the argument of the square root is negative, this term will not affect the real component of the poles. Conversely, if $a_1 = 0$ as is the case with $P_1$, the control only affects the square root term in (10.15). If the argument of the square root is negative, then this does not change the real component, and thus the stability, of the system. On the other hand, if the argument of the square root is positive, then one pole will become more stable, but the other becomes more unstable as the feedback gain either increases or decreases. From this, we can conclude that proportional feedback is unable to stabilize $P_1$.
