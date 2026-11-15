
## 40.3 Methodology

### 40.3.1 Framework for Generating Digital Twin Models in Construction

This study aims to address the limitations in current research on DTM for complex steel structures, using a complex rigid skeleton bridge as a case study. The process consists of three steps: (1) creating the GDTM using 3D laser scanning and feature extraction algorithms; (2) predicting the behavior of the DTM to understand the structural installation; and (3) controlling the construction process with a mechanically endowed DTM, informed by bridge-related control theory. This approach aims to enhance the application of digital twin technology in complex steel structures and improve construction progress, quality (Figure 40.1).

![](img/0dd4397c67b063014553965e4f1cf7e4_711_0.png)

**FIGURE 40.1** Generation process of digital twin model.

### 40.3.2 Generation of Geometric Digital Twin Models

### 40.3.2.1 Point Cloud Pre-processing

Point cloud pre-processing is crucial for ensuring the accuracy and efficiency of post-processing in large-sized skeleton data. This involves noise reduction and point cloud alignment, which can be addressed through a robust filtering algorithm targeting the noise points and an improved ICP algorithm for fine alignment. The improved ICP algorithm consists of three main steps: (1) utilizing the KD-tree algorithm to find neighboring points in both directions; (2) determining the normal vector of the point set and filtering based on a set queue value for the angle cosine; and (3) employing the SVD decomposition method to calculate rotation and translation vectors between the point sets, iterating until the condition is satisfied. This approach effectively mitigates noise and aligns point clouds, improving data analysis accuracy and geometric feature information acquisition.

### 40.3.2.2 Extraction of Features

The algorithm extracts the central feature line of the stiff skeleton point cloud and segments it using micro-segmentation. The steps are:

- 1. Rotate the point cloud to align with the two-dimensional plane's coordinate axis.
- 2. Segment the stiff skeleton point cloud by dividing it into micro-segments based on the maximum and minimum values of X or Y coordinates (Figure 40.2a).
- 3. Fit curves to obtain spatial position parameters of the point cloud cylindrical surface.
- 4. Generate the centerline of the circular tube by interpolating the coordinates of all micro-segment cylindrical center points using a spline curve (Figure 40.2b).

### 40.3.2.3 Generation of Geometric Digital Twin Models

The BIM software platform is used to create a parametrically driven stiff skeleton design model, with the IFC interface generating a GDTM for stiffness digitalization (Figure 40.2c). To address manufacturing deviations, virtual assembly with segment point cloud data is performed before lifting the skeleton. This detects deviations in advance, allowing necessary measures to be taken. The splicing process aligns bolt hole coordinates on adjacent flanges using the Prandtl analysis. The algorithm calculates optimal rotation translation parameters to align skeleton segments, ensuring precise assembly of all sections (Figure 40.2d).

![](img/0dd4397c67b063014553965e4f1cf7e4_713_0.png)

![](img/0dd4397c67b063014553965e4f1cf7e4_713_1.png)

![](img/0dd4397c67b063014553965e4f1cf7e4_713_2.png)

![](img/0dd4397c67b063014553965e4f1cf7e4_713_3.png)

**FIGURE 40.2** Generation of geometric digital twin models: (a) the effect of point cloud segmentation; (b) generation of stiff skeleton centerlines; (c) model of a geometric digital twin; and (d) virtual skeleton assembly.

### 40.3.3 Construction Digital Twin Model Control

### 40.3.3.1 Preliminary Calculations

The construction DTM accurately simulates a structure's mechanical behavior during the construction process, such as deformation under force and boundary constraints. This model ensures the target construction state is achieved while maintaining control over each key step. The stress-free state method is crucial for cable lifting control, ensuring the arch forming line aligns with the design line. The GDTM of the stiff skeleton can be upgraded to the construction DTM (Figure 40.3a). Symmetric lifting is used during the stiff skeleton lifting stage, activating corresponding units, boundary groups, and load groups. The division of construction stages should balance accuracy and calculation complexity, adhering to the construction plan requirements.

### 40.3.3.2 Line Monitoring

Rigid skeleton lifting construction relies on three types of lines: production, construction, and bridge lines, aiming to align the completed bridge with the design alignment. Due to deviations caused by the diagonal buckling system's rigidity and stability during lifting, 3D scanning technology is used to obtain the actual on-site state of the rigid skeleton and analyze deviations from the theoretical alignment. Figure 40.3b shows the point cloud data from the cantilever lifting section.

### 40.3.3.3 Soli Modification

The previously described method extracts the skeleton's centerline at each lifting stage, comparing it to theoretical lines and analyzing differences for on-site adjustments. When significant deviations occur, cable force adjustments are made to ensure lifting process safety. This adjustment is reduced to cable force optimization, with specific methods to be followed.

Assuming that the current construction stage's actual line is z^1 as observed by 3D scanning technology, and that the line is composed of the extracted characteristic control points, then

```
$Z^1 = (z^1_1, z^1_2, z^1_3, ..., z^1_i)$ (40.1)
```

The corresponding control points is calculated using the stiff skeleton theory line as

```
$Z^2 = (z^2_1, z^2_2, z^2_3, ..., z^2_i)$ (40.2)
```

![](img/0dd4397c67b063014553965e4f1cf7e4_715_0.png)

![](img/0dd4397c67b063014553965e4f1cf7e4_715_1.png)

![](img/0dd4397c67b063014553965e4f1cf7e4_715_2.png)

**FIGURE 40.3** Construction digital twin model control: (a) analysis of lifting construction model; (b) point cloud data for lifting construction; and (c) port plane of the combined section.

The required incremental cable force is

\( T = (t_1, t_2, t_3, \dots, t_n) \) (40.3)

If the adjustment of the buckles caused the displacement change of the stiff skeleton's control point at the current construction phase, the influence matrix is

\( C = \begin{bmatrix} \circ & c_{11} & c_{12} & \cdots & c_{1n} \\ c_{21} & c_{22} & \cdots & \cdots & c_{2n} \\ \vdots & \vdots & \ddots & \vdots & \vdots \\ c_{i1} & c_{i2} & c_{i3} & \cdots & c_{in} \end{bmatrix} \) (40.4)

The cable force increment should satisfy the following equation to maximize the lifting line in the stress-free state.

\( [C]^* \begin{bmatrix} t_1 \\ t_2 \\ \vdots \\ t_n \end{bmatrix} = \{Z_i^1\} - \{Z_i^2\} \) (40.5)

When construction control is used to control displacement values in the feasible domain, Z should satisfy:

\( \{\lambda_i^1\} \le \{Z_i^1\} - \{Z_i^2\} \le \{\lambda_i^2\} \) (40.6)

where \(\lambda_i^1\) is the lower limit of the feasible domain of displacement values, \(\lambda_i^2\) is the upper limit of the feasible domain of displacement values, and the influence matrix under the current displacement values is obtained using the above equation, followed by the cable force increment under the current displacement of all nodes.

During the cable adjustment process, the difference between the displacement of the control point and the theoretically required displacement should be made to satisfy Eq. (40.7).

\( \min f = \sum_{i=1}^n (z_i^1 - z_i^2)^2 \) (40.7)

Using point cloud data analysis, the line deviation determines the displacement increment for buckling. Buckles interact at each stage in the system. Ensuring stiffness and stability, on-site cable adjustments require calculating cable force increment with finite element modeling for the current construction stage.
