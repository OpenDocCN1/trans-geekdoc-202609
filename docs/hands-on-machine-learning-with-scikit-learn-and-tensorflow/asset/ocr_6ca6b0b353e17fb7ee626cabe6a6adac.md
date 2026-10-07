to be good, it should be explored more. This takes care of the "zooming" process for and leads you to better solutions in much less time. Here are a few Python libraries you use to optimize hyperparameters:

+   - Hyperopt: a Python library for optimizing over all sorts of complex search spaces (including real values as the learning rate, or discrete values as the number of layers).

+   - Hyperas, kept or Talos: optimizing hyperparameters for Keras model (the first two are based on Hyperopt).

+   - Scikit-Optimize (skopt): a general-purpose optimization library. The SearchCV class performs Bayesian optimization using an interface similar to GridCV.

+   - Spearmint: a Bayesian optimization library.

+   - Sklearn-Deap: a hyperparameter optimization library based on evolutionary algorithms, also with a GridSearchCV-like interface.

+   - And many more!

Moreover, many companies offer services for hyperparameter optimization. For example Google Cloud ML Engine has a hyperparameter tuning service. Other companies provide APIs for hyperparameter optimization, such as Arimo, SigOpt, Oscar and many more.

Hyperparameter tuning is still an active area of research. Evolutionary algorithms are making a comeback. For example, check out DeepMind's 2017 paper where they optimize a population of models and their hyperparameters. Google also use an evolutionary approach, not just to search for hyperparameters, but also to find the best neural network architecture for the problem. They call AutoML, and it is already available a cloud service. Perhaps the days of building neural networks manually will soon be? Check out Google's post on this topic. In fact, evolutionary algorithms have also been used to train individual neural networks, replacing the ubiquitous Gradient Descent! See this 2017 post by Uber introduce their Deepevolution technique.

Despite this exciting progress, and all these tools, it still helps to have an idea of what values are reasonable for each hyperparameter, you can build a quick prototype, and restrict the search space. Here are a few guidelines for choosing the number of hidden layers and neurons in an MLP, and selecting good values for some of the main hyperparameters.