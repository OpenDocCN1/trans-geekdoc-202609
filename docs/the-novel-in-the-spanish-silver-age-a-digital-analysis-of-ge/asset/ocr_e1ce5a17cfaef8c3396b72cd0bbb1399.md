Figure 38: Box plots showing the performance of different parameters

![](bbox=[0.176, 0.185, 0.843, 0.672])

# ### 3.3.5 Multi-Class Evaluation of Parameters

Parallel to the binary evaluation, I also evaluate the classification of CORDE 1860–1960 using CoNSSA using multi-class classification. In this case, I do not pass the texts divided into two groups for each genre (either it belongs to the genre or not). Instead, every text (6,800) gets assigned one single label out of 19 possible values. In this way, the algorithm has to choose a single genre for each text. I choose not to under-sample in this scenario as,