
# RESULTS AND DISCUSSION

For testing initially a mobile application as discussed in the methodology is created and connected to free base engine. Then the operation of the parametric module is carried out and the data is collected and tested, for the purpose of testing the compression random images are chosen and then loaded. Given below are the statics of size of images before after compression respectively. The testing is carried out and the observations are plotted in the Table 1 given below.

Table 1. Results of compression of the random test images, before and after.

| Image no | Before compression | After compression |
| --- | --- | --- |
| Image 1 | 4.53 MB | 534 KB |
| Image 2 | 2.62 MB | 175 KB |
| Image 3 | 2.10 MB | 126 KB |
| Image 4 | 6.23 MB | 934.5 KB |
| Image 5 | 8.06 MB | 1.01 MB |
| Image 6 | 1.45 MB | 233.870 KB |

The equation for calculating the compression ratio is as given below where we can see the ratio of uncompressed to compressed image is calculated

> $Compression ratio(CR) = \frac{Uncompressed image size}{Compressed image size} (1)$

The calculation of the various images selected are performed below for the ratio understanding

> $CR \text{ of image } 1 = \frac{4.53 * 1000}{534} = 8.4831 (2)$

> $CR \text{ of image } 2 = \frac{2.62 * 1000}{175} = 14.971 (3)$

> $CR \text{ of image } 3 = \frac{2.10 * 1000}{126} = 16.667 (4)$

> $CR \text{ of image } 4 = \frac{6.23 * 1000}{934.5} = 6.667 (5)$

> $CR \text{ of image } 5 = \frac{8.06}{1.01} = 8.514 (6)$

> $CR \text{ of image } 6 = \frac{1.45 * 1000}{233,870} = 6.202 (7)$

As the in the equation shows the Compression ratio of various images and their transfer rates it us understand that compression works on the images very well and this definitely help the faster transfer of the images.

Figure 4 shows the compression ratio (CR) of all the test image a bar chart. Here we can see the compression ratio varies between 5% ~20%.The difference between the time to upload a compressed image and time to upload an uncompressed image is huge. Considering that the quality loss of image is very minimal and undetectable by the human eye, in depth statistics about the stream published and subscribed using OpenTok API are also available for the developer this is the main feature which helps the processing of the data, images and videos faster without queue limits.

## Compression ratio (KB)

![](img/a35f8e852e0ee65e528c95ad0821783b_131_0.png)

Figure 4. Compression ratio of the various images.

The Table 2 given above shows the usage statistics based on the user interaction. Each account holder has an unique ID and can create project which are also depicted with ID, each of the users will have their type of stream or route they would use in the application which is recorded in the cloud. Table 2 result is obtained from the cloud dashboard API which takes account for the improvement of the system based on usage statistics. The proposed API with the help of the image compression helps in faster uploading and downloading data which is very much required in the case of telemedicine approach. Thus this system is an useful frame for interactive data transfer.

Table 2. Usage statistics of streaming of images available from API.

| Account ID | Project ID | Type | Usage |
|---|---|---|---||
| 3574702 | 4628262 | Hours | 0.34166667 |
| 3574702 | 4628262 | Streamed Subscribed Minutes | 17.95 |
| 3574702 | 4628262 | Streamed Subscribed Routed Minutes | 17.95 |
| 3574702 | 4628262 | Session Minutes | 17.9 |

## 7 CONCLUSION

The pandemic and necessity for telemedicine data transfer has created needing for an efficient technique or interactive framework for data sharing. This proposed work demonstrates a frame work makes the data sharing with help of API and compression technique. The system interactive paramedics connected with patient with present to share the data or perform a live streaming to a doctor who helps in the pre hospitalization scenario. The system is one stop solution for data sharing which with a real time experiment conducted with an android end Open-tk server API and The system provides an efficient interactive framework to manage the live stream videos as fast as the system compression frame. The results of usage of the real time system show that which accelerates the data sharing which will aid for telemedicine and remote consultation. This work can be integrated into hospital management system to aid many difficult pre hospitalization or hospital transfer very efficiently with the user friendly application and efficient storage and retrieval system.

