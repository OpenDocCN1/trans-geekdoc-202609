# Applied Intelligent Decision in Machine Learning

![](bbox=[0.118, 0.091, 0.843, 0.258])

(a)

![](bbox=[0.118, 0.292, 0.843, 0.459])

(b)

![](bbox=[0.318, 0.494, 0.683, 0.661])

(c)

**Figure 10.2** Exchange rate prediction graph of training and testing phase of LSTM model and GRU model for five currencies with different sliding window (WS): **(a)** five-days-ahead prediction of AUD with WS 10; **(b)** three-days-ahead prediction of CAD with WS 7; **(c)** seven-days-ahead prediction of GBP with WS 10; **(d)** ten-days-ahead prediction of INR with WS 13; and **(e)** one-day-ahead prediction of JPY for WS 7.

(e)

# 10.2 For Sliding Window Size 10

Tables 10.6-10 show the results for sliding window size 10. For AUD, CAD, and JPY daily forex, GRU gives better results; for the INR dataset, LSTM gives better results. When the samples have a long-term dependency problem, the LSTM model outperforms GRU, because it has more features and a more complex architecture than GRU.