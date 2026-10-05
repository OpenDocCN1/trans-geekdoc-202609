# Spatiotemporal recommendation with big geo-social networking data 213

![](bbox=[0.148, 0.095, 0.856, 0.273])

Figure 9.5 Performance on Foursquare dataset: (a) out-of-town and (b) hometown

![](bbox=[0.148, 0.346, 0.856, 0.523])

Figure 9.6 Performance on Twitter dataset: (a) out-of-town and (b) hometown

ST-SAGE is about 0.457 when $k = 5$ and 0.535 when $k = 10$. This means that there is a probability of 45.7% that ST-SAGE will place an appealing point of interest in the top-5 recommendations and a 53.5% probability that it will be placed in the top-10 recommendations. Clearly, our proposed ST-SAGE model outperforms other competitor models significantly, demonstrating the advantages of ST-SAGE over other competitor methods. Several observations are made from the results: (1) ST-SAGE outperforms two other models that also integrate the temporal information: UTE+SE [9] and JIM [29], demonstrating the advantages of ST-SAGE over other competitor methods which also integrate the temporal information. (2) CKNN performs worst as it does not explore the spatial-temporal dynamics since the local experts discovered by CKNN (3) UPS-CF falls behind ST-SAGE and LCA-LDA, demonstrating the advantages of using the latent topic to capture users' interests by exploiting the content of their visited spatial items. Through the medium of content, ST-SAGE and LCA-LDA transfer users' interests inferred from the hometown to out-of-town regions. In contrast, UPS-CF is a mixture of collaborative filtering and social filtering, which ignores the effect of content. Besides, according to the recent survey in [11], for movement farther