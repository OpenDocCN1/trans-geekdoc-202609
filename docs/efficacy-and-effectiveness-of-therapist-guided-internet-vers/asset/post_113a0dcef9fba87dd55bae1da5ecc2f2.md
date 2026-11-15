
## Efficacy and effectiveness of therapist-guided internet versus face-to-face cognitive behavioural therapy for depression via counterfactual inference using naturalistic registers and machine learning in Finland: a retrospective cohort study

Tom H Rosenström, Suoma E Saarni, Samuli I Saari, Jaakko Tammilehto, Jan-Henry Stenberg

## Summary

### Background

According to meta-analyses of randomised controlled trials (RCTs), therapist-guided internet-delivered cognitive behavioural therapy (iCBT) is as effective a treatment for depression as traditional face-to-face CBT (fCBT), despite its substantially lower costs. However, RCTs are not always representative of routine practice, which could inflate effectiveness estimates. We combined rich data with counterfactual causal statistical reasoning to provide an fCBT–iCBT comparison complementary to RCTs.

### Methods

In this retrospective cohort study, we linked full archived therapist-guided iCBT and fCBT cohort registries with multiple Finnish social and health care registries. The therapist-guided iCBT programme with third-wave principles and the fCBTs were provided by HUS Helsinki University Hospital to people with depression without acute suicide or substance-misuse risk; fCBT was delivered in the Uusimaa region, whereas therapist-guided iCBT was nationwide and excluded people with treatment-interfering psychotic, neurological, or personality disorders, chronic or bipolar depression, or aged under 16 years. The primary outcome was the causal average treatment effect (ATE) for the difference in during-treatment symptom reductions between fCBT and therapist-guided iCBT, with symptoms measured by the Patient Health Questionnaire-9 (PHQ-9). If only one PHQ-9 report was recorded, no change was recorded, thereby penalising dropout. For an optimal and robust (a posteriori-balanced) ATE estimate, we applied targeted maximum likelihood machine learning. There was no involvement of individuals with lived experience in the research and writing process.

### Findings

The guided iCBT registry recorded patients from Dec 12, 2018, to Dec 22, 2022, and the fCBT registry spanned Aug 28, 2018, to Sept 28, 2022. From the total of 32 343 registered therapies, 392 people were included from the fCBT registry and 5467 people from the iCBT registry. Four people in the fCBT group and 21 in the guided iCBT group had missing baseline data, therefore the main sample for analysis contained 5834 patients (4101 [70%] were female and 1733 [30%] were male) with a mean age of 35 years (SD 12). Altogether, 5455 (94%) patients were registered with Finnish as their native language. The ATE estimate indicated that the PHQ-9 score declined 0.745 points (95% CI 0.156–1.334) more in the iCBT group than the fCBT group. Sensitivity analyses concurred.

### Interpretation

Considered alongside previous RCTs, our findings suggest that short first-line treatments with therapist-guided iCBT are at least as effective and efficacious as fCBT. Our findings eliminate error sources and extend the representativeness of the population for this cost-effective treatment.

### Funding

The Research Council of Finland (Academy of Finland).

### Copyright

© 2025 Elsevier Ltd. All rights reserved, including those for text and data mining, AI training, and similar technologies.

Lancet Psychiatry 2025; 12: 189–97 Published Online February 12, 2025 https://doi.org/10.1016/S2215-0366(24)00404-8 See Comment page 163 For the Finnish language of the abstract see Online for appendix 1

Department of Psychology, Faculty of Medicine, University of Helsinki, Helsinki, Finland (T H Rosenström, PhD, J Tammilehto, PhD); Department of Psychiatry, Helsinki University Central Hospital, Helsinki, Finland (Prof S E Saarni PhD MD, J-H Stenberg PhD); Faculty of Medicine and Health Technology, Tampere University, Tampere, Finland (Prof S E Saarni, Prof S I Saari PhD MD); Family and Social Services, Psychiatry, Wellbeing Services County of Päijät-Häme, Lahti, Finland (Prof S E Saarni); Department of Psychiatry, The Wellbeing Services County of Pirkanmaa, Tampere, Finland (Prof S I Saarni) Correspondence to: Dr Tom H Rosenström, Department of Psychology, Faculty of Medicine, University of Helsinki, University of Helsinki, University of Helsinki, 00014, Finland, tom.rosenstrom@helsinki.fi

## Introduction

Meta-analyses of available randomised controlled trials (RCTs) indicate that therapist-guided, internet-delivered cognitive behavioural therapy (iCBT) is a similarly effective treatment compared with the more costly and traditional face-to-face CBT (fCBT) for psychiatric disorders.1,2 Much of the cost differential between therapist-guided iCBT and fCBT derives from therapists' differential time investment per patient.

