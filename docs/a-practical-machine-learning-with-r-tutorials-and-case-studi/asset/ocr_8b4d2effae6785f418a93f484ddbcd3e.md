The impact of changing predictor variables for a machine learning model (see Section 11.5.2).

+   - How can use Variable Importance Plots (VIP) to identify predictor variables that are more or less important for the prediction. The less important variables are potential candidates to be dropped from the analysis (see Section 11.6).

+   - How can use SHAP values to quantify the contribution of each predictor variable to the prediction of a specific observation of interest (see Section 11.7).

+   - How can use the Local Interpretable Model-agnostic Explanations (LIME) to approximate a non-linear machine learning model with a linear OLS model. The latter can be used to interpret the impacts of predictor variables (see Section 11.8).

# # 11.2 R Packages Required for the Chapter

This section lists the R packages that you need when load and execute code in the interactive sessions in RStudio. Please install the following packages using Tools -> Install Packages ... from the RStudio menu (you can find more information about installing and loading packages in Section 3.4):

+   - The rio package (Chan et al. (2021)) to enable the loading of various data formats with one import() command. Files can be loaded from the user’s hard drive or the Internet.

+   - The janitor package (Firke (2023)) to rename variable names to Upper-Camel and substitute spaces and special characters in variable names.

+   - The tidymodels package (Kuhn and Wickham (2020)) to streamline data engineering and machine learning tasks.

+   - The cableExtra package (Zhu (2021)) to support the rendering of tables.

+   - The learner package (Aden-Buie et al. (2022)), which is needed together with the shiny package (Chang et al. (2022)) for the interactive exercises in this book.

+   - The shiny package (Chang et al. (2022)), which is needed together with the learner package (Aden-Buie et al. (2022)) for the interactive exercises in this book.

+   - The woodridge package (Shea (2023)) to provide the wage data that will be used throughout this chapter.