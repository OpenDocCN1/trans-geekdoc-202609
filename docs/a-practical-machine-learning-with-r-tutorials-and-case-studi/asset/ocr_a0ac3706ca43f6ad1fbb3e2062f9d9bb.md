200 8 Logistic Regression — Handling Imbalanced Data

+   - How to identify problems related to imbalanced data — unequal distribution of the binary classification variable (see the interactive Section 8.4).

+   - How to troubleshoot an imbalanced Logistic Regression, when predictive quality varies dramatically between sensitivity and specificity (see the interactive Section 8.5).

+   - How to use downsampling and upsampling to install an imbalanced dataset (see the interactive Section 8.5).

# # 8.2 R Packages Required for the Chapter

This section lists the R packages that you need to load and execute code in the interactive sections in RStudio. Please install the following packages using Tools -> Install Packages ... from the RStudio menu (you can find more information about installing and loading packages in Section 8.4):

+   - The rio package (Chin et al. (2021)) to enable the loading of various data formats with one import() command. Files can be loaded from the user's hard drive or the Internet.

+   - The janitor package (Firke (2023)) to rename variable names to Upper-Camel and to substitute spaces and special characters in variable names.

+   - The tidymodels package (Kuhn and Wickham (2020)) to streamline data engineering and machine learning tasks.

+   - The tableExtra package (Zhu (2021)) package to support the rendering of tables.

+   - The learner package (Aden-Bieue et al. (2022)), which is needed together with the shiny package (Chang et al. (2022)) for the interactive exercises in this book.

+   - The shiny package (Chang et al. (2022)), which is needed together with the learner package (Aden-Bieue et al. (2022)) for the interactive exercises in this book.

+   - The glm2 package (Friedman et al. (2010) and Tay et al. (2023)), which is needed to execute Logistic Regression.

+   - The themis package (Hvitfeldt (2023)) to up- and downsample imbalanced datasets with advanced algorithms.

> ^¹See Section 4.8 for the concepts of sensitivity and specificity.