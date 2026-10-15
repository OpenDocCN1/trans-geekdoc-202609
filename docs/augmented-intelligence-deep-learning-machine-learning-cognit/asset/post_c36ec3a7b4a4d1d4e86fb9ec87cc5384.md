
chase other crows to obtain their food. It has been applied successfully to different science and engineering fields of optimization [9]. Nonetheless, the current and focused analysis of this algorithm is lacking in the literature. Furthermore, the CSA was no longer compared to new algorithms; since then, many new algorithms have been introduced. Experimenting with CSA on a wider variety of test functions and comparing it to modern and reliable algorithms would, therefore, further expose the use of the algorithm. As a result, the objective of this paper is to first study the principles of CSA in addition to its basic structure and features and secondly, provide a comprehensive and detailed review of the state of the art CSA algorithm. Thirdly, it offers various CSA applications, especially in the medical field. Finally, we conclude the paper by summing up the progress and evaluating future patterns in the study. This work will be of great assistance to researchers in further growth and implementation work in the area.

## 7.2. CROW SEARCH OPTIMIZATION

### 7.2.1. Overview of Crow Search Optimization

Optimization has played a very important role in several areas, not limited to engineering problems. These problems consist of complex objective functions, various decision variables, and a huge set of constraints, which add complexity to an already complicated problem of optimization. Such constraints take the search from a conventional optimization methodology to a modern area of analysis, i.e., swarm intelligence pioneered in the 1980s by Beni and Wang [6]. SI mimics the collective intellect of the living creatures of nature [6]. Each new algorithm focuses on two features: first, finding solutions close to the actual optimal solution, thus reducing the gap between them, and second, finding the solution in the least possible time, and thus less search time. Several optimization algorithms have been proposed over the past years, as each has its own advantages and disadvantages. The crow search algorithm is a newly developed algorithm that imitates the social intelligence of crows and their way of collecting food. It is a metaheuristic algorithm inspired by crows' intelligent behaviors. Crows are among the wisest creatures in the world as shown in the mirror test [9]. There are numerous bits of proof indicating crows' astuteness. Crows can recollect faces, trade data with one another, take the nourishment and get it far from others by concealing the assortment of food sources [9]. They are clever criminals as they take additional consideration, for example, changing concealing spots from time to time so they can abstain from being casualties later on. Crows utilize a learned way to deal with concealing their nourishment and taking others' nourishment. In the subsequent sections, the features of CSA, the algorithmic structure of CSA, along with the Pseudocode and flowchart, are prepared for understanding and implementation of CSA in different fields of optimization.

![](img/be45bf301a3c0ebefb162571e2625fab_166_0.png)

Fig. (2). Flowchart of CSA.

The CSA procedure steps are as follows:

Step 1: Initializing the problem by defining both decision variables and restrictions related to the issue, in addition to specifying the following criteria: number of population (N), Flight length (fl), Maximum number of iterations (iter max), and Awareness probabilities (AP).

**Step 2:** The position and memory of the crows are randomly configured.

**Step 3:** Calculate the fitness function for each crow.

**Step 4:** Generate new solution by Eq (2).

**Step 5:** Check the feasibility of new solution: By relying on the feasibility or infeasibility of the solution where if the solution is feasible, the crow adjusts its location and the solution is acceptable, otherwise the solution is rejected and the crow remains in its current location.

**Step 6:** Calculate the fitness function for each crow in a new location.

**Step 7:** Update memory:

Crows change their memories according to the formula below:

$$m^{i,iter+1} = \begin{cases} x^{i,iter+1} \ f(x^{i,iter+1}) \ is\ better\ than\ f(m^{i,iter}) \\ m^{i,iter} \ otherwise \end{cases}\tag{3}$$

**Step 8:** Check the end criterion by repeating steps from 4-7 until the termination criterion is met.

### 7.2.4. Pseudocode of CSA

```
Random initialization of the position of a flock of N crows in the search space
Evaluation of the position of the crows
Initialization of the memory of each crow
While iter < iter_max
    for i=1:N (all N crows of the flock)
        Random selection of one of the crows to follow (e.g. j)
        Define an awareness probability
```

While iter < iter_max
  for i=1: N (all N crows of the flock)
    Random selection of one of the crows to follow (e.g. j)
    Define an awareness probability
      If r_j ≥ AP^{i,iter}
        x^{i,iter+1} = x^{i,iter} + r_i * fl^{i,iter} * (m^{j,iter} - x^{i,iter})
      else
        x^{i,iter+1} = a random position of search space
      End if
  End for
