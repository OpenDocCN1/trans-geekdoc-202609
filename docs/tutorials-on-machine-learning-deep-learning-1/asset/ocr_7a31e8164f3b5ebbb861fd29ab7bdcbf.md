Here we'll explain what's going on this random walk.

Basically, Gibbs sampling consists of Gibbs chain. There are several round trips from the visible nodes to the hidden nodes, from the hidden nodes to the visible nodes.

In each round trip of our input Gibbs sampling, the visible nodes are updated, and step by step, we get closer to our good predicted ratings.

At the beginning we start with our input batch of observations. That is, our input ratings in v0, in our batch of 100 users.

Sampling Hidden Nodes: In the first step of Gibbs sampling, using Bernoulli sampling using our p_h_given distribution from sample_h() function.

+   The first step of k-steps contrastive divergence is to sample_h(vk) on the visible nodes, to get the first sampling of the hidden nodes.

Since we want to get this second element returned by sample_h(vk), and then, we use the python trick '_' as we did before.

In this time, we are going to use an underscore '_' and then the hidden nodes obtained at the k-th step of contrastive divergence.

```
vk = rbm.sample_h(vk)
# sampling hidden nodes
```

Since we are doing the sampling of the first hidden nodes, given the values of the first visible nodes, that is our original ratings, the first input for sample_h(vk) in this step of Gibbs sampling is not to change. We so have to take this, because the first step v0 = vk so our output of observations, and then we will be updated.

+   Get our first update of the visible nodes after the first sampling.

Sampling Visible Nodes: We'll update vk after we update it with the following function which is sample_v(vk).

So now right vk = v0, but in then we update vk to the first step of Gibbs sampling, i.e after getting it.

We'll get it Bernoulli sampling our p_v_given distribution from sample_v(vk) on the first sample of our hidden nodes.

Again we get this second element returned by sample_v(vk), we use the python trick under underscore'.

```
vk = rbm.sample_v(vk)
# sampling visible nodes
```

+   Get our first update of the visible nodes after the first sampling.

That's the first of our random walk, that is the first step of Gibbs sampling.

```
for k in range(10):
    _vk = rbm.sample_h(vk)
# sampling hidden nodes
    _vk = rbm.sample_v(vk)
# sampling visible nodes
```

So as the loop continues hk and vk update themselves repeatedly.

Algorithm 1. RBM contrastive divergence
Input: RBM (V1, ..., Vm, H1, ..., Hm), training batch S
Output: gradient approximation Δwij, Δbj and Δvi for i=1, ..., n,
j=1, ..., m
init Δwij = Δbj = Δvi = 0 for i=1, ..., n, j=1, ..., m
for the v in S
    v^(0) ← v
    for t=0, ..., k-1
        for i=1, ..., n do sample h_i^(t) ~ p(h_i | v^(t))
            for j=1, ..., m do sample v_j^(t+1) ~ p(v_j | h^(t))
        for i=1, ..., n, j=1, ..., m do
            Δwij ← Δwij + p(h_i | v^(t)) · v_j^(t) - p(H_i=1 | v^(k)) · v_j^(k)
            Δbj ← Δbj + v_j^(t) - v_j^(k)
            Δvi ← Δvi + p(H_i=1 | v^(0)) - p(H_i=1 | v^(k))