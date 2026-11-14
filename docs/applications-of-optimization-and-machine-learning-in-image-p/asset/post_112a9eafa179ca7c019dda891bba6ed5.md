
## 9.3 MACHINE LEARNING: EXPANDING HORIZONS

The field of computer science with the fastest growth right now is machine learning, which has applications in fields as varied as marketing, healthcare, production, cybersecurity and mobility. Three elements are readily available and combined: (1) faster and more potent part of a computer, like multiple cores and broad-sense GPU; (2) a computer program that utilizes these computational structures; and (3) essentially unlimited training data sets for a certain issue, like digital photos, digitalized files. Posts on social media or even other types of information are the primary cause of this literal “explosion” of the technique. ML is a type of AI that is capable of carrying out tasks without being particularly trained to do so. Instead, it employs a process known as “training to learn” from prior samples of the assigned task. Inference is the technique through which the task can be carried out on fresh data after training [22]. It is notably helpful for instances where the data is challenging to analyze, such as reviewing image and video recordings, and it especially helps in getting data from enormous amounts of continuously increasing data [23]. Computer vision is the science of analyzing and drawing conclusions from digital images and movies. It aims to automate tasks from an engineering standpoint that the human visual interface can do [24]. The two stages of a computer-vision-based machine learning process are feature extraction and classification.

### 9.3.1 Various Steps in Machine Learning Models

Data gathering using cameras/mobile phones/smartphones is the first step in the framework for the creation of the ML-based picture identification model, as illustrated in Figure 9.2. To construct an online image database, collected appropriate photographs can be uploaded to a server. The image is further processed in order to make it suitable for applying a machine learning model. Various extraction techniques can be used to extract various characters in the context of color, shape and size. Following the use of feature extraction techniques, the dimensionality reduction technique is further used to optimize the results. Additional machine learning models, including ANN, CNN, RNN and others, can be applied for system training and optimization. Each of these actions with specific response to herbal drugs is thoroughly explained in the next section.

## 9.4 CREATION OF IMAGE DATABASE

The easiest way to accomplish this is using a mobile phone equipped with a camera that has at least 10 megapixels. Additionally, since cameras have superior

![](img/9c1422d4c6a10143e1802787075307de_147_0.png)

FIGURE 9.2 Basic representation of artificial neural network.

sensors and pixels than cellphones, they can also be employed. The background should be white or clear when clicking an image because pictures taken against a busy background may produce unneeded noise that affects our machine learning algorithm and ultimately produces inaccurate results. Herbs and spices can be photographed and posted to online image databases that can be accessed from anywhere, like Google Drive, Microsoft Community, and other sources. Based on the quality of the camera used to capture the photographs of the herbal/spices entity, the image dataset can be submitted in the form of a Zip file that is clearly classified into categories such as normal, high-end, and moderate [25]. Clear categories for each sort of image should be present in the database.

According to Walch and Mäder, the photos in the Swedish Leaf, ICL, Leafsnap and Flavia databases were taken in a controlled environment. However, the number of images and the species utilized vary depending on the database. On the other hand, the ImageCLEF database provides a wide range of leaf pictures for leaf recognition in a natural context [7].

Using a k-NN classifier, Mzoughi and coworkers detected leaf photos in ImageCLEF 2011, which contained 5436 images from 71 varieties of plants. Due to the roughly comparable leaf shapes of each plant species in the dataset, the classification of this dataset is exceedingly difficult. Despite the similarities in the photos, the researchers were nevertheless able to classify the leaves with an accuracy of 82.1% by using various attributes on various leaf types [26, 27].

For leaf images from ImageCLEF, Pyramid histograms of oriented gradients, top-hat transformation and Haar wavelet transform, according to Ma and coworkers, produced a classification accuracy of 90%. The top-hat transformation was used to eliminate small items from a noisy backdrop, and PHOG is a common shape descriptor that defines the image by the local form and spatial configuration of the shape. Table 9.1 represents a list of the online server databases available [28].

## TABLE 9.1 List of Online Server Databases

