# Recommendation algorithms for unstructured data 155

computation system for processing streams of data. The video recommendation system was in production at Tencent Video. Every day it dealt with billions of user action tuples with size of more than 1 TB. In testing experiments, its performance is undoubtedly superior in production [39].

+   Real-time video recommendation challenges
For real-time recommendations, there exists lots of further works to be done. Only the video-type information was used to measure the content features of videos here. And yet, there exists so many other useful information which can be employed, like the videos directors and actors. Furthermore, combining results from different algorithms to leave benefit of different methods is a better methodology for improving the diversity and novelty of video recommendations.

# 7.2.3.2 Recommendation system for micro-video on big data

One informative form of information called micro-video is what we are going to discuss this point. With the development of the Internet, 3G (the 3rd Generation mobile communication technology) network, and 4G (the 4th Generation mobile communication technology) network, the bandwidth and speed of network increasingly rises. The mentioned technologies make the distribution of information media swift and simple. Micro-video is a type of short video [40] [41], which only lasts for 30 s to 200 s [42]. We can formulate the recommendation issue as follows: assume C is the set of all users and S is the set of all probable items which might be recommended and assume $u$ is an utility function which measures usefulness of item s to user c, i.e., $u:C \times S \rightarrow R$, where $R$ is a totally ordered set. For each user $c$ in $C$, we want to choose item $s \in S$ that maximizes the user's utility.

> $Vc \in C, S_c = \max_{s \in S} u(c, S)$

The utility of an item is generally represented by ratings in recommendation system, which specifies what particular item is liked by a particular user.

+   Content-based recommendation: To represent a text document, Shang et al. always make use of features. The importance of the feature word is measured by feature weighting. The best-known feature weighting algorithm is TF-IDF algorithm [43]. Consider $N$ as the total number of documents that can be recommended to users, and feature $w_i$ appears in $n_i$ of them. Suppose that $f_{i,j}$ is the feature frequency of $w_i$, appears in document $d_j$. Hence, $TF_{i,j}$, the term frequency of

```
$TF_{i,j} = \frac{f_{i,j}}{\max_c f_{c,j}}$
```

where the maximum can be calculated over the frequencies $f_{i,j}$ of all features $w_i$ that appear in the document $d_j$. Yet the features are neither important nor