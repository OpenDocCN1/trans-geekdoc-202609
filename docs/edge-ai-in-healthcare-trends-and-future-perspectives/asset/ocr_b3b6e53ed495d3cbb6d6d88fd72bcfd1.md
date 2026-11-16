# ## 9.4.3 DATA VISUALISATION

Data visualisation is conducted to gain insights into the dataset, and it makes interpretation of data easier, using different types of graph. Heatmaps are drawn to present the correlation between different parameters of the extracted dataset, as shown in Figure 9.4. A pie chart has been plotted to present the percentage of stroke patients and non-stroke patients, as shown in Figure 9.5. A count plot (Ng 2004) is plotted to obtain the number of stroke and no-stroke events in males and females, as shown in Figure 9.6, while a scatter plot to evaluate the relationship between BMI and average glucose level is shown in Figure 9.7.

# ## 9.4.4 DATA SPLITTING

Using the train test split function, imported from ‘sklearn’ in Python, the retrieved dataset after data preprocessing was divided into training and testing data. The dataset was split into ratios of 80% and 20% for training and testing, respectively. Feature selection was performed to obtain the most-contributory and the least-contributory features (Hippisley-Cox et al. 2017; Singh & Choudhary 2017) The least-contributory features were gender and residence type, so these two features were excluded from the dataset. Age, BMI, average glucose level, smoking status, cardiac disease, and other characteristics represent the independent features, whereas the dependent feature is simply stroke.

![](bbox=[0.22, 0.523, 0.875, 0.856])

FIGURE 9.4 Correlation between different attributes of the extracted dataset.