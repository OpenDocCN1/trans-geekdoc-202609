
the AutoML methods [56]. To improve the interpretability of AutoML models we propose three areas for further research on the interpretability of AutoML: Surrogate models, Local Interpretable Model-agnostic Explanations (LIME) [55] and Shapley values [57]. However, others argue that we should improve the trust in artificial intelligence in healthcare rather than improving the interpretability. If the trust is high enough, the researcher-physicians will start using the black boxes [58]. Most researcher-physicians also do not precisely know how a car works. However, they still use cars in their daily lives. We believe that the addition of interpretability will ignite the adoption rate of AutoML methods in healthcare and other sectors to enable self-service data-science.

**Author Contributions:** Conceptualization: MS; Methodology, Software, Formal Analysis, Investigation: RO; Validation: RO, MS; Writing – Original Draft Preparation: RO; Writing – Review & Editing: MS, RO; Supervision: MS. All authors have read and agreed to the published version of the manuscript.

**Funding:** This research received no external funding.

**Conflicts of Interest:** The authors declare no conflict of interest.

## Appendix A

| Tool | Library/Package | Optimization | Pre-Processor | Post-Processor | Extra Feature(s) | Analysis Capabilities | Code Link |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| Auto-Weka 2.0 | WEKA | Tree-based hierarchical BO | Yes | No | | Binary classification<br>Multi-label classification<br>Regression | https://github.com/automl/autoweka |
| Auto-Sklearn | scikit-learn | Tree-based BO | Yes | Yes | Meta-learner | Binary classification<br>Multi-label classification<br>Regression | https://github.com/automl/auto-sklearn |
| Hyperopt-Sklearn | scikit-learn | Tree-based BO | Yes | No | | Binary classification<br>Multi-label classification | https://github.com/hyperopt/hyperopt-sklearn |
| TPOT | scikit-learn DEAP | Tree-based GP | Yes | No | | Binary classification<br>Multi-label classification<br>Regression | https://github.com/EpistasisLab/tpot |
| Layered TPOT | scikit-learn | Tree-based GP | Yes | No | | Binary classification<br>Multi-label classification<br>Regression | https://github.com/PGTue/tpot/tree/layered |
| Auto-Net 1.0 | Lasagne | Feed-forward NN on Stochastic Gradient Descent | Yes | No | | Binary classification<br>Multi-label classification<br>Regression | No implementation found |
| Auto-Net 2.0 | PyTorch | BO and Hyperband (BOHB) | Yes | No | | Binary classification<br>Multi-label classification<br>Regression | No implementation found |
| FLASH | scikit-learn | BO with expected improvement | Yes | No | Pipeline caching | Binary classification | https://github.com/yuyuz/FLASH |
| RECIPE | scikit-learn | Grammar-based GP | Yes | No | | Binary classification | https://github.com/RecipeML/Recipe |
| Auto-Prognosis | scikit-learn | BO and GP | Yes | Yes | Meta-learner, Explainer | Binary classification<br>Survival analysis<br>Temporal analysis | https://github.com/dmaalaa/Autoprognosis |
| ML-Plan | WEKA scikit-learn | HTN and EA | Yes | No | | Binary classification<br>Multi-label classification | https://github.com/fmohr/ML-Plan |
| Auto-stackers | scikit-learn XGBoost | Hierarchical stacking and EA | No | No | | Binary classification<br>Multi-label classification | No implementation found |
| Alpha3DM | PyTorch | NN and Monte Carlo Tree Search | Yes | Yes | | Binary classification<br>Multi-label classification<br>Regression | No implementation found |
| PoSH AUTO-sklearn | scikit-learn | BO with successive halving | Yes | Yes | Meta-learner | Binary classification<br>Multi-label classification<br>Regression | No implementation found |
| Auto-Keras | scikit-learn | BO guided network morphism | Yes | No | | Binary classification<br>Multi-label classification | https://autokeras.com/ |
| ATM | scikit-learn | Conditional Parameter Tree | Yes | No | Meta-learner | Binary classification<br>Multi-label classification | https://github.com/HDI-Project/ATM |

## Appendix B

### Table B1. Collection of the Top-15 elicited user stories, sorted on descending frequency.

