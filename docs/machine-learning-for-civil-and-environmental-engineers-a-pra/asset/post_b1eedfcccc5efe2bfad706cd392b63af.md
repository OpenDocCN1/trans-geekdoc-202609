
- 59 Henderson, P., Hu, J., Romoff, J. et al. (2020). Towards the systematic reporting of the energy and carbon footprints of machine learning. J. Mach. Learn. Res. 21.
- 60 Lacoste, A., Luccioni, A., Schmidt, V., and Dandres, T. (2019). Quantifying the carbon emissions of machine learning. (accessed 10 June 2022) https://mlco2.github.
- 61 Canziani, A., Paszke, A., and Culurciello, E. (2016). An analysis of deep neural network models for practical applications. doi: 10.48550/arxiv.1605.07678.
- 62 Dalgrem, A. and Lundegård, Y. (2019). GreenML: a methodology for fair evaluation of machine learning algorithms with respect to resource consumption. Linköpings universitet. https://www.diva-portal.org/smash/record.jsf?pid=diva2%3A13145 249&dswid=-9453 (accessed 8 June 2022).
- 63 Naser, M.Z. (2022). CLEMSON: an automated machine learning (AutoML) virtual assistant for accelerated, simulation-free, transparent, reduced-Order and inference-Based reconstruction of fire response of structural members. ASCE J. Struct. Eng. 148. doi: 10.1061/(ASCE)ST.1943-541X.0003399.
- 64 Bhaskar, H., Hoyle, D.C., and Singh, S. (2006). Machine learning in bioinformatics: a brief survey and recommendations for practitioners. Comput. Biol. Med. doi: 10.1016/j.compbiomed.2005.09.002.
- 65 Kohavi, R. (1995). A study of cross-validation and bootstrap for accuracy estimation and model selection. International Joint Conference on Artificial Intelligence IJCAI. Vol. 2.
- 66 O’Neil, C. (2016). Weapons of Math Destruction: How Big Data Increases Inequality and Threatens Democracy. Crown.
- 67 Franssen, J.M. and Gernay, T. (2017). Modeling structures in fire with SAFIR®: theoretical background and capabilities. J. Struct. Fire Eng. 8. doi: 10.1108/JSFE-07-2016-0010.
- 68 Ferreira, J., Gernay, T., Franssen, J., and Vassant, O. (2018). Discussion on a systematic approach to validation of software for structures in fire. SiF 2018: 10th international conference on structures in fire. http://hdl.handle.net/2268/223208 (accessed 1 April 2020).
- 69 Ohnkne, P.C. (2013). ANSYS. © ANSYS, Inc.
- 70 Abaqus 6.13, Abaqus 6.13 (2013). Anal. User’s Guid. Dassault Syst.
- 71 Botchkarev, A. (2019). A new typology design of performance metrics to measure errors in machine learning regression algorithms. Interdiscip. J. Inform. Knowl. Manag. 14: 045–076. doi: 10.28945/4184.
- 72 Naser, M.Z. and Alavi, A.H. (2021). Error metrics and performance fitness indicators for artificial intelligence and machine learning in engineering and sciences. Archit. Struct. Constr. 1: 1–19. doi: 10.1007/S44150-021-00015-8.
- 73 Tibshirani, R., Walther, G., and Hastie, T. (2002). Estimating the number of clusters in a data set via the gap statistic. J. R. Stat. Soc. Ser. B: Stat. Methodol. 63. doi: 10.1111/1467-9868.00293.
- 74 Strubell, E., Ganesh, A., and McCallum, A. (2020). Energy and policy considerations for modern deep learning research. Proceedings of the AAAI Conference on Artificial Intelligence. doi: 10.1609/aaai.v34i09.7123.
- 75 Jackson, R. (2019). A roadmap to reducing greenhouse gas emissions 50 percent by 2030. https://earth.stanford.edu/news/roadmap-reducing-greenhouse-gas-emissions-50-percent-2030#gs.zj3zf.
- 76 García-Martín, E., Rodrigues, C.F., Riley, G., and Grahn, H. (2019). Estimation of energy consumption in machine learning. J. Parallel. Distrib. Comput. 134. doi: 10.1016/j.jpdc.2019.07.007.
- 77 Yang, T.J., Chen, Y.H., Emer, J., and Sze, V. (2017). A method to estimate the energy consumption of deep neural networks. 2017 51st Asilomar Conference on Signals, Systems, and Computers. doi: 10.1109/ACSSC.2017.8335698.
- 78 Schwartz, R., Dodge, J., Smith, N.A., and Etzioni, O. (2020). Green AI. Commun. ACM. doi: 10.1145/3381831.
- 79 Kodur, V. and Naser, M.Z. (2020). Structural Fire Engineering, 1e. McGraw Hill Professional.
- 80 Buchanan, A. and Abu, A. (2017). Structural Design for Fire Safety. Wiley. 440. ISBN-10: 9780470972892.
- 81 Parker, P.A. (2020). Statistical intervals: a guide for practitioners and researchers. J. Qual. Technol. 52. doi: 10.1080/00224065.2019.1584508.
- 82 Raschka, S. (2018). Model evaluation, model selection, and algorithm selection in machine learning. ArXiv. doi: 10.48550/arXiv.1811.12808.

