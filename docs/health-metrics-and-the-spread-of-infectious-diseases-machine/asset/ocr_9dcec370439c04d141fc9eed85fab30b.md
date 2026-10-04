# Model Selection Strategies

several orders of magnitude; without standardisation, a model might incorrectly interpret the scale of a feature as a proxy for importance.

Furthermore, the application of transformations, such as logarithmic scaling or the application of spline functions can help in managing skewed data or enhancing model ability to capture non-linear relationships, which result particularly useful in complex data modelling. In addition, tailored adjustments, and more sophisticated manipulations have been implemented over time to allow estimation of missing values in order to obtain customised, flexible, and more homogeneous data. For more information on feature engineering, see¹ useful for effective machine learning strategy application, covering various techniques and appropriate use cases, focusing on practical understanding and implementation.

# 7.3 Model Selection Strategies

In developing predictive models for health metrics and infectious diseases, selecting the appropriate model is critical to ensure accuracy and reliable forecasts. Here are outlined sample examples used in the model selection process, we introduce the Rabies dataset used for our discussion and demonstrate the selection of a suitable model for analysing its impact. Rabies, although nearly 100% fatal symptoms appear, presents a unique challenge due to the relative rarity of cases and limited availability of comprehensive data. This scarcity complicates efforts to model the disease accurately and develop public health strategies.

To address these challenges, we explore advanced modeling techniques that can enhance the robustness of our analyses despite data limitations, which evaluating multiple models based on their performance and selecting the best-fitting models to achieve the most accurate predictions.

# 7.4 Example: Rabies

The rabies dataset from the {hmsidR} package contains information on death rates and disability-adjusted life years (DALYs) per 100,000 inhabitants due to rabies and all causes of mortality in Asia and the Global region from 1990 to 2019. Rabies² (²) is a fatal viral infection, and is also classified as an infectious disease that can infect all mammals causing encephalitis. Caused by the rabies virus, which belongs to the Lyssavirus genus, it is transmitted to humans through the bite of an infected animal such as bats, raccoons, foxes, and obviously dogs, which are the main source of human deaths³ neglected tropical diseases (NTD) predominantly affect already generalised, poor and vulnerable populations. Although effective human vaccines and immunoglobulins for rabies, these are not readily available or accessible to everyone⁴

> ¹Brandon Butter and Brian J. Smith, The American Statistician, 74, no. 3 (July 2020): 308–9, doi:10.1080/00031303.2020.1700217.
²CDC, "About Rabies," May 14, 2024, https://www.cdc.gov/rabies/about/index.html.
³Katie Hopkins et al., "Estimating the Global Burden of Endemic Canine Rabies," PLOS Neglected Tropical Diseases 9, no. 4 (April 2015): doi:10.1371/journal.pntd.0003709.
⁴"Rabies," n.d., https://www.who.int/news-room/fact-sheets/detail/rabies.