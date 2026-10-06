
# Chem
# CellPress

Article

# Selective functionalization of hindered meta-C–H bond of o-alkylaryl ketones promoted by automation and deep learning

![](img/a18ddd6f6f5650b41b9ff9e80884cecf_0_0.png)

Jia Qiu, Jiancong Xie, Shimin Su, Yadong Gao, Han Meng, Yuedang Yang, Kuangiao Liao

yangd25@mail.sys.edu.cn (Y.Y).
liao_kuangiao@gzlab.ac.cn (K.L.)

## Highlights
- Hindered meta-C–H functionalization
- Three steps in one pot (yield up to 76%)
- Graph-based prediction model (CMPRY)
- Two-step reaction prediction (MAE = 6.6%)
- Hindered meta-C–H functionalization
- CO2 steps as traceless director
- Three steps in one-pot
- Graph-based deep learning model
- Two-step reaction prediction

Modification of C-H bonds is of great interest for chemists, but selectivity is challenging. Differentiating sterially hindered C-H bond over sterically favorable C-H bond is difficult. To develop a reaction for the modification of the hindered aromatic meta–C–H bond, automation was used to explore reaction space and artificial intelligence was used to predict reaction outcome. The integration of automation and artificial intelligence will aid the development and application of new synthetic methods.

![](img/a18ddd6f6f5650b41b9ff9e80884cecf_0_1.png)

Qiu et al., Chem 8, 3275–3287
December 8, 2022 Elsevier Inc.
https://doi.org/10.1016/jchempr.2022.08.015

![](img/a18ddd6f6f5650b41b9ff9e80884cecf_0_2.png)

# Chem
# CellPress

Article

# Selective functionalization of hindered meta-C-H bond of o-alkylaryl ketones promoted by deep learning

Jia Qiu,$1,2,5$ Jiancong Xie,$4,5$ Shimin Shu,$1$ Yadong Gao,$2$ Hen Meng,$4$ Yuedong Yang,$3,* and Kuangiao Liao,$1,2,6*$

## SUMMARY

**Selective functionalization of the sterically hindered aromatic meta-C-H bond is unprecedented and remains to be a major challenge.** By automation-based high-throughput experimentation (HTE) and deep learning (DL), a novel strategy to functionalize the hindered meta-C-H bond is demonstrated. With carbon dioxide as a traceless director, a one-pot free-step protocol achieved highly selective arylation of o-alkylaryl ketones at the hindered meta position. This novel strategy involved photo-induced-C-H carboxylation, microwave-assisted decarboxylation. With HTE and DL, a broad scale of substrates was explored (1,032 reactions) and a DL-model (CMPRY) for reaction yield prediction was established. Two independent tests with o-alkylaryl ketones and potassium trifluorobates were used to evaluate the method. The model gave excellent predictions in predicting reactions; mean absolute errors were only 6.6% and 8.4%, showing its potential in synthetic application.

## THE BIGGER PICTURE

Selective C-H functionalization is a key goal in organic chemistry. Although various protocols were reported, distinct electronic and steric properties are generally required for the successful differentiation of C-H bond from others. For C-H bonds with sterically hindered C-H bonds are strongly preferred over established protocols; therefore, selective functionalization of hindered C-H bond remains a major challenge addressed by automation and intelligence, a different strategy to functionalize the aromatic meta-C-H bond developed. Automation-based high-throughput experimentation was used to explore space and reaction data. Artificial intelligence-based models were used to predict reaction yield of substrates. The integration of automation and intelligence in organic synthesis is an emerging field in chemical research, which can expedite reaction discovery and application.

## INTRODUCTION

In natural products, pharmaceuticals, and functional materials, substituted arenes are ubiquitous and important structural motifs.$^{1-5}$ Selective C-H functionalization has been reported. Despite the extra steps to install and remove directing groups (DGs), C-H functionalization has demonstrated achieved excellent selective strategies, particularly at ortho and hindered meta position (Figure 1A).$^{17-20}$ Yu and co-functionalization template strategies enable meta-C-H functionalization, but achieved at hindered meta position due to the steric preference (Figure 1B).$^{16-18}$ Using carbon dioxide ($CO_2$) as a traceless relay for the hindered meta-C-H arylation of phenols was reported by Larrosa and coworkers in 2014, which employs Kolbes-Schmitt reaction, group-directed Pd-catalyzed C-H arylation, and tandem decarboxylation procedure$^{19-21}$ A similar approach, with norbornene (Nb) as a transient mediator, was introduced by Yu to achieve aromatic meta-C-H arylation of methyl phenyl ether in 2015. The Pd/NRE-relay cycle (Cation process)$^{22}$ was further explored for other kinds of hindered meta-C-H functionalization.$^{23-25}$

