
![](img/574135cb1d7125b50cf484d943cdd676_203_0.png)

FIGURE 6.6: A typical binary classification problem.

**PRB-150** **CH.PRB- 6.16.**

*True or false: When using a single model, the risk of overfitting the data increases when the number of adjustable parameters is large compared to cardinality (i.e., size of the set) of the training corpus.*

**PRB-151** **CH.PRB- 6.17.**

*True or false: If we have a committee of K trained models and the errors are uncorrelated, then by averaging them the average error of a model is reduced by a factor of K.*

## 6.2.4 Ensemble Learning

**PRB-152** **CH.PRB- 6.18.**

- Define ensemble learning in the context of machine learning.
- Provide examples of ensemble methods in classical machine-learning.
- *True or false:* Ensemble methods usually have stronger generalization ability.
- Complete the sentence: Bagging is *variance*/*bias* reduction scheme while boosting reduced *variance/bias*

## 6.2.5 Snapshot Ensembling

**PRB-153** **CH.PRB- 6.19.**

*Your colleague, a well-known expert in ensembling methods, writes the following pseudo code in Python shown in Fig. 6.7 for the training of a neural network. This runs inside a standard loop in each training and validation step*

```python
import torchvision.models as models
... models=[ 'resnext' ]
for m in models: train ... compute VAL loss ... amend LR ...
if(val_acc > 90.0): saveModel()
```

![](img/574135cb1d7125b50cf484d943cdd676_204_0.png)

- What type of ensembling can be used with this approach? Explain in detail
- What is the main advantage of snapshot ensembling? What are the disadvantages, if any?

**PRB-154** **CH.PRB- 6.20.**

*Assume further that your colleague amends the code as follows in Fig. 6.8*

```python
1    import torchvision.models as models
2    import random
3    import np
4    ...
5    models = ['resnext']
6        for m in models:
7            train ...
8            compute loss ...
9            amend LR ...
10            manualSeed= draw a new random number
11            random. seed(manualSeed)
12            np. random. seed(manualSeed)
13            torch. manual_seed(manualSeed)
14            if (val_acc > 90.0) :
15                saveModel()
```

![](img/574135cb1d7125b50cf484d943cdd676_205_0.png)

Explain in detail what would be the possible effects of adding lines 10-13.

## 6.2.6 Multi-model Ensembling

**PRB-155** **CH. PRB- 6.21.**

Assume your colleague, a veteran in DL and an expert in ensembling methods writes the following Pseudo code shown in Fig. 6.9 for the training of several neural networks. This code snippet is executed inside a standard loop in each and every training/validation epoch.

```python
1    import torchvision.models as models
2    ...
3    models = ['resnext' ,'vgg' , 'dense' ]
4        for m in models:
5            train ...
6            compute loss/acc ...
7 if (val_acc > 90.0): 
8 saveModel()
```

![](img/574135cb1d7125b50cf484d943cdd676_206_0.png)

*What type of ensembling is being utilized in this approach? Explain in detail.*

Name one method by which NN models may be combined to yield a single prediction.

## 6.2.7 Learning-rate Schedules in Ensembling

**PRB-156** **CH. PRB- 6.22.**

- Referring to Fig. ( 6.10 ) which depicts a specific learning rate schedule, describe the basic notion behind its mechanism.

![](img/574135cb1d7125b50cf484d943cdd676_206_1.png)

- Explain how cyclic learning rates [ 10 ] can be effective for the training of convolutional neural networks such as the ones in the code snippet of Fig 6.10.
- Explain how a cyclic cosine annealing schedule as proposed by Loshchilov $[10]$ and $[13]$ is used to converge to multiple local minima.

# 6.3 Solutions

## 6.3.1 Bagging, Boosting and Stacking

**SOL-135** **CH.SOL- 6.1.**

All the presented options are correct.

**SOL-136** **CH.SOL- 6.2.**

The correct choice would be stacking. In cases where the given corpus is small, we would most likely prefer training our models on the **full data-set**.

**SOL-137** **CH.SOL- 6.3.**

A random forest is a type of a decision tree which utilizes bagging.

**SOL-138** **CH.SOL- 6.4.**

The presented algorithm is a classic bagging.

**SOL-139** **CH.SOL- 6.5.**

The approach which is depicted is the **first phase** of stacking. In stacking, we first (phase 0) predict using several base learners and then use a generalizer (phase 1) that learns on top of the base learners predictions.

**SOL-140** **CH.SOL- 6.6.**

- Sampling with replacement
- Sampling without replacement.
- This may be mostly a result of bagging, since in boosting we would have expected miss-correctly classified observations to repeatedly appear in subsequent samples.

## 6.3.2 Approaches for Combining Predictors

**SOL-141** **CH.SOL- 6.7.**

An Algebraic weighted average for class probabilities.

**SOL-142** **CH.SOL- 6.8.**

This is true. $[\hat{3}]$ provides a mathematical proof.

**SOL-143** **CH.SOL- 6.9.**

This is true. For extension, see instance $[\hat{8}]$.

**SOL-144** **CH.SOL- 6.10.**

This is true. In a bagging approach, we first randomly draw (with replacement), $K$ examples where $K$ is the size of the original training corpus therefore leading to an imbalanced representation of the instances.

## 6.3.3 Monolithic and Heterogeneous Ensembling

**SOL-145** **CH.SOL- 6.11.**

- **True** Due to their lack of diversity, an ensemble of monolithic architectures tends to perform worse than an heterogeneous ensemble.
- **True** This has be consistently demonstrated in $[\underline{11},\ \underline{5}]$.
- True In [6] there is a discussion about both using the whole corpus and a subset much like in bagging.
- True The total error decreases with the addition of predictors to the ensemble.

**SOL-146** **CH.SOL- 6.12.**

Yes, they do.

**SOL-147** **CH.SOL- 6.13.**

- Yes, it is very likely, especially if their errors are independent.
- True It may be proven that ensembles of models perform at least as good as each of the ensemble members it consists of.
- True Different local minima add to the diversification of the models.

**SOL-148** **CH.SOL- 6.14.**

Boosting is the only one that does not.

**SOL-149** **CH.SOL- 6.15.**

False By definition, static committee machines use *only* the output of the single predictors.

**SOL-150** **CH.SOL- 6.16.**

True

**SOL-151** **CH.SOL- 6.17.**

*False* *Though this may be theoretically true, in practice the errors are rarely uncorrelated and therefore the actual error can not be reduced by a factor of K.*

## 6.3.4 Ensemble Learning

**SOL-152** **CH.SOL- 6.18.**

- *Ensemble learning is an excellent machine learning idea which displays noticeable benefits in many applications, one such notable example is the widespread use of ensembles in Kaggle competitions. In an ensemble several individual models (for instance ResNet18 and VGG16) which were trained on the same corpus, work in tandem and during inference, their predictions are fused by a pre-defined strategy to yield a single prediction.*
- *In classical machine learning Ensemble methods usually refer to bagging, boosting and the linear combination of regression or classification models.*
- *True* *The stronger generalization ability stems from the voting power of diverse models which are joined together.*
- *Bagging is variance reduction scheme while boosting reduced bias.*

## 6.3.5 Snapshot Ensembling

**SOL-153** **CH.SOL- 6.19.**

- *Since only a single model is being utilized, this type of ensembling is known as snapshot ensembling. Using this approach, during the training of a neural network and in each epoch, a snapshot, e.g. the weights of a trained instance of a model (a PTH file in PyTorch nomenclature) are persisted into permanent storage whenever a certain performance metrics, such as accuracy or loss is being surpassed. Therefore the name “snapshot”; weights of the neural network are being snapshot at specific*
