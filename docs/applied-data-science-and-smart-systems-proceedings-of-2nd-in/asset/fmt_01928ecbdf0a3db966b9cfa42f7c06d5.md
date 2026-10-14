
Twitter is one of the important data sources for analyzing several factors during corona Covid-19 pandemic situation since October 2019. A detailed analysis of the Covid-19 vaccine been carried out based on 4 million tweets and the parameter were discovered as the number of tweets who are against the vaccine (anti-vaccine) and who support the vaccine (pro-vaccine) (e) (Yousefinaghani Samira et al., 2021). Similarly, the key indicators of economic tensions and war in Ukraine are analyzed using Twitter based on 42 million tweets. It also highlights the impact of war on the US dollar value and crude oil values across the globe (`/path.to.xxx`)(Polyzos, 2022)(`#ch25.xhtml#ref25_8`)). Twitter data quality standards practices are one of the crucial factors which handle the further analytical process and correct results (`#Salvatore et al., 2021`)(`#ch25.xhtml#ref25_9`)). Feng Yunhe et al. (2023) have supplied the impact of chat-GPT on streaming media using social media platforms such as Twitter and Reddit. The study has been collected on real-time analysis where the response time. The Reddit forum data is used to gather the students’ requirements for changes in the infrastructure requirement during corona Covid-19 pandemic outbreak (`#Feng et al., 2023`)(`#ch25.xhtml#ref25_10`)). Additionally, the student’s mental health parameters are also evaluated on the loan debts using Twitter and Reddit platforms (`#Sinha et al., 2023`)(`#ch25.xhtml#ref25_12`)). The Reddit posts are majorly used for topic modeling because the users post comments in the sub-reddit group (`#Bonifazi et al., 2023`)(`#ch25.xhtml#ref25_13`)). The New York Times newspaper articles are used to evaluate the post-covid economic recession conditions across the globe. `[Barhanpurkar et al.’s study (2023)`](#ch25.xhtml#ref25_15) in which the authors have performed sentiment analysis, entity recognition, and topic modeling. The sentiment analysis and NLP processing techniques are used to gain insights from the corona Covid-19 pandemic outbreak on NY Times articles (`#Tunca et al., 2023`)(`#ch25.xhtml#ref25_16`)). In `[Table 25.1](#ch25.xhtml#tab25_1)`, the different studies show the use of Twitter, Reddit, and the New York Times which shows the broad spectrum of domains in which the data is used.

[Table 25.1 Comparative analysis of different studies associated with Twitter, Reddit, and the New York Times.](#ch25.xhtml#R_tab25_1)

| Study || Year || Platform || Domain |
| --- | --- | --- | --- |
| [Edo-Osagie et al.](#ch25.xhtml#ref25_17) || 2020 || Twitter || Public Health care |
| [Malik et al.](#ch25.xhtml#ref25_18) || 2019 || Twitter || Education |
| [Baker et al.](#ch25.xhtml#ref25_19) || 2021 || Twitter || Economics |
| [Pirina et al.](#ch25.xhtml#ref25_20) || 2018 || Reddit || Public healthcare |
| [Karpenko et al.](#ch25.xhtml#ref25_21) || 2021 || Reddit || Personal banking |
| [Ireland et al.](#ch25.xhtml#ref25_21) || 2023 || Reddit || Employment sector |
| [Alieva](#ch25.xhtml#ref25_23) || 2023 || New York Times || Government |
| [Rodden](#ch25.xhtml#ref25_24) || 2021 || New York Times || Economics |
| [Costola et al.](#ch25.xhtml#ref25_25) || 2023 || New York Times || Economics |
| [Ujewe](#ch25.xhtml#ref25_26) || 2023 || New York Times || Humanities |

## Proposed methodology

In `[Figure 25.1](#ch25.xhtml#fig25_1)`, the research methodology employed during the research is described. In the initial step of data collection and storage, data is obtained from three various sources, including tweets from Twitter API, sub-reddit comments from Reddit API, and New York Times articles and headlines from New York Times Archive API. The streaming data from the sources is being stored in the MySQL database using the MySQL Connector. After the completion of the data collection and storage phase, the data cleaning step is carried out to get the data ready for NLP operations. Punctuation removal, tokenization, and stemming are some of the techniques used to refine the data. In the data visualization and analytics stage, the processed data is finally used to generate insights on the recession condition, economic crisis, and inflation markers. The methods used for generating insights consist of time series analysis, memory usage analysis, word cloud analysis, word frequency analysis, and lastly, the sentiment analysis. Time series analysis is used to identify trends in the data and cyclical patterns that focus on how the nature of the data has changed over time. Furthermore, memory usage analysis optimizes data processing workflows by ensuring the scalability of computational resources. The word cloud analysis simultaneously visualizes the major themes in the data and growing trends are revealed by word frequency analysis. Thus, word cloud analysis and word frequency analysis are the two major steps of keyword analysis for large scale textual datasets.

```
![Figure 25.1 Data flow diagram](images/fig25_1_B.jpg)
```

[Figure 25.1 Data flow diagram](#ch25.xhtml#R_fig25_1)

## Results and discussion

The five parameters that were taken into consideration for analysis of Twitter, Reddit and New York Times are Time Series Analysis, Memory Usage Analysis, Word Frequency Analysis, Word Cloud Analysis and Sentiment Score analysis. `[Figure 25.2](#ch25.xhtml#fig25_2a)(a)` consists of a graph illustrating the data collected from tweets related to the recession over the span of 21 days starting from November 1st to 21st, 2023. The x-axis of the graph represents the dates when the data is being collected, and the y-axis represents the number of tweets we have collected on dates. We have collected 155,218 tweets, 240,079 sub-reddit articles (`#Figure 25.2`)(`#ch25.xhtml#fig25_2b`)(`#ch25.xhtml#fig25_2c`)) and 616,895 comments (`#Figure 25.2`)(`#ch25.xhtml#fig25_2c`)) collected using Twitter, New York Times, and Reddit, respectively.

![Figure 25.2(a) Tweets collected over time for recession](images/fig25_2a_C.jpg)

[Figure 25.2(a) Tweets collected over time for recession](#ch25.xhtml#R_fig25_2a)

![Figure 25.2(b) Data collected for recession comments (Reddit)](images/fig25_2b_C.jpg)

[Figure 25.2(b) Data collected for recession comments (Reddit)](#ch25.xhtml#R_fig25_2b)

![Figure 25.2(c) News articles collected over time for recession](images/fig25_2c_C.jpg)

[Figure 25.2(c) News articles collected over time for recession](#ch25.xhtml#R_fig25_2c)

For recession tracking, the use of real-time data is a fundamental step in the evolution of social media platforms such as Twitter, Reddit, and The New York Times. These benefits include quicker response to economic events, early identification of sentiment shifts, capture unconventional indicators, interactive analysis with the public, complementary insights to traditional indicators, and fostering innovative data analytics techniques. It shows the data collection steps that are carried out from the different data sources. We have used open-sourced platforms Twitter API, Reddit API and NYTimes API for data collection (`#Table 25.2`)(`#ch25.xhtml#tab25_2`).

[Table 25.2 Comparison of number of records and memory usage for various datasets.](#ch25.xhtml#R_tab25_2)

| S. No. || Dataset || Number of records || Memory usage |
| --- | --- | --- | --- |
| 1. || Twitter || 155,218 tweets || 40.58 MB |
| --- | --- | --- | --- |
| 2. || Reddit || 616,895 reddit comments || 62.59 MB |
| 3. || New York Times || 240,079 articles || 49.58 MB |

[Figure 25.3](#ch25.xhtml#fig25_3) consists of a graph in which the x-axis represents the number of days we collect the data from the data sources. The y-axis represents the dataset size which is the size of data collected for the corresponding days. This graph provides an insight into the memory usage done by each dataset as data sources like Reddit, Twitter, and NYTimes produce hugely various kinds of data.

![Figure 25.3 Memory-usage of each data source](images/fig25_3_C.jpg)

[Figure 25.3 Memory-usage of each data source](#ch25.xhtml#R_fig25_3)
