
# Fundamentals

**De Gruyter STEM**

**Volume 1**

Edited by

Katharina Morik

Jens Buß

Peter Marwedel

Andreas Becker

ISBN 9783110785937

e-ISBN (PDF) 9783110785944

e-ISBN (EPUB) 9783110786125

Bibliographic information published by the Deutsche Nationalbibliothek

The Deutsche Nationalbibliothek lists this publication in the Deutsche Nationalbibliografie; detailed bibliographic data are available on the Internet at `http://dnb.dnb.de`.

© 2023 Katharina Morik, Peter Marwedel, published by Walter de Gruyter GmbH, Berlin/Boston // The book is published with open access at www.degruyter.com.

This work is licensed under the Creative Commons Attribution 4.0 International License.

## Contents

1.  [Also of interest](#9783110785937_001251.xhtml#d2024e168)
2.  [Preface](#9783110785937_001476.xhtml#d2024e796)
3.  **Katharina Morik, Jian-Jia Chen 1 Introduction** 
    1.  [1.1 Embedded Systems and Sustainability](#9783110785937_001550.xhtml#d2024e1014)
    2.  [1.2 The Energy Consumption of Machine Learning](#9783110785937_001550.xhtml#d2024e1151)
        1.  [1.2.1 Measuring Energy Consumption](#9783110785937_001550.xhtml#d2024e1273)
        2.  [1.2.2 Different Processors](#9783110785937_001550.xhtml#d2024e1294)
        3.  [1.2.3 Reduced Run-Time and Real-time Processing](#9783110785937_001550.xhtml#d2024e1369)
        4.  [1.2.4 Minimizing Energy Consumption of Machine Learning Processes](#9783110785937_001550.xhtml#d2024e1403)
    3.  [1.3 Memory Demands of Machine Learning](#9783110785937_001550.xhtml#d2024e1427)
        1.  [1.3.1 Deep Learning](#9783110785937_001550.xhtml#d2024e1433)
        2.  [1.3.2 Summaries and Clustering](#9783110785937_001550.xhtml#d2024e1479)
        3.  [1.3.3 Executing Machine Learning](#9783110785937_001550.xhtml#d2024e1530)
        4.  [1.3.4 Regularization and Reparametrization](#9783110785937_001550.xhtml#d2024e1554)
    4.  [1.4 Structure of this Book](#9783110785937_001550.xhtml#d2024e1572)
4.  **2 Data Gathering and Resource Measuring**
    1.  **2.1 Declarative Stream-based Acquisition and Processing of OS Data with kCQL**
        1.  [2.1.1 Introduction](#9783110785937_002446.xhtml#d2024e1845)
        2.  [2.1.2 Operating-System Data Acquisition Frameworks](#9783110785937_002446.xhtml#d2024e1888)
        3.  [2.1.3 kCQL: A Relational Streaming Interface for OS Data](#9783110785937_002446.xhtml#d2024e2025)
        4.  [2.1.4 Implementation](#9783110785937_002446.xhtml#d2024e2749)
        5.  [2.1.5 Evaluation](#9783110785937_002446.xhtml#d2024e3013)
        6.  [2.1.6 Discussion](#9783110785937_002446.xhtml#d2024e3250)
        7.  [2.1.7 Conclusion](#9783110785937_002446.xhtml#d2024e3338)
    2.  **2.2 PhyNetLab Test Bed**
        1.  [2.2.1 Introduction](#9783110785937_002446.xhtml#d2024e3388)
        2.  [2.2.2 General Structure of the Test Bed](#9783110785937_002446.xhtml#d2024e3462)
        3.  [2.2.3 Hardware](#9783110785937_002446.xhtml#d2024e3483)
        4.  [2.2.4 Software](#9783110785937_002446.xhtml#d2024e3540)
        5.  [2.2.5 Experiment Examples](#9783110785937_002446.xhtml#d2024e4192)
    3.  **2.3 Zero-Power/Low-Power Sensing**
        1.  [2.3.1 Introduction](#9783110785937_002446.xhtml#d2024e4248)
        2.  [2.3.2 Energy Availability with Indoor Photovoltaics](#9783110785937_002446.xhtml#d2024e4347)
        3.  [2.3.3 Measurement Setup and Deployment](#9783110785937_002446.xhtml#d2024e4356)
        4.  [2.3.4 Energy Harvesting Dataset](#9783110785937_002446.xhtml#d2024e4404)
        5.  [2.3.5 Batteryless System Design](#9783110785937_002446.xhtml#d2024e4548)
        6.  [2.3.6 Batteryless System Architectures](#9783110785937_002446.xhtml#d2024e4563)
        7.  [2.3.7 Energy Management Unit (EMU)](#9783110785937_002446.xhtml#d2024e4607)
        8.  [2.3.8 Ambient Sensing Using Batteryless Sensors](#9783110785937_002446.xhtml#d2024e5741)
        9.  [2.3.9 Gesture Detection on the Batteryless MiroCard](#9783110785937_002446.xhtml#d2024e5884)
        10. [2.3.10 Approaches to Gesture Detection](#9783110785937_002446.xhtml#d2024e6025)
        11. [2.3.11 Batteryless Machine Learning](#9783110785937_002446.xhtml#d2024e6074)
        12. [2.3.12 Batteryless Classification of Time Series Data](#9783110785937_002446.xhtml#d2024e6384)
        13. [2.3.13 Experimental Evaluation](#9783110785937_002446.xhtml#d2024e6418)
        14. [2.3.14 Analysis](#9783110785937_002446.xhtml#d2024e6445)
        15. [2.3.15 Energy Proportionality vs Time Series Processing](#9783110785937_002446.xhtml#d2024e6477)
        16. [2.3.16 Contextualizing Indoor Energy Harvesting](#9783110785937_002446.xhtml#d2024e6486)
        17. [2.3.17 Conclusions](#9783110785937_002446.xhtml#d2024e6497)
5.  **3 Streaming Data, Small Devices**
    1.  **3.1 Summary Extraction from Streams**
        1.  [3.1.1 Introduction](#9783110785937_007154.xhtml#d2024e6662)
        2.  [3.1.2 Submodular Function Maximization over Streams](#9783110785937_007154.xhtml#d2024e6806)
        3.  [3.1.3 Related Work](#9783110785937_007154.xhtml#d2024e7560)
        4.  [3.1.4 Getting More by Doing Less](#9783110785937_007154.xhtml#d2024e7996)
        5.  [3.1.5 Experiments](#9783110785937_007154.xhtml#d2024e9015)
        6.  [3.1.6 Conclusion](#9783110785937_007154.xhtml#d2024e9669)
    2.  **3.2 Coresets and Sketches for Regression Problems on Data Streams and Distributed Data**
        1.  [3.2.1 Introduction](#9783110785937_007154.xhtml#d2024e9706)
        2.  [3.2.2 Our Contributions](#9783110785937_007154.xhtml#d2024e10751)
        3.  [3.2.3 Conclusion](#9783110785937_007154.xhtml#d2024e12686)
6.  **4 Structured Data**
    1.  **4.1 Spatio-Temporal Random Fields**
        1.  [4.1.1 Introduction](#9783110785937_013188.xhtml#d2024e12832)
        2.  [4.1.2 Previous Work](#9783110785937_013188.xhtml#d2024e12947)
        3.  [4.1.3 Graphical Models](#9783110785937_013188.xhtml#d2024e13180)
        4.  [4.1.4 Regularization](#9783110785937_013188.xhtml#d2024e15414)
        5.  [4.1.5 From Linear Chains to Spatio-Temporal Models](#9783110785937_013188.xhtml#d2024e15552)
        6.  [4.1.6 Spatio-Temporal Random Fields](#9783110785937_013188.xhtml#d2024e17233)
        7.  [4.1.7 Experimental](#9783110785937_013188.xhtml#d2024e19805)
        8.  [4.1.8 Regularized Training of Spatio-Temporal Random Fields](#9783110785937_013188.xhtml#d2024e19874)
        9.  [4.1.9 Prediction on Test Sets](#9783110785937_013188.xhtml#d2024e20010)
        10. [4.1.10 Conclusion](#9783110785937_013188.xhtml#d2024e20047)
    2.  **4.2 The Weisfeiler-Leman Method for Machine Learning with Graphs**
        1.  [4.2.1 Introduction](#9783110785937_013188.xhtml#d2024e20095)
        2.  [4.2.2 Preliminaries](#9783110785937_013188.xhtml#d2024e20153)
        3.  [4.2.3 The Weisfeiler-Leman Algorithm](#9783110785937_013188.xhtml#d2024e20698)
        4.  [4.2.4 Kernels Based on the Weisfeiler-Leman Algorithm](#9783110785937_013188.xhtml#d2024e22198)
