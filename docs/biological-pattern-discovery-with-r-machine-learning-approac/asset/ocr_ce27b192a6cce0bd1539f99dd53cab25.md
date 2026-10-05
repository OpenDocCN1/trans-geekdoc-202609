# Biological Pattern Discovery with R

![](bbox=[0.137, 0.106, 0.862, 0.308])

Fig. 4.26. (a) The importance visualisation of the variable ranking result of the SVM model for the olive oil content data. The model employs ten hidden neurons. (b) The fitness measurement for the SVM model.

The random forest regression algorithm can also help ranking variables as well. Figure 4.27(a) shows the variable importance ranking result of the random forest model constructed for the olive oil content data. The ranking was also done using the vip package. In this case, the paste water variable was ranked at the top. Figure 4.27(b) shows the fitness measurements for this model. The R-square of the model was 0.654 and the $F$-statistic $p$ value of the model was 6.05e−6.

![](bbox=[0.137, 0.566, 0.862, 0.74])

Fig. 4.27. The random forest model for the olive content data. (a) The importance measure of variables. (b) The fitness measurements of the model.

Figure 4.28 shows a decision tree generated using the party package. The root node shown in Figure 4.28 employed the fruit weight variable as the first partitioning rule. Using this tree, it can be seen that maximising the oil content in olives may go through two partitioning rules, i.e., the