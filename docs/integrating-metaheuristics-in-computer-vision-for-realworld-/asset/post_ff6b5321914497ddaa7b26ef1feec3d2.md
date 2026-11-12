

Furthermore, advances in technologies like Internet of things, Wireless sensor networks and computer vision can be used to develop newer multi domain solutions [12–18].

## 9.3 Proposed Framework

In this project, machine learning algorithms will be used to predict the existence of exoplanets and to classify the type of exoplanets. Exoplanet prediction and classification are important areas of study, as they have the potential to significantly advance our understanding of these celestial bodies and their role in the universe. A variety of machine learning algorithms will be employed, including support vector machines, logistic regression, k-nearest neighbors, random forest, and extreme gradient boosting. The performance of these algorithms will be evaluated using a range of metrics, including accuracy, precision, and recall. A confusion matrix and a feature importance plot will also be used to provide a more detailed analysis of the performance of the algorithms and to understand which features or variables are most influential in making predictions. A detailed framework for dataset 1 is shown in Figure 9.4.

The steps involved for predicting exoplanets using machine learning are:

- 1. Data collection: In order to train your machine learning model, you must first collect a dataset of exoplanet observations. The mass, radius, and orbital properties of the exoplanets, as well as any other significant variables that could be helpful for prediction, should all be included in this dataset.

- 2. Data preprocessing: Preparing the data for machine learning requires preprocessing the data after you get your dataset. This might involve addressing missing or incomplete values, scaling the features, and cleaning and formatting the data.

- 3. Exploratory Data Analysis (EDA): Before creating a machine learning model, it is often beneficial to carry out EDA in order to comprehend the dataset's properties and spot any trends or patterns that could be important for prediction. This might involve investigating the connections between various attributes and the target variable (exoplanet presence) as well as showing the distribution of various features and determining their correlations.

- 4. Data balancing: If the classes in your dataset are imbalanced, you may want to use techniques such as SMOTE to balance the classes. This involves synthesizing new examples of the minority class to better match the distribution of the majority class.

- 5. Model selection: Select a machine learning model to employ for prediction. Models come in a wide variety, with decision tree, support vector machine, neural networks and random forest among the options.

- 6. Model training: Model training involves fitting the selected model to the dataset, then tuning the model's parameters to maximize performance.

![](img/07f0bb0f402fd4e2f1880bf37d1ea963_183_0.png)

Figure 9.4 Proposed framework for dataset 1.

- 7. Model evaluation: Analyze the model’s performance to determine its accuracy in predicting exoplanets. This may involve utilizing performance indicators like accuracy, precision, and recall or contrasting the model’s predictions with actual exoplanet observations.

The entire framework for the first and second Datasets is same. But for the second dataset, which is from NASA’s KOI catalog, an additional column is added to determine the type of each exoplanet as it is not included in the KOI table. The framework for the second dataset is shown in Figure 9.5.

![](img/07f0bb0f402fd4e2f1880bf37d1ea963_184_0.png)

Figure 9.5 Proposed framework for dataset 2.

## 9.4 Results

A graph that depicts the varying brightness of a star or other celestial object over time is called a light curve plot. The x-axis is often used to indicate time, while the y-axis is used to depict the brightness of the star. Since there are patterns and characteristics evident in the plot, such as periodic brightness dips that may be caused by an exoplanet transiting the star, the light curve can be used to explain any of these patterns or features. Insights or conclusions that may be derived from the light curve plot are also described using them.

Light curves of stars 1 and 3 are shown in the plots below (see Figures 9.6 and 9.7). These light curves clearly show that there are celestial bodies rotating around these stars. Periodic dips in these light curves can be seen, which suggests that an exoplanet is orbiting around it.

The light curves for stars 101 and 102 are shown below (see Figures 9.8 and 9.9). It is apparent from these light curves that they do not show any periodic dips, proving that neither star 101 nor star 102 host any extrasolar planets. These light curves may exhibit erratic dips, but they might also be the result of other disruptions or astronomical phenomenon.

![](img/07f0bb0f402fd4e2f1880bf37d1ea963_185_0.png)

Figure 9.6 Light curve of exoplanet star 1.

![](img/07f0bb0f402fd4e2f1880bf37d1ea963_185_1.png)

Figure 9.7 Light curve of exoplanet star 3.

![](img/07f0bb0f402fd4e2f1880bf37d1ea963_185_2.png)

Figure 9.8 Light curve of non-exoplanet star 101.

![](img/07f0bb0f402fd4e2f1880bf37d1ea963_186_0.png)

Figure 9.9 Light curve of non-exoplanet star 102.

The depth of this dip in the light curve and the length of the transit can be used to estimate the size and orbit of the exoplanet. For instance, a bigger exoplanet will block more of the star’s light, causing the light curve to fall more deeply. Similar to this, a longer orbital period for an exoplanet means that it will take longer to transit the star, lengthening the duration of the drop in the light curve. It is possible to estimate the exoplanet’s size and orbital period by examining the peculiarities of the light curve’s dips.

Below are more insightful plots of the exoplanet-containing stars 0, 1, 2, and 3 (see Figure 9.10). These curves show all of the flux values from 0 to 3187, measured at regular intervals of time. It can be seen that these light curves have regular dips that point to the existence of exoplanets. The light curve of star 0 resembles a sine curve with dips that are broader rather than deeper, suggesting that the exoplanet orbiting the star may be smaller and farther away from the star. And for star 1, the dips are deeper and narrower, suggesting that the exoplanet orbiting the star may be relatively larger and closer to the star.

Below are detailed plots of the stars 230, 1090, 2247, and 3543, none of which have exoplanets (see Figure 9.11). It is evident that there are no periodic dips in these light curves. They may have occasional erratic dips as a result of other factors. As there are no periodic dips in any of the light curves, indicating that no exoplanets are orbiting around them.

A confusion matrix is a helpful tool for assessing how well a machine learning model performs in prediction of exoplanet. Several machine learning models are used to categorize exoplanets and non-exoplanets, including SVM, LR, KNN, DTC, RFC, and XGB classifier. These models’ confusion matrices are shown in Figs. 9.12 to 9.17. According to these confusion matrices, there are 3333 predictions in total. The SVM model has 1633 true positive predictions and 1699 true negative predictions. A total accuracy of 99% was the outcome. 1617 true positive predictions and 1654 true negative predictions are made by the logistic regression model with an accuracy 98%. The KNN model makes 1633 accurate predictions that are true positive, and 1637 accurate predictions that are true negative. And has an overall accuracy of 98%. Decision Tree classifier model also achieved an accuracy of 98% with 1625 true positive predictions and 1402 true negative predictions. 1632 true positive predictions and 1700 true negative predictions were made with the RandomForest Classifier model. A total accuracy of 99% was the outcome. Finally, The XGB classifier model yields an accuracy of 99% with 1687 true negative predictions compared to 1632 true positive predictions. These results reveal that all models are working effectively and can accurately anticipate the existence and characteristics of exoplanets.

