# 22.5 ADVANCES IN GENERALISED PLANNERS

# 22.5.1 MACHINE LEARNING AND PLANNERS

Integration of ML, or the use of ML with planning, is nothing new. DeepMind is arguably the most well-known example. While it showcased the powerful results achievable by combining planning with ML, the goal was more to enhance planners’ efficiency, adaptability, and scalability by leveraging learned models for action outcomes, state transitions, and value functions.

There is also a field of study called Generalised Planning which is very distinct from the concept of a generalised planner. It is important to note that in Generalised Planning, ML is used to find generalised plans as opposed to creating generalised planners (Rivlin et al., 2020).

ML has also been used as a planner itself such as with TDDP-Net, a 3D-pathfinding planner that uses a deep neural network (DNN). While the resulting DNN model could be domain-specific due to the nature of the training data, the approach showcases the potential of using learned models to directly generate plans (Wu et al., 2019). In the broadest sense, using DNNs could be considered a generalised approach, in that the resulting planners can adapt to different environments without manual encoding of rules or heuristics.

Others have used DNNs and reinforcement learning techniques to optimise classical planners by improving the search heuristic using the predictive nature of ML (Groshev et al., 2018). Creating a general set of actions or tasks to support a generalised planner could also be achieved via reinforcement learning.

# 22.5.2 Hybrid Planners

With respect to domainless planners, a common hybrid approach involves using a non-planning method to abstract the planning problem. Abstracting the problem either using PDDL or through some other means is required by a generalised planner. If the problem domain is not abstracted in some fashion, the planner will need domain-specific information to understand the problem it is trying to solve.

As previously discussed, ML can be combined with planning. In particular, for generalised planners, using ML to optimise the search can make generalised planners more performant.

By its very nature, a portfolio approach is a hybrid strategy as it involves combining multiple planners or algorithms to tackle the same problem. This hybrid strategy aims to benefit from the strengths of different methods and improve overall planning performance.

There have also been attempts to automate the abstraction of a classical planner which requires a hybrid of a classical planner with an abstraction heuristic (Srivastava et al., 2011).

In the field of robotics, there has been some success using probability methods to enhance exploration which is then fed into a generalised planner. This hybrid approach combines probabilistic reasoning with planning to enhance exploration and decision-making in uncertain environments.