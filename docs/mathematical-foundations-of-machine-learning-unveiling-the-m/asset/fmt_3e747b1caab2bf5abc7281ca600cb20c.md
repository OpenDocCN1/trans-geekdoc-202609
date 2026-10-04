
# Stage II – Data Acquisition and Understanding

The objective of this stage is to generate a high-quality processed dataset with well-defined relationships to the model targets and establish the data set’s location in the required analytics environment. Additionally, the development of the “solution architecture” for the data pipeline, enabling regular updates and scoring of the data, is crucial. The three primary tasks to be accomplished during this stage are: `Data Ingestion`, `Data Exploration`, and `Data Pipeline Setup`.

## Data Ingestion

This phase involves setting up the process required to transfer data from the source location to the target location. The determination of target locations is based on environments that facilitate analytical activities such as training and predictions.

## Data Exploration

Before the data set can be used to train the data models, it must undergo scrubbing to remove discrepancies and errors. To assess data quality and gather necessary information for processing the data before modeling, tools like data summarization and visualization should be employed. Given the repetitive nature of this process, an automated utility named `IDEAR`, provided by `TDSP`, can be utilized for data visualization and the creation of data summary reports. Achieving satisfactory quality of processed data allows for the observation of inherent data patterns, aiding in the selection and development of an appropriate `predictive model` for the target. It is crucial at this point to assess if the required amount of data is available to initiate the modeling process, which is iterative and may necessitate the identification of new data sources for increased relevance and accuracy.

## Setting Up a Data Pipeline

To complement the iterative process of data modeling, a standard process for scoring new data and refreshing the existing data set must be established through the setup of a `data pipeline or workflow`. The solution architecture of the data pipeline should be developed by the end of this stage. Three types of pipelines can be used based on business needs and constraints: `batch-based`, `real-time or streaming`, and `hybrid`.

### Deliverables in this stage

**Data Quality Report:** This report must include a `data summary`, the relationship between business requirements and their attributes, and variable ranking, among other details. The `IDEAR` tool provided with `TDSP` is capable of generating data quality reports in various formats like a relational table, CSV file, or any other tabular data set.

**Solution Architecture:** A description or diagram of the data pipeline used to score new data and generate predictions after the model has been built is referred to as `solution architecture`. This diagram can also outline the data pipeline needed to `retrain` the model based on new data.

**Checkpoint Decision:** Before commencing the actual model-building process, the project must be reevaluated to determine if the expected value can be achieved. These evaluations are also known as `Go or No-Go` decisions.

# Stage III – Modeling

The objective of this stage is to identify `optimal data features` for the machine learning model, ensuring it is informative enough to predict target variables accurately and can be deployed in the production environment. The three primary tasks in this stage are: `Feature Engineering`, `Model Training`, and `Determination of Model Suitability for the Production Environment`.

### Deliverables in this stage

**Feature Sets:** This document contains all the features described in the `feature sets` section of the data definition report. It is heavily used by programmers to write the required code and develop features based on descriptions provided in the document.

**Model Report:** This document must contain details of each model evaluated, following a standard template report.

**Checkpoint decisions** – A decision regarding deployment of the model to the production environment must be made based on the performance of different models.

# Stage IV – Deployment

The objective of this stage is to introduce the solution models to a lower production-like environment, such as a pre-production environment and a user acceptance testing environment, before eventually deploying the model in the production environment. The primary task to be achieved in this stage is the `operationalization of the model`.

## Operationalize the model

Once a set of models with expected performance levels is obtained, these models can then be operationalized for other applicable applications. According to the business requirements, predictions can be made in real-time or on a batch basis. To deploy the model, they must be integrated with an open `Application Programming Interface` (`API`) to allow interaction of the model with all other applications and its components, as needed.

### Deliverables to be created in this stage

A dashboard report using key performance indicators and metrics to assess the health of the system.

A document or runbook with the details of the deployment plan for the final model.

A document containing the solution architecture of the final model.

# Stage V – Customer Acceptance

The goal of this stage is to ensure that the final solution for the project meets the expectations of the stakeholders and fulfills the business requirements gathered during Stage I of the Data Science lifecycle. The two primary tasks that must be accomplished in this stage are `system validation and project hand-off`.

### Deliverables to be created in this stage

The most important document created during this stage is for the stakeholders and is called the `exit report`. The document contains all the available details of the project that are significant to provide an understanding of the operations of the system. `TDSP` supplies a standardized template for the `exit report`, which can be easily customized to cater to specific stakeholder needs.
