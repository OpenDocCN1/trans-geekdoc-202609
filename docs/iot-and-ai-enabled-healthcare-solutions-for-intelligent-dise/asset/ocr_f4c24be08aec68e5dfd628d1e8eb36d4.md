![](bbox=[0.185, 0.11, 0.815, 0.475])

Fig. 7. Flowchart of the prediction process.

# 3.1 Dataset Description

By preprocessing the photos, the data can be converted into a common classified format. The images were initially converted to grayscale in step one, maintaining a pixel resolution of 224 × 224. Secondly, Gaussian blur was added to the images to reduce noise and enhance the final product's quality. These images were then sharpened and more detailed information was extracted by applying high pass filter details. The process through which an object's borders drop pixels is called erosion. The volume decreased as the white areas' tumors, for example were eroded, but the gaps, particularly the holes in the white area, grew larger. Dilation adds pixels to the borders of structures in the opposite way to erosion. The extra white pixels on the margins caused the white areas to enlarge after dilation. In the meantime, the spaces in the white areas were filled in. The black areas of each image were eliminated in the final stage. Based on the existence of dark patches, contours were identified for these procedures from the left, right, bottom, and upward directions.

# 3.2 Data Augmentation

The quality, quantity, and relevance of training data dictate the efficacy of the majority of machine learning and deep learning models. Lack of data, however, is one of the most common issues with implementing machine learning in businesses.