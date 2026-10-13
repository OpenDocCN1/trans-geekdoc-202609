
| 5 || (31,26,1) || 596130 || 298065 || 5.0051 || 41.13 |
| 6 || (31,16,3) || 968750 || 484375 || 3.7412 || 42.4006 |
| 7 || (63,51,2) || 617589 || 308795 || 6.3971 || 40.0710 |
| 8 || (63,36,5) || 874944 || 437472 || 5.6426 || 40.6160 |

From the results in Table 1, it could be seen that the maximum PSNR is obtained for the encoder `(n, k, t)` values of `(7, 4, 1)`, `(15, 5, 3)` and `(63,51, 2)`. Here the optimum value is found by considering the trade off with respect to number of encoded bits also. The lesser the number of encoded bits, the lesser the number of symbols and therefore the lesser is the number of subcarriers required to transmit them across the channel. By looking at the above table of results it can be said that by encoding with parameters of `(7, 4, 1)`, the maximum PSNR value of 42.4006 can be obtained. Thus for further testing, to find the permutation array the `(n, k, t)` value is fixed to be `(7, 4, 1)`. Table 2 gives the result of the MSE and PSNR values obtained by altering the permutation arrays.

### Table 2. MSE and PSNR for different permutation arrays

| Level || Permutation Array || MSE || PSNR |
| --- | --- | --- | --- |
| 1. || `[2 0 1]` || 4.1003 || 42.0037 |
| --- | --- | --- | --- |
| 2. || `[2 0 1 3 4]` || 3.7412 || 42.4006 |
| 3. || `[3 0 5 2 4 1]` || 4.1003 || 42.0027 |
| 4. || `[6 0 5 2 4 1 3]` || 4.0516 || 42.0545 |
| 5. || `[6 0 5 2 7 1 3 4 ]` || 3.3712 || 42.4006 |
| 6. || `[6 0 8 2 7 1 3 4 5]` || 4.7078 || 41.4026 |
| 7. || `[6 9 10 2 7 1 3 4 5 0 8]` || 4.9396 || 41.1939 |

On analysing the Table 2, it is seen that the permutation array of `[2 0 1 3 4]` has given the maximum PSNR value and thus these parameter values of `(n, k, t)` and permutation array can be fixed for employing along with the hardware component of Universal Software Radio Peripheral (`USRP-2920`).

## CONCLUSION

This work focusses on developing OFDM based transceiver using LabVIEW tool and transmit the data using OFDM transceiver. This is achieved with the aid of USRP because it is universally accepted prototype for wireless systems. To over the channel noise BCH encoding scheme has been utilized. To ensure data security the data is Xored with Hadamard matrix. This assures low level of protection to the data transmitted. The work could be extended by replacing Hadamard matrix with strong encryption algorithms. This ensures high level of protection at the cost of complexity.

## ACKNOWLEDGMENT

The Authors would like to express their sincere thanks to SASTRA Deemed University, for the grant received under R&M fund (`R&M / 0027 / SEEE – 010 / 2012 – 13`) to carry out this research work.

## REFERENCES

AlthafC. I. M.PremaS. C. (2018). Covariance and eigenvalue-based spectrum sensing using USRP in real environment. 10th International Conference on Communication Systems & Networks (COMSNETS), 414-417. 10.1109/COMSNETS.2018.8328231

Andrich, C., Ihlow, A., Bauer, J., Beuster, N., & Del Galdo, G. (2018). High-Precision Measurement of Sine and Pulse Reference Signals Using Software-Defined Radio. IEEE Transactions on Instrumentation and Measurement , 67(5), 1132–1141. doi:10.1109/TIM.2018.2794940

ArshadR.SaleemA.KhanD. (2016). Performance comparison of Huffman coding and double Huffman coding. Proceedings Sixth International Conference on Innovative Computing Technology, 361-364. 10.1109/INTECH.2016.7845058

BalouchZ. A.AslamM. I.AhmedI. (2017). Energy efficient image encryption algorithm. Proceedings International Conference on Innovations in Electrical Engineering and Computational Technologies (ICIEECT), 1-6.

Bartalwar, S., & Deepa, T. (2017). Design and implementation of OFDM signal transmission for Visible light communication. International Journal of Engineering Sciences & Research Technology , 6, 577–583.

ChenJ.ZhangS.WangH.ZhangX. (2013). Practicing a Record-and-Replay System on USRP. Proceedings of the second workshop on Software radio implementation forum, 61-64. 10.1145/2491246.2491257

