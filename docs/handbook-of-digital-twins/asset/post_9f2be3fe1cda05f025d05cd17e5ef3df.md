
indicating that the deviation of the port is caused by the stability of the diagonal tension buckling system, construction load, and temperature during the construction process. So, the deviation of the jointed port can be eliminated by adjusting the stiff skeleton alignment to achieve smooth stiff skeleton jointing.

If the rigid skeleton lifting process ensures that the rigid skeleton alignment meets the stress-free alignment, the final alignment of the bridge will be consistent with the design alignment, according to the stress-free state method. As a result, the buckling cable force can be adjusted prior to the jointing to ensure a smooth installation of the jointed section. Because the actual manufacturing line of the stiff skeleton section meets the requirement of stress-free line, and the entire lifting is controlled according to the stress-free line, the jointing requirement of stress-free length and curvature can be met as long as the horizontal and vertical deviation of the jointed end is zero, and the cable force adjustment model is shown in Figure 40.4a.

The influence matrices C1 and C2 for the upstream and downstream under this merging deviation by adjusting the six cable forces at the cantilever end using the method described in the previous section.

Field adjustments were made based on the deviation results and calculation results of the cable force to obtain the actual deviation value of the adjusted hinge opening, as shown in Figure 40.4a.

Figure 40.4 shows that the deviation of the adjusted joint port has been reduced to within 1–2 mm. This method can predict whether the dimensional deviation of the joint section meets the requirements of the joint in advance. On the one hand, the joint port can be adjusted according to the deviation value to meet the requirements of the joint, while on the other hand, it can improve efficiency and reduce construction difficulty.

The results shown in Figure 40.4b were obtained by comparing the theoretical and actual alignment of the completed bridge by studying the three lower chord rod stiffening skeletons at the bottom of the arches.

According to Figure 40.4c, the deviation of the bare arch alignment in the cross-bridge direction after the bridge is completed is 2.5 mm at most, indicating anti-symmetry; the deviation of the alignment in the elevation direction is 1.4 cm at most, indicating symmetry, and the maximum displacement difference accounts for 7/8,000 of the calculated span, which is within the specification requirement. The deviation of the three main chords is nearly identical, and the overall deviation is small, indicating that the line control effect is effective.

### 40.4.3 Discussion

A DTM detects SSRS section processing accuracy and installation quality using key data from:
- (1) stiff skeleton point cloud collocation station accuracy;
- (2) algorithm extraction accuracy for stiff skeleton features (bolt holes, alignment);
- (3) incomplete flange fit impact on alignment in virtual pre-assembly;

![](img/0dd4397c67b063014553965e4f1cf7e4_721_0.png)

![](img/0dd4397c67b063014553965e4f1cf7e4_721_1.png)

![](img/0dd4397c67b063014553965e4f1cf7e4_721_2.png)

**FIGURE 40.4**
Data results: (a) combined lifting rigging force adjustment model; (b) adjusted deviation of hinge opening; and (c) deviation of main chord elevation line after completion of the bridge.

- and (4) control of the displacement difference between control and theoretical points during cable adjustment.

The spell station algorithm significantly impacts stiff skeleton point cloud accuracy, with millimeter-level deviation in feature points ensuring precise feature extraction. Data collection is challenging due to the site's complexity; obtaining numerous stiff skeleton point cloud feature points is essential for maintaining spell station accuracy. Traditional stiff skeleton alignment inspections use single point measurements like total stations for discrete points. This method, influenced by manual factors, doesn't provide continuous lines. The algorithm discussed here offers automation and robustness, but its stiff skeleton feature extraction depends on both fitting accuracy and point cloud data completeness, warranting further investigation.

During virtual stiff skeleton assembly, imperfect flange and bolt hole fit is considered stress-free linear within a small deviation range. However, forced flange alignment may cause additional structural deformation, leading to deviations between predicted and actual results, requiring future quantification.

