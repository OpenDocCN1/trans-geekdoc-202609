
different subgroups, suggesting that the ML model's predictive ability may primarily derive from the atherosclerotic burden and plaque phenotype itself. However, due to the limited events, further validation in larger studies is needed.

Our study also demonstrated the practical application of the integrated ML model in clinical practice, emphasizing each feature's contribution to the final prediction score, thereby providing clear interpretability of the predicted outcomes. It enables direct visualization of coronary atherosclerosis and luminal stenosis, facilitating a deeper understanding of the pathophysiological mechanisms underlying coronary atherosclerosis. Moreover, the model can be incorporated into PACS systems to automatically generate individualized risk scores based on structured imaging parameters. When the predicted risk exceeds a predefined threshold, automated alerts can be triggered to assist clinicians in early intervention and treatment decision-making. Its application will transform the cardiovascular disease prevention strategies, shifting from population-level risk assessments to individual-level evaluation and intervention, aiding in identifying high-risk individuals for future cardiovascular events. Despite its strong prognostic value, CCTA has several limitations, including the need for iodinated contrast agents, exposure to ionizing radiation, reduced diagnostic accuracy in the presence of heavy coronary calcification, heart rate dependence, and limited availability in some settings.

## Strengths and Limitations

Our study has several notable strengths. It is a nationally representative, prospective registry cohort study with a large sample size and medium to long-term follow-up. Various advanced ML survival techniques were applied to establish a new multidimensional CCTA imaging prediction model. However, our study has several limitations: First, all data were derived from a single specialized tertiary medical center, which may result in selection bias. Although the model performed well in internal validation, its applicability needs to be confirmed through external validation, considering variations across regions, countries, and racial/ethnic. Second, this study did not capture detailed information on atypical ischemic symptoms or specific indications for CCTA, which may have introduced a degree of referral bias. Further validation in a clearly symptomatic population is warranted. Third, the types and dosages of lipid-lowering medications were not recorded during the follow-up period, which may affect the progression of adverse patient outcomes. Fourth, future studies could consider incorporating new CCTA parameters, such as coronary functional flow assessment and perivascular fat attenuation index, to provide additional information about cardiovascular risk and further improve modeling accuracy.

## Conclusions

This study combines CCTA with ML to develop and validate a more interpretable, accurate, individualized, and dynamic model for cardiovascular risk prediction. This model enhances risk stratification, thereby potentially advancing the clinical application and translation of CCTA imaging.

## ARTICLE INFORMATION

Received April 18, 2025; accepted October 29, 2025.

## Affiliations

Department of Cardiology (Y.S., N.X., C.C., Y.Z., L.G., Z.G., J.C., L.S., J.Y.) and Department of Radiology (J.Z., S.J., B.L., H.Z.-H.), Fuwai Hospital, National Clinical Research Center for Cardiovascular Diseases, National Center for Cardiovascular Diseases, Chinese Academy of Medical Sciences and Peking Union Medical College, Beijing, China.

## Acknowledgments

Ethics approval and consent to participate. The Ethical Review Board of Fuwai Hospital approved the study protocol in accordance with the Declaration of Helsinki, and written informed consent was obtained from all participants.

## Author Contributions

All authors contributed to the study conception and design. Drs Xu, Song, Zheng, Jia, Cui, Zhang, L. Gao, Z. Gao, and Chen contributed to data collection and analysis. Drs. Zhi-hui, Lu, Yuan, and L. Song critically revised the article. All authors read and approved the final article. The first 2 authors contributed equally: Dr Xu oversaw the algorithm development part of this work, while Dr Song was in charge of the medical part of this work, and both of the first authors equally contributed to the writing of the article.

## Sources of Funding

This work was supported by the CAMS Innovation Fund for Medical Sciences (2023-I2M-C&T-B-061); CAMS Innovation Fund for Medical Sciences (2021-I2M-1-008); the National High-Level Hospital Clinical Research Funding (2024-GSP-TJ-8); CAMS Innovation Fund for Medical Sciences (2023-I2M-1-002).

## Disclosures

None.

## Supplemental Material

- Supplemental Methods
- Tables S1–S13
- Figures S1–S11

## REFERENCES

