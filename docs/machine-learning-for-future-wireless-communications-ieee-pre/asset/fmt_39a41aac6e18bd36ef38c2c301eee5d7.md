
Some pros and cons that need to be taken into account in order to decide whether to use the solutions based on ANNs or SVRs are discussed in the following. While ANN‐based models permit a compact representation of a multidimensional function, they suffer from two main weaknesses: (i) ANNs often converge on local minima rather than global minima, and (ii) they can suffer from the overfitting problem due to the traditional empirical risk‐minimization principle employed by ANNs. SVR techniques instead use the structural risk‐minimization principle that avoids the model becoming too strongly tailored to the particularities of the training set, thus preventing it from overfitting. Additionally, the solution to SVR is global and unique. Regarding the dimensions, ANNs are parametric models whose size is fixed and depends on their specific architecture, while SVRs (based on kernels) consist of a set of support vectors, selected from the training set, with a weight for each. In the worst case, the number of support vectors is exactly the number of training samples, and in general its model size scales linearly. Thus, if the number of training samples is high, so is the computational complexity of the SVR. Finally, while ANNs may have any number of outputs, SVRs have only one. The most direct way to create a MIMO system with SVR is to create multiple support vector machines and train each of them one by one.

Under the current practical circumstances, ANNs have been successfully employed in several applications in the DFE for their capability to approximate any continuous function. ANNs have been reported in the literature to be used for modeling at the transistor, circuit, and system level. The SVR technique has been successfully applied to circuit modeling for characterizing and designing antennas, filters, and power amplifiers. At the system level, however, solutions based on SVR methods to model or linearize PAs through DPD are not as extended as those based on ANNs. It is strongly believed that ANN‐ or SVR‐based solutions will play a very important role in future DFE implementation and deployment, including intelligent vector processors and functional IP blocks.

## Bibliography

1.  Shoaib Amin, Per N. Landin, Peter Handel, and Daniel Ronnow. Behavioral modeling and linearization of crosstalk and memory effects in RF MIMO transmitters. IEEE Transactions on Microwave Theory and Techniques, 62 (4): 810–823, apr 2014. doi: 10.1109/tmtt.2014.2309932.

2.  J. Armstrong. Peak‐to‐average power reduction for OFDM by repeated clipping and frequency domain filtering. Electronics Letters, 38 (5): 246, 2002. doi: 10.1049/el:20020175.

3.  Taylor Barton. Not just a phase: Outphasing power amplifiers. IEEE Microwave Magazine, 17 (2): 18–31, feb 2016. doi: 10.1109/mmm.2015.2498078.

4.  S.A. Bassam, M. Helaoui, and F.M. Ghannouchi. Crossover digital predistorter for the compensation of crosstalk and nonlinearity in MIMO transmitters. IEEE Transactions on Microwave Theory and Techniques, 57 (5): 1119–1128, may 2009. doi: 10.1109/tmtt.2009.2017258.

5.  R.W. Bäuml, R.F.H. Fischer, and J.B. Huber. Reducing the peak‐to‐average power ratio of multicarrier modulation by selected mapping. Electronics Letters, 32 (22): 2056, 1996. doi: 10.1049/el:19961384.

6.  Dimitri P. Bertsekas and J.N. Tsitsiklis. Neuro‐dynamic programming. In Encyclopedia of Optimization, pages 2555–2560. Springer US, 1996. doi: 10.1007/978‐0‐387‐74759‐0\_440.

7.  R. Neil Braithwaite. A comparison of indirect learning and closed loop estimators used in digital predistortion of power amplifiers. In *2015 IEEE MTT‐S International Microwave Symposium*. IEEE, may 2015. doi: 10.1109/mwsym.2015.7166826.

8.  R.N. Braithwaite. Digital predistortion of an RF power amplifier using a reduced volterra series model with a memory polynomial estimator. IEEE Trans. on Microw. Theory and Tech., 65 (10): 3613–3623, Oct. 2017. doi: 10.1109/tmtt.2017.2729513.

9.  Dalibor Buzic and Jasminka Dobsa. Lyrics classification using naive bayes. In *2018 41st International Convention on Information and Communication Technology, Electronics and Microelectronics (MIPRO)*. IEEE, may 2018. doi: 10.23919/mipro.2018.8400185.

