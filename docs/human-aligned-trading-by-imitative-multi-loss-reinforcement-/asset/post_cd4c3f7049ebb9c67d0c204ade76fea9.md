
loss, supervised classification loss on three-class actions (buy/sell/hold) over 1-step and n-step, respectively. During the pre-training, the loss function is: L_joint = ω1 Lp + ωn Lp^(n) + ωs Ls + ωs Ls^(n), (7)

whereas during regular training, the loss function is: L_joint = ω1 L + ωn L^(n) + ωs Ls + ωs Ls^(n), (8)

where the network parameter θt is omitted from the formulae for simplicity, Lp and Lp^(n) are 1-step and n-step Q-value losses at pre-training, L and L^(n) are 1-step and n-step Q-value losses during regular training, Ls and Ls^(n) are supervised losses on 1-step and n-step actions, and ω1, ωn, ωs and ωs^(n) are the weightings for 1-step Q loss, n-step Q loss, and supervised loss (for both 1-step and n-step). Since L (and Lp) is effectively the vanilla DQN loss, we set ω1 to be always 1.

Being able to pre-train the trading agent with demonstration data is crucial. It is also equally critical that we are able to combine the supervised loss with the Q-learning loss for the pre-training to be effective. This is because the supervised loss grounds the values of agent actions to reasonable values and makes the greedy state-action mapping induced by the network imitate the demonstrator, whereas the Q loss constrains the values between consecutive states and ensures that the network satisfies the Bellman equation and has a suitable starting point for temporal difference learning that follows.

## 4. Trading setup

A high level model architecture and data flow are presented in Fig. 2. After being put through DWT filtering, the time series stock data feeds into an LSTM network which is a kind of recurrent neural network capable of learning long term dependencies without suffering from the vanishing gradient problem (Hochreiter & Schmidhuber, 1997). While more advanced sequence handling models such as the Transformer (Vaswani et al., 2017) could be used in place of LSTM, we would like to focus this research on Reinforcement Learning, but will visit the possibility of integrating with Transformer in later studies.

We permit short selling in our setup meaning that the agent may gain if it chooses to sell a borrowed stock against a falling price. Trading cost is accounted for in each action in the form of bid/ask spread s. Having reviewed the real historical tick data of the chosen stocks over the months of interest, we have chosen an average percentage of 0.02% of the mid price as the spread between a bid and an ask price. No separate trading fee is included which reflects the new norm that brokerages nowadays offer commission-free stock trading services. Only mid prices are used in the time series data.

![](img/5df77e9474116b71217f79f02a02a4ee_4_0.png)

Fig. 2. Flow of data through the model architecture.

The trading agent is allowed to perform one of three actions at any time a_t ∈ {buy, hold, sell} = {−1,0,1}, and it transacts one unit of stock by each action. Assuming a trading action has happened at time t−1, the trading profit is calculated from time t−1 to t as in formula (9): profit_t = a_{t−1}(p_t − p_{t−1}) − s. (9)

The cumulative trading return CTR over T time steps is calculated as in formula (10): CTR_{T} = ∏_{i=1}^{T} (a_{i−1}(p_i − p_{i−1}) − s)/p_{i−1} − 1. (10)

We found that, many similar research works make the assumption that the trading reward between two time steps always follows formula (9) or something similar, while in reality, such an assumption is too simplistic (Carta et al., 2021; Deng et al., 2017; Li et al., 2018; Liu et al., 2020; Tsantekidis et al., 2021). To better test our model’s alignment to a human trader, we put in place a rewarding scheme which is realistic and more importantly considers the present state of stock holding, i.e., long (owning stock), no holding, or short (in a short-selling state).

We also try to make the backtesting setup realistic. Since the trading days are non-continuous, we believe that it would be unreasonable to train/trade on a stock time series data with no regard that there were time gaps between data from different days as is often seen (Li et al., 2019), especially when market events can happen overnight. Also, a full day’s new data becomes available after market closes which we believe ought to be captured before the market opens the next day.

We sequentially divide the data in each training window into n episodes. We choose each episode’s length to be the same as the length of the testing window which is 500 in this case. We iteratively carry out 100 rounds of episodic training, and we choose the first 20% of total episodes as the expert data for pre-training. Cumulative trading gain in percentage terms is computed as our performance metric.

![](img/5df77e9474116b71217f79f02a02a4ee_5_0.png)

