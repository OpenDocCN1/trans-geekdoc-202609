# CHAPTER 6 BRINGING IT INTO THE TWENTY-FIRST CENTURY: DATA SCIENCE

are the most impactful. Figure 6-4 shows an example of a formula that represents a linear regression model that predicts rating in the video game data based on the other numeric features on the table.

```
Rating = 3.44 + 0.52 * ('Number of Ratings')
+ -0.32 * ('Plays')
+ -0.18 * ('Playing')
+ 0.36 * ('Backlogs')
+ 0.86 * ('Wishlist')
```

Figure 6-4. A linear regression formula for predicting rating from several features

This formula is interesting—Wishlist is the most important, even more than Number of Ratings. Plays and Playing both reduce the score, which seems counterintuitive, but Backlogs is more important than either or may counteract them. Models can sometimes have surprising values. It's also possible this just isn't a very accurate model.

Another explainable model is the decision tree, where each decision point can be visually represented, so a path can be followed. At the highest level, the decision tree approach basically splits the data into two sides by identifying the most effective split (where one side matches mostly one label or better than other splits) and repeats the process for each result until it reaches a result that is all or mostly one label (or a max depth is reached). An example of this would be: take the right branch if Number of Plays is greater than 100; otherwise, take the left. If of the data greater than a hundred has a rating of 4 or greater, and most of the data less than 100 has mostly ratings less than 4, this would be a good split. Figure 6-5 shows a very simple tree on the same video game data, also predicting rating.