
## 精确率、召回率和 F-分数

通过将所提框架生成的摘要与数据集中样本视频的基准摘要进行比较，计算精确率、召回率和 F-分数。所提系统和现有框架的精确率、召回率和 F-分数的平均结果如图 `Figure 7.6` 所示。所提框架与之比较的现有框架包括 `VSUMM` [5]、`Delaunay Triangulation` [7] 和 `VRCVS` [14]。所提系统的平均 F-分数为 72%，相较于以往系统相对较高。F-分数始终是视频摘要框架性能的理想因素。F-分数在信息检索系统中权衡了仅使用精确率和召回率的缺点。然而，可观察到所提框架的平均精确率并非最佳。原因是所提框架提取的关键帧数量相较于比较模型更多。由于精确率是相关帧在提取的关键帧中的比例，当提取的帧数稍多时，精确率值倾向于降低，因为两者成反比。另一方面，召回率出现较大回升。召回率是相关帧在提取的关键帧中占所有相关帧的比例，较高值表明所提模型提取的关键帧数量较多。可观察到平均召回率为 88%，这表明所提系统能够识别并提取更大比例的基准真实相关帧。总体而言，定量分析结果证明，该模型在保持较低复杂度的前提下表现优异。

![Figure 7.6 所提系统与现有系统在定量指标方面的比较。](img/fig7-6.jpg)

**Figure 7.6** 所提系统与现有系统在定量指标方面的比较。

## 定性分析

对 20 名用户进行定性评估。评估参数包括信息性、可享受性、多样性、连贯性和整体得分，每项均在 1 至 5 之间，5 为最佳。用户需对每个参数根据生成的摘要与原始视频给出评分，结果取平均值。定性参数的评估结果如图 `Figure 7.7` 所示。可观察到，信息性参数在所有视频类别中均较高，表明摘要内容信息丰富。可享受性参数的结果也令人期待，说明该模型在商业视频（如卡通）中能够提取既提供有用信息又具备娱乐性的帧。多样性和连贯性的结果也属可接受，但并非最佳。多样性较低是因为提取的关键帧数量稍高；连贯性较低则是由于输出为静态摘要，信息流动不连续。然而，所提框架的整体得分在所有视频类别中均较高，验证了模型的可接受性。

![Figure 7.7 所提系统在定性指标方面的性能。](img/fig7-7.jpg)

**Figure 7.7** 所提系统在定性指标方面的性能。

## 7.6 结论

视频摘要旨在通过自动识别视频中的相关帧或片段，为用户提供视频的概述。理想的视频摘要应具备信息性、代表性，同时保持简洁。所提系统基于特征聚类实现关键帧导向的视频摘要框架，聚类作用于已采样帧的单个块集合上。结果表明，由于所采用的聚类技术和嵌入的压缩阶段，系统计算效率高。此外，当聚类作用于不同块大小时，能够确保从视频中提取最大信息。在定量分析中，框架的 F-分数相对较高，优于现有系统。通过根据视频时长调整块大小，结果可进一步提升。定性分析也表明，该系统能够生成多样、信息丰富且有趣的摘要。使系统实时化是尚未实现的目标，这将进一步提升空间和时间的计算效率。同样，利用深度学习技术——近年来因在各领域表现出色而备受关注——也是未来潜在的研究方向。

## 参考文献

1. Ajmal, M., Ashraf, M.H., Shakir, M., Abbas, Y., Shah, F.A., Video summarization: techniques and classification, in: *International Conference on Computer Vision and Graphics*, Springer, Berlin, Heidelberg, pp. 1–13, 2012.

2. Kaur, P. and Kumar, R., Analysis of video summarization techniques. *Int. J. Res. Appl. Sci. Eng. Technol., (IJRASET)*, 6, 1, 1157–1162, 2018.

3. Moses, T.M. and Balachandran, K., A classified study on semantic analysis of video summarization, in: *2017 International Conference on Algorithms, Methodology, Models and Applications in Emerging Technologies (ICAMMAET)*, IEEE, pp. 1–6, 2017.

4. Sreeja, M.U. and Kovoor, B.C., Towards genre-specific frameworks for video summarization: A survey. *J. Visual Commun. Image Represent*., 62, 340–358, 2019.

5. De Avila, S.E.F., Lopes, A.P.B., da Luz Jr., A., de Albuquerque Araújo, A., VSUMM: A mechanism designed to produce static video summaries and a novel evaluation method. *Pattern Recognit. Lett*., 32, 1, 56–68, 2011.

6. Kumar, K., Shrimankar, D.D., Singh, N., Equal partition based clustering approach for event summarization in videos, in: *Signal-Image Technology & Internet-Based Systems (SITIS), 12th International Conference on*, IEEE, pp. 119–126, 2016.

7. Mundur, P., Rao, Y., Yesha, Y., Keyframe-based video summarization using Delaunay clustering. *Int. J. Digit. Libr*., 6, 2, 219–232, 2006.

8. Cirne, M.V.M. and Pedrini, H., A Video Summarization Method Based on Spectral Clustering, in: *Iberoamerican Congress on Pattern Recognition*, pp. 479–486, Springer, Berlin, Heidelberg, 2013.

