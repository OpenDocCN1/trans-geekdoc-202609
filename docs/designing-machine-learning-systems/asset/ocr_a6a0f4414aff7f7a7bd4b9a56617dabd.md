![](bbox=[0.13, 0.07, 0.84, 0.38])

Figure 1-4. When processing queries one at a time, higher latency means lower throughput. When processing queries in batches, however, higher latency might also mean higher throughput.

This is even more complicated if you want to batch online queries. Batching requires your system to wait for enough queries to arrive in a batch before processing them, which further increases latency.

In research, you care more about how many samples you can process in a second (throughput) and less about how long it takes for each sample to be processed (latency). You're willing to increase latency to increase throughput, for example, with aggressive batching.

However, once you deploy your model into the real world, latency matters a lot. In 2017, an Akamai study found that a 100 ms delay can hurt conversion rates by 7%.20 In 2019, Booking.com found that an increase of about 30% in latency cost about 0.5% in conversion rates—“a relevant cost for our business.”21 In 2016, Google found that more than half of mobile users will leave a page if it takes more than three seconds to load.22 Users today are even less patient.

20 Akamai Technologies, Akamai Online Retail Performance Report: Milliseconds Are Critical, April 19, 2017, https://oreil.ly/bEtRu.

21 Lucas Bernardi, Themis Mavridis, and Pablo Estevez, “150 Successful Machine Learning Models: 6 Lessons Learned at Booking.com,” KDD ’19, August 4–8, 2019, Anchorage, AK, https://oreil.ly/G5QNA.

22 “Consumer Insights,” Think with Google, https://oreil.ly/JCp6Z.