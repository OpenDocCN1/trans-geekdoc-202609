
追逐其他乌鸦以获取其食物。它已成功应用于优化的各个科学与工程领域 [9]。然而，文献中缺乏对该算法的当前且聚焦的分析。此外，CSA 不再与新算法进行比较；此后，许多新算法已被引入。因此，在更广泛的测试函数上对 CSA 进行实验并将其与现代可靠的算法进行比较，将进一步揭示该算法的使用。结果，本文的目标首先是研究 CSA 的原理及其基本结构和特征，其次，提供对最先进 CSA 算法的全面详细综述。第三，它提供了各种 CSA 应用，尤其是在医学领域。最后，我们通过总结进展并评估研究中的未来趋势来结束本文。这项工作将极大地帮助研究人员在该领域的进一步发展和实施工作。

## 7.2. 烏鴉搜索優化

### 7.2.1. 烏鴉搜索優化概述

优化在多个领域发挥了非常重要的作用，不限于工程问题。这些问题包含复杂的目标函数、各种决策变量和庞大的约束集，这增加了本已复杂的优化问题的复杂性。此类约束将搜索从传统的优化方法带到现代分析领域，即由 Beni 和 Wang 在 1980 年代开创的群体智能 [6]。SI 模仿自然界生物的集体智力 [6]。每个新算法都关注两个特征：首先，找到接近实际最优解的解，从而减少它们之间的差距，其次，以尽可能少的时间找到解，从而减少搜索时间。过去几年提出了几种优化算法，因为每个算法都有其自身的优缺点。乌鸦搜索算法是一种新开发的算法，它模仿乌鸦的社会智能及其觅食方式。它是一种受乌鸦智能行为启发的元启发式算法。乌鸦是世界上最聪明的生物之一，如镜子测试所示 [9]。有大量证据表明乌鸦的聪明才智。乌鸦可以记住面孔、相互交流信息、获取食物并通过隐藏食物来源将其远离他人 [9]。它们是聪明的罪犯，因为它们会额外注意，例如不时改变藏匿地点，以便以后避免成为受害者。乌鸦利用一种学习方法来隐藏食物并夺取他人的食物。在随后的章节中，CSA 的特征、CSA 的算法结构以及伪代码和流程图已准备好用于理解和在不同优化领域实施 CSA。

![](img/be45bf301a3c0ebefb162571e2625fab_166_0.png)

Fig. (2). Flowchart of CSA.

CSA 程序步骤如下：

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

### 7.2.4. CSA 伪代码

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

## 7.3. CSA 研究

We concentrate on documenting advances on CSA in the form of structured publications in this study. They separate developments into three aspects:

- a. Changes to CSA include Chaotic CSA, Fuzzy CSA, and other minor modifications.
- b. Hybridization of CSA with other metaheuristic methods, including Bat Algorithm (BA), Ant Colony Optimization (ACO), Grey Wolf Optimization (GWP), Genetic Algorithm (GA), Lion Algorithm (LA), Cat Swarm Optimization (CSO).
- c. CSA extensions to other fields of optimization including multi-objective, and binary optimization.
- d. Other applications

### 7.3.1. CSA 的修改

#### 7.3.1.1. 混沌 CSA(CCSA)

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

### 7.3.2. 混合

CSA has been combined with some conventional and evolutionary optimization algorithms to take advantage of both approaches and counteract each other's weaknesses. Both the traditional and evolutionary optimization algorithms have their own strength and weakness. Traditional algorithms generally rely on finding a random solution that is chosen randomly, and then it tries to find the optimal solution repeatedly as it depends on two basic parameters, which are the search direction and the length of the step [33]. Traditional optimization tools are classified into two groups, namely direct search, and gradient-based methods, as these tools suffer from a lack of guarantee of a globally optimal solution due to the dependence of the final solution on the random initial solution in addition to
