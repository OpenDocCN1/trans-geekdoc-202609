![](bbox=[0.17, 0.1, 0.46, 0.28])

**Figure 5.** Multiple nodes intersect each other.

As shown in Figures 2~6, the hole in Figure 2 is the largest, and its patching priority is the highest. For Figures 3~5, the patching priority increases with the size of the circumscribed circle. Figure 6 needs not to be covered, for no hole is generated.

![](bbox=[0.17, 0.36, 0.45, 0.51])

**Figure 6.** Nodes A, B and C intersect each other in pairs.

# 3.2. Steps

The specific hole patching steps are as follows:

+   1. After randomly arranging static nodes, obtain the specific location of each node and store it in the list of locations v.
2. Create a new list of the patching locations List and a temporary information list temp.
3. Divide the adjacent three nodes into a group, make a common circumscribed circle of each group of three nodes, calculate the area of the circumscribed circle G$_{1} · · ·$ G$_{N}$, and store it into the List.
4. Initialize the temporary information list temp.
5. Carry out a loop, traverse the list, directly update the first G$_{1}$ in the list and its related location information into temp. Continue to traverse the list, and take G$_{2}$ to compare it with G$_{1}$ in temp. If G$_{2}$ > G$_{1}$, add G$_{2}$ and its related location information into temp, and remove G$_{1}$ and its related location information from the list. Otherwise, retain G$_{1}$ in temp. When all items in the list are traversed, send the marked locations in the List to the mobile node to guide its movement.
6. Repeat Steps 3~5 until the mobile nodes are all used, and terminate the loop.

# 4. Simulation Experiments

To demonstrate the effectiveness of our algorithm, network coverage and redundancy were analyzed, using the software simulation platforms of Win10 and Matlab 2016b.

The detection area is of the size 125 m × 100 m. A total of 25 static nodes were deployed randomly inside the area, $S = \{S_{1}, S_{2} · · · S_{25}\}$. The nodes fall into two categories. The sensing radii of the two types of nodes are R$_{S1}$ and R$_{S2}$, respectively; the communication radii of the two types of nodes are R$_{C1}$ and R$_{C2}$, respectively. These radii satisfy R$_{C1} = 2R_{S1}$, R$_{C2} = 2R_{S2}$, and R$_{S2} = 1.5R_{S1}$. The sensing radii of the nodes are R$_{S1} = 8$ m and