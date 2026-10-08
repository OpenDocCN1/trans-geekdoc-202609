+   4. The preceding command will print out the directory where the pip utility is installed. Add the path of the Pip utility to the system path by running the following command:

```
set path = %path%;<path to the pip directory>
```

# Installing Jupyter Notebook on Windows

With Python 3 and the pip utility installed, we can now install Jupyter Notebook by running the following command in the Command Prompt window:

```
pip install jupyter
```

# Running the exercise

+   1. Now we have installed Python 3 and Jupyter Notebook, let's get started with the actual data science work. First, download the data files:

+   (a) Let’s create a folder called MLSLab on your local machine to store all the files. You can create the folder anywhere on your local machine as long as you can get to it. I have a Mac, so I created one directly inside the default user folder.

+   (b) Create another subfolder called Lab1-bankchurn under the MLSLab folder.

+   (c) Visit the https://www.kaggle.com/mathchi/churn-for-bank-customers site and download the data file (an archive file) and save it in the MLSLab/Lab1-bankchurn. Create a Kaggle account if you do not already have one. Extract the archive file inside the folder, and you will see a file churn.csv. Now you can delete the archive file.

+   2. Launch Jupyter Notebook:

+   (a) Inside the Terminal window (or the Command Prompt window for Windows), navigate to the MLSLab folder and run the following command to start the Jupyter Notebook server on your machine. A browser will open up and display the Jupyter Notebook environment (see the following screenshot). Detailed instructions on how Jupyter Notebook works is out of scope for this lab. If you are not familiar with how Jupyter Notebook works, you can easily find information on the internet: