
to simulate cycles of days. Therefore, the following reasonable constraints can be specified: 0 ≤ ta_on, ta_off, ta_tmp_w, ta_tmp_d ≤ 24.

### 8.3.4 Actions

To allow the agent to manipulate the time advance values of the DEVS model under construction, actions should be specified in accordance with Eq. (1.1). Below, we show five typical actions.

- Macro-increase `Inc(ta)`: `ta ↦ ta + 0.1`
- Micro-increase `inc(ta)`: `ta ↦ ta + 0.01`
- No change `noc(ta)`: `ta ↦ ta`
- Micro-decrease `dec(ta)`: `ta ↦ ta − 0.01`
- Macro-decrease `Dec(ta)`: `ta ↦ ta − 0.1`

Macro-steps improve the convergence of the agent to a rudimentary solution, while micro-steps allow the agent to refine the solution within a solution area. To speed up the learning process, the agent should be able to change each of the four time advance values encoded in the state in each step. Therefore, it is a good idea to encode the five actions operating on the four time advance values as a 4×5 tensor.

The response to a chosen action is then obtained, as shown in Listing 1. Here, we only show the update of the chosen state variable, i.e., ta_off. The response mechanism of the agent expects the chosen actions on its input (action). The first element of the action tensor (action[0]) corresponds to the action chosen for the first element of the state, i.e., ta_off. The chosen action is represented by an integer. The switch case in Lines 10–21 interprets the value under action[0] and reacts accordingly. Changes to the rest of the state variables are calculated in a similar way. Finally, the new state is returned in Line 30.

Tensorforce provides means for specifying action masks which allow for controlling which actions are enabled in specific states. The action mask in Listing 2 ensures that the agent's actions cannot bring the time advance values outside the [0, 24] interval. Element [i, j] in the action mask tensor corresponds to element [i, j] of the action tensor and element [i] of the state tensor. For example, mask element [1,1] (self.ta['off']) determines that the first action in the action tensor (Inc(ta)) action can be executed on the first value of the state (ta_off) only if ta_off ≤23.9. Clearly, this means that in each timestep k (see Figure 8.7), ta_off (k) ≤24.

### 8.3.5 Reward

As per Section 8.3.1, the reward function is formulated as the distance between the trace of the candidate model and the reference trace.

Following the notations of Figure 8.7, the reward in step $k$ is defined as $r_k = -|d( \text{trace}_k, \text{trace}_0)|$. The goal of the agent is to maximize the expected cumulative reward, i.e., $\max \left\{ E \left[ \sum_{k=0}^H a_k r_k \right] \right\}$, where $H$ denotes the horizon of the action trajectory, $a_k$ denotes the $k$th action, and $r_k$ denotes the $k$th reward.

To ensure faster convergence to the learning objective, a more aggressively increasing penalty can be used, e.g., $-r^2$. The distance metric is the Euclidean distance between the traces. Accordingly, the 2-norm (or Euclidean norm) of the trace vectors can be used, i.e., $r_k = \left( \sum_{n=1}^{|\text{trace}_k|} |x_n|^2 \right)^{\frac{1}{2}} - \left( \sum_{n=1}^{|\text{trace}_0|} |x_m|^2 \right)^{\frac{1}{2}}$, where $|\cdot|$ denotes length with vector arguments $trace_k$ and $trace_0$, and absolute with scalar arguments $x_n$ and $x_m$.

```
def response(self, action):
    on_action = action[0]
    off_action = action[1]
    tmp_u_action = action[2]
    tmp_d_action = action[3]
    update = np.array([0, 0, 0, 0])

    #Compute ON action
    if on_action == 0: update += np.array([0.1, 0, 0, 0])
    elif on_action == 1: update += np.array([0.01, 0, 0, 0])
    elif on_action == 2: update += np.array([0, 0, 0, 0])
    elif on_action == 3: update += np.array([-0.01, 0, 0, 0])
    elif on_action == 4: update += np.array([-0.1, 0, 0, 0])
    else: raise Exception('Unknown action')

    #Compute OFF action
    ...
    #Compute TMP_U action
    ...
    #Compute TMP_D action
    ...
    return self.ta+update
```

Listing 8.1: Action mask controlling the applicability of actions

## 8.4 Discussion

We discuss the advantages and limitations of the presented approach, as well as outline some challenges.

