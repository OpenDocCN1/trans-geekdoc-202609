# Python Environment for Bayesian Learning: Inferring the Structure ... 269

# PEBL DEVELOPMENT

The benefits of open source software derive not just from the freedoms afforded by the software license but also from the open and collaborative development model. PEBL's source code repository and issue tracker are hosted at Google Code and freely available to all. PEBL includes over 200 automated unit tests and mandates that every source submission and resolved error be accompanied with tests.

# RELATED SOFTWARE

While there are many software tools for working with BNs, most focus on parameter learning and inference rather than structure learning. Of the few tools for structure learning, few are open-source and provide the set of features included in PEBL. As shown in Table 1, the ability to handle interventional data, model with missing values and hidden variables, soft and arbitrary priors and exploit parallel platforms are unique to PEBL. PEBL, however, does not currently provide any features for inference or learning Dynamic Bayesian Networks (DBN). Despite its use of optimized matrix libraries and custom C extension modules, PEBL can be an order of magnitude or more slower than software written in Java or C/C++; ability to use a wider range of data and priors, the parallel processing features and the ease-of-use, however, should make it an attractive option for many users.

# CONCLUSION AND FUTURE WORK

We have developed a library and application for learning BNs from data and prior knowledge. The set of features found in PEBL is unmatched by alternative packages and we hope that our open development model will convince others to use PEBL as a platform for BN algorithms research.

# ACKNOWLEDGMENTS

We would like to acknowledge support for this project from the NIH grant #U54 DA021519.