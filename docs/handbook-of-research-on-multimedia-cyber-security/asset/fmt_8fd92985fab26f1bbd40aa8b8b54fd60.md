
The recognition rate using convolution kernel of the CASIA-B data set is better than the recognition result of the `3×3` convolution kernel, the feature fusion is based on the `3×3` and `7×7` convolution kernels. The subsequent recognition accuracy is better than or equal to the recognition accuracy of a single convolution kernel. At the same time, this chapter compares the proposed method with other existing methods GPPE, GEI, STIPs and CNN based methods. In Table 3, the proposed method is slightly lower than the existing deep learning-based methods in the same state experiments (nm-nm) and (cl-cl), because it used a deeper network. In the experiment of cross states, the method is better, it indicates that the method of this chapter is better than its robustness. In addition, the accuracy of cross states is lower than other existing methods, because traditional methods can be identified by using targeted design features, while deep learning requires more walking posture for training to increase the generalization ability of the network. However, only one kind of walking states lead to poor generalization ability of the network; thus, the experimental results of the cross states are not better than the existing methods.

## CONCLUSION

In this chapter, the deep neural network `CRBM+FC` is created for human gait recognition. Based on LBP and HOG fusion, a method of end-to-end deep learning gait recognition from GEI to output is proposed. This paper also proposed an algorithm based on gait energy map for gait recognition. The method used the layering idea to overcome the shortcomings of gait energy map, which not only captures the local information of human body image, but also extracts its contour and shape information. The fusion of these information is based on the CASIA gait datasets. The recognition algorithm of this chapter has achieved a high recognition rate. It proposed a feature learning network consisting of a convolutionally constrained Boltzmann machine and a fully connected neural network. The network first uses feature-constrained Boltzmann machines with different convolution kernels to extract features from gait images; because convolution-limited Boltzmann machines are unsupervised, they can learn extensively and abundantly. Although rich gait feature information is learned, there must be redundant and less useful information. Therefore, this paper used a supervised all-connected layer network to learn these features deeply.

In single scenarios, the detection and extraction of gait are relatively simple. However, in complex practical scenarios, the complexity of factors, e.g., background and multiple individuals, etc., makes it difficult to accurately acquire gait. Inaccurate gait information directly affects the final recognition efficiency and accuracy (Sivapalan, et al. 2013).

## REFERENCES

Ahonen, T., Hadid, A., & Pietikainen, M. (2006). Face description with local binary patterns: Application to face recognition. *IEEE Transactions on Pattern Analysis and Machine Intelligence*, 28(12), 2037–2041. doi:10.1109/TPAMI.2006.244

Begg, R. K., Palaniswami, M., & Owen, B. (2005). Support vector machines for automated gait classification. *IEEE Transactions on Biomedical Engineering*, 52(5), 828–838. doi:10.1109/TBME.2005.845241

Boykov, Y. Y., & Jolly, M. P. (2001). Interactive graph cuts for optimal boundary & region segmentation of objects in ND images. *Proceedings IEEE International Conference on Computer Vision*. (Vol. 1, pp. 105-112). Academic Press.

BulatA.TzimiropoulosG. (2016). Human pose estimation via convolutional part heatmap regression. *Proceedings European Conference on Computer Vision* (pp. 717-732). Springer. 10.1007/978-3-319-46478-7\_44

CaoZ.SimonT.WeiS. E.SheikhY. (2017). Realtime multi-person 2D pose estimation using part affinity fields. *Proceedings IEEE Conference on Computer Vision and Pattern Recognition* (pp. 7291-7299). 10.1109/CVPR.2017.143

Chen, C., Liang, J., Zhao, H., Hu, H., & Tian, J. (2009). Frame difference energy image for gait recognition with incomplete silhouettes. *Pattern Recognition Letters*, 30(11), 977–984. doi:10.1016/j.patrec.2009.04.012

Cunado, D., Nixon, M. S., & Carter, J. N. (1997). Using gait as a biometric, via phase-weighted magnitude spectra. *Proceedings International Conference on Audio-and Video-Based Biometric Person Authentication* (pp. 93-102). Berlin, Germany: Springer. 10.1007/BFb0015984

