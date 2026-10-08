
1166 Applied Intelligent Decision Making in Machine Learning

neuro fuzzy and feature reduction model for data analysis. Using fuzzification, the input pattern classes are identified and the irrelevant data is removed by using feature reduction methods. An ANN model is used for classifying the filtered data. The performance of the model is tested against ten different datasets.

## 8.3 METHODOLOGY

### 8.3.1 DATASET

The Informatics for Integrating Biology and the Bedside Center (i2b2) organized a challenge in 2010, which was focused on NLP for clinical data. The dataset included patients' discharge summaries and clinical notes provided by three institutions: the Beth Medical Center, Partners HealthCare, and the Pittsburgh Medical Center. The organizers annotated manually 826 clinical notes, which provided gold-standard data for the challenge [8].

For developing the new system for entity boundary detection, the task of concept extraction must be focused. In this, 426 annotated progress notes of Partners and Beth were used where 170 progress notes were used as a training set, and the remaining 256 notes were used as a test dataset to assess the performance of the systems with reference data.

### 8.3.2 PROPOSED METHOD

The proposed system uses the concept of multi-pattern matching based on a matrix model [26] for clinical data. Fundamentally, a matrix is a rectangular array of numbers, or expressions arranged in rows and columns. The system performs the parallel pattern matching between two matrices in which of the same size are added or subtracted, by element. Every element of a matrix is a user-assigned value corresponding to the POS tag of entity.

This system is created in two matrices, one for gold-standard training data and another for test data. The framework of the proposed system (see Figure 8.1) is divided into a few components for medical concept extraction. The working of the components is described below.

#### 8.3.2.1 Text Pre-Processing

I2b2 clinical notes contains various parts, such as discharge date, admission date, allergies, present illness history, medical history, social history, family history, physical examination, pertinent results, discharge medication, and discharge instructions. These clinical notes are in an unstructured and semi-structured form of text [27]. Every entry contains a little information associated with each patient and concerns special characters, colons, semicolons, punctuation, hyphens, and so on. For medical concept identification, each sentence of each section needs pre-processing. In this system, a natural language toolkit is used for text processing. For performing tokenization methods, like line tokenize or word tokenizer, are used, followed by a post-tag method for parts of speech tagging. Pre-processing is performed on gold-standard annotations and test annotations. In gold-standard

![](img/d1bf16e7dc1fe5d49ee33c2dfa5cdb06_177_0.png)

**FIGURE 8.1** Framework of proposed matrix-based system.

annotations, each file has named entities with its concepts. These entities are tagged with the POS. In a test dataset, every sentence of the file is tagged with POS. These tagged data are applied as input for creating matrices.

#### 8.3.2.2 Trained Matrix Formation

The system is trained using gold-standard annotations for which a trained matrix was created. After the text processing of the gold-standard annotations of every file, POS tagged patterns are generated collectively for every single entity and sequence of entities. For matrix calculation, every POS tag is assigned with a different value, as shown in Table 8.1. The frequency of each pattern among the different pattern sets of gold annotations are then ascertained. For obtaining frequent pattern sets, a user-defined minimum threshold greater than or equal to 2 is required. These different frequent pattern sets are then applied as elements for the trained matrix.

#### TABLE 8.1
Different POS Tags with Assigned Value for Matrix Calculation

| POS Tag | Assigned Value | POS Tag | Assigned Value |
| :--- | :--- | :--- | :--- |
| NN | 1 | CL | 18 |
| NST | 2 | INTF | 19 |
| NNP | 3 | INJ | 20 |
| PRP | 4 | NEG | 21 |
| PRPS | 5 | UT | 22 |
| DEM | 6 | SYM | 23 |
| VM | 7 | XC | 24 |
| VAUX | 8 | RDP | 25 |
| JJ | 9 | ECH | 26 |
| RB | 10 | UNK | 27 |
| PSP | 11 | VBD | 28 |
| RP | 12 | VBG | 29 |
| CC | 13 | NNS | 30 |
| WQ | 14 | DT | 31 |
| QF | 15 | VBN | 32 |
| QC | 16 | IN | 33 |
| QO | 17 | CD | 34 |

The trained matrix has $k$ number of pattern sets, where every row represents one pattern set. The shortest and shortest pattern length are $maxl$ and $min$, respectively. In $a(M \times N)$, $\alpha$ is a trained matrix, $M$ is $k$ (number of pattern sets), and $N$ is $maxl$. When the location of the elements is lacking, “0” is entered in the columns of the matrix.

