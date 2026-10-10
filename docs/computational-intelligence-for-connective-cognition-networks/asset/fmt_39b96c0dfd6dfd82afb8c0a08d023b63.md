
*   \[19\]S. Ruan, B. Chen, K. Song, and H. Li. Weighted naïve Bayes text classification algorithm based on improved distance correlation coefficient. Neural Computing and Applications, vol. 34, nos. 4, pp. 2729–2738, 2022.

*   \[20\]P. Domingos and Michael Pazzani. On the optimality of the simple Bayesian classifier under zero-one loss. Machine Learning, vol. 29, nos. 2-3, pp. 103–130, 1997.

*   \[21\]S.-B. Kim, H.-C. Rim, D.-S. Yook, and H.-S. Lim. Effective methods for improving Naïve Bayes text classification. In 7th Pacific Rim International Conference on Artificial Intelligence, vol. 7, pp. 414–423, 2002.[⏎](#ch17.xhtml#r188b)

*   \[22\]D. Isa, L. H. Lee, V. P. Kallimani, and R. Rajkumar. Text documents preprocessing with the Bayes formula for classification using support vector machine. IEEE Transactions on Knowledge and Data Engineering, vol. 20, no. 9, pp. 1264–1272, 2008.[⏎](#ch17.xhtml#r189b)

*   \[23\]S.-B. Kim, K.-S. Han, H.-C. Rim, and S. H. Myaeng. Some effective techniques for Naive Bayes text classification. IEEE Transactions on Knowledge and Data Engineering, vol. 18, no. 11, pp. 1457–1466, November 2006.[⏎](#ch17.xhtml#r190b)

*   \[24\]P. Domingos and M. J. Pazzani. On the optimality of the simple Bayesian classifier under zero-one loss. Machine Learning, vol. 29, nos. 2-3, pp. 103–130, 1997.[⏎](#ch17.xhtml#r191b)

*   \[25\]T. S. Guzella and W. M. Caminhas. A review of machine learning approaches to spam filtering. Expert Systems with Applications, vol. 36, no. 7, pp. 10206–10222, 2009.[⏎](#ch17.xhtml#r192b)

*   \[26\]J. Schmidhuber and S. Hochreiter. *Long short-term memory*. Neural Computation, vol. 9, no. 8, pp. 1735–1780, 1997.[⏎](#ch17.xhtml#r193b)

*   \[27\]Z. Huang, W. Xu, and K. Yu. Bidirectional LSTM-CRF Models for Sequence Tagging. *arXiv preprint arXiv:1508.01991*, 2015.[⏎](#ch17.xhtml#r194b)

*   \[28\]M. Schuster and K. K. Paliwal. Bidirectional recurrent neural networks. IEEE Transactions on Signal Processing, vol. 45, no. 11, pp. 2673–2681, 1997.[⏎](#ch17.xhtml#r195b)

*   \[29\]A. Graves and J. Schmidhuber. Framewise phoneme classification with bidirectional LSTM and other neural network architectures. Neural Networks, vol. 18, no. 5, pp. 602–610, 2005.[⏎](#ch17.xhtml#r196b)

*   \[30\]R. Ghaeini, S. A. Hasan, V. V. Datla, J. Liu, K. Lee, A. Qadir, Y. Ling, A. Prakash, X. Z. Fern, and O. Farri. DR-BiLSTM: Dependent Reading Bidirectional LSTM for Natural Language Inference. In Proceedings of the 2018 Conference of the North American Chapter of the Association for Computational Linguistics: Human Language Technologies, Vol 1 (Long Papers), pp. 1460–1469, 2018.[⏎](#ch17.xhtml#r197b)

*   \[31\]S. Hochreiter and J. Schmidhuber. Long short-term memory. Neural Computation, vol. 9, no. 8, pp. 1735–1780, 1997.[⏎](#ch17.xhtml#r198b)

*   \[32\]E. Kiperwasser and Y. Goldberg. Simple and Accurate Dependency Parsing Using Bidirectional LSTM Feature Representations. *Transactions of the Association for Computational Linguistics*, vol. 4, pp. 313–327, 2016.[⏎](#ch17.xhtml#r199b)

*   \[33\]A.Rao and N. Spasojevic. Actionable and Political Text Classification Using Word Embeddings and LSTM. Technical report, Lithium Technologies, July 2016.[⏎](#ch17.xhtml#r200b)

*   \[34\]K. S. Tai, R. Socher, and C. D. Manning. Improved Semantic Representations from Tree-Structured Long Short-Term Memory Networks.In Proceedings of the 53rd Annual Meeting of the Association for Computational Linguistics and the 7th International Joint Conference on Natural Language Processing, vol. 1, pp. 1556–1566, 2015.[⏎](#ch17.xhtml#r201b)

*   \[35\]N. Correia da Silva et al. Document Type Classification for Brazil’s Supreme Court Using a Convolutional Neural Network. In 10th International conference on forensic computer science and cyber law (ICoFCS), Sao Paulo, Brazil, pp. 29–30, 2018.[⏎](#ch17.xhtml#r202b)

*   \[36\]P. H. Luz de Araujo, T. E. de Campos, R. R. R. de Oliveira, M. Stauffer, S. Couto, and P. Bermejo. *Lener-br: A Dataset for Named Entity Recognition in Brazilian Legal Text*. In Proceedings of the International Conference on the Computational Processing of Portuguese (PROPOR), Canela, RS, Brazil, vol. 13, pp. 313–323, September 24–26, 2023.[⏎](#ch17.xhtml#r203b)

# Chapter 8 FNDetector: Fake news detection using combinations of various features

Yun Hwa Wong (Jenny), Amanpreet Kaur, and Sangeeta Lal

DOI: [10.1201/9781003569619-8](http://doi.org/10.1201/9781003569619-8)

## 8.1 Introduction

In the explosion era of technology and the modern world, fake news is permeating our daily lives at an alarming rate. The Cambridge dictionary has defined “fake news” as “false stories that appear to be news, spread on the internet or using other media, usually created to influence political views or as a joke” \[[1](#ch18.xhtml#r204)\]. According to the world’s leading public service broadcaster, British Broadcasting Corporation (BBC), the history of fake news started 2000 years ago during a civil war in the Roman Republic. Octavian wanted to win the war, and he disseminated the “fake news” against Mark Anthony by printing the slogan on the coins and distributing it to the public. In the 19th century, after the technique of print pressed was invented. One of the newspapers in 1835, articles were published about fantastic creatures such as flying batmen and unicorns living on the moon \[[2](#ch18.xhtml#r205)\].

Before the concept of online social media came, most of the people get news via reading newspapers or listening to the broadcast channel on the radio. With the characteristic of connecting people and sharing content easily, the rate of disseminating news has increased drastically via online social media.

A study conducted by \[[3](#ch18.xhtml#r206)\] on the Twitter dataset from the year 2006 to 2017 shows that between 1000 and 100000 people were affected by the top 1% of fake news while the truth was seldom spread to more than 1000 people. The study has shown how fast fake news can be disseminated on online social media.

Fake news is prevalent in many domains, especially in the domain of politics. During 2016 US presidential nomination process, the fake news about Donald Trump was greatly favored and has been shared extensively on social media. On Facebook, there were 115 fake news stories supporting Trump and 41 supporting Clinton \[[4](#ch18.xhtml#r207)\]. The possible impact of fake news disseminated on public forum has drawn up particular attention from different researchers and the public. Fake news, however, is not just about political issues. In recent years, fake news can be disseminated widely when a disaster or pandemic happens. The best example is the SARS-CoV-2 (COVID-19) virus breakout that happened in the year 2019. There are tons of fake news or false information related to information on how to get recover from the disease such as eating hot pepper can help to prevent or cure COVID-19, and drinking alcohol can protect the public against COVID-19 \[[5](#ch18.xhtml#r208)\]. For example, fake news written as a Facebook post by a user regarding steaming can kill the Coronavirus and has been shared more than 33,000 times on Facebook \[[6](#ch18.xhtml#r209)\]. Researchers have put great deal of time and effort to develop different algorithms and models to detect fake news. A study of categorizing different approaches used by various researchers has been done by de Beer and Matthee \[[7](#ch18.xhtml#r210)\]. According to de Beer and Matthee \[[7](#ch18.xhtml#r210)\], the approaches used by existing researchers can be categorized into five main categories (refer to [Table 8.1](#ch18.xhtml#t13)). An example of each of the approaches can be found in [Table 8.1](#ch18.xhtml#t13).

**Table 8.1** Example or descriptions of each approach to identify fake news[⏎](#ch18.xhtml#t13b)

| **Approaches** | **Examples/Descriptions** |
| --- | --- |
