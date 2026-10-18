# Data Acquisition

The following data is captured in the year 2023 in Chengalpattu district of the state Tamil Nadu, India (12°40'54.8"N 79°59'19.7"E). The boundaries of the field area are identified and then extracted the shape files. A DJI Mini2 drone is used to capture the field images. The video capture duration has an interval of 20 minutes between each flightt to capture the field. The data captured through UAV drones in the field and the data set consists of 10,000 images. The image resolution is of 18000 by 15000 pixels. The field consists of Papaya, Mango and Guava trees as depicted in Fig. 7. The field image is annotated and pre-processed and can be used as inputs to perform crop yield estimation using the Normalized Difference Vegetation Index.

![](bbox=[0.115, 0.425, 0.845, 0.545])

Fig. 7. DJI Mini2 drone field images.

# Calculation of Vegetation Index

Initially, a combination of visible and near-infrared wavelengths was used to calculate various ratios and normalized indices as depicted in Equation 1.1. NDVI values span from +1 (strongest vegetative growth) to −1 (typically water). The NR (λ = 700 – 1300 nm) and VS (λ = 550 – 700 nm). The optical properties of the cellular structure and air-cell wall of leaf tissues determine their reflectance levels. Air cell wall contacts between the chloroplasts and the protoplasm.

NDVI = (NR − VS) / (NR + VS) (1.1)

whereas,

+   - NDVI stands for Normalized Difference Vegetation Index
+   - NR - Near Infrared Radiation
+   - VS -Visible Red Spectrum

This formula states that the difference in the red and infrared range’s reflected light intensities divided by the sum of these intensities equals the density of vegetation (NDVI) at a specific place in the image.

# Results and Discussions

The comparison results as depicted in Table 1 and Fig. 8 reveal that the Normalized Difference Vegetation Index provides higher accuracy in estimating crop health compared to other existing models.