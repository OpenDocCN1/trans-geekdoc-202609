

速率极限 \(\dot{\gamma} \to \infty \text{ s}^{-1}\)。在延伸粘度曲线的交点之间，通过平均场模型获得的延伸粘度 \(\eta_{\text{app}}\) 高于计算方法。

![](img/283dee3537da34c9897f9777475c5d3d_82_0.png)

### 3.5 Conclusions

### 3.5 结论

本章致力于研究剪切稀疏基体行为对纤维悬浮液有效粘度的影响。我们将考虑重点放在工程制造工艺（如注塑和压缩成型）感兴趣的剪切速率上。为开展研究，我们采用了Cross型粘度模型和基于FFT的计算方法，以确定纤维悬浮液在广泛剪切速率范围内的有效粘度。我们发现，微观结构离散的分辨率误差取决于剪切速率和加载方向，在中等剪切速率和纯剪切载荷下出现最小分辨率误差。出乎意料的是，我们发现，在具有配向微观结构的牛顿情况与具有横各向同性微观结构的Cross型情况中，代表体元尺寸高度相似。在所考虑的剪切速率区间内，我们发现Cross型悬浮液粘度在幅值和各向异性程度上变化强烈。最后，我们观察到，计算估计与Mori-Tanaka型平均场估计对于悬浮液粘度之间存在显著偏差。

## Chapter 4

## 第4章

## Machine learning assisted discovery of effective viscous material laws for shear-thinning fiber suspensions¹

## 基于机器学习的剪切稀疏纤维悬浮液有效粘性材料定律发现¹

¹ This chapter is based on the sections 1 to 5 of the publication "Machine learning assisted discovery of effective viscous material laws for shear-thinning fiber suspensions" (Sterr et al., 2024b).

¹ 本章基于论文《基于机器学习的剪切稀疏纤维悬浮液有效粘性材料定律发现》（Sterr et al., 2024b）的第1至5节。

Viscosity models for fiber polymer suspensions are widely used in molding process simulations of composite parts (Kennedy and Zheng, 2013), which play a major role in the lightweight design of engineering systems, i.e., in the automotive, aerospace, and energy sectors (Henning et al., 2019; Qureshi, 2022). Molding process simulations are an established tool in composite part engineering, partly because of the industrial benefits of digital twins (Botín-Sanabria et al., 2022) and virtual process chains (Henning et al., 2019; Görthofer et al., 2019; Meyer et al., 2023). In molding simulations for fiber reinforced plastics, accurate modeling of the suspension viscosity is crucial to predict various parameters of engineering interest. The suspension viscosity influences manufacturing process parameters (Castro and Tomlinson, 1990; Goodship, 2017), as well as fiber orientation and fiber volume distributions (Tseng et al., 2018). Consequently, flow fields (Karl et al., 2021) and final part properties (Böhlke et al., 2019; Karl et al., 2021) are also affected by the suspension viscosity. In light of the analytical and experimental difficulties involved when studying the viscosity of fiber suspensions with non-Newtonian solvents, computational approaches provide insights and observations that are otherwise hard to obtain. Švec et al. (2012) combined the lattice Boltzmann method for fluid flow, an immersed boundary procedure for the interaction between fluid and rigid particles, and a mass tracking algorithm for the free surface representation to simulate slump tests of a suspension of rigid spherical particles and fibers suspended in a Bingham-type fluid. In comparison with a slump test of pure matrix material, they observed a smaller spread and increased height in the slump test of the suspension, suggesting an increased effective yield stress. Using a Finite Element Method (FEM) based approach, Domurath et al. (2020) investigated the rheological coefficients of the transversely isotropic fluid equation by Ericksen (1960) in the context of rigid fibers suspended in a power-law fluid. In a simple shear flow, they found the model by Souloumiac and Vincent (1998) to overpredict the orientation dependence of a rheological coefficient. Combining the RVE method (Kanit et al., 2003) and Fast Fourier Transform (FFT) based computational techniques (Schneider, 2021), Sterr et al. (2023) extended work by Bertóti et al. (2021) on Newtonian fiber suspensions to suspensions with non-Newtonian solvents. They visualized the anisotropic viscosity tensor in the case of a Cross-type matrix fluid and studied the effects of fiber volume fraction and shear rate on the suspension viscosity.

