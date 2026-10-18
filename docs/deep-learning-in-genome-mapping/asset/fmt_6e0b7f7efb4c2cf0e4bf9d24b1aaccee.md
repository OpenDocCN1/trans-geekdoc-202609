
We are generating vast amounts of data, yet its relevance remains uncertain. Data engineering has traditionally focused on big data-storing and processing large datasets—but the real value lies in transforming data into knowledge. Deep learning bridges this gap by developing algorithmic expertise in specific domains. This research introduces Domain Driven Data Engineering, emphasizing that data engineering processes are shaped by their application domain. We propose a refined roadmap of data engineering phases based on this methodology, enhancing previous frameworks. For further insights, you can explore this roadmap or this methodology.

## 1\. Introduction

Knowledge discovery is the intelligent process of extracting valid, novel and useful patterns from data, extending beyond logical analysis ([Yamazaki et al. 2022](#ch3.xhtml#ref3_124), [Li et al. 2021](#ch3.xhtml#ref3_62)). It involves data management, cleaning, preprocessing, modeling, and evaluation, alongside usability and knowledge presentation. This chapter explores knowledge discovery techniques across various models, knowledge engineering and technology-driven applications for efficient pattern identification in large datasets. It also examines application engineering, discovery challenges, confirmatory research costs, and connections to machine learning, data visualization, and automated programming.

Machine learning (ML) is evolving rapidly, driven by deeper insights into human neural networks. Once limited to experts, ML now tackles complex problems in image/audio processing, natural language understanding, automation, and autonomous systems ([Samek et al. 2021](#ch3.xhtml#ref3_94), [Pulvermüller et al. 2021](#ch3.xhtml#ref3_85)). Artificial neural networks excel in solving intricate challenges despite transparency concerns ([Yang and Wang 2020](#ch3.xhtml#ref3_125), [Galván and Mooney 2021](#ch3.xhtml#ref3_31)). Their success spans diverse applications, from gene clustering to optimizing data engineering processes ([Liu et al. 2021](#ch3.xhtml#ref3_62), [Taye 2023](#ch3.xhtml#ref3_111)). This research emphasizes knowledge discovery, advocating for pre-aggregation in data engineering to refine patterns and enhance predictive accuracy. Proper data assembly ensures meaningful insights, validating theoretical models for practical use.

![Figure 1: Organization diagram.](images/fig3_1_C.jpg)

Figure 1: Organization diagram.

### 1.1 Core Components in the Medical Field

Deep Learning and Medical Data Engineering for Knowledge Discovery integrates AI-driven techniques with healthcare data processing to enhance patient outcomes and clinical decision-making.

*   Deep Learning: Advanced models like CNNs, RNNs, and transformers analyze medical images and patient records, identifying patterns beyond human perception to improve diagnostics, treatment planning and prognosis prediction.

*   Medical Data Engineering: Focuses on efficient data management, including preprocessing, transformation, and feature engineering, ensuring usability while maintaining privacy and security.

*   Knowledge Discovery: Extracts trends, risk factors and causal relationships in disease patterns, informing clinical guidelines and treatment strategies through deep learning pipelines.

Applications in Healthcare:

*   Medical Imaging: Deep learning models enhance CT, MRI, and X-ray segmentation and classification for accurate disease detection.

*   Genomics: Identifies mutations and patterns in genetic data linked to diseases.

*   Electronic Health Records (EHR): Analyzes patient histories, symptoms, and medications, to predict disease progresses and side effects.

*   Predictive Modeling: Forecasts patient outcomes and recommends optimal treatment paths.

This rapidly evolving field is crucial for advancing next-generation healthcare and personalized medicine.

## 2\. Background and Motivation

Over a decade ago, during the era of narrow AI, researchers focused on how humans learn from stimuli like images, voice, and touch ([Sejnowski 2020](#ch3.xhtml#ref3_102), [Sarker 2021](#ch3.xhtml#ref3_96)). AI advancements raised concerns about automation displacing jobs, with some fearing professional alienation ([Xu et al. 2021](#ch3.xhtml#ref3_58), [Castiglioni et al. 2021](#ch3.xhtml#ref3_14)). Now in the age of general AI, deep learning has evolved rapidly, shaping policy, industry, and open-source initiatives ([Wang et al. 2023](#ch3.xhtml#ref3_115), [Saxe et al. 2021](#ch3.xhtml#ref3_99)). This shift emphasizes new architectures, data engineering, and computing strategies, solidifying deep learning theory ([Saha et al. 2021](#ch3.xhtml#ref3_92), [Janiesch et al. 2021](#ch3.xhtml#ref3_45), [Matsuo et al. 2022](#ch3.xhtml#ref3_71), [Gupta et al. 2021](#ch3.xhtml#ref3_35)).

As health and security challenges grow, adopting Knowledge Discovery in Databases (KDD) within ethical frameworks becomes crucial Solutions to pressing global issues will continue to expand, sparking debates and competition ([Hendrycks et al. 2021](#ch3.xhtml#ref3_40), [Cobbe et al. 2021](#ch3.xhtml#ref3_18)). Economic, cultural, legal, environmental, social, and political complexities demand multidisciplinaryAI-driven approaches. With increasing data on case types and trends, AI algorithms enhance problem-solving across diverse domains ([Djurayeva 2023](#ch3.xhtml#ref3_23)).

This section explores the evolution of data science, data engineering, and deep learning, covering key technologies, techniques, and algorithms. The survey is divided into six subsections ([Yang et al. 2022](#ch3.xhtml#ref3_127), [Sarker 2021](#ch3.xhtml#ref3_96)):

1.  Introduction to Data Science.

2.  Detailed discussions on data mining, statistics, machine learning, data engineering, and knowledge discovery.

3.  Big data platforms for data engineering.

4.  Advancements in deep learning ([Sharifani and Amini 2023](#ch3.xhtml#ref3_104)).

In recent decades, the surge in data generated by human activity has accelerated knowledge development ([Kaluarachchi et al. 2021](#ch3.xhtml#ref3_49), [Sharma et al. 2021](#ch3.xhtml#ref3_105)). Knowledge discovery applications—such as classification, clustering, outlier detection, and association rule mining—support business evaluation, fraud detection, and recommendation systems ([Pan et al. 2022](#ch3.xhtml#ref3_79), [Campesato 2020](#ch3.xhtml#ref3_13), [Zhang et al. 2020](#ch3.xhtml#ref3_38)). Data science has emerged as an interdisciplinary field integrating data mining, statistics, data engineering, and machine learning ([Yeturu 2020](#ch3.xhtml#ref3_129), [Sharma et al. 2021](#ch3.xhtml#ref3_105), [Sarker et al. 2020](#ch3.xhtml#ref3_97)). Machine learning a subset of AI, extracts knowledge from data and intersects with data science. Its integration with data engineering enhances deep learning capabilities. This work, based on ISiC’s tutorial and related research, explores deep learning concepts, data engineering for knowledge discovery and model interpretability ([Pramod et al. 2021](#ch3.xhtml#ref3_84), [Mukhamediev et al. 2022](#ch3.xhtml#ref3_75)).

### 2.1 Foundations of Deep Learning

Deep learning has transformed AI research excelling in object recognition, semantic detection, NLP, machine translation, and autonomous driving. By leveraging vast data, and advanced algorithms, it has surpassed traditional methods across industrial and scientific domains, becoming a key approach in business applications. Key aspects in knowledge discovery include:

1.  Multi-Layered Perceptron (MLP): Since the 1980s, backpropagation enabled training of deep networks, forming the foundation for modern deep learning ([Worden et al. 2023](#ch3.xhtml#ref3_121)). Convolutional and recurrent networks are specialized versions of MLP, balancing simplicity and depth (Ünal and Başçiftçi 2022).
