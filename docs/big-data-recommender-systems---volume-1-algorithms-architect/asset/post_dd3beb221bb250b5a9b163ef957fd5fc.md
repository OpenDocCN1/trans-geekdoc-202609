
[content]
# User's privacy in recommendation systems 281

[58] Fung B, Wang K, Yu PS. Anonymizing classification data for privacy preservation. IEEE Transactions on Knowledge and Data Engineering. 2007;19(5):711–725.

[59] LeFevre K, DeWitt DJ, Ramakrishnan R. Incognito: Efficient full-domain k-anonymity. In: Proceedings of the 2005 ACM SIGMOD International Conference on Management of Data. ACM, 2005. p. 49–60.

[60] LeFevre K, DeWitt DJ, Ramakrishnan R. Multidimensional k-anonymity. In: Data Engineering, 2006. IDE’06. Proceedings of the 22nd International Conference on. IEEE, 2006; p. 25–25.

[61] Machanavajila A, Kefer D, Gehre J, et al. l-Diversity: Privacy beyond k-anonymity. ACM Transactions on Knowledge Discovery from Data (TKDD). 2007;1(1):3.

[62] Samarati P, Sweeney L. Protecting privacy when disclosing information: k-anonymity and its enforcement through generalization and suppression. Technical Report, SRI International, 1998.

[63] Sweeney L. k-Anonymity: A model for protecting privacy. International Journal of Uncertainty, Fairness and Knowledge-Based Systems. 2002;10(05):557–570.

[64] Li N, Li T, Venkatubramanian S. Closeness: A new measure for data publishing. IEEE Transactions on Knowledge and Data Engineering. 2010;22(7):943–956.

[65] Xiao X, Tao Y.-M. Inwards privacy re-publishing of dynamic datasets. In: Proceedings of the 2007.ACM SIGMOD International Conference on Management of Data. ACM; 2007. p. 689–700.

[66] Wang K, Fung BCM, Philip SY. Handicapping attackers’ confidence: An alternative to k-anonymity. Knowledge and Information Systems. 2007;11(3):345–368.

[67] Xiao X, Tao Y. Anatomy: Simple and effective privacy preservation. In: Proceedings of the 32nd International Conference on Very Large Databases. VLDB Endowment; 2006. p. 139–150.

[68] Li N, Li T, Zhang J, et al. Slicing: A new approach for preserving data publishing. IEEE Transactions on Knowledge and Data Engineering. 2012;24(3):561–574.

[69] Terrovitis M, Mammway N, Liagouris J, et al. Privacy preservation by dissociation. Proceedings of the VLDB Endowment. 2012;5(10):944–995.

[70] Li N, Li T, Venkatasubramanian S. t-Closeness: Privacy beyond k-anonymity and l-diversity. In: Data Engineering, 2007. IDE 2007. IEEE 23rd International Conference on. IEEE; 2007; p. 106–115.

[71] Dwork C. An admin approach to protecting and deactivating private data analysis. In: Privacy, Security, and Trust in KDD. Berlin, Heidelberg: Springer; 2008. p. 1–13.

[72] Samarati P. Protecting residents identities in microdata release. IEEE Transactions on Knowledge and Data Engineering. 2001;13(6):1010–1027.

[73] Wang K, Yu PS, Chakraborty S. Bottom-up generalization: A data mining solution to privacy protection. In: Data Mining, 2004. ICDM’04. Fourth International Conference on. IEEE; 2004. p. 249–256.

# Big data recommender systems, volume 1

[74] Fung BCM, Wang K, Yu PS. Top-down specialization for information and privacy preservation. In: 21st International Conference on Data Engineering (ICDE). IEEE; 2005. p. 205–216.

[75] Wang RCW, Li J, Fu ACW, et al. α-Anonymity: An enhanced k-anonymity model for privacy publishing. In: Proceedings of the 12th ACM SIGKDD International Conference on Knowledge Discovery and Data Mining. ACM; 2006. p. 754–759.

[76] Sun X, Wang H, Li J, et al. Enhanced k-anonymity models for privacy publishing. Transactions on Privacy. 2008;2(2):53–66.

[77] Sun X, Li M, Wang H. A family of enhanced α-diversity models for privacy publishing. Future Generation Computer Systems. 2011;27(3):348–356.

[78] Dwork C, Rothblum GN. Differential privacy. arXiv preprint arXiv:1603.0188,2016.

[79] Badsha S, Yi X, Khalil I. A practical privacy-preserving recommender system. Data Science and Engineering. 2016;1(3):161–177.

[80] Nikolaenko J, Joannidis S, Weissberg U, et al. Privacy-preserving matrix factorization. In: Proceedings of the 2013 ACM SIGSAC Conference on Computer & Communications Security. ACM; 2013. p. 801–812.