| # | User Story | Frequency | Category |
|---|---|---|---|
| 1 | As a researcher-physician, I want to know how a prediction mechanism works, so that I can trust it more easily. | 5 | MX |
| 2 | As a researcher-physician, I want to be able to perform ML without having to code, so that I do not have to spend time learning how to program. | 5 | MC |
| 3 | As a researcher-physician, I want to use logistic regression, so that I can follow the medical guidelines for research. | 4 | MC |
| 4 | As a researcher-physician, I want to see which variables are included and excluded in the model, so that I can assess variable importance. | 4 | MX |
| 5 | As a researcher-physician, I want to see the difference between models with different variables included so that I can assess variable importance. | 4 | MX |
| 6 | As a researcher-physician, I want to transfer my model into a calculation tool, so that it can be used in clinical practice. | 4 | MU |
| 7 | As a researcher-physician, I want to have results within a day, so that I do not have to wait. | 4 | MC, MU |
| 8 | As a researcher-physician, I want to know the statistical power of a created model, so that I know if I can use it. | 4 | MX |
| 9 | As a researcher-physician, I want that the AutoML method explains its decisions, so that I can check its reasoning. | 3 | MX |
| 10 | As a researcher-physician, I want to have a graphical user interface, so that the chance of making errors is less than while coding. | 2 | UI |
| 11 | As a researcher-physician, I want to see the importance of each variable. So that I can check the reasoning of the computer. | 2 | MX |
| 12 | As a researcher-physician, I want to use code, so that I can trace back the decisions that I have made. | 2 | UI, MX |
| 13 | As a researcher-physician, I want to know what happens with missing data, so that I can evaluate the model correctly. | 2 | MC, MX |
| 14 | As a researcher-physician, I want to get suggestions for variables to include by the computer, so that I can improve my models. | 2 | MC |
| 15 | As a researcher-physician, I want to see the amount of variance that is explained by my model, so that I can assess the model quality. | 2 | MX |

## Appendix C

- AutoML selection
- Home
- Upload
- Create subset
- Create model
- Logout

### Hi, Richard!

Welcome to the AutoML web application.
This application is designed to make AutoML available to domain experts. The workflow of the application is as follows.
- 1. Upload a raw dataset
- 2. Create one or more (sub)sets from this raw dataset to do your analysis on
- 3. Let AutoML create a good model for your data a model based on the provided subset
- 4. Check the results when the model is done processing. On the menu bar above you can find the buttons to do each of these steps

An overview of the already uploaded datasets, subsets and analysis results is available here:

- Dataset Overview
- Subset Overview
- Result Overview

Figure C1. Screenshot 1 of AutoML artefact A, the Web application interface (preference: GUI).

### Select dataset for processing

You are now using t-test as a dataset to make a subset from. Please also select the target variable in the variables to include. You can select multiple columns by holding the ctrl or shift button while clicking.

- 1. Name of the dataset
- 2. Target variable
- 3. Columns to include

Figure C2. Screenshot 2 of AutoML artefact A, the Web application interface (preference: GUI).

### AutoML notebook

Hi! Welcome to the AutoML notebook. In this notebook you will be enabled to use AutoML in a few steps.

- 1. Upload a raw dataset
- 2. Create a subset from this raw dataset to do your analysis on
- 3. Let AutoML create a good model for your data a model based on the provided subset

To use the notebook in the right way you have to run each code block. Above each code block there is an explanation of what is happening.

```python
from numpy import argwhere, delete
from pandas import read_csv, read_sql_table, DataFrame
from sklearn.model_selection import train_test_split
from sklearn.preprocessing import LabelEncoder
from tpot import TPOTClassifier
import warnings
warnings.filterwarnings('ignore')
```

### Step 1: Upload dataset

Upload a raw dataset, this has to be a .csv file. Copy the filepath into the location variable, use two '\\' instead of one to make sure that the file is uploaded and no error is thrown. Denote the separator of the csv file in the separator variable. examples are commented in the lines below. The top of the dataframe is shown if it is successful.

```python
#separator = ","
location = "C:\\Users\\vrooms\\Desktop\\dataset_37_diabetes.csv"
separator = ","
location = 'D:\\22B\\_5. - RAPP - GWI - ML.csv'
df = pd.read_csv(location, sep = separator)
df.head()
```

|   | preg | plas | pres | skin | insu | mass | pedi | age | class |
|---|---|---|---|---|---|---|---|---|---|
| 0 | 6 | 148 | 72 | 35 | 0 | 33.6 | 0.627 | 50 | tested_positive |
| 1 | 1 | 85 | 66 | 29 | 0 | 26.6 | 0.351 | 31 | tested_negative |
| 2 | 8 | 183 | 64 | 0 | 0 | 23.3 | 0.672 | 32 | tested_positive |
| 3 | 1 | 89 | 66 | 23 | 94 | 28.1 | 0.167 | 21 | tested_negative |
| 4 | 0 | 137 | 40 | 35 | 168 | 43.1 | 2.288 | 33 | tested_positive |

All variables that are not numeric are label-encoded to numeric values in this code section, so that the AutoML method can read your data. The output of this code block is a list with the names of the variables in your dataset.

Figure C3. Screenshot of AutoML artefact B, the Jupyter notebook interface (preference: Code).

## Appendix D

Overview of the refined hypotheses. For user interaction the hypotheses are:

- 1. Artefact A is preferred over Artefact B to upload a dataset.
- 2. Artefact A is preferred over Artefact B to create a subset.
- 3. Artefact B is preferred over Artefact A to find the way in the different steps.
- 4. Artefact B is preferred over Artefact A for the explanations of the workflow.

For model construction the hypotheses are:

- 1. Artefact B is preferred over Artefact A for progress reporting on model construction.
- 2. Artefact B is preferred over Artefact A for model construction.
