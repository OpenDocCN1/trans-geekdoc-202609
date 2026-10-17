
![](img/3c3f2c338e164e667157cfff90de41d7_2_0.png)

**Figure 1: Clinical validation framework and experimental setup**
AI=artificial intelligence. *Publicly available. †Limited access.

median age 73 years [range 39–89] with histologically proven NSCLC referred for radiotherapy between 2001 and 2015 at the Dana-Farber Cancer Institute and Brigham and Women’s Hospital, Boston, MA, USA. Target volumes were delineated by a single radiation oncologist (RHM; referred to as R1). 269 (54%) patients from this dataset were used for training, 96 (19%) for tuning, and 136 (27%) for testing. The test set was identical to that used in a published study, in which contestants competed to develop the best segmentation model. Using volumetric dice (VD) and surface dice (SD) metrics, the top solution from that contest was compared to results obtained here.

model structure closely followed that of original implementation with encoder and decoder paths connected via skip connections. Architecture parameters (eg, convolution and pooling kernel sizes; appendix p 14) and model hyperparameters (eg, learning rate and batch size; appendix pp 6–7) were fine-tuned using nnU-Net (version 1.6.5).

## Data preprocessing

Data preprocessing involved resampling all data to a common voxel spacing of 1×1×3 mm³, using linear interpolations for CT images and nearest-neighbour interpolations for segmentations. CT Hounsfield units were normalised by clipping to 0.5th and 99.5th percentiles. Distributions of dataset characteristics, including gross tumour volume, CT image slice thickness, and use of intravenous contrast are given in the appendix (pp 62, 64–65). Data augmentation details during training are also given in the appendix (p 6).

## Model development

We used U-Nets, fully convolutional neural networks with CT volume inputs and corresponding binary segmentation outputs. Our assisted and automated pipelines consisted of four three-dimensional (3D) U-Net models for the localisation and segmentation of lungs, primary tumour, and involved lymph nodes (figure 2A, B). Overall

## Metrics

We used multiple metrics to assess model performance (appendix p 15), including VD (spatial overlap of two volumes, with 0 being no overlap and 1 being perfect overlap), as well as SD (fraction of surface within a threshold distance from another, with 0 being none of the surfaces within tolerance and 1 being entire surfaces within tolerance). We used the 75th percentile of interobserver variability (1.9 mm) as the threshold (appendix p 25–26).

## Benchmarks

We developed the interobserver benchmark using the multi-delineation dataset of 20 patients (stages IA–IIIB; 12 [60%] male, 8 [40%] female; median age 67 years [IQR 57–71]) with histologically confirmed NSCLC referred for radiotherapy at Maastro Clinic. Manual tumour delineations were done by five radiation oncologists, in addition to R1 (appendix pp 18, 68). Comparisons were drawn between the two residents and four attendings involved in the interobserver benchmark. The intraobserver benchmark was developed using 21 randomly sampled patients from the Harvard-RT1 test set. R1 did the segmentation task twice with a 3-month washout period.

![](img/3c3f2c338e164e667157cfff90de41d7_3_0.png)

## Figure 2: Primary validation results and comparison with benchmarks

Schematics for the assisted (A) and automated (B) segmentation pipelines. (C) The model performance in localising and segmenting primary non-small-cell lung cancer tumours and involved lymph nodes, as validated on five increasingly external datasets using the volumetric dice metric.

## Primary validation

We did further validation on four increasingly external datasets, with increasingly diverging characteristics from those of the training data: Harvard-RT2 segmented by other experts, RTOG-0617 from other institutions, and NSCLC-radiogenomics and Lung-PET-CT-Dx from diagnostic radiology. Harvard-RT2 included 387 patients (stages IA–IV; 165 [43%] male, 222 [57%] female; median age 69 years [range 32–92]) with histologically confirmed NSCLC referred for radiotherapy between 2011 and 2017 at the Dana-Farber Cancer Institute and Brigham and Women’s Hospital. Tumour volumes were delineated by multiple physicians (appendix p 19). RTOG-0617 included 403 patients with histologically confirmed NSCLC (stages IIIA–IIIB; 223 [55%] male, 155 [38%] female, 25 [6%] unspecified; median age 64 years [IQR 57–70]) from the phase 3 RTOG-0617 trial (NCT00533949). Patients were treated with radiotherapy between 2007 and 2011 at 185 institutions across the USA and Canada (appendix pp 20, 69). NSCLC-radiogenomics included 142 patients with histologically confirmed early stage NSCLC (pathological stages T1–3, N0–2, and M0–1; 124 [77%] male, 38 [23%] female; mean age 68 years [range 42–86]) referred for surgical treatment at Stanford University School of Medicine (n=67) and Palo Alto Veterans Affairs (n=75) in California, USA, between 2008 and 2012. Tumour segmentations were done by two thoracic radiologists (appendix pp 22, 70). Lung-PET-CT-Dx included 307 patients with histologically confirmed NSCLC (clinical stages T1–4, N0–3, and M0–13; 163 [53%] male, 144 [47%] female; mean age 61 years [range 28–90]) imaged at the Second Affiliated Hospital of Harbin Medical University, Harbin, China. Tumour location was annotated using per-slice bounding rectangles by five thoracic radiologists (appendix pp 23, 71).

