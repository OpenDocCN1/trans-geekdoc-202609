
Test cases that are written against the application requirements specifications are used in test coverage analysis. To write the test cases, participants in this study do not need to see the code. Test groups relate to a fraction of the test cases that were run, passed, failed, and so on, after a document describing all of the test cases has been produced. Test coverage analysis is frequently done as part of unit testing by the application developer. Overall test coverage analysis is used by quality assurance organizations to show test metrics and coverage according to the test plan. To boost coverage, test coverage analysis generates more test cases. It aids developers in locating portions of an application that are not subjected to a set of test cases. It aids in the calculation of a quantitative measure of code coverage, which indirectly gauges the application or product’s quality. One drawback of code coverage assessment is that it only tests what the code does not cover or what has not been developed. Furthermore, rather than looking at structures or functions that do not yet exist, this approach looks at those that do.

# Interface testing

Interface testing determines whether the systems and components of an application communicate data and control to one another correctly. It checks to see if module interactions are performing properly and if errors are being handled correctly. Client interfaces, server interfaces, remote interfaces, **graphical user interfaces (GUIs)**, APIs, external and internal interfaces, and physical interfaces should all be tested. GUI testing is using test cases to test a product’s graphical user interface to ensure that it fits its specifications. API testing entails testing APIs separately and as part of the end-to-end transactions performed during integration testing to see if they deliver the expected results.

# Agile

Many of the processes that have been examined thus far are based on strict adherence to process-oriented paradigms. In many cases, the emphasis is on following procedural processes rather than reacting rapidly to changes and enhancing efficiency. Continuous feedback and cross-functional teamwork are increasingly important under the agile methodology. Agile aims to be agile enough to respond to unexpected situations throughout development. Less time is spent on upfront analysis, and greater emphasis is given to learning from the process and implementing real-time lessons acquired. Throughout the process, there is also increased interaction with the customer for the agile model, as shown in **Figure 19.8**:

![](images/Image31376.jpg)

**Figure 19.8:** Agile model

# DevOps

Traditionally, the software development process’ three main actors—development (Dev), **quality assurance (QA)**, and **operations (Ops)**—performed their functions separately or in silos. As depicted in **Figure 19.9**, the work would flow in a linear pattern from development through quality assurance to operations:

![](images/Image31384.jpg)

**Figure 19.9:** Traditional development

Due to a general lack of collaboration among the units, this frequently resulted in delays, finger-pointing, and many iterations through the linear cycle. Shorter development cycles, increased deployment frequency, and more reliable releases are all goals of DevOps, which are closely aligned with business goals. **Figure 19.10** depicts the DevOps paradigm, which encourages the three groups to collaborate throughout the development process:

![](images/Image31392.jpg)

**Figure 19.10:** DevOps

# Versioning

Versioning is an organizational concept that assigns a numbered system to software versions to help identify where they belong in the version history. Versioning ensures that developers are working with the most recent versions and that users are also using the most recent versions. There are several ways that can be applied. Changes in version numbers may introduce new features or fix bugs. A hierarchy is used to denote major and minor changes in a sequence-based versioning numbering system. **Figure 19.11** shows an example of this type of numbering; a major revision could be denoted by a change from 3.0 to 4.0, whereas minor version modifications are denoted by 4.6 to 4.7, and patches are denoted by 4.7.5 to 4.7.6:

![](images/Image31401.jpg)

**Figure 19.11:** Components of versioning

Other systems may be based on alphanumeric codes or the date of release.

# Secure coding standards

Secure coding standards are methods that help limit an application’s attack surface when followed throughout the software development life cycle. For common programming languages like C, C++, Java, and Perl, standards are produced through a community effort.

# Documentation

Documentation is important during the development process to ensure optimal functionality and security. Many processes should be documented, resulting in multiple documents. The sections that follow look at some of these procedures and the documents that come from them.

# Security requirements traceability matrix

A **security requirements traceability matrix (SRTM)** lists the security requirements that must be met by a new asset. In a grid, such as an Excel spreadsheet, the matrix maps the requirements to security controls and verification processes. The columns document the requirement identification number, description of the requirement, and source of the requirement, as well as the test goal and test verification technique for each row in the grid. It enables security professionals and developers to guarantee that all requirements are defined, implemented in the final design, and thoroughly tested. An SRTM would aid in determining whether the security requirements set at project inception are carried through to implementation with a sufficient level of certainty. Consider the following scenario. Assume a group of security engineers design a corporate network using regulatory and business guidelines. Based on their efforts and a thorough examination of the entire set of functional and performance criteria in the network design, the engineers create an SRTM. In this instance, the aim of an SRTM is to allow certifiers to verify that the network complies with applicable security criteria.

# Requirements definition

A collection of functional and security requirements that must be met during the software development process is referred to as a requirements definition. It might be in a variety of formats. Contract style requirement lists, which are exactly what they sound like – lists of criteria, are one conventional approach of documenting needs. Another approach is to express these requirements using use cases, which are a set of scenarios that describe how the system should interact with a human user or another system in order to accomplish a given business goal.

# System design document

The software is described in the **system design document (SDD)**, which is frequently accompanied by an architectural diagram. It includes the following details:

- **Data design**: This sort of design explains the features and relationships between data objects that led to the selection of data structures.
- **Architecture design**: Data flow diagrams and transformation mapping are used to describe distinct boundaries between incoming and exiting data in this type of architecture. It incorporates information flow features into the program’s structure. All interfaces, including internal and external program interfaces, as well as the design of the human interaction, are classified as interface design.
