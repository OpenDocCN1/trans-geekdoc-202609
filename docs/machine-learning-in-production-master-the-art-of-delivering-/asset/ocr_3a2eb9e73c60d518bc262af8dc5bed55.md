+   * **Entry point:** The entry point section holds the command to be executed inside the MLflow project environment. This command can take arguments; it is a mandatory field and cannot be left blank.

+   * **Parameters:** This section holds one or more arguments that will be used by the entry point commands, but it is optional.

Create a conda.yaml file:

```
1. name: Loan_prediction
2.
3. channels:
4.   - defaults
5.
6. dependencies:
7.   - python=3.7
8.   - pip
9.   - pip:
10.    - mlflow
11.    - numpy==1.19.5
12.    - pandas==1.1.5
13.    - matplotlib==3.3.4
14.    - scikit-learn==0.24.2
```

Then, create an MLproject file:

```
1. name: Loan_prediction
2.
3. conda_env: conda.yaml
4.
5. entry_points:
6.   main:
7.     command: “python train.py”
```

Switch to the directory where the MLproject file and the conda environment are present. Locate the YAML file and run:

```
mlflow run .
```