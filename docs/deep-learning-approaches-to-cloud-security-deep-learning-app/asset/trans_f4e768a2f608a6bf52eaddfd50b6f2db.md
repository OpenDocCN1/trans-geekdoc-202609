

每个计算节点每次迭代的模型信息集均为固定大小。AdaptQR 向慢节点分配较少的计算，同时通过在每个处理节点的每次迭代中快速重新分配计算量，向快节点分配更多的计算，从而间接调整集群的负载并改善模型训练的性能 [20]。

## 10.8.2 A-DIC（自适应动态同步并行）

Caffe 是一种以快速训练和简单图定义著称的深度学习框架。然而，Caffe 的开源版本不支持分布式深度学习。本文基于 Caffe 利用 A-DIC 和参数服务器的思路，实现了一种分布式深度学习框架。该结构如图 10.10 所示。

参数服务器主要包含以下模块：全局参数、看板模块、集群执行检查模块、动态同步控制模块和剩余负载重分配模块。

全局参数是主控模块，用于维护全局模型参数。它通过维护 Pthreads 与计算节点通信，并管理计算节点的性能及每个计算过程的迭代次数。集群执行检查模块负责收集和处理所有计算节点上传的实时性能信息。在分析各计算节点的性能后，动态协调控制模块和剩余负载重分配模块会校正弱限制（w）、过时阈值（s）和重分配的未完成任务（m_i）。

计算节点和处理节点主要包含以下模块：信息存储模块、处理模块、过时同步模块和性能检查模块。

统计存储模块用于保存每个计算节点的训练子单元。根据分配的任务 m_i，处理节点从数据看板模块读取参考规模数据以进行训练。注册模块提供多种计算文档，可用于检查本地模型。过时同步模块将根据当前的弱限制（w）和过时部分（s）动态调整同步边界的需求状态。如果条件满足，注册模块在当前迭代后可能足以继续同时进行更新。否则，处理模块可被指示在本地刷新并进入下一周期。性能检查模块用于监控处理节点的当前执行指标，例如内存、CPU、I/O，并将其整理后发送到边界服务器进行检查。

MPICH 完成了处理节点与边界从节点之间的通信。处理模块的注册过程通过非并发传输提供更新的梯度，全局参数通过 Pthreads 发送到计算节点。这种通信模式可以有效降低通信阻塞的风险 [21]。

![](img/146f9a713528a3fbc62fcad0f0d5a352_185_0.png)

图 10.10 A-DIC 训练块图。

## 10.9 结论

为了彻底解决分布式深度学习实践中由不同节点执行版本引起的偏差问题，本文引入了一种片负载运行时重分配方式（适配器），该方式可根据集群中各种计算性能，通过改变每个节点每个周期手中的主要任务，有效减少节点间的负载差异。随后，基于 DIC，我们通过集成适配器实现了另一种相同的计算架构和 A-DIC。在上述章节中，我们展示了 A-DIC 可在适当条件下有效适应节点执行的运行时波动，并通过实验完全解决了偏差问题。尽管如此，A-DIC 的精度和收敛速度值得注意。

## 参考文献

