
where \(p_1 = 0.965\), \(p_2 = 0.95\), \(p_3 = 0.93\) are the poles of the system; and \(c_0 = 0.932\) is a constant.

### 13.4.4 BP control after surgery in a diabetic patient

To control BP is a big challenge after surgery of a diabetic patient since diabetes and hypertension are related with each other, so constant observation and control are required. This problem can be overcome by obtaining automatic drug infusion technique. Generally, BP can be controlled in such cases by using SNP at an advised level, as shown in figure 13.6. The SNP performance for BP control can be represented as [43]:

\(G_{BP}(s) = \frac{\Delta P d(s)}{I_i(s)} = \frac{k e^{-T_i s}(1 + \alpha e^{-T_c s})}{\tau s + 1}\) (13.6)

- where \(\Delta P d(s) =\) pressure difference (mmHg);
- \(I_i (s) =\) rate of infusion of SNP (ml h\(^{-1}\));
- \(k =\) sensitivity of the patient (high value of \(k\) will show sensitive patient);
- \(\alpha =\) Index for recirculation;
- \(\tau =\) time constant;
- \(T_i =\) opening transportation delay;
- \(T_c =\) time for recirculation.

Generally, there are three types of modeling: standard, sensitive, and non-sensitive. Table 13.4 illustrates the different values of model parameter for all three types of modeling, which will vary patient-to-patient.

![](img/75406d5bb714dfd3e68fbbc717bd8f67_316_0.png)

Figure 13.6. BP control strategy after surgery using PID.

Table 13.4. Model parameter.

| Parameter | Non-sensitive | Sensitive | Standard |
|---|---|---|---|
| K | -0.179 | -9 | -0.714 |
| A | 0.4 | 0 | 0.4 |
| \(\tau\) | 60 | 20 | 30 |
| \(T_i\) | 75 | 30 | 45 |
| \(T_c\) | 60 | 30 | 40 |

### 13.4.5 Heart modeling using PM

For heart-rate stabilization, the transfer functions of PM, heart and controller are all required, as shown in figure 13.7. PM is an first-order linear time variant system that may be modeled as [74]:

\(G_p(s) = \frac{k}{1 + s\tau}\)

\(Ms^2 X(s) + Bs X(s) + K X(s) = F(s)\)
\(G_h^c = \frac{X(s)}{F(s)} = \frac{1}{Ms^2 + Bs + K}\)

- where: K = steady state gain;
- M = volume of cardiac muscle;
- B = constants of proportionality for sticky drag of myocardial unit;
- K = constants of proportionality for torsional drag myocardial unit;
- F(s) = force utilized by the cardiac muscle sample then this force is produced through electrical and electrochemical action;
- X(s) = movement of the cardiovascular structure;
- Gc h(s) = heart's closed loop transfer function acknowledging unity feedback.

### 13.4.6 Tumor growth control

In today's life cancer is the most serious disease which increases death rates. Just about 1,373,500 people expired in 2017 due to cancer which is 3% extra compared to 2012 [75]. Due to this large number, cancer patient treatment is heavily dependent on the effectiveness of chemotherapy, as shown in figure 13.8. This problem can be overcome by using PID controller with the 'Hahnfeldt model' [76].

\(\dot{x}_1 = -\lambda x_1 \ln \left( \frac{x_1}{x_2} \right)\)
\(\dot{x}_2 = b x_1 - d x_1^{2/3} x_2 - e x_2 g(t)\)
\(y = x_1\)

![](img/75406d5bb714dfd3e68fbbc717bd8f67_317_0.png)

Figure 13.7. Heart disease control using PID.

![](img/75406d5bb714dfd3e68fbbc717bd8f67_318_0.png)

Figure 13.8. Tumor growth control using PID.

- where x1 = tumor size (mm³);
- x2 = endothelial size (mm³);
- g = intensity of the controlled inhibitor (mg kg⁻¹);
- λ1 = tumor development speed (1/day);
- b = stimulatory volume of tumor for vasculature (1/day);
- d = endogenic inhibition of formerly created vasculature (1/day.mm²);
- e = anti-angiogenic impact of the controlled inhibitor on the tumor vasculature (kg/day.mg).

### 13.5 Conclusion

This work studied the application of a combination of AI and PID techniques in the medical diagnosis field. To get the most excellent and greatest response in the biomedical field, a PID controller is famous due to its simple design and intelligent tuning strategy. Non-noisy input provides more accuracy to the PID. The PID control systems are studied for controlling the different health issues such as, insulin delivery for diabetic patients, drug delivery control for H-BP during and post-surgery conditions, tumor growth monitoring, symptoms identification to control arthritis in preliminary stages etc. This work also studied the integration of AI based PID with different medical technologies to get better accuracy and enhanced diagnosis. The effectiveness of the AI based PID controller, mathematical modeling of various biomedical systems and drug infusion control systems are discussed. In this chapter the biomedical system based on a PID controller helps clinicians and control engineers to execute this progressive and harmless infusion method in actual time to automate the system delivery. The prototype models discussed are very effective in the field of medical health care systems.