纤维聚合物悬浮液的粘度模型广泛用于复合部件成型过程模拟（Kennedy and Zheng, 2013），这些模拟在工程系统的轻量化设计中发挥着重要作用，即在汽车、航空航天和能源领域（Henning et al., 2019; Qureshi, 2022）。成型过程模拟是复合部件工程中一种成熟的工具，这在一定程度上归功于数字孪生（Botín-Sanabria et al., 2022）和虚拟工艺链（Henning et al., 2019; Görthofer et al., 2019; Meyer et al., 2023）的工业优势。在纤维增强塑料的成型模拟中，对悬浮液粘度进行准确建模对于预测各种工程感兴趣的参数至关重要。悬浮液粘度影响制造工艺参数（Castro and Tomlinson, 1990; Goodship, 2017）以及纤维取向和纤维体积分布（Tseng et al., 2018）。因此，流场（Karl et al., 2021）和最终部件性能（Böhlke et al., 2019; Karl et al., 2021）也受悬浮液粘度的影响。鉴于在研究非牛顿溶剂中纤维悬浮液粘度时所涉及的分析和实验困难，计算方法提供了否则难以获得的洞察和观察。Švec et al.（2012）结合了用于流体流动的格玻尔兹曼法、用于流体与刚性颗粒相互作用的浸入边界法以及用于自由表面表示的质量跟踪算法，模拟了悬浮于Bingham型流体中的刚性球形颗粒和纤维悬浮液的坍落试验。与纯基体材料的坍落试验相比，他们在悬浮液的坍落试验中观察到更小的扩展和更高的高度，表明有效屈服应力增加。采用基于有限元法（FEM）的方法，Domurath et al.（2020）研究了刚性纤维悬浮于幂律流体中时，Ericksen（1960）各向异性流体方程的流变学系数。在简单剪切流中，他们发现Souloumiac和Vincent（1998）的模型高估了流变学系数的取向依赖性。结合RVE方法（Kanit et al., 2003）和基于快速傅里叶变换（FFT）的计算技术（Schneider, 2021），Sterr et al.（2023）将Bertóti et al.（2021）关于牛顿纤维悬浮液的工作扩展到具有非牛顿溶剂的悬浮液。他们可视化了Cross型基体流体情况下的各向异性粘度张量，并研究了纤维体积分数和剪切速率对悬浮液粘度的影响。

In this chapter, we combine high fidelity, FFT-based computational methods and a supervised machine learning strategy to discover material models for the effective viscosity of shear-thinning fiber suspensions. To do so, we study the anisotropic and shear rate dependent effective viscosity of fiber suspensions with a Cross-type matrix behavior and a fiber volume fraction of 25%. In section 4.2 we outline the setup for the FFT-based computational investigations, where we compute the effective material response for 109 different fiber orientation states and a variety of loading states. In terms of computational scope, this constitutes a significant extension to previous FFT-based work on shear-thinning fiber suspensions, in which a single fiber orientation state was considered (Sterr et al., 2023). Based on the computational data, we visualize the suspension viscosity tensor in three dimensions and formulate an anisotropy criterion applicable in a non-linear setting using a loading direction and shear rate dependent scalar viscosity, see section 4.3. We find that the anisotropy of the suspension viscosity shows a significantly different shear rate dependence for different fiber orientation states. Also, for all investigated microstructures, we confirm that the anisotropy of the suspension viscosity depends on the degree of non-linearity of the matrix material, which was previously only studied for a transversely isotropic microstructure (Sterr et al., 2023). In section 4.4, based on the insights into the shear rate and orientation state dependence of the suspension viscosity, we formulate requirements a model of the suspension viscosity needs to fulfill. According to the formulated requirements we propose four models with different numbers of parameters, as well as different phenomenological and theoretical motivations. Using the ADAM algorithm, we employ supervised machine learning techniques for non-convex optimization to learn the parameters of the model candidates. Overall, three models achieve similar maximum validation errors below 5.15 %, while one model based on superposition and orientation averaging performs unfavorably.

