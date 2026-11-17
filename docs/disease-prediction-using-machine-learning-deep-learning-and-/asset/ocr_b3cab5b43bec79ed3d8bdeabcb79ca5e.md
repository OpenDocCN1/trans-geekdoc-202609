extract the contours of the femur from the planer radiograph. In the second step, they perform the coordinating process on the extracted contours. In the last step, they reconstruct the 3-D geometry.

P. Gamage et al. proposed a technique for the 3-D remaking of the patient-specific bone model from 2-D radiographs [15]. They extracted the edge points from 2-D X-ray images to determine the boundary of the femur. Now, they applied for a non-rigid registration between the edges recognized in the radiograph. They projected the contour point of the genetic model. Now, the translational field distinguishes the deformation required by the 3-D anatomical model in the anterior and lateral viewpoint. In the last step, an entire 3-D translational field is developed through a thin plate spline (TSP) based on insertion and the 3-D generic anatomical data. The TSP technique does not include surface patches in their calculation which gives robust results. On the other hand, if the data size is too large then it leads to the issue of edge points.

Tristan Whitmarsh et al. [16], purposed the reconstruction model for the 3-D shape of the proximal femur from a single DXA. This technique uses a statistical model applied to a large data set of Quantitative Computerized Tomography (QCT) scans.

# Table 2. Performance comparison of 3-D reconstruction models on different image types.

| Image Used | Average Error | Root Mean Square Error (RMS) | Number of Projections |
| :--- | :--- | :--- | :--- |
| Single DXA image [10] | 1.1mm | 2.6mm | 1 |
| X-ray image [17] | 1.2mm | 2.8mm | 2 |
| Two DXA image [28] | 0.8mm | 2.1mm | 2 |

Guoyan Zheng et al. proposed the Partial Least Square Regression (PLSR) model for the 3-D reconstruction of volumetric intensity from 2-D X-ray images [20]. In this technique, the authors used Independent Statistical Shape and Displacement and Appearance (DA) approach. The PLSR technique can easily handle the multi-collinearity between the independent points at the time of 3-D reconstruction. On the other side, PLSR needs a large number of data for training.

Moon Kyu Lee et al. created a 3-D model for a finished femoral bone [21]. The authors used a regular X-ray image and combined the anatomical parameters such as neck length, femoral length, head offset length, the anatomical axis, and sagittal radius into a referential 3-D shape. They calculated the internal position and range of the femoral head by nonliearing regression. They determined the center point of the anatomical axis by applying the elliptical regression.