| S no. | Database Name | Outcomes and Features | References/Website Link |
|---|---|---|---|
| 1 | ImageCLEF11/Image-CLEF12/ImageCLEF13 | Following are the total numbers of species and photos in each database: The 5436 photos in ImageCLEF11 represent 71 species; 11,572 images from 126 species make up Image-CLEF12; 26,077 images from 250 species make up Image-CLEF13. | [29–32] |
| 2 | PlantCLEF14, PlantCLEF15, PlantCLEF16, Plant-CLEF17 | 60,961 images from 500 species make up Plant-CLEF14; 113,205 images from 1000 species make up Plant-CLEF15; 121,205 images from 1000 species make up Plant-CLEF16; and 256,287 images from 10,000 species make up Plant-CLEF17. | [29–32] |
| 3 | Flavia | This collection includes 1907 photos of 33 different plant species that are well aligned, noise-free, and have minimal to no differences in brightness and color. | [33] |
| 4 | ICL | Images of leaves that were entirely cultivated in China are included in the dataset. There are 220 plant species represented by 16,851 photos in total. | [34–36] |
| 5 | Leafsnap | The 30,866 leaf photos in this dataset, which are all from the northeastern United States, represent 185 different species. Only 23,147 of the photos from the Smithsonian Collection are of a good caliber. The remaining pictures were taken with cellphones in a wide range of situations and conditions. | [30, 37, 38] |
| 6 | VITHERB | Images about the Vietnamese plant species | http://viherb.com.vn/ |
| 7 | plant_leaves | Images of healthy plants' leaves | https://data.mendeley.com/datasets/hb74ynkjcn/1 |
| 8 | American Botanical Council | Herbal plant information catalogue | http://www.herbalgram.org/ |
| 9 | ImageCLEF 2013 | Plant image database | https://www.imageclef.org/2013/plant |
| 10 | CIFAR-10 | Plant and other articles image database | https://www.cs.toronto.edu/~kriz/cifar.html |
| 11 | Plant CV | Images of different species of plants | https://www.quantitative-plant.org/dataset |
| 12 | PlantVillage dataset | A set of images and labeled for diseased plant leaves | https://www.kaggle.com/datasets/emmarex/plantdisease |
| 13 | Pl@ntNet-300K | Datasets of different species of plants | https://zenodo.org/record/4726653#.YmowC_NBxQI |
| 14 | Database of leaf images | Datasets of different image of plants | https://data.mendeley.com/datasets/hb74ynkjcn/4 |
| 15 | DiaMOS Plant | Database for identifying and tracking plant disease | https://francescamalloci.com/category/projects/ |

## 9.5 FEATURE EXTRACTION

However, rather than starting with human prior knowledge, the essential step in conceptually understanding a software program is to extract useful and effective visual characteristics and build models from them. The majority of picture identification and retrieval systems are based on color, texture and shape because they are the most common visual features. But how well they function is heavily dependent on how they use picture attributes. The three different types of feature extraction methodologies are region-based, global and block-based features [39].

### 9.5.1 Color Features

Among the most significant aspects of captured image is color. Particular color properties are described in the context of a particular RGB space or model. Color spaces like RGB, HIS, LUV and HSV have been used in literature. Color features can be retrieved from images or regions of interest once the color space has been defined. Color histogram, color coherence vector (CCV), color correlogram and color moments (CM) are just a few of the major color features present in color images [40].

### 9.5.1.1 Color Histogram

A color histogram is a graphical description of the color distribution of a picture. A histogram’s data is derived by recording the appearance of each conceivable color of the respective color model appearing in the image [40].

### 9.5.1.2 Color Coherence Vector

The color coherence vector (CCV) approach is more complicated than the color histogram method. It works by determining whether each pixel is coherent or incoherent. In contrast to an incoherent pixel, which is a member of a tiny connected component, a coherent pixel is a component of a big connected component (CC). Establishing the criteria by which we determine whether a connected component is large is a critical step in making this strategy function [40].

### 9.5.1.3 Color Moments

Color moments are measures that help separate photos based on their many color characteristics. The color moments provide a measurement for color similarity between photos once they’ve been calculated. For applications like image retrieval, these similarity values can be compared to the frequencies
