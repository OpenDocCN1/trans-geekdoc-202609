| NN-1 | NN-2 | NN-3 |
| :--- | :--- | :--- |
| | tanh is a non-linear activation function like we have used MAX operation (non-linear) in figure 6.35.

hₜ = 
[ F(NN_F)  -  ]
[ o₁   0  ]
[ o₂   0  ]
[ o₃   0  ]
[ -   -   ]
[ o₄   0  ]
[ o₅   1  ]
[ o₆   0  ] | |

Table 6.3: Neural network weight's in RNN

+   1. The current input x(t) is provided to the neural network.
+   2. Then by using the current input and the previous state, we determine the current state of the input h(t).
+   3. So, now the current state h(t) becomes the previous state h(t-1) for the upcoming input.
+   4. Now according to the need, as many as time stamps can be used.
+   5. After the completion of all the timestamps, the final state is used to determine the output .

The obtained output is compared with the actual output, which generates the percentage of error.

Finally, the backpropagation process is used for updating the weight values, and accordingly, the neural network is trained.

# # Representation of recurrent relationships

We can further generalize the equation in terms of recurrent equations using a classification problem known as labeling of names or text labeling. In this given sentence, we have to find the names in that. Like we can take sentences from various corpora’s available in natural toolkit (NLTK) libraries.

+   - S1: <s>AB De Villiers is called as 360-degree player. </s>
+   - S2: <s>Rohit Sharma plays very well the bowler of Pakistan whose name is Shaheen Afridi.</s>

So in this problem, input is the sentence that is represented as x<^> = (10,000 × 1), which is converted as an input vector of, say, 10,000 dimensions.