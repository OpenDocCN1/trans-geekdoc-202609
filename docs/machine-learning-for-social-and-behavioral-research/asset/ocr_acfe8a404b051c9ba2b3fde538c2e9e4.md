# Machine Learning for Social and Behavioral Research

For example, for a female professor, one might misspell "she" as "he" in the comments. But "his" is hard to be misspelled as "her." Similarly for "mr" and "mrs", they might not be as reliable as "him" or "her." Therefore, we can assign different weights to the words. For example, for the male gender words, we give a weight of 2 to "him" and "his," and a weight of 1 to "he" and "mr." Then, a weighted gender index can be created.

In this chapter, we simply count the total number of gender words. The number of male gender words and female gender words for a sample of 10 professors is shown in Table 11.4. For some professors, the number of either male gender words or female gender words is 0. In this case, we can label the professor as either a female or a male professor. For example, we can be very confident that Professors 1, 2, 4, and 78 are male professors and Professors 27 and 79 are female professors. For the other four professors in the table, there are both male and female gender words in the comments. However, we can see that the difference in the number of male gender words and female gender words is quite large for all four professors. In this case, we might assume the small number of gender words were misspelled and label the professors based on the larger number of gender words. For example, we can label Professors 3 and 80 as male professors Professors 79 and 84 as female professors.

# TABLE 11.4. Gender Index for a Sample of Professors

| ID | Male Gender Words | Female Gender Words | Gender |
|---|---|---|--|
| 1 | 153 | 0 | M |
| 2 | 152 | 0 | M |
| 3 | 249 | 2 | M |
| 4 | 29 | 118 | F |
| 27 | 0 | 80 | F |
| 78 | 105 | 0 | M |
| 79 | 206 | 2 | M |
| 84 | 1 | 181 | F |

For this dataset, 27.8%(278/999) of professors have both male gender words and female gender words. We plot the number of male and female gender words in Figure 11.5. For the majority of the professors, a clear division exists between the number of male gender words and the number of gender words. Therefore, we can confidently label the professors as male or female based on the larger number of either male or female gender words.

Based on the above classification, there are 415 or 42% female professors and 584 or 58% male professors in the dataset. With this information,