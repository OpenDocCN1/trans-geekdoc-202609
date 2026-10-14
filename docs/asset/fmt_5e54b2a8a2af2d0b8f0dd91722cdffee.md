
文献 [63] 描述了一种利用深度学习的图像篡改检测通用法医方法。具体而言，提出了一种新的卷积网络架构，能够以自动方式直接从训练数据中学习篡改检测特征。在当前实现中，`CNN` 学习的是捕获图像内容而非篡改检测特征的特征。为克服这一问题，开发了一种专门设计用于抑制图像内容并自适应学习篡改检测特征的新型卷积层。作者证明，所提出的方法可以自动学习多种图像伪造的检测，而无需依赖预选特征或其他预处理。

文献 [64] 的作者提出了两种通过融合重采样特征和深度学习来识别和定位图像篡改的方法。在前一种方法中，重采样特征的 Radon 变换在输入图像的重叠补丁上生成。使用深度学习分类器和高斯条件随机场模型创建热图。图像区域中篡改的位置通过随机游走分割方法定位。在后一种方法中，重叠图像补丁上生成的重采样特征通过基于长短期记忆（`LSTM`）的网络进行分类，并用于定位篡改。

文献 [65] 展示了篡改对自动人脸识别性能的影响，并提出了一种算法以高精度将人脸图像分类为原始或修饰。提出了一种有监督的深度玻尔兹曼机算法，通过使用面部部位学习判别特征来检测修饰，用于将人脸图像分类为原始或非原始。

文献 [66] 中提到了基于 `CNN` 的复合操纵检测方法。它通过所提出的 `CNN` 架构学习操纵引起的统计变化并对被操纵图像进行分类。该技术有效，因为它学习复合操纵的集成图像并提取与原始图像不同的特征。

## 24.5 图像篡改检测的未来方向

图像篡改检测系统远未成熟到可在现实世界场景中使用。为了使这些系统克服这一挑战，图像取证算法必须与反向图像搜索算法集成。图像谱系学是研究图像如何从其他图像演变而来的一个不断发展的研究分支，它努力使用树结构在它们之间建立关系。这有助于揭示图像的来源以及在进行法医调查之前所经历的后续变化。用树结构表示用于创建伪造图像的不同对象或来源之间的关系。这一想法源于生物学中的系统发育树概念。它们有很多应用，如追踪版权侵权者、提示儿童色情内容创作者，以及调查使用图像的网络骚扰。

文献 [67] 旨在自动检测图像之间关系的结构，正确重建其历史信息，并根据处理历史将它们分组为不同的树。提出了一种新算法，可自动处理包含相关图像的不同图像集，并输出相应的谱系树。

判断数字对象是否来自同一来源或不同来源本质上被视为一个聚类问题。相关对象归入同一簇，其余则归入不同簇。在 [68] 中，在语义相似图像集合中识别这些簇的问题在树重建之前通过结合流形学习和谱聚类来完成。

需要开发基于决策融合的图像取证方法以提高实际应用效率。

## 24.6 结论

我们已根据图像篡改技术执行方式对其进行分类，并在每一类中介绍了最新且可靠的研究成果。关于图像篡改检测方法的一个共同观察是，其中大多数方法旨在在特定数据集上表现良好，而非在实际案例中。我们尝试通过在图像取证与用于创建伪造图像的不同来源之间关系建立的重叠领域开展研究，为图像取证研究提供未来方向，以实现更好的实际可用性。此外，还应有融合不同来源线索的决策融合方法。

图像取证领域由于数据量、混合攻击方法、多传感器采集、应用领域的多种多样以及反取证活动的快速发展而变得更具挑战性。

## 参考文献

- 1. V. Christlein, C. Riess, J. Jordan, C. Riess, and E. Angelopoulou. An evaluation of popular copy-move forgery detection approaches. Information Forensics and Security, IEEE Transactions on, 7(6):1841–1854, 2012.

- 2. H. Bay, T. Tuytelaars, and L. Van Gool. SURF: Speeded up robust features. In Computer vision–ECCV 2006, pp. 404–417. Springer, Berlin, Germany, 2006.

- 3. C. Harris and M. Stephens. A combined corner and edge detector. In Proceedings of the Fourth Alvey Vision Conference, pp. 147–151, Manchester, UK, August 1988.

- 4. J. Babaud, A. P. Witkin, M. Baudin, and R. O. Duda. Uniqueness of the Gaussian kernel for scale-space filtering. IEEE Transactions on Pattern Analysis and Machine Intelligence, 8(1):26–33, 1986.

- 5. T. Lindeberg. Feature detection with automatic scale selection. International Journal of Computer Vision, 30(2):79–116, 1998.

- 6. I. Amerini, L. Ballan, R. Caldelli, A. Del Bimbo, and G. Serra. A SIFT-based forensic method for copy–move attack detection and transformation recovery. IEEE Transactions on Information Forensics and Security, 6(3):1099–1110, 2011.

- 7. V. Christlein, C. Riess, J. Jordan, C. Riess, and E. Angelopoulou. An evaluation of popular copy-move forgery detection approaches. IEEE Transactions on Information Forensics and Security, 7(6):1841–1854, 2012.

- 8. V. T. Manu and B. M. Mehtre. Copy-move tampering detection using affine transformation property preservation on clustered keypoints. Signal, Image and Video Processing, Vol. 12, 1–8, 2017.

