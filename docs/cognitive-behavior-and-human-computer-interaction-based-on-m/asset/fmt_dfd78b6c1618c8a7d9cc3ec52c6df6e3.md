
In the proposed method, picture description language is used for feature extraction. For tracing the whole image, a 3 x 3 x 3 size voxel is used, as shown in [Figure 6.4](#c06.xhtml#fig6-4). The entire face image is traced pixel by pixel, which starts from (1, 1, 1) position and continues in the same direction until the algorithm will not find the first pixel with intensity value one and this first pixel with intensity 1 represents the first component of the face. The proposed methodology can find the entire neighborhood pixel in the preferred direction. According to the syntactic pattern recognition technique, in a 2D image, there are nine possible directions where a neighborhood pixel could be present. Similarly, in 3D images, there are 26 possible directions where a neighborhood pixel could be present in all possible planes. The image’s tracing will continue until it does not find all the image’s possible neighborhood pixels. The same approach will continue for all the possible planes of the 3D image (Central, front, rear). When all the components are traced, they will finally get the knowledge information representing the image. This knowledge vector contains the image’s feature and consists of the depth information of the face image, which makes this algorithm novel and unique.

![Figure 6.3 3D wireframe concerning central cell 14.](images/fig6_3.jpg)

**[Figure 6.3](#c06.xhtml#fig6_3)** 3D wireframe concerning central cell 14.

![Table 6.2 Sample of possible convex polyhedrons.](images/tab6_2a.jpg)

**[Table 6.2](#c06.xhtml#tab6_2)** Sample of possible convex polyhedrons.

![Figure 6.4 (a) 3 x 3 x 3 size of voxels array. (b) Smallest possible three-dimensional convex polyhedron.](images/fig6_4.jpg)

**[Figure 6.4](#c06.xhtml#fig6_4)** (a) 3 x 3 x 3 size of voxels array. (b) Smallest possible three-dimensional convex polyhedron.

### 6.3.2.3 Dense Feature Extraction

In this step, SIFT (scale-invariant feature transform) algorithm is applied to get a more distinctive feature from the image. These unique features are helpful in the reconstruction of the 3D face model. The first difference of Gaussian is applied to identify the region of interest and it is invariant to the scale and orientation of the image. In the next step, key points are localized and this is helpful to determine the scale and location of every candidate location. Now, each key point will be assigned to the local image gradient direction. Finally, the gradients of the local image are measured around the key issues.

The benefit of applying SIFT is that it produces the dense feature of the image and the syntactic pattern recognition approach can produce each feature in detail and it also gives the depth inform details of the image, which helps reconstruct the 3D image. Calculating the depth information is necessary to understand the 3D geometry and syntactic pattern recognition makes it easy.

### 6.3.3 Enhanced Features

In this step, the extracted features using the step mentioned above will be enhanced using the shape and shading technique. The depth of the image, which is calculated using the syntactic approach, will be added to the image, making the image three dimensions. The image can be translated and rotated according to the requirement by adding depth information to the image.

### 6.3.4 Creation of 3D Model

In this step, we need to align the data with the 3DMM model. In the above step, we retrieved the features from two different methods, and now, these features should be integrated and aligned with the 3DMM model. In this step, a Basel face model is used, which is publically available, and it consists of 100 male and 100 female 3D scans. Now, we need to make a point-to-point correspondence with the Basel face model. The features should be mapped with the face model and sum of the square difference of pixels should be minimum to fit the model. It can be calculated as follows:

(6.1)![img](images/eq6_1.jpg)

This equation is helpful to align the input image on a 3D face model.

## 6.4 Datasets and Experiment Setup

The proposed algorithm is evaluated on the Face Warehouse database \[32\], USF dataset, \[37\] and our dataset. The Face Warehouse dataset contains 150 different subjects with 20 other expressions. Images of varying age groups of people with different facial expressions have been selected to examine the algorithm’s performance. USF dataset contains 77 faces that are combination of male and female faces of different ages and races. These face model consists of depth information and texture of real faces. These models have lightning effects which could introduce error in the reconstruction. The proposed methodology is implemented on python using the Anaconda tool. The specification of the system is windows operating system, GPU processor, and 32 GB RAM.

## 6.5 Results

In the proposed methodology, we evaluated the expression reconstruction results on the Face Warehouse dataset \[32\]. We applied a rigid transformation to compute the vertex correspondence between the Face Warehouse dataset and the proposed methodology results. This rigid transformation aligns the predicted results and the ground truth results provided by the Face Warehouse dataset. Root mean square error between the corresponding vertices is calculated to compute the performance of the proposed methodology. [Table 6.3](#c06.xhtml#tab6-3) represents the mean and standard deviation of the point-to-point root mean square error on the Face Warehouse dataset. The comparative analysis is done with MoFA \[33\] and 3DMM \[34\], and it is represented in [Figure 6.5](#c06.xhtml#fig6-5). The proposed methodology is also applied on the wireframe of the image, where wireframe model of the image is given as an input and then algorithm can reconstruct the image’s wireframe model image. The results of the proposed method are more accurate compared to the existing state of art methods. According to the result analysis, the proposed methodology can generate more identity-specific results. If some unknown expression appears in the image, then MoFA \[33\] cannot produce accurate results (shown in row 2 [Figure 6.5](#c06.xhtml#fig6-5)).

[Figure 6.6](#c06.xhtml#fig6-6) shows the comparative analysis of error maps for 3D detailed reconstruction with state-of-the-art methods and the result shows that the results of the proposed methodology are more robust than the Sela 17 \[35\] and Tran18 \[36\].

**[Table 6.3](#c06.xhtml#tab6_3)** Comparative analysis of mean and standard deviation of point to point RMSE on face warehouse dataset.

| **Sr. no.** || **Method** || **Error** |

| --- | --- | --- |

| 1 || MoFA \[33\] || 2.26±0.58 |

| --- | --- | --- |

| 2 || 3DMM \[34\] || 1.81±0.43 |

| --- | --- | --- |

| 3 || Proposed || 1.69±0.20 |

![Figure 6.5 Comparative analysis of proposed algorithm with existing technique on face warehouse dataset.](images/fig6_5b.jpg)

**[Figure 6.5](#c06.xhtml#fig6_5)** Comparative analysis of proposed algorithm with existing technique on face warehouse dataset.

![Figure 6.6 Comparative analysis of error maps for 3D detailed reconstruction. The numbers under error image represents the mean and standard deviation of these differences in percentage.](images/fig6_6.jpg)

**[Figure 6.6](#c06.xhtml#fig6_6)** Comparative analysis of error maps for 3D detailed reconstruction. The numbers under error image represents the mean and standard deviation of these differences in percentage.

## 6.6 Conclusion
