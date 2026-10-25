
![](img/3ec5662c0c5150f5b95af65046cb9cd4_20_0.png)

| Ref. | Knowledge forms | | | Informed ways |
| :--- | :---: | :---: | :---: | :--- |
| | Explicit | Embedded | Tacit | |
| [13,53,55,58,144,170,174,188,195–198] | ✓ | | | Simulator |
| [59,171,199] | | | ✓ | Gauge |
| [59,167,169,171,183,199,200,201] | ✓ | | | Extractor |
| [36,62,63,113,149,172,182,213] | ✓ | | | Operator |
| [43,51,118,165] | | | ✓ | Operator |
| [81,130,209] | | ✓ | | Operator |
| [37,113,210,217] | ✓ | | | Structure blueprint |
| [20,50,91,95,107,114,115,120,121,129,156,166,178,179,186,211,212] | | ✓ | | Structure blueprint |
| [57,76,142,149,187] | ✓ | | | Initializer |
| [154,168] | | ✓ | | Initializer |
| [96,123,132,133,150] | ✓ | | | Consistency |
| [177,214] | | ✓ | | Consistency |
| [131,146] | | | ✓ | Consistency |
| [84,176] | ✓ | | | Conflict |
| [126,143,173] | | | ✓ | Conflict |

embedded transfer learning model based on the physical attributes of buildings’ damage patterns is trained by minimizing the loss of the damage attribute that is measured via L2-norm and angular loss [215]. Besides, the aforementioned building-related knowledge can also be used to introduce a new physics guided weighted design. In [199], the authors use physical similarity to the target to measure the importance of each source and thus decide the data to which source to transfer.

- 7. The same physics knowledge can be informed in different ways. For example, dynamic mode decomposition capturing system characteristics can be used to design operators for image reconstruction to identify cracks [118], or to design an extractor that generates input feature maps for time-delay-system diagnostic [169]. In particular, knowledge in the form of self-contained input-output relationships and derivations such as finite elements can be used as 1) embedded knowledge to guide the network design for simulating the physics derivation such as the dynamic convolution for accelerating CNN [218], 2) explicit knowledge for data augmentation by designing the failure surrogate model [55], or 3) metric to design conflicting loss between ML and physical predictions [176].

- 8. About when to use what form of knowledge. According to the analysis of the existing research in Table 7, this paper suggests When dealing with explicit knowledge, the system behaviors can be described by mathematical equations or analytical models with clear input-output relations. If the physics signal variables involved in the equations are available, we can use them to customize NN layers or units based on analytical formulas or system physics characteristics. When explicit knowledge of the system behaviors is unavailable, but we have information about system physical structures or behavior model derivation knowledge, along with handling inference relations for the involved signals, we can construct a physics-informed structure. Embedded knowledge is then utilized to customize the data flow in the NN structure or employ custom-designed NNs as surrogate models for specific steps in the physics model derivation. In the case of tacit knowledge, where quantitative information about system behaviors is lacking, but there exist physical relations between system inputs and outputs or constraints on the system outputs, these relations can be employed to customize the ML objective function or regulate the output of hidden layers.

It is important to note that these forms of knowledge are not mutually exclusive, and they can often be combined or integrated within a PIML framework. The choice of which form to use, or whether to combine them, depends on the specific requirements and objectives of the problem at hand. A comprehensive approach to PIML may involve utilizing a combination of explicit, embedded, and tacit knowledge to capture the full range of system characteristics and optimize model performance. Ultimately, the selection of the appropriate form(s) of knowledge requires careful consideration of the problem domain, available expertise, data availability, and the desired level of interpretability and accuracy in the modeling process.

## 5. Challenges and future research directions: Toward PHM in the context of “small data and scarce physics knowledge”

Although PIML can bring numerous alternative solutions for diverse applications in PHM, as mentioned in previous sections, the development of PIML in PHM still comes with some particular limitations and challenges. Some of these limitations and challenges are presented in this section.

