
![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_551_0.png)

Figure 9.12 Illustration of load-deformation history.

degradation within its load bearing capacity due to the temperature-induced material properties. 111 Thus, it is quite possible to associate these two phenomena 112 [17].

Physics principles show that the mid-span deformation resulting in a fire-exposed beam is generated from applied loading, P, and degradation to the beam’s sectional capacity 113 [17]. Since P remains virtually constant during fire testing, 114 then the extent of deformation reflects the cumulative degradation in material properties and any possible losses in cross-section size.

Let us look at Figure 9.13. Now, for two identical beams, 115 Beam 1 and Beam 2, where Beam 1 is loaded with P1 and Beam 2 is loaded with P2 (and P1 > P2). Since P1 > P2, then Beam 1 is expected to undergo higher levels of deformation under fire. Arriving at this notion is trivial since only one feature (P) is varied between the two beams. However, if other features were to be varied as well, then, and similar to the example at ambient temperature, the problem on hand substantially grows.

## 9.4.2 Concept of Mapping Functions

Based on the above examples, one could argue that the sectional capacity equation and load-deformation history plots contain the DNA of beams as they distill the collective interaction between the geometrical and material features, as well as loading and restraint conditions.

For example, this load-deformation history is what we seek to obtain when we design our tests and remains a primary outcome of our investigations. 116 The same history gives us valuable insights into a beam’s response (i.e., cracking, yielding, etc.), performance (ductile, brittle, etc.), and failure (via bending, shear, etc.). Thus, it is essential to be able to obtain such a history especially via a modern approach that minimizes the need for tests or simulations.

> Let us form a hypothesis; “in order to be able to understand or predict a phenomenon, all that is needed is to identify the primary features and the governing relationship that ties these features to patterns belonging to the so-called phenomenon.” Such a governing relationship can be a mapping function. A mapping function does not require complex simulations; but instead, it stems from reverse-engineering the observations that already hold the hidden knowledge we seek into an elegant formula that can be applied in one step.

111 The rise in temperature softens construction materials. In other words, the strength of building material under 500°C can be a fraction of that under ambient conditions.
112 Frankly speaking, obtaining the history experimentally is a costly and complex process due to the harsh nature of fire tests and the need for specialized equipment and experienced personnel [67].
113 A function of temperature rise, geometric features, material properties, restraints, etc.
114 One of the rules of fire testing is that we maintain the same level of loading. This is different than testing at ambient conditions, where the level of applied loading is consistently being increased.
115 In case you are wondering, Beam 2 in this particular example is not the same as that we discussed at ambient temperature. Hence, the difference in colors.
116 Whether at ambient or extreme conditions. An engineer could develop a FE model that captures the interaction between the environment, beam features, and materials properties, as well as applied loads. Both testing and FE approaches are well accepted and have been proven effective, yet continue to suffer on a few fronts (e.g., cost/time associated with setting up fire tests, need for dedicated software/workstations, etc.) [28]. Thus, an opportunity to develop a new approach to tracing phenomena (i.e., deformation history of beams or any structural elements for that matter) presents itself.

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_552_0.png)

**Figure 9.13** Typical response of beams under fire conditions.

Mapping functions can be a bit different than those we often develop from our experiments. For example, in our experiments, specimens are designed to satisfy constraints of testing equipment 117 and funds allocated for testing. 118 Therefore, researchers pick a handful of features 119 and build specimens to examine such parameters using the available equipment they have. Then, researchers adopt traditional statistical methods (i.e., linear regression) to analyze such data. While this leads to good and proper design expressions, given the above limitations, it may also not properly account for all parameters. 120

On the other hand, a mapping function aims to narrow the primary limitation of limited tests by combining data from different experiments and then identifying the key parameters (from a data point of view) to derive a generalized function (equation 121). 122 Therefore, a mapping function is expected to be more encompassing of the examined phenomenon. But that is not all for mapping functions. An additional feature of mapping functions is their ability to infer explainable and causal relationships. 123

Let me address the identification problem, and then I will come back to go over the explainability and causal component.

