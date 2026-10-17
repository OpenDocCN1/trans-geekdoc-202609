
**HDSinRdata** package. The goal of the code is to plot the worst diastolic blood pressure reading against the worst systolic blood pressure reading for each patient, colored by hypertension status. However, the code currently generates an error message. What is wrong with the code? There are four errors for you to identify and fix.

```r
data(NHANESsample)

nhanes_df <- NHANESsample %>%
  mutate(worst_DBP = max(DBP1, DBP2, DBP3, DBP4),
         worst_SBP = max(SBP1, SBP2, SBP3, SBP4))

ggplot() %>%
  geom_point(data = nhanes_df,
             aes(x = worst_SBP, y = worst_DBP),
             color = HYP)
```

3. The following code uses the breastcancer data from the **HDSinRdata** package. The goal is to create a logistic regression model for whether or not the diagnosis is benign or malignant and then to create a calibration plot for the model, following the code from Chapter 14. Debug and fix the code. Hint: there are three separate errors.

```r
data(breastcancer)

model <- glm(diagnosis ~ smoothness_worst + symmetry_mean +
               texture_se + radius_mean,
             data = breastcancer, family = binomial)

pred_probs <- predict(model)

num_cuts <- 10
calib_data <- data.frame(prob = pred_probs,
                         bin = cut(pred_probs, breaks = num_cuts),
                         class = mod_start$y)

calib_data <- calib_data %>%
  group_by(bin) %>%
  summarize(observed = sum(class)/n(),
            expected = sum(prob)/n(),
            se = sqrt(observed * (1 - observed) / n())))
```

```r
calib_data

ggplot(calib_data) +
  geom_abline(intercept = 0, slope = 1, color = "red") +
  geom_errorbar(aes(x = expected, ymin = observed - 1.96 *
    se,
                   ymax = observed + 1.96 * se),
                color = "black", width = .01) +
  geom_point(aes(x = expected, y = observed)) +
  labs(x="Expected Proportion", y="Observed Proportion") +
  theme_minimal()
```

![](img/58a554e865d49ca347d9a3f76f8f0812_350_0.png)

Taylor & Francis Group

http://taylorandfrancis.com

![](img/58a554e865d49ca347d9a3f76f8f0812_352_0.png)

Figure 22.1: Creating a New R Quarto Document.

The extension .qmd. Make sure to save this file with a suitable name in your desired location on your computer by selecting File -> Save, and then you’re ready to start writing your report! Your file should now look like Figure 22.2.

At the top of this pane is a toggle between source and visual mode. In visual mode, we can see that we have a text toolbar including options to bold text or add a list. If we switch to source mode, our text reveals the underlying Markdown in Figure 22.3 and the toolbar disappears. This chapter focuses on teaching you to edit in source mode, but you can always switch to visual mode if you prefer.

We write all of the text and code that we would like to include in your report in this .qmd file, and then produce a nicely formatted report from this file by ‘rendering’ the file. We can either render to HTML, PDF, or Word by clicking on the Render button from the toolbar at the top of the page. To update our format from PDF, we change the text in the top block to format: html or format: word.

![](img/58a554e865d49ca347d9a3f76f8f0812_353_0.png)

Figure 22.2: A New Quarto Document.

![](img/58a554e865d49ca347d9a3f76f8f0812_353_1.png)

Figure 22.3: Source Mode.

To apply the same options to all chunks in the document at once, you can add them to the first chunk at the very top of your Quarto that has the label `setup` using the `knitr::opts_chunk$set()` function. These are called the global settings. For example, using the following code for your first code chunk ensures that none of the errors, warnings, or messages from any of the code chunks appear in your final report. It is also good practice to load all the packages you are using for your report within this first code chunk using the `library()` function. For example, we load the tidyverse and HDSinRdata packages.

```{r}
#| label: setup
#| include: false
knitr::opts_chunk$set(echo = TRUE, warning = FALSE,
                      error = FALSE, message = FALSE)
library(tidyverse)
library(HDSinRdata)
```

If you want to display the code for your report in a code appendix, you can easily do this by creating an empty code chunk at the end of your .qmd file that looks like the following. This finds all other chunks and displays the code.

```{r ref.label = knitr::all_labels()}
#| echo: true
#| eval: false
```

