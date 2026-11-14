until the forces were less than 0.03 eV/Å. During construction of GoldDAC dataset, the additional calculations were conducted without dispersion correction. In case of labeled as “+D3,” the separate calculations were conducted with dispersion correction using D3 (Becke-Johnson) scheme. Spin-polarization calculations were only considered for frameworks with open-shell metal atoms, and U corrections were applied for d orbitals of Cu, Mn, Ni, Fe, Co, V, Nb, and Ti. Since these DFT settings for fine-tuning database did not fully match those used in the pre-training database for MACE-MP model, this discrepancy may contribute to the initial errors observed in MACE-MP model during evaluation (more details on Note S3). However, as interaction energies are derived from three different systems (MOF + gas, MOF, and gas), they are relatively insensitive to subtle variations in DFT settings.

Q_st and K_H using classical force field were calculated with RASPA2 software.53 Both properties were calculated via Widom insertion MC method that we tried to implement in this work. The cutoff was set as 12.8 Å and the Ewald summation method was adopted to consider the electrostatic potential. The pore blocking algorithm was not considered. The 10,000 MC cycles were iterated for both CO2 and H2O molecules and temperature was set as 300 K to keep consistency with DAC-SIM calculations.

The interaction energies using a classical force field of MOFs in the test set were computed using Large-scale Atomic/Molecular Massively Parallel Simulator software.92 Consistent with the approach taken in adsorption property calculations, a cutoff distance of 12.8 Å was used, and the Ewald summation method was used to account for long-range coulombic interactions with an accuracy threshold of 1 x 10^-5.

For classical force field calculations, framework atoms were modeled using the UFF,18 with point charges assigned based on the DDEC21 scheme. If the .cif file for a structure contained pre-defined charges, these values were retained without further modification. For guest molecules, specifically CO2 and H2O, the TraPPE93 and SPC/E94 force fields were used, respectively.

Geometric properties such as LCD, surface area (SA), and volume fraction (VF) were calculated using Zeo++ software.95 Probe radius for calculation of SA and VF were selected as 1.4 Å, which is the van der Waals radius of Helium. We conducted 2k and 50k MC samplings to calculate the SA and VF, respectively.

# RESOURCE AVAILABILITY

# Lead contact

Further information and requests for resources and materials should be directed to and will be fulfilled by the lead contact, Jihan Kim (jihankim@kaist.ac.kr).

# Materials availability

This study did not generate new, unique reagents.

# Data and code availability

The DAC-sim library is available at https://github.com/hspark1212/DAC-SIM. Documentation for the library is available at https://hspark1212.github.io/DAC-SIM. The implementation of continual learning with MACE is available at https://github.com/hspark1212/mace/tree/develop. Associated files for screening results and the GoldDAC dataset are available via Figshare (https://doi.org/10.6084/m9.figshare.27978474.v3).

# ACKNOWLEDGMENTS

We thank Jisu Jung and Honghui Kim for insightful discussions. Y.L. and J.K. acknowledge funding from the Saudi Aramco-KAIST CO2 Management Center (Projects: G01230260 and N11230051) and the National Research Foundation of Korea under grant No. RS-2025-02218827. H.P. and A.W. acknowledge funding from this work was supported by EPSRC project EP/X037754/1 and are grateful to the UK Materials and Molecular Modelling Hub for computational resources, which is partially funded by EPSRC (EP/T022213/1, EP/W032260/1, and EP/P020194/1).

# AUTHOR CONTRIBUTIONS

Conceptualization, Y.L. and H.P.; methodology, Y.L. and H.P.; investigation, Y. L. and H.P.; writing – original draft, Y.L., H.P., A.W., and J.K.; writing – review and editing, Y.L., H.P., A.W., and J.K.; funding acquisition, A.W. and J.K.; supervision, A.W. and J.K.

# DECLARATION OF INTERESTS

The authors declare no competing interests.

# DECLARATION OF GENERATIVE AI AND AI-ASSISTED TECHNOLOGIES IN THE WRITING PROCESS

During the preparation of this work, the authors used ChatGPT to edit the final draft of the manuscript. After using this tool, the authors reviewed and edited the content as needed and take full responsibility for the content of the publication.

# SUPPLEMENTAL INFORMATION

Supplemental information can be found online at https://doi.org/10.1016/j.matt.2025.102203.

Received: December 11, 2024 Revised: March 19, 2025 Accepted: May 16, 2025 Published: June 12, 2025

# REFERENCES

+   1. NASA's Goddard Institute for Space Studies (GISS). Global Temperature. https://climate.nasa.gov/vital-signs/global-temperature/?intent=121%60.
+   2. Olivier, J.G., Schure, K., and Peters, J. (2017). Trends in global CO2 and total greenhouse gas emissions. PBL Netherlands Environmental Assessment Agency 5, 1–11.
+   3. Lackner, K.S., Brennan, S., Matter, J.M., Park, A.-H.A., Wright, A., and Van Der Zwaan, B. (2012). The urgency of the development of CO2 capture from ambient air. Proc. Natl. Acad. Sci. USA 109, 13156–13162.
+   4. Sabatino, F., Grimm, A., Gallucci, F., van Sint Annaland, M., Kramer, G.J., and Gazzani, M. (2021). A comparative energy and costs assessment and optimization for direct air capture technologies. Joule 5, 2047–2076.
+   5. Didas, S.A., Choi, S., Chakitisilp, W., and Jones, C.W. (2015). Amine–oxide hybrid materials for CO2 capture from ambient air. Acc. Chem. Res. 48, 2680–2687.
+   6. Stolaroff, J.K., Keith, D.W., and Lowry, G.V. (2008). Carbon dioxide capture from atmospheric air using sodium hydroxide spray. Environ. Sci. Technol. 42, 2728–2735.
+   7. Zhang, W., Liu, H., Sun, Y., Cakstins, J., Sun, C., and Snape, C.E. (2016). Parametric study on the regeneration heat requirement of an amine-based solid adsorbent process for post-combustion carbon capture. Applied energy 168, 394–405.
+   8. Keith, D.W., Holmes, G., St Angelo, D., and Heidel, K. (2018). A process for capturing CO2 from the atmosphere. Joule 2, 1573–1594.