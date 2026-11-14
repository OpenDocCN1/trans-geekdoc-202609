
![](img/9a8b0347872e9b0be4401898e8cd724c_484_0.png)

Figure 14.3 An example of a transformer model used in bioinformatics, together with the TransEPI frameworks (Shuang et al., 2023) [58].

(genotype) and the environment. Deep learning algorithms are used in phenotypic classification to categorize or classify phenotypes according to particular traits or attributes [61]. Data collection, data processing, model design, model training, model assessment, and model deployment are all steps in the phenotypic classification process that uses deep learning [61, 62] (Figure 14.4).

Being aware of the fact that the effectiveness of deep learning for phenotypic classification relies on the availability and caliber of labeled training data, the selection of suitable features or representations, the design of the model architecture, and the optimization of

![](img/9a8b0347872e9b0be4401898e8cd724c_484_1.png)

Figure 14.4 Phenotypic classification process using deep learning.

hyperparameters [63] is important. Deep learning models for phenotypic categorization can be difficult to interpret and explain since they frequently operate as “black boxes,” making it difficult to comprehend the logic behind their predictions [61].

## 14.5 Deep Learning-Based Prediction of Altered Genes and mRNA Levels in AD

When several biomarkers or gene expression data are utilized to predict the risk of AD, machine learning techniques are widely suggested as a solution [64]. In gene expression datasets, where the number of genes is often in the tens of thousands and generated from a few hundred samples, the “curse of dimensionality” affects machine learning methods. Datasets collected for AD research usually include this range of sampling [65]. Researchers typically merge many datasets to create a larger dataset with more samples since machine learning requires a greater number of samples [64]. Machine learning studies on gene expression data frequently start by eliminating superfluous genes or selecting differentially expressed genes to reflect the samples.

The need for feature engineering is decreased and, in many cases, eliminated by deep learning, a branch of machine learning [66]. CNNs are among the deep learning techniques whose effectiveness in categorizing pictures has been demonstrated even with less data [67]. Deep learning frameworks have been applied to genetic research to examine molecular phenotypes that foretell the consequences of noncoding mutations [42], differential gene expression [68], and possible transcription factor binding sites [69]. To predict chromatin properties like transcription factor binding or DNase hypersensitivity from DNA sequences, these programmes leverage CHIP-Seq or DNase-Seq data as training data. Deep learning has recently been used to analyze gene regulation and capture mutations, suggesting its potential to further our understanding of epigenetic control [70]. Additionally, CRISPR guide RNAs are designed by utilizing deep learning-based gene characteristics in gene therapy [71]. In order to determine population-based genetic risk variation for human illnesses and phenotypes, genome-wide association studies (GWAS) employ a statistical methodology that takes into account one single-nucleotide polymorphism (SNP) at a time across the whole genome [16]. The so-called high-dimension low-sample-size (HDLSS) problem [17], which is known to affect phenotypic prediction using genetic variation, makes it difficult to utilize deep learning for GWAS; hence, it has not been done yet. In order to tackle this issue, feature reduction techniques have been widely adopted [18]. However, feature reduction with high-dimensional genomic data is difficult owing to an NP-hard problem [19]. As a result, research is being done to address these drawbacks and construct a deep learning framework to find genetic variations using whole-genome data.

CNNs are frequently employed in AD detection utilizing image-based data such as MRI [72] or diffusion tensor imaging (DTI) [73]. This is similar to other image classification challenges. Either the CNN or the non-image data must be modified and tailored in order to employ the CNN with non-image data (such as gene expression). Using t-SNE [74], Sharma et al. (2019) [75] suggested a technique (dubbed “DeepInsight”) to transform the non-image data into a 2D image, and a kernel principal component analysis (kPCA) then fed the modified data into the CNN. Authors used t-SNE or kPCA to bring related genes near to one another on a 2D picture plane because they believed that doing so would result in images that were suitable for CNN models. The discriminative qualities of genes are not taken into account by either t-SNE or kPCA, which are both unsupervised machine learning methods for visualizing high-dimensional data in a low-dimensional environment. Gene expressions are suitable for image-based classifiers like CNN thanks to a revolutionary image-formation approach that transforms a one-dimensional gene expression into a discriminative 2D picture. Fisher distance criteria, which maximize the distance between classes and minimize the variation within classes [76], was used in the proposed model to categorize the DEGs (Figure 14.5). Deep learning tactics that have frequently been used to propose a solution to predicting the risk of AD using multiple biomarkers or gene expression data are depicted in Table 14.1.

