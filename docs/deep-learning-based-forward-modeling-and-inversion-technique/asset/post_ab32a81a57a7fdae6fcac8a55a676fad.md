
# Advanced Deep Learning Techniques in Computational Physics

![](img/020125e0e698f9771fbbd32f2ace1e80_185_0.png)

FIGURE 5.16
The predicted results of the closed cavity. (a) |w| calculated by COMSOL, (b) |v| predicted by the framework, (c) the absolute error, (d) $T_{norm}$ calculated by COMSOL, (e) $T_{norm}$ predicted by the framework, and (f) the absolute error.
where $N$, $u_*$, and $u_h$ indicate the total number of sampling points, the ground truth, and the predicted fields. In order to detect the statistical distributions of the error, the violin plot is introduced, whose results are plotted in Figure 5.17. Here, the width of the subgraph denotes the probability density. Obviously, the relative errors are no more than 0.01 for major samples, effectively corroborating the robustness of the network.

## 5.3.2. Comparison

In this part, experiments are performed to highlight the strength of the developed Fourier network. The predicted accuracy is compared to two conventional networks at different resolutions. To end this, the calculation of temperature in the first experiments are investigated by employing the fully connected network (FCN) and the convolutional neural network (CNN). The average mean square errors on the results with a resolution ranging from $16^2$ to $128^2$ are collected. It is noted that the benchmark of the three network is the computational costs of an adequately dense grid. It is lucid that the MSE of the cascaded Fourier framework is more than 10 times lower than FCN and CNN. Additionally, as the conventional CNN or FNN focuses on the data fitting while the Fourier network aims at operator learning, the average MSE is nearly independent of the mesh density. In contrast, the average MSE of the traditional CNN increases with the resolution due to the more sophisticated framework. Therefore, it is possible to train the proposed architecture on a sparse mesh while testing on a dense one, which can save calculation resources.

Another critical issue for implementing the DL technique in multiplications is that it enables faster predictions than conventional approaches by fully utilizing the parallel computing abilities of the GPU, making it feasible to compute a plethora of samples simultaneously. To quantitatively measure the speed of calculation, the time consumption of 1000 specimens via the FEM and the well-trained framework (the total time of the input structure and the Fourier structure) are counted. As displayed in Figure 5.18, it takes nearly 7.48 s on average for the framework to process 1000 samples (1.53 s for the input framework and 5.9 s for the Fourier framework). For the FEM-based software, it needs to spend 185 minutes, which is 1500 times slower. Besides, although the Fourier framework needs some time for data generation and training before being used, that process is just one-off. That is to say, once the offline training is completed, the real-time online prediction can be performed.

## 5.4 Conclusion

In this chapter, several applications of advanced deep learning techniques are investigated in computational physics. At the very first, the physics-informed frameworks are discussed, including the fully connected-based and the convolutional-based architecture. Besides, the PINNs in orthogonal curve coordinate systems are discussed, including the steady state and transient problems in cylindrical, spherical, and parabolic coordinates. After that, the graph neural network is introduced, followed by its applications in electrostatics. As the unstructured grid is applied in GNN, it can be applicable to more universal scientific computation problems. In the last part of chapter, the operator-based Fourier network is introduced. The calculation results firmly attest that the developed framework can obtain the anticipated multiphysics fields in real time. Additionally, the Fourier architecture emerges consistent average error rates for diverse resolutions, which has a certain potential to be adopted in numerous computation scenarios. In all, the newly developed advanced DL techniques have merits in flexibility, universality, efficiency, and economy. Consequently, it is believed to substitute the traditional numerical algorithms or classical DL architectures in some certain computational physics tasks.

## Bibliography

![](img/020125e0e698f9771fbbd32f2ace1e80_187_0.png)

### FIGURE 5.18

The comparison results between the proposed network and other approaches.
(a) Average MSE of the three trained networks with various resolutions and
(b) the solving time of the proposed framework and the finite element method (FEM): (i) the input module, (ii) the Fourier module.

- [1] Randall J. LeVeque. Finite Difference Methods for Ordinary and Partial Differential Equations. Society for Industrial and Applied Mathematics, Philadelphia, 2007.
- [2] Alik Ismail-Zadeh and Paul Tackley. Finite Difference Method, page 24–42. Cambridge University Press, Cambridge, 2010.
- [3] Snehashish Chakraverty, Nisha Mahato, Permumanda Karunakar, and Tharasi Dilleswar Rao. Advanced Numerical and Semi-Analytical Methods for Differential Equations, Finite Difference Method, pages 53–62. John Wiley & Sons, New York, 2019.
- [4] The finite element method: Its basis and fundamentals. In O.C. Zienkiewicz, R.L. Taylor, and J.Z. Zhu, editors, The Finite Element Method: Basis and Fundamentals (Seventh Edition), page iii. Butterworth-Heinemann, Oxford, 2013.
- [5] The finite element method. In G.R. Liu and S.S. Que, editors, The Finite Element Method (Second Edition), page iii. Butterworth-Heinemann, Oxford, 2014.
- [6] I. M. Smith, D. V. Griffiths, and L. Margets. Programming Finite Element Computation, Chapter 3, pages 59–114. John Wiley & Sons, Ltd, Hoboken, New Jersey, 2015.
- [7] J.T. Ogden and N. Kikuchi. Use of variational methods for the analysis of contact problems in solid mechanics. In SEMAT-NASSER, editor, Variational Methods in the Mechanics of Solids, pages 260–264. Pergamon, 1980.
- [8] J.T. Ogden and N. Kikuchi. Use of variational methods for the analysis of contact problems in solid mechanics. In SEMAT-NASSER, editor, Variational Methods in the Mechanics of Solids, pages 260–264. Pergamon, 1980.
- [9] Kun Zhou and Bo Lu. Chapter 1 - Introduction to molecular dynamics. In Kun Zhou and Bo Lu, Molecular Dynamics, pages 1–40.
- [10] Sumit Sharma, Pramod Kumar, and Rakesh Chandra. Chapter 1 - Molecular dynamics. In Sumit Sharma, Molecular Dynamics, pages 1–38.
- [11] Khemraj Shukla. Chapter 1 - Deep learning. In Khemraj Shukla, Deep Learning, pages 29–47.
- [12] Kurt Hornik. Multilayer feedforward networks are universal approximators. Neural Networks, 2(5),359–366, 1989.
- [13] Barak A. Radul, Alexey Andreyevich. Automatic differentiation in machine learning. J. Mach. Learn., 18(1),5595–5637, 2017.
- [14] Christian Huber. Physics-informed neural networks (pins) for loss functions. Journal of Computational Physics, 458,1111, 2222.
- [15] Xiaowe Shen, Hui Li, and George Karniadakis. Sfsnets (navier-stokes flows): Physics-informed neural networks for the compressible navier-stokes equations. Journal of Computational Physics, 426,109951, 2021.
- [16] Majid Rasht-Behesat, Christian Huber. Physics-informed neural networks (pins) for wave propagation and full waveform inversion. Journal of Geophysical Research: Solid Earth, 127(5),c2021JB0320, 2022.
