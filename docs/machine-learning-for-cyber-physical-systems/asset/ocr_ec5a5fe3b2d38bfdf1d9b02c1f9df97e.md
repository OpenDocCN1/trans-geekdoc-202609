# 2 State of the Art

First approaches for process control based on ML were conducted by Oh and co-workers [4] who apply Neural Network/Partial Least Squares to model the relationship between multiple process parameters and multiple quality parameters in the production process of metal plates of a complex structure. Senn and co-workers [5] use Principal Component Analysis and Artificial Neural Networks to model the relation between observed quantities and state variables for a deep drawing process. However, comprehensive studies for ML based process control within production lines are still sparse. In order to contribute to fill this gap we propose an intuitive approach to intelligently control the process parameters within a production line for quality improvement of the final product. The introduced intelligent system is based on linear regression and least squares optimization.

# 3 Data and Methods

We consider a production line for the press hardening of sheet metal in order to produce center pillars, which are ultra-high-strength car body parts. Here, we will focus on the three process steps warming, handling and quenching, see Figure 1. The process involves inserting sheets, which have been heated beyond the austenitizing temperature of about 900°C, into a cooled forming tool, in which they are then quenched. The thermal integrated processing produces press-hardened parts with an extremely high tensile strength of up to 1,500 MPa for the ultra-high-strength steel 22MnB5. The handling of the sheets is done by robots.

![](bbox=[0.17, 0.615, 0.83, 0.725])

**Fig. 1.** Production line for the press hardening of sheet metal focusing on the three steps: (1) warming in a furnace unit, (2) handling with a robot system with grippers, and (3) quenching.

Similar to Oh et al. [4] each process can be described by its

+   - uncontrollable factors (initial conditions of materials or processes; and fix variables),
+   - controllable factors (adjustable variables) and
+   - quality variables (response variables representing the final product quality).