the models, and select performance metrics and hyper parameters. This easy extendable feature can allow users to create new ideas and models in a faster way.

# Auto-Sklearn

Auto Sklern is an AutoML tool written in Python. The tool consists of 15 ML models, 14 feature preprocessing methods, and 4 data preprocessing methods. It selects the suitable algorithm and required hyperparameters to make the best model. The tool automatically solves classification, regression, and multi-label classification tasks. Auto-Sklearn has three major components: meta-learning, Bayesian optimization, and ensemble building. When a new dataset is supplied to the tool, it first extracts its meta-feature to discover the similar feature of the given input dataset with the available knowledge base depending on the meta-learning. The meta-learning process uses 140 pretrained datasets to identify the best combination of models and hyperparameters for a given dataset [3]. Meta-learning reduces the search space. Next, through Bayesian optimization [4], it identifies the best machine learning pipeline. Finally, the tool will choose the best ML work flow pipeline and will construct the ensemble model based on it. Auto-Sklearn works on the operating System Mac and Linux. It does not support Windows OS. It is easy to use if you are familiar with scikit-learn. It does not support GPU.

# TPOT (Tree-Based Pipeline Optimization Tool)

TPOT is an open-source tool developed using Python. TPOT routinely uses evolutionary algorithm [5] to design and improve the ML pipelines for a given problem [6, 7]. It is well suited for genetic problems. Various models and preprocessing techniques are utilized from the sklearn software. This tool uses tree-based algorithms [8] like Random Forest, XG Boost, or decision Tree. Solutions based on tree-based algorithms are robust. This tool is good for unclean datasets or datasets with noise. It does not support GPU.

# AutoML-Docker

AutoML-docker is an open-source tool developed at Kern. Classifiers based on only natural language can be created with the help of this tool. The tool accepts a data set as input, the entire text processing is automatic, and models are produced accurately. The CLI interface is used to create