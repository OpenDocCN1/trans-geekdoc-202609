
the first stage, they used the projection display to discover an angle between two X-ray images of a femur. At the next stage, the system marks the boundary of the femur using active contours. In the third stage, the system finds the coordinating point between 2-D shapes using the Euclidean distance. In the next stage, the system produces a 3-D point cloud. Now, it applies the Iterative Closest Point (ICP) algorithm for 3-D rigid registration. In the last stage, the system applies a meshing technique to find the 3-D shape of the proximal femur. The ICP algorithm is straightforward and simple to implement but it calculates the starting value of the iteration in the first step which should be correctly initialized otherwise this algorithm suffers from the local optimum problem.

Sami P. Vaananen et al. [12] proposed a programmed technique for the reconstruction of the 3-D shape. They applied Structured Auxiliary Mesh (SAM) algorithm for this purpose as shown in Fig. (4). The authors used three sets of bone images. The two sets of bone images were used for training the model and the remaining third set of bone images was used as a testing dataset of the model.

![](img/0616422b380b1bd62613a261ed51be87_39_0.png)

Fig. (4). Development of SAM model.

N. Baka et al. [13] proposed the Statistical Shape Model (SSM) based technique for the posture estimation and shape reconstruction of a 3-D bone surface using two X-ray images. The SSM technique capture the global shape of the surface without reducing the size of the object therefore SSM technique acquire high space.

P.E. Garibarov et al. proposed the patients' specific proximal femur surface reconstruction model [14]. They applied their model to the planar radiographs. The model completes the reconstruction in three steps. In the first step, they extract the contours of the femur from the planar radiograph. In the second step, they perform the coordinating process on the extracted contours. In the last step, they reconstruct the 3-D geometry.

P. Gamage et al. proposed a technique for the 3-D reconstruction of the patient-specific bone model from 2-D radiographs [15]. They extracted the edge points from 2-D X-ray images to determine the boundary of the femur. Now, they applied a non-rigid registration between the edges recognized in the radiograph. They projected the contour point of the generic model. Now, the translational field distinguishes the deformation required by the 3-D anatomical model in the anterior and lateral viewpoint. In the last step, an entire 3-D translational field is developed through a thin plate spline (TPS) based on insertion and the 3-D generic anatomical data. The TPS technique does not include surface patches in their calculation which gives robust results. On the other hand, if the data size is too large then it leads to the issue of edge points.

Tristan Whitmarsh et al. [16] proposed the reconstruction model for the 3-D shape of the proximal femur from a single DXA. This technique uses a statistical model applied to a large data set of Quantitative Computerized Tomography (QCT) scans.

### Table 2. Performance comparison of 3-D reconstruction models on different image types.

| Image Used | Average Error | Root Mean Square Error (RMS) | Number of Projections |
| :--- | :--- | :--- | :--- |
| Single DXA image [10] | 1.1mm | 2.6mm | 1 |
| X-ray image [17] | 1.2mm | 2.8mm | 2 |
| Two DXA image [28] | 0.8mm | 2.1mm | 2 |

Guoyan Zheng et al. proposed the Partial Least Square Regression (PLSR) model for the 3-D reconstruction of volumetric intensity from 2-D X-ray images [20]. In this technique, the authors used Independent Statistical Shape and Displacement and Appearance (DA) approach. The PLSR technique can easily handle the multi-collinearity between the independent points at the time of 3-D reconstruction. On the other side, PLSR needs a large number of data for training.

Moon Kyu Lee et al. created a 3-D model for a finished femoral bone [21]. The authors used a regular X-ray image and combined the anatomical parameters such as neck length, femoral length, head offset length, the anatomical axis, and sagittal radius into a referential 3-D shape. They calculated the internal position and range of the femoral head by nonlinear regression. They determined the center point of the anatomical axis by applying the elliptical regression.

Haithem Boussaid et al. [22] proposed a model for the 3-D reconstruction of the proximal femur using low-dose biplanar X-ray images.

S. Laporte et al. worked on the 3-D reconstruction model by detecting the contours from bi-planar radiographs [23]. They employed Direct Linear Transformation (DLT) and Non-Stereoradiography Corresponding Points algorithm (NSCP) for the reproduction of the structure. NSCP fails in the structures such as the knee joint. Therefore, the authors applied Non-Stereo Corresponding Contours (NSCC) algorithm for recreating the 3-D shape of the bone.

