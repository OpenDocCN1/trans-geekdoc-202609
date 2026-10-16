
Lung cancer appears in the form of small nodules which are difficult to detect and diagnose. In this section we discuss one DL application of lung cancer detection.

## 2.3.7.1 Characterization of lung disease

Malignant lung cancer has a five-year survival rate of less than 10% and therefore is deadly if not diagnosed early. Lung cancer is difficult to detect even with biopsy, as small lung nodules are infrequently malignant. Also, they cannot be reliably categorized by CT-PET scans. In this regard two DL models were applied to lung cancer classification, i.e. CNN and DBN \[[55](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2bib55)\]. The shape of pulmonary nodules can give an initial characterization regarding their malignancy. Additionally, the internal composition, such as fluid, calcification, and fat, can provide an indication. CT scans were collected from 1010 patients. The results are given in table \[2.3](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2t3). The process of the model is shown in figure \[2.34](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2fig34).

```markdown
| Parameter || CNN || DBN |
| --- | --- | --- |
| Sensitivity || 73.3% || 73.4% |
| Specificity || 78.7% || 82.2% |
```

**Table 2.3.** Result analysis of the DL application for lung cancer detection \[[55](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2bib55)\].

![Figure 2.34. Characterization of CT lung cancer.](images/bk978-0-7503-2244-7ch2f34_online.jpg)

**Figure 2.34.** Characterization of CT lung cancer.

## 2.4 Discussion

The advent of computing systems led scientists to develop algorithms to emulate intelligent behavior \[[56](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2bib56)\]. The early algorithms were simple task-specific knowledge tools based on propositional calculus. Therefore, if the task changed the full algorithm had to be adapted. A demand for generalized algorithms for all tasks grew, which led to the development of ML. ML is a two-stage process where the first stage is feature mining and the second stage is the actual statistical model for characterization and segmentation. The issue remained the same since the feature were mined using manual tools and therefore were also task-specific. Thus the performance was limited and could not achieve the necessary generalization for widespread use. This led to the evolution of DL based tools which were single stage and had inbuilt feature mining capability. The depth of the DL networks allowed them to learn more intrinsic details of the pattern relationships. The DL network can mine images and perform characterization in any imaging modality, such as ultrasound, MR, CT, x-ray etc. Therefore, the generalization as well as scalability of the DL models can be achieved in a faster way than other intelligence methods. In this chapter we have displayed different applications in cardiography, neurology, mammography, microscopy, dermatology, gastroenterology, and lung imaging. DL has been also applied in brain lacunes \[[57](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2bib57)\], white matter segmentation \[[58](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2bib58)\], fatty liver disease detection \[[59](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2bib59)\], protein structure prediction \[[66](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2bib66)–[74](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2bib74)\], gene expression regulation \[[75](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2bib75)–[79](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2bib79)\], protein classification \[[80](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2bib80)–[82](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2bib82)\], anomaly classification \[[83](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2bib83), [87](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2bib87)–[89](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2bib89)\], and brain decoding \[[84](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2bib84)–[86](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2bib86)\].

### 2.4.1 Graphics processing unit and open-source software for deep learning

Deep learning modules consist of millions of parameters for training. These parameters represent the memory of the learning process and continuously evolve until convergence. The current multicore CPU systems are not suitable for DL computation. GPUs provide a better alternative. GPUs consist of thousands of cores capable of processing in parallel. Therefore, the operating system can schedule thousands of computations among these cores using multiple filter threads. The speed of GPUs is tens to thousands of times faster than that of multicore CPUs and can achieve convergence faster \[[8](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2bib8)\].

Python is the most accepted and popular programming language for DL application developers. Most packages for DL are derived from some version of Python, such as TensorFlow \[[60](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2bib60)\], Theano \[[61](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2bib61)\], Keras \[[62](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2bib62)\], CAFFE \[[63](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2bib63)\], and Torch \[[64](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2bib64)\]. Deeplearning4j \[[65](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2bib65)\] is derived from the Java programming language for Java developers.

### References

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
