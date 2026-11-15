# 2.4.4 Other directions

Although Algorithm 1 offers a fresh perspective on resolving the EDP, additional exploration is vital to elevate its overall performance. As we progress, we will explore various research paths, deferring the associated theoretical examinations to future studies.

(i) Fully Decentralized: We have discerned that ET-PDA lacks full distribution owing to the reliance on two global variables, s and β. Nevertheless, there is a prospect for achieving complete distribution by substituting these globals with local counterparts, si and βi, which would allow us to conduct an analogous convergence analysis.

(ii) Directed Networks: In practical applications, a significant proportion of communications exhibit a directional nature, and network environments are often subject to dynamic variations. Therefore we are driven to expand the framework from undirected to directed networks and incorporate studies pertaining to time-varying networks [1,3,14,42]. These advancements will enable a more realistic simulation of real-world conditions.

(iii) Computation Efficiency: Acknowledging the generator’s constrained computational prowess when dealing with vast datasets, we can leverage the stochastic gradient [14] as an alternative to the deterministic gradient employed in the original algorithm. This methodology circumvents the necessity of computing all gradients, thereby significantly enhancing computational efficiency.

# 2.5 Numerical simulations

The exploration of EDP in smart grids holds paramount significance in managing daily electricity consumption. For this purpose, this subsection proposes to employ ET-PDA to evaluate its efficacy in various established cases within the relevant field.

# 2.5.1 Case 1: simulation on the IEEE 14-bus system

Initially, we delve into the resolution for Electric Demand Planning (EDP) on the IEEE 14-bus system, as referenced in [17], a testing platform comprising five power generators labeled {1, 2, 3, 6, 8}. For each generator i, the cost associated with its operation is expressed as fi(xi) = Aixi^2 + Bixi, where Ai ∈ [0.03, 0.04] and Bi ∈ [2.0, 4.0] are cost coefficients. The variable xi represents the generation capacity, measured in MW. Notably, the actual power generation of each generator i varies, and ui denotes its maximum generation capacity, constrained within the range of [70, 90] MW. Detailed numerical values for all these parameters are provided in Table 2.1, cited from [17,35,43]. Here, we assume that the total load demand across all generators is known to be $\sum_{i=1}^n c_i = 380$MW.

Analyzing the operational outcomes depicted in Figs. 2.2(a) and 2.2(b), it is evident that ET-PDA has effectively attained the desired optimal economic dispatch, with the generation power of each generator set as follows: x1* = 80MW,