## Functional validation

Data used in the dosimetric analysis were from a random quartile-based subset of 28 patients in the RTOG-0617 dataset (appendix p 44). Dose coverage was compared between the planning target volume as used in the RTOG-0617 clinical trial and its AI-generated counterpart, generated from the gross tumour volume (appendix p 7). Two common dose metrics were calculated: V95, percentage target volume receiving at least 95% of the prescription dose; and D95, dose covering 95% of the target volume. Test-retest stability (geometric overlap between segmentations generated from different CT images of the same patient) was assessed using RIDER,24 which included 26 patients with NSCLC (primary tumour ≥1 cm; 12 men, 14 women; mean age 62 years [range 29–82]), each of whom underwent two CT scans of the chest within 15 min. Images were acquired between January and September, 2007, at the Memorial Sloan-Kettering Cancer Center, New York, NY, USA. Tumour segmentations were done by two thoracic radiologists (appendix p 72). Additionally, we tested the assisted models’ stability as a function of variation in input data by simulating multiple experts’ placement of seed points (50 simulations). Random seed points were generated within a 50 mm cube around the tumour’s centre of mass, and we measured the geometric overlap between the resultant segmentations. Timeframe stability between 3D and 4D CT data was tested in Harvard-RT2 (n=186 single timeframe 3D CT vs n=201 multi-timeframe 4D CT). Model accuracy was assessed using CT of a thorax phantom containing 12 synthetic lung lesions (10 mm and 20 mm in effective diameter, six per lung). The phantom was scanned at Columbia University Medical Center, New York, NY, USA (appendix p 24).25 Lesion volume as calculated from our AI-generated segmentations was compared with that of three previously published segmentation models.26 Model performance based on the use of intravenous contrast in images (detected using a published algorithm27) was assessed through subgroup analysis. DSB conducted the model failure mode analysis by qualitatively assessing model results on the RTOG-0617 dataset and identifying cases of under-segmentation or over-segmentation.

(expert assisted; appendix pp 11, 73). Testing was done in a simulated clinical setting within MIM, the software used for this task at our institution (appendix p 74). Experts were provided with the following information per patient: age, sex, Eastern Cooperative Oncology Group score, histology, stage, and primary tumour lung lobe. Experts were also surveyed before, during, and after reviewing each case. After each case, experts were asked to qualitatively rate the task difficulty and quality of provided segmentations. Time for task completion was recorded automatically in the background. We used time measurements to compare between the de novo, expert-assisted, and AI-assisted groups. Correlation between time and segmentation metrics (VD and SD) was also measured. Details on ethics approval and patient consent for the various datasets are given in the appendix (pp 1–6).

## End-user testing

## Statistical analysis

We recruited and obtained written informed consent (under protocol DF/HCC 20-328) from eight radiation oncologists (DSB, JMQ, HR, SP, AS, LCP, BHK, and RHM) from the Department of Radiation Oncology at Brigham and Women’s Hospital. Experts had varying degrees of experience: three attendings (1, 2, and 9 years of experience) and five residents (appendix pp 9–10). Data used were a random quartile-based subset of 28 patients in the RTOG-0617 dataset, further divided into two groups of 14 patients each (appendix p 44). In the first group, experts were asked to perform the segmentation task de novo. For the second group, experts were asked to rate and edit a provided segmentation while masked to its source. In this second group, for ten patients, automated segmentations from the assisted pipeline were provided (AI assisted). For four patients, clinical segmentations from RTOG-0617 were provided

All statistical tests done were non-parametric, with a two-tailed p value of less than 0.05 indicating significance. For two dependent groups, we used the Wilcoxon matched-pairs signed rank test. For two independent groups, we used the Mann-Whitney U rank test. For three or more independent groups, we used the Kruskal-Wallis H-test. For measuring correlation between two groups, we used the Spearman rank-order correlation coefficient. All analyses were done in python (version 3.8.0).

## Role of the funding source

The funders of the study had no role in study design, data collection, data analysis, data interpretation, or writing of the report.

## Results

Interobserver benchmark was VD 0.83 (IQR 0.77–0.88) and SD 0.72 (0.61–0.81; appendix pp 25–26). AI versus R1 yielded VD 0.91 (0.83–0.92) and SD 0.86 (0.71–0.91), a significant improvement over the benchmark with VD (p=0.0062) and SD (p=0.0005; appendix pp 27–28). Additionally, AI versus R1 was found to be inversely correlated with the IQR of variability among all six experts (Spearman’s r=–0.74; p=0.0002; appendix p 29). With AI segmentations as reference, non-significant differences were detected between residents and attendings (appendix p 30).

Intraobserver benchmark was VD 0.88 (IQR 0.83–0.90) and SD 0.85 (0.80–0.93; appendix p 31). AI versus R1’s first read yielded VD 0.86 (0.83–0.87) and SD 0.79 (0.72–0.90), with similar results for the second read (appendix p 33). For VD, non-significant differences were observed when both results were compared with the benchmark. For SD, AI versus R1’s first read was non-significantly different than the benchmark, while AI versus R1’s second read was significantly lower (p=0.043; appendix pp 32–33).

First, we tested on the internal Harvard-RT1 dataset, also segmented by R1. Results of the assisted primary tumour
