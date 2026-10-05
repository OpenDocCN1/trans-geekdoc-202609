resource-intensive.

# AI assistance de and workflow

To streamline forecasting and improve accuracy, the team leveraged a suite of AI-assisted tools:

+   * **ChatGPT**: ChatGPT provided strategic guidance to enhance time series preprocessing and model selection, helping overcome forecasting challenges through the following recommendations:
    * Advised on performing time series decomposition, trend detection, and stationarity checks using tools like ADF and STL.
    * Suggested pre-transforming data with differencing, log transforms, and rolling averages to improve model stability.
    * Prophet is recommended for interpretable seasonality, and LSTM is recommended for long-sequence modeling.
* **GitHub Copilot**: GitHub Copilot streamlined the implementation process by generating robust, production-ready code templates for advanced time series modeling, including the following components:
    * Generated complete code templates for:
        * **Rolling-window LSTM architectures** with dropout and batch normalization.
        * Multivariate time series inputs and timestamp encoding.
        * Training pipelines with early stopping and sequence padding.
* **Optuna**: Optuna played a key role in automating hyperparameter optimization, enhancing model performance and scalability through the following