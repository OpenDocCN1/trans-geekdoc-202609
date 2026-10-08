# Deep Learning-Based Forward Modeling and Inversion Techniques

![](bbox=[0.205, 0.095, 0.758, 0.345])

**FIGURE 4.17**
The inversion results of the space-related thermal conductivity.

fact, the predicted results of the NMM coincide well with the ground truth while the error is tiny.

B. Temperature-related
The thermal conductivity of materials can vary with temperature, so that it is crucial to figure out the relationship in thermal science. For more practical scenarios, the data sets include metals, glasses and inorganic salts. For most metals, the thermal conductivity decreases with temperature, while for glasses, it increases with temperature. In addition, the data set contains a series of inorganic salts, whose thermal conductivity changes non-monotonically with temperature. Figure 4.18 presents three characteristic materials, the copper (metal), silicon dioxide (glass) and lithium fluoride (inorganic salt), whose crystal structure are exhibited in (a) to (c). In this part, some randomly selected specimen in the testing data set are displayed in Figure 4.19, in which the dot line is the prediction and the solid line is the ground truth. Obviously, the framework is able to yield prediction results in all the three cases, which emerges certain universality.

C. Time-related
Lastly, in certain practical scenarios like cement hardening, the thermal conductivity changes with time. Hence it is valuable to explore whether the developed NMM can be applicable to retrieve the thermal conductivity changing with time. Here, a few examples are selected to measure the performance intuitively. As demonstrated in Figure 4.20, the solid line and the dot line are the ground truth and the predictions, respectively. It is lucid, that the degree of coincidence between the two families of curves is fairly high, which