# Chapter 13

# # Private entity resolution for big data on Apache Spark using multiple phonetic codes

Alexandros Karasakasidis¹ and Georgia Koloniari¹

# ## 13.1 Introduction

Recommender systems are nowadays experiencing a significant boost due to the availability of big data which supply an abundance of user data such as past purchases and browsing history. The benefits are increased when a recommender system can use and combine data that come from multiple sites and illustrate a more complete picture of the user's preferences and interests. However, such data often originate from dispersed, heterogeneous sources, and before processing and analyzing them, it is required to integrate or link them. The problem of linking data consists of identifying data that refer to the same real-world entity across the heterogeneous sources and is known as *record linkage or entity resolution*. As these data also concern human activities, privacy issues arise when linking data across different sources. The problem is known as *privacy preserving record linkage* (PPRL).

In PPRL, two or more dataholders attempt to identify common entities within their records, without revealing to each other any additional information. As the data are from heterogeneous sources, they may adhere to different schemas. No common identifiers can be found, and so, the record-linking methods rely on attributes that describe these records and to all data sources, such as names, surnames and addresses when identifying the same individual. Thus, to determine whether two records match, all their respective fields must be compared. The complexity of matching methods is high, as records belonging to the two dataholders be compared against each other so to determine the matching records. To this end, blocking methods have been introduced [1] to reduce matching complexity by pruning out unlikely to match pairs of records. In addition, data is usually dirty, containing spelling and typographical errors, thus complicating the linkage process further. Exact matching cannot be performed and more expensive approximate matching methods are required.

Different approaches have been applied for approximate matching in the context of record linkage. Most methods rely on hashing, combinations of bigrams and