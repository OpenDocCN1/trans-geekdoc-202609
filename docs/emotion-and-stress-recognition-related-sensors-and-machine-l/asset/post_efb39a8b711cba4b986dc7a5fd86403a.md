
Analyzing the RMSE (left barplot), it is possible to see that the improvements were important over all emotions when feature extraction was used. The emotion happy presented an improvement of 89.66% (prior 3.06/actual 0.31); sad of 84.58% (5.38/0.02); angry of 86.75% (3.84/0.50); surprised of 93.89% (2.19/0.13); and scared of 88.67% (3.18/0.36).

Analyzing the MAE values (right barplot), it is possible to see that the improvements were good over 4 of 5 matches (emotion sad wasn't improved on MAE values), when feature extraction was used. The emotion happy presented an improvement of 26.04% (prior 0.06/actual 0.04); angry of 4.32% (0.065/0.062); surprised of 60.15% (0.04/0.01); and scared of 18.75% (0.05/0.04).

## 5.6. Considering the Intensities Between Emotions

The higher intensities by time (between five emotion intensities) were also computed and its amount of matches were also analyzed, comparing the correct matches between his higher emotion (from the face dataset) with the higher output from the five neurons (output layer).

The benefit to also consider higher values by time is to understand if the regression models from each output result in following emotion intensities related to the others. In other words, if a regression model from each neuron fits to a target, both error levels (RMSE+MAE) and major/minor values will improve.

The corrected amount of matches between these emotions and its relations is in Figure 12, presenting the case of tests 3-6.

![](img/601340ca744b738277eef45ff127492a_107_0.png)

Figure 12. Major emotion accuracies from the tests 3 to 6 (with feature extraction).

Some datasets presented a very low amount of matches during all tests as for instance, GC1, LS1, VCI, CLX and CL3. These low accuracies are probable due the the high misclassification of emotions from the pilots' faces as also presented on prior errors value based on RMSE and MAE. However, if we consider the possibility to improve these results, the next tests can use these datasets with low accuracies to get better general results.

When comparing all matches (from test 3–34) regarding the major emotion values, it is possible to see that the accuracy of the dataset CLX continues to perform the worst accuracies and the dataset GC3 the best accuracies values.

Figure 13, shows a comparison of all accuracies, regarding the major emotions from tests 1 to 34 (top plots) and tests 1 to 34 (bottom plot). Note that on the top plot, shows six datasets kept the major emotion accuracies less than 50%.

![](img/601340ca744b738277eef45ff127492a_108_0.png)

![](img/601340ca744b738277eef45ff127492a_108_1.png)

**Figure 13.** All higher emotion accuracies from tests 1-34. All accuracies (left); mean of all accuracies (right).

The top left plot, presents the relation between the raw dataset accuracies (tests 3–34), which the raw data seems to have better accuracies over the featured datasets. It means that the recognition based on raw datasets was the best solution in this proposed method.

The answer for that is *not necessarily*; if we go back a little and observe the error levels during the tests based on raw datasets; we will see that it was extremely bad compared to the others tests based on featured dataset; we can easily note that, a good regression model must be based on a combination of low error levels and good emotion accuracies.

Finally, when analyzing the bottom plot, it is possible to note that when the activation function *sigmoid* together with the *gradient descend* optimization, the general accuracies presented a constant behaviour along the executed tests. The activation function *rectified unit* performed the worst major emotions in this work.

## 5.7. Improving these Results

To improve these results, this work shows that is strongly recommended, first, to optimize the emotions detection from the face. it was undoubtedly, the main reason for several undesirable recognition error levels. Another way to improve it is to omit datasets which presented bad predictions, it surely will improve the general predictions or emotional recognition.

However, some results were already improved during this work. For instance, when looking to the learning tasks, absolute improvements were applied, changing the traditional learning techniques by the Deep Learning techniques. These latest optimized the recognition results in accuracies of recognition and in execution time.

Figure 1-4, shows the improvement due to the use of Deep Learning techniques, regarding to the amount of correct matches of the major emotions, between all emotions considered in this work. It is possible to see, that the dataset KLX with worst accuracy also on traditional learning.

![](img/601340ca744b738277eef45ff127492a_109_0.png)

Trad. * DP [100 itj.] - Major Emotions C.V. Acc. (%)

Trad. * DP [1000 itj.] - Major Emotions C.V. Acc. (%)

- ☑ Traditional Learning (no features)
- ☑ Deep learning (no features)

**Figure 14.** Traditional learning versus Deep Learning. Improvement in this work regarding the major emotion values when applying the traditional learning and Deep Learning (no feature extraction).

Regarding the accounts of the major emotion values based on 100 training iteration of the traditional learning, the improvement happened in 11 flight datasets from 13: RC1 was 69.52% (prior 15.39/50.50); RC2 of 72.71% (21.41/82.13); RC3 of 68.97% (18.25/58.83); GCI of 80.97% (4.48/23.55); GC3 of 89.88% (10.08/99.65); LSI of 73.63% (5.93/22.49).
