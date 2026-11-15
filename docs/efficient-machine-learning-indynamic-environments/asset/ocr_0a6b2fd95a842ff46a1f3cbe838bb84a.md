+   2.6 Related Work . . . . . . . . . . . . . . . . . . . 25

# 3 Dynamically Determining Elasticity . . . . . . . . . . . 27

+   3.1 Query Difficulty . . . . . . . . . . . . . . . . . . 27

+   3.2 Agreement-Based Cascading (ABC) . . . . . . . . . . . 29

+   3.2.1 Overview of ABC Approach . . . . . . . . . . . . . 29

+   3.2.2 ABC in Modern ML Environments . . . . . . . . . . . 30

+   3.3 Formalization and Theoretical Details . . . . . . . . 31

+   3.3.1 Problem Setup and Notation . . . . . . . . . . . . 32

+   3.3.2 Deferral Rule-Based Drop-in Cascade . . . . . . . . 32

+   3.3.3 Deferral using Ensemble Agreement . . . . . . . . . 33

+   3.3.4 Inference Cost Savings and Competitiveness . . . . . 35

+   3.4 Experiments . . . . . . . . . . . . . . . . . . . . 36

+   3.4.1 When is ABC Practical? . . . . . . . . . . . . . . 37

+   3.4.2 Real-world Case Studies . . . . . . . . . . . . . . 38

+   3.5 Conclusions, Limitations and Further Directions . . . . 43

+   3.6 Related Work . . . . . . . . . . . . . . . . . . . . 43

# II Continual Optim. in Gradually Evolving Environments 47

# 4 Gradually-Evolving Environments . . . . . . . . . . . . 49

+   4.1 Resource Allocation in Machine Learning . . . . . . . . 49

+   4.2 Linear Program Formulation . . . . . . . . . . . . . . 51

+   4.2.1 Solving linear programs . . . . . . . . . . . . . . . 52

+   4.2.2 Scalability challenges in solving linear programs . . . 53

+   4.3 Continual Optimization . . . . . . . . . . . . . . . . 55

+   4.3.1 Gradually Evolving LPs and Continual Optimization . . 55

+   4.3.2 COPTER for Continual Optimization . . . . . . . . . . 58

+   4.4 COPTER: Theoretical Discussion . . . . . . . . . . . . 60

+   4.4.1 Dynamic Regret for GPU Scheduling . . . . . . . . . . 61

+   4.4.2 COPTER and Follow The Leader (FTL) . . . . . . . . . 62

+   4.4.3 Warm Starting Proximal Point Algorithm (PPA) . . . . . 63

+   4.5 Application: GPU Cluster Scheduling . . . . . . . . . . 64

+   4.5.1 SIA: Job-resource co-adaptivity for GPU clusters . . . 64

+   4.5.2 Empirical Evaluation . . . . . . . . . . . . . . . . 66

+   4.6 Conclusion . . . . . . . . . . . . . . . . . . . . . 68

+   4.7 Related Work and Discussion . . . . . . . . . . . . . . 68