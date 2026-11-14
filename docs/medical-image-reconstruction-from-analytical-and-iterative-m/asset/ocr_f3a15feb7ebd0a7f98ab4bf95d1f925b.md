# 6.2 Algebraic reconstruction technique

The main idea of the algebraic reconstruction technique (ART) algorithm (which is also known as the Kaczmarz method) is to make the estimated image satisfy one equation at a time as illustrated in Figure 6.3, where three lines (L1, L2, and L3) represent three equations, and their intersection is the solution. In this example, the image only consists of two pixels.

In Figure 6.3, $\bar{x}^0$ is the initial guess of the solution. The first step is to project this point $\bar{x}^0$ perpendicularly onto $L_1$, obtaining $\bar{x}^1$. Next, project $\bar{x}^1$ perpendicularly onto $L_2$ to obtain $\bar{x}^2$, and so on, projecting each point onto a line (which is one equation) one at a time. Eventually, the algorithm will converge to the solution of the system of equations (see Figure 6.3, top). If the equations are not consistent, the algorithm will bounce around and never converge (see Figure 6.3, bottom). One iteration is defined as the procedure of going through all the equations once.

![](bbox=[0.17, 0.38, 0.7, 0.86])

Fig. 6.3: The ART algorithm tries to satisfy each equation at each update.