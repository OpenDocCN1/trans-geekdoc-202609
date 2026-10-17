
- 此外，在本手稿中，我们提出了一种基于 Monte-Carlo dropout 方法解释 NN 输出不确定性估计的新方法。我们解释模型预测不确定性的方式将提高模型的可信度，即使其初始预测误差率很低。同时，根据广泛的文献综述，这也是海况估计中首次对深度学习模型进行不确定性估计。

## 4. 结论

本文提出了一种新颖的基于注意力的深度学习模型，用于估计重要的海况特征。通过评估每个海况参数的性能，我们确认 AT-NN 模型经过微调，适合估计关键的海况参数。所提出的 AT-NN 模型带来的改进被证明是显著的，与先前提出的最佳原始最先进模型相比，在考虑所有估计的海况参数时，MSE 降低了多达 83%，MAE 降低了多达 62%，NSE 降低了多达 8%。与修改后的模型的最佳版本相比，MSE 降低了多达 13%，MAE 降低了多达 12%，NSE 降低了多达 0.4%。尽管使用 3 自由度输入运动数据，所提出的模型在每个估计的海况参数上，在所有测试的原始模型和增强模型中都取得了最佳结果。作为未来研究的后续步骤之一，利用 6 自由度船舶运动响应可能潜在地提高参数估计的精度。此外，在实际应用中，整个波浪方向谱的估计非常重要。因此，未来的工作方向还可能包括数值模拟中的波浪方向性信息，这可以将深度学习模型的应用扩展到短峰波以及风浪和涌浪组合的海况谱。

## CRediT 作者贡献声明

Denis Selimović：概念化，方法论，软件，验证，调查，数据管理，写作 – 初稿，可视化。Franko Hržić：概念化，方法论，软件，验证，调查，数据管理，写作 – 初稿，可视化。Jasna Prpić-Oršić：概念化，方法论，验证，形式分析，资源，数据管理，写作 – 审阅与编辑，监督，项目管理，获取资助。Jonatan Lerga：概念化，方法论，验证，形式分析，调查，资源，写作 – 初稿，写作 – 审阅与编辑，监督，项目管理，获取资助。

## 利益冲突声明

作者声明，他们没有任何已知的竞争性经济利益或个人关系，这些利益或关系可能影响本文所报告的工作。

## 数据可用性

数据将在合理要求下提供。

## 资助

本工作完全由克罗地亚科学基金会项目 IP-2018-01-3739、欧盟地平线 2020 项目 INNO2MARE（“加强斯洛文尼亚和克罗地亚创新生态系统能力，以支持海事区域的数字和绿色转型”，编号 101087348）、IRI2 项目“ABsistemDCiCloud”（KK.01.2.1.02.0179）以及里耶卡大学项目 uniri-tehnic-18-17 和 uniri-tehnic-18-15 支持。

## 参考文献

Agarap, A.F., 2018. Deep learning using rectified linear units (ReLU). CoRR abs/1803.08375 URL http://arxiv.org/abs/1803.08375, arXiv:1803.08375.

Baldi, P., Sadowski, P.J., 2013. Understanding dropout. In: Burges, C., Bottou, L., Welling, M., Ghahramani, Z., Weinberger, K. (Eds.), In: Advances in Neural Information Processing Systems, vol. 26, Curran Associates, Inc., URL https://proceedings.neurips.cc/paper/2013/file/71f6278d1a0f599e06ad9bf1ba03cb0-Paper.pdf.

Bochkovskiy, A., Wang, C., Liao, H.M., 2020. YOLOv4: Optimal speed and accuracy of object detection. CoRR abs/2004.10934 URL https://arxiv.org/abs/2004.10934, arXiv:2004.10934.

Bottou, L., 2012. Stochastic gradient descent tricks. In: Montavon, G., Orr, G.B., Müller, K.-R. (Eds.), Neural Networks: Tricks of the Trade: Second Edition. Springer Berlin Heidelberg, Berlin, Heidelberg, pp. 421–436. http://dx.doi.org/10.1007/978-3-642-35289-8_25.

Chai, T., Draxler, R.R., 2014. Root mean square error (RMSE) or mean absolute error (MAE)? – Arguments against avoiding RMSE in the literature. Geosci. Model Dev. 7 (3), 1247–1250. http://dx.doi.org/10.5194/gmd-7-1247-2014, URL https://gmd.copernicus.org/articles/7/1247/2014/.

Cheng, X., Li, G., Ellefsen, A., Chen, S., Hildre, H., Zhang, H., 2020a. A novel densely connected convolutional neural network for sea state estimation using ship motion data. IEEE Trans. Instrum. Meas. PP, 1. http://dx.doi.org/10.1109/TIM.2020.2967115.

Cheng, X., Li, G., Skulstad, R., Chen, S., Hildre, H., Zhang, H., 2019. Modeling and Analysis of Motion Data from Dynamically Positioned Vessels for Sea State Estimation. pp. 6644–6650. http://dx.doi.org/10.1109/TRA.2019.8794069.

Cheng, X., Li, G., Skulstad, R., Zhang, H., Chen, S., 2020b. SpectralSeaNet: Spectrogram and convolutional network-based sea state estimation. In: IECON 2020 the 46th Annual Conference of the IEEE Industrial Electronics Society. pp. 5069–5074. http://dx.doi.org/10.1109/IECON43393.2020.9254890.

Denis, M., Pierson, W., 1953. On the Motions of Ships in Confused Seas. Defense Technical Information Center, URL https://books.google.hr/books?id=3816a0AEACAAJ.

