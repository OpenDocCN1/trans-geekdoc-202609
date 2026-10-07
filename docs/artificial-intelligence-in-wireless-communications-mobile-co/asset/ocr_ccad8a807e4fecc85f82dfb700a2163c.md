# Genetic Algorithms for Radio Optimization 91

of looking at the functions. The objective functions, like the radio platform, are likely to improve mathematically and representationally over time. It is important, then, the cognitive engine can be easily adapted to new objective functions.

Again, DTD and XML play their role in this problem along with the use of shared object libraries. The GA is fed the objective functions in the form of an XML file that describes what the library holds. The library is compiled as a shared object library that allows dynamic, run-time linking. The GA can then link to the library, pull out the required objectives, and close the library as required. Then, when new objectives are introduced or better mathematical representations are found for the existing objectives, the library can be compiled separately from the rest of the engine and uploaded to the cognitive radios for the next optimization process. The XML file that the GA receives contains the list of functions available, so during evaluation, the objective functions are referenced by name in the library. The library processes the objective and returns a solution. The important aspect of this is in the function prototype. Each function representation is in the form:

```
float <function_name>(radio_hw_def *knobs, radio_meters *meters)
```

The radio_hw_def data structure is a class that contains the information to map the chromosome representation to the radio platform capabilities. The structure is built from the XML and DTD files that define the chromosome as discussed previously. The radio_meters is a simple data structure that holds the results of the objective calculation. Each function returns a number as part of its result. The WSGA solves a maximization problem, and to allow the generic, dynamic representation of fitness values, this value is a representation of the performance of the objective function as a maximization metric. Simply put, when an objective function should be maximized (e.g., throughput, SINR), the returned fitness is the objective itself. when the objective is minimized the inverse. These fitness values are then stored as credits to represent an individuals fitness. The ranking and selection is based off the values of the credits, which, again, are designed to be compared in a maximization problem. Meanwhile, each member holds a copy of the meters data structure used in the post analysis of the algorithm's performance.

# 5.4.3 Optimal Individual Selection

Pareto ranking only goes far to provide a population of optimal/near-optimal and nondominated individuals. However, from this point, the algorithm needs to return a single, final individual as the solution to the