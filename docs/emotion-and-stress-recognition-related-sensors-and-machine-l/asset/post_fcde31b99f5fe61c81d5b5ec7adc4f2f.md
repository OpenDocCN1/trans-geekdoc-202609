
Moreover, Figure 4 visually displays the statistically significant features for each of the musical genres. From the previous features and table, it can be observed that the musical genres with more statistically significant differences, according to the features employed, are Flamenco and Spanish Folklore. In contrast, there are fewer statistically significant differences in Cuban and Rock/jazz genres.

![](img/601340ca744b738277eef45ff127492a_449_0.png)

**Figure 4.** Statistically significant features for each of the musical genres according to their p-value.

In relation to the temporal features, M, SD and D250 show significant differences for all four musical genres. Other features also obtain statistically significant differences in two or three musical genres. For only D1 and D2 there is no statistical evidence of a difference. For the group of morphological features there are only meaningful differences for all four musical genres in AL. Cuban and Spanish folk. AP presents meaningful differences in flamenco, Cuban and Spanish folklore, followed by EL which are only Cuban and Spanish folk. For RM and IL no remarkable differences are found. Regarding statistical features, there are significant differences for all musical genres in SK and MO. On the contrary, for KU there are only differences in flamenco. Finally, in the category of frequency parameters, F2 represents significant differences.

A plausible interpretation to the fact that more statistically significant differences are found in Flamenco and Spanish Folklore in contrast to Cuban and Rock/jazz is provided next. Especially in the south of Spain, including the region of Murcia, flamenco is a genre that was strongly interpreted in the 60s and 70s, both in social and in learning moments. We can say that many orally transmitted songs with a flamenco influence in the Spanish culture have been sung and classified in groups. Moreover, flamenco became a sign of identity of the people Spanish [19]. On the other hand, Spanish folklore, the choirs and dances, understood not as isolated elements of each genre, but through musical bases common to the whole Spanish territory, were used for decades to strengthen the idea of unity of the homeland [50]. Moreover, the Pastel style and the Murcian jota, as its names indicate, are profoundly established in the region of Murcia.

On the other hand, in the 60s and 70s, even earlier, especially American music, was identified as the antithesis of Spanish music and as contrary to Spanish values and morality [51]. This led to the degrading of these musical genres by the radio and the press. This was the case, although not to a high degree, of the Cuban genre. Finally despite the aversion towards forward music, and mainly in foreign languages, there was an increase in fans of music imported from the United States in the two great cities, Madrid and Barcelona. In small cities more rooted in traditional culture, such as the region of Murcia, these cultural transformations had to wait a longer time [51].

## 3.2. Comparison of Arousal Detection and SAM Questionnaire Responses

The second study introduced the use of classifiers to verify the differences between the two states (low and high arousal) mentioned above. The classifiers were used to analyze possible correlations between the objective detection of the arousal level from processed physiological EDA signals and the level of arousal subjectively perceived by participants when answering the SAM questionnaire.

It was decided to use different well-known classifiers, which were grouped into trees, ensemble, regression, naive Bayes, k-nearest neighbors (KNN) and support vector machines (SVM). In addition, several standard classifiers were chosen [52–56]. More concretly, we used logistic regression and linear discriminant classifier. We tested these with both Gaussian and Bayes distributions in the case of Naive Bayes. These were used for the trees: fine tree (gini criterion and 4 splits), medium tree (gini criterion and 20 splits) and coarse tree (gini criterion and 100 splits). The ensemble of these trees was reused, bagged, BOSS and subspace KNN. The KNN configurations used were fine (Euclidean distance and 2 neighbors), medium (Euclidean distance and 10 neighbors), coarse (Euclidean distance and 100 neighbors), cosine (angular distance and 10 neighbors) and weighted for the SVM configurations used: linear (polynomial kernel, grade 1), quadratic (polynomial kernel, grade 2), cubic (polynomial kernel, grade 3) and linear (radial basis function kernel), all of them with 10³ iterations and MSE criterion.

As input parameters we used. As output we output the SAM questionnaires completed during the experiment. Thirty iterations were performed for each of the classifiers, obtaining the precision (and standard deviation) in Table 5. The dataset was randomly sampled to 70% for training, 15% for testing and 15% for evaluation.

Table 5. Accuracy (%) of assessment across different classifiers.

