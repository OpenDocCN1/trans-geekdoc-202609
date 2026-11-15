
## Developing a Construction Digital Twin for Bridges: A Case Study of Construction Control of Long-Span Rigid Skeleton Arch Bridge

Chunli Ying and Long Chen
Loughborough University

Daguang Han
Southeast University

Kaixin Hu
Chongqing Jiaotong University

Yu Zhang
Shenyang Jianzhu University

Guoqian Ren
Tongji University

Yanhui Liu
Southwest Jiaotong University

Yongquan Dong
Chongqing Jiaotong University

Yatong Yuan
China Construction Fifth Engineering Bureau

### 40.1 Introduction

Digital twins, as dynamic asset representations that mimic real-world behaviors, offer promising solutions for managing, planning, predicting, and demonstrating assets in the built environment (Chen et al. 2021).

These digital twins, based on data from physical assets or systems, facilitate improved decision-making, providing positive feedback to their physical counterparts. Various modeling approaches enable accurate representations of physical reality at different scales. Although numerous digital twins exist for the built environment, few can connect or share data across organizations, industries, or geographies due to limited interoperability.

The digital twin concept has been increasingly applied to various fields, overlapping with virtual simulation and numerical simulation in civil engineering. Building information modeling (BIM), which carries extensive information about buildings, is widely utilized as a digital twin carrier in engineering. Developed in the 1970s, BIM was defined by experts like Charles Eastman (Eastman et al. 2011). BIM technology and its applications are more advanced in the United States and some European countries than in China. European and American scholars have extensively studied BIM in the construction industry, with Caiyun Wan (Wan et al. 2004) providing recommendations for using BIM standard structural analysis models for pre-stressed loads and load combinations. Bridge Information Modeling (BrIM) is a BIM extension in the bridge domain (Costin et al. 2018).

As BIM-related standards and software expand in Europe, the United States, and Asia, BIM models become ideal data carriers for digital twin models (DTMs) in civil engineering. The digital twin BIM model (DT-BIM), built and updated on digital twin concepts, offers enhanced information processing capabilities and application prospects, serving as a precise digital description and information carrier for real-world physical objects. This chapter demonstrates the application of digital twin theory during the construction of a reinforced concrete arch bridge. Reinforced concrete arch bridges have proliferated since the 1800s, with nearly 80 worldwide featuring span diameters over 200m. Monier built the first concrete arch bridge in 1875, and Australian engineer Josef Melan improved the design by using steel as a skeleton in 1890. Continuous advancements have increased span lengths, exemplified by the Hoover Bridge in 2010, which utilized steel–concrete composite construction. By 2007, China led the world with 199 arch bridges featuring spans of at least 100m (Wang 2018).

The Rigid Skeleton Construction Approach is the predominant method for building large-span reinforced concrete arch bridges. The structural steel rigid skeleton (SSRS) is built first, followed by sectional concrete pouring to form the final arch structure. The steel arch skeleton’s position determines the bridge’s shape, making the accurate fabrication and installation of SSRS sections critical for construction quality. One challenge is obtaining precise SSRS section dimensions in a timely manner and controlling on-site installation.

DT-BIM is a digital model that manages and simulates the life cycle of physical objects. To maintain synchronization with real-world objects, DTM must integrate IoT technology for real-time updates. This approach enables predictive simulation, analysis, and visualization of physical models. Digital twin models have proven effective in constructing large-span reinforced concrete arch bridges. Ruodan Lu employed a slice-based object fitting method for automated modeling of point clouds in reinforced concrete bridges (Lu & Bralakis 2019), generating geometric digital twin models (GDTM). Their experiments showed an average modeling distance of 7.05 cm and a modeling time of 37.8 seconds. Masoud Mohammadi used the digital twin concept with UAV photogrammetry and TLS to evaluate and monitor a steel truss bridge in Australia, resulting in accurate data capture and 3D reconstruction models (Mohammadi et al. 2021).