Gouda, M, Hussien, M., Ragab, M.R., Anwar, A.M., & Gouda, A.F. (2017). USRP Implementation of PTS Technique for PAPR Reduction in OFDM Using LABVIEW. Advances is Wireless Communications and Networks, 2, 15-24.

KumarA.KhanA. S.ModanwalN.SahaS. (2019). Experimental Studies on Energy / Eigenvalue based Spectrum Sensing Algorithms using USRP Devices in OFDM Systems. URSI Asia-Pacific Radio Science Conference (AP-RASC), 1-4. 10.23919/URSIAP-RASC.2019.8738506

Kushnure, D., Jiniyawala, M., Molawade, S., & Patil, S. (2017). Implementation of FM Transceiver using Software Defined Radio (SDR). International Journal of Engineering Development and Research , 5, 225–233.

Lee, M. H., Shahab, M. B., Kader, M. F., & Shin, S. Y. (2016). Spatial multiplexing using walsh-hadamard transform. Proceedings International Conference on Smart Green Technology in Electrical and Information Systems (ICSGTEIS), 43-46. Academic Press.

Mathew, P., Augustine, L., & Devis, T. (2014). Hardware Implementation of `(63, 51)` BCH Encoder and Decoder For WBAN Using LFSR and BMA. International Journal on Information Theory , 3(3), 1–11. doi:10.5121/ijit.2014.3301

MusliminJ.AsnawiA. L.IsmailA. F.JusohA. Z. (2016). SDR-Based Transceiver of Digital Communication System Using USRP and GNU Radio. International Conference on Computer and Communication Engineering (ICCCE), 449-453. 10.1109/ICCCE.2016.100

NafkhaA.NaouesM.CichonK.KliksA. (2014). Experimental spectrum sensing measurements using USRP Software Radio platform and GNU-radio. Proceedings 9th International Conference on Cognitive Radio Oriented Wireless Networks and Communications, 429-434. 10.4108/icst.crowncom.2014.255415

Peng, F., Zhang, S., Cao, S., & Xu, S. (2018). A Prototype Performance Analysis for V2V Communications using USRP-based Software Defined Radio Platform. Proceedings 6th IEEE Global Conference on Signal and Information Processing, 1-5.

Praveenkumar, P., Priya, P. C., Avila, J., Thenmozhi, K., Rayappan, J. B. B., & Amirtharajan, R. (2017). Tamper Proong Identification and Authenticated DICOM Image Transmission Using Wireless Channels and CR Network. Wireless Personal Communications, 97, 5573-5595.

Rupali, B. (2018). Patil, K., Kulat, D., & Gandhi, A. S. (2018). SDR Based Energy Detection Spectrum Sensing in Cognitive Radio for Real Time Video Transmission. Modelling and Simulation in Engineering , 1–10.

Salwa, M., & Eldin, S. (2017). Encrypted gray image transmission over OFDM channel for TV cloud computing. International Journal of Speech Technology , 20(3), 431–442. doi:10.1007/s10772-017-9415-3

Saravanan. (2010). Color Image to Grayscale Image Conversion. Proceedings Second International Conference on Computer Engineering and Applications, 96-199. Academic Press.

Serkin, F. B., & Vazhenin, N. A. (2013). USRP platform for communication systems research. Proceedings 2013 15th International Conference on Transparent Optical Networks (ICTON), 1-4. Academic Press.

Shujaat, A. K. T., Rehman, M., Khan, M. B., Jadoon, I., Khan, F. A., Nawaz, F., & Nasir, A. A. (2018). An Experimental Channel Capacity Analysis of Cooperative Networks Using Universal Software Radio Peripheral (USRP). Sustainability , 10, 1–13.

Singh, R., Sharma, S., & Singh, S. (2014). Image Encryption Using Block Scrambling Technique. International Journal of Computer Technology and Applications , 5, 963–966.

Sklar, B., & Ray, P. K. (2001). Digital communication-Fundamentals and applications (2nd ed.). Pearson Education.

Telagam, , N., Lakshmi, S., & Nehru, K. (2019). Digital Audio Broadcasting Based Gfdm Transceiver Using Software Defined Radio . International Journal of Innovative Technology and Exploring Engineering , 8, 273–281.

Telagam, N., Reddy, S., Nanjundan, M., & Nehru, K. (2018). USRP 2901 Based MIMO-OFDM Transceiver in Virtual and Remote Laboratory. International Journal on Computer Science and Engineering , 6, 1033–1040.

# Chapter 13

*   Amany Sarhan
