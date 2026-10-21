Table 18.9: The stocks with top five lowest correlation values of China Railway Construction.

| Rank | Code | Name | Industry | Correlation |
|---|---|---|---|---|
| 1 | 600518.SH | Kangmei Pharmaceutical Co., Ltd. | Medical | 0.112 |
| 2 | 600893.SH | AVIC Aviation Engine Corporation PLC. | Aerospace | 0.144 |
| 3 | 600637.SH | Shanghai Oriental Pearl Media Co., Ltd. | Media | 0.146 |
| 4 | 002024.SZ | Suning Commerce Group Co., Ltd. | Elec retail | 0.160 |
| 5 | 601727.SH | Shanghai Electric Group Co., Ltd. | Appliance | 0.189 |

# 18.4 Multi-Source Multiple Instance Learning for Market Composite Index Movements¹⁰

# 18.4.1 Overview

In this section, we aim to learn a predictive model for describing the fluctuations of the stock market index, e.g., Dow Jones Index or SSE (Shanghai Stock Exchange) Composite Index. Please note that this goal is different from the studies in Sections 18.2 and 18.3 that aim to predict the movements for each individual stock. We still perform broad learning by utilizing various sources of data, that is, the historical quantitative data, the social media and Web news. The essential features we extract include the event representations from news and the sentiments from social media, and these features are for the overall market rather than for individual stocks.

To conduct predictions, firstly, we propose a novel method to capture the events from short texts. Different from the event extraction method adopted in Section 18.3 that only considers verb or gerund in the sentence, here we model events by considering the structure information of the whole sentence, aiming to capture more effective event information. Specifically, structured events are extracted and then used as the inputs for Restricted Boltzmann Machines (RBM) to do the pre-training. After that, the output vectors from RBMs are used as the inputs to a recently proposed sentence2vec framework (Le and Mikolov, 2014), in order to achieve the event embeddings as features. Secondly, we propose an extension of the Multiple Instance Learning (MIL) model which can effectively integrate the event embeddings, sentiments and the historical quantitative data for accurate predictions. Compared to the