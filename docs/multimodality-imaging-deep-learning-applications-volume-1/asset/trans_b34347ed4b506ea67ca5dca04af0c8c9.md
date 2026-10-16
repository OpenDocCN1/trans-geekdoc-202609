
-   [肺癌](https://wiki.example.org/feynmans_learning_method)以小结节的形式出现，这些结节难以检测和诊断。本节讨论肺癌检测中的一个深度学习（DL）应用。

## 2.3.7.1  lung disease characterization

恶性肺癌的五年生存率低于10%，因此如果不及时诊断，就会危及生命。即使进行活检，小肺结节也很少是恶性的，而且CT-PET扫描无法可靠地区分它们。针对这一点，应用了两种DL模型进行肺癌分类，即CNN和DBN \[[55](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2bib55)\]。肺结节的形状可以初步判断其恶性程度。此外，内部组成（如液体、钙化和脂肪）也能提供线索。CT扫描来自1010名患者。结果见表 \[2.3](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2t3)。模型的处理流程见图 \[2.34](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2fig34)。

```markdown
| Parameter || CNN || DBN |
| --- | --- | --- |
| Sensitivity || 73.3% || 73.4% |
| Specificity || 78.7% || 82.2% |
```

**Table 2.3.** DL应用于肺癌检测的结果分析 \[[55](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2bib55)\].

![Figure 2.34. Characterization of CT lung cancer.](images/bk978-0-7503-2244-7ch2f34_online.jpg)

**Figure 2.34.** CT肺癌的特征化。

## 2.4 Discussion

计算系统的出现促使科学家开发算法，以模拟智能行为 \[[56](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2bib56)\]。早期的算法是基于命题逻辑的、针对特定任务的简单知识工具。因此，任务变更时，整个算法必须被适配。于是，对通用算法的需求出现，推动了机器学习（ML）的发展。ML是一个两阶段过程：第一阶段是特征挖掘，第二阶段是实际的统计模型用于特征表征和分割。然而，特征挖掘仍使用手工工具，因此仍是任务特定的，导致性能有限，难以实现广泛应用所需的泛化。这促使了基于深度学习（DL）的工具发展，这些工具是单阶段的，并内置特征挖掘能力。DL网络的深度使其能够学习图像中的更内在的模式关系。DL网络可以处理任何成像模态的图像，如超声、MRI、CT、X光等，从而能够更快速地实现DL模型的泛化和可扩展性，相比于其他智能方法。本章展示了心血管学、神经学、乳腺癌学、显微镜学、皮肤学、胃肠学和肺部成像等不同领域的应用。DL还被应用于脑室窝 \[[57](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2bib57)\]、白质分割 \[[58](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2bib58)\]、脂肪肝病检测 \[[59](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2bib59)\]、蛋白质结构预测 \[[66](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2bib66)–[74](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2bib74)\]、基因表达调控 \[[75](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2bib75)–[79](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2bib79)\]、蛋白质分类 \[[80](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2bib80)–[82](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2bib82)\]、异常分类 \[[83](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2bib83), [87](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2bib87)–[89](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2bib89)\] 和脑解码 \[[84](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2bib84)–[86](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2bib86)\]。

### 2.4.1 Graphics processing unit and open-source software for deep learning

深度学习模块包含数百万个训练参数。这些参数代表学习过程的记忆，并持续演变直至收敛。当前的多核CPU系统不适合DL计算。GPU提供了更好的替代方案。GPU拥有数千个核心，能够并行处理。因此，操作系统可以在多个滤波线程中调度数千项计算。GPU的速度比多核CPU快数十到数千倍，能更快实现收敛 \[[8](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2bib8)\]。

Python是DL开发者最常用和接受的编程语言。大多数DL包都是基于某种版本的Python，如TensorFlow \[[60](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2bib60)\]、Theano \[[61](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2bib61)\]、Keras \[[62](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2bib62)\]、CAFFE \[[63](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2bib63)\] 和 Torch \[[64](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2bib64)\]。Deeplearning4j \[[65](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2bib65)\] 源自Java编程语言，面向Java开发者。

**References**

\[1\] LeCun Y, Bengio Y and Hinton G 2006 Deep learning *Nature* [**521** 436–44](http://dx.doi.org/10.1038/nature14539)

\[2\] Ciregan D, Meier U and Schmidhuber J 2012 Multi-column deep neural networks for image classification *Computer Vision and Pattern Recognition* (Piscataway, NJ: IEEE) pp 3642–9

\[3\] Wawrzynski P 2015 Control policy with auto correlated noise in reinforcement learning for robotics *Int. J. Mach. Learn. Comput.* [**5** 91–5](http://dx.doi.org/10.7763/IJMLC.2015.V5.489)

\[4\] Mnih V, Kavukcuoglu K, Silver D, Graves A, Antonoglou I, Wierstra D and Riedmiller M 2013 Playing Atari with deep reinforcement learning, arXiv: [1312.5602](http://arxiv.org/abs/arXiv:1312.5602)

\[5\] Du T and Vijay K S 2009 Deep learning for natural language processing *Eecis. Udel Edu.* 1–7 [https://www.eecis.udel.edu/∼vijay/fall13/snlp/lit-survey/DeepLearning.pdf](https://www.eecis.udel.edu/~vijay/fall13/snlp/lit-survey/DeepLearning.pdf)

\[6\] Hadsell R, Erkan A, Sermanet P, Scoffier M, Muller U and LeCun Y 2008 Deep belief net learning in a long-range vision system for autonomous off-road driving *Proc. Intelligent Robots and Systems* pp 628–33

\[7\] Rosenblatt F 1958 The perceptron: a probabilistic model for information storage and organization in the brain *Psychol. Rev.* [**65** 386](http://dx.doi.org/10.1037/h0042519)

\[8\] Raina R, Madhavan A and Ng A Y 2009 Large-scale deep unsupervised learning using graphics processors *Proc. of the 26th Annual Int. Conf. on Machine Learning* (New York: ACM) pp 873–80

\[9\] Najafabadi M M, Villanustre F, Khoshgoftaar T M, Seliya N, Wald R and Muharemagic E 2015 Deep learning applications and challenges in big data analytics *J. Big Data* [**2** 1](http://dx.doi.org/10.1186/s40537-014-0007-7)

\[10\] McCulloch W S and Pitts W 1943 A logical calculus of ideas immanent in nervous activity *Bull. Math. Biophys.* [**5** 115–33](http://dx.doi.org/10.1007/BF02478259)

\[11\] Bebis G and Georgiopoulos M 1994 Feed-forward neural networks *IEEE Potentials* [**13** 27–31](http://dx.doi.org/10.1109/45.329294)

\[12\] Hopfield J J 1984 Neurons with graded response have collective computational properties like those of two-state neurons *Proc. Natl Acad. Sci. USA* [**81** 3088–92](http://dx.doi.org/10.1073/pnas.81.10.3088)

\[13\] Hinton G E 2009 Deep belief networks *Scholarpedia* [**4** 5947](http://dx.doi.org/10.4249/scholarpedia.5947)

\[14\] Smolensky P 1986 Information processing in dynamical systems: foundations of harmony theory *Research Paper* NO. CU-CS-321-86 Department of Computer Science, Colorado University at Boulder
