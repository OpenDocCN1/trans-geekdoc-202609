
The first type of agents represented either cardiac tissue or blood vessels. They have the attribute “damage” and “inflammation.” The second type of agents represented either MSC, endothelial, or cardiomyocyte. For the type of agent MSC, the attributes were “cardiomyocyte differentiation probability,” “endothelial differentiation probability,” “differentiation time counter,” “duration of the differentiation process,” and “following cell type.” For the type of agent endothelial cells and cardiomyocytes, the attributes were “probability of dying by apoptosis” and “influence over the differentiation decision.”

The simulations were expensive and slow in time. They required 50 GB RAM server to lower by 83% what it would have taken on an 8 GB RAM desktop computer. Even then, this multiagent system was developed as a general model based on empirical knowledge and available research. The authors recognize that some simplifications were introduced in order to get the simulations to produce good results in the available timeframe.

The simulations were validated by considering the physical behavior of the system: The authors performed two simulations that behaved as expected, namely, the anti-inflammatory effect that MSCs exert over the infarcted myocardium and the population size of each cell type (MSC, endothelial, and cardiomyocyte) over time. Both were 60-day simulations.

Finally, there was no cell migration in any of the collagen scaffolds. The authors adduce this situation to the lack of significant tensile forces for focal adhesions to occur.

### 1.4.5 Cellular automata

Cellular automata are a set of discrete elements that evolve in time according to predefined rules. Specifically, a distance or neighborhood is defined and each cell acquires a new state (usually living or dead), according to its previous value and those in its immediate predefined neighborhood. This has allowed us to use them to successfully model complex phenomena ([Pérez Betancourt et al., 2015](#bodymatter-001.xhtml#b_9783110648195-001_ref_031)).

The authors built a computer model based on cellular automata ([Czarnecki et al., 2014](#bodymatter-001.xhtml#b_9783110648195-001_ref_011)). The objective of the work is twofold: (1) to study the effects of crystallinity, orientation, and surface roughness in cell growth in three carbon fiber scaffolds, and (2) model this effect using cellular automata, as a first step toward developing a proper scaffold design tool.

As for the experimental data, three different types of carbon fibers were tested (T300, P25, and P120). The total number of samples, by type of fiber, was six because they used six-well tissue culture plates. Each experiment was repeated three times. The cells considered were primary human osteoblasts.

The authors propose a two-dimensional grid for cellular automata modeling of the adhesion, differentiation, and proliferation processes, where the size of the grid is the diameter of an osteoblast as well as the size of the fiber, 8 µm. As for the reproduction and life or death of each cell, they use two functions: a Lagrange polynomial and an exponential function, both influenced by the physical parameters of the fiber and using linear correlation of the experimental results to adjust the three parameters found in each model. Each lattice site can assume one of three states (empty, occupied, or blocked). The obtained results showed that the polynomial obtains better results than exponential one. The authors use IBM SPSS© software to make a statistical comparison between the numerical results and the obtained images, obtaining a maximum difference of 13.2% among them in the polynomial case. MATLAB© software package was used for all algorithms and simulations.

In this work, the impact of the considered variables: crystallinity, surface roughness, and material orientation were studied. The results obtained by the authors propose carbon fiber as suitable for osteoblast growth obtaining a good simulation validation and providing most of the necessary experimental and methodological details. They also confirm that material alignment is critical since multidirectional scaffolds showed better cell growth than unidirectional ones.

These authors also implemented a cellular automata model to simulate cell adhesion and cell proliferation of an initial cell population when they are seeded on a scaffold ([Vivas et al., 2015](#bodymatter-001.xhtml#b_9783110648195-001_ref_040)).

The cells considered were 3T3 murine fibroblasts. The model was a two-dimensional monolayer culture. The output variables considered were cell settling time in culture, adhesion time, and proliferation time.

The simulated area was 1 mm of length and 0.5 mm of height. Then, it was discretized in squares, resulting in 67 horizontal and 33 vertical elements. Each element was a square with 15 µm of side. They represented the cell as a 15 µm diameter circle. Cells were placed in a random way. The first part of the simulation consisted of evaluating at what time the cells came into contact with the surface in seconds. To do this, the authors began the simulation with a population of 50 cells, randomly distributed. The results they obtained were 4 s so that the first cell has contact with the surface and 34 s so that all the cells have reached the surface.

The second part of the study consisted of simulating the adhesion process, which takes place once the cells have come into contact with the surface of the scaffold. As cells were randomly placed, the adhesion time varies according to the distance to the substrate. The results obtained were: focal adhesions were observed after 100 min. During this time, cells preserve their rounded morphological shape. After that, cell membrane molecules reorganize. The cytoskeleton and glycocalyx are also reorganized to minimize repulsion between cell and substrate. This will allow FA to mature so that it increases the number of anchoring sites. A total of 236 iterations were required to simulate the cell adhesion process.

The simulation results were contrasted with an experimental part that consisted of 3T3 fibroblast culture, which was then plated into T25 cell culture flasks. Then, the evaluations of cell adhesion and cell proliferation were made triplicate and quadruplicate, respectively.

This work only makes a two-dimensional approximation of a scaffold. Although some details are provided for the cellular automata rules and grid, more details should be provided for the experimental setup of the program.

## 1.5 Conclusions and future works

There are very few examples of AI applications to bone scaffolds in tissue engineering that consider cell adhesion as an important part of their analysis. In this work, we have presented the results of the literature review focused on answering the question: what are the AI techniques used and what exactly have they been used for?

In response to those questions, we found that different types of neural networks (combined with PSO, SVM, and SVR) have been used and cellular automata and multiagent systems have been applied to works focusing on scaffolds and cell adhesion. The use is mainly for modeling a part of the process to perceive and interpret the role of each variable in the process (as opposed to directly trying to optimize some aspect of the constructive process). [Table 1.1](#bodymatter-001.xhtml#b_9783110648195-001_tab_001) shows a summary of the works analyzed and a comparison of them with respect to their main characteristics: method used, input variables, output variables, validation of results, and so on.

Table 1.1:Summary of the works analyzed.

| Title || Year || Method || Input parameters || Amount of data || k-Fold cross-validation || Output variables || Validate results? || Reference |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Optimal design of a 3D-printed scaffold using intelligent evolutionary algorithms || 2016 || PSO |
| AANN |
