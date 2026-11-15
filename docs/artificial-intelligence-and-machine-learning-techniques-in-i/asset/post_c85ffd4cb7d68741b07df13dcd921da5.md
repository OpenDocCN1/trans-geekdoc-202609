
![](img/08e33f9814ed09d3c1bb11cd99f09e86_165_0.png)

In this image (Ground Truth), colors are vibrant with no discoloration and high resolution. Quality of the image is high, since no image processing operations have been performed on it.

### FIGURE 8.7 (a) Ground truth.

![](img/08e33f9814ed09d3c1bb11cd99f09e86_165_1.png)

In the gray scale image, there is a drop in quality.

### FIGURE 8.7 (b) Gray scale.

![](img/08e33f9814ed09d3c1bb11cd99f09e86_165_2.png)

The colors again are dull in the output and the image is not as sharp as ground truth.

### FIGURE 8.7 (c) Result.

### TABLE 8.1 Comparison With Other Research Paper.

| Parameters Authors | Title of paper | Methodology used | Network | Limitation |
|---|---|---|---|---|
| Kamyar Nazeri, Eric Ng, and Mehran Ebrahimi | Image Colorization using Generative Adversarial Networks (May 16, 2018) | CIFAR-10 Dataset | GAN | Miscoloration of certain images. |
| Federico Baldassarre, Diego González Morín, Lucas Rodés-Guirao | Deep Koalarization: Image Colorization using CNNs and Inception-Resnet-v2 (December 9, 2017) | Inception Resnet-V2 | Visual Geometry Group (VGG) | Discoloration of objects. |
| Ours | Image Colorization and Restoration Using Deep Learning | Resnet34 | UNet and DCGAN | Dullness in output images. |

### 8.6 CONCLUSION

In this research paper, technique of image colorization and restoration is successfully executed. The findings from this paper, based on the output, were that the gray scale images which were given as an input got colorized methodically. Also, the level of colorization of our model was on par with online software. However, the sharpness of an image got curtailed and the same can be resolved by further refining of the code, hence increasing the efficiency of the model. We found that there is a scope for improvizations hereafter.

### KEYWORDS

- deep learning
- colorization
- convolutional neural network (CNN)
- Resnet34
- ImageNet

### REFERENCES

