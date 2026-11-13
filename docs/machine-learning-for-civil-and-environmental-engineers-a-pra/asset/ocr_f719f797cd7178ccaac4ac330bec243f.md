+   - Step 1: We start by observing a certain engineering phenomenon to establish trends/patterns.
+   - Step 2: We then investigate the possible parameters (features) that govern such phenomenon.
+   - Step 3: We collect data on our observations (from step no. 1) and compare the identified parameters to that in step no. 2.
+   - Step 4: We apply ML algorithms to analyze the observed trends as identified by the governing parameters.
+   - Step 5: We examine the adequacy of the developed algorithm by invoking explainability measures to cross check if the algorithms apply the same/similar mechanisms to that known from step no. 2 to arrive at predictions.
+   - Step 6: We transform the logic of the algorithms into a mapping function(s). Such a function would resemble a mathematical expression that can be used to directly predict and/or examine the phenomenon on hand. A mapping function has causal implications since it is derived from causal assumptions.

# Figure 9.14 Outline of the proposed approach.

The rationale behind this approach is that it is unlikely that the majority of the tested algorithms (given their different processing mechanisms) to constantly rank features at higher scores unless they prove to be elemental to algorithmic predictions [33–35]. The above two arbitrary conditions were selected after a series of preliminary tests and serve as a stepping-stone for this discussion.124

In contrast to mapping functions, existing explainability methods such as SHAP or LIME aim to explain model predictions solely based on the available data for that particular model, which: 1) are likely to be limited, and 2) do not have a physical or domain knowledge basis. On the other hand, mapping functions draw causal effects from physics principles, domain knowledge, and data-driven perspectives and hence are more appropriate for engineering problems. Unlike existing explainability methods, mapping functions is not just about the data.

# 9.4.3 Approach to Mapping Functions

Figure 9.14 presents a flowchart for arriving at mapping functions. The first three steps are self-explanatory as they relate to our observations and data collection. In this step 4, we apply ML algorithms125 to examine the collected features and evaluate the performance of models. In step no. 5, we explore explainability measures that indicate the importance of each feature on the models/ensemble’s predictions (i.e., how often such a feature was used to arrive at a correct prediction) and the partial effect of each parameter when varied across the range of the outcome while keeping other parameters fixed.126 In step no. 6, the ML models/ensemble is converted into a mapping function which, given its 1) transparency, 2) resemblance of design expressions engineers are familiar with, and 3) independence from the need for ML coding/software can have room in our domain.127