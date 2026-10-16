```
In [23]:

pet_data_p1 = pet_data.copy()  # don't muck the original data
pet_data_p1['ones'] = 1.0      # manual +1 trick

# remove coding intercept ..... add manual ones == add manual intercept
formula = 'cost ~ (pet - 1) + ones'
sm_model = smf.ols(formula, data=pet_data_p1).fit()
display(pd.DataFrame(sm_model.params).T)
```

|  | pet[cat] | pet[dog] | ones |
|---|---|---|---|
| 0 | 1.6667 | 19.1667 | 20.8333 |

Something seems to be wrong, Major Tom. The coefficients are different. Let's take a quick look at the predictions from both models:

```
In [24]:

# row-slicing is annoying, but have to get to single-D things
# and .flat gives a warning in the DF constructor
df = pd.DataFrame({'predicted_sk' : sk_model.predict(sk_ftrs)[:,0],
                   'predicted_sm' : sm_model.predict(pet_data_p1),
                   'actual'       : sk_tgt[:,0]})
display(df)
```

|  | predicted_sk | predicted_sm | actual |
|---|---|---|---|
| 0 | 22.5000 | 22.5000 | 20.0000 |
| 1 | 22.5000 | 22.5000 | 25.0000 |
| 2 | 40.0000 | 40.0000 | 40.0000 |

Yet the predictions are the same. What on Earth is going on?

# 10.5.1.4 Solving the Riddle

Let's look under the hood at what happens when we specify a pet formula without an intercept. Here's our data including the column of ones:

```
In [25]:

display(pet_data_p1)
```

|  | pet | cost | ones |
|---|---|---|---|
| 0 | cat | 20.0000 | 1.0000 |
| 1 | cat | 25.0000 | 1.0000 |
| 2 | dog | 40.0000 | 1.0000 |