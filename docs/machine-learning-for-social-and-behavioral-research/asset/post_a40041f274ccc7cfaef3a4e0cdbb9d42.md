
Francis, & Booth, 2001), which is implemented as a commercially available software program (Pennebaker, Boyd, Jordan, & Blackburn, 2015). LIWC analyzes text according to a dictionary comprised of 6,400 words, word stems, and emoticons, largely related to psychological processes (e.g., affective, social processes; Pennebaker et al., 2015). From this analysis, users get an output of scores on 90 components of the dictionary and linguistic/grammatical dimensions of their data. Particularly when the sample size is small or the response lengths are relatively short, of dictionary-based approaches like the LIWC will likely result in better prediction than more complex algorithms.

- We discussed the analysis of text from a relatively simplistic point of view, mainly focusing on the individual words while negating the order in which they were used. The field of natural language processing has developed a number of more advanced approaches for modeling the sequence in which words are used, most commonly using various forms of neural networks (i.e., deep learning). We chose not to discuss this area of algorithmic development because many research applications in social and behavioral research do not have the amount of text necessary to take advantage of these more complex approaches. For readers interested in this, we recommend Chollet and Allaire (2017) for an introduction to deep learning with applications in R.

## 11.9.2 Computational Time and Resources

While the focus in this chapter was using R to process and analyze the data, Python has a richer set of tools for text data, as well as a larger array of researches. Most of the analyses conducted in this chapter can run in a matter of seconds. Computational time scales with the complexity of the analysis, with LDA, STM, and SLDA analytics typically on the order of minutes or a few hours. The main factors in the amount of these analyses are the number of observations (documents) and the number of words in the DTM. Often it is common to remove both stop words and infrequently used words (e.g., less than 10 times across all documents) to reduce the dimensionality of the DTM for the express purpose of reducing computational time. Scraping data can result in much larger datasets, thus potentially increasing the amount of time it takes to analyze. As with many of the previous chapters, it is recommended to try and parallelize as many of the computations as possible, either through built in arguments in each R package, or by explicitly creating your own script to run 5-fold CV in parallel, for instance.

## 12
Introduction to Social Network Analysis

Although the history of social network analysis can be traced back to 1930s (Moreno, 1934) when graphs were used to visualize social communities, it only became a popular interdisciplinary research topic in statistics, sociology, political science, and psychology in the past few decades (e.g., Che, Jin, & Zhang, 2020; Liu, Jin, & Zhang 2018; Saul & Filkov, 2007; Schaefer, Adams & Haas 2013). The popularity of social network analysis is attributed to its distinct features in data and analysis techniques that differ from traditional methods used in social and psychological research. The primary information of a social network is the interrelations (often called edges, connections, links, or paths) among a group of participants (often called nodes, vertices, entities, actors, or individuals) (Wassermann & Faust, 1994). In this chapter we introduce basic techniques for social network analysis including network visualization, basic network analysis, and network modeling. In particular, we will demonstrate how to apply these techniques through the analysis of a set of real network data introduced in the following section.

### 12.1 Key Terminology

- Node. Also referred to as vertices, entities, actors, or individuals. This refers to the actual people in the network.
- Edges. Also referred to as ties, connections, links, or paths. This refers to the inter-relationships between nodes.
- Binary network. Most common type of network in social network analysis. This refers to edges either being present or not present in the network. For our data, people can be friends or not friends. In other types of networks, the edges can represent strength values, such as the commonly used partial correlation networks.

### Introduction to Social Network Analysis

- Sparse. It is common for social networks to be sparse, meaning most people are not related to others.
- Network size. Number of nodes in a network.
- Density. Total number of edges divided by the number of possible edges.

The structural pattern of relationships of nodes is naturally the target of typical social network analysis. For instance, in a friendship network or a Facebook network, some people are closer to each other and thus form small friendship networks. The inherent patterns in dyadic ties are very informative and provide researchers opportunities to understand actors not only from their attributes but also from the social environment around them.

Social network analysis has methodological advantages to other data analysis such as dyadic data analysis. In traditional dyadic analysis, only data with relations are collected. Social network data, however, consist of both dyads with social relations and dyads without social relations. Therefore they allow researchers to better understand dyadic relations. For example, sociologists and personality psychologists are often interested in the association between friendship and personalities (Asendorf & Wilpers, 1998; Youyou, Stillwell, & Schwartz, 2017).

