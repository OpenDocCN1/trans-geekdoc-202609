# Chapter 1 Introduction to Data Structures

| Data Structure | Advantages | Disadvantages |
| --- | --- | --- |
| Stack | Provides last-in-first-out access | Slow access to other items |
| Queue | Provides first-in-first-out access | Slow access to other items |
| Linked list | Quick insertion and deletion | Slow search |
| Binary tree | Quick search, insertion, deletion (if tree remains balanced) | Deletion algorithm is complex |
| Red-Black tree | Quick search, insertion, deletion. Tree always balanced | Complex |
| 2-3-4 tree | Quick search, insertion, deletion. Tree always balanced. Similar trees use good for storage | Complex |
| Hash | Very fast access if key known. Fast insertion | Slow deletion, access slow if key not known, inefficient memory usage |
| Heap | Fast insertion, deletion, access to large item | Slow access to other items |
| Graph | Models real world situations | Some algorithms are slow and complex |

# 1.5 ALGORITHM

An algorithm is a step-by-step finite sequence of instructions to solve a problem. Every algorithm must satisfy the following condition:

**Input:** zero or more quantities.

**Output:** at least one quantity is produced.

**Definiteness:** each instruction is clear and unambiguous.

**Finiteness:** if we trace the instructions of an algorithm, then for all cases the algorithm will terminate after a finite number of steps.

**Effectiveness:** every instruction must be sufficiently basic that it can in principle be carried out by a person using only pencil and paper.

# 1.6 APPROACH FOR ALGORITHM DESIGN

There are two basic approaches for designing an algorithm; they are Top-Down Approach and Bottom-Up Approach.

**Top-Down Approach:** a top-down approach (also known as stepwise design and in some cases used as a synonym of **decomposition**) is essentially the breaking down of a system to gain insight into its compositional sub-systems in a reverse engineering fashion. In a top-down approach an overview of the system is formulated, but not detailing any first-level subsystems. Each subsystem is then refined in yet greater detail, sometimes in many additional subsystem levels, until the entire specification is reduced to base elements. A top-down model is often specified with the assistance of “black boxes”, these make it easier to