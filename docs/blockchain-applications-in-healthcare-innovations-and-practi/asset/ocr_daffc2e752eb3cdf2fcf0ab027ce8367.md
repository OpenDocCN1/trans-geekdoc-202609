+   - In Blockchain due to cryptography and digital signature, all records are digitally signed by the source hence all records are source verifiable.
+   - Due to decentralization, as data is not with a single node, it can never suffer a single point of failure issues, this makes data always available.
+   - As every block is encrypted in Blockchain by default, it makes sure that the confidentiality of data is not hampered.
+   - Blockchain enables and strengthens patient rights to own, share and control their data.
+   - Permissioned Blockchain assures that malicious nodes cannot participate in the network.
+   - Most importantly, many regulatory requirements related to compliance and agreement between the healthcare entity and patient can be implemented using smart contracts and consensus algorithms.

# 7.5. Differential privacy

The idea of differential privacy (Ul Hassan et al. 2020) was first introduced by C. Dwork in 2006 for statistical datasets. To understand it mathematically, differential privacy is adding noise in the data to preserve its privacy. Consider a function that analyzes a dataset and computes statistical results such as mean, median and variance. Now, if the algorithm of this function is enhanced in such a way that by looking at the output no one can tell whether an individual’s data was used as input in the dataset or not, in this situation, the algorithm will be considered as differentially private (Ul Hassan et al. 2020).

Let us take a simple example: during market research, a team wants to know “how many people have watched the series Friends”, “how many have watched Suits” and “how many have watched Joker”. Now if the system answering these questions have algorithms which are differentially private, it will first add noise to the real values and then will provide the approximate data to the market research team. This approximate data will draw the same conclusions as what actual data would have done so in this way it will not affect the market research team too. This is the main benefit of differential privacy, i.e. the data can be used for analysis while guaranteeing the protection of individual’s privacy.

Let us take another example: a curator asks a medical data owner to check a dataset of patients who have died in the last five years in a particular city and answer for each patient whether they died of cancer. The medical data owner agrees to provide an approximate count based on an algorithm, rather giving actual data. The