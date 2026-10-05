
- 30. C. Cifuentes and M. Van Emmerik, “Recovery of jump table case statements from binary code,” Science of Computer Programming, vol. 40, no. 2-3, pp. 171–188, 2001.
- 31. A. Mycroft, “Type-based decompilation,” in Proceedings of the European Symposium on Programming (ESOP ‘99), pp. 208–223, 1999.
- 32. G. Balakrishnan and T. Reps, “Divine: discovering variables in executables,” in Verification, Model Checking, and Abstract Interpretation: 8th International Conference, VMCAI 2007, Nice, France, January 14–16, 2007. Proceedings, vol. 4349 of Lecture Notes in Computer Science, pp. 1–28, Springer, Berlin, Germany, 2007.
- 33. A. Cozzie, F. Stratton, H. Xue, and S. T. King, “Digging for data structures,” in Proceedings of the 8th Conference on Operating Systems Design and Implementation (OSDI ‘08), pp. 255–266, San Diego, Calif, USA, December 2008.

## CHAPTER 14
## POLYGLOT PROGRAMMING IN APPLICATIONS USED FOR GENETIC DATA ANALYSIS

Robert M. Nowak

Institute of Electronic Systems, Warsaw University of Technology, Nowowiejska 15/19, 00-665 Warsaw, Poland

## ABSTRACT

Applications used for the analysis of genetic data process large volumes of data with complex algorithms. High performance, flexibility, and a user interface with a web browser are required by these solutions, which can be achieved by using multiple programming languages. In this study, I developed a freely available framework for building software to analyze genetic data, which uses C++, Python, JavaScript and several libraries. This system was used to build a number of genetic data processing applications and it reduced the time and costs of development.

**Citation:** Robert M. Nowak, “Polyglot Programming in Applications Used for Genetic Data Analysis,” BioMed Research International, vol. 2014, Article ID 253013, 7 pages, 2014. doi:10.1155/2014/253013.

**Copyright:** © 2014 Robert M. Nowak. This is an open article distributed under the Creative Commons Attribution License, which permits unrestricted use, distribution, and reproduction in any medium, provided the original work is properly cited.

## BACKGROUND

The number of computer programs for the analysis of genetic data is increasing significantly, but it still needs to be improved greatly because of the importance of result analysis with appropriate methods and the exponential growth in the volume of genetic data.

Genetic data are typically represented by a set of strings [1], where each string is a sequence of symbols from a generic alphabet. The string representation, called primary structure, reflects the facts that the molecules storing genetic information (DNA and RNA) are biopolymers of nucleotides, while proteins are polypeptide chains. The secondary, tertiary, and quaternary structures need to be considered to understand the interactions among nucleotides or amino acids, but they are used less frequently in computer programs. The secondary structure includes the hydrogen bonds between nucleotides in DNA and the RNA bonds between peptide groups in proteins, where the molecules are represented by graphs. The tertiary structure refers to the positions of atoms in three-dimensional space, and the quaternary structure represents the higher level of organization of molecules. The representations of molecules are extended based on connections between sequences or subsequences, which denotes similarity from various perspectives. Moreover, these data are supplemented with human-readable descriptions, which facilitate an understanding of the biological means of the sequence, its function and/or structure.

The large number of possible candidate solutions for the analysis of genetic data means that the employed algorithms must be selected carefully [2]. Exhaustive search algorithms must be supported by heuristics based on biological properties of the modeled objects. Particular importance in this field are dynamic programming algorithms, which allow us to find the optimal alignment of biological sequences (i.e., arranging the sequences by inserting gaps to identify regions of similarity [1]) in polynomial time, although the search space grows exponentially. Dynamic programming is used to search for similarity (local or global), to generate a multisequence representation (profile), and to examine sequences with Markov models. In addition, backtracking algorithms are used to search for motifs (i.e., identifying meaningful patterns in genetic sequences), greedy algorithms to detect genome rearrangements and to sort by reversals, divide-conquer algorithms to perform space-efficient sequence alignments, and graph algorithms for DNA assembly.

## Polyglot Programming in Applications Used for Genetic Data Analysis 315

A characteristic feature of the computer programs applied to genetic data is the necessity to analyze large amounts of data using complex algorithms, which means that high performance is crucial. Different user and system requirements mean that the flexibility of software is also important. Finally, users prefer a graphical interface that is accessible from a web browser and applications that update automatically.

Scientists are becoming increasingly involved in software development [3]. They should use software engineering practices and tools to avoid common mistakes and to speed up the development tasks [4]. The architecture of working application with explanation of development decisions could help in developing new computer programs. Biological and medical terminology is simplified to invite developers to discuss the presented solutions.

In this study, I describe the bioweb framework, including application architecture, the programming languages, libraries, and tools, to develop applications for processing genetic data. I propose a multilingual platform using C++, Python, and JavaScript. The use of appropriate and tested architectures, libraries, and tools decrease the risk of failure in system development as well reduces the costs and time. The use of appropriate systems also facilitates rapid prototyping, which allows us to verify concepts by obtaining the requisite information from end users: biologists and doctors.

## RESULTS

### Deployment Model

A three-layer software architecture was selected where the presentation layer, data processing layer, and data storage layer were kept separate. The use of multilayered model makes computer programs flexible and reusable, because applications have different responsibilities. Thus, it is beneficial to seg models into layers that communicate via well-defined interfaces. Layers help to separate different subsystems, and the code is easier to maintain, clean, and well structured.

Four possible deployment models were considered for the three-layer architecture: the desktop, the database server, the client, and the web application, as shown in Figure 1. The desktop architecture (Figure 1(a)) was rejected because the framework was designed to support multiuser applications. Collaboration features were hard to implement in this architecture because of the lack of central data server that could be accessed by multiple users.

![](img/e1ab17402154bec3fa9a7873fe3ee232_341_0.png)

Figure 1: Three-layer application deployment models: desktop application (a), database server (b), thin client (c), and web application (d). This solution supports the creation of applications using a web application architecture.

An application architecture with a shared database and data processing modules deployed on client machine (Figure 1(b)) was rejected because of the requirement for high client computer performance. Another problem is the need to update the software on the client side when changes and additions
