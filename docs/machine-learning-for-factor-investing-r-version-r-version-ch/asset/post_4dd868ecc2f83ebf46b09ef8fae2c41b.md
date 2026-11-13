
The construction of the dataset is unelegantly coded below.

```
return_3 <- data_ml %>% filter(stock_id == 3) %>% pull(R1M.Usd) # Return of asset 3
return_4 <- data_ml %>% filter(stock_id == 4) %>% pull(R1M.Usd) # Return of asset 4
pb_3 <- data_ml %>% filter(stock_id == 3) %>% pull(Pb) # P/B ratio of asset 3
pb_4 <- data_ml %>% filter(stock_id == 4) %>% pull(Pb) # P/B ratio of asset 4
action_3 <- floor(runif(length(pb_3))*3) - 1 # Action for asset 3 (random)
action_4 <- floor(runif(length(pb_4))*3) - 1 # Action for asset 4 (random)

RL_data <- tibble(return_3, return_4, # Building the dataset
                  pb_3, pb_4,
                  action_3, action_4) %>% # Uniting actions
  mutate(action = paste(action_3, action_4), # Simplifying states (P/B)
         pb_3 = round(5 * pb_3), # Simplifying states (P/B)
         pb_4 = round(5 * pb_4), # Simplifying states (P/B)
         state = paste(pb_3, pb_4), # Uniting states
         reward = action_3*return_3 + action_4*return_4, # Computing rewards
         new_state = lead(state)) %>% # Infer new state
  dplyr::select(-pb_3, -pb_4, -action_3, # Remove superfluous vars.
                -action_4, -return_3, -return_4)
head(RL_data) # Showing the result
```

```
## # A tibble: 6 x 4
##   action state reward new_state
##   <chr> <chr> <dbl> <chr>
## 1 1 -1 -1 1 1 -0.061 1 1
## 2 0 1 1 1 0 1 1
## 3 3 -1 0 1 1 -0.018 1 1
## 4 4 0 -1 1 1 0.011 1 1
## 5 5 -1 1 1 1 -0.036 1 1
## 6 6 -1 -1 1 1 -0.056 1 1
```

Actions and states have to be merged to yield all possible combinations. To simplify the states, we round 5 times the price-to-book ratios.

