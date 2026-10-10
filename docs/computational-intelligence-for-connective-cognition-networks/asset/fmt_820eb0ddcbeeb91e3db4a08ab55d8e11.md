
### Table 8.21 Total training and prediction time of FNDetector[RF] and FNDetector[LSTM] with different parameters

| Batch Size | | |
| :--- | :--- | :--- |
| | | 128 |
| | | 256 |

| Method | Parameter | Value | Training Time (secs) | Prediction Time (secs) |
| :--- | :--- | :--- | :--- | :--- |
| FNDetector[RF] | n estimators | 50 | 0.30 | 0.03 |
| | | 100 | 0.33 | 0.04 |
| | | 150 | 0.40 | 0.04 |
| FNDetector[LSTM] | epoch/batch size | 5/128 | 25.0 | 2.39 |
| | | 5/256 | 16.0 | 2.24 |
| | | 10/128 | 53.0 | 2.24 |
| | | 10/256 | 31.0 | 2.53 |

Table 8.21 shows that for the `FNDetector[RF]` classifier, the training and prediction time increases as we increase the number of estimators. As we are increasing the number of estimators, the `RF` algorithm needs to create more trees and hence, the time increases. For the `FNDetector[LSTM]` classifier, we observe a similar pattern, i.e., training time increases as we intensify the number of epochs. As we increase batch size, the training time decreases for the `FNDetector[LSTM]` classifier. This happened because with increases in batch size, the algorithm can take big chunks of the training dataset and can learn faster. Overall, we observe that the `FNDetector[RF]` classifier took much less time in both training and testing as compared to the `FNDetector[LSTM]` classifier. Experimental results show that parameter tuning is very important as it can have a big influence on the `FNDetector` model’s effectiveness. In our experiment, the `RF` classifier achieved its best performance when the `n estimator` was set to 150, and the `LSTM` classifier achieved its best performance when the `epochs` value is 10 and the `batch size` value is 128. `FNDetector[RF]` took much less training and testing time as compared to the `FNDetector[LSTM]` classifier.

## 8.9 Concluding remarks and future scope

The amount of news items shared on social networking websites has skyrocketed. Because so much false information circulates on social media, people are less likely to believe news articles published on these channels. It is challenging to confirm the veracity of news articles on social media. The identification of fake news has become more significant as a way to get around this problem and as a motivator for related research. We provide `FNDetector`, a fake news detection model, in this paper. `FNDetector` uses a combination of various feature sets. We train the `FNDetector` using two classifiers, i.e., `RF` and `LSTM`. The `FNDetector` model outperformed the baseline classifier significantly. `FNDetector[RF]` and `FNDetector[LSTM]` give an accuracy of 88.2% and 78.4%, respectively. Our investigation related to feature importance shows that all the feature sets used in this paper are important and help in increasing the accuracy. Also, 'noun count' and 'total word count' in both the title and content of news articles are found to be the top four important features. We intend to use ensemble learning to expand the model in the future. The ensemble learning model combines different classifiers to improve training models. The ensemble learning model working has been shown in a few studies such as [69](#ch18.xhtml#r272) and [45](#ch18.xhtml#r248) to improve the outcomes of the models. Additionally, we plan to use more advanced methods such as `BERT` to enhance the effectiveness of fake news detection.

## References

*   [1] Cambridge dictionary. (n.d). Cambridge dictionary. <https://dictionary.cambridge.org/dictionary/english/fake-news>
*   [2] BBC. (2022). A brief history of fake news. <http://www.bbc.co.uk/bitesize/articles/zwcgn9q>. [Accessed Date: 22 June 2022].
*   [3] Vosoughi, S., Roy, D., & Aral, S. (2018). The spread of true and false news online. *Science*, 359, 1146–1151. doi: <http://dx.doi.org/10.1126/science.aap955>
*   [4] Allcott, H., & Gentzkow, M. (2017). Social media and fake news in the 2016 election. *Journal of Economic Perspectives*, 31, 212. doi: <http://dx.doi.org/10.1257/jep.31.2.211>
*   [5] WHO (2022). Covid-19 mythbusters. <http://www.who.int/emergencies/diseases/novel-coronavirus-2019/advice-for-public/myth-busters#pepper> [Accessed Date: 22 June 2022].
*   [6] BBC (2020). Coronavirus: Fake and misleading stories that went viral this week. <http://www.bbc.co.uk/news/52124740>. [Accessed Date: 28 July 2022].
*   [7] de Beer, D., & Matthee, M. (2020). Approaches to identify fake news: A systematic literature review. *Integrated Science in Digital Age 2020*, (p. 13–22). doi: <http://dx.doi.org/10.1007/978-3-030-49264-9_2>
*   [8] Wang, W. Y. (2017). "liar, liar pants on fire": A new benchmark dataset for fake news detection. *arXiv preprint arXiv:1705.00648*.
*   [9] Choudhary, A., & Arora, A. (2021). Linguistic feature-based learning model for fake news detection and classification. *Expert Systems with Applications*, 169, 1–15. doi: <http://dx.doi.org/10.1016/j.eswa.2020.114171>
*   [10] Lischka, J. A., & Garz, M. (2021). Clickbait news and algorithmic curation: A game theory framework of the relation between journalism, users, and platforms. *New Media and Society*, (p. 3). <https://journals.sagepub.com/doi/full/10.1177/14614448211027174>. doi: <http://dx.doi.org/10.1177/14614448211027174>
*   [11] Hu, X. E. (2017). Clickbait and conscientiousness. <https://stanforddaily.com/2017/03/20/clickbait-and-conscientiousness/> [Accessed Date: 23 June 2022].
*   [12] Barrón-Cedeno, A., Da San Martino, G., Jaradat, I., & Nakov, P. (2019). Proppy: A system to unmask propaganda in online news. In *Proceedings of the AAAI Conference on Artificial Intelligence* (pp. 9847–9848). volume 33.
*   [13] Lewis, H. (2016). How the Brexit campaign lied to us–and got away with it. *New Statesman*, 30. <http://www.newstatesman.com/politics/2016/06/how-brexit-campaign-lied-us-and-got-away-it> [Accessed Date: 27 June 2022].
*   [14] The Independent (2018). The misinformation that was told about brexit during and after the referendum. <http://www.independent.co.uk/news/uk/politics/final-say-brexit-referendum-lies-boris-johnson-leave-campaign-remain-a8466751>. [Accessed Date: 23 June 2022].
*   [15] Shu, K., Sliva, A., Wang, S., Tang, J., & Liu, H. (2017). Fake news detection on social media. *ACM SIGKDD Explorations Newsletter*, 19, 22–36. doi: <http://dx.doi.org/10.1145/3137597.3137600>.
*   [16] BuzzFeedNews Dataset. <https://github.com/BuzzFeedNews/2016-10-facebook-fact-check/tree/master/data>
*   [17] BuzzFeedNews Dataset. <http://www.cs.ucsb.edu/~william/data/liar_dataset.zip>
*   [18] BS Detector Dataset. <http://www.kaggle.com/mrisdal/fake-news>
*   [19] CREDBANK Dataset. <http://compsocial.github.io/CREDBANK-data/>