DNV-GL, 2018. Class guideline: Wave loads. DNVGL-CG-0130 84, Edition January.

Düz, B., Mak, B., Hageman, R., Grasso, N., 2019. Real time estimation of local wave characteristics from ship motions using artificial neural networks.

Faltinsen, O.M., 1990. Sea Loads on Ships and Offshore Structures. Cambridge University Press, The Edinburgh Building, Cambridge CB2 2RU, UK.

Gal, Y., Ghahramani, Z., 2016. Dropout as a Bayesian approximation: Representing model uncertainty in deep learning. In: Balcan, M.F., Weinberger, K.Q. (Eds.), Proceedings of the 33rd International Conference on Machine Learning. In: Proceedings of Machine Learning Research, vol. 48, PMLR, New York, New York, USA, pp. 1050–1059, URL https://proceedings.mlr.press/v48/gal16.html.

Galassi, A., Lippi, M., Torroni, P., 2021. Attention in natural language processing. IEEE Trans. Neural Netw. Learn. Syst. 32 (10), 4291–4308. http://dx.doi.org/10.1109/TNNLS.2020.3019893.

Garbin, C., Zhu, X., Marques, O., 2020. Dropout vs. batch normalization: An empirical study of their impact to deep learning. Multimedia Tools Appl. 79 (19), 12777–12815. http://dx.doi.org/10.1007/s11042-019-08453-9.

Hinostroza, M., Guedes Soares, C., 2016. Parametric estimation of the directional wave spectrum from ship motions. Int. J. Marit. Eng. 158, A121–A130. http://dx.doi.org/10.3940/rina.2016.a2.356.

Hochreiter, S., Schmidhuber, J., 1997. Long short-term memory. Neural Comput. 9 (8), 1735–1780. http://dx.doi.org/10.1162/neco.1997.9.8.1735.

Hu, J., Shen, L., Sun, G., 2018. Squeeze-and-excitation networks. In: Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition. CVPR.

IMO, 2007. Revised guidance to the master for avoiding dangerous situations in adverse weather and sea conditions.

ITTC (Ed.), 1969. Proceedings of the 12th International Towing Tank Conference, Vol. 1. ITTC, URL https://www.ittc.info/media/2745/index.pdf.

Jaderberg, M., Simonyan, K., Zisserman, A., kavukcuoglu, k., 2015. Spatial transformer networks. In: Cortes, C., Lawrence, N., Lee, D., Sugiyama, M., Garnett, R. (Eds.), In: Advances in Neural Information Processing Systems, vol. 28, Curran Associates, Inc., URL https://proceedings.neurips.cc/paper/2015/file/33ceb07bf4eeb3da587e268d663aba1a-Paper.pdf.

James, W., Stein, C., 1992. Estimation with quadratic loss. In: Kotz, S., Johnson, N.L. (Eds.), Breakthroughs in Statistics: Foundations and Basic Theory. Springer New York, New York, NY, pp. 443–460. http://dx.doi.org/10.1007/978-1-4612-0919-5_30.

Kingma, D.P., Ba, J., 2014. Adam: A method for stochastic optimization. http://dx.doi.org/10.48550/ARXIV.1412.6980, URL https://arxiv.org/abs/1412.6980.

Mak, B., Düz, B., 2019. Ship as a wave buoy: Estimating relative wave direction from in-service ship motion measurements using machine learning. In: International Conference on Offshore Mechanics and Arctic Engineering, Volume 9: Rodney Eatock Taylor Honoring Symposium on Marine and Offshore Hydrodynamics; Takeshi Kinoshita Honoring Symposium on Offshore Technology, http://dx.doi.org/10.1115/OMAE2019-96201.

Mittendorf, M., Nielsen, U., Bingham, H., 2022. The prediction of sea state parameters by deep learning techniques using ship motion data.

Montazeri, N., Nielsen, U.D., Juncher Jensen, J., 2016. Estimation of wind sea and swell using shipboard measurements – A refined parametric modelling approach. Appl. Ocean Res. 54, 73–86. http://dx.doi.org/10.1016/j.apor.2015.11.004, URL https://www.sciencedirect.com/science/article/pii/S0141118715001388.

Mukkamala, M.C., Hein, M., 2017. Variants of RMSProp and adagrad with logarithmic regret bounds. In: Precup, D., Teh, Y.W. (Eds.), Proceedings of the 34th International Conference on Machine Learning. In: Proceedings of Machine Learning Research, vol. 70, PMLR, pp. 2545–2553, URL https://proceedings.mlr.press/v70/mukkamala17a.html.

Nash, J., Sutcliffe, J., 1970. River flow forecasting through conceptual models part I — A discussion of principles. J. Hydrol. 10 (3), 282–290. http://dx.doi.org/10.1016/0022-1694(70)90255-6, URL https://www.sciencedirect.com/science/article/pii/0022169470902556.

Nielsen, U.D., 2006. Estimations of on-site directional wave spectra from measured ship responses. Mar. Struct. 19 (1), 33–69. http://dx.doi.org/10.1016/j.marstruc.2006.05.001, URL https://www.sciencedirect.com/science/article/pii/S095183390600529.

Nielsen, U.D., 2017. A concise account of techniques available for shipboard sea state estimation. Ocean Eng. 129, 352–362. http://dx.doi.org/10.1016/j.oceaneng.2016.11.035, URL https://www.sciencedirect.com/science/article/pii/S0029801816305388.
