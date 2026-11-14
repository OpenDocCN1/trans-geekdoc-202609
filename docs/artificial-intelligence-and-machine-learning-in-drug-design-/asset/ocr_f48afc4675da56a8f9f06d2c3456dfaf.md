agents to control the progression of a particular disease. Gene expression is a highly reliable approach to creating a ML model that screens genomic data. This analysis investigates the regulation of genes in normal and diseased states to provide a comparative analysis of both. Network-based ML models can be based on the genetic data provided by the screening to identify key protein or metabolic pathway data that are critical in disease progression [49]. ML models must be developed in a way that may further validate the target data obtained after prospective targets have been identified. To determine if a target is likely to have a specific ailment, AI models must effectively cross-validate the target data. A group of researchers designed an ML model that predicted disease-associated genes which could be potential drug targets based on genomic data and system analysis [50]. The ML-based approach included a range of data, including gene expression profiles, protein–protein interaction profiles, and others to predict the likelihood of druggable vs. non-druggable targets and morbid vs. normal genes. The authors also cross-validated the ML model to substantiate its robustness by training and testing multiple subsets of the data. This paper demonstrates the efficiency of ML-based frameworks in target identification and validation. Table 5.1 presents a few examples of AI models that have been incorporated to predict AMR genes based on the analysis of microbial genomic data.

# Table 5.1 AI models employed for predicting AMR genes.

| ML-based model | Purpose and application | Reference |
|---|---|---|
| DeepARG | Scans metagenomic data to predict AMR genes using deep learning | [43] |
| AntiSMASH | Predicts biosynthetic gene clusters of secondary metabolites in bacterial and fungal genomes using SVM, HMM, pHMM | [51] |
| Resistance Gene Identifier (RGI) | Predicts antibiotic resistomes from protein or nucleotide data based on homology and SNP models using HMM | [52] |
| ResFinder | Identification of acquired antimicrobial resistance genes in whole-genome using BLAST sequence analysis | [53] |
| ArgANNOT | Predicts existing and novel AMR genes in bacterial genomes using BLAST sequence analysis | [54] |
| PRGPred | Predicts domains of resistance gene analogues using SVMs | [55] |
| Meta-MARC | Predicts of diverse antimicrobial resistance sequences using hierarchical, DNA-based hidden Markov models | [56] |
| MEGAResand AMR++ | Classifies resistome sequences directly from FASTA using k-mer-based metagenomic classifier | [57] |
| ARGMiner | Analyzes all of the information available from several AMR gene databases and provides information on potential AMR genes carried by pathogens using RF algorithm | [58] |