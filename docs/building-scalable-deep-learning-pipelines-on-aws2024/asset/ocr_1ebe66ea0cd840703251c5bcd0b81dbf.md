# Predicting Diabetes with PyTorch

In this section, we build, train, and evaluate a neural network model and use it to predict the likelihood of a Pima Indian woman having diabetes using the dataset we have just explored. We use six features: number of pregnancies, blood pressure, BMI, glucose level, diabetes pedigree function, and age. These features are important factors in predicting the presence of diabetes.

We leverage the distributed computing capabilities of Spark for data preprocessing and PyTorch for developing the deep learning model. The code has been organized into the following steps:

+   1. Data Preprocessing:
	    - Load the diabetes dataset from a CSV file on AWS S3 using Spark.
	    - Filter out invalid records in specific columns (Glucose, BloodPressure, BMI).
	    - Assemble feature columns into a single vector using VectorAssembler.
	    - Scale the assembled features using StandardScaler.
	    - Split the preprocessed data into training and testing datasets.

+   2. Model Definition:
	    - Define the architecture of the neural network model for diabetes classification using PyTorch. The model consists of multiple fully connected layers with ReLU activation functions.