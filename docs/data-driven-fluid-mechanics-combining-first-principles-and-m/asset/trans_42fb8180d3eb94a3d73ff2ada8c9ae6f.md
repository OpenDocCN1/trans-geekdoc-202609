
科学研究的循环在于研究者构思一个模型，并设计实验来检验它。虽然这种“假设驱动的搜索”在理论上具有明显的吸引力，但它会限制创造力。模型必须在被检验之前被构思，而新思想则依赖于研究者的想象力。然而，我们在本章开头已指出，更快的实验和计算方法为我们所称的蒙特卡洛搜索提供了可能性，或许可以描述为“搜索驱动的假设”，在这种方法中，实验是随机进行的，并在事后进行评估，希望其中一些会是有趣的。这比经典程序更昂贵，但可能是避免根深蒂固偏见的最佳希望。

我们已通过对第19.2节和19.3节中二维湍流的应用来说明这些思想，但这些讲座的主题不是湍流本身而是方法，我们现在简要讨论在此练习中先前表达的希望实现到了何种程度。第一个考虑因素是成本，这始终是湍流研究的制约因素。本文中的整个程序在中等规模的院系集群上花费了大约一个月计算机时间，并由作者在一年内的业余时间编写。花在与同事讨论应该做什么的时间远多于实际执行的时间。由于该工作被设想为原理验证，问题是有意选择得很小，但更有趣的问题也在可及范围内。第19.2节实验中必须多次重复的基本模拟大约运行10个核心秒，但即使是三维各向同性湍流的256³模拟，也可以在现代GPU上在两分钟内运行（Jiménez 2020a）。因此，针对三维湍流级联中因果关系的程序——相比二维而言我们对其了解要少得多——可以在适度的GPU集群上在几个月内完成。同样，主要的障碍将是如何决定做什么。

第二个问题是是否学到了一些具有物理意义的东西。如第19.2节开头所述，对于通常被认为基本已理解的问题，人们期望甚微，但实际结果很有趣。本章大致遵循Jiménez（2020b）中的讨论，但两个早期版本（Jiménez 2018b，Jiménez 2020a）完全遗漏了偶极子，并得出实验证实了二维湍流的经典涡气模型。图19.4(b)中的偶极子模板是进一步后处理的略微令人惊讶的结果，如果我们承认惊讶是发现的定义性要素之一（Schaffer 1994），那它就是一次小发现。不幸的是，我们在第19.3节看到，偶极子并非二维流动中完全未知的组成部分，发现它们与其说是真正新发现，不如说是回忆起被遗忘的东西。很明显，本章需要在成为流体力学中具有独立兴趣的文章而非方法学之前做大量额外工作，但作者在没有“提示”的情况下发现了意料之外的事情，这一事实对蒙特卡洛方法在真正未知的问题中的未来是鼓舞人心的。

第三个问题是我们对数据利用过程学到了什么。科学方法可以被视为搜索“最佳”

![](img/ddadb1d3eaa6f9576eea68f95d453bca_426_0.png)

图19.7 科学方法。转载自第2章以便参考。

假设，自然会问其中哪些部分可以被自动化。第19.2节和19.3节中的案例研究被设想为实验测试自动化过程可以推进到何种程度。可以得出几点结论。第一点是图19.7中的步骤S1（观测）可以很大程度上外包给计算机，包括对“提问”的引用。表19.1中的实验是有意地在几乎不考虑其意义的情况下决定的，尽管很难说它们受作者之前经验的影响有多大。对步骤S3中涉及将预测与观测进行对比的部分也可以这样说。二维湍流的模拟现在已是微不足道，结果的分类被外包给了库程序（图19.2和图19.3）。一个有趣的、尽管并不完全出乎意料的结果是验证和确认的重要性，重读第19.2.2节以及在一定程度上第19.3节，显示了通过这种方式避免的陷阱。这类问题在任何涉及数据分析的项目中都是预期的，但在像本例这样目标是探测未知的案例中尤其危险。

最后一个需要考虑的点是图19.7中模型生成和评估步骤（S2），这是发现过程的核心。即便在此，某些部分也被自动化了。图19.4中的模板是流动模型，并且是自动获得的。注意，正是在这一点上，从子符号到符号AI的转变在此示例中发生了。图19.2和图19.3主要对计算机分类有用，但图19.4中的模板是为人类准备的。

另一方面，第19.3节中对模板的解释完全是手动的，目前很难看出它如何能外包给计算机。这不仅是因为需要一种略高于现有计算机软件的智能水平，而且因为我们试图做的事情并没有很好地定义。如果科学项目的目标是找到一个“好”模型，我们需要精确地定义我们认为什么是好的假设。我们在第2章中提到，科学方法的一个目标是产生“美丽”的理论，但我们并不知道如何很好地定义科学之美。二维湍流的终极模型是纳维–斯托克斯方程，任何观测的终极原因都是某种假想的初始条件。我们

