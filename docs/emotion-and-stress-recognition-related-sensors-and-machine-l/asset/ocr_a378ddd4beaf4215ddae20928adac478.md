Analyzing the RMSE (left barplot), it is possible to see that the improvements were important over all emotions when feature extraction was used. The emotion happy presented an improvement of 89.66% (prior 3.06/actual 0.31); sad of 84.58% (5.38/0.02); angry of 86.75% (3.84/0.50); surprised of 93.89% (2.19/0.13); and scared of 88.67% (3.18/0.36).

Analyzing the MAE values (right barplot), it is possible to see that the improvements were good over 4 of 5 matches (emotion sad wasn't improved on MAE values), when feature extraction was used. The emotion happy presented an improvement of 26.04% (prior 0.06/actual 0.04); angry of 4.32% (0.065/0.062); surprised of 60.15% (0.04/0.01); and scared of 18.75% (0.05/0.04).

# 5.6. Considering the Intensities Between Emotions

The higher intensities by time (between five emotion intensities) were also computed and its amount of matches were also analyzed, comparing the correct matches between his higher emotion (from the face dataset) with the higher output from the five neurons (output layer).

The benefit to also consider higher values by time is to understand if the regression models from each output result in following emotion intensities related to the others. In other words, if a regression model from each neuron fits to a target, both error levels (RMSE+MAE) and major/minor values will improve.

The corrected amount of matches between these emotions and its relations is in Figure 12, presenting the case of tests 3-6.

![](bbox=[0.145, 0.442, 0.854, 0.755])

Figure 12. Major emotion accuracies from the tests 3 to 6 (with feature extraction).

Some datasets presented a very low amount of matches during all tests as for instance, GC1, LS1, VCI, CLX and CL3. These low accuracies are probable due the high misclassification of emotions from the pilots' faces as also presented on prior errors value based on RMSE and MAE. However, if we consider the possibility to improve these results, the next tests can use these datasets with low accuracies to get better general results.