## 22.2 Formatting Text in Markdown

To add text to your report, you can simply type directly into the Quarto file, between the code chunks. This code is formatted using Markdown, which allows us to specify how to format and display the text when it is knit. For example, adding a single asterisk * on either side of some text italicizes it, while adding a double asterisk ** on either side of text makes it bold. To indicate code, you can use backticks ` .

regular text regular text

*italicized text* italicized text

**bold text** bold text

`code text` code text

To create headers and sections, you can add the # symbol in front of your text. Adding more of these symbols makes the headers smaller, which is useful for making sub-headers (see Figure 22.4).

```text
# Header
## Smaller Header
### Even Smaller Header
```

# Header

## Smaller Header

### Even Smaller Header

Figure 22.4: Example Header Sizes.

You can also add links [text](www.example.com) and images ![alt text](#fig-label image.png). In the latter example, fig-label becomes the label of the image we can use to cross-reference it, while image.png is the image file name (see Figure 22.5).

Example link.²

![](img/58a554e865d49ca347d9a3f76f8f0812_357_1.png)

**Figure 22.5:** Example Image.

The Markdown Guide³ has a great cheat sheet⁴ as well as more resources for formatting Markdown text.

You can also have inline R code by using single backticks around your code `r max(c(1,2,3))`. The code must start with r to be run when knit. This allows you to reference variables in your text. For example, we could display the variance of a column in our data without having to copy the value over `r round(var(cars$speed),2)`.

## 22.3 Formatting Figures and Tables

Often, you’ll want to include figures generated by your code in your report, and you can customize these figures by changing the chunk options for the chunks that produce them. To change the size of a figure, you can add in the chunk option `fig-width: 3` with your desired size in inches. To add a nice caption to a figure in your report, you can add `fig-cap : 'Your Desired Caption.'` option. To name a figure, you want to start your label with `fig-` such as `fig-myfigure`.

By default, the figures generated by your code chunks are allowed to ‘float’ in Quarto. This means that the figures might move away from where they were coded or referenced in the final report. To prevent this behavior, you can

- ² https://alicepaul.github.io/health-data-science-using-r/
- ³ https://www.markdownguide.org/
- ⁴ https://www.markdownguide.org/cheat-sheet/

To demonstrate the abilities of these packages, let's suppose that we wanted to display the head of the first few columns of the NHANESsample data from the HDSinRdata package. The following code produces the corresponding output in the knitted pdf report. You can see in Table 22.1 that it essentially just copies the raw output from R, which is rather messy.

```r
NHANESsample %>%
select(AGE, SEX, EDUCATION, INCOME, LEAD) %>%
head()
```

**Table 22.1**

|    | AGE | SEX | EDUCATION | INCOME | LEAD |
|----|-----|-----|-----------|--------|------|
| 1  | 77  | Male | MoreThanHS | 5.00 | 5.0 |
| 2  | 49  | Male | MoreThanHS | 5.00 | 1.6 |
| 3  | 37  | Male | MoreThanHS | 4.93 | 2.4 |
| 4  | 70  | Male | LessThanHS | 1.07 | 1.6 |
| 5  | 81  | Male | LessThanHS | 2.67 | 5.5 |
| 6  | 38 | Female | MoreThanHS | 4.52 | 1.5 |

We use the `kable()` and `kable_styling()` functions from the kableExtra package to produce a more nicely formatted table. The `kable()` function generates a table from a data frame. The `kable()` function allows you to specify some display options for your table. For example, you can add a caption to your table using the `caption` argument, and you can change the names of the columns in the table using the `col.names` argument. The `kable_styling()` has additional options available. Similar to the `fig-pos = H` command described for figures in the previous section, adding “HOLD_position” to the `kable_styling()` function prevents the table from floating on the report; adding “scale_down” scales the table so that it fits in the margins of the paper. The updated code and output are shown in the following code chunk and Table 22.2. See the documentation for the `kable()` and `kable_styling()` functions for more options available.

```r
NHANESsample %>%
select(AGE, SEX, EDUCATION, INCOME, LEAD) %>%
head() %>%
kable(col.names = c("Age", "Sex", "Education Level",
"Poverty Income Ratio", "Lead Level")) %>%
kable_styling(latex_options = c("scale_down", "HOLD_position"))
```

