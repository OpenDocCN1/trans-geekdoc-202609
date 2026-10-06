
on the page to get an earlier version for an older computer. You can also scroll down to see all the installers. Once you've downloaded it, double-click it and follow the instructions. Everything is ready to go for R.

# Installing Data Science Packages

If you code for any length of time, you'll eventually come across a package that you don't already have installed. It's common to install several before you even get started just because you know you'll probably need them eventually.

Note that I tend to use the terms "library" and "package" interchangeably in reference to Python. They are subtly different, but it's not important for this appendix. However, in R, they are more different, and the term "package" is the right one.

# Python Packages

As mentioned, the Anaconda distribution already has most of the libraries you need to do data science already installed. If you're going to be doing some specialized stuff like NLP or deep learning, it won't have packages for those, so you might want to go ahead figure out which ones you need and install them. Table A-1 shows good data science libraries to start with, indicating which aren't included in the Anaconda distribution.

If you've installed the official Python distribution instead, you will likely want to install the libraries listed in Table A-1.

# APPENDIX A SETTING UP YOUR COMPUTER TO DO DATA SCIENCE

# Table A-1. Recommended Python packages

| Package | Use | In Anaconda |
| --- | --- | --- |
| pandas | Data frames | ✓ |
| numpy | Numeric data manipulation | ✓ |
| scipy | Builds on numpy | ✓ |
| plotly | Visualization | ✓ |
| matplotlib | Visualization | ✓ |
| seaborn | Visualization | ✓ |
| statsmodels | Statistics | ✓ |
| scikit-learn | ML modeling and performance | ✓ |
| xgboost | ML modeling | No |
| pytorch | ML modeling (deep learning) | ✓ |
| keras | ML modeling (deep learning) | No |
| nltk | NLP modeling | ✓ |
| spacy | NLP modeling | No |
| jupyter | Jupyter Notebooks | ✓ |

The common way to install libraries is at the command line with the command conda (with Anaconda) or pip. Note that this is not within the Python interpreter itself, but rather at the system level. With Anaconda, you have an additional option. You can run the Anaconda Navigator GUI (available in all operating systems) and select libraries to install. Otherwise, use the Anaconda Prompt in Windows and the system terminal on Mac and Linux (in VS Code, you can open a terminal in an IDE and type the command there).

The full command to install a library, let's say XGBoost, is conda install xgboost or pip install xgboost. Usually, if you have Anaconda, you'll try with conda first, and if that doesn't work, use pip. Otherwise start with pip. conda requires some integration with the distribution to work, and not all libraries have been set up for this, which is why sometimes you have to use pip. But they both accomplish the same thing. Note that often you'll need to use pip3 rather than pip. That just ensures you're using the Python version 3 installer.

# R Packages

In R, you install packages from within the R interpreter itself, rather than at the system level like you do with Python. A new installation of R only comes with 15 base packages installed, so you will need to install some. Open RStudio and run the function install.packages() with the name of the package you want installed inside single quotes in the parentheses, like install.packages('lubridate'). You can also install multiple in one line, which looks like this: install.packages(c('lubridate', 'dplyr', 'stats')). Table A-2 shows some of the packages you might want to install.

# APPENDIX A SETTING UP YOUR COMPUTER TO DO DATA SCIENCE

# ### Table A-2. Recommended R packages

| Package | Use | Base Install |
| --- | --- | --- |
| data.table | More data frame manipulation | No |
| dplyr | Data manipulation | No |
| lubridate | Date manipulation | No |
| ggplot2 | Visualization | No |
| stats | Statistics | ✓ |
| e1071 | ML modeling | No |
| xgboost | ML modeling | No |
| randomForest | ML modeling | No |
| tensorflow | ML modeling | No |
| naivebayes | ML modeling | No |
| metrics | ML performance | No |
| tidymodels | ML support | No |
| shiny | Presentation | No |

# ## System vs. Virtual Environment Installation

The methods described above are how you would install these packages at the system (or the logged-in user) level. It's long been common to work with what are called virtual environments in Python, where you basically create an encapsulated space on your computer that has a particular version of Python and specific packages installed. R has a package called renv that allows you to manage virtual environments.

For a given virtual environment, you would specify which versions of each package should be installed, and that environment won't be modified by any other changes at the system level. This can be useful if you need to use an older version of some package because you're using another one that isn't compatible with the most recent version. It's also a way of keeping things static, as sometimes installing a package on your computer will automatically update another package, and if you had code working on a specific version of that second package, it could break.

When using virtual environments, you normally manage the packages with a list that is used to configure the environment. Usually, this is done with a YAML file (extension .yml) that lists all the packages and their version number in a particular format. This can be done with both Python and R environments.

# Start Coding

Everything's set up and ready to go. Now you just need to open up your IDE and start writing code.

# Coding in Python in VS Code

Now that you've got your extensions in place, you'll need to ensure that you can access your Python installation (and R if appropriate) from within the IDE. Often it works out of the box, but if you have trouble, go to Settings in VS Code and find the option “Python: Default Interpreter Path” and point to the python.exe file in your new Python installation folder.

If you didn't install Jupyter, you will need to create a file with a .py extension. This is called a script. You can put whatever code in this file, but to run any of it, you'll have to run the whole file. If you have a step that takes a long time, it will still have to run every time.

# APPENDIX A SETTING UP YOUR COMPUTER TO DO DATA SCIENCE

If you installed Jupyter, there are a couple options for writing your code. You can still do it the old way, but better is to create a notebook. Create a file with the extension .ipynb, and VS Code will treat it as a Jupyter Notebook. This is the best way to get started writing code. A notebook has individual cells one after the other, and you can put code or text (markdown) in each cell. This allows you to run code separately. If you run a big data processing step that takes several minutes and you want to use the data frame (the table) that it produces, you won't have to rerun that step even if you change code that is after. To run a cell in a notebook, click the right-pointing arrow to the left of the cell or use keyboard shortcuts (Ctrl-Enter).

# Coding in R in RStudio Desktop

When first open RStudio, it shows a console, which is basically the R interpreter. You can run commands here. You can also create files with lines of code just like Python, but you can run each line independently, giving you the flexibility that Jupyter Notebooks do for Python. It's recommended to create files because otherwise you haven't saved what you've run. When you create a file, it opens in the top left. You can start typing your code there. Each line can be run with Ctrl-Enter or clicking the Run button at the top of the file. The Source button runs the entire file.

# Conclusion

Now you've got your computer set, and you're ready to start doing data science, whether you're using R or Python (or a mix of both). Make sure if you run into any trouble installing anything, check in with Google because somebody somewhere has probably had the same trouble.
