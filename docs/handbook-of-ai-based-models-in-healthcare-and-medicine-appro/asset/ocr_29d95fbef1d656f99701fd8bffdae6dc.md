where Rt[C] represents the overall reward for the whole series of characters that was created.

$$Q(K, C_i)=Q\left(K = C_{1:(i-1)}, C_i\right)=R_i(C)\tag{20.3}$$

To determine the optimum action at intermediate phases, or to maximize the predicted long-term reward, we must take into account the total expected benefit when the entire sequence is created. The validity function Rt(C) rewards the generator based on the generated SMILES when a full SMILES sequence is produced. Equation 20.4 provides the stochastic policy’s predicted long-term reward (value function).

$$J(\theta)=E\left[R_t|K,\theta\right]=\sum_{C_i\in C} G_\theta(C_i|K)\cdot Q(K, C_i)\tag{20.4}$$

We employ the Monte Carlo search [49] to obtain the full sequence in advance of computing the reward function. For a given partial sequence, this creates the subsequent set of characters at an intermediate stage. The characters representing future states are stochastically sampled from state [k + 1] to N, completing the supplied sequence. The subsequent set of actions (choosing the best character for a larger reward) is determined by the future reward applied at each step. Figure 20.1 depicts the entire generative architecture. For our studies, the validity metric V(C) (using the RDKit library), as well as the discriminator’s classification, are used as the total reward to update the generator’s weights throughout the first generator training

![](bbox=[0.1, 0.73, 0.92, 0.9])

FIGURE 20.1 (a) Process for finding new drugs in which the reward is determined by the correctness of produced sequences and the discriminator’s prediction. (b) The rewards from the Tanimoto Similarity Metric, which arbitrarily selects a sequence from the dataset and creates molecules to calculate comparable attributes, are used in the fine-tuning procedure.