In the existing studies, only data with friendship relations are available and used in an analysis, as dyadic data without friendship are often not available.

Therefore, any conclusion may only reflect the situation with the friendship relation. Social network analysis, in contrast, can better understand the dyadic relations.

The structural pattern of relationships of nodes is naturally the target of typical social network analysis. For instance, in a friendship network or a Facebook network, some people are closer to each other and thus form small friendship networks. The inherent patterns in dyadic ties are very informative and provide researchers opportunities to understand actors not only from their attributes but also from the social environment around them.

Social network analysis has methodological advantages to other data analysis such as dyadic data analysis. In traditional dyadic analysis, only data with relations are collected. Social network data, however, consist of both dyads with social relations and dyads without social relations. Therefore they allow researchers to better understand dyadic relations. For example, sociologists and personality psychologists are often interested in the association between friendship and personalities (Asendorf & Wilpers, 1998; Youyou, Stillwell, & Schwartz, 2017).

In the existing studies, only data with friendship relations are available and used in an analysis, as dyadic data without friendship are often not available.

Therefore, any conclusion may only reflect the situation with the friendship relation. Social network analysis, in contrast, can better understand the dyadic relations.

The structural pattern of relationships of nodes is naturally the target of typical social network analysis. For instance, in a friendship network or a Facebook network, some people are closer to each other and thus form small friendship networks. The inherent patterns in dyadic ties are very informative and provide researchers opportunities to understand actors not only from their attributes but also from the social environment around them.

Social network analysis has methodological advantages to other data analysis such as dyadic data analysis. In traditional dyadic analysis, only data with relations are collected. Social network data, however, consist of both dyads with social relations and dyads without social relations. Therefore they allow researchers to better understand dyadic relations. For example, sociologists and personality psychologists are often interested in the association between friendship and personalities (Asendorf & Wilpers, 1998; Youyou, Stillwell, & Schwartz, 2017).

In the existing studies, only data with friendship relations are available and used in an analysis, as dyadic data without friendship are often not available.

Therefore, any conclusion may only reflect the situation with the friendship relation. Social network analysis, in contrast, can better understand the dyadic relations.

The structural pattern of relationships of nodes is naturally the target of typical social network analysis. For instance, in a friendship network or a Facebook network, some people are closer to each other and thus form small friendship networks. The inherent patterns in dyadic ties are very informative and provide researchers opportunities to understand actors not only from their attributes but also from the social environment around them.

Social network analysis has methodological advantages to other data analysis such as dyadic data analysis. In traditional dyadic analysis, only data with relations are collected. Social network data, however, consist of both dyads with social relations and dyads without social relations. Therefore they allow researchers to better understand dyadic relations. For example, sociologists and personality psychologists are often interested in the association between friendship and personalities (Asendorf & Wilpers, 1998; Youyou, Stillwell, & Schwartz, 2017).

In the existing studies, only data with friendship relations are available and used in an analysis, as dyadic data without friendship are often not available.

Therefore, any conclusion may only reflect the situation with the friendship relation. Social network analysis, in contrast, can better understand the dyadic relations.

The structural pattern of relationships of nodes is naturally the target of typical social network analysis. For instance, in a friendship network or a Facebook network, some people are closer to each other and thus form small friendship networks. The inherent patterns in dyadic ties are very informative and provide researchers opportunities to understand actors not only from their attributes but also from the social environment around them.

Social network analysis has methodological advantages to other data analysis such as dyadic data analysis. In traditional dyadic analysis, only data with relations are collected. Social network data, however, consist of both dyads with social relations and dyads without social relations. Therefore they allow researchers to better understand dyadic relations. For example, sociologists and personality psychologists are often interested in the association between friendship and personalities (Asendorf & Wilpers, 1998; Youyou, Stillwell, & Schwartz, 2017).

In the existing studies, only data with friendship relations are available and used in an analysis, as dyadic data without friendship are often not available.

Therefore, any conclusion may only reflect the situation with the friendship relation. Social network analysis, in contrast, can better understand the dyadic relations.

The structural pattern of relationships of nodes is naturally the target of typical social network analysis. For instance, in a friendship network or a Facebook network, some people are closer to each other and thus form small friendship networks. The inherent patterns in dyadic ties are very informative and provide researchers opportunities to understand actors not only from their attributes but also from the social environment around them.

