
# Introduction

Moreover, this aligns with the idea that health is closely tied to happiness. Cultivating positive behaviours, such as maintaining a healthy lifestyle, fostering social connections, and contributing to one's community, can significantly impact both health and happiness. These behaviours can be universal, yet their interpretation and emphasis might vary based on cultural contexts.

## 1.1.2 A Global Perspective

In essence, global standardisation in well-being requires a multi-faceted approach that includes education, social support systems, and a collective effort to reshape cultural narratives. It's a complex task, but incremental changes in education and social structures contribute to a more harmonised vision of well-being across diverse cultures.

The aim of this book is to provide extensive information on how the well-being can be statistically measured. Public health metrics, such as Years of Life Lost (YLL) and Years with Disability (YLD), are examples of the health metrics discussed and used throughout this book. They are expressed in number of years of life lost or years lived with disabilities, and their sum represents a crucial value: Disability Adjusted Life Years (DALYs). DALYs are generally used for ranking the health status of a population. The book covers the history of the development of the health metrics and aims at stimulating reasoning to suggest alternatives by providing a comprehensive manual to make reference to if you get lost among the plethora of. The hope is to provide insights for health researchers and policymakers.

To be more specific, the book compares the metrics to summarise the health status of population across different locations. It tests prediction levels using key models. The initial tools are {tidymodels} and {INLA} for modelling, but other machine learning packages like {fml3} and {caret} are also tested as alternative tools.

In practice, the data will include information about health such as age, life expectancy, mortality, and risk levels. The interesting part is related to the identification of insights from outbreaks to predict and manage future ones. This is done through a process called model transfer. Each outbreak breaks as a story with unique but similar events, like the spread patterns and impacts of diseases. By studying these stories, models can be built to capture factors influencing outbreaks, such as transmission rates, environmental triggers, and population behaviours.

A focus on the impact of recent infectious disease outbreaks, such as SARS-COVID-19, on the state of health of the population, will be provided along the most affected locations to compare results of both deterministic and stochastic (Bayesian) models. Risk factor analysis is another important aspect covered in this book. It aims at identifying connections that lead to an increase in the number of DALYs for specific populations. Additionally, it looks at providing suggestions for public health policy and practice.

> ²Kirstin Roster, Colton Vaughn, Francisco A. Rodrigues, “Forecasting New Diseases in Low-Data Settings Using Transfer Learning,” Chaos, Solitons and Fractals 161 (August 2022): 112306, doi:10.1016/j.chaos.2022.112306.

> ³Theo Vos et al., “Global Burden of 369 Diseases and Injuries in 204 Countries and Territories, 1990-2019: A Systematic Analysis for the Global Burden of Disease Study 2019,” The Lancet 396, no. 10258 (October 2020): 1204–22, doi:10.1016/S0140-6736(20)30925-9.

# The Structure of the Book

## 1.2 The Structure of the Book

The book is structured with an alternation of text and chunks of code, primarily in the R programming language; hints for translations in Python are provided in Appendix C. The book encourages readers to actively engage with real-world case studies, transforming theoretical concepts into practical skills. This hands-on approach enables readers to become practitioners, applying the methods learned directly to relevant scenarios.

The material supports fully exploratory data analysis and model visualisation, offering code for generating compelling visualisations using packages such as ggplot2, {leaflet}, {sf}, and {terra}, others which allow for extensive user customization. The inclusion of these tools is intended to unlock the full potential of the R language, broadening the reader's understanding of both spatial and health metrics.

To ensure reproducibility, the book-project employs the {renv} package, which provides a snapshot of the specific versions of all packages used during the writing of the book. Appendix B enables readers to restore all R package libraries to the exact versions they were at the time of writing, ensuring that all code works regardless of future package updates. This is crucial for readers who wish to recreate the analysis or adapt it to their own datasets.

This book is designed for practitioners at early stages of their careers and graduate students in STEM fields, yet it remains a valuable resource for experts who seek to have all the tools in one place for quick reference. The overarching goal of this book is to contribute to the scientific development of health metrics and evaluation, providing a comprehensive resource that supports both learning and application in this important field.

## 1.2.1 Navigating the Chapters and Key Concepts

### First Section: Metrics and Evaluation

The Metrics and Evaluation section introduces the foundational concepts of health metrics. Chapter 2 (Introduction to Health Metrics) provides an overview of the definitions, historical context, and development of health metrics over time. Chapter 3 (Methods and Calculations) is a first level calculation of the metrics, including Disability-Adjusted Life Years (DALYs) and Years of Life Lost (YLLs) and Years Lived with Disability (YLDs), along with Healthy Life Expectancy (HALE). Chapter 4 (Metrics Components) examines life tables, mortality rates, incidence, prevalence, and disability weights. Chapter 5 (Causation and Risks) focuses on factors influencing YLLs and YLDs. This is complemented by Appendix A, where detailed calculations are further explained.

### Second Section: Machine Learning

The Machine Learning section offers a deeper dive into evaluating health metrics using techniques and provides an overview of R packages. Chapter 6 (Introduction to Machine Learning) covers various types of models appropriate for health data. Chapter 7 (Techniques for Machine Learning Applications) provides practical case studies. Chapter 8 (Essential R Packages for Machine Learning) lists useful R packages for modelling.

> 4Christopher JL Murray and Julio Frenk, "Health Metrics and Evaluation: Strengthening the Science," The Lancet 371, no. 9619 (April 2008): 1191–99, doi:10.1016/S0140-6736(08)60526-7.

### Third Section: Data Visualisation

The Data Visualisation section equips readers with the knowledge to create and customise plots and maps. Chapter 9 (Predictive modelling and Beyond) focuses on applying predictive models to forecast health outcomes and trends. Chapter 10 (Introduction to Data Visualisation) discusses the history and application of data visualisation techniques in R. Chapter 11 (Interpreting Model Results Through Visualisation) provides detailed methods for tailoring representations to enhance data interpretation. Chapter 12 (Spatial Data Modelling and visualisation) instructs on how to create informative maps, Chapter 13 (Advanced Data Visualisation Techniques) presents practical examples to reinforce learning.

### Fourth Section: Infectious Diseases

The Infectious Diseases section starts with Chapter 14 (Introduction to Infectious Diseases) setting the stage for detailed case studies. Chapter 15 (COVID-19 Outbreaks) and Chapter 16 (The Case of Malaria) provide in-depth analysis of COVID-19 and malaria, illustrating how these diseases impact population metrics. The section concludes with Chapter 17 (Summary: The State of Health), comparing countries and regions to evaluate health status.
