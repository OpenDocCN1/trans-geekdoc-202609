# CHAPTER 3 DATA PREPARATION WITH PYS PARK FOR DEEP LEARNING

Below is an explanation of each new column in the table:

+   • price_range: Represents the difference between High and Low prices
    • price_change: Represents the difference between Close and Open prices
    • volume_price_interaction: Represents the product of Volume and Close prices

Let's break down how each of these new columns was generated, using data for 2/23/24:

Price Range:

+   • 197.57−191.50=6.07

Price Change:

+   • 191.97−195.31=−3.34

Volume−Price Interaction:

+   • 78,670,300×191.97=15,102,337,569.07

Each of these engineered features can provide valuable information that may enhance the predictive performance of a model for forecasting Tesla stock prices:

+   • The price range can provide insights into the volatility of the stock. High price ranges may indicate periods of market uncertainty or significant price fluctuations, while low price ranges may suggest relative stability. Incorporating this feature allows the model to capture the magnitude of price movements, which can be valuable for predicting future price changes.