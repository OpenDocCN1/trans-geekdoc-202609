
small sample size of the subjects, especially for the bilateral cohort, can be considered as a limitation for this study.

Study IV compared the accuracy of differentiating mTLE subjects from the control subjects based on the segmentations obtained by the unified segmentation and the Gram–Schmidt method. The results showed that the texture features of the regions segmented by the unified method were more discriminative than those of the Gram–Schmidt method. They found the three-dimensional texture features successfully in detecting mTLE cases. Moreover, whole-brain texture features outperformed those of the hippocampus.

In the last study discussed in this chapter [61], normalized volumes of three neuroanatomical regions were found to be optimal for mTLE lateralization. The study showed that a combination of the normalized volumetric features of the hippocampus and amygdala resulted in 94.1% accuracy in mTLE lateralization. Without integrating amygdalar volumetric features, hippocampal volumetric features generated 82.4% accuracy. Moreover, integrating thalamic volumetric features increased the accuracy of the mTLE lateralization to 98.5%.

In all of the above studies, the patients used in the training phase were diagnosed to have mTLE. Thus, the proposed machine learning models are applicable to the mTLE patients. They may not be applicable to patients with other types of epilepsy, e.g., extra-temporal epilepsy. Also, the performance of the proposed features and classification models should be studied for patients with lateral, neocortical TLE.

## 6.5 CONCLUSION

The features used in the presented studies can be clustered in four groups: (1) volumetric features including single and multi-structural volumes used in Studies I–V; (2) first- and second-order texture features used in Study IV; (3) DTI features used in Study III; and (4) FLAIR intensity features including single and multi-structural features used in Studies I–III. We described the roles of these features in the lateralization of drug-resistant mTLE patients.

The multi-structural approaches proposed in Ref. [37,61] offered high reliability in the prediction of the side of the epilepsy at a reduced cost and risk to the patients. Based on these results, it can be concluded that an integration of the FLAIR intensity features, like those presented in Ref. [37] and the tri-structural imaging biomarker proposed in Ref. [61], may further improve the lateralization accuracy. However, these methods have not been validated in the case of bilateral epilepsy. To include bilateral cases, future work may extend the methods in an approach similar to that of Ref. [20].

## REFERENCES