9. Mishra, D.K. and Singh, N., Parameter Free Clustering Approach for Event Summarization in Videos, in: *Proceedings of International Conference on Computer Vision and Image Processing*, Springer, Singapore, pp. 389–397, 2017.

10. Guimarães, S.J.F. and Gomes, W., A static video summarization method based on hierarchical clustering, in: *Iberoamerican Congress on Pattern Recognition*, pp. 46–54, Springer, Berlin, Heidelberg, 2010.

11. Sachan, P.R., Frame clustering technique towards single video summarization, in: *Cognitive Computing and Information Processing (CCIP), Second International Conference on*, IEEE, pp. 1–5, 2016.

12. Gharbi, H., Bahroun, S., Massaoudi, M., Zagrouba, E., Key frames extraction using graph modularity clustering for efficient video summarization, in: *Acoustics, Speech and Signal Processing (ICASSP), IEEE International Conference on*, pp. 1502–1506, 2017.

13. Bay, H., Ess, A., Tuytelaars, T., Van Gool, L., Speeded-up robust features (SURF). *Comput. Vision Image Understanding*, 110, 3, 346–359, 2008.

14. Wu, J., Zhong, S.H., Jiang, J., Yang, Y., A novel clustering method for static video summarization. *Multimed. Tools Appl*., 76, 7, 9625–9641, 2017.

15. Rodriguez, A. and Laio, A., Clustering by fast search and find of density peaks. *Science*, 344, 6191, 1492–1496, 2014.

16. Majumdar, J., Kumar, K.S., Venkatesh, G.M., Analysis of video shot detection using color layout descriptor and video summarization based on expectation-maximization clustering, in: *Cognitive Computing and Information Processing (CCIP), International Conference on*, IEEE, pp. 1–5, 2015.

17. Cvetkovic, S., Jelenkovic, M., Nikolic, S.V., Video summarization using color features and efficient adaptive threshold technique. *Prz. Elektrotech*., 89, 2, 247–250, 2013.

18. Zhao, Y., Lv, G., Ma, T., Ji, H., Zheng, H., A novel method of surveillance video Summarization based on clustering and background subtraction, in: *Image and Signal Processing (CISP), 8th International Congress on*, IEEE, pp. 131–136, 2015.

19. John, A.A., Nair, B.B., Kumar, P.N., Application of Clustering Techniques for Video Summarization–An Empirical Study, in: *Computer Science On-line Conference*, Springer, Cham, pp. 494–506, 2017.

20. Fei, M., Jiang, W., Mao, W., Song, Z., New fusional framework combining sparse selection and clustering for key frame extraction. *IET Comput. Vision*, 10, 4, 280–288, 2016.

21. Sony, A., Ajith, K., Thomas, K., Thomas, T., Thomas, T., Deepa, P.L., Video summarization by clustering using Euclidean distance, in: *2011 International Conference on Signal Processing, Communication, Computing and Networking Technologies*, IEEE, pp. 642–646, 2011.

22. Lv, C. and Huang, Y., Effective Keyframe Extraction from Personal Video by Using Nearest Neighbor Clustering, in: *2018 11th International Congress on Image and Signal Processing, BioMedical Engineering and Informatics (CISPBMEI)*, IEEE, pp. 1–4, 2018.

23. Majumdar, J., Udandakar, S., Bai, B.M., Implementation of Cure Clustering Algorithm for Video Summarization and Healthcare Applications in Big Data, in: *Emerging Research in Computing, Information, Communication and Applications*, pp. 553–564, Springer, Singapore, 2019.

24. Chamasemani, F.F., Affendey, L.S., Mustapha, N., Khalid, F., Video abstraction using density-based clustering algorithm. *Vis. Comput*., 34, 10, 1299–1314, 2018.

25. Kuanar, S.K., Ranga, K.B., Chowdhury, A.S., Multi-view video summarization using bipartite matching constrained optimum-path forest clustering. *IEEE Trans. Multimedia*, 17, 8, 1166–1173, 2015.

26. Srinivas, M. and Mohan, C.K., Efficient clustering approach using incremental and hierarchical clustering methods. *International Joint Conference on Neural Networks (IJCNN)*, Barcelona, pp. 1–7, 2010.

27. Srinivas, M. and Mohan, C.K., Medical Image Indexing and Retrieval Using Multiple Features, in: *International Conference on Computational Intelligence and Information Technology*, October 2013.

28. Wang, Z., Bovik, A.C., Sheikh, H.R., Simoncelli, E.P., Image quality assessment: from error visibility to structural similarity. *IEEE Trans. Image Process*., 13, 4, 600–612, 2004.

1. *Corresponding author*: kishan.sreeja@gmail.com

# Part 2

## MACHINE LEARNING FOR HEALTHCARE SYSTEMS

# 8

## Cardiac Arrhythmia Detection and Classification From ECG Signals Using XGBoost Classifier

**Saroj Kumar Pandeyz\*, Rekh Ram Janghel and Vaibhav Gupta**

*Department of Information Technology, National Institute of Technology, Raipur, India (C.G.) India*

> ***Abstract***
>
