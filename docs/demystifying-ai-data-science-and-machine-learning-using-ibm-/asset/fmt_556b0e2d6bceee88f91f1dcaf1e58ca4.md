
### 3. Provide descriptive statistics

Provide descriptive statistics results of the data. It includes measures such as frequency, mean, median, mode, standard deviation, minimum, maximum, or any other relevant statistical measures that help describe the characteristics of the dataset.

### 4. Present data mining results

Present the main results of your data mining analysis. This part should include the outcomes of all predictive models that you trained and validated. Report the specific model fit metrics for each model, model comparison, and the champion model. Present and explain the predictive power of the champion model, its detailed structure, and data patterns detected by this model. Finally, present the variable importance results to show which predictors are important and rank them by order.

### 5. Visualize the results

Use visualizations such as tables, charts, graphs, or diagrams to enhance the understanding of your results. Choose visual representations that are appropriate for the type of data and the research objectives. Include captions or labels to provide clear explanations of the visualizations. Visualization is usually easier to understand and follow than just texts.

### 6. Explain the findings

Explain the findings of your data mining analysis objectively in the context of your research objectives. It is to help the readers follow and understand the findings. Don’t assume that they can understand everything just by looking at tables or graphs. Explain the patterns, relationships, or insights that emerge from the analysis and avoid interpreting and discussing the findings. The objective of this section is to present the results objectively without influencing the readers.

### 7. Highlight new discoveries

Compare your results with the findings from existing literature in the field of data mining. If your results show any new discoveries, such as new significant predictors, new relationships, or new patterns, highlight them.

### 8. Provide supplementary analysis

Consider providing additional supplementary analysis if relevant to support or clarify your main findings. This could include sensitivity analyses, subgroup analyses, or additional exploratory data mining techniques that help deepen the understanding of the results.

### 9. Write and revise

Start by drafting the results section and incorporating the points discussed above. Once you have a draft, review and revise it multiple times. Make sure that the information is presented clearly, concisely, and in a well-structured manner. Use appropriate terminology and provide sufficient context for readers to understand and follow the results.

The results section should provide a comprehensive and clear presentation of the findings derived from your data mining analysis. It should be supported by appropriate statistical measures, visualizations, and interpretation. By effectively communicating the results, you contribute to the overall credibility and impact of your research.

## Example of Writing a Results Section

![](images/ufig11_17.jpg)

Below are specific examples demonstrating how to write the results section for the airline recommendation paper. These results are extracted from the findings in previous chapters and presented in a clear, objective manner.

### Demographic Information

This section provides readers with essential information about the demographic characteristics of individuals, cases, or organizations in the dataset. Presenting demographic information helps the audience understand the sample's makeup and how it connects to the data mining outcomes. It also justifies the representativeness of the sample, supporting the generalizability of the study's findings.

Depending on data availability, you should select relevant demographic variables to present. In [Chapter 4](#chapter4.xhtml), we explored the airline recommendation dataset and used multiple charts to visualize the data. Since the dataset is based on passenger survey responses, you should focus on passengers’ primary demographic characteristics. Bar charts and pie charts are effective methods for visualizing this information. Drawing from the data description ([Table 4.1](#chapter4.xhtml#tbl4_1) in [Chapter 4](#chapter4.xhtml)), you can present key demographic variables such as age, gender, airline status, and travel purposes. In this section, I highlight the most relevant visualizations from [Chapter 4](#chapter4.xhtml) for demonstration purposes.

It's important to remember that the graphs provide detailed demographic information, so repeating the same details in the report isn’t necessary. Instead, focus on explaining and highlighting significant patterns or insights for readers to notice.

Here is an example of the demographic information results.

[Refer to [Chapter 4](#chapter4.xhtml) for detailed results.]

### Descriptive Statistics Results

Descriptive statistics provide readers with an overview of the statistical measures summarizing the characteristics of all variables in the dataset. It is helpful to present detailed descriptive statistics for both categorical and interval variables using tables, as this allows for a clear and comprehensive view of the data. However, rather than explaining every detail, the focus should be on key observations or any notable trends that stand out.

Below is an example of how to write this part.

[Refer to [Chapters 4](#chapter4.xhtml) and [5](#chapter5.xhtml) for detailed results. The only update here is the revised descriptive statistics for the price sensitivity variable, as we re-coded zero values to missing values during the data modification step. This replacement, which was completed in [Chapter 5](#chapter5.xhtml), was done using the `Filler` node to replace zero values with missing values. After applying the `Filler` node, running the `Data Audit` node again on the entire dataset provided the updated descriptive statistics for the price sensitivity variable.]

### Data Mining Results

This part is crucial as it presents the data mining results. Typically, you start with the model comparison to identify the champion model. Then, you provide details about the champion model, including its predictive power, structure, and variable importance. It is important not to repeat the details from tables and charts in the text but rather explain what they mean and highlight what the readers should focus on. You also need to explain the decisions you made throughout the process and provide justification for those choices.

Let's begin by presenting the model comparison results. Usually, both tables and charts are useful to illustrate the comparison between models using various model fit metrics. While ROC charts and Lift charts are commonly used metrics, in this case, it is not feasible to present these charts for all models in a single view because we extracted model fit metrics from different streams. Furthermore, the curves of the models are often very close to each other, making it difficult to distinguish the superior model from the charts alone. Therefore, we chose to present the ROC index, which is easily extracted from the `Analysis` node output. Additionally, we could use the Lift value (for 20% of responses) from the Lift chart, but since both metrics give similar outcomes, the ROC index was selected for its simplicity. Presenting the results in a table format allows for a clearer comparison.

Below is an example of how to write the model comparison results in this hypothetical scenario.

[Refer to [Chapters 7](#chapter7.xhtml)–[9](#chapter9.xhtml) for the detailed results.]

Now that the champion model has been identified, it is important to further examine its performance to ensure that the results are reliable and valid and that the model possesses strong predictive power.

Below is an example of how to write this part.