Fig. 3. This diagram breaks down the various cases of transaction going from time t-1 to t. r_{t-1:t} is the realised PnL (profit and loss) of the trading agent only from t-1 to t. Since we only permit the trading agent to possess or transact one share at a time, the implications of this diagram are: (1). A buy or sell signal while being already Long or Short a share does not change the state of share holding. This refers to case 1 and 7. (2). A Sell signal while being Long simply disposes of a currently-owned share. A Buy signal while being short a stock closes the short position by buying back a share from the market. In both cases, the trading action at t-1 is realising a profit/loss with respect to the initial price of transaction which happened before t-1. This refers to case 2 and 6. (3). A Sell signal while having no holding triggers a short-selling action. This refers to case 5. Note that s is the bid/ask spread which is regarded as the cost of trading incurred in each transaction.

## 5. Experiments, results, and analysis

In this section, we provide a detailed view on how we construct our environments, set up, and conduct the experiments, followed by assumptions and rationales, experimental results, and our analyses.

### 5.1. Data and trading environment

We choose 10 stocks representative of different industrial sectors and liquidity levels for diversity reasons: blue chip stocks of Apple (AAPL), Netflix (NFLX), Costco (COST), JPMorgan (JPM), Disney (DIS) as well as small cap stocks of Stitch Fix (SFIX), InVitae (NVTA), Novavax (NVAX), Sunrun (RUN), and Digital Turbine (APPS). Minute tick data is sourced from the Investors Exchange which is a national US stock exchange which provides reliable real historical stock trading data. The same data that we have chosen to use is easily obtainable from the exchange for benchmarking purposes. 390 min data points are available on each trading day for each stock and linear interpolation/extrapolation are employed to fill those time points without a price data due to lack of trading activity.

20-period Bollinger Band oscillator signal. Three manually enhanced signals are also used: a moving average trend signal, a moving average golden cross signal, and a break out signal, the value of all of which are evaluated not just on the current time point t, but over a period of three time points prior to t. Together with the normalised and filtered time series data, they form the trading environment of our experiments (Ni, Day, Cheng, & Huang, 2022).

### 5.2. Experimental results and analysis

To evaluate the performance of our model we have chosen the following baseline models for comparison, all of which are run through the exact training and testing windows.

- Supervised Learning with the same network A trading agent driven by supervised learning that uses the same internal network in HAT is an important benchmark to compare against. It uses the network architecture as presented in Fig. 2 including the input layers and an LSTM component, except that only one output layer is required to produce softmax cross entropy loss on the 1-step action. Trading is driven entirely based on the predicted buy/sell/hold 1-step actions.
- Vanilla DQN The first RL baseline model is a vanilla DQN model as created by Mnih et al. (2015) which uses a normal Experience Replay. The internal network architecture is made to be the same as the benchmark supervised learning network.
- Prioritised Double DQN (PDDQN) We apply Double Q-learning (Hasselt, 2010) and PER (Schaul et al., 2016) as additional features to the vanilla DQN to bring this benchmark model closer to our own model. Double Q-learning was shown in Hasselt, Guez, and Silver (2016) to have remedied the problem of overestimated action values. This benchmark model also shares the same network architecture as other ones.
- Multi-Step DQN (MSDQN) Multi-step Q-learning (Peng & Williams, 1998) is added as an extension to the vanilla DQN. This model again shares the same underlying network architecture as other baseline models.
- DQfD The model of Deep Q-learning from Demonstrations (DQfD) (Hester et al., 2018) is the closest model to our design which also features the pre-training concept as well as using multi-step learning and a supervised loss function. The key difference is that DQfD's supervised loss is based on 1-step actions only and it is not using separate PER buffers like we do for 1-step and n-step instances. DQfD also has a different joint loss function profile compared to HAT and all losses are equally weighted.
- Buy-and-Hold (BnH) There is no modelling involved and the cumulative trading return is calculated by Eq. (10) on a daily basis using historical stock price data assuming that a share is bought at the beginning and held to the end of the trading day.

### 5.3. Performance evaluation

All models are trained using the same training set and tested over the three 7-day rolling windows on each of the ten stocks. Each round of testing exercises are carried out 50 times and the daily intraday cumulative trading returns are calculated as the average of the 50 test rounds. A summary is provided in Table 1 which presents the mean daily intra-day trading returns by HAT and the benchmark models/methods, averaged over each 7-day window. It is evident that the HAT consistently performs better than all baseline models, both in terms of higher mean returns and lower return variances.
