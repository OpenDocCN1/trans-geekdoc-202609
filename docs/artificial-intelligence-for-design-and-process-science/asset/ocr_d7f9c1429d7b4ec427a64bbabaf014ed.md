# Introducing Feature Selection Before Propositionalization

Clement Ting, Patrick Then, and Man Lu

**Abstract** The selection stage of knowledge discovery in databases (KDD) reduces the project scope to features relevant to the data objective while maintaining the final model's effectiveness. The scope reduction is important because the next stage of KDD, compilation (propositionalization), is a resource-intensive task that converts the data from a relational dataset into a propositional dataset for data mining. However, KDD selection is done manually because conventional feature selection techniques are not compatible with the pre-compiled, relational data.

In this chapter, we introduce an automated feature selection before propositionalization (FSbp) and compare its characteristics with traditional feature selection techniques. We provide a use case for FSbp in KDD for oil drilling data, where FSbp is vital for timely project completion. We also discuss the implementation of FSbp algorithms for the above use case, areas for improvement, and limitations of FSbp.

**Keywords** Feature selection before propositionalization · Big data · Harmonization · Knowledge discovery in databases · Oil drilling

# ## Introduction

Feature selection is a staple preprocessing task in machine learning that aims to remove redundant or irrelevant features from training sets. It has been shown to improve model accuracy, training time, generalization ability, and model running time. This process, however, assumes that the dataset to be used is already in

C. Ting (✉ · P. Then
Swinburne University of Technology Sarawak Campus, Kuching, Sarawak, Malaysia
e-mail: cpting@swinburne.edu.my; pthen@swinburne.edu.my
M. Lau
Swinburne University of Technology, Hawthorne, Vic, Australia
e-mail: elau@swinburne.edu.au

© The Author(s), under exclusive license to Springer Nature Switzerland AG 2025 175
S. C. Suh (ed.), Artificial Intelligence for Data Science and Process Design., https://doi.org/10.1007/978-3-031-67886-8_11