
## 6.7 AI-Based Toolkits Used for Drug Discovery

Table 6.2 presents some ML tools used currently for drug design and development.

Deep learning (DL) has emerged as a powerful approach in various fields, including drug discovery. DeepChem uses deep learning methods to develop models that predict essential features of chemicals, such as activity against a certain target or toxicity. Models like these learn from enormous volumes of information and can reveal complicated patterns and correlations that older approaches may miss. Figure 6.7 explains the workflow of DeepChem.

Deep learning’s capacity to automatically identify useful characteristics from unprocessed molecular data is one of its primary advantages in drug development. Deep learning models may acquire and adjust to the most useful interpretations directly from the data, rather than depending on predetermined descriptors or features. Deep learning models can capture delicate and detailed molecular properties that are essential to their biological function because of their flexibility. It can handle a variety of molecular data formats, such as 1D patterns (such as proteins or DNA patterns), 2D models (such as biochemical graphs), as well as 3D structures. This adaptability enables the combination of many forms of data to produce more accurate forecasts [68].

Table 6.2 Machine learning toolkits used widely for drug design and development.

| S. no | ML tools | Function | Web Link |
|---|---|---|---|
| 1 | AlphaFold | Protein fold prediction | https://alphafold.ebi.ac.uk/ |
| 2 | DeepChem | Drug discovery | https://deepchem.io/ |
| 3 | AMPL—atom modeling pipeline | Data preparation for drug discovery | https://github.com/ATOMconsortium/AMPL |
| 4 | Open Drug Discovery Toolkit (ODDT) | Molecular docking and prediction | https://pypi.org/project/oddt/0.1.9 |

- stages of workflow in deepchem
- 1. Dataset Information
- 2. Accessing the Data
- 3. creating numpy dataset
- 4. Molecular Fingerprints
- 5. Graph Convolutions
- 6. Splitting up datasets

Figure 6.7 DeepChem workflow chart.

## 6.8 Applications of AI in Molecular Docking

Traditional drug and vaccine development are difficult endeavours that seek to produce novel molecules with a variety of desirable characteristics [69]. As a result, developing drugs and vaccines is very expensive, time-consuming, and has a low success rate. In the vast molecular space, the efficient discovery of numerous plausible, unique, and new candidate molecules has been revolutionized by advancements in artificial intelligence (AI) and machine learning (ML)-based models, which has helped to resolve this conundrum [70].

The use of AI-powered molecular docking in drug development is becoming more prevalent thanks to advancements in docking algorithms, neural networking models, and the availability of open-access data on ligands and targets. Initially, molecular docking was primarily used to study the interactions between ligands and targets. However, in the modern era, the applications and scope of molecular docking have expanded and evolved [71].

### 6.8.1 Prediction of Drug–Target Interactions

Computational tools are being developed to predict the activities of new molecular targets for drug repurposing. These tools work alongside experimental drug–target discovery efforts, providing data on compound-target interactions. Machine learning (ML) models, for example, use the structures of drugs and targets to guide their predictions in a drug–target space. This approach helps in understanding the interactions between compounds and targets [72].

In addition, AI and ML methods have been employed to predict target activities for kinase inhibitors and other compound classes. Researchers have used multi-kernel learning and chemical fingerprints to forecast the affinities of compound kinase targets. Deep learning techniques, such as convolutional network models, have also emerged for predicting drug-target interactions (DTIs). These techniques improve our understanding of the factors influencing DTI prediction and enable computational drug repurposing [73].

Atom-wise, a biopharma company, utilizes 3D identification and prediction of small structures. They employed this method to identify active molecules for the Ebola virus and successfully developed two new drugs using artificial intelligence. These drugs have demonstrated greater effectiveness than previously available options. However, to ensure safety and other considerations, peer review and regulatory oversight are necessary before these drugs can be widely utilized [74].

### 6.8.2 Drug Repurposing

Discovering new therapeutic uses for existing drugs, developing drug candidates, and exploring natural products are exciting avenues in drug discovery. One promising approach is drug repurposing, which involves repurposing approved medications, candidates in development, or synthesized compounds for new therapeutic purposes. To expedite this process, docking, a virtual screening technique, allows for rapid screening of approved drugs, phytochemicals, or pre-synthesized compounds against specific targets of interest.

Innovative deep learning (DL) methodologies have revolutionized de novo drug design. State-of-the-art DL models like Generative Autoencoders (GAE) and Generative Adversarial Networks (GAN) have transformed the way new molecules are designed [75]. Recently, generative models such as variational autoencoders (VAE) have been utilized to generate atom sequences, resulting in the production of diverse and distinct drug molecules [76]. These powerful autoencoders, encode molecules into a vector that captures crucial characteristics such as bond order, element properties, and functional groups [77]. This cutting-edge approach opens up new possibilities for innovative and unique drug design.

The COVID-19 pandemic has caused the world to realize the need for novel drug development at this historic time. This process has been greatly aided over the past year by AI/ML [78]. A computational drug discovery system typically has three components: target discovery, small molecule drug discovery, and clinical trial outcome predictors. The fusion of artificial intelligence and core chemistry in computational drug design holds tremendous promise for revolutionizing the field. Researchers are eagerly seeking high-quality research on drugs and clinical data to harness the full potential of this innovative approach [79]. By combining the power of artificial intelligence with deep insights from rigorous scientific investigations, computational drug design has the potential to unlock ground-breaking discoveries and transform the landscape of drug development. The quest for this cutting-edge synergy between AI and chemistry drives the pursuit of excellence in drug research and clinical investigations, pushing the boundaries of what is possible in the world of medicine.

Artificial intelligence (AI) facilitates the use of the continuously growing open-access information sources in databases of biological, chemical, and structural activity. Therefore, predictions of binding affinity of molecules are more precise [80]. In this text, pose generation and scoring have been handled by deep learning neural networks. In order to study the convolutional neural network, protein–ligand complexes were designed as three-dimensional cages. Similar to the machine learning models and other non-neural network algorithms, deep learning scoring functions have produced superior results [81]. AI-based ML makes predictions based on blind data by learning from the properties of the available data. These strategies might not be preferable to recently identified therapeutic targets because they have not undergone in-depth analysis and lack chemical, structural, and bio-activity data [82].

In order to predict binding affinities in classical scoring, predetermined function forms can be improved upon or replaced by machine learning algorithms. In virtual screening, these have also been used to distinguish between binders and non-binders [83]. Nonparametric learning, or machine learning, does not use predefined functions. Instead, results are extracted from the data used as input. The output could be continuous, similar to nonlinear regression. This then makes it possible for precise and varied scoring. The random forest (RF)-Score was among the first machine learning scoring methods to outperform conventional scoring methods. Additionally, support vector machines (SVM) and logistic regression were applied to enhance docking-based binding affinity prediction [84].

## 6.9 Challenges and Limitations of AI-Based Molecular Docking

The use of docking tools and the study’s findings presents a number of challenges. Each program reportedly has its own restrictions and flaws. Programs therefore are unable to produce the same output as reliably [85]. Additionally, if the amount of chemical structure processed exceeds the capabilities of the developed software, the program might not
