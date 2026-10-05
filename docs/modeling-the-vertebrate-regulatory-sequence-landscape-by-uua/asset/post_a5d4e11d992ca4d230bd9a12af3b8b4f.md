
## Model performance evaluation

The prediction of models on different datasets was measured by the area under the receiver operating characteristic curve (AUROC). The accessibility prediction performance was evaluated on a completely held-out test chromosome, which was not used during hyperparameter optimization and had never seen by the training model to avoid information leakage.

We displayed the AUROC for each lineage for species-trained model. Using the binarized peak matrix derived from the mouse chromatin profile of 5,034 nuclei, we produced the dataset for model benchmark. Notably, our NvCA model outperformed models such as Nwawa¹ and scBase²² and classical frameworks such as Transformer and Recurrent Neural Network (RNN) evaluated by AUROC. To evaluate the predicted relationships in the held-out chromosome for test, we computed correlations between predicted and observed chromatin accessibility test profiles at the subcluster level. Adjusted mutual information (AMI) was used in quantifying the extent to which the predicted cell aligns with the actual cell types, offering a nuanced and informative assessment of the model's performance in capturing the underlying lineages.

## Cross-species prediction for UA elements

The unlabeled (UA) elements were defined by converting the coordinates of COREs in chicken, zebrafish and zebrafish genome reference (mm10) using UCSC liftOver and the available UCSC files. We made sequences uniform unifying the UA elements (500bp size with 100bp step size) using the ‘builds makindows -b UIA -w 500 -s 100’ command. The accessibility of sequences was predicted by the pretrained model and accelerate continuous signals. Based on the chromatin accessibility profiles, we identified the predicted accessible regions by running “macc3 bdgapeak” command. The conservation of sequences was represented by the ratio of UA elements predicted accessible to all UA elements. This was repeated for all combinations of fish, mouse, mouse, and zebrafish pretrained models with UA elements in other species.

## De novo prediction of single-cell tracks for human and mice

First, we firstly normalized accessibility profiles for each query with NvCA by running a forward pass on the peak set. We used the input DNA sequence as the output of bottleneck layer as a latent embedding for each peak. We then generated the accessibility profiles across all cells by the product of bottleneck layer with the weighted matrix extracted from the collected layer. The accessibility profiles served as the base for further analysis, including dimension reduction through uniform manifold projection (UMAP) and Singular Value Decomposition (SVD) with a resolution of 0.2 in Signatures³ pipeline. Finally, we utilized t-SNE to represent a representative predicted cell profile for human and mice.

## Predicting genome-wide chromatin accessibility for different species

We extracted 500bp window with a step size of 100bp to identify the different species of elements. By using the ‘buildseqs makindows -w 500 -s 100’, we extracted the sequences using the ‘to-getfasta fasta’ command. Applying the NvCA model trained on human mouse datasets, we predicted chromatin accessibility profiles within these windows. This enabled the generation of genome-wide predictions for each individual nucleus, which were aggregated at the subcluster level. To provide a comprehensive evaluation, we utilized the Genomics Viewer (IG-2-16),⁴⁵ displaying the predicted open regions and the experimental data data.

## Comparison of predicted and experimental human CREs

To assess the consensus between predicted and experimentally measured regulatory landscapes, we generated genome-wide cell-type specific sc-CREs (endothelial cells, macrophages, and smooth muscle) from CATLAS⁴⁶ (https://catlas.org/downloads/human/sigwig). The scATAC-seq signal charts were scaled to the [0,1] interval using min-max normalization to match the distribution of predicted-accessibility scores. The correlation analysis was performed using the ‘bi.wigSummary’ function from deeptools (v3.5.2) with the ‘bins’ argument.⁴⁷ We retained the normalized signal with a resolution of 0.01 in both predicted and experimental scores to ensure robust correlation. We identified the predicted signal and interacted with cCREs from NvCA encoder v3 (https://github.com/jue-lab/NvCA),⁴⁸-overlapping peaks were reported as “ne-CREs”. With top peak categories, cell-type-specific distributions and nucleotide-resolution profiles were computed and summarized.

## Motif identification and visualization from NvCA

To extract motifs from our NvCA, we utilized the TF-Motisif that combines single-nucleotide importance scores for generic sequence patterns. By sampling 10,000 cells and evaluated the saliency scores for each task, we improved the computational efficiency of TF-Motisif. Motif similarity was then queried by the JASPAR2024 database using TomTom algorithm⁴⁹ We applied motif⁵⁰ package to visualize the relationship between motifs derived from NvCA trained for species.

e14 Cell 188, 5343–5362.e1–e16, September 18, 2024

## Cell Resource

The mouse embryo cREs were categorized into two classes: broad and narrow cREs, as described previously. We generated regions by tiling the cREs (500bp with 100bp step size) using the "tools makewindows -b IU -s 100" command. For each region, we extracted the sequences from the forward strand and input into the mouse model to predict accessibility.

## Cross-species prediction of homologous gene chromatin accessibility

To validate the generalization ability of the model, we utilized the predicted mouse model to predict the chromatin accessibility on homologous genes of HGB1, mouse Hb-b and human HGB1. The sequences 500bp upstream of the target gene TSS were extracted using "bedseq gefasta" and input as a forward propagation to predict the accessibility.

## Regulatory sequence identification (Wait, the OCR text has some fragmented sections. Let's re-align based on the provided flow.)

*Note: The OCR text provided contains fragmented sections at the end. I will process them as they appear in the source.*

## Regulatory sequence identification
(The source text becomes fragmented here, I will reconstruct based on the available OCR blocks provided in pages 34-35).

## Fine-mapped prediction and validation

## Causal non-coding QTL prediction and validation

## Functional prediction of synthetic mutagenesis

## Benchmark of NvCA model in predicting effect with MPRA and multi-omic model