- 1. Albawi, S.; Mohammed, T. A.; Al-Zawi, S. In Understanding of a Convolutional Neural Network, 2017 International Conference on Engineering and Technology (ICET), 2017; pp 1–6. DOI: 10.1109/ICEngTechnol.2017.8308186.
- 2. Simard, P. Y.; Steinkraus, D.; Platt, J. C. In Best Practices for Convolutional Neural Networks Applied to Visual Document Analysis, Proceedings of the Seventh International Conference on Document Analysis and Recognition, 2003; vol 2, pp 958–962.
- 3. Glorot, X.; Bengio, Y. In Understanding the Difficulty of Training Deep Feedforward Neural Networks, International Conference on Artificial Intelligence and Statistics, 2010; pp 249–256.
- 4. LeCun, Y.; Boser, B.; Denker, J. S.; Henderson, D.; Howard, R. E.; Hubbard, W.; Jackel, L. D. Backpropagation Applied to Handwritten Zip Code Recognition. Neural Comput. 1989, 1 (4), 541–551.
- 5. Krizhevsky, A.; Sutskever, I.; Hinton, G. In Imagenet Classification with Deep Convolutional Neural Networks, NIPS, 2012.
- 6. Zeiler, M. D.; Fergus, R. In Visualizing and Understanding Convolutional Neural Networks, ECCV, 2014, pp 818–833.
- 7. Sermanet, P.; Eigen, D.; Zhang, X.; Mathieu, M.; Fergus, R.; LeCun, Y. In Overfeat: Integrated Recognition, Localization and Detection Using Convolutional Networks, ICLR, 2014.
- 8. Simonyan, K.; Zisserman, A. In Very Deep Convolutional Networks for Large-Scale Image Recognition, ICLR, 2015.
- 9. Szegedy, C.; Liu, W.; Jia, Y.; Sermanet, P.; Reed, S.; Anguelov, D.; Erhan, D.; Vanhoucke, V.; Rabinovich, A. In Going Deeper with Convolutions, CVPR, 2015.
- 10. He, K.; Zhang, X.; Ren, S.; Sun, J. In Delving Deep into Rectifiers: Surpassing Human-Level Performance on Imagenet Classification, ICCV, 2015.
- 11. Ioffe, S.; Szegedy, C. In Batch Normalization: Accelerating Deep Network Training by Reducing Internal covariate Shift, ICML, 2015.
- 12. Russakovsky, O.; Deng, J.; Su, H.; Krause, J.; Satheesh, S.; Ma, S.; Huang, Z.; Karpathy, A.; Khosla, A.; Bernstein, M.; et al. Imagenet Large Scale Visual Recognition Challenge. arXiv:1409.0575, 2014.
- 13. Girshick, R.; Donahue, J.; Darrell, T.; Malik, J. In Rich Feature Hierarchies for Accurate Object Detection and Semantic Segmentation, CVPR, 2014.
- 14. He, K.; Zhang, X.; Ren, S.; Sun, J. In Spatial Pyramid Pooling in Deep Convolutional Networks for Visual Recognition, ECCV, 2014.
- 15. Girshick, R. In Fast R-CNN, ICCV, 2015.
- 16. Ren, S.; He, K.; Girshick, R.; Sun, J. In Faster R-CNN: Towards Real-time Object Detection With region Proposal Networks, NIPS, 2015.
- 17. Long, J.; Shelhamer, E.; Darrell, T. In Fully Convolutional Networks for Semantic Segmentation, CVPR, 2015.
- 18. Yamashita, R.; Nishio, M.; Do, R. K. G.; et al. Convolutional Neural Networks: An Overview and Application in Radiology. Insights Imaging 2018, 9, 611–629.
- 19. Ronneberger, O.; Fischer, P.; Brox, T. U-Net: Convolutional Networks for Biomedical Image Segmentation. In MICCAI 2015: LNCS; Navab, N., Hornegger, J., Wells, W. M., Frangi, A.F., Eds.; Springer: Cham, 2015; vol 9351, pp 234–241.
- 20. Jegou, H.; Perronnin, F.; Douze, M.; Sanchez, J.; Perez, P.; Schmid, C. Aggregating Local Image Descriptors into Compact Codes. Trans. Pattern Anal. Mach. Intell. 2012, 34 (9), 1704–1716.
- 21. Perronnin, F.; Dance, C. In Fisher Kernels On visual Vocabularies for Image Categorization, Conference on Computer Vision and Pattern Recognition, 2007.
- 22. Chatfield, K.; Lempitsky, V.; Vedaldi, A.; Zisserman, A. In The Devil is in the Details: An Evaluation of Recent Feature Encoding Methods, BMVC, 2011.
- 23. Vedaldi, A.; Fulkerson, B. VLFeat: An Open and Portable Library of Computer Vision Algorithms, 2008.
- 24. Jegou, H.; Douze, M.; Schmid, C. Product Quantization for Nearest Neighbor Search. Trans. Pattern Anal. Mach. Intell. 2011, 33 (1), 117–128.
- 25. Briggs, W. L.; McCormick, S. F.; et al. In A Multigrid Tutorial. SIAM, 2000.
- 26. Szeliski, R. Fast Surface Interpolation using Hierarchical Basis Functions. Trans. Pattern Anal. Mach. Intell. 1990, 12 (6), 513–528.
- 27. Szeliski, R. In Locally Adapted Hierarchical Basis Preconditioning, SIGGRAPH, 2006.
- 28. Goodfellow, I.; Pouget-Abadie, J.; Mirza, M.; Xu, B.; Warde-Farley, D.; Ozair, S.; Courville, A.; Bengio, Y. In Generative Adversarial Nets, Advances in Neural Information Processing Systems, 2014; pp 2672–2680.
- 29. Vincent, J. A Never-Ending Stream of AI Art Goes up for Auction. The Verge, 2019 (retrieved June 13, 2020).
- 30. Nazeri, K.; Ng, E.; Ebrahimi, M. Image Colorization using Generative Adversarial Networks, In Articulated Motion and Deformable Objects, 2018; pp 85–94.
- 31. Baldassarre, F.; Morin, D. G.; Rodés-Guirao, L. Deep Koalarization: Image Colorization using CNNs and Inception-Resnet-v2, Dec 9, 2017.
- 32. Konovalenko, I.; Maruschak, P.; Brezinová, J.; Prentkovskis, O.; Brezina, J. Research of U-Net-Based CNN Architectures for Metal Surface Defect Detection. Machines 2022, 10, 327. https://doi.org/10.3390/machines10050327

## CHAPTER 9

## DETERMINING IMAGE SCALE IN REAL-WORLD UNITS USING NATURAL OBJECTS PRESENT IN IMAGE

SAURABH SINGH^1 and RHEA S. SHRIVASTAVA^2

^1School of Computing Science and Engineering, Galgotias University, Greater Noida, India
^2Amity School of Engineering and Technology, Amity University, India

### ABSTRACT

The photograph is a 2D representation of intensity values in columns and rows which are stored in a digital computer. Defining the physical size of article in actual world units (e.g., mm, cm) is a challenging task. Some images have a real-world unit scale that helps individuals to assess the size of the objects present in the image. This scale is introduced at the acquisition time of the picture by the metalware infrastructure. Inopportunely, the scale is not present in a lot of visual descriptions (images), and it poses a problem to define the genuine size of the objects captured in an illustration. Thus, the determination of the size of objects in an image became the main goal of this research proposal.

The reason that this segment of the study is yet to be explored to its fullest was the incentive behind the work. In this research endeavor, our proposition is to find image scale (size in real-world unit per pixel) using the common size of the objects existing in the visual description. These regular objects could be people, cars, bikes, signposts, etc., depending
