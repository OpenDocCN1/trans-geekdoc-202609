+   - In some epochs, there are minor differences in the loss values between PyTorch and TensorFlow, but overall, the trends are comparable.
	- Toward the end of training, both frameworks achieve low training loss values, indicating that the models have converged effectively.

Turning to test loss and R-squared score, we have the data below:

| Metric | PyTorch | TensorFlow |
| :--- | :--- | :--- |
| Test loss | 20.54 | 12.11 |
| R-squared | 0.998 | 0.998 |

The table shows that the test loss obtained from the PyTorch model is 20.54, while the TensorFlow model achieves a lower test loss of 12.11. Interestingly, both models exhibit an identical R-squared value of approximately 0.998, indicating an exceptionally high level of explanatory power and predictive accuracy in capturing the variance of the test data. Despite the difference in test loss, the comparable R-squared values suggest that both frameworks produce models with similar predictive performance in explaining the TSLA stock prices.

While this comparison is largely apples-to-apples, as we used the same Tesla stock dataset, there are practical differences in implementing the models in PyTorch and TensorFlow that extend beyond the data and model architecture. In TensorFlow, the use of a static computational graph requires that the model's structure be defined upfront. This approach allows TensorFlow to optimize the graph for performance, making it particularly well-suited for production environments where efficiency is critical. However, this static nature can make the development process