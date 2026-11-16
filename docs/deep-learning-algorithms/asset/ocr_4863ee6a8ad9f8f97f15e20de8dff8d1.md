is sent.Designing a suitable reward function is a key for using TORCS as the platform to test BAMDDPG, which helps to learn a good policy to control the simulated car. We describe the details of designing the reward function in this section. As the driving environment state of TORCS can be perceived by various sensors of the simulated car, we can create the reward function using these sensor data which is shown in Table

Equation (14) presents our constructed reward function, which restricts the behavior of the simulated car in TORCS. Each time the simulated car interacts with the driving environment of TORCS, we expect to gain as large reward as possible through the following equation:

r = \left( v \times \left( \frac{1 - |v - \beta|}{\alpha} \right)^{\mathbb{I}_{d_1 \le 10}} \right) \times \cos \phi \times (1 - |\sin \phi|) \times (1 - |d_2|) \times \left( \frac{|d_1|}{50} \right)^{\mathbb{I}_{d_1 \le 50}} ,

# Table 1. Performance comparison of subpolicies and the aggregated policy

| Policy | Episodes | Total reward | Average reward |
|---|---|---|---|
| Subpolicy1 | 20 | 720.69 | 36.03 |
| Subpolicy2 | 20 | 538.28 | 26.91 |
| Subpolicy3 | 20 | 463.98 | 23.20 |
| Aggregated policy | 20 | 829.17 | 41.46 |

![](bbox=[0.103, 0.58, 0.85, 0.885])

# Figure 6. Diagram of the client-server architecture of TORCS.