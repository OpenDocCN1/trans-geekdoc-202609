
stochastic decision process, and a hard Atari game, Montezuma's Revenge. See the open source at https://github.com/mrkulk/hierarchical-deep-RL

## FEUDAL NETWORKS

Vezhnevets et al. (2017) propose feudal networks (FuNs) for hierarchical RL, inspired by feudal RL (Dayan and Hinton, 1993). In FuNs, a Manager module discovers and sets abstract sub-goals and operates at a long time scale, and a Worker module selects atomic actions at every time step of the environment to achieve the sub-goal set by the Manager. FuNs decouple end-to-end learning across multiple levels at different time scales, by separating the Manager module from the Worker module, to facilitate long time scale credit assignment and emergence of sub-policies for sub-goals set by the Manager. In FuNs, sub-goals are formulated as directions in the latent space, so that the Manager selects a subgoal direction to maximize reward, and the Worker selects actions to maximize cosine similarity to the direction of the subgoal set by the Manager. The authors utilize a dilated LSTM to design the Manager to allow backpropagation through long time steps, and experiment FuNs with a water maze and Atari games.

## OPTION-CRITIC

Bacon et al. (2017) derive policy gradient theorems for options, and propose an option-critic architecture to learn both intra-option policies and termination conditions gradually, at the same time with the policy-over-options, combining options discovery with options learning. The option-critic architecture works with linear and non-linear function approximations, with discrete or continuous state and action spaces, and without rewards or sub-goals. The authors experiment with a four-row domain, a pinball domain, and Atari games. See the open source at https://github.com/jeanharb/option_critic.

Harutyunyan et al. (2018) study the dilemma between efficiency of long options and flexibility of short ones in the option-critic architecture. The authors decouple the behaviour and target termination conditions, similar to off-policy learning for policies, and propose to cast options learning as multi-step off-policy learning. The authors show benefits of learning short options from longer ones, by analysis and with experiments.

Riemer et al. (2018) further study the option-critic architecture.

## OPTION DISCOVERY WITH A LAPLACIAN FRAMEWORK

Machado et al. (2017) propose to discover options with proto-value functions (PVFs) (Mahadevan and Maggioni, 2007), which are well-known for representation in MDPs and define options implicitly. The authors introduce the concepts of eigen-purpose and eigen-behavior. An eigen-purpose is an intrinsic reward function, to motivate an agent to traverse in principle directions of the learned representation of state space. An eigen-behavior is the optimal policy for an intrinsic reward function. The authors discover task-independent options, since the eigen-purposes are obtained without reward information. The authors observe that some options are not helpful for exploration, although they improve the efficiency of planning. The authors further show that the options they discover improve exploration, since these options operate at different time scales, and they can be sequenced easily. The authors experiment with tabular domains and Atari games.

## STRATEGIC ATTENTIVE WRITER

Vezhnevets et al. (2016) propose strategic attentive writer (STRAW), a deep recurrent neural network architecture, for learning high-level temporally abstract macro-actions in an end-to-end manner based on observations from the environment. Macro-actions are sequences of actions commonly occurring. STRAW builds a multi-step action plan, updated periodically based on observing rewards, and learns for how long to commit to the plan by following it without replanning. STRAW learns to discover macro-actions automatically from data, in contrast to the manual approach in previous work. Vezhnevets et al. (2016) validate STRAW on next character prediction in text, 2D maze navigation, and Atari games.

## STOCHASTIC NEURAL NETWORKS

Florensa et al. (2017) propose to pre-train a large span of skills using stochastic neural networks with an information-theoretic regularizer, then on top of these skills, to train high-level policies for downstream tasks. Pre-training is based on a proxy reward signal, which is a form of intrinsic motivation to explore agent’s own capabilities, requiring minimal domain knowledge about the downstream tasks. Their method combines hierarchical methods with intrinsic motivation, and the pre-training follows an unsupervised way.

## 12 MULTI-AGENT RL

