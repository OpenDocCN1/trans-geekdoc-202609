
# Hyperparameter Tuning for Bayesian Networks

Hyperparameter tuning for Bayesian networks typically involves finding the best structure and parameter settings that optimize model performance. Unlike other machine learning algorithms that often have hyperparameters related to the optimization process, Bayesian networks have hyperparameters associated with the network structure and the parameter estimation process. Below are some key hyperparameters to consider when tuning Bayesian networks.

*   **Network structure configuration**: Arrangement of nodes (variables) and edges (directed connections) in the Bayesian network. Different configurations of the network structure can result in different causal relationships and dependencies between variables.
*   **Nodes and edges**: Configurations involving adding or deleting nodes and edges can alter the network structure. Adding new nodes can incorporate additional variables, while deleting nodes can simplify the model.
*   **Maximum number of parents per node**: Maximum number of parent nodes each node can have in the network. Setting this parameter can control the complexity of the network and prevent overfitting.
*   **Prior probabilities for CPTs**: Bayesian networks require estimating CPTs for each node. Configuring prior probabilities can influence the learning process and incorporate prior beliefs or knowledge about the variable relationships.
*   **Scoring metric**: The choice of the scoring metric, such as log-likelihood, BIC, or AIC, influences the evaluation of different network structures during learning.
*   **Search algorithm**: The search algorithm determines how the network structure is explored during learning. Score-based and constraint-based algorithms are common search algorithms to learn the network structure from data.
*   **Prior knowledge**: Incorporating prior knowledge or constraints, such as known causal relationships, can be specified as part of the configuration to guide the learning process.

Remember that Bayesian network tuning is a complex task, as the number of possible network structures can grow exponentially with the number of nodes. It is essential to strike a balance between model complexity and performance. Additionally, domain knowledge and understanding of the data are critical for making informed decisions during the hyperparameter tuning process.

Fortunately, SPSS Modeler has a built-in automatic search algorithm that makes configuring Bayesian networks easier, especially for non-programmers. In addition, it still provides users with options for changing certain configurations. We will practice with those configurations in the example.

## Example: Bayesian Networks

![](images/ufig16_19.jpg)

In this example, we will build predictive models for the **Airline Recommendation** dataset using the Bayesian network algorithm with various configurations.

*   **Dataset:** `AirlineRecommendation.sav`
*   **Target variable:** `Recommendation` (Flag: Yes/No)

### Sample-Explore-Modify

Refer to the previous chapters for more details on these steps.

### Bayesian Network Modeling

In this example, we train five different Bayesian network models. Since Bayesian networks work better with complete datasets, we use the data with imputation.

Follow the steps below to set up the Bayesian Network models.

1.  **Create a new stream**:
    *   Open SPSS Modeler and create a new stream named `Airline_BayesianNetworks`.
2.  **Copy the existing stream**:
    *   Open the stream `Airline_Tree`.
    *   Copy the section of the stream from the **data source**, **Filler node**, to the **Partition node**.
    *   Paste these nodes into your new `Airline_BayesianNetworks` stream.
3.  **Add five Bayes net nodes**:
    *   From the **Modeling** group, add **four Bayes Net Nodes** to the stream.
    *   Connect them to the **Partition node**.
    *   Label the five XGBoost Tree nodes as:
        1.  TAN 1
        2.  TAN 2
        3.  Markov Blanket 1
        4.  Markov Blanket 2
        5.  Markov Blanket FS

At this point, your stream diagram should look like the following:

![](images/ufig16_20.jpg)

Then, use the details below to set the configurations for each Bayesian Network model. We focus on a few key configurations that are available under the Model options and Expert options in the Bayes Net node settings.

#### TAN 1 Model Configurations

*   **Model options**
    *   Select “Use partitioned data” and “Build model for each split.”
    *   Structure type: `TAN`
    *   Parameter learning method: `Maximum likelihood`
*   **Expert options**
    *   Select “Expert”
    *   Missing values: `Use only complete records`
    *   Independent test: `Likelihood ratio`

#### TAN 2 Model Configurations

*   **Model options**
    *   Select “Use partitioned data” and “Build model for each split.”
    *   Structure type: `TAN`
    *   Parameter learning method: `Bayes adjustment for small cell counts`
*   **Expert options**
    *   Select “Expert”
    *   Missing values: `Use only complete records`
    *   Independent test: `Pearson chi-square`

#### Markov Blanket 1 Model Configurations

*   **Model options**
    *   Select “Use partitioned data” and “Build model for each split.”
    *   Structure type: `Markov Blanket`
    *   Parameter learning method: `Maximum likelihood`
*   **Expert options**
    *   Select “Expert”
    *   Missing values: `Use only complete records`
    *   Independent test: `Likelihood ratio`

#### Markov Blanket 2 Model Configurations

*   **Model options**
    *   Select “Use partitioned data” and “Build model for each split.”
    *   Structure type: `Markov Blanket`
    *   Parameter learning method: `Bayes adjustment for small cell counts`
*   **Expert options**
    *   Select “Expert”
    *   Missing values: `Use only complete records`
    *   Independent test: `Pearson chi-square`

#### Markov Blanket FS Model Configurations

*   **Model options**
    *   Select “Use partitioned data” and “Build model for each split”
    *   Structure type: `Markov Blanket`
    *   Select “Include feature selection preprocessing step”
    *   Parameter learning method: `Maximum likelihood`
*   **Expert options**
    *   Select “Expert”
    *   Missing values: `Use only complete records`
    *   Independent test: `Likelihood ratio`

To run each of the Bayes Net nodes separately and produce model nuggets, follow the same steps described in [Chapter 7](#chapter7.xhtml):

1.  **Run each node separately**: After configuring the five Bayesian Network models (TAN 1, TAN 2, Markov Blanket 1, Markov Blanket 2, and Markov Blanket FS) with the specified settings, execute each of the nodes separately. This will generate the corresponding model nuggets for each.
2.  **Connect model nuggets**: Since all models use the same input data with identical field names, you can use the approach described in [Chapter 7](#chapter7.xhtml) to connect all the model nuggets for comparison. Follow the same steps outlined in [Chapter 7](#chapter7.xhtml) under the section “How to run the analysis node with multiple models?”
3.  **Add filter node**: Add a Filter node to the stream and connect it to the model nugget for Markov Blanket FS. Rename the model nuggets to the selected names (TAN 1, TAN 2, MB 1, etc.) (see the detailed instructions in Step 2 of the next process).
4.  **Add analysis node**: After renaming the model nuggets, use an Analysis node to compare the performance of the models. The Analysis node will compare the models based on key performance metrics.
5.  **Add evaluation graph node**: Use an Evaluation Graph node to produce ROC charts and Lift charts for all the models. This will provide a graphical representation of model performance.
6.  **Run the diagram**: Run the entire diagram to generate the comparison results for each Bayesian Network model.

By following these steps, you’ll have a diagram as below, including model comparison through the Analysis node and graphical evaluation with the ROC and Lift charts.

![](images/ufig16_21.jpg)