The image-based representation technique is carried out in two steps: first, the gene is categorized for discriminating power (that is, control vs. illness), and then, using their discriminating power, they are mapped into 2D pictures. The Convex Hull algorithm is used to create a minimal rectangle in order to reduce the sparse areas and produce a compact picture. In order for the minimal rectangle to fit within the 2D coordinate system, it is rotated. Each gene is positioned in the 2D picture at its correct location using the location system (Kalkan et al. [76], (2022)).

![](img/9a8b0347872e9b0be4401898e8cd724c_486_0.png)

Figure 14.5 Use of linear discriminant analysis to locate the genes in the 2D image.

Table 14.1 Deep learning tactics for predicting Alzheimer's disease risk using gene expression.

| Machine learning model | Dataset | Sample size for AD patients | Number of selected genes | Outcome (AUC) | Reference |
| :--- | :--- | :--- | :--- | :--- | :--- |
| CNN | GSE63060 + GSE63061 + GSE140829 | 1,262 | 482 | 0.875 | [76] |
| DNN | GSE63060 | 145 | 353 | 0.874 | [64] |
| | ADNI | 63 | 922 | 0.657 | [64] |
| SVM | GSE33000 + GSE44770 | 439 | 35 | 0.511 | [77] |
| | GSE63061 | 139 | 188 | 0.804 | [64] |
| | GSE5281 | 87 | 1,001 | 0.894 | [78] |
| | GSE63060 + GSE63061 | 245 | 3,601 | 0.859 | [79] |
| RF | GSE33000 + GSE44770 | 439 | 35 | 0.531 | [77] |
| | GSE63061 + DCR | 118 | 12 | 0.724 | [80] |

## 14.6 Deep Learning with Neuroimaging and Genomics in Alzheimer's Disease

The notion of combining neuroimaging and genomics has been around for at least two decades, and it was originally intended to leverage the concept of intermediate endophenotypes by combining the advantages of both types of research [81, 82]. This ensemble technique was formerly known as image genetics or imaging genomics, which are both interchangeable terms. These days, it is often referred to as “neuroimaging genomics,” which is an example of how the two disciplines of “neuroimaging” and “genomics” overlap [83]. The Enhancing Neuro Imaging Genetics through Meta-Analysis Consortium (ENIGMA) [84], which aims to comprehend how psychiatric disorders affect the brain by combining neuroimaging (such as MRI, diffusion tensor imaging, and functional MRI) and genomics (such as GWAS) data, is a notable example of neuroimaging genomics [84, 85].

The idea of intermediate endophenotypes in neuroimaging was thought to provide quantitative measurements for behavioral phenotypes, perhaps leading to a relationship between genes and behavioral phenotypes [86, 87]. The quantitative biomarkers of brain activity recorded by neuroimaging modalities are known as intermediate endophenotypes, and they may be used to assess neurobiological changes in brain processes impacted by conditions like AD [88]. According to certain theories [89, 90], AD-associated genetic variations may appear in the intermediate endophenotypes that may be evaluated using neuroimaging modalities and may be directly connected to AD. Additionally, it has been suggested that the problem of small effect sizes in genomics investigations can be resolved using the intermediate endophenotypes of neuroimaging [89, 90]. Contrarily, it is suggested that the results of neuroimaging genomics are only partially replicated, which may be due to small sample sizes, shaky study designs, and a dearth of multiple testing corrections [91, 92].

Such research on the combination exploration of neuroimaging and genomes or neuroimaging genomics are still uncommon in the present literature, particularly for AD prediction [93]. The design of integrating neuroimaging and genomics to predict AD risk is depicted in Figure 14.6.

## 14.7 Limitations and Challenges in Deep Learning-Based Neuroimaging Genomics Investigations in Alzheimer's Disease

Lack of cross-validation methods, conventional benchmark models, and large-scale, standardized benchmark datasets, hardware limitations, difficulty in understanding deep learning models, lack of open-source software platforms/packages, and instability and difficulties with mode collapse in the GAN model are just a few of the major problems
