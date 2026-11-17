# Proposed Algorithm for Composite-LSTM

Results: The accuracy of the earthquake prediction is done by using the Mean Squared Error(MSE) and R-squared (R2) scores

Input: The dataset is about the seismic earthquake data of South America ,collected from NOAA(National oceanic and atmospheric Administration).

Output:Predict magnitude values

Procedure:

+   Step 1:Loading a earthquake data from a csv file into a pandas data frame named ‘df’
+   1.1:Random sampling and mean imputation functions are implemented to handle the missing values.
+   Step 2:Preprocessing Data
+   2.1: Using one-hot encoding to encode categorical variables
+   2.2: Dividing the data into sets for testing and training.
+   2.3: Robust Scaler from scikit-learn is used to scale numerical features.
+   Step 3: Dividing the preprocessed data (df) into the first and second halves, respectively
+   Step 4: Building LSTM model
+   4.1: Constructing two LSTM models, one for the first half of the dataset and one for the second.
+   Step 5:Defining input layers and connecting models
+   5.1: Defining the input layers for each of the two datasets
+   5.2: Connecting each LSTM model's input layers to it.
+   5.3:Joining the two LSTM model's outputs together.
+   Step 6:Assembling the parallel LSTM model using the Adam optimizer and mean square errorloss
+   Step 7: Trimming Sequences and Training the Model:
+   7.1: Reshaping and trimming the sequences to the anticipated duration for training.
+   7.2: Using the first half of the dataset, train the parallel LSTM model.
+   Step 8: Evaluating the Model
+   8.1:Reshaping and trimming the test sequences to the anticipated length in order to assess them.
+   8.2: Assessing the model's performance with metrics such as R2 score and mean squared error.

Figure 15.1 Algorithm for the proposed model composite LSTM.