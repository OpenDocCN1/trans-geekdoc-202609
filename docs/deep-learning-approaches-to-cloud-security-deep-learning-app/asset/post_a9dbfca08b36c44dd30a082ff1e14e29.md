
updated for a mosaic background. Figure 5.2 illustrates how mosaicing is generated for the 50 frames and it indicates a Red as Necessary Frame, Green as Lost Area, and Blue as Overlapping Area [15].

Overlapping area between two key frames should retain enough information for this scene; meanwhile, the lost information must be smaller than a limit. Equations (5.2), (5.3), (5.4), (5.5), and (5.6) are used to define the conditions.

Overlap area > \(P_{overlap}\) (5.2)

Lost area < \(P_{lost}\) (5.3)

Overlap is the threshold which is used to make sure that the two key frames’ overlap area is large enough [16]. This parameter is often set to 30%. At the same time, the lost information should not be too large to influence the final mosaic significantly. Therefore, another parameter, Plots, is also very useful. This threshold, Plots, is often been set to 10%. Where W is the sum number of Pixels [17],

Overlap Area = \(\frac{Area (A \cap C)}{Area (oneframe)}\) (5.4)

![](img/146f9a713528a3fbc62fcad0f0d5a352_90_0.png)

Figure 5.3 Comparison of mosaic features.

Lost Area = \(\frac{Area (A \cup B_1 \cup B_n \cup C)-Area(A \cup C)}{Area (oneframe)}\) (5.5)

Difference (X, Y) = \(\frac{1}{W} \sum \|X - Y\|^2\) (5.6)

### 5.3.3 Foreground Segmentation

The constructed mosaiced background model as shown in Figure 5.3, is fed to the foreground segmentation. Fixed thresholds for finding the foreground and background are determined. If the threshold is higher than the key frame, then it is foreground and otherwise, background [18].

## 5.4 Results and Discussion

Foreground segmentation in image sequences taken from PTZ cameras has been experimented with using MATLAB® 2016 software on datasets,
![](img/146f9a713528a3fbc62fcad0f0d5a352_91_0.png)
Figure 5.4 (a) Input frame 220 on VIP dataset, (b) Extracted SURF features, (c) Mosaic background modelling and (d) Foreground segmentation.

such as MICC and VIP Videos, by applying Deep Learning techniques. The sample frames are shown in Figure 5.4 (a-d) and Figure 5.5 (a-d). Input video is used for feature extraction by SURF as shown in Figure 5.4 (a-d) and Figure 5.5 (a-d) and illustrates the robust features [19]. The first frame is taken as a reference frame and is compared to each successive frame. Track these N feature points using a SURF algorithm frame-to-frame until feature points mismatch. Then, set the current frame as a key frame for mosaicking, updating the key frame to the new reference image and selecting N feature points on it. Finally, the Background Mosaic Construction is made as shown in Figures 5.4 and 5.5. Further, the background mosaic is used for region-based segmentation and is done with more accurate results, as shown in Figures 5.4 and 5.5. Compared to traditional methods like SIFT Features, the SURF will have fast and robust features for motion segmentation. Performance measure for the dataset proves Mosaic Based Background Modeling for SURF has fast and accurate registration results, as shown in Figure 5.5.

![](img/146f9a713528a3fbc62fcad0f0d5a352_92_0.png)

![](img/146f9a713528a3fbc62fcad0f0d5a352_92_1.png)

![](img/146f9a713528a3fbc62fcad0f0d5a352_92_2.png)

![](img/146f9a713528a3fbc62fcad0f0d5a352_92_3.png)

Figure 5.5 (a) Input frame 220 on MICC dataset, (b) Extracted SURF features, (c) Mosaic background modelling and (d) Foreground segmentation.

## 5.5 Conclusion

This paper proposes and solves the problem of moving object detection in frame sequences. With PTZ cameras, object segmentation is done using a Background Mosaic Model based on Deep Learning segmentation approaches and then uses the foreground extraction technique. From extracted feature points, the accuracy of segmentation is improved with the help of a SURF feature-based Background Mosaic Model algorithm. The advantages of this method are plenty and, thus, this method is used in a variety of surveillance applications which require tracking and classification. In future work, complex video scenarios with harder conditions will be tested. Trying to detect humans while they are partially or completely occluded is not easy, but using a fast and discriminative descriptor like SURF can solve the problem.

## References

