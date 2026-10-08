# 118 Applied Intelligent Decision Making in Machine Learning

![](bbox=[0.273, 0.095, 0.726, 0.363])

**FIGURE 6.3** Re-weightage in the boosting model.

Stacking combines several base learners using a meta-classifier or regressor. Base learners are trained on a subset of samples. A meta-classifier/regressor works on top of the base learner. The procedure for stacking is given below.
The training set is split into two sets that are disjoint:

+   1. In one part, several base learners are trained;
2. In the other part, the base learners are tested;
3. Higher level learners are then trained using input as the predictions from the previous step and output as the correct responses.

# 6.2.2.1 Variants of Ensemble Models

Variant approaches for ensemble methods are proposed using fuzzy, neural network, and some statistical approaches. Fuzzy instance weight assignment for ensemble classification on data streams was proposed to identify the concept drift. This is an adaptive approach using a dynamic voting method. This method proposed by Dong et al. has the advantage of less computational cost with better accuracy. It is adaptive and can recognize concept drift.

A weighted neural network of ensemble models uses a bagging scheme. The dynamic weightage method uses integration of a network ensemble classifier. This method outperforms the performances of traditional integration methods (Li et al. 2007). The composite prediction output is obtained by combining various Long Short Term Memory (LSTM) models by dynamically adjusting the combining weights. By using the forgetting weight factor and past prediction errors the combining weights can be updated in a recursive and adaptive way (Choi and Lee 2018).