## References

- [1] Alley D E 2016 Accountable health communities addressing social needs through Medicare and Medicaid New Engl. J. Med. 374 8–11
- [2] ASTHO (Association of State and Territorial Health Officials). Medicaid and Public Health Partnership Learning Series http://astho.org/Health-Systems-Transformation/Medicaid-and-Public-Health-Partnerships/Learning-Series/Managed-Care
- [3] CMS (Centers for Medicare and Medicaid Services) 2019 Medicare and Medicaid Programs; Patient Protection and Affordable Care Act; Interoperability and Patient Access for Medicare Advantage Organization and Medicaid Managed Care Plans, State Medicaid Agencies, CHIP Agencies and CHIP Managed Care Entities, Issuers of Qualified Health Plans in the Federally Facilitated Exchanges, and Health Care Providers Proposed Rule. Federal Register 84 7610-80
- [4] Kissam S M, Beil H, Cousart C, Greenwald L M and Lloyd J T 2019 States encouraging value-based payment: lessons from CMS’s state innovation models initiative Milbank Quart. 97 506-42
- [5] Mendelson A, Kondo K, Damberg C, Low A, Motuapuaka M, Freeman M, O’Neil M, Relevo R and Kansagara D 2017 The effects of pay-for performance programs on health, healthcare use, and processes of care: a systematic review Ann. Intern. Med. 166 341–55
- [6] Israeli S T and Verghese A 2019 Humanizing artificial intelligence JAMA 321 29–30
- [7] Patel V, Chatterji S, Chisholm D, Ebrahim S, Gopalakrishna G, Mathers C and Reddy K S 2011 Chronic diseases and injuries in India Lancet 377 413–28
- [8] Murray C J L, Inoue M and Lopez A D 1997 Alternative projections of mortality and disability by cause 1990–2020: global burden of disease study Lancet 349 1498–504
- [9] Govind K A and Sekhar R A 2014 Design of a novel PID controller for cardiac pacemaker 2014 Int. Conf. on Advances in Green Energy (ICAGE) (Piscataway, NJ: IEEE) pp 82–7
- [10] Sarangi L, Mohanty M N and Patnaik S 2017 Detection of abnormal cardiac condition using fuzzy inference system Int. J. Autom. Control 11 372–83
- [11] Sarangi L, Mohanty M N and Patnaik S 2016 Critical heart condition analysis through diagnostic agent of E-healthcare system using spectral domain transform Indian J. Sci. Technol. 9 1–7
- [12] Sarangi L, Mohanty M N and Patnaik S 2016 Design of ANFIS based E-health care system for cardio-vascular disease detection Recent Developments in Intelligent Systems and Interactive Applications (Berlin: Springer International Publishing) pp 445–53
- [13] Sarangi L, Mohanty M N and Patnaik S 2015 An intelligent decision support system for cardiac disease detection Int. J. Control. Theory Appl. 8 2137–43
- [14] Mohanty M D, Patnaik D, Parida M, Mohanty S and Mohanty M N 2019 Design of intelligent PID controller for smart toilet of CCU/ICU patients in healthcare systems Int. Conf. on Intelligent Computing and Applications (Singapore: Springer) pp 97–107
- [15] Yen J and Langari R 1999 Fuzzy Logic. Intelligence, Control, and information (Englewood Cliffs, NJ: Prentice-Hall)
- [16] Zhou Y S and Lai L Y 2000 Optimal design for fuzzy controllers by genetic algorithms IEEE Trans. Ind. App. 1 93–7
- [17] Vaishnav S R and Khan Z J 2007 Design and performance of PID and fuzzy logic controller with smaller rule set for higher order system Proc. of the World Congress on Engineering and Computer Science pp 24–6
- [18] Venugopal P, Ganguly A and Singh P 2013 Design of tuning methods of PID controller using fuzzy logic Int. J. Emerg. Trends Eng. Dev. 5 239–48
- [19] Mallesham G and Rajani A 2006 Automatic tuning of PID controller using fuzzy logic 8th Int. Conf. on Development and Application Systems pp 120–7
- [20] Sharma S and Ma K K 2015 Analysis of liquid level control of coupled tank system by PI, PD, PID controller Int. J. Sci. Res. 4 294–6
