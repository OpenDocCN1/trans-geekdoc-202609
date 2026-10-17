
![Image 1174](index-268_1.png)

![Image 1175](index-268_2.png)

![Image 1176](index-268_3.png)

![Image 1177](index-268_4.png)

Deep Learning Algorithms

242

For the classical features, the classification accuracy is also computed using an SVM classifier, however, with the original images (without resizing) trained using the leave-one-patient-out cross-validation strategy assuring that there are no images from patients of the validation set in the training set as in \[55\] to make sure the classifier generalizes to unseen patients.

This cross-validation is applied to the classical feature extraction methods from the literature as well as to the full training and off-the-shelf CNNs features. The accuracy measure is used to allow an easy comparability of results due to the high number of methods and databases to be compared.

**RESULTS AND DISCUSSION**

**CNNs Trained from Scratch**

In the first experiment for the CNN full training, we first use the configuration similar to \[20\] that can be seen in Table 2 and it can be concluded that the accuracy result was not satisfactory (79%).

This can be explained by the fact that Neural Networks involving a large number of inputs require a great amount of computation in training,

\* \` #

size of our dataset).

**Table 2**\# ! »»

respective accuracy in %

For the second experiment, the hyperparameters presented in Table 3 were selected based on the works \[48, 56\] and empirical adjustment

! #

well as the number of units in the fully connected layer were made and are also shown in Table 3. It can be seen that the architecture CNN-05 obtained the best results, therefore, chosen to perform the subsequent tests.

本书版权归Arcler所有

![Image 1178](index-269_1.png)

![Image 1179](index-269_2.png)

![Image 1180](index-269_3.png)

![Image 1181](index-269_4.png)

![Image 1182](index-269_5.png)

Exploring Deep Learning and Transfer Learning for Colonic Polyp ...

243

**Table 3** !

{»{»Á

' +

CNN for each patient from the database (leave-one-patient-out (LOPO)

+|

Table 4 are the mean values of the validation set from 62 different CNNs, one for each patient, implemented using the MatConvNet framework \[50\].

»' # #"

{»{' # \` |

of this approach is the opportunity to have a set of decisions available to

\*

subimages can increase the system accuracy likewise to give the assurance of certainty for the overall decision.

**Table 4**. Accuracy of different strides for overlapping subimages in the CNN-05 evaluation for i-Scan1 database in %

\# <# { '

'# {»{# # !{

subimages for each image, resulting in an accuracy of 89.00%. This evaluation is very computationally expensive to perform, so we decided to evaluate with different strides resulting in different number of subimages as it is shown in Table 4. We also perform a random patch extraction and it can 本书版权归Arcler所有

![Image 1183](index-270_1.jpg)

![Image 1184](index-270_2.png)

![Image 1185](index-270_3.png)

![Image 1186](index-270_4.png)

Deep Learning Algorithms

244

be concluded that there is not much difference between 16384 subimages or just 25 cropped subimages (accuracy of 91.00%), saving considerable computation time and achieving good results. Besides that, using the same procedure we evaluate the architecture CNN-05 for the i-Scan3 database without staining the mucosa that presented the best results among the classical features and results are presented in Table 5.

**Table 5**. Accuracy of CNN-05 architecture comparing to classical features for the i-Scan1 and i-Scan3 databases in %

For a better comparability of results, we trained an SVM with the extracted vectors from the last fully connected layers (LFCL) and from the prior fully connected layers (PFCL) of CNN-05 as we make in the transfer learning approach explained in the next section. The vectors are extracted

\# ! { » { \` ' |

feedforwarded into the CNN-05 subsequently used to train a support vector machine also using the LOPO cross-validation \[55\]. The results from this approach using the CNN-05 architecture trained with the i-Scan1 and i-Scan3 without staining the mucosa databases are presented in Table 5. As it can be seen, using the last-layer vectors to train an SVM does not improve

#

\# ¯

the CNN is fully trained, the results surpass the classical features results as can be seen also in Table 5 mostly because the last layers are more suitable

¯

problem of lack of data still is an issue and using all the information in

\# # <

comparison between the methods will be explored in the next section.

Therefore, in order to try solving this problem, we also propose the use of transfer learning by pretrained CNNs that will be also explained in the next section.

本书版权归Arcler所有

![Image 1187](index-271_1.png)

![Image 1188](index-271_2.png)

![Image 1189](index-271_3.png)

![Image 1190](index-271_4.png)

Exploring Deep Learning and Transfer Learning for Colonic Polyp ...

245

**Pretrained CNNs**

In this section we present the experiments made exploring the 11 different off-the-shelf CNN architectures with the classical features trying to achieve better results than the CNN trained from scratch. As well as in the CNN

trained from scratch, we use the i-Scan1 without staining the mucosa database for the first experiments.

'

same image using overlapping patches by randomly cropping 25 images

! »» ! »»\` !

using bicubic interpolation for the tests presented in Table 8) increasing the database from 100 to 2500 images. The obtained results after the feature extraction performed by the CNN and after the SVM training also using the LOPO cross-validation are presented in Table 6.

**Table 6** +{# ! »

! »

It can be observed that, in this case, the use of more samples from the On the average, resizing the images produces an accuracy of 87.70% while cropping the images produces an average of 84.87%. One of the explanations for this is that, in case of resized images, there is more information about the polyp to provide to the network, so the CNN can abstract more information and form a more robust and intrinsic vector from the actual features of the lesion. However, in three cases (GoogleLeNet, VGG-VD16, and AlexNet MCN), the results using smaller cropped images surpassed the results using the entire image.

In the second experiment, still using i-Scan1 without staining the mucosa database, we also tested the use of other layers of CNNs to extract features. Table 7 shows the results obtained when the vectors are extracted from the last fully connected layer and when the vectors are from the prior fully connected layer. In the case of the last layer, the results are worse (87.70% against 85.75% on average) because the vectors from the prior fully connected layer are more related to high-level features describing the natural images used for training the original CNNs that are very different 本书版权归Arcler所有

![Image 1191](index-272_1.png)

![Image 1192](index-272_2.png)

![Image 1193](index-272_3.png)

![Image 1194](index-272_4.png)

![Image 1195](index-272_5.png)

Deep Learning Algorithms

246

from the features to describe colonic polyp images. However, in this case, the results from CNN-F and AlexNet CNN are better using the features from the last fully connected layers.

**Table 7** +{# ! »

the last fully connected layer and the prior fully connected layer **Table 8**. Accuracies of the methods for the CC-i-Scan databases in %

Based on the results from the two experiments explained before, we tested the methods with all the other databases using the inputs resized to

! »»### and extracting the features from

the prior fully connected layer. The accuracy results for the colonic polyp

\# <#

be seen, the results in Table 8 are divided into three groups: off-the-shelf features, classical features, and the fusion between off-the-shelf features and classical features that will be explained as follows.
