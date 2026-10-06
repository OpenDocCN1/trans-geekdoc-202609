
# Machine Learning: Concepts, Tools and Data Visualization

![](img/3c3c87d78136583581b0cf0620f5ae66_108_0.png)

| | |
| --- | --- |
| Mean | 5.8338 |
| Median | 5.8 |
| Min | 4.3 |
| Max | 7.9 |
| Standard Deviation | 0.8336 |
| Unique Values | 35 |
| Missing Values | 0 |
| Feature Type | Numeric Feature |

Figure 6-33 Statistics through data visualization

Also, you can check the statistics and histogram of the selected attribute shown in Figure 6-33.

## 6.3.3 Data Preprocessing

Once you have inserted the experimental data and confirmed through visualization, you should delete missing or unnecessary values. It is important to preprocess the data set before designing the experiment. Therefore, it is necessary to deal with missing values before applying the machine learning algorithm.

For the preprocessing practice, the row missing an attribute for “Species” was added, as shown in Figure 6-34. If the species value is missing, we should delete all the rows.

Import the “Select Columns in Dataset” block from the palette and include all the columns, as shown in Figure 6-35, using “Launch column selector”.

# Create Prediction Model using Microsoft Azure Machine Learning Studio

![](img/3c3c87d78136583581b0cf0620f5ae66_109_0.png)

Figure 6-34 Missing value

![](img/3c3c87d78136583581b0cf0620f5ae66_109_1.png)

Figure 6-35 Select Columns in Dataset to Inspect Missing Data

Machine Learning: Concepts, Tools and Data Visualization

Import the "Clean Missing Data" block from the palette and set the cleaning mode to "Remove entire row", as shown in Figure 6-36.

After clicking the "Run" button and completing execution, right-click the "Clean Missing Data" block, as shown in Figure 6-37, and check the preprocessed data hovering over the "Cleaned Dataset" item. Then, click "Visualize".

![](img/3c3c87d78136583581b0cf0620f5ae66_110_0.png)

Figure 6-36 Missing data preprocessing using "Clean Missing Data"

![](img/3c3c87d78136583581b0cf0620f5ae66_110_1.png)

Figure 6-37 Preprocessed data visualization

![](img/3c3c87d78136583581b0cf0620f5ae66_111_0.png)

As shown in Figure 6-38, if a value in the “Species” attribute is missing, confirm that the row has been deleted.

### 6.3.4 Feature Definition

Once you have dealt with missing values in the data, use the “Select Columns” in the “Dataset” block to select the attribute values in the data set in order to apply the algorithm. Of course, “Select Columns in Dataset” was used when preprocessing, but here it is used to select attribute values in order to implement the algorithm.

Place the “Select Columns in Dataset” block in the palette and include the Petal.Length, Petal.Width, and Species property values to apply the algorithm through the Launch Column Selector, as shown in Figure 6-39. It is up to the data scientist to find the attribute values to implement the algorithm.

## 6.3.5 Machine Learning Algorithm Selection and Implementation

Once you have selected the attribute values to apply to the machine learning algorithm, you need to split the training and test data from the entire data set, and then select and implement the appropriate machine learning algorithm.

Place a “Split” block in the navigation palette, as shown in Figure 6-40, and use 70% as training data.

Let’s import the Multiclass Decision Forest from the palette onto the canvas, place it, and then take a look at the Properties window. The algorithm to implement is the Multiclass Decision Forest. The Properties window makes it easy to modify parameters of an algorithm. Proceed to the default value, as shown in Figure 6-41.

![](img/3c3c87d78136583581b0cf0620f5ae66_112_0.png)

Create Prediction Model using Microsoft Azure Machine Learning

![](img/3c3c87d78136583581b0cf0620f5ae66_113_0.png)

Figure 6-40 Data split

![](img/3c3c87d78136583581b0cf0620f5ae66_113_1.png)

Figure 6-41 Property of Multiclass Decision Forest

Machine Learning: Concepts, Tools and Data Visualization

![](img/3c3c87d78136583581b0cf0620f5ae66_114_0.png)