10.  Jialin Cai, Chao Yu, Lingling Sun, Shichang Chen, and Justin B. King. Dynamic behavioral modeling of RF power amplifier based on time‐delay support vector regression. *IEEE Transactions on Microwave Theory and Techniques*, pages 1–11, 2018. doi: 10.1109/tmtt.2018.2884414.

11.  Wenhui Cao and Anding Zhu. A modified decomposed vector rotation‐based behavioral model with efficient hardware implementation for digital predistortion of RF power amplifiers. IEEE Transactions on Microwave Theory and Techniques, 65 (7): 2443–2452, jul 2017. doi: 10.1109/tmtt.2016.2640318.

12.  Wenhui Cao, Yue Li, and Anding Zhu. Magnitude‐selective affine function based digital predistorter for RF power amplifiers in 5G small‐cell transmitters. In *2017 IEEE MTT‐S International Microwave Symposium (IMS)*. IEEE, jun 2017. doi: 10.1109/mwsym.2017.8058921.

13.  Jessica Chani‐Cahuana, Mustafa Ozen, Christian Fager, and Thomas Eriksson. Digital predistortion parameter identification for RF power amplifiers using real‐valued output data. IEEE Trans. on Circ. and Sys. II: Express Briefs, 64 (10): 1227–1231, Oct. 2017. doi: 10.1109/tcsii.2017.2686004.

14.  Kaiya Chen, Minxi Wang, and Xusheng Li. Amplifier predistortion method based on support vector machine. In *2005 Asia‐Pacific Microwave Conference Proceedings*. IEEE, 2005. doi: 10.1109/apmc.2005.1607109.

15.  Peng Chen and Thomas J. Brazil. Classifying load‐pull contours of a broadband high‐efficiency power amplifier using a support vector machine. In *2017 Integrated Nonlinear Microwave and Millimetre‐wave Circuits Workshop (INMMiC)*. IEEE, apr 2017. doi: 10.1109/inmmic.2017.7927305.

16.  Peng Chen and Thomas J. Brazil. Optimization‐oriented method for broadband doherty power amplifier designs using support vector regression. In *2018 IEEE MTT‐S International Microwave Workshop Series on 5G Hardware and System Technologies (IMWS‐5G)*. IEEE, aug 2018. doi: 10.1109/imws‐5G.2018.8484335.

17.  Peng Chen, Brian M. Merrick, and Thomas J. Brazil. Support vector regression for harmonic optimization in continuous class‐F power amplifier design. In *2015 Integrated Nonlinear Microwave and Millimetre‐wave Circuits Workshop (INMMiC)*. IEEE, oct 2015. doi: 10.1109/inmmic.2015.7330376.

18.  D.L. Chester. Why two hidden layers are better than one. Proc. IJCNN, Washington, D.C., 1: 265–268, 1990. URL [https://ci.nii.ac.jp/naid/10000055979/en/](https://ci.nii.ac.jp/naid/10000055979/en/).

19.  D. Comaniciu and P. Meer. Mean shift: a robust approach toward feature space analysis. IEEE Transactions on Pattern Analysis and Machine Intelligence, 24 (5): 603–619, may 2002. doi: 10.1109/34.1000236.

20.  G. Cybenko. Approximation by superpositions of a sigmoidal function. Mathematics of Control, Signals, and Systems, 2 (4): 303–314, dec 1989. doi: 10.1007/bf02551274.

21.  Ramzi Darraji, Pedram Mousavi, and Fadhel M. Ghannouchi. Doherty goes digital: Digitally enhanced doherty power amplifiers. IEEE Microwave Magazine, 17 (8): 41–51, aug 2016. doi: 10.1109/mmm.2016.2561478.

22.  Sijmen de Jong. SIMPLS: An alternative approach to partial least squares regression. Chemometrics and Intelligent Laboratory Systems, 18 (3): 251–263, Mar. 1993. doi: 10.1016/0169‐7439(93)85002‐x.

23.  D.R. Morgan, Z. Ma et al. A generalized memory polynomial model for digital predistortion of RF power amplifiers. IEEE Trans. on Signal Processing, 54 (10): 3852–3860, Oct. 2006. doi: 10.1109/TSP.2006.879264.

24.  Toshiyuki Eda, Takanori Ito, Hiromitsu Ohmori, and Akira Sano. Adaptive compensation of nonlinearity in high power amplifier by support vector machine. IFAC Proceedings Volumes, 34 (14): 243–248, aug 2001. doi: 10.1016/s1474‐6670(17)41629‐6.
