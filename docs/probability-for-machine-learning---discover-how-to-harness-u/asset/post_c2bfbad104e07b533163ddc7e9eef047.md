
### 28.6.2 API

- `sklearn.calibration.CalibratedClassifierCV` API.
  <http://scikit-learn.org/stable/modules/generated/sklearn.calibration.CalibratedClassifierCV.html>
- `sklearn.calibration.calibration_curve` API.
  <http://scikit-learn.org/stable/modules/generated/sklearn.calibration.calibration_curve.html#sklearn.calibration.calibration_curve>
- Probability calibration, scikit-learn User Guide.
  <http://scikit-learn.org/stable/modules/calibration.html>
- Probability Calibration curves, scikit-learn.
  <http://scikit-learn.org/stable/auto_examples/calibration/plot_calibration_curve.html>
- Comparison of Calibration of Classifiers, scikit-learn.
  <http://scikit-learn.org/stable/auto_examples/calibration/plot_compare_calibration.html>

### 28.6.3 Articles

- Calibration (statistics) on Wikipedia.
  <https://en.wikipedia.org/wiki/Calibration_(statistics)>
- Probabilistic classification on Wikipedia.
  <https://en.wikipedia.org/wiki/Probabilistic_classification>

## 28.7 Summary

In this tutorial, you discovered the importance of calibrating predicted probabilities and how to diagnose and improve the calibration of models used for probabilistic classification. Specifically, you learned:

- Nonlinear machine learning algorithms often predict uncalibrated class probabilities.
- Reliability diagrams can be used to diagnose the calibration of a model, and methods can be used to better calibrate predictions for a problem.
- How to develop reliability diagrams and calibrate classification models in Python with scikit-learn.

### 28.7.1 Next

This was the final tutorial in this Part. In the next Part, you will discover additional resources.

## Part IX: Appendix

## Appendix A: Getting Help

This is just the beginning of your journey with probability. As you start to work on projects and expand your existing knowledge of the techniques, you may need help. This appendix points out some of the best sources of help.

### A.1 Probability on Wikipedia

Wikipedia is a great place to start. All of the important topics are covered, the descriptions are concise, and the equations are consistent and readable. What is missing is the more human-level descriptions such as analogies and intuitions. Nevertheless, when you have questions about probability, I recommend stopping by Wikipedia first. Some good high-level pages to start on include:

- Probability, Wikipedia.
  <https://en.wikipedia.org/wiki/Probability>
- Probability theory, Wikipedia.
  <https://en.wikipedia.org/wiki/Probability_theory>
- List of probability topics, Wikipedia.
  <https://en.wikipedia.org/wiki/List_of_probability_topics>
- Catalog of articles in probability theory, Wikipedia.
  <https://en.wikipedia.org/wiki/Catalog_of_articles_in_probability_theory>
- Notation in probability and statistics, Wikipedia.
  <https://en.wikipedia.org/wiki/Notation_in_probability_and_statistics>

### A.2 Probability Textbooks

I strongly recommend getting a good textbook on the topic of probability and using it as a reference. The benefit of a good textbook is that the explanations of the various operations you require will be consistent (or should be). The downside of textbooks is that they can be very expensive. A good textbook is often easy to spot because it will be the basis for a range of undergraduate or postgraduate courses at top universities.

Some introductory textbooks on probability I recommend include:

- *Probability Theory: The Logic of Science*, 2003.
  <https://amzn.to/21nw2pp>
- *Introduction to Probability*, 2nd Edition, 2019.
  <https://amzn.to/2xPvobK>
- *Introduction to Probability*, 2nd Edition, 2008.
  <https://amzn.to/211A3PR>

I’d also recommend reading popular science books on probability and statistics. They provide good context and intuitions for the methods. Some recommendations include:

- *Naked Statistics: Stripping the Dread from the Data*, 2014.
  <http://amzn.to/2t7yXdV>
- *The Drunkard’s Walk: How Randomness Rules Our Lives*, 2009.
  <http://amzn.to/2CT4rUD>
