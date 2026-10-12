
# Model Performance and Retraining Policies

Model performance usually degrades over time. To fix this we need to retrain the model. The idea is to trigger a retrain pipeline based on a policy. Here are a couple of available policies:

*   **Absolute threshold:** You can set an absolute threshold for retraining. For example, whenever accuracy falls below 90 percent, you can trigger. Determining what this absolute threshold is would depend on your use case.
*   **Rate of degradation:** You can trigger retraining whenever there is a sudden dip in performance. For example, if you see a drop of more than 2 percent in accuracy in a day, you can trigger a retraining.

Now considering the preceding policies, there are a few main points to think about:

*   **Training costs:** There is a cost to training models. Frequently training models could be expensive. So it is important to make sure the policy does not frequently trigger retraining.
*   **Training time:** Some models train in a few minutes, but others take weeks to train. The deployed model could degrade further when waiting for the newly trained model.
*   **Delayed training:** If the threshold is too low, the model could degrade too much before the new model is deployed. This not only affects the performance of the ML service, it also shows inconsistency in the ML performance, which may not be tolerated by the end user.
*   **Scheduled training:** A much simpler policy could be a retraining on a fixed schedule. This would incorporate new data on a regular basis and the costs are predictable.

## Versioning Models

When you are building multiple models and sharing them with other teams, it is important to have some way to find them. One method is to use metadata to identify artifacts; however, users external to the organization access a deployed model using an API, and to them the metadata store might not be accessible. This is where versioning can be used.

The problem with having multiple models is that, when users are accessing through an API, they expect a certain performance and behavior from the model. If there is a sudden change in behavior from the same API, it causes unexpected disruption. However, there is a need for the model to update or change. For example, say there is a model to identify objects and humans in an image and it accurately detects all the human faces. Later, say you have updated the model and it now has the ability to also detect dogs and other pets; this could cause a disruption. In this case, the user needs the ability to choose the older model.

The solution is to use model versioning. Model versioning allows you to deploy an additional model to the existing model, with the ability to select it using a version ID. In this case, both the models can be accessed by the end user by specifying the version. This solves the problem of backward compatibility; that is, this works well for models that have the same inputs and outputs.

For models that behave in a different way (say a model has the ability to provide model explanations), they can be deployed as a new model (and not a new version of an existing model).

In both cases, there should be the ability to access these models using REST endpoints, separately and conveniently for the users. Enabling monitoring on all the deployed model versions allows you the ability to compare the different versions.

# Feature Store

Feature engineering is an important factor in the ability to build good ML models. However, it has been observed that, practically, feature engineering is more time‐consuming than experimenting with ML models. For this reason, a valuable feature that has been engineered provides a huge value for the entire ML solution.

So, feature engineering is a huge investment for any organization. In order to optimize their models, many teams work on creating new features. At times these features would have been valuable to other teams as well. Unfortunately, sharing these features is tricky and so the same feature engineering tasks are done over and over again. This creates several problems:

*   **Non‐reusable:** Features are created ad hoc and not intended to be used by others. Each team creates a feature with the purpose of only using it themselves. These ad hoc features are not automated in pipelines and are sometimes derived from other expensive data preprocessing pipelines.
*   **Governance:** Diversity of sources of the methods of creating these features creates a very complex situation for data governance.
*   **Cross‐collaboration:** Due to the ad hoc nature of these features not being shared, more divisions between teams are created and they continue to go separate ways.
*   **Training and serving differences:** When features are built ad hoc and not automated, this creates differences between training data and serving data and reduces the effectiveness of the ML solution.
*   **Productizing features:** While these ad hoc features are useful during experimentation, they cannot be productized because of the lack of automation and the need for low‐latency retrieval of the features.

## Solution

The solution is to have a central location to store the features as well as the metadata about the features that can be shared between the data engineers and ML engineers. This also allows the application of the software engineering principles of versioning, documentation, and access control of these features.

Feature stores also has two key features: the ability to process large feature sets quickly and the ability to access the features with low latency for real‐time prediction and batch access for training time and batch predictions.

`Feast` is an open‐source Feature Store created by Google and Gojek that is available as a software download. `Feast` was designed with `Redis` and Google Cloud services `BigQuery` and `Apache Beam`. Google Cloud also offers a managed service called `Vertex AI Feature Store` that allows you to scale dynamically based on your needs.

## Data Model

We will now discuss the data model used by the `Vertex AI Feature Store` service. It uses a time‐series model to store all the data, which enables you to manage the data as it changes over time. All the data in `Vertex AI Feature Store` is arranged in a hierarchy with the top level called a featurestore. This featurestore is a container that can have one or more entity types, which represents a certain type of feature. In your entity type you can store similar or related features.

*   `Featurestore` → `EntityType` → `Feature`

As an example, [Table 13.1](#c13.xhtml#c13-tbl-0001) has data of baseball batters. The first step is to create a featurestore called `baseballfs`.

[**TABLE 13.1**](#c13.xhtml#R_c13-tbl-0001) Table of baseball batters

| Row | | `player_id` | | `Team` | | `Batting_avg` | | `Age` | |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 | | `player_1` | | `RedSox` | | `0.289` | | `29` | |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 2 | | `player_2` | | `Giants` | | `0.301` | | `32` | |
| 3 | | `player_3` | | `Yankees` | | `0.241` | | `35` | |

You can then create an `EntityType` called `batters` and map the column header `player_id` to that entity. You can then add `team`, `batting_avg`, and `age` as features to this `EntityType`.

Here `player_1` and `player_2` are entities in this `EntityType`. Entities must always be unique and must always be of type `String`.

`RedSox`, `Giants`, and `Yankees` are featurevalues in the featurestore.

## Ingestion and Serving

`Vertex AI Feature Store` supports both batch and streaming ingestion. A typical method to do this is to have the feature stored in `BigQuery` and then ingested into the Feature Store.

For retrieving features from the Feature Store, there are two methods: batch and online. The batch method is used for the model training phase and the online method is used for online inference. When you request data from time `t`, the `Vertex AI Feature Store` returns values at or before time `t`.

# Vertex AI Permissions Model