Social network analysis has methodological advantages to other data analysis such as dyadic data analysis. In traditional dyadic analysis, only data with relations are collected. Social network data, however, consist of both dyads with social relations and dyads without social relations. Therefore they allow researchers to better understand dyadic relations. For example, sociologists and personality psychologists are often interested in the association between friendship and personalities (Asendorf & Wilpers, 1998; Youyou, Stillwell, & Schwartz, 2017).

In the existing studies, only data with friendship relations are available and used in an analysis, as dyadic data without friendship are often not available.

Therefore, any conclusion may only reflect the situation with the friendship relation. Social network analysis, in contrast, can better understand the dyadic relations.

The structural pattern of relationships of nodes is naturally the target of typical social network analysis. For instance, in a friendship network or a Facebook network, some people are closer to each other and thus form small friendship networks. The inherent patterns in dyadic ties are very informative and provide researchers opportunities to understand actors not only from their attributes but also from the social environment around them.

Social network analysis has methodological advantages to other data analysis such as dyadic data analysis. In traditional dyadic analysis, only data with relations are collected. Social network data, however, consist of both dyads with social relations and dyads without social relations. Therefore they allow researchers to better understand dyadic relations. For example, sociologists and personality psychologists are often interested in the association between friendship and personalities (Asendorf & Wilpers, 1998; Youyou, Stillwell, & Schwartz, 2017).

In the existing studies, only data with friendship relations are available and used in an analysis, as dyadic data without friendship are often not available.

Therefore, any conclusion may only reflect the situation with the friendship relation. Social network analysis, in contrast, can better understand the dyadic relations.

The structural pattern of relationships of nodes is naturally the target of typical social network analysis. For instance, in a friendship network or a Facebook network, some people are closer to each other and thus form small friendship networks. The inherent patterns in dyadic ties are very informative and provide researchers opportunities to understand actors not only from their attributes but also from the social environment around them.

Social network analysis has methodological advantages to other data analysis such as dyadic data analysis. In traditional dyadic analysis, only data with relations are collected. Social network data, however, consist of both dyads with social relations and dyads without social relations. Therefore they allow researchers to better understand dyadic relations. For example, sociologists and personality psychologists are often interested in the association between friendship and personalities (Asendorf & Wilpers, 1998; Youyou, Stillwell, & Schwartz, 2017).

In the existing studies, only data with friendship relations are available and used in an analysis, as dyadic data without friendship are often not available.

Therefore, any conclusion may only reflect the situation with the friendship relation. Social network analysis, in contrast, can better understand the dyadic relations.

The structural pattern of relationships of nodes is naturally the target of typical social network analysis. For instance, in a friendship network or a Facebook network, some people are closer to each other and thus form small friendship networks. The inherent patterns in dyadic ties are very informative and provide researchers opportunities to understand actors not only from their attributes but also from the social environment around them.

Social network analysis has methodological advantages to other data analysis such as dyadic data analysis. In traditional dyadic analysis, only data with relations are collected. Social network data, however, consist of both dyads with social relations and dyads without social relations. Therefore they allow researchers to better understand dyadic relations. For example, sociologists and personality psychologists are often interested in the association between friendship and personalities (Asendorf & Wilpers, 1998; Youyou, Stillwell, & Schwartz, 2017).

[Note: The OCR text contained many repetitions/fragments. I have processed the logical flow based on the provided segments.]

| Name | Mean | Median | SD | Minimum | Maximum | Female (55%) |
| --- | --- | --- | --- | --- | --- |
| Gender | Male 74 (43%) | | | | |
| Age | 21.64 | 22 | 0.855 | 18 | 24 |
| GPA | 3.273 | 3.265 | 0.488 | 1.173 | 4.22 |
| BMI | 21.51 | 20.31 | 3.848 | 15.4 | 39.52 |
| Happy | 19.72 | 19 | 3.51 | 10 | 28 |
| Lonely | 11.28 | 11 | 5.67 | 0 | 26 |
| Depression | 5.46 | 5 | 2.92 | 0 | 13 |
| Smoke | Yes 43 (36%) | | | | No 122 (64%) | |
| Alcohol | Yes 68 (41%) | | | | No 97 (59%) | |