## 6 Coding-free and Coding-based Approaches to Machine Learning

> > You take the blue pill, the story ends, you wake up in your bed and believe whatever you want to believe. You take the red pill, you stay in wonderland, and I show you how deep the rabbit hole goes.
> 
> Morpheus (The Matrix, 1999)

### Synopsis

A few chapters ago, I took the liberty of outlining my thoughts on why a good component of the inertia against ML lies in our lack of coding/programming in our curriculum.¹ It felt more beneficial to find some solutions that do not require us to change our domain abruptly. The simplest of all solutions was to adopt a coding-free approach to ML where engineers with limited knowledge/resources of programming can still leverage the full potential of ML without the need to resort to traditional coding. Thus, this chapter offers a look into the two main approaches to practicing ML, coding-free and coding-based. In this journey, we will go over a few platforms that I found most suitable for engineers, and especially students, to implement and use. All of the presented platforms offer free services to engineering students and hence are adopted in this chapter.² Along the way, we will cover the origins and capabilities of such platforms. Toward the end of this chapter, we will cover the use of Python and R as representatives of coding-based approaches. In all cases, I have supplemented my discussions with a series of examples and tutorials.³ I have listed and appended these here for you to practice along the way.

### 6.1 Coding-free Approach to ML

An instinctive way to start this chapter is by showcasing the traditional approach to ML in which a user codes or programs an executable script. However, I find it to be more exciting to start this chapter with a look into the new approach to ML. In this approach, coding is no longer required to build ML models.⁴ Similarly, this approach negates the need for specialized software/hardware infrastructure needed to carry out ML modeling and analysis. It only requires access to an online coding-free platform!

1 Quick story: My good friend, Sami Hasasneh, used to say; if you are ever faced with a problem, all that you need to do is to find a solution. Most intuitive solutions are simple. Simply, remove the problem! Re-iterating this story from the context of this chapter implies the following. If one of the main problems to integrate ML in our area arises from the heavy reliance on coding/programming, then let us try to remove this problem (at least for a bit)!

2 Some also offer free services/downloads to any user – including practicing engineers. It is worth noting that other platforms than those explicitly mentioned here are available (i.e., DataBricks, OpenML, Google Colab, Kaggle, etc.). Please feel free to try them.

3 Admittedly, most of these examples cover tabular data and two will cover the application of computer vision. In all cases, similar, modified, and extended examples can also be tailored and applied. Use your imagination to extend these beyond the scope of this book and toward your field!

4 This would qualify as a simple solution!

Imagine this; if there is no need for coding and specialized equipment, then ML becomes a bit more accessible to various users and industries.5 From this end, the user is expected to become familiar with the platform of their choice and general ideas behind ML as opposed to learning ML via learning how to code. The latter is indeed one of the biggest hurdles to embracing ML in a variety of engineering industries.

In the coding-free approach, a civil or environmental engineer can access an online portal with an intuitive graphical interface.6 It is through this interface that the engineer can upload their data, select the type of analysis they envision to carry out, select one or a series of ML algorithms, run the ML analysis, and examine the outcome of this analysis.7 In some instances, the engineer could deploy their final model to use it outside of the platform. The engineer could seamlessly share and collaborate with others on projects.

I will be covering five platforms in this chapter. My reasoning for selecting these five stems from the positive experiences I gained while using such platforms, as well as the fact that these platforms offer free access and academic support to students and faculty. These platforms are BigML, DataRobot, Dataiku, Exploratory, and Clarifai.8

### 6.1.1 BigML

According to BigML,9

> BigML is a consumable, programmable, and scalable Machine Learning platform that makes it easy to solve and automate Classification, Regression, Time Series Forecasting, Cluster Analysis, Anomaly Detection, Association Discovery, and Topic Modeling tasks.

BigML was founded in 201110 with the mission of making ML easy and beautiful for everyone [1]. Of all the presented platforms in this textbook, BigML could arguably be the most general in applications. BigML also has a strong academic program that supports ML education and research and allows students to freely access and practice its platform. A unique feature of BigML is that it allows its users to download the completed ML models in scripts11 (i.e., once a user completes building a model, the same user can download their model’s code in a programming language of their choice to share with other users, etc.). BigML also supports explainable ML.12 A screenshot of BigML’s homepage is shown in Figure 6.1. We will use this platform to cover four examples,13 as you will see below. Please feel free to follow my steps.

#### Example no. 1 [BigML, Classification]: Categorizing failure mode in FRP-strengthened RC beams.

In this example, we have a dataset14 that homes the outcome of over 100 experimental tests on RC beams strengthened with FRP15 composites. This dataset includes compressive strength of concrete fc, yield strength of steel reinforcement fy, the ratio of steel reinforcement rs, FRP ratio rf, modulus of FRP Efr, moment arm a, and strengthening type t.16 The target in this dataset is the failure mode17 (FM) observed in each test (i.e., steel yielding/concrete crushing or failure through the FRP system). Let us use the BigML platform to carry out this example.