[81] Shokri R, Pedarsani P, Theodoropoulos G, et al. Preserving privacy in collaborative filtering through distributed aggregation of profiles. In: Proceedings of the third ACM Conference on Recommender Systems. ACM; 2009. p. 157–164.

[82] Machanavajila A, Korolova A, Sarma AD. Personalized social recommendations: Accurate or private. Proceedings of VLDB Endowment. 2011;4(7):440–450.

[83] Hofmann T, Hartmann D. Collaborative filtering with privacy via analysis. In: Proceedings of 2005 ACM Symposium on Applied Computing. 2005. p. 791–795.

[84] Li D, Chen C, Lv Q, R, et al. An algorithm for efficient privacy-preserving item-based collaborative filtering. Future Generation Computer Systems. 2016;5:311–320.

[85] Boutet A, Domingo-Ferero J, Guerraoui R, Patsakis C, et al. A k-anonymous approach to privacy preserving collaborative filtering. Journal of Computer and System Sciences. 2015;81(6):1000–1011.

[86] Jorgensen Z, Yu T. A privacy-preserving framework for personalized social recommendations. In: EDBT 2014. p. 571–582.

[87] Shang S, Hui Y, Hui P, et al. Beyond personalization and anonymity: Towards a group-based recommender system. In: Proceedings of 29th Annual ACM Symposium on Applied Computing. ACM; 2014. p. 266–273.

# Chapter 13
# Private entity resolution for big data on Apache Spark using multiple phonetic codes
Alexandros Karakasidis and Georgia Koloniari

## 13.1 Introduction

Recommender systems are nowadays experiencing a significant boost due to the availability of big data which supply an abundance of user data such as past purchases and browsing history. The benefits are increased when a recommender system can use and combine data that come from multiple sites and illustrate a more complete picture of the user's preferences and interests. However, such data often originate from dispersed, heterogeneous sources, and before processing and analyzing them, it is required to integrate or link them. The problem of linking data consists of identifying data that refer to the same real-world entity across the heterogeneous sources and is known as *record linkage or entity resolution*. As these data also concern human activities, privacy issues arise when linking data across different sources. The problem is known as *privacy preserving record linkage* (PPRL).

In PPRL, two or more dataholders attempt to identify common entities within their records, without revealing to each other any additional information. As the data are from heterogeneous sources, they may adhere to different schemas. No common identifiers can be found, and so, the record-linking methods rely on attributes that describe these records and all sources, such as names, surnames and addresses when identifying the same individual. Thus, to determine whether two records match, all their respective fields must be compared. The complexity of matching methods is high, as records belonging to the two dataholders be compared against each other to determine the matching records. To this end, blocking methods have been introduced [1] to reduce matching complexity by pruning out unlikely to match pairs of records. In addition, data is usually dirty, containing spelling and typographical errors, thus complicating the linkage process further. Exact matching cannot be performed and more expensive approximate matching methods are required.

Different approaches have been applied for approximate matching in the context of record linkage. Most methods rely on hashing, combinations of bigrams and n-grams as well as similarity or appropriate distance measures. A popular approach is based on use of phonetic codes. A phonetic code is a hash of a string, based on its pronunciation. Phonetic codes are being used for almost a century [2] for duplicate detection and record linkage, due to their inherent information suppression properties, which make them tolerant to spelling errors. Use of phonetic codes reduces the problem of approximate matching of dirty data to a problem of exact matching of phonetic codes, leading to faster processing and rendering the use of distance measures redundant. However, this often comes with a cost in quality with regards to precision or recall.

In this chapter, we propose a parallel protocol for PPR based on phonetic encodings that exploit novel big data processing engines to provide results of high quality in an efficient manner. Our work previously presented in [3] that is based on the use of the Soundex phonetic algorithm [2]. This protocol also features noise generation to prevent frequency attacks and encryption of actual and fake data to enable processing by an untrusted party. However, to cope with the low recall that the existence of a big percentage of dirty data may incur, we propose using Soundex with another phonetic algorithm, and particularly ISIS. By combining two encodings, our protocol becomes more robust and more tolerant to errors in the matching fields, as it introduces redundancy. Furthermore, as Soundex is particularly vulnerable to whatever occurs in the beginning of the encoded text, our protocol deploys another optimization by encoding the reverse of the original text with the second phonetic algorithm.

The rest of the chapter is organized as follows. Section 13.2 summarizes work. In Section 13.3, we formulate the problem and briefly present the basic components of our approach. Section 13.4 details the proposed technique, while Section 13.5 contains our empirical evaluation. Finally, Section 13.6 sums up with conclusions and some thoughts for future work.

## 13.2 Related work

The problem of record linkage has attracted much attention due to the importance and variety of its applications. Useful reviews of the most representative traditional
