Recovery factor prediction can be a function of multiple variables of the reservoir characteristics to be determined. The operational controllable input parameters for the MARS and GMDH models are average reservoir pressure (ARP), cumulative gas injection (CGI), cumulative low salinity water injection (CLSWI), gas cumulative production (GCP), oil cumulative production (OCP), gas injection rate (GIR), low salinity water injection rate (LSWIR), and the target is the ORF for CO₂-LSWAG as shown in Table 7.4. The LSW and CO₂ injection rate employed in the carbonate model for the simulation period is shown in Fig. 7.4b.

For constructing the proxy machine learning models, the oil saturation maps obtained for the 15 years of CO₂-LSWAG injection oil recovery are shown in Figs. 7.5a, 7.5b, and 7.5c for 5, 10, and 15 years, respectively. It was observed that CO₂ injection lowers the viscosity of the crude oil after it becomes miscible with it. Figure 7.5 shows the initial and final oil saturation of the reservoir, depicting how the CO₂-LSWAG injection lowered the viscosity to recover more oil. It can be seen from the final oil saturation plot in Fig. 7.5c of the CO₂-LSWAG that the injection scheme lowered the viscosity of the reservoir oil, enabling more oil to be recovered.

# Table 7.4. Dataset ranges for CO₂-LSWAG oil recovery factor prediction.

| Variable/Unit | Minimum | Average | Maximum | Standard Deviation | Data Type |
|---|---|---|---|---|---|
| Average reservoir pressure (psi) | 3349.11 | 5187.38 | 6679.61 | 1298.05 | Input |
| Cumulative gas injection (MMMSCF) | 0.00 | 12.12 | 25.64 | 5.28 | Input |
| Cumulative low salinity water injection (MMbbl) | 0.00 | 6.83 | 18.48 | 4.24 | Input |
| Gas cumulative production (MMMSCF) | 0.00 | 7.61 | 17.02 | 3.16 | Input |
| Oil cumulative production (MMbbl) | 0.00 | 13.73 | 15.96 | 3.17 | Input |
| Gas injection rate (MMSCFD) | 0.00 | 13.81 | 30.00 | 4.77 | Input |
| Low salinity water injection rate (Mbbl/day) | 0.00 | 5.09 | 7.17 | 1.58 | Input |
| Oil recovery factor (%) | 0.00 | 72.38 | 84.07 | 16.68 | Output |