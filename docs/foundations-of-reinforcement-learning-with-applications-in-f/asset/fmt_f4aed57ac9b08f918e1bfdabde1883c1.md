
$$\\begin{array}{r} {\\mathcal{P}^{\\pi}(s,s^{\\prime}) = {\\sum\\limits\_{a \\in \\mathcal{A}}\\pi}(s,a) \\cdot \\mathcal{P}(s,a,s^{\\prime})} \\\\ \\end{array}$$  

$$\\begin{array}{r} {\\mathcal{R}\_{T}^{\\pi}(s,s^{\\prime}) = {\\sum\\limits\_{a \\in \\mathcal{A}}\\pi}(s,a) \\cdot \\mathcal{R}\_{T}(s,a,s^{\\prime})} \\\\ \\end{array}$$  

$$\\begin{array}{r} {\\mathcal{R}^{\\pi}(s) = {\\sum\\limits\_{a \\in \\mathcal{A}}\\pi}(s,a) \\cdot \\mathcal{R}(s,a)} \\\\ \\end{array}$$  

So any time we talk about an MDP evaluated with a fixed policy, you should know that we are effectively talking about the implied MRP. This insight is now going to be key in the design of our code to represent Markov Decision Processes.

We create an abstract class called `MarkovDecisionProcess` (code shown below) with two abstract methods—`step` and `actions`. The `step` method is key: it is meant to specify the distribution of pairs of next state and reward, given a non-terminal state and action. The `actions` method's interface specifies that it takes as input a state: `NonTerminal[S]` and produces as output an `Iterable[A]` to represent the set of actions allowable for the input state (since the set of actions can be potentially infinite—in which case we'd have to return an `Iterator[A]`—the return type is fairly generic, i.e., `Iterable[A]`).

The `apply_policy` method takes as input a policy: `Policy[S, A]` and returns a `MarkovRewardProcess` representing the implied MRP. Let's understand the code in `apply_policy`: Firstly, we construct a class `RewardProcess` that implements the abstract method `transition_reward` of `MarkovRewardProcess`. `transition_reward` takes as input a state: `NonTerminal[S]`, creates actions: `Distribution[A]` by applying the given policy on state, and finally uses the `apply` method of `Distribution` to transform actions: `Distribution[A]` into a `Distribution[Tuple[State[S], float]]` (distribution of (next state, reward) pairs) using the abstract method `step`.

We also write the `simulate_actions` method that is analogous to the `simulate_reward` method we had written for `MarkovRewardProcess` for generating a sampling trace. In this case, each step in the sampling trace involves sampling an action from the given policy and then sampling the pair of next state and reward, given the state and sampled action. Each generated `TransitionStep` object consists of the 4-tuple: (state, action, next state, reward). Here's the actual code:

![](images/comp04_8.jpg)

The above code is in the file `rl/markov_decision_process.py`.

## 4.6 SIMPLE INVENTORY EXAMPLE WITH UNLIMITED CAPACITY (INFINITE STATE/ACTION SPACE)

Now we come back to our simple inventory example. Unlike previous situations of this example, here we assume that there is no space capacity constraint on toothpaste. This means we have a choice of ordering any (unlimited) non-negative integer quantity of toothpaste units. Therefore, the action space is infinite. Also, since the order quantity shows up as On-Order the next day and as delivered inventory the day after the next day, the On-Hand and On-Order quantities are also unbounded. Hence, the state space is infinite. Due to the infinite state and action spaces, we won't be able to take advantage of the so-called “Tabular Dynamic Programming Algorithms” we will cover in [Chapter 5](#chapter5.xhtml) (algorithms that are meant for finite state and action spaces). There is still significant value in modeling infinite MDPs of this type because we can perform simulations (by sampling from an infinite space). Simulations are valuable not just to explore various properties and metrics relevant in the real-world problem modeled with an MDP, but simulations also enable us to design approximate algorithms to calculate Value Functions for given policies as well as Optimal Value Functions (which is the ultimate purpose of modeling MDPs).