- 1. D. Hirtz, D. J. Thurman, K. Gwinn-Hardy, M. Mohamed, A. R. Chaudhuri, and R. Zalutsky, “How common are the ‘common’ neurologic disorders?” *Neurology*, vol. 68, no. 5, pp. 326–337, Jan. 2007.
- 2. G. S. Bell, A. Neligan, and J. W. Sander, “An unknown quantity – The worldwide prevalence of epilepsy,” *Epilepsia*, vol. 55, no. 7, pp. 958–962, 2014.
- 3. A. T. Berg, et al., “Revised terminology and concepts for organization of seizures and epilepsies: Report of the ILAE Commission on Classification and Terminology, 2005–2009,” *Epilepsia*, vol. 51, no. 4, pp. 676–685, 2010.
- 4. A. M. Harriott and W. O. Tatum, *Electroclinical Syndromes: Adolescent Onset*, *Swaiman’s Pediatric Neurology*, 6th ed.: Elsevier Inc., 2017.
- 5. R. D. G. Blalr, “Temporal lobe epilepsy semiology,” *Epilepsy Res. Treat.*, vol. 2012, pp. 1–10, 2012.
- 6. J. A. Hill and N. Venna, *Human Herpesvirus 6 and the Nervous System*, 1st ed., vol. 123: Elsevier B.V., 2014.
- 7. F. J. Rugg-Gunn, et al., “Diffusion tensor imaging in refractory epilepsy,” *Lancet*, vol. 359, no. 9319, pp. 1748–1751, 2002.
- 8. R. P. Carne, et al., “MRI-negative PET-positive temporal lobe epilepsy: A distinct surgically remediable syndrome,” *Brain*, vol. 127, no. 10, pp. 2276–2285, 2004.
- 9. J. C. Bulacio, et al., “Long-term seizure outcome after resective surgery in patients evaluated with intracranial electrodes,” *Epilepsia*, vol. 53, no. 10, pp. 1722–1730, 2012.
- 10. Engel J Jr, Van Ness PC, Rasmussen T, et al. Outcome with respect to epileptic seizures. In: Engel J Jr, editor. *Surgical Treatment of the Epilepsies*. 2nd ed. New York: Raven Press; 1993:609–622.
- 11. E. Achtken, P. Boon, T. Van Der Kerkhof, J. Caemaert, J. De Reuck, and M. Kunnem, “Value of single-voxel proton MR spectroscopy in temporal lobe epilepsy,” *Am. J. Neuroradiol.*, vol. 18, no. 6, pp. 1131–1139, 1997.
- 12. J. De Tisi, et al., “The long-term outcome of adult epilepsy surgery, patterns of seizure remission, and relapse: A cohort study,” *Lancet*, vol. 378, no. 9800, pp. 1388–1395, 2011.
- 13. G. D. Cascino, “Neuroimaging in partial epilepsy: Structural magnetic resonance imaging,” *J. Epilepsa*, vol. 11, no. 3, pp. 121–129, 1998.
- 14. M. Thom, “Review: Hippocampal sclerosis in epilepsy: A neuropathology review,” *Neuropathol. Appl. Neurobiol.*, vol. 40, no. 5, pp. 520–543, 2014.
- 15. M. Thom, “Hippocampal sclerosis: Progress since sommer,” *Brain Pathol.*, vol. 19, no. 4, pp. 565–572, 2009.
- 16. I. Blümcke, et al., “International consensus classification of hippocampal sclerosis in temporal lobe epilepsy: A Task Force report from the ILAE Commission on Diagnostic Methods,” *Epilepsia*, vol. 54, no. 7, pp. 1315–1329, 2013.
- 17. G. D. Jackson, R. I. Kuzniecky, and G. D. Cascino, “Hippocampal sclerosis without detectable hippocampal atrophy,” *Neurology*, vol. 44, no. 1, pp. 42–42, Jan. 1994.
- 18. I. Blümcke, M. T. Mrcpu, and D. Wiestler, “Blümcke, Mrcpu, Wiestler_Amm’s Horn Sclerosis A Maldevelopmental Disorder Associated with Temporal Lobe Epilepsy.pdf,” vol. 1, 2002.
- 19. I. Blümcke, R. Coras, H. Miyata, and C. Özkara, “Defining clinico-neuropathological subtypes of mesial temporal lobe epilepsy with hippocampal sclerosis,” *Brain Pathol.*, vol. 22, no. 3, pp. 402–411, 2012.
- 20. M. R. Nazem-Zadeh, et al., “DTI-based response-driven modeling of mTLE laterality,” *NeuroImage Clin.*, vol. 11, pp. 694–706, 2016.
- 21. P. F. Yang, et al., “Long-term epilepsy surgery outcomes in patients with PET-positive, MRI-negative temporal lobe epilepsy,” *Epilepsy Behav.*, vol. 41, no. 2014, pp. 91–97, 2014.
- 22. S. Treit, et al., “Regional hippocampal diffusion abnormalities associated with subfield-specific pathology in temporal lobe epilepsy,” *Epilepsia Open*, no. August, pp. 544–554, 2019.
- 23. M. Mishito, et al., “Immunoproteasome expression is induced in mesial temporal lobe epilepsy,” *Biochem. Biophys. Res. Commun.*, vol. 408, no. 1, pp. 65–70, 2011.
- 24. R. S. Briellmann, R. M. Kalinis, S. F. Berkovic, and G. D. Jackson, “Hippocampal pathology in refractory temporal lobe epilepsy,” *Neurology*, vol. 58, no. 2, pp. 265–271, Jan. 2002.
- 25. F. Cendes, et al., “MRI of amygdala and hippocampus in temporal lobe epilepsy,” *J. Comput. Assist. Tomogr.*, vol. 17, no. 2, pp. 206–210, 1993.
- 26. C. R. Jack, et al., “Temporal lobe seizures: Lateralization with MR volume measurements of the hippocampal formation,” *Radiology*, vol. 175, no. 2, pp. 423–429, May 1990.
- 27. C. R. Jack, “Hippocampal T2 relaxometry in epilepsy: Past, present, and future,” *AJNR. Am. J. Neuroradiol.*, vol. 17, no. 10, pp. 1811–1814, 1996.
- 28. C. R. Jack, et al., “Mesial temporal sclerosis: Diagnosis with fluid-attenuated inversion-recovery versus spin-echo MR imaging,” *Radiology*, vol. 199, no. 2, pp. 367–373, May 1996.
- 29. J. H. Kim, R. D. Tien, G. J. Felsberg, A. K. Osumi, and N. Lee, “MR measurements of the hippocampus for lateralization of temporal lobe epilepsy: Value of measurements of the body vs the whole structure,” *Am. J. Roentgenol.*, vol. 163, no. 6, pp. 1453–1457, 1994.
- 30. W. Van Paessen, “Quantitative MRI of mesial temporal structures in temporal lobe epilepsy,” *Epilepsia*, vol. 38, no. SUPPL. 10, pp. 3–12, 1997.
- 31. K. Jafari-Khouzanli, K. Elisevich, S. Patel, B. Smith, and H. Soltanian-Zadeh, “FLAIR signal and texture analysis for lateralizing mesial temporal lobe epilepsy,” *NeuroImage*, vol. 49, no. 2, pp. 1559–1571, 2010.
- 32. L. Bonilha, et al., “Texture analysis of hippocampal sclerosis,” *Epilepsia*, vol. 44, no. 12, pp. 1546–1550, Dec. 2003.
- 33. S. B. Antel, et al., “Automated detection of focal cortical dysplasia lesions using computational models of their MRI characteristics and texture analysis,” *NeuroImage*, vol. 19, no. 4, pp. 1748–1759, Aug. 2003.
