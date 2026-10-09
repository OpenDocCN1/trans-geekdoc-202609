
### Comparing and Plotting Actual and Predicted Values

The script below performs the following:

- Loads test data from a CSV file containing stock price data
- Preprocesses the data by scaling the features using the `preprocess_data` function imported from the `tesla_stock_price_prediction` module
- Defines a neural network model architecture using PyTorch
- Loads pre-trained model weights from a file
- Makes predictions on the preprocessed test data using the loaded model
- Prints the top ten actual and predicted stock prices side by side
- Plots all actual and predicted values on a line chart for visualization

```python
import torch
import numpy as np
import matplotlib.pyplot as plt
from tesla_stock_price_prediction import (
    load_data,
    preprocess_data
)
```

```python
def main():
    """
    Load test data, preprocess it, and make predictions
    using a pre-trained model.
    
    This function loads test data from a CSV file,
    preprocesses it, loads a pre-trained PyTorch model,
    makes predictions on the test data, and visualizes
    the actual vs. predicted stock prices.
    """
    test_data_file_path = \
        "/home/ubuntu/airflow/dags/TSLA_stock.csv"
    test_data = load_data(test_data_file_path)
    test_data = preprocess_data(test_data)
    
    test_features = \
        test_data.select('scaled_features').collect()
    
    test_features = np.array([
        row.scaled_features.toArray()
        for row in test_features
    ],
        dtype=np.float64)
    
    input_size = 4
    output_size = 1
    model = torch.nn.Sequential(
        torch.nn.Linear(input_size, 64),
        torch.nn.ReLU(),
        torch.nn.Linear(64, 32),
        torch.nn.ReLU(),
        torch.nn.Linear(32, 16),
        torch.nn.ReLU(),
        torch.nn.Linear(16, output_size)
    )
    model.load_state_dict(
        torch.load(
            '/home/ubuntu/airflow/dags/trained_model.pth',
            map_location=torch.device('cpu')
        )
    )
    model.eval()
    test_features_tensor = torch.tensor(
        test_features,
        dtype=torch.float64
    )
    model = model.double()
    with torch.no_grad():
        predictions = model(
            test_features_tensor
        ).squeeze().numpy()
    actual_labels = test_data.select('Close').collect()
    actual_labels = np.array(
        [
            row.Close for row in actual_labels
        ],
        dtype=np.float64
    )
    
    actual_labels = actual_labels[:-1]
    predictions = predictions[:-1]

    print("Top 10 Actual vs Predicted Values:")
    print("Actual\tPredicted")
    for i in range(10):
        print(f"{actual_labels[i]:.4f}\t{predictions[i]:.4f}")

    plt.figure(figsize=(10, 6))
    plt.plot(actual_labels, label='Actual')
    plt.plot(predictions, label='Predicted')
    plt.xlabel('Index')
    plt.ylabel('Price')
    plt.title(
        'Actual vs Predicted Tesla Stock Prices\n(Feb 26, 2019 to Feb 23, 2024)'
    )
    plt.legend()
    plt.grid(True)
    plt.show()

if __name__ == "__main__":
    main()
```

## Summary

In this chapter, we began our exploration of deep learning using PyTorch. Our focus was on regression, a fundamental task in machine learning aimed at predicting continuous numerical values. We discussed the advantages of deep learning for regression, such as its ability to capture complex patterns and relationships in data, particularly useful for datasets with nonlinearities and interactions. However, we also acknowledged the black-box nature of these models, which can make interpretation difficult. More importantly, we highlighted the computational intensity of deep learning algorithms, a challenge that can be mitigated by using Amazon Web Services (AWS) as a solution for scalable cloud computing infrastructure, essential for deploying and running deep learning models efficiently.

We demonstrated PyTorch’s application for regression by building and evaluating a neural network to predict Tesla stock prices, showing strong performance with low MSE and high R-squared score. Additionally, we briefly discussed early stopping and overfitting, topics we will explore further in Chapter 9.

In the next chapter, we will demonstrate how to follow similar steps using TensorFlow, mirroring the process employed with PyTorch. We will utilize the same Tesla stock dataset for model comparison, allowing for a direct evaluation of the performance and characteristics of models implemented in both frameworks.

# CHAPTER 5

# Deep Learning with TensorFlow for Regression

In the previous chapter, we began our journey of exploring deep learning models for regression tasks. We trained and evaluated a PyTorch model and used it to predict Tesla’s daily stock prices. In this chapter, we demonstrate how to replicate that same process with TensorFlow. We’ll use the same dataset to directly compare the performance of models in both frameworks. Additionally, we will leverage the distributed computing capabilities of PySpark to preprocess this dataset.

It’s worth noting that the advantages and disadvantages of deep learning algorithms, compared with traditional predictive models like linear regression, as discussed in the previous chapter, remain relevant in the current chapter.

The chapter begins with a reminder of what the Tesla stock dataset looks like, followed by the construction, training, and evaluation of the TensorFlow regression model. It then brings everything together by combining the code snippets discussed throughout the chapter before concluding with a summary of the key takeaways.

## The Dataset

We will use the same daily historical dataset of Tesla stock obtained from Yahoo! Finance. This dataset was downloaded in CSV format and then stored on Amazon Web Services (AWS) S3 within a bucket named “instance1bucket” from the following link:

<https://finance.yahoo.com/quote/TSLA/history/>

We explored this dataset in great detail in Chapter 3 and used it to train and evaluate a PyTorch deep learning regression model in Chapter 4. As a reminder, below are the top five observations from the dataset:

| Date | Open | High | Low | Close | Volume |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 2/23/24 | 195.31 | 197.57 | 191.50 | 191.97 | 78670300 |
| 2/22/24 | 194.00 | 198.32 | 191.36 | 197.41 | 92739500 |
| 2/21/24 | 193.36 | 199.44 | 191.95 | 194.77 | 103844000 |
| 2/20/24 | 196.13 | 198.60 | 189.13 | 193.76 | 104545800 |
| 2/16/24 | 202.06 | 203.17 | 197.40 | 199.95 | 111173600 |

This dataset spans from February 26, 2019, to February 23, 2024, encompassing 1,258 observations. Each trading day records real-time fluctuations in Tesla stock price. These observations provide insight into key indicators—Open, High, Low, Close, and Volume—depicting price movements over a specific timeframe.

Here are their definitions:

- **Open**: The opening price of Tesla stock on the given date
- **High**: The highest price of Tesla stock reached during the trading session on the given date