- 1. Abhishek Kumar & Jyotir Moy Chatterjee & Pramod Singh Rathore, 2020. “智能手机对抗应用与安全问题，” International Journal of Risk and Contingency Management (IJRCM), IGI Global, vol. 9(2), pages 1–18, April.
- 2. Alam M, Khan ZA (2017) 云计算环境中负载均衡算法的问题与挑战. Indian J Sci Technol. https://doi.org/10.17485/ijst/2017/v10i25/105688
- 3. Arani M, Souri A, Rahmanian A (2019) 雾计算中的资源管理方法：全面综述. J Grid Computer. https://doi.org/10.1007/s10723-019-09491-1
- 4. Baek J, Kaddoum G, Garg S, Kaur K, Gravel V (2019) 基于强化学习负载均衡算法的雾网络管理. IEEE Wirel Commun Netw Conf. https://doi.org/10.1109/WCNC.2019. 8885745
- 5. Bhargava, N., Bhargava, R., Rathore, P. S., & Kumar, A. (2020). 基于 Gabor 滤波器和回归挖掘算法提取特征向量的纹理识别. International Journal of Risk and Contingency Management (IJRCM), 9(3), 31–44. doi:10.4018/IJRCM.2020070103
- 6. Chilimbi, T. M., Suzue, Y., Apacible, J., & Kalyanaraman, K. (2014) Project Adam：构建高效可扩展的深度学习训练系统. In OSDI (Vol. 14, pp. 571–582).
- 7. Cun, Y. L., Boser, B., Denker, J. S., Henderson, D., Howard, R. E., Hubbard, W., et al. (1990). 基于反向传播网络的手写数字识别. Advances in Neural Information Processing Systems, 2(2), 396–404.
- 8. Dai, W., Kumar, A., Wei, J., Ho, Q., Gibson, G., & Xing, E. P. (2014). 基于参数服务器一致性模型的大规模高性能分布式机器学习. In National conference on artificial intelligence (pp. 79–87).
- 9. Deng, L. (2012). 用于机器学习研究的手写数字图像 MNIST 数据库 [网络精选]. IEEE Signal Processing Magazine, 29(6), 141–142.
- 10. Jia, Y., Shelhamer, E., Donahue, J., Karayev, S., Long, J., Girshick, R., et al. (2014) Caffe：用于快速特征嵌入的卷积架构. In Proceedings of the 22nd ACM international conference on Multimedia (pp. 675–678). ACM.
- 11. Kumar, A., Chatterjee, J. M., & Díaz, V. G. (2020). 一种结合 NLP 和概率神经网络的 SVM 电子邮件钓鱼新型混合方法. International Journal of Electrical and Computer Engineering, 10(1), 486.
- 12. Li, M., Zhou, L., Yang, Z., Li, A., Xia, F., Andersen, D. G., et al. (2013) 分布式机器学习参数服务器. In Big learning NIPS workshop (Vol. 6, p. 2).
- 13. N. Bhargava, S. Dayma, A. Kumar and P. Singh, “基于 WEKA 中简单 CART 算法的分类方法，” 2017 年第 11 届智能系统与控制国际会议 (ISCO), Coimbatore, 2017, pp. 212-216, doi: 10.1109/ISCO.2017.7855983.
- 14. Naveen Kumar, Prakarti Triwedi, Pramod Singh Rathore, “基于椭圆曲线密码学 (ECC) 的图像自适应水印自适应方法，” 第一届信息技术与知识管理国际会议 pp. 89–92, ISSN 2300-5963 ACSIS, Vol. 14 DOI: 10.15439/2018KM19
- 15. Naveen Kumar, Prakarti Triwedi, Pramod Singh Rathore, “基于椭圆曲线密码学 (ECC) 的图像自适应水印自适应方法，” 第一届信息技术与知识管理国际会议 pp. 89–92, ISSN 2300-5963 ACSIS, Vol. 14 DOI: 10.15439/2018KM19
- 17. Rathore, P.S., Chatterjee, J.M., Kumar, A. et al. 基于中继方法的 WSN 能效簇头选择. J Supercomput (2021). https://doi.org/10.1007/s11227-020-03593-4
- 18. Singh Rathore, P, Kumar, A., & Gracia-Diaz, V. (2020). 基于蜻蜓算法的先进簇头选择 RFID 网络寿命改进整体方法. International Journal Of Interactive Multimedia And Artificial Intelligence, 6 (Regular Issue), 8. http://doi.org/10.9781/ijimai.2020.05.003
- 19. Xing, E., Ho, Q., Dai, W., Kim, J. K., Wei, J., Lee, S., et al. (2015). Petuum：面向大数据的分布式机器学习新平台. IEEE Transactions on Big Data, 1(2), 49–67.
- 20. Zhang, J., Sha, C., Wu, Y., Jian, W., Li, Z., Ren, Y., et al. (2016). 基于 GPU 集群核反应堆扩散方程的新型隐式 LU-SGS 并行迭代方法. Computer Physics Communications, 211, S0010465516301965.
- 21. Zhang, J., Xiao, J., Wan, J., Ren, Y., Si, H., et al. (2017). 基于异构集群的移动信息系统卷积神经网络并行策略. Mobile Information Systems, 2017, 3824765. https://doi.org/10.1155/2017/3824765