Checking the feasibility of new positions
Evaluation of the new position of the Crow
Updation of the memory of Crows
End while

## 7.3. CSA STUDIES

We concentrate on documenting advances on CSA in the form of structured publications in this study. They separate developments into three aspects:

- a. Changes to CSA include Chaotic CSA, Fuzzy CSA, and other minor modifications.
- b. Hybridization of CSA with other metaheuristic methods, including Bat Algorithm (BA), Ant Colony Optimization (ACO), Grey Wolf Optimization (GWP), Genetic Algorithm (GA), Lion Algorithm (LA), Cat Swarm Optimization (CSO).
- c. CSA extensions to other fields of optimization including multi-objective, and binary optimization.
- d. Other applications

### 7.3.1. Modifications of CSA

#### 7.3.1.1. Chaotic CSA(CCSA)

CSA has incorporated principles related to chaos theory to boost its efficiency. Gehad [10] introduced chaotic maps with CSA. The proposed algorithm deals

| Paper | Proposed method | Dataset used | Method objective | Findings |
|---|---|---|---|---|
| Ahmed [17] | Improved fast fuzzy c-means using CSA (FFCM-CSA) | Images from maize field | 1. The method is used for crop identification in agriculture. 2. Aims to increase the computational performance of FFCM by using CSA to find clusters centers due to its ability to provide very accurate results in the clustering process, which contributes to avoiding the occurrence of FFCM in the local Optima | The method finds the ideal centers value and avoid falling into the local optima. |
| Parvathavarthini [18] | Intuitionist fuzzy clustering focused on CSA with neighborhood attraction called(CrSA-IFCM-NA) | Breast cancer data | To detect cancer masses at an early stage through effective clustering with neighborhood attraction. | Its results showed accuracy in detecting cancerous masses at an early stage through its ability to effectively separate cancerous masses from mammography images. |
| Ahmed [5] | CSA with chaos theory and fuzzy c-means algorithm (CFCSA) | Breast cancer, diabetes, lung cancer, hepatitis, Radiopaedia CT liver, and cardiotocography | Used for feature selection for medical diagnostic problems | It showed good results in the diagnosis of these diseases compared to other algorithms |

(Table 2) cont......

| paper | Proposed method | Method Objectives | Findings |
|---|---|---|---|
| Hao Wu [29] | Levy Flight Crow Search Algorithm [LFCSA] | A finite element model updating (FEMU) to obtain higher accuracy in the process of analyzing fatigue and vibration of an elastic body. Where the algorithm was applied to update two different states: simple structure (beam) and complex structure (gearbox housing) | The LFCSA algorithm was compared with both CSA and LFPSO as its results showed obvious effects on FEMU as it showed high accuracy in addition to high-convergence speed and global search ability in both simple and complex structures. |
| Deepak [30] | A modified Crow Search Algorithm [MCSA] | This method aims to reach the optimum solution in the process of extracting the usability features that are most beneficial from the hierarchical model | The results of the algorithm were compared with BBA, CSA, and MWOA where It showed better results in the process of selecting features compared to other algorithms |
| Ronali [31] | Improved Crow Search Algorithm [ICSA] | The goal of this method is the ability to schedule dynamic tasks in the heterogeneous multiprocessor system which is a difficult problem in a network environment. | Its results showed superiority over many other standard algorithms that were compared with it like Genetic Based Bacteria Foraging (GBF), Bacteria Foraging Optimization (BFO) |
| Bighnaraj [32] | Enhanced Crow Search Algorithm (ECSA) | This method has used for solving classification problem in data extraction by enhancing the functional neural network linking system using an enhanced CSA to avoid convergence and early stagnation of the system | To assess the performance of the proposed model, the CSA FLA-based FLA trainers were compared with FLANN GA-based trainers and PSO FLANN trainers. The CSA-optimized model showed superiority in the classification speed and accuracy with fewer iterations compared to other models. |

### 7.3.2. Hybridization

CSA has been combined with some conventional and evolutionary optimization algorithms to take advantage of both approaches and counteract each other's weaknesses. Both the traditional and evolutionary optimization algorithms have their own strength and weakness. Traditional algorithms generally rely on finding a random solution that is chosen randomly, and then it tries to find the optimal solution repeatedly as it depends on two basic parameters, which are the search direction and the length of the step [33]. Traditional optimization tools are classified into two groups, namely direct search, and gradient-based methods, as these tools suffer from a lack of guarantee of a globally optimal solution due to the dependence of the final solution on the random initial solution in addition to