Figure 6-42 selection for training

Place the Train Model block in the navigation palette as shown in Figure 6-42, select the Species that you want via the Launch Column Selector, connect as follows, and click the “Run” button to train. Once the training is complete, right-click on the Train Model block and click the “Visualize” button on the Trained model item to see the results. Figure 6-43 shows trained results.

Create Prediction Model using Microsoft Azure Machine Learning Studio

![](img/3c3c87d78136583581b0cf0620f5ae66_115_0.png)

![](img/3c3c87d78136583581b0cf0620f5ae66_115_1.png)

Figure 6-43 Trained results

Machine Learning: Concepts, Tools and Data Visualization

![](img/3c3c87d78136583581b0cf0620f5ae66_116_0.png)

(c) Trained Tree 3

![](img/3c3c87d78136583581b0cf0620f5ae66_116_1.png)

(d) Trained Tree 4

Figure 6-43 (Continued)

![](img/3c3c87d78136583581b0cf0620f5ae66_117_0.png)

![](img/3c3c87d78136583581b0cf0620f5ae66_117_1.png)

Figure 6-43 (Continued)

![](img/3c3c87d78136583581b0cf0620f5ae66_118_0.png)

![](img/3c3c87d78136583581b0cf0620f5ae66_118_1.png)

Figure 6-43 (Continued)

## 6.3.6 Predicting with New Data

Since the model has completed training, the remaining 30% of the test data can be applied to the trained model to evaluate how well it predicts.

Create Prediction Model using Microsoft Machine Learning Studio

![](img/3c3c87d78136583581b0cf0620f5ae66_119_0.png)

Figure 6-44 Arrangement for prediction model

Place the Score Model, as shown in Figure 6-44, connect the Train Model block and the Split Block, and click the Run button to train. Let's check the types of irises predicted through visualization and the types of irises stored in the test data.

As shown in Figure 6-45, you can see that 30% of the test data has been applied to the prediction model.

To see the evaluation of the prediction results, add an “Evaluate Model” block to the canvas, and associate it with the “Train Model” block, as shown in Figure 6-46. Then press the “Run” button to run it. When it is done, check the results of the model evaluation with “Visualize”.

Machine Learning: Concepts, Tools and Data Visualization

![](img/3c3c87d78136583581b0cf0620f5ae66_120_0.png)

Figure 6-45 Predicted value

![](img/3c3c87d78136583581b0cf0620f5ae66_120_1.png)

Figure 6-46 Arrangement for prediction model evaluation

Create Prediction Model using Microsoft Azure Machine Learning

As shown in Figure 6-47, the prediction model evaluation results show the accuracy, average precision, and average recall.

As shown in Figure 6-48, you can see the visualization by comparing the actual data with the predicted data.

+   Metrics
* Overall accuracy 0.977778
* Average accuracy 0.985185
* Micro-averaged precision 0.977778
* Macro-averaged precision 0.979167
* Micro-averaged recall 0.977778
* Macro-averaged recall 0.977778

Figure 6-47 Prediction model evaluation results

![](img/3c3c87d78136583581b0cf0620f5ae66_121_0.png)

+   Confusion Matrix

Figure 6-48 Visualization of prediction result

## 6.4 Practice Questions

Q1. Describe the process of creating a Prediction Model in Azure Machine Learning Studio

Q2. Describe the ROC (Receiver Operating Characteristic) Curve for model evaluation.

Q3. Describe the Accuracy, Precision, Recall, and F1 Scores for model evaluation.

# Chapter 7

## Create Prediction Models using Microsoft Azure Machine Learning Studio Web Service Deployment

### 7.1 Create Prediction Models using Azure Machine Learning Studio Web Service Deployment Tutorial

Figure 7-1 shows the completion of the prediction model tutorial and suggests building a web service to use the prediction model remotely. Click the “Show Me” button to go through the tutorial to deploy the web service.

![](img/3c3c87d78136583581b0cf0620f5ae66_123_0.png)

**Figure 7-1** Web service deployment tutorial
