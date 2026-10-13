
• 不应用时间和星期几的过滤器这一事实，由于数据集规模较小，为检测异常提供了更好的结果。这意味着 `Isolation Forest` 只需执行较少次数的分割即可隔离向量所选特征的值。

结论是，决定为位置维度使用一个数据集，为应用维度使用另一个数据集。这两个数据集均不按时间和星期几进行过滤。此外，新增的特征（本意欲通过它们构建两个特定的训练数据集）被移除，因为 `Isolation Forest` 可以从异常向量中选择这些特征。

图 12 显示了 `Isolation Forest` 所拥有的训练数据集方面的一组向量的评估。被评估的数据集由 15 个向量（前面表示的那些）组成，属于设备所有者用户；以及 5 个向量（后面表示的那些）组成，属于异常用户。正如你所见，设定在 0.55 的阈值使我们能够区分设备所有者用户与具有异常行为用户的行为。

| 图 12. 实验 3 数据集的图形表示 |
| --- |
| ![Figure978-1-7998-2701-6.ch002.f12](i/ch002.f12.png) |

# 6. 结论与未来工作

在本工作中，提出了一种基于通过位置维度和应用使用统计维度收集用户特征的、面向多媒体移动设备的持续自适应认证系统。采用了一种基于异常检测的无监督机器学习技术（如 `IF`），以精确的结果检测设备所有者和入侵者。选择 `IF` 作为使用的算法，是因为它在移动设备上使用时具有低能耗和低计算消耗，且提供较高的精度水平。在 `IF` 经过设备所有者配置文件训练后，所提出的解决方案准备好实时评估用户行为，允许算法通过插入满足特定特征的新向量到数据集中来实现自适应性。最后，不同的实验获得了有效结果，能够准确区分异常用户和设备所有者的行为。

在未来的研究方向中，我们计划将 `IF` 执行的计算迁移到云端，以降低其在移动设备上产生的计算成本和能耗成本。还打算研究新的维度，以更确定地建模用户行为档案。最后，我们计划使用额外的机器学习算法，测试在新改进加入后的异常检测效率。

# 致谢

本工作由 Fundación Séneca - 穆尔西亚大区科学技术局通过 AUTHCODE（面向设备持续访问的认证）项目（资助代码 20549/PDC/18）以及爱尔兰政府通过 IRC 博士后奖学金（资助代码 GOIPD/2018/466）提供资助。

# 参考文献

Abdiansah, A., & Wardoyo, R. (2015). Time complexity analysis of support vector machines (SVM) in LibSVM. *International Journal of Computers and Applications*, 128(3).

Adeli, H. (1999). Machine Learning‐Neural Networks, Genetic Algorithms and Fuzzy Systems. *Kybernetes*, 28(3), 317–318. doi:10.1108/k.1999.28.3.317.5

Agarwal S., Sureka A. (2015). Using knn and svm based one-class classifier for detecting online radicalization on twitter. *Proceedings International Conference on Distributed Computing and Internet Technology*, 431-442. 10.1007/978-3-319-14977-6_47

Aware, Inc. (2019). Biometrics Software Solutions. - Fingerprint, Face, Iris, Keystroke Recognition. Retrieved October 29, 2019, from http://aware.com/biometrics-software-solutions/authentication-and-payments

Bala, J. D. (2017). Application of Machine Learning in Feature Selection for Continuous Authentication. *Tennessee Tech University*.

BehavioSec, Inc. (2019). Continuous Authentication through Passive Behavioral Biometrics. Retrieved October 29, 2019, from http://behaviosec.com

Ben-Gal, I., Ruggeri, F., Faltin, F., & Kenett, R. (2007). Bayesian Network.

Bo C., Zhang L., Li X., Y. Huang Q., Wang Y. (2013). SilentSense: Silent User’s identification Via Touch and Movement Behavioral Biometrics. *Proceedings 19th Annual International Conference on Mobile Computing & Networking*, 187-190. 10.1145/2500423.2504572

Carmona, E. (2014). Tutorial sobre Máquinas de Vectores Soporte (SVM). *Department of Intelligence Artificial, Universidad Nacional de Educación a Distancia*. Spain: UNED.