Ryo Kurazume et al. proposed a technique for the 3-D reconstruction of a femoral shape using a parametric approach [24]. They performed the statistical analysis of 3-D femoral shape obtained from CT scan images of 56 patients. They employed the manual segmentation and marching cubes algorithm, Principal Component Analysis (PCA) [25].

S. Kolta et al. [26] proposed the model for the 3-D reconstruction of the proximal femur bone from the DXA image. The model works by detecting the contours in the images.

V.H. Kim et al. used the Simulated Implantation System (SIS) [27] for 3-D perception and numeric investigations between the artificial hip joint and the femur [28, 29]. The Architecture of 3-D Reconstruction Simulation Systems is shown in Fig. (5).

![](img/0616422b380b1bd62613a261ed51be87_41_0.png)

Fig. (5). Architecture of 3-D reconstruction simulation systems.

Vikas Karade et al. [30] proposed a Laplacian Surface Deformation (LSD) based technique for 3-D femur reconstruction from bi-planar X-ray images.

Moritz Ehlke et al. introduced a GPU-based method to deal with render virtual X-ray projections of deformable tetrahedral networks for 3-D geometry reconstruction from X-ray [31].

Guoyan Zheng et al. introduced a 2-D to 3-D correspondence building technique by point matching procedure in the non-rigid 2-D structures [17]. They employed the adapted iterative closest point (ICP) algorithm [32] at the first stage and statistical instantiation at the second phase. The authors applied the regularized shape deformation at the third stage [33].

The above discussion shows that many researchers proposed the techniques for the reconstruction of 3-D medical images [1-9]. These techniques focus on the reconstruction of the femur bone. The above-stated techniques are based on numerical morphology strategy for boundary detection [1], DLT [8], 3-D stereo radiographic reconstruction [9], B spline FFD [10], SSM [7], contour detection [8], and edge detection [9] for the reconstruction of 3-D view of femur bone from the 2-D images. These techniques report low accuracy due to the ineffectiveness in detecting the edges or boundaries. The performance comparison of the most effective techniques is given in Table 3.

### Table 3. Comparative analysis of methods of 3-D reconstruction.

| S.No | Author | Method | Shape | Input | Contour Generations | Number of Cases | Mean P2S Error | RMS P2S Error | Computation Time (S) | System Configuration |
|---|---|---|---|---|---|---|---|---|---|---|
| 1 | Karade et al. [30] | LSD-SOM | Distal femur | Real | Manual | 5 | 1.2 | 1.4 | 52 | Intel 2.4 GHz, 8GB |
| 2 | Karade et al. [30] | LSD-SOM | Distal femur | Simulated | Automatic | 22 | 1.2 | 1.5 | 46 | Intel 2.4 GHz, 8GB |
| 3 | Filippi et al. [34] | FFD | Full Femur | Simulated | Manual | 5 | 1.4 | - | - | - |
| 4 | Gunay et al. [35] | FFD | Tibia | Real | - | - | - | - | 100 | AMD, 1GHz |
| 5 | Baka et al. [13] | SSM | Distal Femur | Real | Automatic (canny) | 10 | - | 1.68 | 300 | 2.4 GHz, 2GB |
| 6 | Zhu et al. [36] | SSM | Distal Femur | Real | Manual | 10 | 0.9 | - | 178 | Intel 2.67 GHz, 9GB |
| 7 | Fleute et al. [37] | SSM | Distal Femur | Simulated | Automatic | - | - | 1.0 | 60 | - |
| 8 | Gamage et al. [38] | TPS | Full femur | Real | Automatic | 6 | 0.9 | - | - | - |
| 9 | Laporte et al. [39] | NSCC | Distal femur | Real | Semi-automatic | 8 | - | 1.4 | - | - |
| 10 | Tang et al. [40] | Hybrid atlas | Distal Femur | Simulated | Automatic | 2 | 2.0 | - | - | - |
| 11 | Le Bras et al. [9] | NSCC | Proximal Femur | Real | Manual | 28 | 2.0 | - | - | - |
