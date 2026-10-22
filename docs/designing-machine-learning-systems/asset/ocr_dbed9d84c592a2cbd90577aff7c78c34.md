Despite knowing its importance, many still ignore systematic approaches to hyperparameter tuning in favor of a manual, gut-feeling approach. The most popular is arguably graduate student descent (GSD), a technique in which a graduate student fiddles around with the hyperparameters until the model works.24

However, more and more people are adopting hyperparameter tuning as part of their standard pipelines. Popular ML frameworks either come with built-in utilities or have third-party utilities for hyperparameter tuning—for example, scikit-learn with auto-sklearn,25 TensorFlow with Keras Tuner, and Ray with Tune. Popular methods for hyperparameter tuning include random search,26 grid search, and Bayesian optimization.27 The book AutoML: Methods, Systems, Challenges by the AutoML group at the University of Freiburg dedicates its first chapter (which you can read online for free) to hyperparameter optimization.

When tuning hyperparameters, keep in mind that a model's performance might be more sensitive to the change in one hyperparameter than another, and therefore sensitive hyperparameters should be more carefully tuned.

![](bbox=[0.15, 0.42, 0.24, 0.52])

It's crucial to never use your test split to tune hyperparameters. Choose the best set of hyperparameters for a model based on its performance on a validation split, then report the model's final performance on the test split. If you use your test split to tune hyperparameters, you risk overfitting your model to the test split.

# Hard AutoML: Architecture search and learned optimizer

Some teams take hyperparameter tuning to the next level: what if we treat other components of a model or the entire model as hyperparameters. The size of a convolution layer or whether or not to have a skip layer can be considered a hyperparameter. Instead of manually putting a pooling layer after a convolutional layer or ReLu (rectified linear unit) after linear, you give your algorithm these building blocks and let it figure out how to combine them. This area of research is known as architectural

24 GSD is a well-documented technique. See “How Do People Come Up With All These Crazy Deep Learning Architectures?,” Reddit, https://oreil.ly/5vEsH; “Debate About Science at Organizations like Google Brain/FAIR/DeepMind,” Reddit, https://oreil.ly/2K77r; “Grad Student Descent,” Science Dryad, January 25, 2014, https://oreil.ly/dIR9r; and Guy Zyskind (@GuyZys), “Grad Student Descent: the preferred #nonlinear #optimization technique #machinelearning,” Twitter, April 27, 2015, https://oreil.ly/SW1or.

25 auto-sklearn 2.0 also provides basic model selection capacity.

26 Our team at NVIDIA developed Milano, a framework-agnostic tool for automatic hyperparameter tuning using random search.

27 A common practice I've observed is to start with coarse-to-fine random search, then experiment with Bayesian or grid search once the search space has been significantly reduced.