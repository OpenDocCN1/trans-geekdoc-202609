
Another challenge was variations in the shape of surrounding structures of any human organ. Lesion and tumor detection means the detection and segmentation of lesions. This task was essential for cancer staging and assessment of the response to treatment in patients with cancer. The shape and size of the lesions, as well as blurred margins, pose several difficulties. Vessel segmentation aims at delineation and extraction of the vessels in medical imaging techniques employing CT and MRI angiography. Successful vessel segmentation was crucial for the identification of vascular pathology and planning interventions; nevertheless, in addition to being tortuous, thin blood vessels are relatively indistinct from other tissues and artifacts. Finally, functional region segmentation was used to segment regions of interest, including active brain regions during cognitive tasks that demonstrate metabolic activity. This task was important in fMRI and PET; variability in functional activity and its relationship with anatomy makes segmentation difficult.

### 2.4.1 Challenges in segmentation

Several factors affect medical image segmentation. Some of the problems highlighted include variability in imaging modalities. A variety of imaging techniques, such as MRI, computerized axial tomography, and ultrasound, generate images with dissimilar resolutions, contrast levels, and distortions. Such intra-observer variability has highlighted the need to adopt modality-specific, previously used segmentation techniques to obtain accurate segmentation across different imaging modalities. Other factors that are also somewhat challenging include image quality and artifacts, which occur in the acquired images. There are many factors that have a negative impact on the segmentation process, including noise, blurring, and artifacts that are common in medical images and obscure the boundaries. Such imperfections require that the techniques employed should also be strong enough to work with these deficits and give accurate results. There was patient variability: each patient was unique in some ways, such as organ size and organ shape, which means that segmentation could also be affected. These variations must then be reflected in the models to ensure that the targets fit all categories of patients. Another drawback was class imbalance, particularly in rare lesions. This was because, on average, biased models that perform well on the most frequently seen classes but poorly on the least frequently seen classes are developed due to the fact that few, if any, annotated examples of such classes are available for training the model. Lastly, computational complexity was an issue because advanced segmentation methods, especially those using DL algorithms, require a long time and substantial computation. Current technological advances in medical imaging data, especially in large-scale data, necessitate efficient algorithms and resource management strategies.

are providing increased accuracy of diagnostic and therapeutic strategies and opening the door to accurate individualized treatment.

These current trends and innovations are at the forefront of human medical image segmentation, thereby showing the high rate of development in the field and how it can revolutionize clinical practice by improving accuracy, efficiency, and flexibility.

## 3 Traditional segmentation techniques

### 3.1 Thresholding methods

Fixed-level thresholding and Otsu’s method belong to the simplest types of image segmentation methods, which are applied mostly to simple bi-level segmentation. These approaches involve dividing an image into different zones using pixel intensity values and hence are well-suited for basic and well-defined segmentation problems.

There are basically four main principles that are followed while selecting a threshold.

By fixing the intensity value at a certain threshold level, it becomes possible to distinguish between the background and foreground of an image. Foreground pixels are defined as those having intensity values greater than the threshold “T,” while background pixels have values less than “T.” This technique is particularly effective when there is a clear intensity contrast between regions of interest and the background. Figure 4 illustrates this threshold-based segmentation approach, highlighting how it separates anatomical structures based on pixel intensity. Due to its simplicity and low computational demands, this method is especially well-suited for applications with constrained processing resources.

![](img/18722240e44c225d7ff2f58a10eecb4a_72_0.png)

**Figure 4:** Thresholding methods.

Despite these shortcomings, thresholding was a fundamental step in image segmentation and was useful as a basis for more sophisticated approaches in applications that require simplicity and speed.

### 3.2 Region-based methods

Region-based approaches are also one of the main types of conventional image segmentation techniques, which partition an image based on certain criteria for pixel values and spatial relations within the picture. These techniques are based on the assumption that some attributes, such as differences in intensity and texture, have to be used to determine regions within a picture.

#### 3.2.1 Area development

One of the simplest techniques used in segmentation was called region growing; this procedure begins by segmenting several seed points from images. These seed points are then enlarged multiple times by the algorithm into neighboring pixels that meet several criteria, such as texture. When the entire image was separated into sections that met the criteria, this process was continued. Region growing was particularly effective for partitioning regions that shared similar properties, but most of the time, it was unable to handle clusters that displayed a lot of variation.

#### 3.2.2 Region merging

From this, we see that region merging techniques work on principles obtained from segmentation, where adjacent regions are combined based on resemblance. Originally, the image was partitioned into an overpartitioned map of small segments that were gradually merged using features like intensity, texture, and statistical measures. During the merging process, segmentation improved and resulted in much larger and more complete areas. Although region merging was useful in grouping small segments into sensible structures, its applicability heavily depends on the initial segmentation and requires proper tuning of merging criteria in many cases.

#### 3.2.3 Watershed segmentation

Watershed segmentation is a powerful technique that operates on the image as a topographical map; pixel intensity describes the altitude. This surface is then gradually filled by the algorithm, imitating a flood and acting from seeds at the local minima as object boundaries. For some time, it unites areas according to the catchment areas caused by the water levels as the “flood” begins to progress. Watershed segmentation can be useful for partitioning the data set in a way that captures structure and boundaries, but there are issues with oversplitting of the image, which means that subsequent processing was usually needed to clean up the final segmentation.

#### 3.2.4 Region splitting and merging

Region splitting and merging is a strategy that begins with the whole image as a single region, splitting it into smaller regions based on a homogeneity criterion. After the initial splitting, the algorithm fuses neighboring regions if two areas meet the homogeneity criteria. This approach lies right in the middle between the extreme of very fine subdivisions of the region and the cohesiveness of each segment. The effectiveness of the method depends on the split-and-merge criteria that are applied, which must be sensitive enough to avoid excessive splitting and merging.

#### 3.2.5 Active contours (snakes)

Snake contours are a technique in which an energy-minimization curve is used to outline object boundaries. The algorithm actively updates a contour using energy functions that include internal energy attributed to the continuity of the contour and external energy associated with image gradients. It continuously adjusts the contour according to the object’s shape and size, which is advantageous because segmentation can be complex in some images. Active contours are particularly suitable for the segmentation of objects with clear boundaries, yet they require initial placement of the contour and tuning of the parameters to achieve the best outcome.

These region-based methods are the basis of many of the more conventional image segmentation techniques and provide useful tools with which images can be partitioned on the basis of spatial and intensity properties. Both methods have some advantages and disadvantages, and the efficiency of their application varies according to the features of the images and the intended application.

### 3.3 Edge detection techniques

Basic approaches such as edge detection are computational strategies in medical images that identify boundaries of objects within images. These techniques are very useful in segmenting areas of interest by emphasizing the changes between different types of tissue and pathological zones. In medical image segmentation, edge detection
