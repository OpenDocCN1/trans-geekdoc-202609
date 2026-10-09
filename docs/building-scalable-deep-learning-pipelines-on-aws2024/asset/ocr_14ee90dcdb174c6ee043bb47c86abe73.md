+   Then, it calls the `copy_file_from_s3` function to copy the file from the specified S3 bucket to the local file path.

Loading Data:

+   The function loads the data from the local file path (`local_file_path`) using the `load_data` function and assigns it to the DataFrame variable `df`.

Printing First Five Observations:

+   The function prints the first five observations of the DataFrame (`df`) using the `print_first_5_observations` function with a custom heading “First 5 observations:”.

Preprocessing Data:

+   The function preprocesses the loaded data by calling the `preprocess_data` function and assigns the preprocessed DataFrame back to `df`.

+   After preprocessing, it again prints the first five observations of the DataFrame with a custom heading “First 5 observations after scaling:”.

Converting Data to NumPy Arrays:

+   The function converts the Spark DataFrame columns containing scaled features and the ‘Close’ values to NumPy arrays (`df_features` and `df_labels`, respectively).

+   These arrays will be used as input features and labels for training the model.