### 5.1. Limitations and challenges of PIML

The challenges related to sparse and noisy data, data availability, and incomplete physics models have been highlighted in other reviews [18,29,32]. In addition, there is a need for further research into the collection of more representative data, the selection of an appropriate benchmark model, and the determination of the weighting parameters or hyperparameters for the informed ML part. This paper argues that the fundamental problem underlying these challenges is how to convert various forms of knowledge into the type necessary for the ML framework, that is, to adjust knowledge to ML models rather than selecting ML models to fit physics knowledge. Consequently, one can highlight the challenges in two aspects:

- 1. Building a physics aware ML framework

  In the current research on the design of PIML, the inter-conversion between physics knowledge and ML, as well as the assessment metric for ML physical inconsistency, remains an under-explored and challenging topic. Therefore, there is a need to construct a physics-aware ML framework that can automatically incorporate physics knowledge into various parts of the ML pipeline based on the form of knowledge according to the physics-ML inter-conversion mechanism and the inconsistency evaluation results.

- 2. Construction of knowledge basis

  The construction of effective PIML frameworks requires a thorough comprehension of the physical characteristics of the system under investigation. This necessitates that the researcher possesses comprehensive knowledge and skills in both computer science and physics (e.g. mechanics). Thus, this leads to significant barriers for junior researchers without interdisciplinary experience in the implementation of PIML techniques. Furthermore, due to the fact that most knowledge can be ambiguous, mathematical expressions and physics modeling are not always well-developed for PHM case studies. Consequently, it is essential to construct a knowledge basis for PIML from ambiguous information.

### 5.2. Future directions

Although it is difficult to determine which direction will lead to transformative discoveries, the PHM community can make a substantial contribution to the future of PIML by taking into account the challenges outlined in the previous section in the following areas:

- 1. Compiling fault mechanisms in ML

  There is a lack of studies regarding how ML can better use integrated physics knowledge from multiple sources. Establishing the cognitive mechanisms for PIML when different forms of knowledge are embedded in different ML frameworks thus appears as a meaningful work.

- 2. From the perspective of metric learning

  Another track that appears worth investigation is the development of ML objective functions with more multidimensional metrics that can cover model complexity, physics consistency, computational cost, and result accuracy.

- 3. Further building suitable benchmark problems

  A set of well-defined benchmark problems can facilitate the evaluation and comparison of different algorithms and thus contribute to the development of research on this topic. The physics knowledge corresponding to public datasets is usually not available because of a deep-domain background requirement. This often leads to numerous obstacles in developing PIML methods because of the knowledge shortage. The development of open-source benchmark problems with shared the encoded knowledge, such as the synthetic fatigue damage database presented in [219], or similar developments in other domains would be welcome.

- 4. Combining flexible twin model to build life cycle tool. The modeling techniques and twinning enabling technologies in [192, 193] present an appealing opportunity to integrate with PIML. This combination has the potential to develop a robust life-cycle management tool that incorporates flexible fidelity models and maintains physics consistency. Additionally, it enables the inclusion of indeterminate quantitative assessment evaluations by building twin framework.

- 5. Adaptation to sparse run-to-failure data and sparse label data. Most of the research on PIML in PHM focuses on sparse observations or information bias in the dataset. However, unlabeled data and non-complete failure process data accounts for the vast majority. Therefore, the theoretical and applied research of PIML for sparse and noisy data is worth exploring. Development of new PHM paradigms such as physics-informed unsupervised learning, self-supervised learning, and semi-supervised learning is expected.

- 6. PIML in “small data and scarce physics knowledge”. One of the ultimate development purposes of PIML in PHM is to be able to work under “small data and scarce physics knowledge” conditions, which will greatly extend the scope of potential PHM application. Following from the above-mentioned research directions, combining PIML with knowledge discovery and ML architecture search techniques has the potential for emerging breakthrough methods.

## 6. Conclusion

