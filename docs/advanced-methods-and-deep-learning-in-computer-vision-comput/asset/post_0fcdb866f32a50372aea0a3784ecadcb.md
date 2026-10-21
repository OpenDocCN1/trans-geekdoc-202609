
## TABLE 4.3 Summarized results on Pixel1 phone (Cai et al., 2020a). The first group corresponds to human-designed CNN models. The second group corresponds to conventional NAS. The third group corresponds to hardware-aware NAS. The final group corresponds to OFA. “#75” indicates that the specialized subnetworks are fine-tuned for 75 epochs after grabbing weights from the OFA network. “CO2e” denotes CO2 emission which is calculated based on (Strubell et al., 2019). AWS cost is calculated based on the price of Amazon AWS on-demand P3.16x large instances.

| Network | ImageNet Top1 (%) | MACs | Mobile latency | Search cost (GPU hours) | Training cost (GPU hours) | GPU hours | CO2e (lbs) | AWS cost |
|---|---|---|---|---|---|---|---|---|
| MobileNetV2 (Sandler et al., 2018) | 72.0 | 300M | 66 ms | 0 | 150× | 6k | 1.7k | $18.4k |
| MobileNetV2 #1200 | 73.5 | 300M | 66 ms | 0 | 1200× | 48k | 13.6k | $146.9k |
| NASNet-A (Zoph et al., 2017) | 74.0 | 564M | – | 48,000× | – | 1920k | 544.5k | $5875.2k |
| DARTS (Liu et al., 2018b) | 73.1 | 595M | – | 96× | 250× | 14k | 4.0k | $42.8k |
| MnasNet (Tan et al., 2018) | 74.0 | 317M | 70 ms | 40,000× | – | 1600k | 453.8k | $4896.0k |
| FBNet-C (Wu et al., 2019) | 74.9 | 375M | – | 216× | 360× | 23k | 6.5k | $70.4k |
| ProxylessNAS (Cai et al., 2019) | 74.6 | 320M | 71 ms | 200× | 300× | 20k | 5.7k | $61.2k |
| SinglePathNAS (Guo et al., 2019) | 74.7 | 328M | – | 288 + 24× | 384× | 17k | 4.8k | $52.0k |
| AutoSlim (Yu and Autoslim, 2019) | 74.2 | 305M | 63 ms | 180 | 300× | 12k | 3.4k | $36.7k |
| MobileNetV3-Large (Howard et al., 2019) | 75.2 | 219M | 58 ms | – | 180× | 7.2k | 1.8k | $22.2k |
| OFA | 76.0 | 230M | 58 ms | 40 | 1200 | 1.2k | 0.34k | $3.7k |
| OFA #75 | 76.9 | 230M | 58 ms | 40 | 1200 + 75× | 4.2k | 1.2k | $13.0k |
| OFA_Large #75 | 80.0 | 595M | – | 40 | 1200 + 75× | 4.2k | 1.2k | $13.0k |

Lebedev, Vadim, Ganin, Yaroslav, Rakhuba, Maksim, Oseledets, Ivan, Lempitsky, Victor, 2014. Speeding-up convolutional neural networks using fine-tuned cp-decomposition. arXiv preprint. arXiv:1412.6553.

Lebedev, Vadim, Lempitsky, Victor, 2016. Fast convnets using group-wise brain damage. In: Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition, pp. 2554–2564.

LeCun, Yann, Cortes, Corinna, Burges, Christopher JC, 2010. Mnist handwritten digit database. AT&T Labs [Online]. Available: http://yann.lecun.com/exdb/mnist.

LeCun, Yann, Denker, John S., Solla, Sara A., Howard, Richard E., Jackel, Lawrence D., 1989. Optimal brain damage. In: NIPS, vol. 2, pp. 598–605.

Li, Fengfu, Zhang, Bo, Liu, Bin, 2016a. Ternary weight networks. arXiv preprint. arXiv:1605.04711.

Li, Hao, Kadav, Asim, Durdanovic, Igor, Samet, Hanan, Graf, Hans Peter, 2016b. Pruning filters for efficient convnets. arXiv preprint. arXiv:1608.08710.

Li, Muyang, Lin, Ji, Ding, Yaoyao, Liu, Zhijian, Zhu, Jun-Yan, Han, Song, 2020. Gan compression: efficient architectures for interactive conditional gans. In: Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition, pp. 5284–5294.

Lillicrap, Timothy P., Hunt, Jonathan J., Pritzel, Alexander, Heess, Nicolas, Erez, Tom, Tassa, Yuval, Silver, David, Wierstra, Daan, 2015. Continuous control with deep reinforcement learning. arXiv preprint. arXiv:1509.02971.