Reported progresses focused on hindered meta-C-H bond; however, selective functionalization of the hindered meta-C bond bond was rarely reported. To circumvent this challenge, we developed a one-pot three-step reaction using $CO_2$ as a traceless director (Figure 1C). A photo-induced-C-H carboxylation, microwave-assisted decarboxylation, and group-directed Pd-catalyzed C-H arylation were used to achieve selective arylation at the hindered meta position. Automation-based high-throughput experimentation (HTE) was used to explore reaction space and reaction data. Artificial intelligence-based models were used to predict reaction yield of substrates. The integration of automation and intelligence in organic synthesis is an emerging field in chemical research, which can expedite reaction discovery and application.

# Chem
# CellPress

Article

## A directed(sp³)-H functionalization

![](img/a18ddd6f6f5650b41b9ff9e80884cecf_1.png)

## B Approaches toward hindered meta-C-H bond

![](img/a18ddd6f6f5650b41b9ff9e80884cecf_2.png)

## C This work

![](img/a18ddd6f6f5650b41b9ff9e80884cecf_3.png)

Figure 1. Strategies for regioselective C-H functionalization
[A] Directed C(sp³)-H functionalization
[B] Approaches toward hindered meta-C-H bond.
[C] This work, a one-pot protocol for selective arylation at the hindered meta position. Photo-induced-C-H carboxylation was used to install a carboxyl group at the hindered meta position, then microwave-assisted decarboxylation was employed to release CO. HTE was the key to obtain optimal condition, substrate scopes, and standardized experimental data for broadening the application of this methodology, deep learning.

Modification of hindered meta-C-H functionalization
Chem 8, 3275–3287
December 8, 2022 Elsevier Inc.

*These authors contributed equally.
*Correspondence:
*Guangzhou Laboratory, Guangzhou 510320, P. China
*Boland Laboratory, Guangzhou, 51005, P. China
*School of Computer Science and Engineering, Sun-yat University, 51006, P. China
*Department of Chemistry, Southern University of Science and Technology, Shenzhen 51805, P. China
*Southern University of Science and Technology, Shenzhen 51805, P. China
*yangd25@mail.sys.edu.cn (Y.Y).
liao_kuangiao@gzlab.ac.cn (K.L.)

# RESULTS AND DISCUSSION

## Reaction development

Figure 2

![](img/a18ddd6f6f5650b41b9ff9e80884cecf_4.png)

## A Optimization of carbonylation process

B Optimization of tandem C-H arylation/decarbonylation

![](img/a18ddd6f6f5650b41b9ff9e80884cecf_5.png)

i. Selected examples of screened ligands, bases and BQs:

ii. yields of 4a and 5a

![](img/a18ddd6f6f5650b41b9ff9e80884cecf_6.png)

Figure 2. Optimization of C-H carbonylation/C-H arylation/decarbonylation
(A) Optimization of C-H carbonylation process.
(B) Optimization of tandem C-H arylation/decarbonylation. (i) Selected examples of MPAA ligands, bases, and BQs; (ii) yields of 4a (darkgreen) and 5a (chocolate).

yield prediction that relies on graph-based methods were developed, and the interpretation of the model was also improved 32–39.

Our studies began at the optimization of the photo-induced C(sp³)–H carbonylation (Figure 2A)²²⁴. Considering the solubility of CO2 and relatively low boiling,point dimethylformamide (DMF) was selected as solvent instead of dimethyl sulfoxide (DMSO). Then, bases were evaluated to improve the carbonylation yield. Addition of KHCO3, base compound (2) was favored in excellent yield. With KHPO4 and DMF saturated by CO2 in advance, C(sp³)–H carbonylation also proceeded successfully (90% yield in 40 min).
