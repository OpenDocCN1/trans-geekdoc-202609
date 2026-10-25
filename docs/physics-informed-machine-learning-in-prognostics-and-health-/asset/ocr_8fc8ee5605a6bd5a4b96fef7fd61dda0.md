![](bbox=[0.285, 0.065, 0.715, 0.2])

Fig. 11. Three ways to construct a physics-informed input space.

conditions. The effect of tooth wear and tooth breakage on the meshing stiffness are the only factors to be considered. In contrast, the PIML simulator based on the surrogate model uses a grey box model to fit the relationship among the excitation, responses and the structural parameters. It assumes that the corresponding mappings of the grey box model are constant and applicable in different working state spaces, thus further increasing the number of samples.

# Physics-informed gauges

In some specific case studies, e.g., complex structural systems, it is inevitable to use simplified physical models for the construction of “Simulators”. However, this simplification might lead to significant deviations in model behavior as well as in estimated values compared to the true values of the system [80]. Then, model updates can not inherently correct modeling errors. To overcome this issue, data transferring is an alternative solution for enhancing the data space. In this light, some studies focus on applying physics knowledge as a “Gauge” to evaluate the similarity between the source and target database. This technique migrates feature knowledge from the source domain to the target domain by designing a physically based transfer criterion between them. It allows enhancing the ML robustness and improving the efficiency and accuracy of ML models.

The two basic ways to implement “Gauge” are shown in Fig. 13. Its principle consists of finding the invariant variable or invariant relationship between the source and target domains, such as feature symmetry, conservation, transformation invariance, and monotonicity [139,203]. The source domain, which has a large amount of data and information, is then selectively transferred to the target domain according to physical similarity criteria [159].

# Physics-informed extractor

In addition to data extraction, data processing is another crucial task that directly affects the performance of ML models. To ensure that the input space contains as many fault-related features as possible, it is necessary to create a physics-informed extractor to guide the data preprocessing according to physics knowledge. For example, the proposed physics-informed extractors allow selecting suitable domain transformation methods [204] to get the relevant aggregated features [155], or fusing heterogeneous information from multiple sources [40,65]. In [88], the taut string model equation standardizes the principal component analysis method for extracting the specified modal frequency bands of cable vibration. The study in [79] develops a physics-guided ML model to conduct the feature extraction process that can generate particular features directly reflecting the performance of electric vehicles.

Following feature extraction, the ML module incorporates an embedding component that functions as a set of sub-feature extractors. Subsequently, information fusion takes place, with a primary focus on merging physical health indicators with virtual health indicators. The former pertains to fault physics and typically carries significant interpretability in terms of the indicators. For the latter, there are two implementations in existing PIML studies [205]:

+   - Information fusion from multiple physics domains to obtain “sensory data” with less redundancy and representing all original information. For example, multiple regression [132], elevated space projection [206], and other supervised and unsupervised learning methods are used to perform signal-level data fusion and feature-level data fusion [42].

+   - Cross-physics domain relations fusion through physics relationships to get “perceptual data”, where the physics relationships of the various parts of the data are prominent [207,208], as shown in Fig. 14. For example, in crack growth prediction, information on the structural response, such as displacement and phase fields, obtained by the Newton-Raphson solution, are preserved in the form of images of the current state of the crack to build spatial structural knowledge [70].

# 3.2.2. Physics-embedded algorithm structure

Regarding “Physics-embedded algorithm structure”, PIML seeks to make the traditional physics-agnostic ML become physics aware so that the governing processes are added to the design of ML algorithm structures and the parameters searching process. It is prone to integrate the “Hard Constraint Projections (HCP)” [90] with ML, including the three following paradigms: “Basic operator”, “ML Structure blueprint”, and “Parameter initializer”, as shown in Fig. 15.

The “Basic Operato” is responsible for enforcing physically resolved relationships in machine learning processing. On the other hand, the “ML Structure Blueprint” is dedicated to designing ML modules or inter-layer connections based on physically derived relationships, thereby endowing sparsity. These components are implemented in the algorithm’s structural design. Additionally, the “Parameter Initializer” focuses on identifying the ML parameters. A brief summary of these three approaches used in the existing literature is shown in Table 5.

# Physics-informed operator