Lin, Ji, Rao, Yongming, Lu, Jiwen, 2017. Runtime neural pruning. In: NeurIPS.

Lin, Zhouhan, Courbariaux, Matthieu, Memisevic, Roland, Bengio, Yoshua, 2015. Neural networks with few multiplications. arXiv preprint. arXiv:1510.03009.

Liu, Chenxi, Chen, Liang-Chieh, Schroff, Florian, Adam, Hartwig, Hua, Wei, Yuille, Alan L., Li, Fei-Fei, 2019. Hierarchical neural architecture search for semantic image segmentation. In: Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition, pp. 82–92.

Liu, Chenxi, Zoph, Barret, Neumann, Maxim, Shlens, Jonathon, Hua, Wei, Li, Li-Jia, Li, Fei-Fei, Yuille, Alan, Huang, Jonathan, Murphy, Kevin, 2018. Progressive neural architecture search. In: Proceedings of the European Conference on Computer Vision (ECCV), pp. 19–34.

Liu, Chenxi, Zoph, Barret, Shlens, Jonathon, Li, Li-Jia, Li, Fei-Fei, Yuille, Alan, Huang, Jonathan, Murphy, Kevin, 2017. Progressive neural architecture search. arXiv preprint. arXiv:1712.00559.

Liu, Hanxiao, Simonyan, Karen, Vinyals, Oriol, Fernando, Chrisantha, Kavukcuoglu, Koray, 2018a. Hierarchical representations for efficient architecture search. In: ICLR.

Liu, Hanxiao, Simonyan, Karen, Yang, Yiming, 2018b. Differentiable architecture search. arXiv preprint. arXiv:1806.09055.

Liu, Yifan, Chen, Ke, Liu, Chris, Qin, Zengchang, Luo, Zhenbo, Wang, Jingdong, 2019a. Structured knowledge distillation for semantic segmentation. In: Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition, pp. 2604–2613.

Liu, Zechun, Mu, Haoyuan, Zhang, Xiangyu, Guo, Zichao, Yang, Xin, Cheng, Kwang-Ting, Sun, Jian, 2019b. Meta learning for automatic neural network channel pruning. In: Proceedings of the IEEE International Conference on Computer Vision, pp. 3296–3305.

Ma, Ningning, Zhang, Xiangyu, Zheng, Hai-Tao, Sun, Jian, 2018. Shufflenet v2: practical guidelines for efficient cnn architecture design. In: ECCV.

Ma, Xiaolong, Guo, Wei, Niu, Fu-Ming, Lin, Xue, Tang, Jian, Ma, Kaisheng, Ren, Bin, Wang, Yanzhi, 2020. The missing but desirable sparsity in dnn weight pruning for real-time execution on mobile devices. In: AAAI, pp. 5117–5124.

Mao, Huizi, Han, Song, Pool, Jeff, Li, Wenshuo, Liu, Xingyu, Wang, Yu, Dally, William J., 2017. Exploring the granularity of sparsity in convolutional neural networks. In: Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition Workshops, pp. 13–20.

Molchanov, Pavlo, Tyree, Stephen, Karras, Tero, Aila, Timo, Kautz, Jan, 2016. Pruning convolutional neural networks for resource efficient transfer learning. CoRR. arXiv:1611.06440 [abs].

Molchanov, Pavlo, Tyree, Stephen, Karras, Tero, Aila, Timo, Kautz, Jan, 2017. Pruning convolutional neural networks for resource efficient transfer learning. In: International Conference on Learning Representations.

Nagel, Markus, van Baalen, Mart, Blankevoort, Tijmen, Welling, Max, 2019. Data-free quantization through weight equalization and bias correction. In: Proceedings of the IEEE International Conference on Computer Vision, pp. 1325–1334.

Niu, Wei, Ma, Xiaolong, Lin, Sheng, Wang, Shihao, Qian, Xuehai, Lin, Xue, Wang, Yanzhi, Ren, Bin, 2020. Achieving real-time dnn execution on mobile devices with pattern-based weight pruning. In Proceedings of the Twenty-Fifth International Conference on Architectural Support for Programming Languages and Operating Systems, pp. 907–922.

Pham, Hieu, Guan, Melody Y., Zoph, Barret, Le, Quoc V., Dean, Jeff, 2018. Efficient neural architecture search via parameter sharing. In: ICML.

Ramachandran, Prajit, Zoph, Barret, Le, Quoc V., 2017. Searching for activation functions. arXiv preprint. arXiv:1710.05941.

Rastegari, Mohammad, Ordonez, Vicente, Redmon, Joseph, Farhadi, Ali, 2016. Imagenet classification using binary convolutional neural networks. In European Conference on Computer Vision. Springer, pp. 525–542.

