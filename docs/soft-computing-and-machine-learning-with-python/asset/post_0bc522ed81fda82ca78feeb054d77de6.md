
# 294 Soft Computing and Machine Learning with Python

In order to show this second working mode of our platform, we use the research work done by Rosenblum et al. [6] as an example. They extract patterns from stripped binary files to detect function entry points (FEP), which existing disassemblers do not detect perfectly yet [5]. They analyze consecutive bytes in binary files, representing them as 3 grams of assembly instructions. Once the grams are extracted, they formulate the FEP identification problem as structured classification using Conditional Random Fields (CRF) [16]. An initial flat model is later enriched with the evidence that a call instruction indicates the existence of a FEP in the callee address. The model detects FEPs more accurately than GCC, ICC, and MSVS compilers [6].

Figure 3 shows the changes to the architecture when we want to process binary files, and the high-level program is not available. White elements are the same as in the previous architecture. Blue elements are modifications of the previous working mode. All the modules related to processing high-level programs are not present.

![](img/e1ab17402154bec3fa9a7873fe3ee232_319_0.png)

**Figure 3: Platform architecture to process binary code.**

Although the behavior of the Binary Pattern Extractor is the same, the rules for detecting individuals and patterns are different. The main difference is that no instrumented code is added, since the source code is not available. Depending on the case, debug information is not available either (i.e., stripped binaries are used). Regarding the Classifier module, the Classification Rules must consider a plain binary file instead of a high-level program representation.

# An Efficient Platform for the Automatic Extraction of Patterns in ... 295

In the example of FEP detection in binary files, this is how the platform has been used to generate a dataset valid to create the CRF model. The output dataset, individuals (rows) are instruction offsets in the binary file; one feature (column) will be created for each 1, 2, and 3 grams in the binary code, indicating the occurrence of that pattern in each individual; another call <offset> feature is added, associating function invocation with the <offset> individual. Finally, the classifier variable (target) is 1 if the individual is a FEP and 0 otherwise (debug information is available).

In order to create the dataset described above, the Individual Detector creates as many individuals as instruction offsets in the binary file. The Pattern Detector extracts 1, 2, and 3 grams for each offset and a call feature for each different function. In this second case, the feature is not associated with the offset where the pattern is detected, but to the offset (memory address) being called (as done in Algorithm 6). Pattern Generalization is done via the normalization process described in [6]. Finally, the Classification Rules use the debug information to set 1 to one individual identified as a FEP and 0 otherwise.

This platform configuration (and the previous one) to extract datasets valid to create the CRF model proposed by Rosenblum et al. is available for download at [17].

# Representing Nonsequential Patterns

In the analysis of binary applications, it is common to require the detection of nonsequential patterns, such as subgraphs of control flow and data dependency graphs. The detection of these subgraphs can be used for many different purposes, such as the FEP detection problem described in the previous subsection.

Although the Binary Pattern Detector module of our platform (Figures 1 and 3) is aimed at extracting patterns made up of contiguous binary instructions, the rest of the modules can be used to represent nonsequential structures as graphs. This functionality is provided by the versatile way our platform considers the sequential patterns (features), permitting the definition of different criteria to associate these features to the corresponding individuals.

One example of this functionality is present in the decompiler scenario. Algorithm 5 shows how RET features are associated with the function (individual) ( 296 Soft Computing Machine Learning with Python) where the pattern was detected. In Algorithm 5, this association is represented by the first element in the tuple returned, which is the function ID the RET instruction belongs to. Thus, the output dataset will have 1 in the cell corresponding to that function (row or individual) and pattern (column feature). However, CALL patterns are associated with individuals in a different way. Algorithm 6 shows how this feature is not associated with the function where the pattern is detected, and to the function being invoked. Therefore, a machine learning algorithm trained with the generated dataset may have inconsequential patterns (e.g., there must exist RET pattern inside the function and, in any part of the program, a CALL pattern invoking the same function) to identify the type returned by a function.

Another example of this functionality is the FEP implementation problem described in Section 3.6. The dataset generated by our platform can be to create the proposed CRF model, which uses graphs for structural prediction and classification [16]. Those graphs are obtained from the dataset by using the versatile association of features to individuals already discussed. Its implementation and a sample dataset can be consulted in [17].

# Platform Implementation

We have implemented the proposed platform and it is freely available at http://www.reflection.uniovi.es/decompilation/download/2016/sp/. The Instrumentator and Classifier modules have been implemented in C++, since they use clang [18] to process the high-level representation of C programs. The rest of the platform has been implemented in Python. For the disassembly services we have used IDAPython [19].

The implementation is highly parallelized, providing important performance benefits when multicore architectures are used. The parallelization follows a pipeline scheme, where both data and task parallelism are used. Figure 4 shows the concrete approach followed. We have been the issues tackled to parallelize the platform implementation.

# An Efficient Platform for the Automatic Extraction of Patterns in ... 297

![](img/e1ab17402154bec3fa9a7873fe3ee232_322_0.png)

Figure 4: Parallelization of the platform implementation.

- (1) Data Parallelization. We identify each module in the compiler (obj files used) as a different portion of data to work in parallel. This obj files can be combined in lib or exe files to produce bigger modules. In the example in Figure 4, three different modules are processed in parallel.

- (2) Task Identification. The tasks to be parallelized are those identified as modules in the platform architecture (Section 3). As shown in Figure 4, an additional initialization task was defined to initialize the database and create a temporary folder where the input files are copied.

- (3) Task Dependency. After identifying the tasks, we defined the dependencies among them with a Directed Acyclic Graph (DAG). These dependencies define when two tasks can run in parallel, and when a task has to wait for others to end. As shown in Figure 4, the instrumentation, compilation, binary pattern extraction, generalization, and classification tasks can run in parallel. For the same piece of data, one has to wait for the previous to complete. The initialization (at the beginning) and dataset generation (at the end) tasks cannot be parallelized. The last one waits for all the classification tasks to process all the data.

- (4) Task Implementation. Tasks should be mapped to threads or processes. The current implementation uses the Python programming language to combine all the different modules of the architecture (implemented in Python itself or C++). Since most implementations of Python use the Global Interpreter Lock (GIL) to synchronize the execution of threads [20], we implemented
