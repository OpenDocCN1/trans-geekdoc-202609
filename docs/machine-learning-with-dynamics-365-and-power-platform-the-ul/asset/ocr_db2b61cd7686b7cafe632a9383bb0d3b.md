+   2. Sign into Azure Machine Learning Studio and select your subscription and workspace you created just now.

+   3. Now click the option Get started.

+   4. Go to the left pane under the Author section and select the option Automated ML.

+   5. If it is your first Automated ML experiment, you'll see an empty list and links to documentation.

+   6. Click on +New automated ML run.

Now, you must create and load your dataset (Figure 4.1). First, you need to upload your data file to your workspace. The reason behind uploading your data in the form of an Azure Machine Learning dataset in your workspace is because it assures you that your data is appropriately formatted for your experiment (Figure 4.2). Following are the steps to create and load the dataset. Of course, in a real production environment, you should connect to your own datastore like your Azure Data Lake Storage or even your Synapse Analytics. You can also try to use Azure Open Data sets, which will give you some basic examples to try with real datasets very fast.

![](bbox=[0.124, 0.534, 0.875, 0.825])

# FIGURE 4.1 Select dataset.