- 9. J. Li, X. Li, B. Yang, and X. Sun. Segmentation-based image copy-move forgery detection scheme. IEEE Transactions on Information Forensics and Security, 10(3):507–518, 2015.

- 10. D. Cozzolino, G. Poggi, and L. Verdoliva. Efficient dense-field copy–move forgery detection. IEEE Transactions on Information Forensics and Security, 10(11):2284–2297, 2015.

- 11. S. Wenchang, Z. Fei, Q. Bo, and L. Bin. Improving image copy-move forgery detection with particle swarm optimization techniques. China Communications, 13(1):139–149, 2016.

- 12. N. B. A. Warif, A. W. A. Wahab, M. Y. Idna Idris, R. Salleh, and F. Othman. SIFT-symmetry: A robust detection method for copy-move forgery with reflection attack. Journal of Visual Communication and Image Representation, 46 (Supplement C): 219–232, 2017.

- 13. G. Jin and X. Wan. An improved method for SIFT-based copy–move forgery detection using non-maximum value suppression and optimized j-linkage. Signal Processing: Image Communication, 57(Supplement C):113–125, 2017.

- 14. X. Bo, W. Junwen, L. Guangjie, and D. Yuewei. Image copy-move forgery detection based on SURF. In Multimedia Information Networking and Security (MINES), 2010 International Conference on, pp. 889–892. Nanjing, China, November 2010.

- 15. E. Silva, T. Carvalho, A. Ferreira, and A. Rocha. Going deeper into copy-move forgery detection: Exploring image telltales via multi-scale analysis and voting processes. Journal of Visual Communication and Image Representation, 29(Supplement C):16–32, 2015.

- 16. E. Ardizzone, A. Bruno, and G. Mazzola. Copy–move forgery detection by matching triangles of keypoints. IEEE Transactions on Information Forensics and Security, 10(10):2084–2094, 2015.

- 17. F. Yang, J. Li, W. Lu, and J. Weng. Copy-move forgery detection based on hybrid features. Engineering Applications of Artificial Intelligence, 59(Supplement C):73–83, 2017.

- 18. P. Kakar and N. Sudha. Exposing postprocessed copy–paste forgeries through transform-invariant features. IEEE Transactions on Information Forensics and Security, 7(3):1018–1028, 2012.

- 19. Z. Mohamadian and A. A. Pouyan. Detection of duplication forgery in digital images in uniform and non-uniform regions. In 2013 UKSim 15th International Conference on Computer Modelling and Simulation, Cambridge, UK, pp. 455–460, April 2013.

- 20. L. Zhong and W. Xu. A robust image copy-move forgery detection based on mixed moments. In 2013 IEEE 4th International Conference on Software Engineering and Service Science, pp. 381–384, May 2013.

- 21. M. F. Hashmi, V. Anand, and A. G. Keskar. Copy-move image forgery detection using an efficient and robust method combining un-decimated wavelet transform and scale invariant feature transform. AASRI Procedia, 9:84–91, 2014. 2014 AASRI Conference on Circuit and Signal Processing (CSP 2014).

- 22. R. Davarzani, K. Yaghmaie, S. Mozaffari, and M. Tapak. Copy-move forgery detection using multiresolution local binary patterns. Forensic Science International, 231(1):61–72, 2013.

- 23. D. G. Lowe. Distinctive image features from scale-invariant keypoints. International Journal of Computer Vision, 60(2):91–110, 2004.

- 24. C. Harris and M. Stephens. A combined corner and edge detector. In Alvey Vision Conference, vol. 15, pp. 147–151. Manchester, UK, 1988.

- 25. C. Barnes, E. Shechtman, A. Finkelstein, and D. B. Goldman. Patchmatch: A randomized correspondence algorithm for structural image editing. ACM Transactions on Graphics, 28(3):24–1, 2009.

- 26. E. Kee, J. F. O'brien, and H. Farid. Exposing photo manipulation from shading and shadows. ACM Transactions on Graphics, 33(5):165–171, 2014.

- 27. P. Fernández Alcantarrilla, A. Bartoli, and A. J. Davison. Kaze features. In European Conference on Computer Vision, pp. 214–227. Springer, Heidelberg, Germany, 2012.

- 28. S.-J. Ryu, M. Kirchner, M.-J. Lee, and H.-K. Lee. Rotation invariant localization of duplicated image regions based on Zernike moments. IEEE Transactions on Information Forensics and Security, 8(8):1355–1370, 2013.

- 29. J. Zhao and J. Guo. Passive forensics for copy-move image forgery using a method based on DCT and SVD. Forensic Science International, 233(1):158–166, 2013.

- 30. S. Bravo-Solorio and A. K. Nandi. Automated detection and localisation of duplicated regions affected by reflection, rotation and scaling in image forensics. Signal Processing, 91(8):1759–1770, 2011.

- 31. Y. Cao, T. Gao, L. Fan, and Q. Yang. A robust detection algorithm for copy-move forgery in digital images. Forensic Science International, 214(1):33–43, 2012.

- 32. M. Zandi, A. Mahmoudi-Aznaveh, and A. Talebpour. Iterative copy-move forgery detection based on a new interest point detector. IEEE Transactions on Information Forensics and Security, 11(11):2499–2512, 2016.

- 33. A. Ferreira, S. C. Felipussi, C. Alfaro, P. Fonseca, J. E. Vargas-Muñoz, J. A. dos Santos, and A. Rocha. Behavior knowledge space-based fusion for copy–move forgery detection. IEEE Transactions on Image Processing, 25(10):4729–4742, 2016.
