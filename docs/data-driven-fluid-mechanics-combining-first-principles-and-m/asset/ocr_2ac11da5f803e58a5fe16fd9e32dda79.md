the dynamics of the closed-loop system can be written as

\dot{\mathbf{x}} = (\mathbf{A} - \mathbf{B}\mathbf{K})\mathbf{x}, \tag{10.24}

which is the same as (10.9) with \mathbf{C} = \mathbf{I}. If we have desired closed-loop poles, then this can be achieved by finding the components of \mathbf{K} such that \mathbf{A} - \mathbf{B}\mathbf{K} has eigenvalues at these locations. If the system is controllable, then this can always be achieved. For example, if we wish to place poles at p = -0.5 \pm 0.5i for our systems P1 or P2 with full-state feedback, then we find that \mathbf{K} = [1.0965 \; 0.0095]^T. Pole placement can be computed using the command K = place(A,B,p) in either MATLAB or Python.

# 10.5.2 Optimal Control

So far, the design of controllers has seemed somewhat ad hoc, and has relied upon tuning parameters based on insight and desired properties. This motivates the question: is there a way to define a controller that is, in some sense, the “best” ? At least for some definition of “best,” then this is something that we can indeed do. For simplicity, assume that we have full-state feedback. The idea is that, when applying control, we want to balance a desire to drive the system to a specified controlled state (e.g., to zero), while at the same time ensuring that we are limiting the exertion of our controller (i.e., penalizing the use of too much input energy). Mathematically, one way to account for both of these objectives is by constructing a cost function of the form

J = \int_{t=0}^{\infty} \left( \mathbf{x}^T \mathbf{Q} \mathbf{x} + \mathbf{u}^T \mathbf{R} \mathbf{u} \right) dt, \tag{10.25}

where \mathbf{Q} and \mathbf{R} are positive definite matrices that define the penalty associated with nonzero states and control effort, respectively. A controller that is designed to minimize (10.25) is called an LQR controller. Mathematically, this control law that minimizes (10.25) is given by

\mathbf{K} = \mathbf{R}^{-1} \mathbf{B}^T \mathbf{M}, \tag{10.26}

where \mathbf{M} is the unique positive definite matrix that satisfies the algebraic Riccati equation

\mathbf{A}^T \mathbf{M} + \mathbf{M}\mathbf{A} - \mathbf{M}\mathbf{B}\mathbf{R}^{-1}\mathbf{B}^T\mathbf{M} + \mathbf{Q} = 0. \tag{10.27}

This might look like a difficult problem to solve, but once again there are commands in MATLAB and Python libraries that will output the gain matrix K that optimizes (10.25). As well as being “optimal” in this sense, it turns out that the resulting controller also satisfies certain robustness properties (e.g., Stengel 1994). To test this method, we design LQR controllers for the system P1, using \mathbf{Q} = \mathbf{I} and three different choices of \mathbf{R} (10, 1, and 0.1), which prescribe how aggressive the resulting controller is in achieving the desired state. The characteristics of these feedback systems are explored in Figures 10.5 and 10.6. We see in Figure 10.5 that all three controllers stabilize the system, though the locations of the poles are noticeably