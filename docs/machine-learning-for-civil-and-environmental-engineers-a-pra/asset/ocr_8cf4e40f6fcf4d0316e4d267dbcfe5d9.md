Let us say that we have acquired the data needed for a specific ML analysis. What do we do with such data?
Well, we can use the data in three primary ways:

+   - To describe the phenomenon the data was collected on.
+     - For example, say that we have built 20 reinforced concrete beams and then tested these beams under flexure. The results from these tests can be used to describe a few observations, such as the patterns of cracks in beams before failure; some beams failed with large deformations while others were under small deformations. A few beams failed at larger loads than others, etc. Such descriptions can be obtained via data exploration and/or unsupervised ML.
+   - To predict the phenomenon the data was collected on.
+     - For example, we can use the data we collected on the above beams to build a model that can forecast/estimate how similar beams would behave. Structural engineers can be interested in knowing the bending capacity of beams. Thus, we make use of the data we collected on failure loads to develop a model that can predict the failure load in beams. This is where the majority of supervised ML applications fall.
+   - To causally understand or infer cause and effect relations.
+     - For example, out of the 20 failures we have seen, what has/have caused the failures in each beam? Can we identify a causal mechanism that uncovers how failure takes place? Answering such a question is where causal ML comes into the picture.

Thus, to use the data in any of the three above ways to arrive at knowledge, we need to follow systematic and well-established approaches. Hence, data science is the subject that uses scientific methods, processes, algorithms, and systems to extract knowledge from data. This chapter will primarily focus on data.

From this view, it is of merit to list the properties of data. These fall under:

+   - Scale and size.
+   - Variety of types.
+   - Rate of generation and recording.
+   - Meaningfulness.
+   - Degree of confidence.

# ## 3.2 Types of Data

There are numerous types of data, and five are presented herein.

# ### 3.2.1 Numerical Data

This type represents quantitative and measurable data such as forces, weights, deformations, age, etc. Exact and whole numbers are called discrete numbers. Continuous numbers are those that fall under a range (i.e., the axial capacity is 1234.2 kN). Continuous data can be further divided into two groups: interval and ratio data. Interval data can be measured on a known scale where each point is placed at an equal distance from its neighbors. This type of data can