We will cover details on these approximate algorithms later in the book—for now, it's important for you to simply get familiar with how to model infinite MDPs of this type. This infinite-space inventory example serves as a great learning for an introduction to modeling an infinite (but countable) MDP.

We create a concrete class `SimpleInventoryMDPNoCap` that implements the abstract class `MarkovDecisionProcess` (specifically implements abstract methods `step` and `actions`). The attributes `poisson_lambda`, `holding_cost` and `stockout_cost` have the same semantics as what we had covered for Markov Reward Processes in [Chapter 3](#chapter3.xhtml) (`SimpleInventoryMRP`). The `step` method takes as input a state: `NonTerminal[InventoryState]` and an order: `int` (representing the MDP action). We sample from the Poisson probability distribution of customer demand (calling it `demand_sample: int`). Using `order: int` and `demand_sample: int`, we obtain a sample of the pair of `next_state: InventoryState` and `reward: float`. This sample pair is returned as a `SampledDistribution` object. The above sampling dynamics effectively describe the MDP in terms of this `step` method. The `actions` method returns an `Iterator[int]`, an infinite generator of non-negative integers to represent the fact that the action space (order quantities) for any state comprise of all non-negative integers.

![](images/comp04_9.jpg)

We leave it to you as an exercise to run various simulations of the MRP implied by the deterministic and stochastic policy instances we had created earlier (the above code is in the file `rl/chapter3/simple_inventory_mdp_nocap.py`). See the method `fraction_of_days_oos` in this file as an example of a simulation to calculate the percentage of days when we'd be unable to satisfy some customer demand for toothpaste due to too little inventory at store-opening (naturally, the higher the re-order point in the policy, the lesser the percentage of days when we'd be Out-of-Stock). This kind of simulation exercise helps build intuition on the tradeoffs we have to make between having too little inventory versus having too much inventory (holding costs versus stockout costs)—essentially leading to our ultimate goal of determining the Optimal Policy (more on this later).

## 4.7 FINITE MARKOV DECISION PROCESSES

Certain calculations for Markov Decision Processes can be performed easily if:

*   the state space is finite (𝒮 = {*s*[1],*s*[2],…,*s*[*n*]}),

*   the action space 𝒜(*s*) is finite for each *s* ∈ 𝒩,

*   the set of unique pairs of next state and reward transitions from each pair of current non-terminal state and action is finite.

If we satisfy the above three characteristics, we refer to the Markov Decision Process as a Finite Markov Decision Process. Let us write some code for a Finite Markov Decision Process. We create a concrete class `FiniteMarkovDecisionProcess` that implements the interface of the abstract class `MarkovDecisionProcess` (specifically implements the abstract methods `step` and the `actions`). Our first task is to think about the data structure required to specify an instance of `FiniteMarkovDecisionProcess` (i.e., the data structure we'd pass to the `__init__` method of `FiniteMarkovDecisionProcess`). Analogous to how we curried 𝒫[*R*] for a Markov Reward Process as 𝒩→(𝒮×𝒟→[0,1]) (where 𝒮 = {*s*[1],*s*[2],…,*s*[*n*]} and 𝒩 has *m* ≤ *n* states), here we curry 𝒫[*R*] for the MDP as:

$$\\begin{array}{r} \\left. \\mathcal{N}\\rightarrow(\\mathcal{A}\\rightarrow(\\mathcal{S} \\times \\mathcal{D}\\rightarrow\\lbrack 0,1\\rbrack)) \\right. \\\\ \\end{array}$$  

Since 𝒮 is finite, 𝒜 is finite, and the set of next state and reward transitions for each pair of current state and action is also finite, we can represent 𝒫[*R*] as a data structure of type `StateActionMapping[S, A]` as shown below:

![](images/comp04_10.jpg)
