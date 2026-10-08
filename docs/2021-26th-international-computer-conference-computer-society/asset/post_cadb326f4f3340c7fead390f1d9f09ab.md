
how the reward function changes to Diversity(t) and Rating(t). The ideal goal in this post is to get to the right corner, e.e. Diversity(t) = 1 and Rating(t) = 5, which of our reward function changes smoothly to achieve this goal.

![](img/293e1bf91565016a8c5cd326223dbb9c_4_0.png)

$\nabla_{\theta} J(\theta) \approx \frac{1}{N} \sum_{i=1}^{N} \nabla_{\theta} Q(s_i, \mu(s_i))\theta^Q \nabla_{\theta} \mu(s_i)\theta^{\mu}$ (15)

The target networks are updated by a update technique as follows:

```
$$\theta^Q \leftarrow \theta^Q + (1-\tau^Q)\theta^{Q}$$
$$\theta^{\mu} \leftarrow \theta^{\mu} + (1-\tau^{\mu})\theta^{\mu}$$
where $\tau \ll 1$ (16)
```

the training algorithm based on DDPG is described in Algorithm 2:

### Algorithm 2 Training of proposed model

1. Initialize the network $\theta^F$ and critic network $Q(s,a|\theta^Q)$ with parameters $\theta^Q$ and an buffer $\theta^D$ 
2. Initialize target network $F'$ and $Q'(s,a|\theta^{Q'})$ with weights $\theta^{F'}=\theta^F$ and $\theta^{Q'}=\theta^Q$
3. Initialize replay buffer $r$
4. for $episode = 1$ to $E$
5. Initialize state $s_0 = (e_1, ..., e_n)$
6. Add each entry to $e_i \in s_0$ according to Eq 4
7. for $t = 1$ to $D$
8. Generate action $f_{\theta}(s_t) = a_t$ according to policy $\theta$
9. Generate diverse list $d_t$ according to Algorithm 1
10. Recommend list to $d_t$
11. Calculate reward $r_t$ according to Eq 8
12. Update state from $s_t$ to $s_{t+1}$ according to Eq 1
13. Store $(s_t, a_t, r_t, s_{t+1})$ in $r$
14. Set $s_t \leftarrow s_{t+1}$
15. Sample a mini-batch of transitions $(s_t, a_t, r_t, s_{t+1})$ from $r$
16. Set $y_t = r_t + \gamma Q'(s_{t+1}, \mu(s_{t+1}))\theta^{Q'}$
17. Update the critic by mini-batch: $loss = \frac{1}{N} \sum_{i=1}^{N} (y_i - Q(s_i, a_i|\theta^Q))^2$
18. Update the actor using the sampled policy $\theta$
19. Update the target networks:
20. for each
21. end

### Training

In this paper, we use the Deep Deterministic Policy Gradient (DDPG) algorithm to train our model. In DDPG, there are four neural networks as follows: 1) a critic network with parameters $\theta^Q$ 2) an actor-network with parameters $\theta^{\mu}$ 3) a target critic network with parameters $\theta^{Q'}$ 4) a target actor-network with parameters $\theta^{\mu}$. In each step, a user's state is given, and the actor-network generates a policy $U$ in step $t$. Then, the user provides feedback to recommendation list and to construct a diverse list using Algorithm 1. After, the user provides feedback to recommendation list $d_t$, and the recommender recommends $r_t$. After that, $(s_t, a_t, r_t, s_{t+1})$ are stored in the replay buffer. In order to update the critic network $Q(s,a|\theta^Q)$, a mini-batch of size $N$ is sampled from experience replay $r$ to calculate the Temporal Difference (TD) target value:

```
$y_t = r_t + \gamma Q'(s_{t+1}, \mu(s_{t+1}))\theta^{Q'}$ (17)
```

Then, the network is updated by the following function:

```
$loss = \frac{1}{N} \sum_{i=1}^{N} (y_i - Q(s_i, a_i|\theta^Q))^2$ (20)
```

Also, the objective of the actor is to maximize the expected return, which is defined as:

In order to optimize this objective, the gradient of $J(\theta)$ can be taken using some rule as follows:

```
$$\nabla_{\theta^{\mu}} J(\theta) \approx E_{\mu}[\nabla_{\theta} Q(s, \mu(s))\theta^Q \nabla_{\theta} \mu(s)\theta^{\mu}]$$ (14)
```

Since the actor-network is updated by sampled mini-batch of size $N$ from experience replay, the mean of $\nabla_{\theta^{\mu}} J(\theta)$ over $N$ samples is:

### Datasets

We use MovieLens datasets to develop our proposed framework. MovieLens dataset contains a set of users' expressed ratings for movies which were collected by the MovieLens website. In each row $i$, there is a tuple $(u_i, m_i, r_i, f_i)$ where

> https://movielens.org/

## TABLE I
The MAJOR HYPERPARAMETERS

| Method | Major Hyperparameters |
|---|---|
| DLRIR | $N = |d_i| = 5, n = |s_i| = 10, |C_u| = 30, T = 5 \theta = 3, \lambda_1 = .60, \lambda_2 = 3, d_{model} = 100$ |
| DRR-ave | $N = |d_i| = 5, n = |s_i| = 10, T = 10$ |
| LIRD | $N = |d_i| = 5, n = |s_i| = 10, T = 7$ |
| D^2 RL | $N = |d_i| = 5, n = |s_i| = 10, T = 10$ |

is rating (range [1-5]) of user $u_i$ to movie $m_i$ at a particular $t_i$. **Movielens-1m** contains 1 million rating from 640 3706 movies. Since each user's $s_i$ contains only positive interactions, we remove ratings less than 3 from datas.

## B. Methods Comparison

We utilize following methods to compare performance of our proposed model:

- **LIRD [16]:** Proposed a list-wise recommendation model based on deep reinforcement learning the actor network generates a list of weight vectors then scores all items in space using these weights.
- **DRR-ave [15]:** Proposed a state representation model to model user interactions explicitly in deep learning-based recommendation system. The generated proto-action by actor-network is used to the recommender recommends an item with the highest score to the user.
- **DRL [32]:** Proposed a fast greedy mapping algorithm to promote diversity in generated recommendations.

In each dataset, we consider 80% of users' positive interactions for training and 20% of testing. Since we use pretrained, in which each user and item is represented as 100-dimensional embeddings, to simulate unknown ratings. DRR-ave method, the scoring function returns one item with the highest score to the user. Hence, we select N items with the highest score to generate a list of items. The hyperparameters are listed in Table I. We employ **NDCG@**, **Diversity@** and **Precision@** to evaluate performance of our recommendation models. In this paper, the proposed **Precision@** as follows:

```
Precision@ = \frac{\sum_{i=1}^N r_{ui}}{N}
```

such that $r_{ui}$ is rating of user $u$ to $i^{th}$ item in recommended list $d_i$ and $r_{ui} \geq 3$.

## C. Results

The evaluation results are summarized in Fig.5 to 8. The results show that the proposed model is better than other in 90% of cases in our dataset, 40% in precision and 30% in nDCG. In other cases, it is slightly different from other methods. Fig8 indicates that the use of positional encoding improves diversity by 9%, precision by 8%, and nDCG by 0.5%. Complex structures like CNN and RNN can be replaced by positional

![](img/293e1bf91565016a8c5cd326223dbb9c_5_0.png)

![](img/293e1bf91565016a8c5cd326223dbb9c_5_1.png)

![](img/293e1bf91565016a8c5cd326223dbb9c_5_2.png)

![](img/293e1bf91565016a8c5cd326223dbb9c_5_3.png)

## V. CONCLUSION

In this paper we proposed a deep reinforcement learning system DRL which generates the recommendation list concerning both relevance and diversity. Unlike previous works, which had redundant computation in the recommendation system, we propose to use an approximate neighbor search (ANN) method to find the closest items to the proto-action and then generate a diverse list using TDE algorithm.

## REFERENCES

- [1] O. Chancellor and Li, "An empirical evaluation of threshold sampling in Advances in information processing systems, 2011, pp. 2249–2257.
- [2] L. Wi, Chu. Wang., J. Mansfield, and R. Sharma, "Context-aware approach to personalized recommendation," in Proceedings of the 24th ACM SIGDD Conference on Knowledge Discovery and Data Mining, 2018, pp.–9.
- [3] X. Zhao, Z. Wang, and J. Wang, "Interactive collaborative filtering," in Proceedings of 22nd ACM international conference on Information and Management, 2019, pp. 141–150.
- [4] M. Barnett, J. Das, T. Tran, and S. Blackwell, "Efficient sampling for matrix-factorization models," Advances in information processing systems, 2016, pp. 3145–3154.
- [5] H. Wang, Q. Wu, and H. Wang, "Factorization bandits for item recommendation," in Advances in AAAI, 2017, pp. 2996–3003.
- [6] A. Vaswani, N. Shazeer, N. Parmar, U. Uszkoreit, L. Jones, A. Gomez, L. Kaiser, and A. Polosukhin, "Attention is all you need," in NeurIPS information processing systems, 2017.
- [7] D. Silver, A. Huang, C. J. Madsen, L. Guest, G. Deniese, J. Jensche, A. Vasudev, M. Mielekar, and D. Hassabis, "Deep RL without human control," nature, 530, pp. 548–554, 2016.
- [8] W. Emchotewat, P. Poonong, and J. Wang, "Interactive collaborative filtering using deep learning based top-k recommendation," in 2013 IEEE 5th International Conference on Computer Science and Workshops. IEEE, 2013, pp. 403–408.
- [9] J. Wang, Y. Wang, Y. Xu, and Y. Zhou, "A deep learning to rank in ecommerce search engine: Formalization, analysis, and application," in Proceedings of the 24th ACM SIGKDD International Conference on Knowledge Discovery & Data Mining, 2018, pp. 2145–2154.
- [10] O. M. Andykh, B. Kaiser, C. Rospolskiy, R. Vielekov, and G. V. Mazurov, "Attention mechanism for sequence-to-sequence interaction," The International Journal of Robotics Research, 39, no. 1, pp. 3–30, 2020.
- [11] L. Tang, "A survey on deep reinforcement learning," arXiv preprint:1909.02268.
- [12] N. Takahashi and K. Lin, "A hybrid content-based recommender system in Proceedings of the 20th ACM SIGIR international conference, 2006, pp. 1164–1168.
- [13] F. Agarwal, J. Lee, and L. Britman, "An market-based recommender system, Journal of Machine Learning Research, 6, no. 5, pp. 1265–1295, 2005.
- [14] D. Gulci, K. Elifakis, P. Parter, J. Ibañez, E. Herzog, and J. Wang, "Variational autoencoder bandits for context-aware recommendation," arXiv preprint:1809.10233, 2019.
- [15] F. Liu, X. Tang, L. Wang, Y. Zhang, Y. Chen, H. Sun, and J. Zhao, "Deep reinforcement learning for user-item interaction," arXiv preprint:1810.1227, 2018.
- [16] X. Zhao, L. Zhang, X. Xu, Z. Ding, D. Yin, and J. Tang, "Deep reinforcement learning for list-diverse recommendations," arXiv preprint:1801.00279, 2018.
- [17] X. Zhao, L. Li, X. Zhang, Z. Ding, D. Yin, and J. Tang, "Deep reinforcement learning for page-wise recommendations," in Proceedings of the 12th ACM Conference on Recommender Systems, 2018, pp. 95–99.
- [18] A. Vaswani, N. Shazeer, N. Parmar, U. Uszkoreit, L. Jones, A. Gomez, L. Kaiser, and A. Polosukhin, "Attention is all you need," in NeurIPS information processing systems, 2017.
- [19] Airbnb, "Anonymous," https://github.com/spotify/annonymizer.
- [20] W. Emchawotewat, P. Poonong, and J. Wang, "Interactive collaborative filtering using deep learning based top-k recommendation," in 2013 IEEE 5th International Conference on Computer Science and Applications Workshops. IEEE, 2013, pp. 403–408.
