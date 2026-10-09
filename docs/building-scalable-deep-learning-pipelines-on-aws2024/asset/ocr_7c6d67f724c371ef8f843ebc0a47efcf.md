In the next step, we transition to the main function, which orchestrates the entire workflow. This function, situated outside the TSLARegressor class, instantiates a TSLARegressor object and then calls methods to preprocess data, convert data to NumPy arrays, create and train the model, and evaluate the model. It also logs the test loss and R2 score and plots the training loss over epochs using Matplotlib:

```
[In]: def main(file_path):
        """
        Main function to orchestrate the entire workflow.

        Parameters:
            - file_path (str): Path to the CSV file.

        Returns:
            - None
        """
        try:
            tsla_regressor = TSLARegressor()
            train_df, test_df = tsla_regressor.
            preprocess_data(
                file_path
            )
            train_features, train_labels, test_features, \ test_labels = tsla_regressor.convert_to_numpy(
                train_df,
                test_df
            )
            history = tsla_regressor.create_and_train_model(
                train_features,
                train_labels
            )
```