
Let us now plot predictions from the two expressions in Figure 9.10. It is clear that there is good convergence between the two expressions. 93 When we apply these expressions to predict temperature rise in RC beams, Figure 9.11 shows that these expressions can realize decent predictions. 94

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_545_0.png)

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_545_1.png)

93 In fact, R and R² for predictions from these two expressions are unity.

94 I would like to make very clear that these expressions, while seeming to be able to capture the phenomenon on hand, they cannot be thought of as causal expressions (as in, they may not articulate the cause → effect relationships).

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_546_0.png)

Figure 9.10 (Cont'd) Outcome of software used in deriving symbolic expressions for temperature rise in RC beams under standard fire conditions.

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_546_1.png)

(a) Overall comparison

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_546_2.png)

(b) NSC-1 tested by Raut and Kodur [25]

(Continued)

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_547_0.png)

(c) B10 tested by Lie and Woollerton [26]

Figure 9.11 (Cont'd) Comparison between descriptive expressions and observed temperature rise under fire conditions.

## Example no. 4: Descriptive expression of a classification problem.

The last example will tackle a classification problem with regard to transportation infrastructure. Say that we have a collection of bridges, would we be able to derive an expression that can identify which bridges are vulnerable to collapse? 95

This dataset comprises the following features, structural systems (S), construction materials (M), Span (P), Age (A), and the number of lanes (N). 96 The outcome in this dataset is binary (collapse, no collapse).

To carry out a classification analysis, a few tweaks are to be applied to Eureqa. These are shown in the following snippets as well as in the provided Eureqa file. The outcome of this analysis is this Step function, which returns a value of unity if a bridge is vulnerable to collapse.

Collapse = step (564.74 × M – 1278.08 – 0.81 × P – 4.72 × A – 14.61 × N – 44.19 × S – 632.72
× or (0.85 × M – 2.70 × P – 116.91))
(9.8)

### Step 1: Assign the proper Formula building-blocks (you may use the Step or Logistic functions).

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_547_1.png)

### Step 2: Keep an eye on the AUC ROC Error.

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_548_0.png)

### Step 3: Arrive at a possible descriptive expression.

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_548_1.png)

97 We usually calculate the AUC ROC. Eureqa calculates the error (i.e., 1-AUC ROC) which implies that smaller error is favorable.

### 9.3.16 A Note

This section was all about the following concept. Can we use ML to arrive at a simple model that represents a formula? If so, how? As you can see, we can derive such expressions simply with many of the available software that we have access to. We can also do the same via programming scripts.

What I would like to remember is that for some problems, arriving at such descriptive expressions can be of merit as an engineer will be substituted into a formula as opposed to a ML model. 98 The same can also be extended to the following question, could you just update codal equations via symbolic regression into one equation of much higher performance? This is a good question. My answer is that while symbolic regression searches for symbols, the goal of codal expressions is not just to predict a phenomenon with high accuracy. These expressions go beyond that to incorporate reliability and confidence measures. The same expressions often arise from first principles vs. a data-driven analysis. 99

Now, what if we can supplement symbolic regression with reliability and confidence measures, while at the same time incorporating domain knowledge and physics and causal principles? This is a good question that I hope we can address one day.

## 9.4 Mapping Functions

The previous discussion on symbolic regression opens the door to this section on _mapping functions_. While symbolic regression ties a set of features together 100 without considering any insights in our data, _mapping functions_, on the other hand, ensure that features are properly identified, selected, and tied by incorporating physics principles, domain knowledge, and insights from our data. 101 The overarching goal of a _mapping function_ 102 is to mimic a ML model as much as possible to allow the engineer to adopt and apply the principles of ML without having to hassle with building models or programming. One of the great strengths of a _mapping function_, and given its mathematical representation, is its ability to form the basis for a hypothesis which could then be tested and explored.

### 9.4.1 Big Ideas

Let me start with the following. Deriving a _mapping function_ requires an understanding of the phenomenon we happen to be interested in. At a minimum, we need observations that depict some form of consistent response regarding the problem on hand. It is because of this consistency that it could be possible to encode the response we see into a mathematical expression that can be repeatedly used with confidence. To ensure its wide acceptance and ease of use, a _mapping function_ is preferred to be compact 103 and reliable.

To demonstrate the concept of _mapping functions_, allow me to revert back to some visual examples. 104

### 9.4.1.1 Sectional Phenomenon

In a general sense, structural engineering phenomena that is related to the _sectional_ level (i.e., moment) are primarily governed by two components: geometric features and material properties comprising this structural member.

