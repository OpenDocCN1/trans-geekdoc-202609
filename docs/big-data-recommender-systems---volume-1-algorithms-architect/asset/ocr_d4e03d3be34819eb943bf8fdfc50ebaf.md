# Spatiotemporal recommendation with big geo-social networking data 217

![](bbox=[0.135, 0.096, 0.866, 0.273])

Figure 9.10 Efficiency of online recommendations: (a) target region with 100 km × 100 km and (b) target region with 50 km × 50 km

in 12.1 and 3.9 for the target region with 100 km × 100 km and 50 km × 50 km, respectively. From the figures, we observe that (1) “ST-SAGE-TA” outperforms “ST-SAGE-LS” in all querying regions, which demonstrates that the TA-based query processing technique is efficient; (2) “ST-SAGE-TA” and “ST-SAGE-LS” significantly outperform “CKNN,” and “UTE+SE” significantly in both querying regions, showing that the model-based methods produce faster responses to querying users than memory-based methods once the parameters have been learned offline; (3) the time costs of all algorithms in the target region with 100 km × are higher than in the target region with 50 km × 50 km due to the increase of the number of the candidate spatial items; and (4) the time costs of all algorithms increase slowly with the number of recommendations (k).

# 9.6 Related work

With the availability of large-scale user activity records in the physical world, many recent works have tried to improve spatial items recommendation by exploiting the GPS data, geographical and social influence, temporal effect and content information of spatial items.

**GPS data.** The task of spatial item recommendation is highly relevant to human mobility. It is traditionally studied on mobile data, i.e., cellphone-based GPS data. Various works have explored this information to study human mobility and have promoted a set of location-based applications including spatial item recommendation [46–50]. The raw GPS data is a sequence of time-stamped latitude/longitude pairs and there is no mapping information between geo-coordinates and specific real-world spatial items. Thus, a spatial item is extracted from users’ GPS trajectory logs as the stay points on which a user spends sufficient time [51,52]. The data availability of GPS data is limited by the user privacy problem since GPS data is obtained from users’ cell phones through telecommunication services. Generally speaking, existing systems fall into two categories: systems without or