#### 8.3.2.3 Test Matrix Formation

The test matrix $\langle\beta\rangle$ is created using gold-standard annotations for which a trained matrix was created. After the text processing of the gold-standard annotations of every file, POS tagged patterns are generated collectively for every single entity and sequence of entities. For matrix calculation, every POS tag is assigned with a different value, as shown in Table 8.1. The frequency of each pattern among the different pattern sets of gold annotations are then ascertained. For obtaining frequent pattern sets, a user-defined minimum threshold greater than or equal to 2 is required. These different frequent pattern sets are then applied as elements for the trained matrix.

The trained matrix has $k$ number of pattern sets, where every row represents one pattern set. The shortest and shortest pattern length are $maxl$ and $min$, respectively. In $a(M \times N)$, $\alpha$ is a trained matrix, $M$ is $k$ (number of pattern sets), and $N$ is $maxl$. When the location of the elements is lacking, “0” is entered in the columns of the matrix.

#### 8.3.2.4 Pattern Matching

The test matrix $\langle\beta\rangle$ is created using gold-standard annotations for which a trained matrix was created. After the text processing of the gold-standard annotations of every file, POS tagged patterns are generated collectively for every single entity and sequence of entities. For matrix calculation, every POS tag is assigned with a different value, as shown in Table 8.1. The frequency of each pattern among the different pattern sets of gold annotations are then ascertained. For obtaining frequent pattern sets, a user-defined minimum threshold greater than or equal to 2 is required. These different frequent pattern sets are then applied as elements for the trained matrix.

The trained matrix has $k$ number of pattern sets, where every row represents one pattern set. The shortest and shortest pattern length are $maxl$ and $min$, respectively. In $a(M \times N)$, $\alpha$ is a trained matrix, $M$ is $k$ (number of pattern sets), and $N$ is $maxl$. When the location of the elements is lacking, “0” is entered in the columns of the matrix.

#### 8.3.2.5 Pruning

The test matrix $\langle\beta\rangle$ is created using gold-standard annotations for which a trained matrix was created. After the text processing of the gold-standard annotations of every file, POS tagged patterns are generated collectively for every single entity and sequence of entities. For matrix calculation, every POS tag is assigned with a different value, as shown in Table 8.1. The frequency of each pattern among the different pattern sets of gold annotations are then ascertained. For obtaining frequent pattern sets, a user-defined minimum threshold greater than or equal to 2 is required. These different frequent pattern sets are then applied as elements for the trained matrix.

The trained matrix has $k$ number of pattern sets, where every row represents one pattern set. The shortest and shortest pattern length are $maxl$ and $min$, respectively. In $a(M \times N)$, $\alpha$ is a trained matrix, $M$ is $k$ (number of pattern sets), and $N$ is $maxl$. When the location of the elements is lacking, “0” is entered in the columns of the matrix.

## 8.4 SYSTEM EVALUATION

The effectiveness of the proposed system is measured by precision and recall [28]. Here, precision is the ratio of correctly extracted medical concepts out of all extracted. Recall is the ratio of correctly extracted medical concepts that should have been extracted. Precision and recall for the proposed system is calculated as:

$$Precision = \frac{\text{Number of patterns that are completely matched in matrix}}{\text{Number of patterns that are retrieved in matrix}} \times 100 \quad (8.1)$$

$$Recall = \frac{\text{Number of patterns that are completely matched in matrix}}{\text{Number of relevant patterns that are given in gold annotation}} \times 100 \quad (8.2)$$

## 8.5 RESULTS AND DISCUSSION

Based on the concept of precision and recall given in Equations 8.1 and 8.2, the matrix-based system generates approximately a 60% recall and a 30% precision for all concepts collectively (test, problem, treatment). The precision of the system is reduced because it uses the concept of parallel pattern matching between two matrices and generates many non-medical entities. To improve the precision of the system, some post-processing rules are introduced, after which precision is increased to 70% approximately. A comparison of precision before and after post-processing is given for Beth and Partners data in Figure 8.2.

![](img/d1bf16e7dc1fe5d49ee33c2dfa5cdb06_180_0.png)

**FIGURE 8.2** Comparison of precision before and after post-processing rules.
