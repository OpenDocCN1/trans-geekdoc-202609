
It serves to prevent the loss of energy within the plasma. If energy is lost in the plasma, the fusion reaction slows down, and energy cannot be produced. It prevents energy from being lost in the plasma through the edge.

The edge plays a critical role in a fusion reactor. Therefore, it is important to constantly monitor and maintain the condition of the edge.

In a fusion reactor, a divertor refers to a device that separates the plasma. Plasma, as explained earlier, consists of high-energy particles produced at high temperatures and pressures. As a result, the plasma can damage walls. Therefore, it is necessary to separate the plasma. A divertor is a device that separates such plasma by changing the direction in which the plasma flows. The divertor is usually installed inside the container that contains the plasma. By changing the plasma's flow direction, the plasma can be separated. Divertors play an important role in fusion reactors. Among the most important roles are the following:

- It serves to separate the plasma within the container that houses the plasma. This prevents the plasma from damaging the walls.
- It serves to prevent the loss of energy within the plasma. If energy is lost in the plasma, the fusion reaction slows down, and energy cannot be produced. Through the divertor, energy can be prevented from being lost in the plasma.

The divertor plays a critical role in a fusion reactor. Therefore, it is important to constantly monitor and maintain the condition of the divertor.

In a fusion reactor, it is expected to visualize the plasma region from a group of magnetic field lines calculated by setting an appropriate starting point based on the electromagnetic field simulation results. A device called the Force Free Helical Reactor (FFHR), designed by the National Institute for Fusion Science (NIFS), has helical coils to generate twisted magnetic field lines [51]. The plasma is confined within a donut-shaped vacuum vessel. The large-circumferential direction of the donut-shaped vacuum vessel is called the toroidal direction, and the small-circumferential direction is called the poloidal direction. In the helical type, as the name implies, an electric current is applied to the helical circumferential coils to form a magnetic field that confines the plasma, and the enveloping surface of the magnetic flux is considered the boundary of the plasma region.

One of the main problems with the device designed by FFHR is that the space between the plasma region geometry and the structure in the vessel is limited. Conventional visualization of the plasma region mainly calculated the intersection of magnetic field lines in the poloidal plane of the plasma and expressed the plasma region on a two-dimensional cross section. Based on this visualization, the geometry of the in-vessel structures was examined to determine whether they were in contact with the plasma boundary. This method was performed by rotating the poloidal surface one degree in the toroidal direction, which was not an efficient way to get a bird’s-eye view of the plasma region shape. Therefore, in order to more efficiently determine the contact between the plasma and the structure, we considered it necessary to construct a 3D model of the plasma shape to determine the contact with the in-vessel structure. The objective of this case study is to create a 3D model representing the plasma existence region as a closed curved surface based on the magnetic field group data in order to facilitate identification of interference between the plasma and the 3D design data of the in-vessel structure components.

In this section, we will present an overview of electromagnetic field simulations in a fusion reactor. To calculate the steady-state magnetic field lines, 3D modeling of the internal environment of the FFHR is performed by inputting the precise structure of the magnetic field coils, vacuum vessel, and blanket and then calculating the electromagnetic field simulation using the finite element method (FEM), which is described later in 4.3.2.1. To trace the magnetic field lines from a suitable starting point, the magnetic field line trace code (MGTRC) is used. At present, 799 magnetic field lines are stored. And all magnetic field lines consist of $4.8 \times 10^6$ points (Figure 2.40).

As shown in Figure 2.40, the calculated 799 magnetic field lines are twisted, making it difficult to assess their intersection with the structure based on the magnetic field lines alone. The key is to detect interference with components in the fusion reactor, which requires evaluation of the outermost magnetic field lines.

90 poloidal surfaces with intersections with magnetic field lines are set up so the plasma area shape is 90° in the toroidal direction. Additional starting points are needed to draw the magnetic field lines leading to the surface layer of the edge and the legs of the divertor. A divertor is one of the devices that make up a fusion reactor and is responsible for three functions: particle pumping, heat removal, and improved plasma confinement. These starting points are indicated interactively using the Point Annotation Tool [52]. This process should be completed before the plasma region geometry is expanded to 90°.

![](img/fa57e7010b16a211d5cf69ebb17e416e_114_0.png)

Figure 2.40. Group of magnetic field lines calculated in the structure of a helical fusion reactor.

To find the outermost closed curved surfaces of the magnetic and edge layers, labeling is required to indicate the trajectory of the points on the Poincaré plot. If the magnetic field lines stay in the plasma region long enough, all the points that make up the magnetic field lines are labeled with a "2". At the same time, all points comprising the magnetic field lines reaching the outer wall of the fusion reactor or the divertor are labeled "0" or "1", respectively. Magnetic field lines that reach the outer wall of the fusion reactor or the divertor are considered to have escaped outside the plasma region.

In this case study, a suitable NN model is first created that explains the point data on the magnetic field lines (Figure 2.40). NN model building is an NN parameter optimization calculation that minimizes the loss function. The loss function is the mean square error $\text{MSE}_u = \lVert \hat{u} - u \rVert_2^2 / N_u$ between the point data $u(x, y, z)$ and the data regressed by the NN model, where $N_u$ represents the number of points on the magnetic field lines. In this case, the point data represent the probability that the point is in the plasma region and take a value of 1.0 on the magnetic field lines that stay within the plasma region. The information for the NN to perform this calculation is as follows:

- **Structure**: The NN has a five-layer structure with a number of nodes of 3-512-128-16-3 in the forward direction. The first three and the last three are the number of nodes in the input and output layers, respectively.
- **Activation function**: Rectified linear unit activation function
- **Optimization calculation**: RMSProp

![](img/fa57e7010b16a211d5cf69ebb17e416e_115_0.png)

Figure 2.41. Visualization of the envelope surface of a group of magnetic field lines using isosurfaces.

Figure 2.41 presents a visualization of the envelope surface formed by a group of magnetic field lines passing through a region identified as a plasma region and a divertor, represented as an isosurface.

# Chapter 3
Practical Part

So far, we have explained how to create a spatiotemporal model using an NN from physical data. In terms of application examples, we have explained the method used for visualizing page information from ancient literature data shot utilizing a three-dimensional CT machine. In addition, we have explained the method for visualizing the plasma region from a magnetic line group calculated from the results of analyzing electromagnetic fields in a fusion reactor.

In this chapter, we will begin by explaining differentiation operations on a spatiotemporal model. The ability to perform differentiation operations may improve the accuracy of an NN model in some cases, and also enhance the accuracy with which to evaluate gradient data, which is important for visualization. It allows you to find an essential partial differential term and derive a PDE governing the given physical data. You can also solve the given PDE. As described earlier, adding differential information increases the added value of the NN model. Since differential information is crucial for a PDE that describes physics, we refer to such NN as physics-informed neural network (PINN).

### 3.1. About PINNs

An NN suitable for analyzing physical data is a physics-informed neural network (PINN). A PINN is a kind of machine learning model proposed by Raissi et al. that incorporates the laws of physics into the structure of an NN itself [28]. This allows a model to make predictions that are consistent with the underlying physics based on which a system is modeled. A PINN is particularly useful for solving problems, such as fluid dynamics, structural dynamics, and electrodynamics problems, where the relationship between variables is governed by the laws of physics. Incorporating
