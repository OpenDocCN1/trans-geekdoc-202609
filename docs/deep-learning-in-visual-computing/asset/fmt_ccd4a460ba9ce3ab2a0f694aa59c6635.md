
where `im` is an image number, and `n` is total images in the training set and,

$$CS\left( {test\_{im},training\_{im}^{n}} \right) = \frac{\sum\_{j = 1}^{m}{training\_{jm}^{i}test\_{im}}}{\sqrt{\sum\_{j = 1}^{m}{training\_{jm}^{i2}}}\sqrt{\sum\_{j = 1}^{m}{test\_{im}^{2}}}}$$ (4.7)

where `m` is the length of the vector.

## Experiments

Using the above formulation, some experiments are discussed here showing how the VGG-F behaves and performs on face recognition tasks with partial faces. To undertake this work, we have utilised face images from two popular face datasets, namely, the FEI and LFW. All images from both of the databases were cropped to remove the background as much as possible using a cascade object detector to extract the face and the internal facial features. However, for some images with very complex backgrounds (as in the case of the LFW database), we cropped the faces from those images manually. For the purpose of training, 70% of the images per subject were utilised and augmented through operations such as padding and flipping. The remaining 30% of the images were used for testing in each case.

## Experiment 1

In this experiment, using the FEI dataset, ten test sets were generated for each part of the face. Hence there are 600 images per dataset. The parts of the face chosen were the eyes, nose, right cheek, mouth, and forehead. In addition, faces were generated just with eyes and nose, bottom half face, top half face, right half and three quarters face, and the full-face as well. [Figure 4.6](#11_ch4.xhtml#f4_6) shows a sample of each image.

![Figure 4.6: A sample of parts of the face for a typical face from the FEI dataset.](images/fig4_6_B.jpg)

[Figure 4.6:](#11_ch4.xhtml#f4_6b) A sample of parts of the face for a typical face from the FEI dataset.

After extracting the features from all the testing databases by the VGG-F model, the SVM was applied to investigate a rate of recognition in each part separately. As can be seen in the graph shown in [Figure 4.7](#11_ch4.xhtml#f4_7), the highest percentage was with the full face, which was 100% and three quarters as well. At the bottom half, the proportion is decreased gradually and reaches about 50% and this decline is continued until nearly 0.5% at the right cheek.

## Experiment 2

This experiment aimed to find the effect of the rotation of the face on recognition. Here 18 separate datasets were generated, and each one had 600 images. These datasets were named R10, R20, R30... R180, etc. The symbol R indicates the rotation in degrees applied. [Figure 4.8](#11_ch4.xhtml#f4_8) shows some samples of rotated faces.

As in the previous experiment, the features that were extracted from all the images were by using the VGG-F model, and these features were tested by SVMs. The best angles that produced the optimum recognition were 10°, 20°, and 30°, the recognition rate at these degrees are 100%, 100%, and about 97% respectively. On the other hand, at 50° the recognition rate dropped down gradually to approximately 27% and this decline continued to decrease until it reached 1% at the inverted face. [Figure 4.9](#11_ch4.xhtml#f4_9) presents the rate of recognition at each angle.

![Figure 4.7: Face recognition rates (%) for partial faces, for the FEI face data.](images/fig4_7_B.jpg)

[Figure 4.7:](#11_ch4.xhtml#f4_7b) Face recognition rates (%) for partial faces, for the FEI face data.

![Figure 4.8: Sample of rotated faces from 10’ to 180’.](images/fig4_8_B.jpg)

[Figure 4.8:](#11_ch4.xhtml#f4_8b) Sample of rotated faces from 10’ to 180’.

## Experiment 3

In this experiment, nine test sets were used for zoomed faces (zoom 10, zoom 20, zoom 30, ... , zoom 90). In addition, each test set had 600 images and all of them were tested individually to find out which degree of zooming can a machine fail in the recognition and which degree had a good rate of recognition. [Figure 4.10](#11_ch4.xhtml#f4_10) illustrates the samples of zoomed faces.

![Figure 4.9: Face recognition rates (%) for partial faces with rotation for data from the FEI database.](images/fig4_9_B.jpg)

[Figure 4.9:](#11_ch4.xhtml#f4_9b) Face recognition rates (%) for partial faces with rotation for data from the FEI database.

![Figure 4.10: Samples of zoomed faces.](images/fig4_10_B.jpg)

[Figure 4.10:](#11_ch4.xhtml#f4_10b) Samples of zoomed faces.

After extracting the features for all the faces by using the VGG-F model and linear SVM that was used to classify all of the faces, the following results were formed; the highest recognition rate is at zooming 10°, 20° and 30° respectively which is 100% at each of them. This percentage is slightly decreased at the zooming angle of 50°, which is about 97%. On the other hand, at 60° the recognition dropped down gradually to roughly 46%. Contrary to that the recognition proportion reached near 0.5% at zooming 70, 80, and 90.

## Experiment 4

In this experiment, twelve test sets were generated with each test corresponding to a specific part of the face, from faces in the FEI dataset. This time both the full and parts of the face were used in training. The parts of the face that were tested included the eyes, nose, right cheek, mouth, and forehead. Also, faces were generated using just the eyes and nose, the bottom half of the face, the top half of the face, the right half, and a three-quarter of the face, in addition to the full face.

After extracting features from the VGG-Face model, the CS without parts (CS-Wo) and the linear SVM (with 19900 binary classifiers) without parts (SVM-Wo) were applied to investigate the rate of recognition for each facial part separately. The highest recognition rate is achieved when using the full face, and the three-quarter of the face since a recognition rate of 100% is achieved when using both classifiers. However, the recognition rate starts to slightly decrease when using the right half and the top half of the face, respectively with SVM-Wo, but in the case of CS-Wo, the rate remains at 100%. Similarly, as we approach the bottom half of the face, the rate of recognition decreases further to approximately 50% in the case of SVM-Wo and about 60% for CS-Wo. This decline continues until nearly 0.5% for the right cheek.

To measure the rate of recognition using parts of the face, we repeated the above procedure, but this time we added the individual parts of the face into the training set also. The recognition rates in this case significantly improved. For instance, while the results from the right cheek previously were nearly 0%, the recognition rate increased to 15% when using both the classifiers. Also, in the case of the combined eyes and nose features, recognition was previously at 22% for SVM-W and 40% for CS-W. However, in this case, recognition improves to approximately 57% for SVM-W and 90% when using CS-W. We have noticed, however, that not all recognition rates steadily increase. In some cases, the results were slightly worse for SVM-W. For example, a slight decrease in the recognition rate was observed when the bottom half of the face was tested, a recognition rate of 53% was achieved but decreased to 51%. In contrast, the CS-W approach has produced a significant improvement; for example, the recognition rate for combined eyes and nose increased from 40% to 90%.

## Experiment 5

In this experiment, twelve test sets were generated with each test corresponding to a specific part of the face, from faces in the LFW dataset—again using both the full and parts of the face were used in training. The parts of the face that were tested included the eyes, nose, right cheek, mouth, and forehead. Also, faces were generated using just the eyes and nose, the bottom half of the face, the top half of the face, the right half, and a three-quarter of the face, in addition to the full face.