- *The Signal and the Noise: Why So Many Predictions Fail - but Some Don’t*, 2015.
  <http://amzn.to/2FQdYyX>

### A.3 Probability and Machine Learning

There are a number of textbooks that introduce machine learning from a probabilistic perspective. These can be helpful, but do assume you have some background in probability and linear algebra. A few probabilistic perspectives on machine learning I would recommend include:

- *Machine Learning: A Probabilistic Perspective*, 2012.
  <https://amzn.to/2xKSTCP>
- *Pattern Recognition and Machine Learning*, 2006.
  <https://amzn.to/2JwHE7I>
- *Machine Learning*, 1997.
  <https://amzn.to/2jWd51p>

### A.4 Ask Questions About Probability

There are a lot of places that you can ask questions about probability online given the current abundance of question-and-answer platforms. Below is a list of the top places I recommend posting a question. Remember to search for your question before posting in case it has been asked and answered before.

- Probability tag on the Mathematics Stack Exchange.
  <https://math.stackexchange.com/?tags=probability>
- Cross Validated.
  <https://stats.stackexchange.com>
- Probability tag on Stack Overflow.
  <https://stackoverflow.com/questions/tagged/probability>
- Probability on Quora.
  <https://www.quora.com/topic/Probability-statistics-1>
- Probability Theory Subreddit.
  <https://www.reddit.com/r/probabilitytheory/>

### A.5 How to Ask Questions

Knowing where to get help is the first step, but you need to know how to get the most out of these resources. Below are some tips that you can use:

- Boil your question down to the simplest form. E.g. not something broad like “my model does not work” or “how does x work”.
- Search for answers before asking questions.
- Provide complete code and error messages.
- Boil your code down to the smallest possible working example that demonstrates the issue.

### A.6 Contact the Author

You are not alone. If you ever have any questions about probability, or the tutorials in this book, please contact me directly. I will do my best to help.

**Jason Brownlee**  
`Jason@MachineLearningMastery.com`

## Appendix B: How to Setup Python on Your Workstation

It can be difficult to install a Python machine learning environment on some platforms. Python itself must be installed first and then there are many packages to install, and it can be confusing for beginners. In this tutorial, you will discover how to setup a Python machine learning development environment using Anaconda.

After completing this tutorial, you will have a working Python environment to begin learning, practicing, and developing machine learning software. These instructions are suitable for Windows, macOS, and Linux platforms. I will demonstrate them on macOS, so you may see some Mac dialogs and file extensions.

### B.1 Tutorial Overview

In this tutorial, we will cover the following steps:

1. Download Anaconda
2. Install Anaconda
3. Start and Update Anaconda

Note: The specific versions may differ as the software and libraries are updated frequently.

### B.2 Download Anaconda

In this step, we will download the Anaconda Python package for your platform. Anaconda is a free and easy-to-use environment for scientific Python.

1. Visit the Anaconda homepage.
   <https://www.continuum.io/>
2. Click Anaconda from the menu and click Download to go to the download page.
   <https://www.continuum.io/downloads>

![](img/6ef657cfead7281442f755181c4f6e50_300_0.png)

*Figure B.1: Click Anaconda and Download.*

3. Choose the download suitable for your platform (Windows, OSX, or Linux):
   - Choose Python 3.6
   - Choose the Graphical Installer

![](img/6ef657cfead7281442f755181c4f6e50_301_0.png)

*Figure B.2: Choose Anaconda Download for Your Platform.*

This will download the Anaconda Python package to your workstation. I'm on macOS, so I chose the macOS version. The file is about 426 MB. You should have a file with a name like:

```
Anaconda3-4.4.0-MacOSX-x86_64.pkg
```

Listing B.1: Example filename on macOS.

### B.3 Install Anaconda

In this step, we will install the Anaconda Python software on your system. This step assumes you have sufficient administrative privileges to install software on your system.

1. Double click the downloaded file.
2. Follow the installation wizard.