- 1. O'Donoghue ML, Giugliano RP, Wiviott SD, Atar D, Keech A, Kuder JF, Im K, Murphy SA, Flores-Arredondo JH, López-JAG, et al. Long-term evolocumab in patients with established atherosclerotic cardiovascular disease. *Circulation*. 2022;146:1109–1119. doi: 10.1161/CIRCULATIONAHA.122.061620.
- 2. Nicholls SJ, Katoka Y, Nissen SE, Prati F, Windecker S, Puri R, Hucko T, Aradi D, Hermen JPR, Hernandes RS, et al. Effect of evolocumab on coronary plaque phenotype and burden in statin-treated patients following myocardial infarction. *JACC Cardiovasc Imaging*. 2022;15:1308–1321. doi: 10.1016/j.jcmg.2022.03.002.
- 3. Ray KK, Troquay RPT, Visseren FLJ, Leiter LA, Scott Wright R, Vikarunnessa S, Tallozy Z, Zang X, Maheux P, Lesogor A, et al. Long-term efficacy and safety of inclisiran in patients with high cardiovascular risk and elevated LDL cholesterol (ORION-3): results from the 4-year open-label extension of the ORION-1 trial. *Lancet Diabetes Endocrinol*. 2023;11:109–119. doi: 10.1016/S2213-8587(22)00353-9.
- 4. Budoff MJ, Bhatt DL, Kinnerger A, Lakshmanan S, Muhlestein JB, Le VT, May HT, Shaliik K, Shekar C, Roy SK, et al. Effect of icosapent ethyl on progression of coronary atherosclerosis in patients with elevated triglycerides on statin therapy: final results of the EVAPORATE trial. *Eur Heart J*. 2020;41:3925–3932. doi: 10.1093/eurheartj/ehaa652.
- 5. Bhatt DL, Steg PG, Miller M, Brinton EA, Jacobson TA, Ketchum SB, Doyle RT, Julio RA, Jiao L, Granowitz C, et al. Effects of icosapent ethyl on total ischemic events. J Am Coll Cardiol. 2019;73:2791–2802. doi: 10.1016/j.jacc.2019.02.032.
- 6. Bethel MA, Patel RA, Merrill P, Lokhnygina Y, Buse JB, Mentz RJ, Pagliaripo NJ, Chan JC, Gustavson SM, Iqbal N, et al; EXSCEL Study Group. Cardiovascular outcomes with glucagon-like peptide-1 receptor agonists in patients with type 2 diabetes: a meta-analysis. Lancet Diabetes Endocrinol. 2018;6:105–113. doi: 10.1016/S2213-8587(17)30412-6.
- 7. Nidorf SM, Fiolet ATL, Mosterd A, Eikelboom JW, Schut A, Opstal TSJ, The SHK, Xu XF, Ireland MA, Lenderink T, et al; LoDoCo2 Trial Investigators. Colchicine in patients with chronic coronary disease. N Engl J Med. 2020;383:1838–1847. doi: 10.1056/NEJMoa2021372.
- 8. Yu M, Yang Y, Dong L, Zhao C, Yang F, Yuan YF, Liao YH, He SL, Liu K, Wei F, et al. Effect of colchicine on coronary plaque stability in acute coronary syndrome as assessed by optical coherence tomography: the COLOCT randomized clinical trial. Circulation. 2024;150:981–993. doi: 10.1161/CIRCULATIONAHA.124.069808.
- 9. Nasir K, Cánzoles-Achirica M. Role of coronary artery calcium score in the primary prevention of cardiovascular disease. BMJ. 2021;373:n776. doi: 10.1136/bmj.n776.
- 10. Hageman S, Pennells L, Ojeda F, Kaptooge S, Kuulasmaa K, De Vries T, Xu Z, Kee F, Chung R, et al; SCORE2 working group and ESC Cardiovascular risk collaboration. SCORE2 risk prediction algorithms: new models to estimate 10-year risk of cardiovascular disease in Europe. Eur Heart J. 2021;42:2439–2454. doi: 10.1093/eurheartj/ehab309.
- 11. Hageman SM, McCay AJ, Ueda P, Gunn LH, Jennerud H, Tagström E, Bhatt DL, Steg PG, Lill M, Magi R, et al. Estimation of recurrent atherosclerotic cardiovascular event risk in patients with established cardiovascular disease: the updated SMART2 algorithm. Eur Heart J. 2022;43:1715–1727. doi: 10.1093/eurheartj/ehac056.
- 12. Arnett DK, Blumenthal RS, Albert MA, Buroker AB, Goldberger ZD, Hahn EJ, Himelfarb CD, Khera A, Lloyd-Jones D, McEvoy JW, et al. 2019 ACC/AHA guideline on the primary prevention of cardiovascular disease: a report of the American College of Cardiology/American Heart Association Task Force on Clinical Practice Guidelines. Circulation. 2019;140:e596–e646. doi: 10.1161/CIR.0000000000000678.
- 13. D’Agostino RB, Vasan RS, Pencina MJ, Wolf PA, Cobain M, Massaro JM, Kannel WB. General cardiovascular risk profile for use in primary care: the Framingham Heart Study. Circulation. 2008;117:743–753. doi: 10.1161/CIRCULATIONAHA.107.699579.
- 14. Sud M, Sivaswamy A, Chu A, Austin PC, Anderson TJ, Naimark DMJ, Farkouh ME, Lee DS, Roifman I, Thanassoulis G, et al. Population-based recalibration of the Framingham risk score and pooled cohort equations. J Am Coll Cardiol. 2022;80:1330–1342. doi: 10.1016/j.jacc.2022.07.026.
- 15. Damen JA, Pajooyeshin A, Heus P, Moons KGM, Reitsma JB, Scholten RJPM, Hooft L, Debray TPA. Performance of the Framingham risk models and pooled cohort equations for predicting 10-year risk of cardiovascular disease: a systematic review and meta-analysis. BMC Med. 2019;17:109. doi: 10.1186/s12916-019-1340-7.
- 16. Nurmohamed NS, Van Rosendael AR, Danad I, Ngo-Metzger Q, Taub PR, Ray KK, Fichtner G, Bonaca MP, Hisa J, Rodriguez F, et al. Atherosclerosis evaluation and cardiovascular risk estimation using coronary computed tomography angiography. Eur Heart J. 2024;45:1783–1800. doi: 10.1093/eurheartj/ehae190.
- 17. Osborne-Grinter M, Kwicinski J, Doris M, McElhinney P, Cadet S, Adamson PD, Moss AJ, Alam S, Hunter A, Shah ASV, et al. Association of coronary artery calcium score with qualitatively and quantitatively assessed adverse plaque on coronary CT angiography in the SCOT-HEART trial. Eur Heart J Cardiovasc Imaging. 2022;23:1210–1221. doi: 10.1093/ehjci/jeab135.
- 18. Manubolu VS, Ichikawa K, Budoff MJ. Innovations in cardiac computed tomography: Imaging in coronary artery disease. Prog Cardiovasc Dis. 2024;84:51–59. doi: 10.1016/j.pcad.2024.05.005.
- 19. Sato Y, Motoyama S, Miyagi K, Kawai H, Sarai M, Muramatsu T, Takashi H, Naruse H, Ahmadi A, Ozaki Y, et al. Clinical outcomes based on coronary computed tomography-derived fractional flow reserve and plaque characterization. JACC Cardiovasc Imaging. 2024;17:284–297. doi: 10.1016/j.jcmg.2023.07.013.
- 20. Williams MC, Moss AJ, Dweck M, Adamson PD, Alam S, Hunter A, Shah ASV, Pawade T, Weir-McCall JR, Roditi G, et al. Coronary artery plaque characteristics associated with adverse outcomes in the SCOT-HEART study. J Am Coll Cardiol. 2019;73:291–301. doi: 10.1016/j.jacc.2018.10.066.
- 21. Nurlu J, Chandrashekar Y, Ahmadi A, Abbra C, Barman DS, Blankstein R, Leipisj C, Newby D, Nicol ED, Nieman K, et al. SCCT 2021 expert consensus document on coronary computed tomographic angiography: a report of the Society of Cardiovascular Computed Tomography. J Cardiovasc Comput Tomogr. 2021;15:192–217. doi: 10.1016/j.jcct.2020.11.001.
- 22. Expert Panel on Detection, Evaluation, and Treatment of High Blood Cholesterol in Adults. Executive summary of the third report of the National Cholesterol Education Program (NCEP) expert panel on detection, evaluation, and treatment of high blood cholesterol in adults (Adult Treatment Panel III). JAMA. 2001;285:2486–2497. doi: 10.1001/jama.285.19.2486.
- 23. Yesilay A, Kumar AK, Agrawal A, Furqan MM, Verma BR, Syed AB, Majid M, Akyuz K, Rayes DL, Chen D, et al. Predicting long-term clinical outcomes of patients with recurrent pericarditis. J Am Coll Cardiol. 2024;84:1193–1204. doi: 10.1016/j.jacc.2024.05.072.
- 24. Unterhuber M, Krescjp K, Rommel KC, Besler C, Baragetti A, Klöting N, Ceglarek U, Blüher M, Scholz M, Katapana AL, et al. Proteomics-enabled deep learning machine algorithms can enhance prediction of mortality. J Am Coll Cardiol. 2021;78:1621–1631. doi: 10.1016/j.jacc.2021.08.018.
- 25. Diamond GAA. Clinically relevant classification of chest discomfort. J Am Coll Cardiol. 1983;1:574–575. doi: 10.1016/S0735-1097(83)80099-X.
- 26. Mousavi I, Suffredini J, Virani SS, Ballantyne CM, Michos ED, Misa A, Saeed A, Jia X. Early onset atherosclerotic cardiovascular disease. Eur J Prev Cardiol. 2024;32:100–112. doi: 10.1093/eurjpc/zwad240.
- 27. Shah ASV, Lee KK, Pérez JAR, Campbell D, Astengo F, Logue J, Gallacher PJ, Katikireddi SV, Bing R, Alam SR, et al. Clinical burden, risk factor impact and outcomes following myocardial infarction and stroke: a 25-year individual patient level linkage study. Lancet Reg Health Eur. 2021;7:100141. doi: 10.1016/j.lanepe.2021.100141.
- 28. Biavati F, Saba L, Bousseliou M, Kofoed KF, Benetek T, Donnelly P, Rodriguez-Palomares J, Erglis A, Štěsković S, Sakalagà G, et al; DISCHARGE Trial Group. Coronary artery calcium score predicts major adverse cardiovascular events in stable chest pain. Radiology. 2024;310:e231557. doi: 10.1148/radiol.231557.
- 29. Houlberg EJ, Lin F, Bla MJ, Budoff MJ, Van Den Hoogen IJ, Gianni U, Lu Y, Bax AM, Van Rosendael AR, Tantawy SW, et al. Relationship between coronary artery calcium and atherosclerosis progression among patients with suspected coronary artery disease. JACC Cardiovasc Imaging. 2022;15:1063–1074. doi: 10.1016/j.jcmg.2021.12.015.
- 30. Bergström G, Persson M, Adiels M, Björnson E, Bonander C, Ahlström H, Alfreidsson J, Angerås O, Bergland G, Blomberg A, et al. Prevalence of subclinical coronary artery atherosclerosis in the general population. Circulation. 2021;144:916–929. doi: 10.1161/CIRCULATIONAHA.121.055340.
- 31. Han D, Klein E, Friedman J, Gransar H, Achenbach S, Al-Mallah MH, Budoff MJ, Cademartiri F, Maffei E, Callister TQ, et al. Prognostic significance of subtle coronary calcification in patients with zero coronary artery calcium score: from the CONFIRM registry. Atherosclerosis. 2020;309:33–38. doi: 10.1016/j.atherosclerosis.2020.07.011.
- 32. Al’Refai SJ, Malikia G, Singh G, Van Rosendael AR, Ma X, Xu Z, Alawamlh OAH, Lee B, Pandey M, Achenbach S, et al. Machine learning of clinical variables and coronary artery calcium scoring for the prediction of obstructive coronary artery disease on coronary computed tomography angiography: analysis from the CONFIRM registry. Eur Heart J. 2020;41:359–367. doi: 10.1093/eurheartj/ehz565.
- 33. Bell JKL, White S, Hassan O, Zhu L, Scott AM, Clark J, Glaziou P. Evaluation of the incremental value of a coronary artery calcium score beyond traditional cardiovascular risk assessment: a systematic review and meta-analysis. JAMA Intern Med. 2022;182:634–642. doi: 10.1001/jamainternmed.2022.1262.
- 34. Nakazato R, Arsanjani R, Achenbach S, Gransar H, Cheng VY, Dunning A, Lin FY, Al-Mallah M, Budoff MJ, Callister TQ, et al. Age-related risk of major adverse cardiac event risk and coronary artery disease extent and severity by coronary CT angiography: results from 15 187 patients from the international multicentre CONFIRM study. Eur Heart J Cardiovasc Imaging. 2014;15:586–594. doi: 10.1093/ehjci/jet132.
- 35. Motwani M, Dey D, Berman DS, Germano G, Achenbach S, Al-Mallah MH, Andreini D, Budoff MJ, Cademartiri F, Callister TQ, et al. Machine learning for prediction of all-cause mortality in patients with suspected coronary artery disease: a 5-year multicentre prospective registry analysis. Eur Heart J. 2017;38:500–507. doi: 10.1093/eurheartj/ehw188.
- 36. Feuchtner GM, Lacaita PG, Bax JJ, Rodriguez F, Nakanishi R, Pontone G, Mushtaq S, Buchell RR, Gränic C, Patel AR, et al. AI-quantitative CT coronary plaque features associate with a higher relative risk in women: CONFIRM2 registry. Circ Cardiovasc Imaging. 2025;18:e018235. doi: 10.1161/CIRCIMAGING.125.018235.
- 37. Chang HJ, Lin FY, Lee SE, Andreini D, Bax J, Cademartiri F, Chinnaiyan K, Chow BJW, Conte E, Cury RC, et al. Coronary atherosclerotic precursors of acute coronary syndromes. J Am Coll Cardiol. 2018;71:2511–2522. doi: 10.1016/j.jacc.2018.02.079.
