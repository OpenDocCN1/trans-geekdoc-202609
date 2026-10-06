# Introduction to Text Mining

that you can learn it on your own. I definitely recommend taking him for whatever math courses you can. He requires a lot of work, but it pays off in the run!

First, we can identify the sentiment words in the comment. Using different lexicons, we can get different words, as shown in Table 11.9. For example, using the lexicon AFINN, five words are selected with "help" appearing twice. The lexicon syuzhet identified nine words. For four lexicons, only positive words are found in the comment.

# TABLE 11.9. The Sentiment Words in the Example Comment in the Above Listing

| AFINN | Score | nr | Score | bing | Score | syuzhet | Score |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| favorite | 2 | favorite | 1 | favorite | 1 | favorite | 0.75 |
| helpful | 2 | professor | 1 | helpful | 1 | professor | 0.4 |
| best | 3 | guide | 1 | willing | 1 | best | 0.7 |
| help | 2 | learn | 1 | recommend | 1 | best | 0.5 |
| recommend | 2 | recommend | 1 | work | 1 | guide | 0.6 |
| | | | | | | learn | 0.8 |
| | | | | | | work | 0.25 |

If we are interested in the overall sentiment of the comment, we can then add the score for each word. For example, using the bing lexicon, the sentiment score for the comment is 6 and using the syuzhet lexicon, the sentiment score is 5.35. The comment includes five sentences, if splitting based on the period. Then the sentiment of each sentence can be similarly evaluated. If we use the syuzhet lexicon, the sentiment of each sentence is 1.15, 2.05, 1.40, 0.50, and 0.25, respectively. Note that although lexicons pointed to a positive sentiment of the example comment, the magnitude of the sentiment cannot be determined simply by the score without defining a norm first.

# 11.7.1 Sentiment Analysis of Teaching Evaluation Text Data

The evaluation dataset includes 27,939 comments from terms of their teaching. For each comment, we can calculate its overall sentiment as illustrated earlier. Figure 11.16 shows the histogram of the sentiment scores of the 27,939 comments based on the bing lexicon. The average sentiment score is 1.68 with a standard deviation of 2.37. If it means a neutral comment, the comments are positive.