```
1 np.array([
2 [self.ta['off'] <= 23.9, self.ta['off'] <= 23.99,
3 True, self.ta['off'] >= 0.01, self.ta['off'] >= 0.1],
4 [self.ta['on'] <= 23.9, self.ta['on'] <= 23.99,
5 True, self.ta['on'] >= 0.01, self.ta['on'] >= 0.1],
6 [self.ta['tmp_u'] <= 23.9, self.ta['tmp_u'] <= 23.99,
7 True, self.ta['tmp_u'] >= 0.01, self.ta['tmp_u'] >= 0.1],
8 [self.ta['tmp_d'] <= 23.9, self.ta['tmp_d'] <= 23.99,
9 True, self.ta['tmp_d'] >= 0.01, self.ta['tmp_d'] >= 0.1],
10 ])
```

Listing 8.2: Action mask controlling the applicability of actions

### 8.4.1 Advantages of This Approach

As we have shown, reinforcement learning aligns well with the construction of simulators. As reported by previous work [32], the illustrative setup in Section 8.3 performs well on DEVS construction problems. The state encoding and the reward function in are general enough to accommodate simulation formalisms other than DEVS. Basically, it is the set of actions (Section 8.3.4) that make the presented approach specific to DEVS. By the separation of formalism-specific concerns, the approach promises high reusability across various formalisms used in Digital Twins.

Our approach illustrates that the complexity of simulator construction reduces to the essential complexity of setting up and tuning reinforcement learning agents. Accidental complexity is largely mitigated, mostly due to the high automation and minimized need for human intervention. The engineering of Digital Twins is challenged by the enormous complexity of the systems subject to twinning, and therefore, approaches such as the one outlined in this book chapter project to be key enablers in the next generation of Digital Twins.

With proper automation, these approaches reduce the costs of developing simulators. As a consequence, the development costs of Digital Twin services relying on simulation will decrease as well. Reduced costs, in turn, enable more sophisticated services and features. For example, training machine learning agents in the simulated worlds of Digital Twins allows the agent to explore potentially unsafe or hazardous settings without actual physical risk.

As emphasized previously, DEVS is a versatile simulation formalism. Consequently, it is not surprising to see numerous Digital Twin use cases relying on DEVS. Such use cases with substantial upside include the optimization of manufacturing processes through simulation [34], explicitly modeled interactions between services and with data Markov Decision Process (APIs) that allow for better validation and verification of interaction protocols [35], and explicit models at runtime driven by programmed graph transformations [36].

### 8.4.2 Limitations

While the eventually inferred model behaves similarly to the system to be modeled, this approach faces limitations.

It is not always obvious whether learning a similarly behaving model is sufficient or structural constraints should be respected as well. To overcome this limit, one needs to ensure that behavioral congruence is sufficient for the problem at hand. In addition, the trace information must be rich enough to allow reasoning about the property on which the similarity between the underlying asset and the simulation model is based on. Alternative distance measures can be considered to further improve the reward function, such as dynamic time warping and various kernel methods [37,38]. In many practical settings, ensuring behavioral congruence is sufficient, and this threat to validity may be negligible.

While opting for DEVS makes the outlined approach fairly generic, the approach is reusable only if appropriate congruence is ensured between applications. As demonstrated in Ref. [32], it is feasible to parameterize the outlined approach in a way that the agent and the reward function are reusable for a class of models. However, the generalizability of the policy might be limited to structurally similar models. Transposing the originally inferred policy to other problems without retraining the agent is a challenge to be investigated. One promising direction to explore is the ability of validity frames [10] to capture the contextual information of the physical asset and its environment. The conditions under which the policy is transferable to other problems could be expressed in a formal way.

### 8.4.3 Open Challenges

Below, we outline some of the challenges and opportunities we find the most important currently.

### 8.4.3.1 Human–Machine and Machine–Machine Learning

We see opportunities in learning settings with the human or other machine learning agents involved. While humans perform poorly in specifying optimal models, they perform considerably well in specifying reasonable ones [39]. As a consequence, rudimentary models or model templates provided by domain experts would increase the performance of the approach. Furthermore, domain experts can be employed in the oversight of the learning process as well. In such interactive settings, the human expert can be queried by the machine at the points of the exploration where the search algorithm indicates tough choices for the machine. Learning from the human expert can be enabled to further improve the agent’s performance. Despite the high costs of human reward function in naive reinforcement learning approaches [40], learning from the human has been shown to be feasible in numerous settings [41,42].
