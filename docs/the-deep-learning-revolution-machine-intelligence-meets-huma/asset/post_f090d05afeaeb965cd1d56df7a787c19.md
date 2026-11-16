

![](img/dd452eef0506ea820c436fef2f776436_111_0.png)

![](img/dd452eef0506ea820c436fef2f776436_111_1.png)

![](img/dd452eef0506ea820c436fef2f776436_111_2.png)

![](img/dd452eef0506ea820c436fef2f776436_111_3.png)

![](img/dd452eef0506ea820c436fef2f776436_111_4.png)

Figure 7.4

Separating figure from ground with a Boltzmann machine. (Above) The square units in the network identify the figure and the triangular edge units identify the outline, with the signs of the connections indicated. Edge units can point toward or away from the figure. (Below) (a) Snapshot of a network with attention on the inside of the “C.” The temperature starts out high so that the units are fluctuating between on and off. (b) As the temperature drops, units on the inside of the “C” begin to coalesce, with support from the boundary units that point to the inside. Units on the outside that do not have attention or edge input disappear as the temperature is decreased. (c) The figure is filled in when attending the inside when the temperature reaches zero. (d) The outside is filled in when the process is repeated while attending the outside. From P. K. Kienker, T. J. Sejnowski, G. E. Hinton, and L. E. Schumacher, “Separating Figure from Ground with a Parallel Network,” Perception 15 (1986): 197–216, Below: figure 6; above: figure 3.

perceptron, the Boltzmann machine also had units in between, which we called “hidden units” (box 7.2). By presenting input-output pairs and applying the learning algorithm, the Boltzmann network learned the desired mapping. But the goal was not just to memorize the pairs; it was also to correctly categorize new inputs that were not used to train the network. Also, because it is always fluctuating, the Boltzmann machine is learning the probability distribution—how often each output state is visited for a given input pattern—which makes it generative: after learning, it can generate new input samples by clamping each output category.

## Hebbian Synaptic Plasticity

The surprise was that the Boltzmann machine learning algorithm turned out to have a long history in neuroscience, going back to the psychologist Donald O. Hebb, who in his book The Organization of Behavior postulated that when two neurons fired together, the synapse between them should strengthen:

> Let us assume that the persistence or repetition of a reverberatory activity (or “trace”) tends to induce lasting cellular changes that add to its stability. When an axon of cell A is near enough to excite a cell B and repeatedly or persistently takes part in firing it, some growth process or metabolic change takes place in one or both cells such that A’s efficiency, as one of the cells firing B, is increased.¹⁶

This may be the most famous prediction in all of neuroscience. Hebbian synaptic plasticity was later discovered in the hippocampus, an important brain area for long-term memory. When a hippocampal pyramidal cell receives a strong input at the same time the neuron is spiking, the strength of the synapse is increased. Subsequent experiments showed that the strengthening was based on the conjunction of transmitter release from the synapse and elevation of the voltage in the recipient neuron. Moreover, this conjunctive occurrence was recognized by a special receptor, the NMDA (N-methyl-D-aspartate) glutamate receptor that triggers long-term potentiation (LTP), which is rapid in onset and long lasting, a good candidate for the substrate of long-term memory. Hebbian plasticity at a synapse is governed by coincidences between inputs and outputs, just like the Boltzmann machine learning algorithm (see box 7.2).

Even more amazing, the Boltzmann machine had to go to sleep to be able to learn. Its learning algorithm had two phases. In the first or “wake” phase, with the input and output patterns were clamped to the desired mapping, the units in the network were updated many times to settle down to an equilibrium, and the fraction of time each pair of units were on together was counted. In the second or “sleep” phase, the input and output units were set free, and the fraction of time each pair of units were on together was counted in a free running condition. Each connection strength was then updated in proportion to the difference between the coincidence rates in the wake and sleep phases (box 7.2). The computational reason for the sleep phase is to determine which part of the clamped correlations was due to external causes. Without subtracting the internally generated correlations, the network would strengthen the internal patterns of activity and would learn to ignore outside influences, a network version of folie à deux. Interestingly, extreme sleep deprivation in humans leads to delusional states, a common problem in intensive care units in hospitals that have no windows and constant lighting. Patients with schizophrenia often have sleep disorders that can contribute to their delusional ideation. We were convinced that we were on the right track to understanding how the brain worked.

