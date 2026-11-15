![](bbox=[0.285, 0.085, 0.705, 0.485])

Fig. 15.4 The geometry of a 47-bar transmission tower

**Example 4** As the final example, the sizing and geometric optimization of a 244-bar tower is considered. The primary geometry of the tower is shown in Fig. 15.9. This problem was first optimized by Saka [24]. The members of this tower are put into 26 groups. The elastic modulus is taken as 210 KN/mm² and the allowable tensile stress is considered as 140 N/mm². For design of this tower AISC is employed.

The loading of the tower together with displacement constraints are shown in Table 15.9. For this tower, two loading cases are considered. For designing members single angles with minimum cross section equal to 192 mm² are used. In this example due to higher size of the problem, the second method is employed.

In order to illustrate the performance of the network, a tower with 244 elements is considered in 4 substructures, each of which contains 50 elements. After 10 generations a neural network is trained. The output of the network after 40 generations is comparable with exact solution. The output consists of force and displacements. In Fig. 15.10 only the forces are used for comparison. The correlation factor is 0.9998 which is a suitable value. As it can be observed from this figure, neural network can efficiently be used in the process of optimization.