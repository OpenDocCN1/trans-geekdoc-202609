
3. 文献中报告的各种评估方法是另一需要解决的问题。在机器学习社区中，众所周知，使用不同的评估方法时，同一系统流水线在分类性能上可能表现出巨大差异。例如，文献中 Ref. \[[14](#C15_chapter8.xhtml#ref8_14)\] 所述工作提供了两个截然不同的准确率：使用五折交叉验证，系统能够实现对 MCI 检测的 98% 准确率；而使用留一出交叉验证，同一系统的准确率仅约为 70%。建议研究者在设计实验时尽量模拟真实场景，特别是避免使用同一主体同一会话的数据作为训练和测试数据。

4. 虽然临床脑电数据（尤其是 EEG）相当丰富，但根据文献，几分钟的记录即可提供合理的准确率。单会话的额外记录似乎无法进一步提升性能，并且可能引入冗余数据。

5. 当前大多数研究均基于休息状态数据。作为早期基线研究，这非常推荐。为了进一步探索，尤其是感兴趣区域（ROIs）及其功能响应，应开发不同的实验范式。例如，阿尔茨海默病（AD）影响大脑的多个认知区域，结合多种认知刺激范式可以更好地探讨认知变化及其关系。

鉴于其部署规模有限且整体处于早期发展阶段，机器学习辅助轻度认知障碍（MCI）/阿尔茨海默病（AD）诊断的潜力还有很大空间可开发。从信息收益的角度来看，MEG 模态直观上比 EEG 信号更具信息性，因为其传感器密度更高，且每个通道的信息量更大。然而，MEG 基于自动诊断的方法也需要精心设计以去除冗余信息。相反，EEG 因其安装成本低、已广泛部署，在大多数主流临床实践中仍发挥辅助作用。

提升预测性能的一个可能途径是结合 EEG 和 MEG：装备良好融合算法的多模态识别系统可以协同利用两种模态的互补信息。从广阔视角来看，使用 E/MEG 基于机器学习的算法对阿尔茨海默病患者及其他神经退行性疾病（如帕金森病和莱伊体痴呆）进行分类，在未来的研究中也值得关注。

## [References](#C15_chapter8.xhtml#rreferences-6)

1. [1.](#C15_chapter8.xhtml#rref8_1) S. Yang, J. Miguel, S. Bornot, K. Wong-lin, G. Prasad, and S. Member, “M/EEG-based bio-markers to predict the mild cognitive impairment and Alzheimer’s disease : A review from the machine learning perspective,” *IEEE Trans. Biomed. Eng.*, pp. 1–12.

2. [2.](#C15_chapter8.xhtml#rref8_2) H. Azami, M. Rostaghi, A. Fernandez, and J. Escudero, “Dispersion entropy for the analysis of resting-state MEG regularity in Alzheimer’s disease,” in *Proceedings of the Annual International Conference of the IEEE Engineering in Medicine and Biology Society, EMBS*, 2016, vol. 2016-Oct, pp. 6417–6420.

3. [3.](#C15_chapter8.xhtml#rref8_3) G. Q. Mamani, F. J. Fraga, G. Tavares, E. Johns, and N. D. Phillips, “EEG-based biomarkers on working memory tasks for early diagnosis of Alzheimer’s disease and mild cognitive impairment,” *2017 IEEE Healthc. Innov. Point Care Technol.*, pp. 237–240, 2017.

4. [4.](#C15_chapter8.xhtml#rref8_4) J. Ye, Y. Lan, R. Wang, and Y. Yang, “Relative power analysis of electroencephalograph rhythms in elderly with mild cognitive impairment,” in *2017 10th International Congress on Image and Signal Processing, BioMedical Engineering and Informatics (CISP-BMEI)*, 2017, no. 91420302, pp. 1–6.

5. [5.](#C15_chapter8.xhtml#rref8_5) S. Ruiz-Gómez et al., “Automated multiclass classification of spontaneous EEG activity in Alzheimer’s disease and mild cognitive impairment,” *Entropy*, vol. 20, no. 1, p. 35, 2018.

6. [6.](#C15_chapter8.xhtml#rref8_6) A. H. H. Al-Nuaimi, E. Jammeh, L. Sun, and E. Ifeachor, “Complexity measures for quantifying changes in electroencephalogram in Alzheimer’s disease,” *Complexity*, vol. 2018, pp. 22–24, 2018.

7. [7.](#C15_chapter8.xhtml#rref8_7) H. Yu, X. Lei, Z. Song, J. Wang, X. Wei, and B. Yu, “Functional brain connectivity in Alzheimer’s disease: An EEG study based on permutation disalignment index,” *Phys. A Stat. Mech. Appl.*, vol. 506, pp. 1093–1103, 2018.

8. [8.](#C15_chapter8.xhtml#rref8_8) A. Mazaheri et al., “EEG oscillations during word processing predict MCI conversion to Alzheimer’s disease,” *NeuroImage Clin.*, vol. 17, no. October 2017, pp. 188–197, 2018.

9. [9.](#C15_chapter8.xhtml#rref8_9) F. Maestú et al., “A multicenter study of the early detection of synaptic dysfunction in mild cognitive impairment using magnetoencephalography-derived functional connectivity,” *NeuroImage Clin.*, vol. 9, pp. 103–109, 2015.

10. [10.](#C15_chapter8.xhtml#rref8_10) J. P. Amezquita-Sanchez, A. Adeli, and H. Adeli, “A new methodology for automated diagnosis of mild cognitive impairment (MCI) using magnetoencephalography (MEG),” *Behav. Brain Res.*, vol. 305, pp. 174–180, 2016.

11. [11.](#C15_chapter8.xhtml#rref8_11) S. Yang and F. Deravi, “Novel HHT-based features for biometric identification using EEG signals,” *2014 22nd Int. Conf. Pattern Recognit.*, pp. 1922–1927, Aug. 2014.

12. [12.](#C15_chapter8.xhtml#rref8_12) H. Aghajani, E. Zahedi, M. Jalili, A. Keikhosravi, and B. V. Vahdat, “Diagnosis of early Alzheimer’s disease based on EEG source localization and a standardized realistic head model,” *IEEE J. Biomed. Heal. Informat.*, vol. 17, no. 6, pp. 1039–1045, 2013.

13. [13.](#C15_chapter8.xhtml#rref8_13) J. A. Pineda-Pardo et al., “Guiding functional connectivity estimation by structural connectivity in MEG: An application to discrimination of conditions of mild cognitive impairment,” *Neuroimage*, vol. 101, pp. 765–777, 2014.

14. [14.](#C15_chapter8.xhtml#rref8_14) J. Guillon et al., “Loss of brain inter-frequency hubs in Alzheimer’s disease,” *Sci. Rep.*, vol. 7, no. 1, pp. 1–14, 2017.

15. [15.](#C15_chapter8.xhtml#rref8_15) S. I. Dimitriadis et al., “How to build a functional connectomic biomarker for mild cognitive impairment from source reconstructed MEG resting-state activity: The combination of ROI representation and connectivity estimator matters,” *Front. Neurosci.*, vol. 12, no. JUN, pp. 1–21, 2018.

16. [16.](#C15_chapter8.xhtml#rref8_16) C. Babiloni et al., “Functional cortical source connectivity of resting state electroencephalographic alpha rhythms shows similar abnormalities in patients with mild cognitive impairment due to Alzheimer’s and Parkinson’s diseases,” *Clin. Neurophysiol.*, vol. 129, no. 4, pp. 766–782, 2018.

17. [17.](#C15_chapter8.xhtml#rref8_17) S. Yang and F. Deravi, “On the usability of electroencephalographic signals for biometric recognition: A survey,” *IEEE Trans. Human-Machine Syst.*, vol. 47, no. 6, pp. 958–969, 2017.
