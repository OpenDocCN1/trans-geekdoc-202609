# Chapter 4: Getting Started with Python & Turi Create

From the command prompt in **Terminal**, create a new environment named **mlenv**nwith **Python 3.7:**

```
conda create -n mlenv python=3.7
```

Type y to proceed with installing the base packages of the environment. Next,
activate the environment:

```
conda activate mlenv
```

You should see (mlenv) in the command promptmtr. Finally, install a bunch of
packages at once:

```
conda install numpy pandas matplotlib seaborn scipy scikit-learn
scikit-image jupyter
```

Type y again to proceed and wait for the installation to finish.

> **Note:** It's possible that when you're reading this book, the Anaconda
download will be for Python version 3.8 or later. However, in all the
environments used by this book, you will **need to use Python 3.7. This means,
when you create your environment, **be sure to specify** the Python version. If you
choose another version of Python, some of the machine learning libraries
y'll need for the book may not work with that version.

# An important note about package versions

Technology moves fast, also in the world of Python. Chances that by the time you
read this book, newer versions are available for the packages that we're using. It's
quite possible newer versions may not be 100% compatible with older versions.

For example, in this book we use Keras version 2.2.4. But newer versions of Keras
may not work with some of the code examples in this book. Even version 2.2.1, which
emed a minor upgrade from 2.2.0 that shouldn't have much of an impact,
actually breaks things.

Here's a dirty little secret you should be aware of: You do not need to use the latest,
greatest version of these packages. Keras 2.2.4 works for our purposes and we
can't keep updating the book every time a new version comes out and breaks
sothing.