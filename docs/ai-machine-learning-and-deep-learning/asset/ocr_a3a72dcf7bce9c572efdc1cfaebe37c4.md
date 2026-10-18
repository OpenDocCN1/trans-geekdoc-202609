where is the iterate of the solution and Then we solve the following(1.3.12) optimization problem:

subject to by finding the saddle node of the Lagrangian given by: (1.3.13)

The optimization problem can be solved to obtain the saddle(1.3.14) node

This saddle node can be considered the orthogonal projection of onto the decision hyperplane $g$ at iteration and the iteration stops when is misclassified; i.e.,

The multiclass (in one-vs.-all scheme) approach of the DeepFool attack follows the iterative linearization procedure in the binary case, except that an attacker needs to determine the closest decision boundary $l$ to the input $x$. The iterative linear approximation method used to find the minimum perturbation is a greedy method that may not guarantee the global minimum. Moreover, the closest distance from the original input to the nearest decision boundary may not be equivalent to the minimum difference observed by human eyes. In practice, DeepFool usually generates small unnoticeable perturbations.

So far, we have only considered untargeted DeepFool attacks. A targeted version of DeepFool can be achieved if the input $x$ is pushed toward the boundary of a target class subject to Furthermore, the DeepFool attack can also be adapted to find the minimal distorted perturbation for any $p$-norm, where If interested, see [28] for details.

# 1.3.5  Fast Adaptive Boundary Attack

The fast adaptive boundary attack, proposed by Croce and Hein [25], is an extension of the DeepFool attack [20]. Specifically, the computation of for a FAB attack follows the DeepFool algorithm closely. The main differences between the two types of attacks are that a DeepFool attacker projects onto the decision hyperplane $g$ only, whereas a FAB attacker projects onto the intersection of and the approximated decision hyperplane with the following additional steps.