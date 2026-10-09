The R-squared score is computed using the formula

```
[In]: r_squared = 1 - ss_res / ss_tot
```

where ss_res is the sum of squares of residuals (differences between predictions and targets) and ss_tot is the total sum of squares.

The logger.info logs the test loss and R-squared score to provide insights into the model's performance on the test dataset. These metrics help in assessing the model's predictive capabilities and identifying areas for improvement.

# Step 8: Main Function (main)

In this step, we'll discuss the main function, which serves as the entry point for executing the code:

```
[In]: def main(
    data_file_path: str,
    num_epochs: int = 100,
    batch_size: int = 32,
    learning_rate: float = 0.001
):
    """
    Main function for training and evaluating a deep
    learning
    model for Tesla stock price prediction.

    Args:
        data_file_path (str): The path to the CSV file
        containing stock price data.
        num_epochs (int): The number of epochs for
        training the
        model. Defaults to 100.
        batch_size (int): The batch size for data
        loading during
        training. Defaults to 32.
```