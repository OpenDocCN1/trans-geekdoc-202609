Same thing here, our RBM-recommender-model is **trained for 10-step (k-step)** and, for test-set it have to take `only-one` step.

+   - The whole principle of the blind walk technique with MCMC. Markov Chain Carlo. That's to the random walk keep in mind that the probabilities are not the same, it is blind-walk with different probabilities.

So our prediction will be *directly* the **result of one round trip?** Gibbs sampling. One **step** of the blind walk is Then we'll get all our predictions of the **test** set in one shot.

In this step we gonna start with an condition/filter the **unseen-movies** from the **test-set** (the -1 ratings that just never predicted). And it's time we are dealing with for the train-test 0 set.

+   - We use `len()` to get the real-ratings (original ratings of the test set) that are existent from the target `vt`.

+   - We take all the ratings that existent using the condition `vt=0`.

+   - `len(vt[vt==0]) > 0` : Specifies the number of nodes containing the non-negative ratings must be larger than zero, and in this we can make some predictions.

To make the predictions we use `sample_h()` and `sample_v()` functions. In this step we use `h` and `v` of hk and vk

```
python
if len(vt[vt==0]) > 0:
    h = rbm.sample_h(v)
    v = rbm.sample_v(h)
```

For the input nodes we'll get only one hidden node because there is **one step** i.e one vector of hidden nodes to get our **final prediction** of predictions and that's all for the one step of the blind walk.
We don't need `vk[vk<0] < v[v<0]` We do not use `phk` or `train()`, so we get rid of those lines.

NOTE that, we have to update the **test_loss** and the **counter cnt** inside this `if`-block. Because these are in the `if`-block we are computing the **test_loss** only for the existent target, so we used `torch.mean()` and `torch.abs()`.

```
test_loss += torch.mean(torch.abs(vt[vt == 0] - v[vt == 0]))
```

So

```
python
if len(vt[vt==0]) > 0:
    h = rbm.sample_h(v)
    v = rbm.sample_v(h)
```

```
python
# Error rate
test_loss += torch.mean(torch.abs(vt[vt == 0] - v[vt == 0]))
cnt += 1.0
```

```
python
eval_loss = test_loss/cnt
print(f"Evaluation or Test loss = {eval_loss}")
```

```
python
# Evaluating the RBM on Test-set
test_loss = 0
cnt = 0
for u_id in range(nb_users):
    vt = train_test_set[u_id:u_id + 1]
    vt = test_test_set[u_id:u_id + 1]
```

```
python
if len(vt[vt==0]) > 0:
    h = rbm.sample_h(v)
    v = rbm.sample_v(h)
```

```
python
# Error rate
test_loss += torch.mean(torch.abs(vt[vt == 0] - v[vt == 0]))
cnt += 1.0
```

```
python
eval_loss = test_loss/cnt
print(f"Evaluation or Test loss = {eval_loss}")
```