这里将时间范围限制在由于混沌导致记忆损失之前，这是出于对流动控制的某种概括性兴趣。这是一个影响结果并使其不那么普遍的选择，但它定义了使我们能够定义模板的度量。

人类监督可能仍需在一段时间内来完善假设，但蒙特卡洛科学即使现在也能做出贡献。再次考虑将科学方法解释为最大化“理解”的优化循环。作为这样，它原则上可以被实现为自动优化程序，例如神经网络。然而，大多数经典优化器，包括人类，都假设代价函数局部凸，这正是我们对研究者原创性和偏见疑虑的根源。蒙特卡洛是寻找最大值的一种不同方式，原则上绕过了凸性约束，并通过在过程中注入噪声来逃离局部最大值（Deb & Gupta 2006）。蒙特卡洛科学的最佳用途可能是作为部分随机化的搜索和分类步骤，随后进行反复的人工微调。令人鼓舞的消息是，在流体力学中，现在做这件事成为可能。

## 参考文献

Abdi, H. (2003), ‘Factor rotations in factor analyses’, Encyclopedia for Research Methods for the Social Sciences, Sage, Thousand Oaks, CA, pp. 792–795.
Abraham, R., Marsden, J. E., and Marsden, J. E. (1978), Foundations of Mechanics, Benjamin/Cummings Publishing Company, Reading, MA.
Abraham, R., Marsden, J. E., and Ratiu, T. (1988), Manifolds, Tensor Analysis, and Applications, Vol. 75 of Applied Mathematical Sciences, Springer-Verlag, New York.
Abu-Mostafa, Y. S., Magdon-Ismail, M., and Lin, H.-T. (2012), Learning from Data: A Short Course, https://amlbook.com/.
Abu-Zurayk, M., Ilic, C., Schuster, A., and Liepelt, R. (2017), Effect of gradient approximations on aero-structural gradient-based wing optimization, in ‘EUROGEN 2017’, September 13–15, 2017, Madrid, Spain.
Adrian, R. J. (1975), On the role of conditional averages in turbulence theory, in ‘Proceedings of the 4th Biennial Symposium on Turbulence in Liquids, University of Missouri-Rolla, 1975’, Science Press, Princeton, NJ.
Adrian, R. J. (1991), ‘Particle-imaging techniques for experimental fluid mechanics’, Annual Review of Fluid Mechanics 23(1), 261–304.
Adrian, R. J. (2007), ‘Hairpin vortex organization in wall turbulence’, Physics of Fluids 19, 041301.
Adrian, R. J., Jones, B., Chung, M., Hassan, Y., Nithianandan, C., and Tung, A.-C. (1989), ‘Approximation of turbulent conditional averages by stochastic estimation’, Physics of Fluids A: Fluid Dynamics 1(6), 992–998.
Ahuja, S. and Rowley, C. W. (2010), ‘Feedback control of unstable steady states of flow past a flat plate using reduced-order estimators’, Journal of Fluid Mechanics 645, 447–478.
Albers, M., Meysonnat, P. S., Fernex, D., Semaan, R., Noack, B. R., and Schröder, W. (2020), ‘Drag reduction and energy saving by spanwise traveling transversal surface waves for flat plate flow’, Flow, Turbulence and Combustion 105, 125–157.
Aleksic, K., Luchtenburg, D. M., King, R., Noack, B. R., and Pfeiffer, J. (2010), Robust nonlinear control versus linear model predictive control of a bluff body wake, in ‘5th AIAA Flow Control Conference’, June 28–July 1, 2010, Chicago, AIAA-Paper 2010-4833, pp. 1–18.
Allaire, G. and Schoenauer, M. (2007), Conception optimale de structures, Vol. 58 of Mathématiques et Applications, Springer, Berlin.
Alsalman, M., Colvert, B., and Kanso, E. (2018), ‘Training bioinspired sensors to classify flows’, Bioinspiration & Biomimetics 14(1), 016009.
Amsallem, D., Zahr, M. J., and Farhat, C. (2012), ‘Nonlinear model order reduction based on local reduced-order bases’, International Journal for Numerical Methods in Engineering 92(10), 891–916.
Antoranz, A., Gonzalo, A., Flores, O., and Garcia-Villalba, M. (2015), ‘Numerical simulation of heat transfer in a pipe with non-homogeneous thermal boundary conditions’, International Journal of Heat and Fluid Flow 55, 45–51.
Antoranz, A., Ianiro, A., Flores, O., and García-Villalba, M. (2018), ‘Extended proper orthogonal decomposition of non-homogeneous thermal fields in a turbulent pipe flow’, International Journal of Heat and Mass Transfer 118, 1264–1275.
Antoulas, A. C. (2005), Approximation of Large-Scale Dynamical Systems, Society for Industrial and Applied Mathematics, Philadelphia.

