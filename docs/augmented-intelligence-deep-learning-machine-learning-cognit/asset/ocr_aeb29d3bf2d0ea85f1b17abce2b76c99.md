It will continue adding features from the feature set and training them with the determined hypothesis until the feature subset contains the number of desired features specified at the start.

# 5.3.1.2. *Particle Swarm Optimization (PSO)*

The PSO method simulates the social behaviours of animals such as birds flocking and fish schooling. Initially, PSO was suggested as an optimization approach for continuous problems. However, the need to optimize many concepts such as feature selection pushed the creators of the PSO algorithm to broaden its usage. To solve the discrete problems, they introduced binary particle swarm optimization (BPSO). The technique encodes the position of every particle via a binary string [50].

The technique works as follows. A swarm refers to a population where viable solutions encode as particles in the search space. This technique starts by randomly initializing a population of particles. Particles roam the search space to find the ultimate solution. The algorithm updates the position of each particle according to its experience and that of its neighbours. The best prior particle position is saved as the personal best (pbest), while the best position acquired so far by the swarm is the global best (gbest). At every iteration, BPSO updates the position and the velocity of every particle and then finally outputs the best solution [51].

# 5.3.1.3. *Random Subset Feature Selection (RSFS)*

Random Subset Feature Selection (RSFS) is used to detect a subset of features, which is more suitable than the original variable set [52]. RSFS evaluates every variable depending on its adequacy in the different feature combinations. The values of the relevance are not based on the preceding options in the selection procedure but are a by-product of several independent tests [53].

In RSFS, the random subset classification is carried out as often as it is crucial to differentiate appropriate features from variables that merely seem beneficial because of the random factors of the process. Consequently, there is no greedy backward elimination needed, and the feature set quality improves progressively as arbitrary aspects in the selection procedure are averaged out [54].

RSFS takes as input an initial set of features (F) alongside a learning algorithm and a criterion function. It initializes the algorithm with a dummy feature set zj, a hypothesis for feature relevance, and a null set. The algorithm starts by selecting a