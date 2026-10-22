# 1.3. Model Building and Input Variable Selection in Machine Learning for Water-related Problems

ML procedures are described in detail in many books (e.g., Haykin, 1999). In relation to the use of ML in water-related problems, most papers and books present similar modeling frameworks (Fig. 1.5). For example, Elshorbagy et al. (2010) compiled information about methodologies used in various studies, presenting a general-purpose framework, which was tested on several relevant water-related cases. Similar frameworks can be found also in more recent publications (e.g., Potgieter & Dahlberg, 2022).

A large number of procedures for designing data-driven models (learning systems) have been proposed in different areas. Some of these procedures have been generalized in such a way that they can be applied to other modeling approaches (Mitchell, 2007; Pyle, 1999; Abraham et al., 2008). Corzo Perez (2009) presented the concept of characterizing the way models can include physical-based knowledge. A typical procedure of model building, presented, for example, by Haykin (1999) and many other authors, is as follows:

+   1. Explore the problem and solution spaces, and state the problem.
+   2. What is the expected result and how will it be used?
+   3. Select the input and output variables (features).
+   4. Specify the appropriate modeling methods and choose the tools (software and algorithms).
+   5. Prepare and survey the data. Partition the date into the training, verification, and test subsets.
+   6. Build (train) the model, using training and validation subsets.
+   7. Test (validate) the model, using the test subset.
+   8. Apply the model and evaluate the results.

In reality, the process of modeling is not linear but continuous with feedback loops. For example, a lack of particular data may lead to a change in the modeling method selected. For these processes, there is a sort of checklist, or golden rules, widely accepted in the ML community, helping a modeler in the process of model building.

+   1. Clearly define the problem that the model will help to solve.
+   2. Specify the expected solution for the problem.
+   3. Evaluate if the delivered solution will be accepted and used in practice.
+   4. Learn the problem, collect the domain knowledge, analyze and understand it.