+   - User dataset: The user dataset contains attributes about the users. This allows Personalize to have a better representation of each user to provide highly personalized recommendations. This dataset is also optional.

+   - User-item interaction dataset: This is a required dataset, and it provides the historical interaction between users and items, such as viewing a movie or purchasing a product. Personalize uses this data to learn the behaviors of individual users towards different items to generate highly personalized recommendations.

To help understand how Personalize works, let's review some of the main Personalize concepts:

+   - Dataset group: Dataset group contains the related datasets (item, user, and interaction dataset) for model training.

+   - Recipe: A recipe is the ML algorithm that's used for model training. Personalize provides multiple recipes for the three main functionalities.

+   - Solution: A solution represents a trained Personalize model.

+   - Campaign: A Personalize campaign is a hosted endpoint for a trained Personalize model to handle recommendation and ranking requests.

To train and deploy a custom model using Personalize, you must follow these steps:

+   1. **Prepare and ingest the dataset**: In this step, you prepare the dataset in the required format, store it in S3, and then load the dataset into Personalize. There are three API actions involved in this step – `CreateDatasetGroup`, `CreateDataset`, and `CreateDatasetJob`. `CreateDatasetGroup` creates an empty dataset group. `CreateDataset` adds datasets (for example, item dataset, and interaction dataset) to a dataset group, and `CreateDatasetJob` kicks a data ingestion job to load data from S3 to the Personalize repository for subsequent model training.

+   2. **Pick a recipe for model training**: In this step, you choose a recipe (ML algorithm) to use for the different model training processes. There are multiple recipe options available for user personalization, related items, and personalized ranking. You can use the `ListRecipes` API to get the full list of recipes.

+   3. **Create a solution**: In this step, you configure a solution with the dataset group and recipe for the model training job using the `CreateSolution` API. Then, you use the `CreateSolutionVersion` API to kick off the training job.