# 4.3.4 IMPUTATION

Missing values in the dataset lead to unreliable measures of the model's performance. Instances of data with missing values can be dropped or imputed. In this work, qualitative and quantitative attributes are imputed through statistical measures like mean, median, and mode.

# 4.3.5 FEATURE ENCODING

Feature encoding is an essential preprocessing step for the structured dataset in supervised learning. Since the machine learning algorithms cannot understand categorical attributes, it is essential to encode the attributes. Nominal attributes are those that do not follow any order, such as, for example, the gender of a person. Ordinal attributes are those where the order is essential, such as, for instance, a person's income or a student's grade. Almost every attribute is nominal and applied label encoding. Only one attribute was ordinal and applied ordinal encoding.

# 4.3.6 FEATURE SCALING

Feature scaling is the process of standardizing the attributes in a fixed range. Feature scaling is mainly done either by normalization or standardization. StandardScaler has been used here to standardize features. This transforms each attribute's value to a mean of zero and a standard deviation of one. StandardScaler has been used, since most of the attributes followed a normal distribution.

# 4.3.7 SPLITTING THE DATASET

The dataset is split into training (80%) and test (20%) datasets in a stratified manner for building and validating the model. The dataset is split in a stratified manner to overcome the data imbalance issue. The training dataset is used for model building, and the test dataset is used to validate the model.

# 4.3.8 FEATURE SELECTION

Feature selection helps to identify the important attributes for model building. The cirrhosis dataset consists of 19 independent variables. Relationships among the independent variables are checked using Pearson correlation (r), as given in Equation 4.3. The non-parametric statistical test is also used to identify attribute relationships.

$$r = \frac{\sum (x_i - \bar{x})(y_i - \bar{y})}{\sqrt{\sum (x_i - \bar{x})^2 \sum (y_i - \bar{y})^2}} \tag{4.3}$$

x_i and y_i are variable samples and r ranges from −1 to +1, where zero specifies that there is no relation between the two variables. If the value is greater than zero, it indicates a positive relationship between two variables; if the value is less than zero,