## Learning Mirror Symmetries

A problem the Boltzmann machine could solve but a perceptron could not is how to learn mirror symmetries.¹⁷ The human body is bilaterally symmetric along a vertical axis. We can generate a large number of random patterns with this axis of symmetry, as shown in figure 7.5, and also with horizontal and diagonal axes of symmetry. In our Boltzmann machine network, 10×10 blocks of binary inputs projected to sixteen hidden units, which in turn projected to three output units, one for each of the three possible axes of symmetry. The Boltzmann machine was 90 percent successful at classifying the axis of symmetry of novel inputs after being trained on 6,000 symmetric input patterns. A perceptron can do no better than chance because a single input carries no information about the symmetry of the pattern; the correlations between pairs of inputs must be interrogated. What is remarkable is that the array of inputs a human observer sees is not what the Boltzmann machine sees since each hidden unit receives inputs from the whole array in no particular order. The equivalent problem for an observer would be to randomize the locations of the input units in the array, which would make the array look random to the observer even though there is a hidden symmetry.

One day, I was watching the display and calling the symmetry of each input pattern at a rate of two per second. Neal Cohen, then a colleague in the Psychology Department at Johns Hopkins, was also watching the

![](img/dd452eef0506ea820c436fef2f776436_114_0.png)

Figure 7.5

Symmetric random patterns. Each 10×10 array has a vertical, horizontal, or diagonal axis of mirror symmetry. The goal of the network model is to learn how to classify the axis of the symmetry in new patterns not used to train the network model. From T. J. Sejnowski, P. K. Kienker, and G. E. Hinton, “Learning Symmetry Groups with Hidden Units: Beyond the Perceptron,” Physica 22D (1986): 260–275, figure 4.

display but could not categorize the symmetries without scrutinizing the patterns and was amazed that I could. Watching the display for days as the Boltzmann machine learned had trained my visual system to detect the symmetry automatically, without having to look around the display. Neal and I designed an experiment with undergraduates as naïve subjects and followed their progress.¹⁸ At the beginning, it took them many seconds to get the right symmetry, but after a few days of training, they were much faster, and by the end of the experiment, they could detect the symmetries so quickly and effortlessly that they could talk with us during the task and still get all of them right. This was remarkably fast perceptual learning.

I taught “The Biophysics of Computation” at Johns Hopkins, a course that attracted several talented students and researchers. Ben Yuhas was a graduate student in the Department of Electrical Engineering who worked with me and for his doctoral dissertation, he trained a neural network to read lips.¹⁹ There is information on the sound of a voice in the movement of a person’s mouth. Ben’s network transformed images of mouths into the corresponding frequency spectrum of the sound being generated at each time step. This could then be added to the noisy sound spectrum to improve speech recognition. His fellow graduate student Andreas Andreou, a Greek Cypriot with a booming voice, was building analog VLSI (very large-scale integration) chips in the basement of Barton Hall. (These chips are featured in chapter 14.) In the 1980s, there was hostility from faculty in their department toward neural networks, which was common at many institutions, but this did not deter either Ben or Andreas. Indeed, Andreas would go on to become a full professor at Hopkins and to cofound the Johns Hopkins University Center for Language and Speech Processing. Ben has a consulting group on data science for political and corporate clients.

## Learning to Recognize Handwritten Zip Codes

More recently, Geoffrey Hinton and his students at the University of Toronto trained a Boltzmann machine with three layers of hidden units to classify handwritten zip codes with high accuracy (figure 7.6).²⁰ Because the Boltzmann network had feedback as well as feedforward connections, it was possible to run the network in reverse, clamping one of the output units and generating input patterns that corresponded to the clamped output unit (figure 7.7). Generative networks capture the statistical structure of the training set and the samples they generate inherit these properties. It is as if these networks go to sleep and activate at the highest level of the networks generates sequences of dreamlike states on the input layer.

Although the rise of neural networks in physics and engineering was swift, traditional cognitive scientists were slow to accept it as a formalism

