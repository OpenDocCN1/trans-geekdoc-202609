# Table 7.14. Temperature Sample

| Time | Temperature |
| 1 | 20 |
| 2 | 19.9 |
| 3 | 19.8 |
| 4 | 19.7 |
| 5 | 19.6 |
| 6 | 19.5 |
| 7 | 19.4 |
| 8 | 19.3 |
| 9 | 19.2 |
| 10 | 19.2 |
| 11 | 19.1 |
| 12 | 19 |
| . | . |
| . | . |
| n | y |

A single-step forecast would require a forecast at time step 13 only. A multi-step may require a forecast for the next two days, as follows:

# Table 7.15. Multistep Forecast

| Time | Temperature |
| 13 | ? |
| 14 | ? |

For predicting multiple timesteps, the multiple output strategy is used. This is a supervised learning method instead of predicting a single output as compared to normal regression, involves developing one model that is capable of outputting multiple variables for each prediction. In the case of predicting the temperature for the next N minutes, the model is developed and is used to predict the next two days as one operation as:

```
$Pred_{t+1},Pred_{t+2} = model(O_{t-1}, O_{t-2}, \dots, O_{t-n})$
```

Where,

+   - $Pred_{t+1}$ - prediction at $t = t + 1$
- $Pred_{t+2}$ - prediction at $t = t + 2$
- $O_{t-1}$ - observation at time $t = t + 1$
- $O_{t-n}$ - observation at time $t = t + n$