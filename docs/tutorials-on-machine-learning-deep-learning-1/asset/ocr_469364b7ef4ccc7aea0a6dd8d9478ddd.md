In continues the end of the loop, we'll get the 10th sample of hidden nodes and the 10th sample of visible nodes.

Getting hk and vk after the last step of the random walk, we can now approximate the gradients by 8, 9, and 10th steps of k-Contrastive-divergence algorithm.

What we observed is step 5 & 6 of k-Contrastive-divergence algorithm.

We want to get the last sample after the last step of the random walk, the last sample of hidden nodes and the last sample of visible nodes.

We need those last samples to update the weight and the bias to approximate the gradient.

Actually here we the last sample of visible nodes.

+   - But we don't only use the last sample of the hidden nodes, which was just to get the last sample of visible nodes.
- We got out that vk: we can now approximate the gradient to the weights and the bias.
- We use tarin() to update the weights and the bias, from our RBM class.

Ignorant unwanted moving during weight update: Before we use this function to update the weight, we need to do something very important:

+   - We don't wanna from the movies which has no rating, that is for the cells (movies) that have a minus -1(no rating).
- We'll ignore these cells that contain the -1 ratings in the training process.
- We are going to freeze these visible nodes that contain the -1 ratings. So that it won't be possible to update them during Gibbs sampling.

How can we freeze these visible nodes containing the minus ratings? We need to take the vk-visible nodes, and inside the for-loop,

```
for k in range(10):
    _hk = random.sample_h(vk) # sampling hidden nodes
    vk = random.sample_v(hk) # sampling visible nodes
    vk[0] < 0 = v0[0] < 0
```

That is, we use v0-1s to make vk updated to keep away from updating.
vk<0] gets the nodes that have a -1 rating in vk, that were not originally rated by the users. replace those nodes with v0's original/unchanged values that were not originally rated by the users. The original minus from the target v0 because it is not updated.
We used v0 < 0, to get the minus one ratings because our ratings are either -1, or 1.

By doing this, we make sure the training is not on these ratings that were not actually existed(not-rated by users).

So now we get out of this thin for loop and soon enough we will start the training.

# 14.5.4 Training the RBM-model - part 3: train()

phk: We want to apply the train() function to update the weight and the bias. But, notice that in this train() function, we need

```
train(self, v0, vk, ph0, phk):
```

+   i. target, v0
ii. our sampled visible nodes at the last step of the random walk, vk.
iii. The initial probabilities, phk.
iv. And k-step probabilities, phk.

Notice, we have one ph: We didn't calculate it because vk wasn't updated at start.

So before applying the train() function we compute phk