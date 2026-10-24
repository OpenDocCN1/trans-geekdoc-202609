# ### 17.1.3 CHAPTER ORGANIZATION

The rest of the chapter is organized as follows. Section 2.2 discusses the related existing studies on cybersecurity analytics using data science methodologies. Section 2.3 describes the conceptual framework designed for the chapter, while section 2.4 discusses the experimental result. Section 2.5 concludes with recommendations.

# ## 17.2 RELATED WORK

Feature selection techniques, including information gain (IG), gain ratio, chi-square, and correlation-based approaches, were employed by Adi et al. (2019) on the UCI phishing dataset.

When applied to the chosen feature subset, the classification algorithms NB, *k*-nearest neighbor (KNN), support vector machine, decision tree (DT), and iterative dichotomiser 3 algorithm show a decline in accuracy when compared to the full set of 30 features.

On the Mendeley dataset, Almseidin et al. (2022) used feature selection techniques, such as IG and ReliefF, along with classification algorithms, including J48, RF, and multilayer perceptron (MLP).

Le et al. (2010) suggested a technique for identifying phishing websites by collecting lexical information from URL strings and applying adaptive regularization of weights. This approach ensures higher detection accuracy while overcoming noise in the training data.

The URL size, number of dots, number of hyphens, number of numeric characters, a discrete variable that corresponds to the presence of an IP address in the URL, and similarity index were the only six URL features used by Zouina and Outtaj (2017) in their proposed lightweight phishing website detection method. Owing to their few features and quick identification, the features collected are entirely reliant on the URLs.

However, inadequate experimental data are available. Xiang et al. (2011) proposed a CANTINA+ phishing website detection system based on CANTINA.

Before extracting 15 highly distinct features from the URL vocabulary, HTML DOM, WHOIS data, and search engine information, the method first filtered out highly similar phishing websites and webpages without log-in forms.

Finally, phishing website prediction was implemented using a machine learning algorithm. A strategy for detecting phishing websites that is scalable and independent of language was proposed by Marchal et al. (2016).

In their study, 212 characteristics were chosen for the URL and HTML, and gradient boosting was applied to identify fraudulent websites with high accuracy. Based on the combined attributes, phishing detection performs better because it accurately depicts a website.

Qurashi et al. (2021b) proposed a method that creates adversarial phishing assaults by identifying the best subsets of attributes that increase the rate of evasion. Recursive feature elimination, least absolute shrinkage and selection operator, and cancel out were utilized as feature engineering techniques to create and evaluate attack vectors that have a higher potential to elude phishing detection.