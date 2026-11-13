There are 3 parameters in the implementation of the Q-learning algorithm:

+   - \(\eta\), which is the learning rate in the updating Equation (16.8). In *ReinforcementLearning*, this is coded as alpha;

+   - \(\gamma\), the discounting rate for the rewards (also shown in Equation (16.8));

+   - and \(\epsilon\), which controls the rate of exploration versus exploitation (see Equation (16.10)).

```
```r
control <- list(alpha = 0.1,
                gamma = 0.7,
                epsilon = 0.1)

fit_RL <- ReinforcementLearning(data_RL,
                                s = "state",
                                a = "action",
                                r = "reward",
                                s_new = "new_state",
                                control = control)

print(fit_RL)  # Show the output
```
```

```
```
## State-Action function Q
##       0.25        0         1      0.75       0.5
## neg 0.2473169 0.4216894 0.1509653 0.1734538 0.229004
## pos 1.0721669 0.7561417 1.4739050 1.1214795 1.045047
##
## Policy
## neg pos
## "0" "1"
##
## Reward (last iteration)
## [1] 2588.659
```
```

The output shows the Q function, which depends naturally both on states and actions. When the state is negative, large risky positions (action equal to 0.75 or 1.00) are associated with the smallest average rewards, whereas small positions yield the highest average rewards. When the state is positive, the average rewards are the highest for the largest allocations. The rewards in both cases are almost a monotonic function of the proportion invested in the risky asset. Thus, the recommendation of the algorithm (i.e., the policy) is to be fully invested in a positive state and to refrain from investing in a negative state. Given the positive autocorrelation of the underlying process, this does make sense.

Basically, the algorithm has simply learned that positive (*resp.* negative) returns are more likely to follow positive (*resp.* negative) returns. While this is somewhat reassuring, it is by no means impressive, and much simpler tools would yield similar conclusions and guidance.

# 16.4.2 Q-learning with market data

The second application is based on the financial dataset. To reduce the dimensionality of the problem, we will assume that:

+   - only one feature (price-to-book ratio) captures the state of the environment. This feature is processed so that is has only a limited number of possible values;

+   - actions take values over a discrete set consisting of three positions: +1 (buy the market), -1 (sell the market) and 0 (hold no risky positions);

+   - only two assets are traded: those with stock_id equal to 3 and 4 - they both have 245 days of trading data.