- 1. Abhishek Kumar & Jyotir Moy Chatterjee & Pramod Singh Rathore, 2020. “Smartphone Confrontational Applications and Security Issues,” International Journal of Risk and Contingency Management (IJRCM), IGI Global, vol. 9(2), pages 1–18, April.
- 2. Alessio Ferone and Lucia Maddalena, “Neural Background Subtraction for Pan-Tilt-Zoom Cameras”, IEEE Transactions on Systems, Man, and Cybernetics: Systems.
- 3. Bhargava, N., Bhargava, R., Rathore, P. S., & Kumar, A. (2020). Texture Recognition Using Gabor Filter for Extracting Feature Vectors With the Regression Mining Algorithm. International Journal of Risk and Contingency Management (IJRCM), 9(3), 31-44. doi:10.4018/IJRCM.2020070103.
- 4. Christopher Broaddus, Changjiang Yang, Shunguang Wu, Tao Zhao and Manoj Aggarwal, “Robust pan, tilt and zoom estimation for ptz camera by using meta data and/or frame-to-frame correspondences”, Control, Automation, Robotics and Vision, 2006.
- 5. J. Lu, F. L. Li, M. Jiang, “Detection and Tracking of Moving Targets with a Moving Camera”, Journal of Harbin Engineering University, 29(8), pp. 831-835, Aug 2008.
- 6. Jing Li, Quan Pan, Stan. Z. Li, Tao Yang, “Automated Feature Points Management for Video Mosaic Construction”, World Academy of Science, Engineering and Technology International Journal of Computer, Information, Systems and Control Engineering Vol:1 No:2, 2007.
- 7. Kang Xue, Gbolabo Ogunmakin, Yue Liu, Patricio A. Vela, Yongtian Wang, “Ptz Camera-Based Adaptive Panoramic And Multi-Layered Background Model”, 2011 18th IEEE International Conference on Image Processing.
- 8. Kumar, A., Chatterjee, J. M., & Diaz, V. G. (2020). A novel hybrid approach of SVM combined with NLP and probabilistic neural network for email phishing. International Journal of Electrical and Computer Engineering, 10(1), 486.
- 9. Maddalena and A. Petrosino, “A self-organizing approach to background subtraction for visual surveillance applications,” IEEE Trans.Image Process., vol. 17, no. 7, pp. 1168–1177, Jul. 2008.
- 10. N. Bhargava, S. Dayma, A. Kumar and P. Singh, “An approach for classification using simple CART algorithm in WEKA,” 2017 11th International Conference on Intelligent Systems and Control (ISCO), Coimbatore, 2017, pp. 212-216, doi: 10.1109/ISCO.2017.7855983.
- 11. Naveen Kumar, Prakarti Triwedi, Pramod Singh Rathore, “An Adaptive Approach for image adaptive watermarking using Elliptical curve cryptography (ECC)”, First International Conference on Information Technology and Knowledge Management pp. 89–92, ISSN 2300-5963 ACSIS, Vol. 14 DOI: 10.15439/2018KM19.
- 12. Rathore P S, Kumar A “An adaptive method for Edge Preserving Denoising”, International Conference on Communication and Electronics Systems, Institute of Electrical and Electronics Engineers and PPG Institute of Technology. (2017). Proceedings of the 2nd International Conference on Communication and Electronics Systems (ICCES 2017): 19-20, October 2017.
- 13. Rathore, P.S., Chatterjee, J.M., Kumar, A. et al. Energy-efficient cluster head selection through relay approach for WSN. J Supercomput (2021). https://doi.org/10.1007/s11227-020-03593-4.
- 14. Singh Rathore, P., Kumar, A., & Gracia-Diaz, V. (2020). A Holistic Methodology for Improved RFID Network Lifetime by Advanced Cluster Head Selection using Dragonfly Algorithm. International Journal Of Interactive Multimedia And Artificial Intelligence, 6 (Regular Issue), 8. http://doi.org/10.9781/ijimai.2020.05.003.
- 15. Sudipta N. Sinha and Marc Pollefeys, “Pan-tilt-zoom camera calibration and high-resolution mosaic generation”, Computer Vision and Image Understanding, vol. 103, pp. 170–183, 2006.
- 16. X. C. Zhou, D. W. Tu, Y. Chen, Q. J. Zhao, Y. C. Zhang, “Moving Object Detection under Dynamic Background based on Phase-correlation and Differential Multiplication”, Chinese Journal of Scientific Instrument, 31(5), pp. 980-983, May 2010.
- 17. Xinghua Li, Qinglei Chen, Haiyang Chen, “Detection and Tracking of Moving Object Based on PTZ Camera”, 2012 IEEE fifth International Conference on Advanced Computational Intelligence (ICACI) October 18-20, 2012 Nanjing, Jiangsu, China.