We keep the same hyperparameters as in the previous example. Columns below stand for actions: the first (resp. second) number notes the position in the first (resp. second) asset. The rows correspond to states. The scaled P/B ratios are separated by a point (e.g., “X2.3” means that the first (resp. second) asset has a scaled P/B of 2 (resp. 3).

```
fit_RL2 <- ReinforcementLearning(RL_data, # Main RL function
                                 s = "state",
                                 a = "action",
                                 r = "reward",
                                 s_new = "new_state",
                                 control = "control")
fit_RL2$Q <- round(fit_RL2$Q, 3) # Round the Q-matrix
print(fit_RL2) # Show the output
```

```
## State-Action function Q
##         0 0 0 1 -1 -1 -1 0 -1 0 -1 1 1 -1 1 1 0 0
##  X0.2 0.000 0.000 0.000 -0.017 0.000 0.000 0.000 0.002 0.000
##  X0.3 0.000 0.000 0.003 0.000 0.000 0.000 0.030 0.000 0.000
##  X3.1 0.002 0.000 0.005 0.000 -0.002 0.000 0.000 0.000 0.000
##  X2.1 0.005 0.018 0.009 -0.028 0.010 -0.003 0.021 0.008 -0.004
##  X2.2 0.000 0.010 0.000 0.014 0.000 0.000 -0.013 0.006 0.000
##  X2.3 0.000 0.000 0.000 0.000 0.000 0.020 0.000 -0.034 0.000
##  X1.1 0.002 -0.005 -0.022 -0.011 -0.002 -0.009 -0.020 -0.014 -0.023
##  X1.2 0.006 0.016 0.006 0.028 -0.001 0.001 0.020 0.020 -0.001
##  X1.3 0.001 0.004 0.004 -0.011 0.000 0.003 0.005 0.003 0.010
##
## Policy
## X0.2 X0.3 X3.1 X2.1 X2.2 X2.3 X1.1 X1.2 X1.3
## "1 0" "1 -1" "0 -1" "1 -1" "-1 -1" "-1 1" "0 0" "-1 -1" "1 1"
##
## Reward (last iteration)
## [1] -1.296
```

The output shows that there are many combinations of states and actions that are not spanned by the data: basically, the Q function has a zero and it is likely that the combination has not been explored. Some states seem to be more often represented (“X1.1”, “X1.2” and “X2.1”), others, less (“X3.1” and “X3.2”). It is hard to make any sense of the recommendations. Some states close “X0.1” and “X1.1” but the outcomes related to them are very different (buy and short versus hold and buy). Moreover, there is no coherence and no monotonicity in actions with respect to individual state values: low values of states can be associated to very different actions.

One reason why these conclusions do not appear trustworthy pertains to the data size. With only 200+ time points and 99 state-action pairs (11 times 9), this yields on average only two data points to compute the Q function. This could be improved by testing more random actions, but the limits of the sample size would eventually (rapidly) be reached anyway. This is left as an exercise (see below).

## 16.5 Concluding remarks

Reinforcement learning has been applied to financial problems for a long time. Early contributions in the late 1990s include Neuneier (1996), Moody and Wu (1997), Moody et al. (1998) and Neuneier (1998). Since then, many researchers in the computer science field have sought to apply RL techniques to portfolio problems. The advent of massive datasets and the increase in dimensionality make it hard for RL tools to adapt well to very rich environments that are encountered in factor investing.

Recently, some approaches seek to adapt RL to continuous action spaces (Wang and Zhou (2019), Aboussalah and Lee (2020)) but not to high-dimensional state spaces. These spaces are those required in factor investing because all firms yield hundreds of data points characterizing their economic situation. In addition, applications of RL in financial frameworks have a particularity compared to many typical RL tasks: in financial markets, actions of agents have **no impact on the environment** (unless the agent is able to perform massive trades, which is rare and ill-advised because it pushes prices in the wrong direction). This lack of impact of actions may possibly mitigate the efficiency of traditional RL approaches.

Those are challenges that will need to be solved in order for RL to become competitive with alternative (supervised) methods. Nevertheless, the progressive (online-like) way RL works seems suitable for non-stationary environments: the algorithm slowly shifts paradigms as new data arrives. In stationary environments, it has been shown that RL manages to converge to optimal solutions (Kong et al. (2019), Chaouki et al. (2020)). Therefore, in non-stationary markets, RL could be a recourse to build dynamic predictions that adapt to changing macroeconomic conditions. More research needs to be carried out in this field on large dimensional datasets.

We end this chapter by underlining that reinforcement learning has also been used to estimate complex theoretical models (Halperin and Feldshteyn (2018), García-Galicia et al. (2019)).

The research in the field is incredibly diversified and is oriented towards many directions. It is likely that captivating work will be published in the near future.

## 16.6 Exercises

- 1. Test what happens if the process for generating returns has a negative autocorrelation. What is the impact on the Q function and the policy?
- 2. Keeping the same 2 assets as in Section 16.4.2, increases the size of RL\_data by testing **all possible action combinations** for each original data point. Re-run the Q-learning function and see what happens.

## Part V

## Appendix

![](img/8861a37f775d09b4ba7a5151f604d9f5_282_0.png)

## Taylor & Francis

Taylor & Francis Group

http://taylorandfrancis.com

## Data description

### TABLE 17.1: List of all variables (features and labels) in the dataset

| Column Name | Short Description |
|---|---|
| stock_id | security id |
| date | date of the data |
| Advt_12M_Usd | average daily volume in amount in USD over 12 months |
| Advt_3M_Usd | average daily volume in amount in USD over 3 months |
| Advt_6M_Usd | average daily volume in amount in USD over 6 months |
| Asset_Turnover | total sales on average assets |
| Bb_Yld | buyback yield |
| Bv | book value |
| Capex_Ps_Cf | capital expenditure on price to sale cash flow |
| Capex_Sales | capital expenditure on sales |
| Cash_Div_Cf | cash dividends cash flow |
| Cash_Per_Share | cash per share |
| Cf_Sales | cash flow per share |
| Debtequity | debt to equity |
| Div_Yld | dividend yield |
| Dps | dividend per share |
| Ebit_Bv | EBIT on book value |
| Ebit_Noa | EBIT on non operating asset |
| Ebit_Oa | EBIT on operating asset |
| Ebit_Ta | EBIT on total asset |
| Ebitda_Margin | EBITDA margin |
| Eps | earnings per share |
| Eps_Basic | earnings per share basic |
| Eps_Basic_Gr | earnings per share growth |
| Eps_Contin_Oper | earnings per share continuing operations |
| Eps_Dil | earnings per share diluted |
| Ev | enterprise value |
| Ev_Ebitda | enterprise value on EBITDA |
| Fa_Ci | fixed assets on common equity |
| Fcf | free cash flow |
| Fcf_Bv | free cash flow on book value |
| Fcf_Ce | free cash flow on capital employed |
| Fcf_Margin | free cash flow margin |
| Fcf_Noa | free cash flow on net operating assets |
