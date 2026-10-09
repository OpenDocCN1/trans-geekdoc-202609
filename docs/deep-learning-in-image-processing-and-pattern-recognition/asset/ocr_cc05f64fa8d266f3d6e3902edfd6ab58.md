# 5. Conclusions

In this paper, through the processing and analysis of an actual spectrum observation data set, we find that the spectrum utilization rate of the GSM900 band is not high, and there is a large waste of resources, which proves that the spectrum in today’s world has a major problem. Based on this, we propose the B-LTF algorithm to predict the spectrum using neural networks. In it, we analyze the performance of four network models, namely the B-LTF model, GRU model, LSTM model and BP model, in predicting the channel occupancy status and predicting the future spectrum trend in detail. From the overall simulation results, the prediction effect of the long short-term memory network and its improved model is better than that of the BP network model, which also proves that they have a strong ability to deal with time series. When predicting the channel occupancy state, the B-LTF model improves the prediction accuracy by about 1% to 2% compared with the LSTM and GRU models. In the spectrum signal trend prediction, the B-LTF model can predict the overall trend and amplitude change of the future spectrum signal more effectively, but the sequence length has a great influence on the prediction results in the overall simulation and the operation time is too long. Therefore, how to reduce the operation time and reduce the impact of sequence length on the prediction results while improving the spectrum prediction performance are the main issues worth exploring in future research.

**Author Contributions:** Q.C. and X.W. put forward the idea of this paper. Q.C. finished the design of the study and the algorithms. Q.C. and X.W. contributed to the experimental work and the data analysis. Q.C. and X.Y. made figures and tables. Q.C. and X.W. drafted the manuscript. All authors have read and agreed to the published version of the manuscript.

**Funding:** This research was funded by Heilongjiang Postdoctoral Foundation, grant number LBH-Z19168 and Heilongjiang Provincial Natural Science Foundation of China, grant number YQ2022F014.

**Institutional Review Board Statement:** Not applicable.

**Informed Consent Statement:** Not applicable.

**Data Availability Statement:** Not applicable.

**Conflicts of Interest:** The authors declare no conflict of interest.

# References

+   1.  Kolodzy, P. *Spectrum Policy Task Force Report*; FCC ET Docket No. 02-155; Federal Communications Commission: Washington, DC, USA, 2002; Volume 40, pp. 147–158.

+   2.  Kiftaro, F.; El-Tarhouni, M.; Assaleh, K. UHF Spectrum Occupancy Measurements in Sharjah—UAE. In *Proceedings of the 2017 9th IEEE-GCC Conference and Exhibition (GCCCE)*, Manama, Bahrain, 8–11 May 2017.

+   3.  Yu, X.; Kong, M.; Li, X. Spectrum occupancy in the 87.5–108 MHz band: Measurement and analysis. In *Proceedings of the 2017 IEEE 2nd Advanced Information Technology, Electronic and Automation Control Conference (IAEAC)*, Chongqing, China, 25–26 March 2017.

+   4.  Ramírez, D.; Cardenas-Juarez, M.; Pineda-Rico, U. Spectrum Occupancy Measurements in the Sub-6 GHz Band for Smart Spectrum Applications. In *Proceedings of the 2018 IEEE 10th Latin-American Conference on Communications (LATICOM)*, Guadalajara, Mexico, 14–16 November 2018.

+   5.  Engiz, B.K.; Rajab, Y.A. Investigation of Spectrum Occupancy in GSM Band in Samsun, Turkey. In *Proceedings of the 2019 6th International Conference on Electrical and Electronics Engineering (ICEEE)*, Istanbul, Turkey, 16–17 April 2019.

+   6.  Zulfiqar, M.D.; Ismail, K.; Hassan, N.U. Radio Spectrum Occupancy Measurement from 30MHz-1030MHz in Pakistan. In *Proceedings of the 2019 UK / China Emerging Technologies (UCET)*, Glasgow, UK, 21–22 August 2019.

+   7.  Tandra, R.; Sahai, A. Fundamental limits on detection in low SNR under noise uncertainty. In *Proceedings of the 2005 International Conference on Wireless Networks, Communications and Mobile Computing*, Maui, HI, USA, 13–16 June 2005.

+   8.  Mitola, J.; Maguire, G.Q. Cognitive radio: Making software radios more personal. *IEEE Pers. Commun.* **1999**, *6*, 13–18. [CrossRef]

+   9.  Woods, T.; Furman, S. All-Domain Spectrum Software and Control via Hierarchical Dynamic Spectrum Sharing with Implemented Dynamic Spectrum Access Toolchain. In *Proceedings of the MILCOM 2021–2021 IEEE Military Communications Conference (MILCOM)*, San Diego, CA, USA, 29 November–2 December 2021.

+   10.  Madhavan, A.; Govindarajan, Y. Wideband Spectrum Sensing in Dynamic Spectrum Access Systems Using Bayesian Learning. *J. Phys. Conf. Ser.* **2021**, *1964*, 62067–62075. [CrossRef]