在本章中，我们结合高保真、基于FFT的计算方法和受监督机器学习策略，以发现剪切稀疏纤维悬浮液有效粘度的材料模型。为此，我们研究了具有Cross型基体行为和25%纤维体积分数的纤维悬浮液的各向异性及剪切速率依赖有效粘度。在4.2节中，我们概述了基于FFT的计算研究设置，其中我们针对109种不同的纤维取向状态和多种加载状态计算了有效材料响应。从计算范围来看，这对以前基于FFT的剪切稀疏纤维悬浮液工作（Sterr et al., 2023）构成了重大扩展，该工作仅考虑了单一纤维取向状态。基于计算数据，我们以三维可视化了悬浮液粘度张量，并利用加载方向和剪切速率依赖的标量粘度，制定了适用于非线性场景的各向异性准则，见4.3节。我们发现，悬浮液粘度的各向异性对不同纤维取向状态表现出显著不同的剪切速率依赖性。此外，对于所有被研究的微观结构，我们证实悬浮液粘度的各向异性取决于基体材料的非线性程度，此前这只针对横各向同性微观结构进行过研究（Sterr et al., 2023）。在4.4节中，基于对悬浮液粘度剪切速率和取向状态依赖性的洞察，我们制定了悬浮液粘度模型需要满足的要求。根据制定的要求，我们提出了四种具有不同参数数量以及不同现象学和理论动机的模型。使用ADAM算法，我们采用受监督机器学习技术进行非凸优化，以学习模型候选项的参数。总体而言，三种模型达到相似的最大验证误差，均低于5.15%，而一种基于叠加和取向平均的模型表现不佳。

### 4.2 A computational study of the effective behavior of shear-thinning fiber suspensions

### 4.2 剪切稀疏纤维悬浮液有效行为的计算研究

### 4.2.1 Computational homogenization procedure

### 4.2.1 计算同质化程序

In this chapter, we consider incompressible, shear-thinning fiber suspensions, occupying a rectangular volume \( Y \subseteq \mathbb{R}^3 \). First, we give a short summary of the numerical procedure for the homogenization of shear-thinning fiber suspensions detailed in section 3.2. We are interested in computing the effective viscous stress \( \bar{\tau} \in \text{Sym}_0(3) \) of the suspension in response to an applied, effective shear rate tensor \( \bar{D} \in \text{Sym}_0(3) \), where \( \text{Sym}_0(3) \) denotes the vector space of symmetric and traceless second-order tensors. For a pressure field \( p : Y \rightarrow \mathbb{R} \), a solenoidal velocity field \( v : Y \rightarrow \mathbb{R}^3 \) and a local viscous stress field

\( \tau = \mathcal{T}(\cdot, \bar{D} + \nabla^s v), \quad (4.1) \)

with associated stress operator

\(\begin{aligned} \mathcal{T} : Y \times \text{Sym}_0(3) \rightarrow \text{Sym}_0(3), \quad (4.2) \\ (x, D) \mapsto \frac{\partial \Psi}{\partial D}(x, D), \quad (4.3) \end{aligned}\)

and dissipation potential \( \Psi : Y \times \text{Sym}_0(3) \rightarrow \mathbb{R} \), the local balance of linear momentum without inertial effects

\( \text{div}(\tau) - \nabla p = 0, \quad (4.4) \)

needs to be fulfilled. In the context of suspensions with rigid inclusions, the local viscous stress \( \tau \) in equation (4.4) is, constitutively, not well-defined inside the rigid inclusions. We address this issue by changing to a dual formulation as follows. With the complementary dissipation

在本章中，我们考虑占据矩形体积 \( Y \subseteq \mathbb{R}^3 \) 的不可压缩、剪切稀疏纤维悬浮液。首先，我们简要总结3.2节中详细介绍的剪切稀疏纤维悬浮液同质化数值程序。我们感兴趣的是计算悬浮液在施加的有效剪切速率张量 \( \bar{D} \in \text{Sym}_0(3) \) 作用下的有效粘应力 \( \bar{\tau} \in \text{Sym}_0(3) \)，其中 \( \text{Sym}_0(3) \) 表示对称无迹二阶张量的向量空间。对于压力场 \( p : Y \rightarrow \mathbb{R} \)、无散度速度场 \( v : Y \rightarrow \mathbb{R}^3 \) 和局部粘应力场

\( \tau = \mathcal{T}(\cdot, \bar{D} + \nabla^s v), \quad (4.1) \)

及相关应力算子

\(\begin{aligned} \mathcal{T} : Y \times \text{Sym}_0(3) \rightarrow \text{Sym}_0(3), \quad (4.2) \\ (x, D) \mapsto \frac{\partial \Psi}{\partial D}(x, D), \quad (4.3) \end{aligned}\)

和耗散势 \( \Psi : Y \times \text{Sym}_0(3) \rightarrow \mathbb{R} \)，需要满足不含惯性效应的局部线性动量平衡

\( \text{div}(\tau) - \nabla p = 0, \quad (4.4) \)

。在包含刚性包容体的悬浮液背景下，方程（4.4）中的局部粘应力 \( \tau \）在构成上在刚性包容体内部定义不明确。我们通过切换到如下双重公式来解决这个问题。利用互补耗散