How do we know if a parameter/feature has high fidelity or not? Frankly speaking, recent reviews [30–32] infer that: 1) we lack guidance on setting mathematical standard scores for feature fidelity, 2) we do not know the influence of algorithmic topology/formulation or data quality on such scores, and 3) this is a highly-specific domain problem.

Thus, fundamentally identifying what high fidelity means for our domain by combining physics principles, domain knowledge, and pure data perspective is critical and is one to be handled on a problem-basis.

To arrive at an inclusive view of fidelity, we can: 1) leverage findings of classical approaches (i.e., examine the parameters within formulas adopted in codal provisions or derived by researchers), and 2) seek experts’ guidance. In addition, we can also leverage ML! However, instead of applying one algorithm, as commonly accepted, we apply a series of algorithms with different topologies (e.g., thus giving us distinctly various methods to process our data). Then, high fidelity features will be those that satisfy a set of problem-based conditions.

For example, the following two conditions can be tried (for now): attaining an importance score of 50% or higher across 75% of the adopted algorithms. Simply put, a feature X with an importance score of 50% in algorithm A, 57% in algorithm B, 40% in algorithm C, and 70% in algorithm D, will satisfy the above set of conditions.

117 In a way, we do not have labs that contain all equipment to test all combinations of parameters in a single campaign.
118 Thus, it is rare to test all parameters in a given campaign.
119 In this instance, the use of parameters is more adequate. Also, these parameters are primarily identified by expert judgment and knowledge domain.
120 Which, as we have seen before, is one of the reasons why data-driven models seem to outperform codal expressions.
121 Note that there is no guarantee that the mapping function will have a similar form to one obtained in the traditional manner.
122 Which overcomes the limitations of traditional statistical methods.
123 Which symbolic regression does not account for.

- Step 1: We start by observing a certain engineering phenomenon to establish trends/patterns.
- Step 2: We then investigate the possible parameters (features) that govern such phenomenon.
- Step 3: We collect data on our observations (from step no. 1) and compare the identified parameters to that in step no. 2.
- Step 4: We apply ML algorithms to analyze the observed trends as identified by the governing parameters.
- Step 5: We examine the adequacy of the developed algorithm by invoking explainability measures to cross check if the algorithms apply the same/similar mechanisms to that known from step no. 2 to arrive at predictions.
- Step 6: We transform the logic of the algorithms into a mapping function(s). Such a function would resemble a mathematical expression that can be used to directly predict and/or examine the phenomenon on hand. A mapping function has causal implications since it is derived from causal assumptions.

### Figure 9.14 Outline of the proposed approach.

The rationale behind this approach is that it is unlikely that the majority of the tested algorithms (given their different processing mechanisms) to constantly rank features at higher scores unless they prove to be elemental to algorithmic predictions [33–35]. The above two arbitrary conditions were selected after a series of preliminary tests and serve as a stepping-stone for this discussion. 124

In contrast to mapping functions, existing explainability methods such as SHAP or LIME aim to explain model predictions solely based on the available data for that particular model, which: 1) are likely to be limited, and 2) do not have a physical or domain knowledge basis. On the other hand, mapping functions draw causal effects from physics principles, domain knowledge, and data-driven perspectives and hence are more appropriate for engineering problems. Unlike existing explainability methods, mapping functions are not just about the data.

## 9.4.3 Approach to Mapping Functions

Figure 9.14 presents a flowchart for arriving at mapping functions. The first three steps are self-explanatory as they relate to our observations and data collection. In this step 4, we apply ML algorithms 125 to examine the collected features and evaluate the performance of models. In step no. 5, we explore explainability measures that indicate the importance of each feature on the models/ensemble’s predictions (i.e., how often such a feature was used to arrive at a correct prediction) and the partial effect of each parameter when varied across the range of the outcome while keeping other parameters fixed. 126 In step no. 6, the ML models/ensemble is converted into a mapping function which, given its 1) transparency, 2) resemblance of design expressions engineers are familiar with, and 3) independence from the need for ML coding/software can have room in our domain. 127
