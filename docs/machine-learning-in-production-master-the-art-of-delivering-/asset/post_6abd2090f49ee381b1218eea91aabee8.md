
Saved Pipeline : classification_v1.pkl # Output
7. test_data = pd.read_csv("/home/suhas/code/test.csv") # Load the data
8. result = make_prediction(test_data[0:1])#Make prediction on the first row
9. print(result)

{'prediction': ['Y']}

You should get the output as Y (that is, ‘Yes’) for the given set of input data.

## Conclusion

This chapter discussed the importance of modular programming in the production environment; virtual environments play a crucial role when you are working on multiple projects. After that, you explored the steps to create and activate a virtual environment. You can list the packages to be installed inside the virtual environment in the requirements.txt file so that all the required packages can be installed in one go. Writing test cases boosts confidence about the package, functions, and overall integrity. Packages are portable and reusable, and they can be easily debugged.

In the next chapter, you will learn to leverage MLflow for tracking the ML experiments and saving the serialized models.

## Points to remember

- The Python package holds multiple modules, and each module contains functions, classes, and variables.
- The MANIFEST.in file contains the list of files to be included and excluded.
- The requirements.txt files hold the list of packages to be installed using pip.
- Python refers to serialization and deserialization by the terms pickling and unpickling, respectively.
- The __init__.py file indicates that the directory should be treated as a package.

## Multiple choice questions

- 1. Identify a Python module.
  a) load.py
  b) requirements.txt
  c) transform.ccm
  d) MANIFEST.in

- 2. Python fixtures can be declared by which of the following?
  a) fixture
  b) pytest.fixture
  c) @pytest.fixture
  d) fixture.pytest

## Answers

- 1. a
- 2. c

## Questions

- 1. What is a Python module?
- 2. How can you interpret the output of the pytest command?
- 3. How can you install Python packages in editable mode?

## Key terms

- PYTHONPATH: It augments the default search path for modules. The PYTHONPATH variable contains a list of directories whose modules are to be accessed in the Python environment.
- Joblib: Joblib is a set of tools to provide lightweight pipelining in Python. It is used to persist the model for future use, the following in particular:
  - Transparent disk-caching of functions and lazy re-evaluation (memorize pattern).
  - Simple parallel computing.

Join our book's Discord space

Join the book's Discord Workspace for Latest updates, Offers, Tech happenings around the world, New Release and Sessions with the Authors:

https://discord.bpbonline.com

![](img/cc4299656808e62a294f1843a1e18e72_99_0.png)

## CHAPTER 5

### MLflow-Platform to Manage the ML Life Cycle

### Introduction

The Machine Learning life cycle involves many challenges. For instance, data scientists need to try different models containing multiple parameters and hyperparameters. They need to keep track of the model that is performing well and its parameters. Next, they need to save the serialized model for reusability. This chapter explains the role of MLflow in an ML life cycle. MLflow is a platform for streamlining machine learning development, including tracking experiments, packaging code into reproducible runs, and sharing and deploying models. It can manage a complete ML life cycle.

### Structure

This chapter discusses the following topics:

- Introduction to MLflow
- MLflow tracking
- MLflow projects
- MLflow models
- MLflow model registry

### Objectives

After studying this chapter, you should be able to train, reuse and deploy ML models using MLflow. You should also be able to track model evaluation metrics and model parameters, pickle the trained models, and compare two model results on MLflow UI. MLflow supports many downstream tools when it comes to deployment. You should be able to pick any iteration (by run ID) that is outperforming others and consume it through Python code, terminal, or postman.

### Introduction to MLflow

MLflow is an open-source platform for managing the end-to-end machine learning life cycle.

MLflow allows data scientists to run as many experiments as they want before deploying the model into production; however, it keeps track of model evaluation metrics, such as RMSE and AUC. It also tracks the hyperparameters used while building the model. It enables you to save the trained model along with its best hyperparameters. Finally, it allows you to deploy an ML model into a production server or cloud. You can even keep track of the models being used in staging and production so that other team members can be aware of this information.

MLflow is library-agnostic, that is, you can use any popular ML library with it. Moreover, you can use any popular programming language for it as MLflow functions can be accessed via REST API and Command Line Interface (CLI).

Integrating MLflow with your existing code is quite easy as it requires minimal changes. If you are working on a local system, it will automatically create a mlrun directory, wherein it stores the output, artifacts, and metadata. It creates a separate directory for each run. However, you can specify the path to create the mlrun directory. MLflow allows you to store information of each run into databases, such as MySQL or PostgreSQL.

MLflow is more useful in the following scenarios:

- Comparing different models: MLflow offers a UI that allows users to compare different models. You can compare Random Forest vs Logistic regression side by side, along with their model metric and parameters used. MLflow supports a wide range of model frameworks.
- Cyclic model deployment: In production, it is required to push a new version of the model after every data change, when new requirements come up, or after building a model better than the current one. In these scenarios, MLflow helps keep track of the models that are in staging (pre-production) and models that are in production with versions and brief descriptions.
- **Multiple dependencies**: If you are working on different projects or different frameworks, each of them will have a different set of dependencies. MLflow helps you to maintain dependencies along with your model.
- **Working with a large data science team**: MLflow stores the model metrics, parameters, time created, versions, users, and so on. This information is accessible to other team members working on the same projects. They can track all the metadata using MLflow UI or SQL table (if you are storing it in the database).

### Set up your environment and install MLflow

In this section, you will install miniconda and then install mlflow in the conda environment. However, if you already have anaconda or miniconda installed, you can create a conda environment and install mlflow using PIP.

### Miniconda installation

If you have anaconda installed on your machine, then you can skip the next step, that is, installing and setting up Miniconda.

You can download Miniconda from the following link:

```
https://docs.conda.io/en/latest/miniconda.html#linux-installers
```

Or you can simply execute the following command in the terminal (for Linux):

```
wget https://repo.anaconda.com/miniconda/Miniconda3-py37_4.10.3-Linux-x86_64.sh
```

Run the installation:

```
bash Miniconda3-latest-Linux-x86_64.sh
```

Read and follow the prompts on the installer screens. Restart the terminal when the miniconda installation is completed.

In the terminal, you will see that the base conda environment is auto-activated. You can disable the auto-activation of the base environment by running the following command in the terminal:

```
conda config --set auto_activate_base false
```

Verify the conda installation using the following command:

```
conda list
```

Run the following command to update conda (optional):

```
conda update conda
```