Factors like diagrid buckling system stability, construction load, and temperature affect displacement differences between control and theoretical points during cable adjustment. Slight deviations in major chord lines are observed, within millimeters. Comparing post-hoisting alignment to theoretical alignment, maximum deviation is around 2cm, with overall deviation gradually increasing. Cable adjustment reduces overall line deviation, remaining within millimeters, and the effect is positive. Ensuring cable force adjustment occurs at consistent on-site temperatures is crucial.

Alignment monitoring accuracy decreases with increasing distance and angle during stiff skeleton construction, as does point cloud accuracy due to vibration. This unconsidered factor may affect stiff skeleton control, necessitating further research on alignment monitoring accuracy during construction in future studies.

## 40.5 Conclusion

This research created a construction digital twin for a large-span arch bridge to verify machining accuracy and installation quality during construction. A feature extraction algorithm for skeleton collocation stations, based on a fine alignment algorithm, was developed to provide accurate 3D geometry. Noise reduction algorithms for the stiff skeleton point cloud and alignment extraction were also developed to minimize human factors' interference. The virtual pre-assembly technique was used to simulate the assembly of adjacent stiff skeletons, with the developed GDTM accurately predicting installation positions and quality. Post-closure, the arch bridge nears design alignment, with improved alignment control compared to prior methods. Future research will develop construction digital twins with semantic info to simulate operational bridge behavior based on its digital twin.

## References

- Abdel-Qader, I., O. Abudayyeh et al. 2003. “Analysis of Edge-Detection Techniques for Crack Identification in Bridges.” Journal of Computing in Civil Engineering 17 (4): 255–63. https://doi.org/10.1061/(ASCE)0887-3801(2003)17:4(255).
- Andreotti, C., D. Liberatore, and L. Sorrentino. 2015. “Identifying Seismic Local Collapse Mechanisms in Unreinforced Masonry Buildings through 3D Laser Scanning.” Key Engineering Materials, 628: 79–84.
- Bosché, F., and E. Guenett. 2014. “Automating Surface Flatness Control Using Terrestrial Laser Scanning and Building Information Models.” Automation in Construction 44 (aug.): 212–26. https://doi.org/10.1016/j.autcon.2014.03.028.
- Case, F., A. Beinat, F. Crosilla et al. 2014. “Virtual Trial Assembly of a Complex Steel Structure by Generalized Procrustes Analysis Techniques.” Automation in Construction 37 (jan.): 155–65. https://doi.org/10.1016/j.autcon.2013.10.013.
- Chen, L., Xie, X., Lu, Q., Parlikad, A. K., Pitt, M., Yang, J. 2021. “Gemini Principles-Based Digital Twin Maturity Model for Asset Management.” Sustainability 13: 8224. https://doi.org/10.3390/su13158224
- Eastman, C. M. et al. 2011. BIM Handbook: A Guide to Building Information Modeling for Owners, Managers, Designers, Engineers and Contractors. John Wiley & Sons. DOI:10.1002/9781119287568
- Kashani, M. M., A. J. Crewe et al. 2013. “Use of a 3D Optical Measurement Technique for Stochastic Corrosion Pattern Analysis of Reinforcing Bars Subjected to Accelerated Corrosion.” Corrosion Science 73 (aug.): 208–21. https://doi.org/10.1016/j.corsci.2013.03.037.
- Kim, D., Y. Kwak, and H. Sohn. 2020. “Accelerated Cable-Stayed Bridge Construction Using Terrestrial Laser Scanning.” Automation in Construction 117: 103269. https://doi.org/10.1016/j.autcon.2020.103269.
- Kim, S., S. Kim, and D. E. Lee. 2020. “Sustainable Application of Hybrid Point Cloud and BIM Method for Tracking Construction Progress.” Sustainability 12: 4106.
- Lu, R., and I. Brilakis. 2019. “Digital Twinning of Existing Reinforced Concrete Bridges from Labelled Point Clusters.” Automation in Construction 105 (SEP): 102837.1–102837.16.
- Lubowiecka, I., J. Armesto, P. Arias et al. 2009. “Historic Bridge Modelling Using Laser Scanning, Ground Penetrating Radar and Finite Element Methods in the Context of Structural Dynamics.” Engineering Structures 31 (11): 2667–76. https://doi.org/10.1016/j.engstruct.2009.06.018.
