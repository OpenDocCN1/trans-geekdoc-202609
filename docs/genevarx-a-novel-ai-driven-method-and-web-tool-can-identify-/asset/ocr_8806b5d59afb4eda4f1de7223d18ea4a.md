# GENEvaRX: A novel AI-driven method and web tool can identify critical genes and effective drugs for Lichen Planus

Turki Turki a,*, Y.-h. Taguchi b,*

a King Abdulaziz University, Department of Computer Science, Jeddah 21589, Saudi Arabia b Chuo University, Department of Physics, Tokyo 112-8551, Japan

# ARTICLE INFO

+   Dataset link: GSE63741, GSE193351, GSE52130
+   Keywords:
+   Lichen planus
+   Gene expression
+   Therapeutic targets
+   Drug discovery
+   Machine learning
+   Novel AI application in dermatology

# ABSTRACT

Lichen planus (LP) is an autoimmune disorder diagnosed based on physical symptoms and lab tests. Examples of symptoms include flat bumps, and itchy and purplish skin while lab tests include a shave biopsy of the lesion. When the pathology report shows consistency with LP and is negative for potential triggers for an allergy test and hepatitis C, a dermatologist typically prescribes corticosteroid in the form of pills or injection into the lesion to treat the symptoms. To understand the molecular mechanism of the disease and thereby overcome issues associated with disease treatment, there is a need to identify potential effective drugs, drug targets, and therapeutic targets associated the LP. Hence, we propose a novel computational framework based on new constrained optimization to support vector machines coupled with enrichment analysis. First, we downloaded three gene expression datasets (GSE63741, GSE193351, GSE52130) pertaining to healthy and LP patients from the gene expression omnibus (GEO) database. We then processed each dataset and entered it into our computational framework to select important genes. Finally, we performed enrichment analysis of selected genes, reporting the following results. Our methods outperformed baseline methods in terms of identifying disease and skin tissue. Moreover, we report 5 drugs (including dexamethasone, retinoic acid, and quercetin), 45 unique genes (including PSMB8, KRT31, KRT16, KRT19, KRT17, COL3A1, LCE2D, LCE2A), and 23 unique TFs (including NFKB1, STAT1, STAT3), reportedly related to LP pathogenesis, treatments, and therapeutic targets. Our methods are publicly available in the GENEvaRX web server at https://aibio.shinyapps.io/GENEvaRX/.

# 1. Introduction

Lichen planus (LP) is a non-infectious autoimmune disorder in which the immune system attacks affect different areas, including the skin, mouth, and genitals, among other (Patil et al., 2022; Zare et al., 2021). Skin symptoms include itchy (or irritating), flat bumps, and purplish, characterized by more persistent symptoms depending on the affected area (e.g., genitals or mouth) (Suga, 2022). Normally, a shave biopsy is performed by shaving the skin lesion and sending it to a pathology laboratory (Astudillo et al., 2021; Reimann et al., 2021). Then, a dermatopathologist uses a microscope to inspect the sample skin for disease diagnosis. Examples of microscopic descriptions include skin associated with hypergranulosis, hyperkeratosis, and vacuolar basal change. This also involves specifying whether the skin dermis demonstrates band-like patterns of lymphocytic infiltration, pigment incontinence and other info pertaining to stains (Hassanandani, 2020; Vinay et al., 2020; Zhang et al., 2022a). Such descriptions provide a more accurate diagnosis if the skin lesion is related to LP. Other possible triggers of LP include hepatitis C and allergic reactions

(Budimiri et al., 2019; Pitak-Arnnop et al., 2022). When potential triggers are excluded, doctors prescribe treatments to manage LP and treat the symptoms. As the etiology for LP is unknown and the disease still has no cure (Baek et al., 2020; Zhang et al., 2022b), researchers, mainly in biology, medical, and computational biology domains, have attempted to describe the molecular mechanism of LP and gain biological insights, thereby speeding up the drug discovery process (Xie et al., 2023). Vo et al. (Vo et al., 2021) utilized a bioinformatics approach to gain biological insights into oral lichen planus (OLP). The input datasets were downloaded from the gene expression omnibus (GEO) database according to the accession numbers GSE52130 and GSE38616. Both datasets have 14 uniformly distributed samples consisting of seven healthy controls and seven OLP patients. GSE52130 is related to the epithelium of OLP patients while GSE38616 is related to the mucosa of OLP patients. A t-test was performed for each input dataset to identify differentially expressed genes (DEGs) with p < 0.05 and with a Benjamini–Hochberg FDR correction. A cluster analysis was performed