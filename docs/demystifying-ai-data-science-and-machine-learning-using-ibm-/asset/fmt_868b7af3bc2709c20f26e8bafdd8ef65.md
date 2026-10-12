
# Case Study—Airline Recommendation

One important thing to remember in data exploration is the need to understand the variables and their attributes before creating charts and graphs. This understanding is crucial because it helps us determine the appropriate types of graphs to use and how to interpret the outputs. Therefore, before running any visualizations, it's essential to first gather basic information about the dataset, including the number of variables, their descriptions, and their measurement scales. This information will guide us in selecting the most suitable graphs to make sense of the data.

In this chapter, I will use the airline recommendation dataset as an example to demonstrate various types of visualizations using SPSS Modeler. First, let's examine the parameters and characteristics of this dataset.

![](images/ufig4_3.jpg)

In this case study, a large-scale survey was conducted with passengers from multiple airlines across the United States flying a specific airline from one origin to a destination. They were asked to complete a survey about their flight experience and whether they would recommend that airline to others. The survey collected demographic information and details about their flight experience, including the origin and destination states, number of previous flights, travel purposes, spending at the airport, and price sensitivity. The passenger survey data were then consolidated with airline status and flight variables, such as flight distance, flight time, departure and arrival delays, and flight cancellations.

The goal of this project is to predict the target variable: passengers’ airline recommendations. We aim to identify which model best predicts this target variable and which variables are significant predictors. These predictions would help airline executives develop strategies to improve operations and services, thereby attracting more passengers.

Given the number of variables in the dataset, it's essential to first examine those variables, their roles, and their scales. [Table 4.2](#chapter4.xhtml#tbl4_2) describes the variable names, descriptions, and scales in this dataset.

![](images/ufig4_4.jpg)

**TABLE 4.2 Data Description** [Return to text.⏎](#chapter4.xhtml#b4tbl4_2)

| Variable Name | Label/Description | Scale | Role |
| --- | --- | --- | --- |
| `recommend` | Recommend the airline | Flag (Binary)(Yes/No) | Target |
| `airline_st` | Airline status | Nominal | Input |
| `age` | Age | Continuous | Input |
| `gender` | Gender | Flag (Binary)(Male/Female) | Input |
| `price_sensitivity` | Price sensitivity | Continuous | Input |
| `no_years_flying` | Number of years flying | Continuous | Input |
| `no_flt_pa` | Average number of flights per year | Continuous | Input |
| `pct_flt_other_airline` | Percent of flights with other airlines | Continuous | Input |
| `type_of_travel` | Travel purpose | Nominal | Input |
| `no_other_lty_cards` | Number of other loyalty cards | Continuous | Input |
| `shopping_amt_airpt` | Shopping amount at airport | Continuous | Input |
| `eat_drink_airpt` | Spending for eating and drinking at airport | Continuous | Input |
| `Class` | Passenger class | Nominal | Input |
| `origin_state` | Origin state | Nominal | Input |
| `destin_state` | Destination state | Nominal | Input |
| `depart_delay_in_minutes` | Departure delay (in minutes) | Continuous | Input |
| `arrival_delay_in_minutes` | Arrival delay (in minutes) | Continuous | Input |
| `flt_cancel` | Flight cancellation | Flag (Binary)(Yes/No) | Input |
| `flt_time` | Flight time (in minutes) | Continuous | Input |
| `flt_distance` | Flight distance (miles) | Continuous | Input |

*   **Variable names**: Since variable names are used in actual analyses and results, they should be both clear and concise. A variable name should be descriptive enough to allow easy recognition of the variable, yet brief enough to prevent it from being cut off in the output. Many software applications impose length limits on variable names. I strongly recommend avoiding the use of blank spaces or special characters (e.g., `@#$%^&*`) in variable names. Some software programs, like SAS Enterprise Miner and RapidMiner, do not permit spaces or special characters and will generate error messages if these issues are detected in variable names. The same requirements apply to programming languages such as R or Python. While some software, like SPSS Modeler, may be more flexible with variable names, integrating models with platforms like Python can still lead to errors if naming conventions are not followed. Therefore, it is best to adhere to correct naming practices. To separate words in a variable name, use an underscore (`_`) instead of a space.

*   **Variable labels/descriptions**: The details of a variable can be provided in its description, often referred to as “labels” in some applications. The description or label offers users a more detailed explanation of the variables. As shown in [Table 4.2](#chapter4.xhtml#tbl4_2), the labels clearly describe each variable and include measurement units, such as years, minutes, or miles. Labels are especially helpful when variable names are short or use acronyms, as they provide clarity and context. While there are no strict limits on variable descriptions, it is advisable to keep them clear and concise to avoid confusion or misinterpretation.

    In software applications with user interfaces (UI), such as SAS Enterprise Miner, SPSS Modeler, or RapidMiner, labels can often be displayed alongside variable names. This feature allows users to refer to the label for a full understanding of the variable when the name alone is not sufficiently descriptive. Additionally, labels can be used instead of variable names in outputs for reporting purposes. However, lengthy labels can pose challenges in reports by enlarging output tables, making them difficult to fit within the report. They can also create difficulties when presenting graphs. Therefore, it's important to choose labels carefully.

*   **Measurement scales**: Measurement scales are crucial for analysis, particularly when selecting the appropriate machine learning algorithms during the modeling step. As discussed in [Chapter 2](#chapter2.xhtml), variables can have different scales, including nominal, flag (or binary), ordinal, or continuous. In [Table 4.2](#chapter4.xhtml#tbl4_2), the dataset includes one flag (binary) target variable, two flag (binary) predictors, five nominal predictors, and 11 continuous predictors. Note that the `price_sensitivity` variable uses a Likert scale, and we assume the intervals between levels are equal. Therefore, it is treated as a continuous variable (see [Chapter 2](#chapter2.xhtml) for a more detailed discussion on the Likert scale).

*   **Role**: The role of a variable is another critical piece of information. Variables generally have two primary roles: **Target** or **Input**. The target variable is the one we intend to predict, while input variables (also known as predictors) are used to make that prediction. In our example, `recommendation` is the target variable with a flag (binary) scale, while the other variables serve as predictors. Additionally, there are other roles, such as **Record ID** (a record identifier), **Partition** (used to partition the data), **Split** (a model is built for each possible value of the field), **Frequency** (a frequency weighting factor), and **None** (the variable is ignored). For now, we will focus primarily on the Target and Input roles. The Partition role will be used later in the modeling process.

## Add Data to SPSS Modeler