Dalal, N., & Triggs, B. (2005). Histograms of oriented gradients for human detection. *Proceedings International Conference on Computer Vision & Pattern Recognition*, 1, 886–893. IEEE.

DerlatkaM.BogdanM. (2015). Fusion of static and dynamic parameters at decision level in human gait recognition. *Proceedings International Conference on Pattern Recognition and Machine Intelligence* (pp. 515-524). Springer. 10.1007/978-3-319-19941-2\_49

Foresti, G. L. (1999). Object recognition and tracking for remote video surveillance. *IEEE Transactions on Circuits and Systems for Video Technology*, 9(7), 1045–1062. doi:10.1109/76.795058

Han, J., & Bhanu, B. (2005). Individual recognition using gait energy image. *IEEE Transactions on Pattern Analysis and Machine Intelligence*, 28(2), 316–322. doi:10.1109/TPAMI.2006.38

Han, X. (2010). Gait recognition considering walking direction. USA: University of Rochester.

HeK.GkioxariG.DollárP.GirshickR. (2017). Mask R-CNN. *Proceedings IEEE International Conference on Computer Vision* (pp. 2961-2969). IEEE.

JeevanM.JainN.HanmandluM.ChettyG. (2013). Gait recognition based on gait pal and pal entropy image. *Proceedings IEEE International Conference on Image Processing* (pp. 4195-4199). IEEE. 10.1109/ICIP.2013.6738864

Johansson, G. (1973). Visual perception of biological motion and a model for its analysis. *Perception & Psychophysics*, 14(2), 201–211. doi:10.3758/BF03212378

Kusakunniran, W. (2014). Attribute-based learning for gait recognition using spatio-temporal interest points. *Image and Vision Computing*, 32(12), 1117–1126. doi:10.1016/j.imavis.2014.10.004

Lam, T. H., Cheung, K. H., & Liu, J. N. (2011). Gait flow image: A silhouette-based gait representation for human identification. *Pattern Recognition*, 44(4), 973–987. doi:10.1016/j.patcog.2010.10.011

LeeH.GrosseR.RanganathR.NgA. Y. (2009). Convolutional deep belief networks for scalable unsupervised learning of hierarchical representations. *Proceedings ACM Annual International Conference on Machine Learning* (pp. 609-616). 10.1145/1553374.1553453

LeeL.GrimsonW. E. L. (2002). Gait analysis for recognition and classification. *Proceedings IEEE International Conference on Automatic Face Gesture Recognition* (pp. 155-162). IEEE. 10.1109/AFGR.2002.1004148

Little, J., & Boyd, J. (1998). Recognizing people by their gait: The shape of motion. *Journal of Computer Vision Research*, 1(2), 1–32.

Liu, X., & Payandeh, S. (2018). A study of chained stochastic tracking in RGB and depth sensing. *Journal of Control Science and Engineering*, 2018.

Murase, H., & Sakai, R. (1996). Moving object recognition in eigenspace representation: Gait analysis and lip reading. *Pattern Recognition Letters*, 17(2), 155–162. doi:10.1016/0167-8655(95)00109-3

NiyogiS. A.AdelsonE. H. (1994). Analyzing gait with spatiotemporal surfaces. *Proceedings IEEE Workshop on Motion of Non-rigid and Articulated Objects* (pp. 64-69). IEEE.

RidaI.BoubchirL.Al-MaadeedN.Al-MaadeedS.BouridaneA. (2016). Robust model-free gait recognition by statistical dependency feature selection and Globality-Locality Preserving Projections. *Proceedings International Conference on Telecommunications and Signal Processing (TSP)* (pp. 652-655). 10.1109/TSP.2016.7760963

Sarkar, S., Phillips, P. J., Liu, Z., Vega, I. R., Grother, P., & Bowyer, K. W. (2005). The humanid gait challenge problem: Data sets, performance, and analysis. *IEEE Transactions on Pattern Analysis and Machine Intelligence*, 27(2), 162–177. doi:10.1109/TPAMI.2005.39