## REFERENCES

- [1] Al-Dharabi, Y., Paraiso, F., Djaralla, N., & Merle, P. (2018). Elasticity in Cloud Computing: State of the Art. IEEE Transactions on Services.
- [2] Birman, K., Chocker, G., & van Renesse, R. (2009). Toward A Cloud Computing Agenda. ACM SIG News. https://doi.org/10.1145/15614.15612
- [3] Russkov, A. (2014). Shared Storage Performance of Cloud Computing: OpenNebula Nebula. In 2014 3rd International Conference on Cloud Networking, CloudNet 2014. https://doi.org/10.1109/CloudNet2014.06007
- [4] Wang, J., Peng, G., Xe, Y., & Fu, J. (2010). Cloud Storage As Infrastructure of Cloud Computing. In Proceedings - 2010 International Conference on Intelligent Computing and Cognitive Informatics, ICICI.
- [5] Prabhavathy, B., Priya, K., & Babu, C. (2013). Load Balancing Algorithm For Private Storage. In 2013 4th International Conference on Cloud Computing, Communications and Technologies, ICCNT. https://doi.org/10.1109/ICCNT2013.67285
- [6] Cimeone, A., Laurentis, C., Massimo, A., Sernov, V., & Debre, C. (2016). Analysis of Cloud Systems. In 2016 30th International Conference on Advanced Information Networking and Applications (WAINA), 193–243. https://doi.org/10.1109/WAINA.2016.923
- [7] Li, Z., et al., "Efficient Synchronization in Dropbox-Like Cloud Services," 3rd International Conference on Cloud Based Computing, pp. 1–7.
- [8] Rahat, A., Parsa, I., & Babu, P. W. (2017). Interactive Clinical Information System Using Firebase and Google Maps, (7), 8–12.
- [9] Bocchi, E., Dario, L., & Mellia, M. (2015). Personal Storage Comparisons and Benchmark. In Transactions on Cloud Computing, 554–764. https://doi.org/10.1109/tcc.2015.242719
- [10] Esposito, E., Dario, L., & Mellia, M. (2015). Personal Storage Comparisons and Benchmark. In Transactions on Cloud (March).
- [11] Johnson, A., Yu, S., & Singh, K. (2018). Telehealth Web in an Enterprise Era. IEEE Communications Magazine, 51(4), 48–54. https://doi.org/10.1109/MCOM.2018.80570
- [12] Liu, Y., Guo, J., & Liang, C. (2008). A Survey on Peer-to-Peer Video Streaming Systems. In Peer-to-Peer Networking and Applications, (1), 18–28. https://doi.org/10.1007/s10283-007-006-y
- [13] Wade V.A., Karnon, Elijah A.G., & Heller J.E. (2010). A Systematic Review of Economic Analyses of Telehealth Services Using Electronic Health Records. Health Research, 10
- [14] Mukhopadhyay, A., Shaj, R. P., & Raj, A. (2018). Delay Reduced Multimedia Transmission in JPEG Algorithm to Improve Image Compression. 2018 International Conference on Advances in Computing, Communications and Informatics, ICACCI 2018. https://doi.org/10.1109/ICACCI2018.855473
- [15] Mukhopadhyay, A., Shaj, R. P., & Raj, A. (2018). ICCACCI2018, 1313–1319. https://doi.org/10.1109/ICACCI2018.855470
- [16] Parekh M. & Saleena B. U. (2015). "Designing a Cloud Based Framework for HealthCare System and Applying Clustering Techniques for Region Wise Diagnosis," Procedia Comput., Vol. 50, pp. 537–542, Jan, 2015.
- [17] Javad, M., Haleem, A., Raj, R. P., Sultan, S., and Khan, I.H. (2022). Evolutionary Trends in Cloud Computing: Challenges and Barriers., Int. J. Cogn. Eng., vol. 3, pp. 124–135, Jun, 2022. https://doi.org/10.1016/ijce.2022.06.001.
- Hussein N.W., Hussain H.N. and Humod I.M., (2022), "A Proposed Framework for Healthcare Based on Cloud Computing and IoT Applications," Future. Gen.
