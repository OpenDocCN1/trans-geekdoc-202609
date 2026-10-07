
# Stochastic-binary convolutional neural networks 93

[6] J. Li, A. Ren, Z. Li, et al. Towards Acceleration of Deep Convolutional Networks using Stochastic Computing. In 2017 22nd ASP-DAC, pages 115–120, January 2017.

[7] H. Sim, D. Nguyen, J. Lee, and K. Choi. Scalable Stochastic Computing Accelerator for Convolutional Neural Networks. In 2017 22nd Asia and South Pacific Design Automation Conference (ASP-DAC), January 2017.

[8] H. Sim and J. Lee. New Stochastic Computing Multiplier with Application to Deep Convolutional Neural Networks. In 2017 54th ACM/EDAC/IEEE Design Automation Conference (DAC), June 2017.

[9] Z. Li, A. Ren, J. Li, et al. Structural Design Optimization for Deep Convolutional Neural Networks using Stochastic Computing. In Design, Automation Test in Europe Conference Exhibition (DATE), 2017, pages 250–253, March 2017.

[10] A. Ren, Z. Li, C. Ding, et al. SC-DCNN: Highly-Scalable Deep Convolutional Neural Network using Stochastic Computing. In ASPL’17, New York, USA, 2017.

[11] A. Arkdakani, F. Leduc-Prime, N. Onizawa, T. Hanyu, and W. J. Gross, VLSI implementation of deep neural network using integral stochastic computing. IEEE Transactions on VLSI Systems, 25(10):2688–2699, 2017.

[12] R. Rojabr, K. Gavaki, S. M. Reza Tayarian, et al. SkippyNN: An Embedded-Stochastic-Computing Accelerator for Convolutional Neural Networks. In Design Automation Conference (DAC), 2019.

[13] B. Li, Y. Qin, Yuan, and D. Lilja. Neural network classifiers for a hardware-based approximate activation function with a hybrid stochastic multiplier. ACM Journal on Emerging Technologies in Computing Systems, 15(1):12–1:19, 2019.

[14] B. Li, M. H. Hajafi, and D. Lilja. Low-Cost Stochastic Hybrid Multiplier for Quantized Neural Networks. ACM Journal on Emerging Technologies in Computing Systems, 15(2):18–1:19, 2019.

[15] B. Li, M. H. Hajafi, B. Yuan, and D. J. Lilja. Quantized Neural Networks With New Stochastic Multipliers. In 2018 19th International Symposium on Quality Electronic Design (ISED), pages 376–382, March 2018.

[16] H. Sim, S. Khezgolov, and J. Lee. DPS: Dynamic Precision Scaling for Stochastic Computing-based Deep Neural Networks. In Proceedings of the 55th Annual Design Automation Conference, DAC’18, pages 13:1–13:6, New York, USA, ACM.

[17] A. Zakatayev, S. Lee, H. Sim, and J. Lee. Sign-Magnitude SC: Getting 10x Accuracy for Free Stochastic for Deep Neural Networks. In Proceedings of the 55th Annual Design Automation Conference, DAC’18, pages 158:1–158:6, New York, USA, 2018. ACM.

[18] D. Jensen and M. Riedel. A Deterministic Approach to Stochastic Computation. In Proceedings of the 35th International Conference on Computer-Aided Design, ICCAD’16, New York, USA, 2016.

[19] M. H. Hajafi, S. Jamali-Zavarchh, D. J. Lilja, M. D. Riedel, K. Bazargon, and R. Harjani. Time-encoded values for highly efficient stochastic circuits. IEEE Transactions on Very Large Scale Integration (VLSI Systems), 25(5):1644–1657, 2017.

[20] M. H. Najafi, S. Jamali-Zavareh, D. J. Lilja, M. D. Riedel, K. Bazargan, and R. Harjani. Overview of time-based computing with stochastic constructs. IEEE Micro, 37(6):62–71, 2017.

[21] S. R. Faraji and K. Bazargan. Hybrid Binary-Unary Hardware Accelerators. In 2019 24th Asia and South Pacific Design Automation Conference (ASP-DAC).

[22] M. H. Najafi and D. J. Lilja. High-sampling for deterministic approaches to stochastic computing. IEEE Transactions on Emerging Topics in Computing, 1, 2018.

