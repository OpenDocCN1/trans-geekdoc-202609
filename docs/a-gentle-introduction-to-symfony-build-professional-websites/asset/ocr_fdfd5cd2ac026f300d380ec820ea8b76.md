# SQL queries

+   1. [1.00 ms] SELECT COUNT(ask_question.ID) FROM ask_question, ask_interest WHERE
+   ask_interest.CREATED_AT>'2006-11-24 10:47:17' AND ask_interest.QUESTION_ID=ask_question.ID
+   
+   2. [3.53 ms] SELECT ask_question.ID, ask_question.AT, ask_question.USER_ID, ask_question.TITLE,
+   ask_question.BODY, ask_question.HTML_BODY, ask_question.INTERESTED_USERS, ask_question.REPORTS,
+   ask_question.CREATED_AT, ask_question.UPDATED_AT, ask_user.ID, ask_user.NICKNAME,
+   ask_user.FIRST_NAME, ask_user.LAST_NAME, ask_user.EMAIL, ask_user.SHA1_PASSWORD, ask_user.SALT,
+   ask_user.IS_ACTIVE, ask_user.IS_ADMIN, ask_user.MODERATOR, ask_user.LAST_LOGIN,
+   ask_user.IS_ADMINISTRATOR, ask_user.DELETIONS, ask_user.CREATED_AT AS
+   count FROM ask_question, ask_user WHERE ask_question.CREATED_AT>'2006-11-24 10:47:17' AND
+   ask_interest.QUESTION_ID=ask_question.ID AND ask_question.USER_ID=ask_user.ID GROUP BY
+   ask_question.QUESTION_ID ORDER BY COUNT DESC, ask_question.CREATED_AT DESC LIMIT 10
+   
+   3. [0.49 ms] SELECT ask_answer.ID, ask_answer.QUESTION_ID, ask_answer.USER_ID, ask_answer.BODY,
+   ask_answer.HTML_BODY, ask_answer.RELEVANCY_UP, ask_answer.RELEVANCY_DOWN,
+   ask_answer.REPORTS, ask_answer.CREATED_AT FROM ask_answer WHERE ask_question.ID=1
+   
+   4. [0.45 ms] SELECT DISTINCT ask_question.TAG_QUESTION_ID, ask_question.TAG_USER_ID,
+   ask_question.TAG_CREATED_AT, ask_question.TAG, ask_question.TAG_NORMALIZED_TAG,
+   ask_question.TAG_NORMALIZED_TAG FROM ask_question WHERE
+   ask_question.TAG_QUESTION_ID=1 GROUP BY ask_question.TAG_NORMALIZED_TAG ORDER BY
+   UPPER(ask_question.TAG_NORMALIZED_TAG) ASC
+   
+   5. [0.33 ms] SELECT ask_question.TAG_NORMALIZED_TAG AS tag, COUNT(ask_question.TAG_NORMALIZED_TAG) AS
+   count FROM ask_question WHERE ask_question.TAG_QUESTION_ID=1 GROUP BY
+   ask_question.TAG_NORMALIZED_TAG ORDER BY COUNT DESC LIMIT 5
+   
+   6. [0.43 ms] SELECT ask_answer.ID, ask_answer.QUESTION_ID, ask_answer.USER_ID, ask_answer.BODY,
+   ask_answer.HTML_BODY, ask_answer.RELEVANCY_UP, ask_answer.RELEVANCY_DOWN,
+   ask_answer.REPORTS, ask_answer.CREATED_AT FROM ask_answer WHERE ask_question.ID=2

Figure 16-6 - The clock icon shows execution time by category

# Timers

| type | calls | time (ms) |
|---|---|---|
| Configuration | 14 | 60.42 |
| Action "question/frontpage" | 1 | 132.43 |
| Database | 9 | 7.56 |
| View "Success" for "question/frontpage" | 1 | 243.24 |
| Partial "question/_question_list" | 1 | 151.49 |
| Partial "question/_question_block" | 2 | 119.74 |
| Partial "question/_interested_user" | 2 | 12.99 |
| Partial "moderator/_question_options" | 2 | 2.80 |
| Component "sidebar/default" | 1 | 0.02 |
| Partial "sidebar_default" | 1 | 25.62 |
| Partial "tag/_tag_cloud" | 1 | 2.09 |
| Partial "question/_search" | 1 | 0.97 |
| Partial "sidebar/_rss_links" | 1 | 3.08 |
| Partial "sidebar/_moderation" | 1 | 1.32 |
| Partial "sidebar/_administration" | 1 | 1.85 |