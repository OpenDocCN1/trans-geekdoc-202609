![](bbox=[0.15, 0.11, 0.85, 0.43])

Figure 1.12. Derivation of equation of motion.

with a flow. As another example, consider a case (translational equation) where a substance is transported in a flow at a constant velocity $a_0$ and the concentration of the substance is $C:u(x,t)$. Figure 1.13 shows a schematic diagram for a one-dimensional equation.

The advection equation given by

$$u_t + a_0u_x = 0$$

(1.2)

has an exact solution in which the geometry given by initial conditions moves along the $x$ axis at a velocity of $a_0$.

The concentration $u$ can be calculated by setting the time $t$ and the position $x$ and using this exact solution. Furthermore, this exact solution itself can be differentiated to calculate time derivative of $uu_t$ or space derivation of $uu_x$. Regression analysis is then used to obtain a regression equation that describes time derivative as spatial derivative. This regression equation is a derived PDE (Figure 1.13).

As described earlier, if the physical data are obtained and a partial derivative can be obtained for each piece of data, a PDE can be derived in a data-driven manner using an Excel analysis tool. The above example deals with a PDE consisting of linear terms where a constant coefficient