[23] M. H. Najafi, D. J. Lilja, and M. Riedel. Deterministic Methods for Stochastic Computing Using Low-discrepancy Sequences. In Proceedings of the International Conference on Computer-Aided Design, ICCAD’18, 51:1–58, New York, USA, ACM.

[24] A. Alaghi and P. Hayes. Fast and Accurate Stochastic Circuits. In Proceedings of the Conference on Design, Automation in Europe, DATE’14, Belgium, 2014.

[25] S. Liu and Han. Energy Efficient Stochastic Computing with Sobol Sequences. In Design, Automation in Europe Conference Exhibition (DATE), pages 650–653, March 2017.

[26] S. Liu and Han. Toward energy-efficient stochastic circuits with parallel sobol sequences. IEEE Transactions on Very Large Scale Integration (VLSI) Systems, 26(7):1326–1339, 2018.

[27] B. D. Brown and C. Stochastic neural computation I. IEEE Transactions on, 50(9):891–905, 2001.

[28] K. Sanni, G. Garreau, J. Molin, and A. Andreov. FPGA Implementation of a Deep Belief Network Architecture for Character Recognition using Stochastic Computation. In 2019 Annual Conference on Information Sciences and Systems (CISS), pages 1–5, March 2019.

[29] Y. Ji, F. Ran, C. Ma, and D. J. Lilja. A Hardware Implementation of a Radial Function Neural Network using Stochastic Logic. In Design, Automation in Europe Conference & Exhibition, DATE’15, pages 880–883, San Jose, USA, 2015. EDA Consortium.

[30] B. Li, M. H. Najafi, and D. J. Lilja. Stochastic Computing to Reduce the Hardware Requirements for a Restricted Boltzmann Machine. In Proceedings of the 2016 ACM/SIGDA International Symposium on Field-Programmable Gate Arrays, FPGA’16, pages 36–41, New York, USA, 2016. ACM.

[31] B. Li, J. Hu, M. H. Najafi, S. Koester, and D. Lilja. Low Cost Hybrid CMOS Processor for Stochastic Neural Networks. In 2019 International Great Lakes Symposium on VLSI (GLSI), May 2019.

[32] Y. Lecun, L. Bottou, U. Bengio, and P. Haffner. Gradient-based learning applied to document recognition. Proceedings of the IEEE, 86(11):2278–2324, 1998.

# Chapter 5 Binary neural networks
Najmeh Nazari and Mostafa E. Salehi¹

Convolutional neural networks (CNNs) are used in a spread spectrum of machine learning applications, such as computer vision and speech recognition. Computation and memory accesses are the major challenges for CNNs in resource-limited and low-power embedded systems. The recently proposed binary neural networks (BNNs) use just 1 bit for weights and/or activations instead of full-precision values, hence substitute complex-accumulation operations with bitwise logic operations to reduce the computation and memory footprint drastically. However, most B models come with some accuracy loss, especially in big datasets. Improving the accuracy of BNNs and designing efficient hardware accelerator for them are two important research directions that have attracted many attentions in recent years. In this chapter, we conduct a survey on the state-of-the-art researches on the design and hardware implementation of the BNN models.

# 5.1 Introduction

Due to the promotion of high-performance computer architectures, deep learning has rapidly grown to an extent that exceeds the human accuracy level [1]. A particular model of deep neural networks (DNNs) is the convolutional neural network (CNN) model that attained noticeable results in several computer vision tasks, such as image classification [2], and object localization and detection [3].

CNN models were primarily designed with the aim of increasing accuracy. In fact, CNN models are continuously becoming more and more complicated and deeper to achieve more accuracy. For instance, the ResNet network exploits 50 layers and uses 25.5M of parameters and performs 9G multiply-accumulate (MAC) operations [4] for achieving 94.7% top-5 classification accuracy on the ImageNet dataset. According to state-of-the-art researches, as CNNs go deeper and larger, they give higher accuracy, but at the cost of higher complexity. For instance, in [1], He al have explored the deep model of ResNet with 1,202 layers to give very high accuracy, but obviously, the model suffers from high computation and memory bandwidth demand. In almost all other CNN models, the massive computations and the huge amount of memory accesses are the major challenges of deep CNNs.

¹School of Electrical and Computer Engineering, College of Engineering, University of Tehran, Tehran, Iran