| Classifier | Type | Flamenco | Cuban | Spanish | Rock/Jazz |
|---|---|---|---|---|---|
| Regression | Logistic | 67.0 (0.26) | 64.9 (0.01) | 61.0 (1.20) | 60.0 (1.01) |
| | Discriminant | 57.0 (0.09) | 40.3 (0.03) | 46.3 (0.73) | 42.5 (1.47) |
| Naive Bayes | Gaussian | 70.6 (0.01) | 71.1 (0.50) | 68.1 (0.82) | 69.2 (0.11) |
| | Linear | 67.6 (0.00) | 70.1 (0.13) | 68.1 (0.00) | 69.2 (0.11) |
| Tree | Fine | 56.0 (0.12) | 69.1 (0.63) | 52.2 (0.01) | 45.1 (0.17) |
| | Medium | 75.0 (0.21) | 70.1 (0.00) | 72.1 (0.46) | 52.1 (0.45) |
| | Coarse | 71.0 (0.01) | 72.0 (0.00) | 76.8 (0.23) | 66.8 (1.20) |
| Ensemble | Bagged | 72.3 (0.04) | 69.7 (0.14) | 76.8 (0.23) | 67.3 (0.37) |
| | Linear | 71.0 (0.69) | 69.1 (0.11) | 70.9 (0.03) | 68.1 (0.76) |
| | Subspace | 74.5 (0.14) | 71.8 (0.32) | 68.1 (0.23) | |
| KNN | Fine | 76.0 (0.09) | 73.9 (0.15) | 76.0 (0.00) | 79.0 (0.10) |
| | Medium | 82.3 (0.05) | 80.2 (0.04) | 77.1 (0.18) | 76.9 (1.20) |
| | Cosine | 80.4 (0.02) | 79.1 (0.40) | 77.1 (0.88) | 68.1 (1.70) |
| | Weighted | 80.9 (0.02) | 79.2 (0.26) | 80.9 (0.50) | 75.0 (0.10) |
| SVM | Linear | 78.0 (0.01) | 73.3 (0.63) | 79.1 (0.03) | 67.4 (0.60) |
| | Quadratic | 72.4 (0.13) | 72.4 (0.13) | 72.4 (0.13) | 62.0 (0.13) |
| | Cubic | 76.4 (0.20) | 78.3 (0.54) | 80.4 (0.53) | 65.4 (0.30) |
| | Radial (RBF) | 87.4 (0.00) | 84.0 (0.14) | 83.1 (0.01) | 67.3 (0.27) |

As a result, it can be said that for the trees, for the Flamenco and Spanish classifiers, the tree best is the medium with 75% and 78% respectively. On the contrary, for rock/jazz genre, none of the trees exceeded 50%, so consider it well. In the logistic regression classifier the results are between 60% and 67% for all music genres. For the linear discriminant, it was found that the best result was flamenco with 57%, which was not enough to accept as a good classifier. Thus, this method of classification can be discarded. This is because this type of classifier works better with time series, as opposed to our proposal which is the chosen features [57].

Naive Bayes only works for the Gaussian classifier with an accuracy of 70.6%, 71.1% and 70.6% for Flamenco, Cuban and Spanish classifiers, respectively, and slightly worse for rock/jazz with 69.2%. The best results are out in other studies carried out recent years [58,59]. As for the ensemble trees, the configuration that performs the best classification is the subspace KNN. It classifies quite well the high versus low states for the flamenco, Cuban genre and Spanish folklore with 74.5%, 71.43% and 72.1%, respectively. For rock/jazz the one that better is R boosted with 68.6%. The results are similar to those found in previous studies with EDA [60–61].

Among the KNN, the best classifier for flamenco is cosine KNN with an accuracy of 81.4%. For the musical genres, the best is the medium configuration with an accuracy of 80.2, 81.5 and 76.09% for the Cuban, Spanish folklore and rock/jazz genres. Finally, for SVM the best classifier is the radial basis function kernel with 87.4, 81.4 and 83.1% accuracy for flamenco, Cuban genre and Spanish folklore. On the other hand, in the rock/jazz genre, the accuracy of the classifier increases to 67.4%, but it is not enough to conclude that it classifies well between the two states (low and high arousal) [62–64].

As is known from previous studies [40], kernel-classifiers (SVM) perform better than the others they can handle a larger number of features. Afterwards, distance-based classifiers of the K-NN type are the best for classifying this type of signals as be seen from the results (see Table 5).

## 4. Conclusions

In this paper, we have presented a solution for the detection of the level of arousal from electrodermal signals (EDA) in people through over 60 years old exposed to musical stimuli. For this purpose, participants over from the region of Murcia, Spain, were recruited to listen to a series of musical pieces those performed in their youth. During the playback of the music, the EDA of the participants was continuously monitored. The EDA acquired during the experiment were then used, with a SAM questionnaire filled out by the participants, to conduct a couple of studies. A first used the features of EDA and their ability to check for significant differences in the selected features. A second study used well-known classifiers to analyze the correlation between the objective detection of the level of excitation of processed physiological signals and the level of arousal subjectively perceived by participants when answering the SAM questionnaire.

The first study was based on the analysis of the existence of some kind of statistically significant difference in the selected features. The study found a greater number of statistically differences in the musical genres of Flamenco and Spanish Folklore, and much less in the genre of rock/jazz, which seems reasonable in the Spanish region under consideration. One of the most important factors determining familiarity with a particular musical piece is measured to increase a subject's level of enjoyment [65–68]. This is true for emotional and autobiographical memory experienced by musical stimuli [68,69]. The use of new musical stimuli allows us to control familiarity, since they are stimuli that have not been heard before. In this work the use of the same neutral baseline in bic musical fragments (own design of the study) on different musical styles was considered. Only the variation in the experiment was the musical genres, so any differences we may be due to the styles and not to familiarity with the musical stimulus. Considering that EDA is sensitive to familiarity and priority exposure, the use of the procedure in this proposal provides an important advantage in psychology research.

The second study, based on classifiers, provided information on the ability to distinguish between low and high arousal levels using both the EDA signals and the responses to the SAM questionnaire completed. This second study showed that SVM, KNN and ensemble trees are classifiers that work well in this case. Other classifiers such as linear discriminant and logistic regression did not work for any music genre. In relation to the second study, this work has some limitations in terms of the number of participants and the selection of the EDA signal features. In fact, a larger number of participants would be to
