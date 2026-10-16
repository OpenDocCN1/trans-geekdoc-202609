
[92] 窦 Q、陈 H、Yu L、Zhao L、Qin J、Wang D、Mok V C T、Shi L 和 Heng P-A 2016 利用 3D 卷积神经网络自动检测脑部微出血 *IEEE Trans. Med. Imaging* [**35** 1182–95](http://dx.doi.org/10.1109/TMI.2016.2528129)

[93] Cruz-Roa A、Basavanhally A、González F、Gilmore H、Feldman M、Ganesan S、Shih N、Tomaszewski J 和 Madabhushi A 2014 利用卷积神经网络自动检测侵袭性乳腺癌 *Proc. SPIE* [**9041** 904103](http://dx.doi.org/10.1117/12.2043872)

[94] Roth H R、Lu L、Seff A、Cherry K M、Hoffman J、Wang S、Liu J、Turkbey E 和 Summers R M 2014 采用深度卷积神经网络观测集的新型 2.5 D 表示法进行淋巴结检测 *Int. Conf. on Medical Image Computing and Computer-Assisted Intervention* (Cham: Springer) pp 520–7

[95] Wang D、Khosla A、Gargeya R、Irshad H 和 Beck A H 2016 深度学习在转移性乳腺癌中的识别 *arXiv:*[1606.05718](http://arxiv.org/abs/arXiv:1606.05718)

[96] IBM Research 2013 IBM 研究加速发现：医学影像分析 *YouTube* 10 月 10 日 [https://youtube.com/watch?v=0i11VCNacAE](https://youtube.com/watch?v=0i11VCNacAE)

[97] Bos L 2005  telemedicine 的经济影响：综述 *Med. Care Compunetics* **2** 140

[98] 2016 计算机辅助检测市场到 2022 年将达 19 亿美元 *Grand View Research* 8/2016 [http://grandviewresearch.com/press-release/global-computer-aided-detection-market](http://www.grandviewresearch.com/press-release/global-computer-aided-detection-market)

[99] Liew C 2018 放射学与人工智能的未来：成功策略 *Eur. J. Radiol.* [**102** 152–6](http://dx.doi.org/10.1016/j.ejrad.2018.03.019)

[100] Nagar Y、Malone T W、De Boer P 和 Garcia A C B 2016 集体智能论文集 *PhD Thesis* Massachusetts Institute of Technology, Cambridge, MA

[101] Kremer M 1993 经济发展的 O 环理论 *Q. J. Econ.* [**108** 551–75](http://dx.doi.org/10.2307/2118400)

[102] [https://www.enlitic.com/ai-in-radiology/](https://www.enlitic.com/ai-in-radiology/)

[103] Cooke R E Jr、Gaeta M G、Kaufman D M 和 Henrici J G 2003 图像存档和通信系统 *US Patent* 6574629

[104] Vapnik V N 1999 统计学学习理论概述 *IEEE Trans. Neural Netw.* [**10** 988–99](http://dx.doi.org/10.1109/72.788640)

[105] Vincent P、Larochelle H、Lajoie I、Bengio Y 和 Manzagol P-A 2010 堆叠去噪自编码器：在深度网络中通过局部去噪标准学习有用表示 *J. Mach. Learn. Res.* **11** 3371–408

[106] Cireşan D C、Giusti A、Gambardella L M 和 Schmidhuber J 2013 利用深度神经网络在乳腺癌病理切片图像中检测有丝分裂 *Int. Conf. on Medical Image Computing and Computer-assisted Intervention* (Berlin: Springer) pp 411–8

[107] Sirinukunwattana K、Shan E、Raza A、Tsang Y-W、Snead D R J、Cree I A 和 Rajpoot N M 2016 局部感受野深度学习用于常规结肠癌病理切片中细胞核的检测和分类 *IEEE Trans. Med. Imaging* [**35** 1196–206](http://dx.doi.org/10.1109/TMI.2016.2525803)

[108] Wang H、Roa A C、Basavanhally A N、Gilmore H L、Shih N、Feldman M、Tomaszewski J、Gonzalez F 和 Madabhushi A 2014 通过手工特征与卷积神经网络特征相结合，在乳腺癌病理切片图像中检测有丝分裂 *J. Med. Imaging* [**1** 034003](http://dx.doi.org/10.1117/1.JMI.1.3.034003)

[109] Molteni M 2017 如果你从事 X 光片或痣的观察，人工智能正在抢走你的工作 *Wired* [https://wired.com/2017/01/look-x-rays-moles-living-ai-coming-job/](https://wired.com/2017/01/look-x-rays-moles-living-ai-coming-job/)

[110] Saba L *et al* 2019 深度学习在放射学中的现状与未来 *Eur. J. Radiol.* [**14** 14–24](http://dx.doi.org/10.1016/j.ejrad.2019.02.038)

* * *

# **IOP** Publishing

# Multimodality Imaging, Volume 1

# Deep learning applications

# Mainak Biswas and Jasjit S Suri

* * *

# Chapter 2

## Deep learning in biomedical imaging

# Mainak Biswas and Jasjit S Suri

In the last few decades, deep learning (DL) and allied artificial intelligence (AI) technologies have taken the world by storm with driverless cars, self-recovery and reusable rockets, intelligent chatbots etc. The core of DL is the networked computing neurons, similar to the brain’s visual cortex and also functioning like it, i.e. recognizing patterns. The depth of the DL network allows the identification of complex relationships within data. Open-source software and the reduction in the cost of hardware such as GPUs has led to faster implementation of these DL based modules.

This review chapter is dedicated to studying the different DL models available in biomedical imaging and their applications in the cardiovascular, neurological, mammography, microscopy, dermatology, pulmonary, and gastroenterology fields. This chapter also discusses the reasons for this paradigm shift in automated computer-aided diagnosis. Our special focus is on the availability of different open-source software and their uses. Several complications in this paradigm shift and the benefits to users are also discussed in detail.

### 2.1 Introduction

The computational approach to the primary human function of learning and its application has come to full circle through deep learning (DL) \[[1](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2bib1)\]. As currently understood, DL has already made inroads into image processing \[[2](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2bib2)\], driverless cars \[[6](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2bib6)\], thinking and judging robots \[[3](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2bib3)\], the gaming industry \[[4](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2bib4)\], language processing \[[5](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2bib5)\] etc. The DL models are highly popular and are used every day to build real-life technologies never thought possible outside the laboratory environment. This is due to their robust and better performance with respect to conventional algorithms. In fact, the advent of Big Data has led to greater emphasis on DL based technologies as the performance of conventional automated algorithms remained static \[[7](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2bib7)\]. DL applications have been further propelled by multicore CPU architectures and the dawn of graphical-processing units (GPUs) allowing a high degree of parallel computations, leading to faster convergence. The identification of patterns by the brain can be ascribed to the functioning of the multi-layered neural network of the visual cortex (VC) \[[8](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2bib8)\]. This functioning was adopted in the form of McCulloch Pitt’s neural model consisting of a single neuron \[[9](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2bib9)\]. This led to the development of multiple neural models based on different parameters, such as learning function, number of hidden layers, activation functions etc. Some of the famous models are the perceptron \[[10](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2bib10)\], feed-forward neural networks \[[11](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2bib11)\], and feedback neural networks \[[12](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2bib12)\]. The earlier neural networks were singular, or included one hidden layer. The DL models, in contrast, use multiple layers (hidden) to increase the depth of the network for robustness and better results.
