
![](img/0684d2da98e09085c0a622d4fd69aaad_55_0.png)

Figure 1-23. Regularization reduces the risk of overfitting

The amount of regularization to apply during learning can be controlled by a hyperparameter. A hyperparameter is a parameter of a learning algorithm (not of the model). As such, it is not affected by the learning algorithm itself; it must be set prior to training and remains constant during training. If you set the regularization hyperparameter to a very large value, you will get an almost flat model (a slope close to zero); the learning algorithm will almost certainly not overfit the training data, but it will be less likely to find a good solution. Tuning hyperparameters is an important part of building a Machine Learning system (you will see a detailed example in the next chapter).

## Underfitting the Training Data

As you might guess, underfitting is the opposite of overfitting: it occurs when your model is too simple to learn the underlying structure of the data. For example, a linear model of life satisfaction is prone to underfit; reality is just more complex than the model, so its predictions are bound to be inaccurate, even on the training examples.

The main options to fix this problem are:

- Selecting a more powerful model, with more parameters
- Feeding better features to the learning algorithm (feature engineering)
- Reducing the constraints on the model (e.g., reducing the regularization hyperparameter)

## Stepping Back

By now you already know a lot about Machine Learning. However, we went through so many concepts that you may be feeling a little lost, so let's step back and look at the big picture:

- Machine Learning is about making machines get better at some task by learning from data, instead of having to explicitly code rules.

- There are many different types of ML systems: supervised or not, batch or online, instance-based or model-based, and so on.

- In a ML project you gather data in a training set, and you feed the training set to a learning algorithm. If the algorithm is model-based it tunes some parameters to fit the training set (i.e., to make good predictions on the training set itself), and hopefully it will be able to make good predictions on new cases as well. If the algorithm is instance-based, it learns the examples by heart and generalizes to new instances by comparing them to the learned instances using a similarity measure.

- The system will not perform well if your training is too small, or if the data is not representative, noisy; or polluted with irrelevant features (garbage in, garbage out). Lastly, your model needs to be neither too simple (in which case it will underfit) nor too complex (in which it will overfit).

There’s just last important topic to cover: once you have trained a model, you don’t want to just “hope” it generalizes to new cases. You want to evaluate it, and fine-tune it if necessary. Let’s see.

## Testing and Validating

The only way to know how well a model will generalize to new cases is to actually try it out on new cases. One way to do that is to put your model in production and monitor how well it performs. This works well, but if your model is bad, your users will complain—not the best idea.

A better option is to split your data into two sets: the training set and the test set. As these names imply, you train your model using the training set, and test it using the test set. The error on new cases is called the generalization error (or out-of-sample error), and by evaluating your model on the test set, you can get an estimate of this error. This value tells you how well your model will perform on instances it has never seen before.

If the training error is low (i.e., your model makes few mistakes on the training set) but the generalization error is high, it means your model is overfitting the training data.

![](img/0684d2da98e09085c0a622d4fd69aaad_56_0.png)

It is common to use 80% of the data for training and hold out 20% for testing. However, this depends on the size of the dataset: if it contains 10 million instances, holding out 1% means your test set will contain 100,000 instances: that’s probably enough to get a good estimate of the generalization error.

## Hyperparameter Tuning and Model Selection

So evaluating a model is simple enough: just use a test set. Now suppose you are hesitating between two models (say a linear model and a polynomial model): how can you decide? One option is to train both and compare how they generalize using the test set.

Now suppose that the linear model generalizes better, but you want to apply some regularization over overfitting. The question is: how do you choose the value of the regularization hyperparameter? One option is to train 100 models using 100 different values for this hyperparameter. Suppose you find the best hyperparameter value that produces a model with the lowest generalization error, say just 5% error.

So you launch this model into production, but unfortunately it does not perform as well as expected and produces 15% errors. What happened?

The problem is that you measured the generalization error multiple times on the test set, and adjusted the model and hyperparameters to produce the best model for that particular set. This means that the model is unlikely to perform as well as on new data.

A common solution to this problem is called holdout validation: you simply hold out part of the training set to evaluate several candidate models and select the best one. The new holdout set is called the validation set (or sometimes the development set, or dev set). More specifically, you train multiple models with various hyperparameters on the reduced training set (i.e., the full training set the validation set), and you select the model that performs best on the validation set. After this validation process, you train the model on the full training set (including the validation set), and this gives you the final model. Lastly, you evaluate this final model on the test set to get an estimate of the generalization error.

This solution usually works well. However, if the validation set is too small, then model evaluations will be imprecise: you may end up selecting a suboptimal model by mistake. Conversely, if the validation set is too large, then the remaining training set will be much smaller than the full training set. Why is this bad? Well, since the final model will be trained on the full training set, it is not ideal to compare models trained on a much smaller training set. It would be like the fastest sprinter to participate in a marathon. One way to solve this problem is to perform repeated cross-validation, using many validation sets. Each model is evaluated once per validation set, after it is trained on the rest of the data. By averaging out the evaluations of a model, we get a more accurate measure of its performance. However, there is a drawback: the training time is multiplied by the number of sets.

## Data Mismatch

In some cases, it is easy to get a large amount of data for training, but it is not representative of the data that will be used in production. For example, suppose you want to create a mobile app to take pictures of flowers and automatically determine their species. You can easily download millions of pictures on the web, but they will not be representative of the pictures that will be taken on a mobile device. Perhaps you only have 10,000 representative pictures (i.e., actually taken with the app). In this case, the most important rule to remember is that the validation set and the test must be as representative as the data you expect to use in production, so they should be composed exclusively of representative pictures: you can shuffle them and put half in the validation set, and half in the test set (making sure that no duplicates or near-duplicates end up in both sets). After training your model on the web pictures, if you observe the performance of your model on the validation set is disappointing, you will not know whether this is because your model has overfit the training set, or whether this is just due to the mismatch between the web pictures and the mobile app pictures. One solution is to hold out part of the training (from the web) in another set as Andrew Ng calls the train-dev set. After the model is trained (on the training set, not on the train-dev set), you evaluate it on the train-dev set: if it performs well, the model is not overfitting the training set, the problem must come from the data mismatch. You can try to tackle this by preprocessing the web images to make them more like the pictures that will be taken by the mobile app, and then retraining the model. Conversely, if the model performs poorly on the train-dev set, the model must have overfit the training set, so you try to simplify or regularize the model, get more training data and clean up the training data.

## No Free Lunch Theorem

A model is a simplified version of the observations. The simplifications are meant to discard the superfluous details that are unlikely to generalize to new instances. However, to decide what to discard and what data to keep, you must make assumptions. For, a linear model makes the assumption that the data is fundamentally linear and the distance between the instances and the straight line is just noise, which can be safely ignored.

In a famous 1996 paper,¹ David Wolpert demonstrated that if you make absolutely no assumption about the data, then there is no reason to prefer one model over other. This is called the No Free Lunch (NFL) theorem. For some datasets the best