Centeno M. P., van Moorsel A., Castruccio S. (2017). Smartphone continuous authentication using deep learning autoencoders. *Proceedings 15th Annual Conference on Privacy, Security and Trust (PST)*, 147-1478. 10.1109/PST.2017.00026

Developers, A. (2019). Distribution Dashboard. Retrieved October 29, 2019, from https://developer.android.com/about/dashboards/

Deyan, G. (2019, March 28). 60+ Smartphone. *Stat*, 2019. Retrieved from https://techjury.net/stats-about/smartphone-usage/

Domingos, P. (2012). A Few Useful Things to Know about Machine Learning. *Communications of the ACM*, 55(10), 78–87. doi:10.1145/2347736.2347755

Ehatisham-ul-Haq, M., Azam, M. A., Loo, J., Shuang, K., Islam, S., Naeem, U., & Amin, Y. (2017). Authentication of Smartphone Users Based on Activity Recognition and Mobile Sensing. *Sensors (Basel)*, 17(9), 2043. doi:10.3390/s17092043

Fridman, L., Weber, S., Greenstadt, R., & Kam, M. (2017). Active Authentication on Mobile Devices via Stylometry, Application Usage, Web Browsing, and GPS Location. *IEEE Systems Journal*, 11(2), 513–521. doi:10.1109/JSYST.2015.2472579

Gilles, L. (2014). Understanding Random Forest from Theory to Practice. *University of Liège*.

Goldstein, M., & Uchida, S. (2016). A comparative evaluation of unsupervised anomaly detection algorithms for multivariate data. *PLoS One*, 11(4). doi:10.1371/journal.pone.0152173

Gupta, B. B. (2018). Computer and cyber security: principles, algorithm, applications, and perspectives. Boca Raton, FL: CRC Press.

Gupta, B. B., & Agrawal, D. P. (Eds.). (2019). *Handbook of Research on Cloud Computing and Big Data Applications in IoT*. IGI Global. doi:10.4018/978-1-5225-8407-0

Gupta, B. B., Yamaguchi, S., & Agrawal, D. P. (2018). Advances in security and privacy of multimedia big data in mobile and cloud computing. *Multimedia Tools and Applications*, 77(7), 9203–9208. doi:10.1007/s11042-017-5301-x

Huertas, A., García, F. J., Gil, M., & Martínez, G. (2016). SeCoMan: A Semantic-Aware Policy Framework for Developing Privacy-Preserving and Context-Aware Smart Applications. *IEEE Systems Journal*, 10(3), 111–1124.

Huertas, A., Gil, M., García, F. J., & Martínez, G. (2014a). Precise: Privacy-aware recommender based on context information for cloud service environments. *IEEE Communications Magazine*, 52(8), 90–96. doi:10.1109/MCOM.2014.6871675

Huertas, A., Gil, M., García, F. J., & Martínez, G. (2014b). What Private Information Are You Disclosing? A Privacy-Preserving System Supervised by Yourself (pp. 1221–1228). Paris, France: IEEE Intl Conf on High Performance Computing and Communications.

Huertas A., Gil M., García F. J., Martínez G. (2016). MASTERY: A multicontext-aware system that preserves the users’ privacy. *NOMS IEEE/IFIP Network Operations and Management Symposium*, 523-528.

Huertas, A., Gil, M., García, F. J., & Martínez, G. (2017). Preserving patients’ privacy in health scenarios through a multicontext-aware system. *Annales des Télécommunications*, 72(9-10), 577–587. doi:10.1007/s12243-017-0582-7

Hyperplane, W. (2019). Retrieved October 29, 2019, from https://en.wikipedia.org/wiki/Hyperplane

Jararweh, Y., Alsmirat, M., Al-Ayyoub, M., Benkhelifa, E., Darabseh, A., Gupta, B., & Doulat, A. (2017). Software-defined system support for enabling ubiquitous mobile edge computing. *The Computer Journal*, 60(10), 1443–1457. doi:10.1093/comjnl/bxx019
