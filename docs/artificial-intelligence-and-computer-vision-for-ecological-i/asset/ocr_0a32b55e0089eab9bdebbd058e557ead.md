into a predictive model. This methodology can be extended and refined using more complex algorithms and additional predictor variables to augment the accurateness and reliability of crop yield predictions.

# Classification Models

Classification models are a pivotal aspect of AI and ML applied in the domain of crop yield estimation. These models aim to categorize data points into predefined classes based on their attributes. The primary goal is to govern which category a new observation belongs to, grounded on a training dataset comprising observations whose category membership is known.

# Example: Classification Model for Wheat Yield Estimation

Data Collection and Preprocessing: The application of classification models in crop yield estimation, consider a case study focused on estimating the yield of wheat. The dataset includes various features such as soil quality, weather conditions, and historical yield data. The features are:

+   1. Soil Quality Index (SQI)
+   2. Annual Rainfall (mm)
+   3. Average Temperature (°C)
+   4. Historical Yield (kg/hectare)

The target variable is the yield category, which can be classified as:

+   - Low Yield (0–2000 kg/hectare)
+   - Medium Yield (2001–4000 kg/hectare)
+   - High Yield (4001–6000 kg/hectare)

The dataset is divided into training and testing subsets, typically in a 70:30 ratio.

Model Selection: For this example, we use a Decision Tree classifier, known for its interpretability and effectiveness in handling both numerical and categorical data.

Training the Model: The training dataset comprises 70% of the observations. Each observation is characterized by its features and the corresponding yield category.

Table 11. Sample data for yield classification based on soil quality index (SQI), rainfall, temperature, and historical yield.

| Observation | SQI | Annual Rainfall (mm) | Average Temperature (°C) | Historical Yield (kg/hectare) | Yield Category |
|---|---|---|---|---|---|
| 1 | 85 | 450 | 18 | 2500 | Medium |
| 2 | 78 | 500 | 20 | 3200 | Medium |
| 3 | 92 | 600 | 15 | 4200 | High |
| ... | ... | ... | ... | ... | ... |

Source: Author’s calculation.