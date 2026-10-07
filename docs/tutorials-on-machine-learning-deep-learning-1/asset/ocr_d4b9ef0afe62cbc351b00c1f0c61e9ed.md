# Movie 1

# Movie 2

# Movie 3

# Movie 4

![](bbox=[0.237, 0.038, 0.762, 0.303])

Movie 1

Movie 2

Movie 3

Movie 4

Visible
Input
Nodes

Hidden
Nodes

Visible
Output
Nodes

+   Let's look at an input. Let's say as an input, we get 1 for input, and 0 for others. The person who just like Movie 1, and dislikes the rest of the movies.

> In this case, hidden nodes will be "+1" and "+1" because blue synapse is multiplying by "+1". And the 0 in the input nodes, they will just add zero, and not going to contribute to the hidden nodes.
For the first output-node:
1*(blue-synapse) = (1+1) + (1+1) = 2
For the 2nd and 3rd output-node:
1*(blue-synapse) + 1*(black-synapse) = (1+1) + (1*-1) = 0
For the 4th output-node:
1*(black-synapse) + 1*(black-synapse) = (1*-1) + (1*-1) = -2

![](bbox=[0.368, 0.395, 0.882, 0.565])

![](bbox=[0.117, 0.703, 0.882, 0.893])

+   As your outputs are both that are are preliminary outputs. In Auto Encoder we use a SOFTMAX function for the end. As you see, final output is indeed identical to our output.

+   Softmax takes the highest value, so in this case it is "2" and it turns into "1" and everything into "0".