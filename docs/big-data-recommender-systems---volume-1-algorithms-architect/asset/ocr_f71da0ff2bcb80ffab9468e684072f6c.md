# 216 Big data recommender systems, volume 1

![](bbox=[0.265, 0.098, 0.693, 0.303])

Figure 9.9 Training time of ST-SAGE on GraphLab

#  9.5.3.1 Model training efficiency

To make our ST-SAGE model scalable to large-scale datasets, we implement based on the GraphLab framework. The training time of ST-SAGE on the Twitter dataset is reported under different numbers of nodes in Figure 9.9. From the result, we observe that the training time of ST-SAGE decreases significantly with growing size of distributed GraphLab nodes. We reduce the training time for ST-SAGE from approximately 100 h to less than 10 h. Though the basic implementation of ST-SAGE is costly, the parallel implementation guarantees the scalability of our ST-SAGE model. This model is feasible in practical deployment.

#  9.5.3.2 Online recommendation efficiency

In this section, we evaluate the recommendation efficiency using the Foursquare dataset. In the efficiency study, we tested top-k recommendations for the target region with 50km × 50km and 100km × 100km, respectively. Obviously, there are more spatial items in the target region with 100 km × 100 km than in the region with 50km × 50 km. All recommendation algorithms are implemented in Java 1.7 and run on a Windows Server with "Intel E5-2690" CPU and 256 G RAM.

For the online recommendation efficiency test, we compare ST-SAGE with UPSCF, CKNN and UTE+SE. We did not compare our model with LCA–LDA and JIM due to the fact that the TA algorithm can be employed to use the online recommendation in the two recommender models, as ranking functions are also monotonous. For the online recommendation of ST-SAGE, we adopt two methods to utilize the learned offence to produce recommendations. The first method extends the TA algorithm to produce top-k recommendations and is denoted as “ST-SAGE-TA.” The second method linearly cleans all the spatial items in the target region, computes their ranking scores and recommends the top-k items with the highest scores. This method is called “ST-SAGE-LS.”

Figure 9.10 presents the average online efficiency of the four different methods. On average, we proposed “ST-SAGE-TA” produces top-10 recommendations