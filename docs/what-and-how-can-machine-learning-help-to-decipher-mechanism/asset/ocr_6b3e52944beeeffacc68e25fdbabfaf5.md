# Review Article

# What and how can machine learning help to decipher mechanisms in molecular electrochemistry?

Jingwen Sun¹ and Chong Liu¹,²

# Abstract

Electrochemists have long been dedicated to heuristically analyzing electrochemical data with meticulous visual inspection and striving to deterministically assign reaction mechanisms. We contend that machine learning (ML) offers a new approach of mechanistic analysis with high data throughput and minimal human intervention. In this perspective, we propose that the deployment of ML in electrochemistry will enable a probability-driven mechanistic analysis amid the inevitable mechanistic ambiguity. We will discuss examples of ML deployment in electroanalysis, enlist current challenges for experimentalists, and discuss ML's prospects in molecular electroanalysis. We hope such a discussion will promote and advance ML-aided mechanistic deciphering for electrochemical systems in the long run.

# Addresses

¹ Department of Chemistry and Biochemistry, University of California Los Angeles, Los Angeles, CA 90095, United States
² California NanoSystems Institute, University of California Los Angeles, Los Angeles, CA 90095, United States

Corresponding author: Liu, Chong (chongliu@chem.ucla.edu)

Current Opinion in Electrochemistry 2023, 39:101306
This review comes from a themed issue on Organic and Molecular Electrochemistry (2023)
Edited by Cyrille Costentin
For complete overview about the section, refer Organic and Molecular Electrochemistry (2023)
Available online 21 April 2023
https://doi.org/10.1016/j.coelec.2023.101306
2451-9103/© 2023 Elsevier B.V. All rights reserved.

# Keywords

Molecular electrochemistry, Mechanistic ambiguity, Machine learning, Information-rich dataset, Probability-driven approach.

# Introduction

The essence of electrochemical mechanistic analysis demands the extraction of plausible reaction mechanisms from a finite set of electrochemical data while if possible minimizing the persistent and inevitable mechanistic ambiguity. As illustrated by Feldberg and coworkers in the 1970s for the case of cyclic voltammetry [1], mechanistic ambiguity denotes to the fact that different reaction mechanisms will frequently

converge to similar voltammograms that are indistinguishable within measurement errors, rendering a deterministic mechanistic designation unfeasible when there are competing reaction pathways and multiple possible explanations. Such a surjective relationship between mechanisms and electrochemical data is not limited to cyclic voltammetry but persists in almost all electrochemical techniques, because every electrochemical characterization is indeed perturbations and detections of electric current and voltage with finite temporal resolutions. For decades, multiple electrochemical techniques [2], including voltammetry [3,4], chronoamperometry [5], and alternating-current methods including electrochemical impedance spectroscopy [6,7], have been deployed for mechanistic analysis. Nonetheless, the intrinsic incompatibility between the deterministic mechanistic designation and the mechanistic ambiguity of electrochemical data remains unresolved. Such an incompatibility risks biased, misassigned, or neglected mechanistic findings.

In such a context, we contend that analysis aided by machine learning (ML) will be beneficial for mechanistic studies for molecular electrochemistry if not for electrochemistry in general [8]. It is reasonable to consider MLs well-known expertise in pattern recognition and feature extraction [9] complementary if not substitutive to the manual inspection of electrochemical data [10,11]. The nature of probability-driven analysis in ML algorithms [9] provides a more satisfying accommodation toward the aforementioned mechanistic ambiguity in electrochemistry, potentially yielding a probability distribution for various reaction pathways based on finite electrochemical data and characterization resolutions. Last but not least, the deployment of ML-based analysis algorithm not only heralds automated electrochemical analysis with high data throughput but also opens the opportunities of simultaneous data analysis for multiple electrochemical techniques, a feast untenable by human owing to the data's nature of high dimensionality.

Encouraged by such a promising perspective, here we attempt to answer one question: what and how can ML help with mechanistic analysis in molecular electrochemistry? In the following three interconnected sections, we will first discuss selected, proof-of-concept applications of ML in mechanistic examination; we will subsequently note a few areas of electrochemical