Multi-agent RL (MARL) is the integration of multi-agent systems (Horling and Lesser, 2004; Shoham and Leyton-Brown, 2009; Stone and Veloso, 2000) with RL. It is at the intersection of game theory (Leyton-Brown and Shoham, 2008) and RL/AI.

Besides issues in RL like sparse rewards and sample efficiency, there are new issues like multiple equilibria, 6 and even fundamental issues like what is the question for multi-agent learning, and whether convergence to an equilibrium is an appropriate goal, etc. Consequently, multi-agent learning is challenging both technically and conceptually, and demands clear understanding of the problem to be solved, the criteria for evaluation, and coherent research agendas (Shoham et al., 2007).

In a fully centralized approach, when global state and joint action information are available, estimating the joint Q action value function becomes possible. This can address the nonstationary issue. However, it encounters the issue of curse of dimensionality when the number of agents grows. Another issue is that it may be hard to extract decentralized policies, for an agent to make decisions based on its own observation.

Littman (1994) employs stochastic games as a framework for MARL, propose minimax-Q learning for zero-sum games, and show convergence under certain conditions. Hu and Wellman (2003) propose Nash Q-learning for general-sum games and show its convergence with a unique Nash equilibrium. Bowling and Veloso (2002) propose the win or learn fast (WoLF) principle to vary the learning rate to tackle the issues with learning a moving target, and show convergence with self-play in certain iterated matrix games. These papers, together with Foerster et al. (2018a), Lowe et al. (2017), and Usunier et al. (2017), follow centralized approaches.

Tan (1993) introduces independent Q-learning (IQL) for MARL, where each agent learns a Q action value function independently. For Q-learning to be stable and convergent, the environment would be stationary. This is usually not the case for multi-agent systems, where an agent would change its policy according to other agents, and the environment is usually nonstationary or even adversarial. Independent approaches to MARL may not converge. Foerster et al. (2017) and Omidshafiei et al. (2017) propose to stabilize independent approaches.

Oliehoek et al. (2008) introduce the paradigm of centralized training for decentralized execution. We discuss several papers following this scheme below.

Along with the success of RL in single agent problems, like, Mnih et al. (2015), Jaderberg et al. (2017), Schulman et al. (2015), Nachum et al. (2018), and two-player games, like Silver et al. (2016a; 2017); Moravčík et al. (2017), recently, we see some progress in multi-agent RL problems, like Jaderberg et al. (2018) for Quake III Arena Capture the Flag, Sun et al. (2018) and Pang et al. (2018) for StarCraft II, and OpenAI Five for Dota 2.

Zambaldi et al. (2018) investigate StarCraft II mini-games with relational deep RL, as discussed in Chapter 13. Bansal et al. (2018) investigate the emergent complex skills via multi-agent competition. Foerster et al. (2018b) propose learning with opponent-learning awareness, so that each agent considers the learning process of other agents in the environment. Hoshen (2017) presents vertex attention interaction network (VAIN), for multi-agent predictive modelling, with an attentional neural network. Mhamdi et al. (2017) introduce dynamic safe interruptibility for MARL, in joint action learners and independent learners scenarios. Perolat et al. (2017) propose to use MARL for the common pool resource appropriation problem. Hu et al. (2018b) propose opponent-guided tactic learning for StarCraft micromanagement. Song et al. (2018) extend generative adversarial imitation learning (GAIL) (Ho and Ermon, 2016) to multi-agent settings. Lanctot et al. (2018) study actor-critic policy optimization in partially observable multi-agent settings. See also Hughes et al. (2018), Wai et al. (2018), and Zhou et al. (2018)

Multi-agent systems have many applications, e.g., as we will discuss, games in Chapter 15, robotics in Chapter 16, energy in Section 20.3, transportation in Section 20.4, and compute systems in Section 20.5.

6 Chen and Deng (2006) show that finding a Nash equilibrium in a two-player game is PPAD-complete, i.e., unless every problem in PPAD is solvable in polynomial time, there is not a fully polynomial-time approximation algorithm for finding a Nash equilibrium in a two-player game. PPAD is a complexity class for polynomial parity arguments on directed graphs.