Real, Esteban, Aggarwal, Alok, Huang, Yining, Le, Quoc V., 2018. Regularized evolution for image classifier architecture search. arXiv preprint. arXiv:1802.01548.

Romero, Adriana, Ballas, Nicolas, Ebrahimi Kahou, Samira, Chassang, Antoine, Gatta, Carlo, Bengio, Yoshua, 2014. Fitnets: hints for thin deep nets. arXiv preprint. arXiv:1412.6550.

Sandler, Mark, Howard, Andrew, Zhu, Menglong, Zhmoginov, Andrey, Chen, Liang-Chieh, 2018. Mobilenetv2: inverted residuals and linear bottlenecks. In: Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition, pp. 4510–4520.

Sanh, Victor, Debut, Lysandre, Chaumond, Julien, Wolf, Thomas, 2019. Distilbert, a distilled version of bert: smaller, faster, cheaper and lighter. arXiv preprint. arXiv:1910.01108.

Sharify, Sayeh, Delmas Lascorz, Alberto, Siu, Kevin, Judd, Patrick, Moshovos, Andreas, 2018. Exploiting weight and activation precisions to accelerate convolutional neural networks. In: DAC.

Sharma, Hardik, Park, Jongse, Suda, Naveen, Lai, Liangzhen, Chau, Benson, Chindada, Vikas, Esmailzadeh, Hadi, 2018. Bit fusion: bit-level dynamically composable architecture for accelerating deep neural networks. In: Proceedings of the 45th Annual International Symposium on Computer Architecture. IEEE Press, pp. 764–775.

Simonyan, Karen, Zisserman, Andrew, 2014. Very deep convolutional networks for large-scale image recognition. arXiv preprint. arXiv:1409.1556.

Srinivas, Suraj, Babu, R. Venkatesh, 2015. Data-free parameter pruning for deep neural networks. arXiv preprint. arXiv:1507.06149.

Strubell, Emma, Ganesh, Ananya, Mccallum, Andrew, 2019. Energy and policy considerations for deep learning in nlp. In: ACL.

Szegedy, Christian, Liu, Wei, Jia, Yangqing, Sermanet, Pierre, Reed, Scott, Anguelov, Dragomir, Erhan, Dumitru, Vanhoucke, Vincent, Rabinovich, Andrew, 2015. Going deeper with convolutions. In: Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition, pp. 1–9.

Szegedy, Christian, Vanhoucke, Vincent, Ioffe, Sergey, Shlens, Jon, Wojna, Zbigniew, 2016. Rethinking the inception architecture for computer vision. In: CVPR.

Tan, Mingxing, Chen, Bo, Pang, Ruoming, Vasudevan, Vijay, Le, Quoc V., 2018. Platform-aware neural architecture search for mobile. arXiv preprint. arXiv:1807.11626.

Tan, Mingxing, Pang, Ruoming, Le, Quoc V., 2020a. Scalable and efficient object detection. In: Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition, pp. 10781–10790.

Tan, Zhanhong, Song, Jiebo, Ma, Xiaolong, Tan, Sia-Huat, Chen, Hongyang, Miao, Yuqing, Wu, Yifu, Ye, Shaokai, Wang, Yanxi, Li, Dehui, et al., 2020b. Pcn: pattern-based fine-grained regular pruning towards optimizing cnn accelerators. arXiv preprint. arXiv:2002.04997.

Ummuroglu, Yaman, Rasnayake, Lahiru, Sjölinder, Magnus, 2018. A scalable bit-serial matrix multiplication overlay for reconfigurable computing. In: FPL.

Vanhoucke, Vincent, Senior, Andrew, Mao, Mark Z., 2011. Improving the Speed of Neural Networks on Cpus. In: Proc. Deep Learning and Unsupervised Feature Learning NIPS Workshop. In: Citeseer, vol. 1, p. 4.

Wang, Kuan, Liu, Zhijian, Lin, Yujun, Lin, Ji, Han, Song, 2018. Hardware-aware automated quantization. arXiv preprint. arXiv:1811.08886.

Wen, Wei, Wu, Chunpeng, Wang, Yandan, Chen, Yiran, Li, Hai, 2016. Learning structured sparsity in deep neural networks. In: Advances in Neural Information Processing Systems, pp. 2074–2082.

Wu, Bichen, Dai, Xiaoliang, Zhang, Peizhao, Wang, Yanghan, Sun, Fei, Wu, Yiming, Tian, Yuandong, Vajda, Peter, Jia, Yangqing, Keutzer, Kurt, 2019. Hardware-aware efficient convnet design via differentiable neural architecture search. In: Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition, pp. 10734–10742.
