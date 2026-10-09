+   2. a Partition all data instances at the node by the value of the attribute.
b Compute the **information gain ratio** from the partitioning.

$$\mathrm{Gain\ ratio}(S, A) = \frac{\mathrm{Gain}(S, A)}{\mathrm{Split\ information}(S, A)}$$

$\mathrm{Gain}(S, A)$ = expected reduction in entropy due to sorting on $A$, $S = \{X\}$ is a collection of training examples.

$$\mathrm{Gain}(S, A) \equiv \mathrm{Entropy}(S) - \sum_{v \in \mathrm{Values}(A)} \frac{|S_{v}|}{|S|} \mathrm{Entropy}(S_{v})$$

where $\mathrm{Values}(A)$ is the set of all possible values for attribute $A$, and $S_{v}$ is the subset of $S$ for which attribute $A$ has value $v$ (i.e., $S_{v} = \{s \in S | A(s) = v\}$).

$$\mathrm{Split\ information}(S, A) \equiv -\sum_{i=1}^{c} \frac{|S_{i}|}{|S|} \log_{2} \frac{|S_{i}|}{|S|}$$

where $S_{i}$ is a subset of $S$ for which $A$ has value $v_{i}$, and $c$ is the number of class.

```
**end for**
```

+   3. Identify a feature that generates the highest information gain ratio.
Exploit this feature to be the splitting criterion at the current node.
   **if** the best information gain ratio is 0 **then**
   label the current node as a leaf and return.

```
**end if**
```

+   4. Partition all instances according to the attribute value of the best feature.

+   5. Denote each partition as a child node of the current node.

+   6. a. If the child node is “pure” (has instances from only one class), label it as a leaf and return.
b. If not set the child node as the current node and repeat Step 2.

```
**end for**
**end function**
```