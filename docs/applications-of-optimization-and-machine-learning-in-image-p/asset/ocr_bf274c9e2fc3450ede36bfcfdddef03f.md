# ## 9.5.3 Texture Features

A variety of images can make use of the varied characterization of texture. Human visual systems are hypothesized to use texture for interpretation and detection. Normally, color is a pixel attribute, while texture can only be determined from a group of pixels. Several methods have been investigated to extract texture features. According to the domain in which the feature extraction is taken, they can be categorized into two groups: methods for extracting spatial texture features and spectral texture features [42].

# ## 9.5.3.1 Spatial Method

By calculating pixel statistics or identifying local pixel patterns in the source image domain, texture characteristics are retrieved using this method.

# ## 9.5.3.2 Spectral Method

Texture features can be identified by converting an image into frequency domain, and then the features are calculated from the transformed image. Some advantages and disadvantages are included in Table 9.3.

Lin and coworkers suggested a visual consistency-dependent method for feature extraction to identify particular features, like aspect ratio, rectangularity, vertical eccentricity, shape complexity, and horizontal structure, to define leaf lamina. The authors also used the inertia axis method to spin leaves, which must be done in a specific orientation. This is done to mimic how people typically observe objects. The results demonstrated that characteristics of the same plant exhibit excellent consistency with negligible variation in laminae, while aspect ratio, vertical eccentricity and form complexity exhibit the greatest variation in the laminae of different plants [43]. Patil and Manza collected geometric information from photographs,

TABLE 9.3 Advantages and Disadvantages of Spatial and Spectral Texture Feature Extraction

| Method | Advantages | Disadvantages |
|---|---|---|
| **Spatial method** | Relevant, simple to interpret and can be retrieved without losing information from any shape | The frequency domain is prone to noise and distortions, and the feature is calculated from the altered image. |
| **Spectral method** | Dependable, with fewer computations required | There is no semantic meaning; hence, square image portions of adequate size are required. |