To summarize, the digital twin concept is less widely used in bridge construction quality control. In this chapter, the GDTM is created using a series of algorithmic processes that begin with establishing point cloud data of stiff skeleton segments and end with this GDTM. The stiff skeleton's construction control is realized on this basis by combining mechanical information. Compared with previous methods, the developed GDTM can (1) not only provide precise 3D dimensions but also reduce the impact of human factors on data processing, and (2) be useful to control each key step to achieve a better overall force state based on the inherent mechanical information.

### 40.2 Literature Review

Creating a construction DTM involves three steps: (1) developing a GDTM; (2) predicting a DTM; and (3) generating a mechanical analysis DTM model by providing mechanical information, construction process analysis, and force control of the completed bridge. The key to realizing a DTM is acquiring consistent, comprehensive, and accurate object information through reality capture technology, which primarily utilizes 3D scanning and digital image processing methods.

Research into digital image processing for concrete structure detection has advanced significantly in the 21st century. Abdel-Qader compared four crack detection techniques, finding the fast Hal transform (FHT) to be the most reliable (Abdel-Qader et al. 2003). Yiyang proposed an algorithm for glass crack detection using segmentation and feature extraction (Yiyang 2014). In conclusion, digital image processing techniques effectively acquire and process object texture information but are unsuitable for precise geometry acquisition in complex steel structures like stiff skeleton segments.

The 3D laser scanning is widely used in capturing surface shapes and reverse modeling of complex geometries, such as body surface organ reconstruction (Zhang 2007) and steel bar corrosion pattern identification (Kashani et al. 2013). Combined with BIM technology and photogrammetry, 3D scanning manages project progress and quality inspection. S. Yoon explored optimal scanning arrangements (Yoon et al. 2018) for identifying positioning errors in prefabricated steel beam shear nails (Bosché & Guenet 2014). In addition, 3D scanning was employed to measure stone arch bridge surface alignment and analyze finite element simulations (Lubowiecka et al. 2009). C. Andreotti (Andreotti et al. 2015) used 3D scanning to detect minor masonry structure anomalies post-earthquake. These case studies confirm 3D laser scanning as a reliable method for obtaining GDTMs of bridge-like structures.

Prediction is crucial in DTM for structural objects. Case demonstrated a successful virtual assembly method for complex steel structures using generalized Procrustes analysis (Case et al. 2014). Zhou developed a mesh-based parameter extraction method for bolt hole features, enabling accurate prediction of alignment and stress in assembled steel structures (Zhou et al. 2021). To accelerate cable-stayed bridge construction, Donggun Kima devised a 3D laser point cloud-based method for measuring and predicting temporal variations in displacement between welded precast segments, reducing Cheonsa Bridge construction time by 10 days (D. Kim et al. 2020).

These cases indicate that predicting assembly behavior and actual construction of complex steel structures using 3D laser point clouds is feasible. However, bolted stiff skeletons require more stringent accuracy and prediction thresholds compared to welded prefabricated sections. Further verification of the method’s feasibility in actual engineering is needed.

Final quality of constructed targets relies on construction control. Uncertainties and risk factors arise during construction as the structure’s size and height increase. Seungho Kim focused on a five-stage construction process, demonstrating a reliable method for tracking construction progress via point clouds (S. Kim et al. 2020). Nisha Puria et al. proposed a semi-automated bridge monitoring method, with results indicating sensitivity to factors such as point cloud density (Puri & Turkan 2020). Yawei Qin combined 3D laser scanning and BIM technology for integrated engineering quality control but did not include mechanical behavior control in arch bridge construction (Qin et al. 2019). Research on point clouds for constructed object control has mostly focused on construction progress and quality assessment. However, none of the aforementioned cases address the mechanical properties of the constructed object. For complex rigid skeletons, structural behavior during construction directly impacts safety and final quality. Therefore, providing rigid skeleton DTM mechanical information is essential for constructing mechanical analysis DTM models and performing force control for completed bridges.
