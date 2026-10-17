
Unfortunately then, there is no simple answer to the question, ‘How large a sample do I need?’ since it depends on the particular research you are conducting, the outcome measures you are using and the size of the effect you might be expecting.^()

In practice, there are often limitations in terms of time, resources and the available sample. For example, if there are only 30 referrals to a counselling service during the year, and you need to evaluate the service after a year, then that is your sample. Alternatively, if this is deemed to be too small a sample for your purposes (to provide meaningful results) then you would have to extend the recruitment period until you achieved a larger sample. Now let us move on to something simpler and more enjoyable – re-coding the data.

69 Page 69 

## 4.5Re-coding interval variables into categorical variables

In our data we have only two categorical variables that we could cross-tabulate: sex of patients and counsellors (and we’ve done that). Sometimes, however, it is useful to transform interval variables into categories so that they can be cross-tabulated with existing categorical variables. As we will see in the following exercise, and the exercises at the end of this chapter, grouping interval data into categories can reveal interesting comparisons that would not otherwise be apparent.

For example, we might wish to cross-tabulate sex and age of patients. Obviously we are unable to do this because the age data is not in categories – we would end up with as many categories as there are ages! What we could do, however, is to put the ages into categories, say 20–9, 30–9, 40–9, and then cross-tabulate the *age categories* with sex of patients. In SPSS we do this by re-coding variables.

### Re-coding age into categories

1.  From the menu at the top of the screen click **Transform** then **Recode into different variables**. This should produce the dialogue box shown. (Note: If we had chosen ‘Into same variables’ our re-coding would *over-write* the existing data; not a good choice!)

2.  Next put the variable **age** into the **Input Variable** box (the title of this box changes to **Numeric Variable** after you put **age** into it).

3.  Under **Output Variable** on the right side of the box type in a name for the new age variable you will be creating. I have used **agecats** to stand for age categories, and added a fuller description below in the **Label** box: age categories.

4.  Click **Change** and this will then appear in the **Numeric Variable/Output Variable** box.

    ![Screenshot 4.4](Images/p69-1.jpg)

    Screenshot 4.4

    70 Page 70

5.  Click **Old and New Values** to open the recode dialogue box.

6.  Click in the circle next to **Range** to enter age categories. In our data, age ranges from 21 to 49, so we will use the following categories: 20–9, 30–9, 40–9.

7.  First enter 20, then 29 (as shown below), then in the **New Value** box type in 1. You have assigned the number 1 to the age category 20–9.

    ![Screenshot 4.5](Images/p70-1.jpg)

    Screenshot 4.5

8.  Now click **Add** and this will be entered into the **Old–New** variable box below.

9.  Continue until you have assigned numbers to all the age categories, as illustrated next: 71 Page 71

    ![Screenshot 4.6](Images/p71-1.jpg)

    Screenshot 4.6

10.  Click **Continue,** then click **OK** on the next screen. Your database will now have an additional variable that you have created called **agecats**. (If your new variable includes decimal places, remove them in **Variable View**.)

    ![Screenshot 4.7](Images/p71-2.jpg)

    Screenshot 4.7

11.  Be sure to check that you have conducted this procedure correctly – that your categories actually match, i.e., check that a 1 in agecats is within the range 20–9 in the age variable, that a 2 = 30–9 and a 3 = 40–9.

12.  You should then add value labels to your age categories – by going into the **Variable View** and clicking on **Values** (as described in [Chapter 2](#07_Chapter02.xhtml)). You should also change the **Measure** from **Scale** to **Ordinal**.

13.  Once you have added value labels, you can run crosstabs on **sex** and **agecat** by going to **Analyze** then **Descriptive Statistics** then **Crosstabs**. Move **sex** into Rows and **agecats** into Columns. Then click on the **Cells** tab and check that there is a tick in the box next to **Observed counts** and **row percentages** in the **Crosstabs: Cell Display** box as illustrated next: 72 Page 72

    ![Screenshot 4.8](Images/p72-1.jpg)

    Screenshot 4.8

14.  Click **Continue,** then **OK**.

This should produce the following table:

**Table 4.8**Cross-tabulation of sex with age categories

| sex \* agecats Crosstabulation  |

| --- |

|  || agecats || Total |

| --- | --- | --- |

| 20-29 || 30-39 || 40-49 |

| sex || male || Count% within sex || 535.7% || 750.0% || 214.3% || 14100.0% |

|  || female || Count% within sex || 212.5% || 743.8% || 743.8% || 16100.0% |

| Total ||  || Count% within sex || 723.3% || 1446.7% || 930.0% || 30100.0% |

A table titled sex agecats crosstabulation lists the count and percentage values within sex for male and female, and total values in column 1. Columns 2 and 3 list the corresponding values for agecats, including 20 to 29, 30 to 39, and 40 to 49, and total, respectively.

Although the numbers in each category are small, we might note that the males tended to be younger than the females. While there were similar percentages in the 30–9 age range, there were differences in the younger and older age categories: 36 per cent of males were in their 20s compared to only 12.5 per cent of females; 44 per cent of females were in their 40s compared to only 14 per cent of males.

Transforming data like age into categories can sometimes provide interesting information that would not be otherwise apparent. For example, a simple comparison of the mean age of male and female patients reveals that the mean age of males was 31 years and the mean age of females was 39 years. But all this tells us is that, on average, females were older. By transforming age into categories and cross-tabulating with sex we can actually see where these differences lie in terms of specific age groups.

73 Page 73 

There is just one more thing to note: because we have created three categories of age the numbers are even fewer in the six cells. Many students go on to report the chi-square statistic for this analysis. However, the numbers really are too small to produce a reliable chi-square, as you would see from the chi-square tests table, which cautions that ‘4 cells (67%) have expected count less than 5’. In such cases we can only report the cross-tabulation percentages showing this trend, and perhaps recommend a larger sample for statistical analysis.

## 4.6Summary

In this chapter you have learnt about:

*   How to cross-tabulate categorical data in SPSS.

*   How to produce the chi-square statistical test.

*   The concept of statistical significance, levels of significance, Type I (false positive) and Type II errors (false-negative) errors, and issues relating to power and ‘effect size’.

*   How to re-code interval variables into categorical variables.

## 4.7Exercises

### Exercise 4.1 Re-code counselling sessions into categories

Re-code the data for number of counselling sessions into three equal groups representing ‘low’, ‘medium’ and ‘high’ attendance and first cross-tabulate with ‘counsellor’ then with ‘sex’. What do these cross-tabulations show?

### Exercise 4.2 Re-code satisfaction ratings into categories