This paper presented bibliometric results and a state of the art review of physics-informed machine learning for prognostics and health management. An overview of its basic paradigm from the innovative perspective of “How to inform” and “What to be informed”, is summarized and provided. The existing approaches are grouped according to where and how the physics knowledge is embedded in the ML pipeline. The challenges of applying PIML to solve PHM problems and future research directions are also discussed. The main contribution of this paper is to provide a concise and comprehensive overview of PIML in PHM and to focus on the fundamental challenge of translating the appropriate form of knowledge for PIML utilization. It is hoped that this paper will encourage further works to expand the potential of PIML in the field of PHM.

## Declaration of Competing Interest

The authors declare that they have no known competing financial interests or personal relationships that could have appeared to influence the work reported in this paper.

## Data availability

Data will be made available on request.

## References

- [1] N. Kim, D. An, J.-H. Choi, Prognostics and health management of engineering systems, 2017.
- [2] B. Rezaeianjouybari, Y. Shang, Deep learning for prognostics and health management: state of the art, challenges, and opportunities, Measurement 163 (2020) 107929.
- [3] O. Fink, Q. Wang, M. Svensen, P. Dersin, W.-J. Lee, M. Ducoffe, Potential, challenges and future directions for deep learning in prognostics and health management applications, Eng. Appl. Artif. Intell. 92 (2020) 103678.
- [4] S. Zhang, S. Zhang, B. Wang, T.G. Habetler, Deep learning algorithms for bearing fault diagnostics-a comprehensive review, IEEE Access 8 (2020) 29857–29881.
- [5] P. Singh, M. Keyvanloo, A. Sadhu, An improved time-varying empirical mode decomposition for structural condition assessment using limited sensors, Eng. Struct. 232 (2021) 111882.
- [6] A. Khan, H. Hwang, H.S. Kim, Synthetic data augmentation and deep learning for the fault diagnosis of rotating machines, Mathematics 9 (18) (2021) 2336.
- [7] S. Khan, T. Yairi, A review on the application of deep learning in system health management, Mech. Syst. Signal Process. 107 (2018) 241–265.
- [8] E. Zio, Prognostics and health management (phm): where are we and where do we (need to) go in theory and practice, Reliab. Eng. Syst. Saf. 218 (2022) 108119.
- [9] A.K.B.M. Nor, S.R. Pedapati, M. Muhammad, Explainable ai (xai) for phm of industrial asset: state-of-the-art, prisma-compliant systematic review, arXiv preprint arXiv:2107.03869 (2021).
- [10] M. Arias Chao, Combining Deep Learning and Physics-Based Performance Models for Diagnostics and Prognostics, ETH Zurich, 2021. Ph.D. thesis.
- [11] A. Rasheed, O. San, T. Kvamsdal, Digital twin: values, challenges and enablers, arXiv preprint arXiv:1910.01719 (2019).
- [12] L. Scapino, H.A. Zondag, J. Dirken, C.G. Rindt, J. Van Baal, A. Sciacovelli, Modeling the performance of a sorption thermal energy storage reactor using artificial neural networks, Appl. Energy 253 (2019) 113525.
- [13] M.A. Chao, C. Kulkarni, K. Goebel, O. Fink, Hybrid deep fault detection and isolation: combining deep neural networks and system performance models, arXiv preprint arXiv:1908.01529 (2019).
- [14] K.L. de Calle, S. Ferrero, A. Arnau, B. Sierra, Dynamic condition monitoring method based on dimensionality reduction techniques for data-limited industrial environments, Comput. Ind. 112 (2019) 103114.
- [15] B. Zhao, G. Wen, H. Sun, D. Sun, H. Yang, J. Cao, L. Dai, B. Wang, Similarity criteria and coal-like material in coal and gas outburst physical simulation, Int. J. Coal Sci. Technol. 5 (2) (2018) 167–178.
- [16] P.C. Berri, M.D. Dalla Vedova, L. Mainini, Computational framework for real-time diagnostics and prognostics of aircraft actuation systems, Comput. Ind. 132 (2021) 103523.