However, a meta-analysis3 found no association between contact time and treatment effect in psychotherapy for depression. When people are directed to digital therapy supported by a therapist, their expectations of benefit are comparable to face-to-face therapy.4 People with depression might benefit from therapist-guided iCBT and fCBT regardless of their symptom severity at intake.5,6 However, some clinicians might find it difficult to accept the idea that

## Research in context

### Evidence before this study

Multiple meta-analyses indicate that cognitive behavioural therapy (CBT) is equally efficacious in treating depressive disorders when implemented as guided internet-delivered CBT (iCBT) compared with when delivered as the usual face-to-face CBT (fCBT). Because guided iCBT programmes use automated videos and exercises, online therapists can spend much less time per patient compared with face-to-face therapists, which can lead to significant costs savings. However, the meta-analyses rely on randomised controlled trials (RCTs), and the possibility remains that the trials do not represent the full routine-treatment population, or adequately account for the large differences in treatment adherence or other differences between fCBT and guided iCBT. Over the past few decades, the use of complementary sources of causal information has been increasingly recommended for all of medicine. One of the state-of-the-art methods for such causal triangulation is the targeted maximum likelihood estimation with machine learning. We searched PubMed (MEDLINE), with no language restrictions, for papers published from database inception to Sept 16, 2024, using the search terms: “targeted maximum likelihood” AND depression AND (“internet” OR “digital”) AND (“cognitive behavioural therapy” OR “cognitive behavioural therapy”), yielding no results. A second search, replacing terms “targeted maximum likelihood” with “causal triangulation” or with “causality”, or with “quasi-experiment”, also gave no results. Overall, causal triangulation of the fCBT-iCBT efficacy differential in depression treatment is important given the substantial societal and monetary costs associated with depressive disorders and their treatment, which jointly imply a need to comprehensively understand the health effects of seemingly low-cost treatment policies.

### Added value of this study

To our knowledge, this study is the first to evaluate quantitatively the efficacy differential between fCBT and guided iCBT in a format that is not an RCT or a meta-analysis of RCTs. We used counterfactual causal inference using targeted maximum likelihood machine learning and a unique linked registry from five distinct registry owners, combined using Finnish laws and regulations on secondary use of health and social registries. This targeting method can integrate features from both parametric and non-parametric methods to provide precise and reliable estimates of causal effects in situations in which the data are complex and could contain multiple confounding factors. We observed that the results from RCTs held true both in routinely collected data and in a posteriori-balanced (ie, causally informative) data: the guided iCBT programme was as effective and efficacious as fCBT in terms of depression symptom decline from before to after treatment (or to the last available measurement).

### Implications of all the available evidence

Therapist-guided iCBT is equally effective and more cost-effective in treating depression than face-to-face delivery. Internet-delivery of short first-line treatments is a sensible default-treatment option and an apt response to the high demand for services.

partly automated treatments could yield treatment outcomes that are as effective as face-to-face therapies. The risk is that clinicians might inadvertently impart their attitudes to patients, potentially leading to diminished treatment efficacy.4 RCTs are not always representative of routine practice, which might inflate effectiveness estimates.7,8 For example, people who object to digital treatments might not enrol in an RCT offering iCBT. Furthermore, samples in RCTs tend to be small relative to registries. Although meta-analyses combine RCTs to achieve larger samples, they often lack commensurate and comprehensive data on the complexity of people’s conditions and other background factors that could affect representativeness. Thus, whether therapist-guided iCBT truly is as effective as fCBT in real-world settings remains unclear. The central counterfactual question is: would the average treatment effect (ATE) still be similar if we could allocate exact replicas of the same patients simultaneously to both guided iCBT and fCBT and compare their efficacies? Although considered a gold standard, RCTs are neither the only nor a perfect method for balancing intervention group composition to avoid confounding. Researchers in medicine, psychology, and statistics argue that reliable causal inference often requires multiple sources of evidence rather than RCTs exclusively.9–11 Many methods make assumptions that reduce bias from confounding (Figure 1). For example, estimates weighted by known inverse probabilities of treatment are free from confounding.12,13 Alternatively, if the outcome can be accurately modelled as a function of confounders and treatment allocation, an unbiased estimate of treatment effect is achievable via G-computation.14 If models for both outcome and treatment-assignment probability exist, models can be combined to achieve an augmented inverse-probability-of-treatment weighted (AIPTW) estimate that is doubly robust. This method ensures that a consistent estimate of the ATE is obtained if at least one of the models is correctly specified.14 Finally, an ensemble of machine learners (ie, super learners) maximise the probability of at least one model being correct.13,14 In our case, the aforementioned methods make the working assumption that treatment outcome depends on the treatment (ie, delivery method). Outcome and treatment might depend on covariates, but all such confounding covariates are assumed to be fully observed. Other key assumptions are consistency