To reinforce this discussion, I will be referring to Equation 9.1, which we can arrive at from mechanics. This equation illustrates the functional relation between the _geometry_ and _material properties_ for the moment capacity of a typical rectangular reinforced concrete (RC) beam with tensile reinforcement. Thus, at a sectional level, the _governing parameters_ are expected to belong to the class of geometric features and material properties.

98 Which requires access to the code, as well as knowledge of programming and a computing device/cloud.
99 Remember that the data can take us so far. That does not mean the data can always unlock the physics behind our problems.
100 Whether collected from literature, or identified by domain/expert knowledge, or based on their availability.
101 And in some cases, a _mapping function_ can also answer causal questions.
102 A _mapping function maps_ the features to the target. There is a lot that we still do not know on _mapping functions_ and they could tie to structural causal models. Perhaps the next edition will house a more rich discussion and examples/codes.
103 Keep in mind that complex phenomena may sometimes result in complex functional forms.
104 The concept behind mapping functions could be generalized to other problems. I will stick to my comfort zone here and will advise to explore this concept for your own problems.

$M = A_s \times f_y \left(d - \frac{a}{2}\right)$ (9.9)

and, \( a = \frac{A_s \times f_y}{0.85 f_c \times b} \)

where \(A_s\): Area of the tensile steel reinforcement, \(d\): depth of the concrete beam, and \(b\): width of the concrete beam, \(f_c\): compressive strength of the concrete, and \(f_y\): yield strength of the tensile steel reinforcement.

### 9.4.1.2 Behavioral Phenomenon

On the other hand, behavioral structural engineering phenomena that occur at the element level, such as load-deformation history, require the addition of more governing features in lieu of the geometric features and material properties. Most notably, such features will arise from the type of applied loading and/or boundary conditions. Intuitively, we can infer that 1) complex phenomena are likely to require a higher degree of features, and 2) there is mutual independence between the classes of features.

Let us walk through two examples.

Let us revisit one of the first examples we covered in this book. Beams are load bearing members designed to satisfy strength and serviceability criteria [27]. A primary interest to structural engineers is to trace the load-deformation history of beams [105]. From a practical perspective, the deformation a beam undergoes can be measured in tests or calculated following mechanics principles (such as the moment-curvature method) or simulated via FE models. Given that the magnitude of deformation a beam undergoes primarily reflects the degree of degradation in its load bearing capacity arising from the applied loading, then it is quite possible to associate these two events together [17].

Obtaining the load-deformation history experimentally is an involved process that requires building and testing a series of beam specimens. [106] Similarly, to model such history, an engineer is tasked with developing an analytical or a FE model that captures the interaction between the applied loads, beam geometry, materials properties, etc. In both cases, the mentioned methods follow and obey mechanics and physics principles [28].

Similarly, if you happen to witness or visualize such a test, then domain knowledge informs us that the deformation history of a loaded beam in bending results in a parabolic-like or curved-like history plot. This plot insinuates that the observed deformations, which result from stresses generated from a continually applied load, P, reflect the degradation of the beam's sectional capacity [107] [17].

If we confine our discussion to RC beams, [108] then such a plot is likely to have distinct points that reflect distinct phenomena (e.g., concrete cracking, steel yielding, concrete crushing, and at the point of failure). For example, Figure 9.12 illustrates the deformation history of two idealized beams, Beam 1 and Beam 2. The only difference between these two beams is that Beam 2 is shallower than Beam 1, and hence under identical loading conditions, [109] Beam 2 will fail before Beam 1.

Arriving at the above conclusion is trivial since we are only considering one feature (height of beam) and only this feature is varied between the two beams. Now, if other parameters were to vary as well, then the problem substantially grows as our perception of physics principles and domain knowledge becomes hard to bridge.

Let us extend the Figure 9.12 example by trying to trace the deformation-history of beams once exposed to fire conditions. [110]

As we have seen above, the load bearing capacity and degree of deformation in a beam can be calculated following mechanics principles or FE simulations. However, under certain conditions (say, under fire effects), arriving at load bearing capacity and deformation history turns into a multifaceted problem [29]. Unlike tracing the load-deformation of beam at ambient conditions, the magnitude of deformation a beam undergoes under fire primarily reflects the degree of

105 The load-deformation history of beam is a chart that plots the load and mid-span deformation at the vertical and horizontal axes, respectively. It is a history since it shows the propagation of deformation as a function of the applied loading. In a way, this plot reflects how the features of the beam responds to the applied loading.
106 This turns into a more complex endeavor at extreme events, which we will visit in the next example.
107 A function of geometric features, material properties, restraints, etc.
108 Re-visit this discussion by referring to steel or timber beams bit.
109 I hope you can read between the lines to identify the little bit of causal language embedded here.
110 In this instance, the addition of fire adds a new layer of complexity that you are going to see in a bit.
