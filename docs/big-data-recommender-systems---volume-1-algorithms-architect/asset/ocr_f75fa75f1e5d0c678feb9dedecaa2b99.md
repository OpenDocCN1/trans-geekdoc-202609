# Big data recommcommender systems, volume 1

useful, if they appear in various documents. Afterward we can identify the inverse frequency (IDFi) of feature $w_i$ as log

$$$IDF_i = \log \frac{N}{n_i} \quad (7.24)$

Therefore, the TF–IDF weight for feature $w_i$ in document $d_j$ is defined as

$\omega_{ij} = TF_{ij} \times IDF_{ij} \quad (7.25)$

So, the recommended document $d_j$ can be represented as the vector, $d_j = \{(t_{1j}, \omega_{1j}), (t_{2j}, \omega_{2j}), \dots, (t_{ij}, \omega_{ij})}$, where $t_{ij}$ is the $i$th feature in document $d_j$, and $\omega_{ij}$ is the $t_{ij}$s weight.

Several candidate documents are weighed against the input document; this will be done in recommendation system. The utility function $u(c,s)$, in 7.21, is generally an indication of the similarity between the candidate document and the input, for instance cosine similarity.

$u(c,s) = \cos(\omega_c, \omega_s) = \frac{\sum_{i=1}^k \omega_{ic}\omega_{is}}{\|\omega_c\||\omega_s\|}} = \frac{\sum_{i=1}^k \omega_{ic}\omega_{is}}{\sqrt{\sum_{i=1}^k \omega_{ic}^2}\sqrt{\sum_{i=1}^k \omega_{is}^2}} \quad (7.26)$

where $\omega_c$ is the candidate document vector and $k$ is the total number features in the recommendation system.

As an example, in order to suggest users $c$ in the micro video application, the collaboration system attempts to discover other users with similar tastes in videos liked by user $c$. The similarity among users should be considered by particular items. The adjust cost [44], as following formula, is used in CF methods for similarity among users where the difference in each user's rating scale is taken into account.

$sim(i,j) = \sqrt{\frac{\sum_{l_{ij}} (R_{is} - A_i)(R_{js} - A_j)}{\sum_{l_{ij}} (R_{is} - A_i)^2 \sum_{l_{ij}} (R_{js} - A_j)^2}} \quad (7.27)$

where $R_{is}$ stands for rating of item s by user $i$, $A_i$ indicates the average rating of user $i$ for all the co-rated items and $l_{ij}$ signifies the set rated by user $i$ and user $j$.

+   2. Slope recommendation: An open-source machine learning library called Apache Mahout provides a framework of tools that permits powerful and scalable recommendation and classification applications. Slope one [45,46] is a CF framework in Mahout. Slope one, Mahout and Hadoop platform are all based on data. They are able to deal with the computation of large volume data space, like large amount similarity computing. The main idea of Slope one algorithm is to find the similarities between two items along with the users. If we calculate the average rating of the two items and then compare the difference of them, the results would lend us a hand in predicting another user's rating of those items.