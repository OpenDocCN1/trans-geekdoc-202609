# CHAPTER 5 FIGURING STUFF OUT: DATA ANALYSIS

If the project will involve any modeling, you'll also need to do feature engineering, where new features are created based on existing data source(s) in order to improve modeling or analysis. Knowing what to create usually relies on what's discovered in the next step, there is some back-and-forth with these two, as well. Feature engineering is almost necessary in data science, even when we have clean data from a data engineering team, but it's not as often in data analysis. Determining what features are needed is its own process and is based on both how the data looks and what techniques they're going to be used in.

It's worth mentioning that there can be a lot of back-and-forth between this step and the next, exploratory analysis and modeling, because you may find things in the next step that require you to do additional data prep or change some of what's been done.

In our football example, some of the data prep might be creating a new table with all of the basic stats with player names and replacing null values with 0 based on stakeholders confirming that is the right business logic. You would also make sure to save all the numeric fields as numeric data types. You may still be wondering about the possibility of deriving sacks from the two data sources. You likely wouldn't have enough knowledge to do that yet and will rely on what you find in the next step to determine if it's possible and necessary.

# Exploratory Analysis and Modeling

After you've got the data ready, it's time to start doing what you've been wanting to do the whole time: dig into the data. Exploratory analysis and modeling is often another big step. How big depends on how deep you go. But as mentioned, you will probably be going back to the data preparation step a few times after finding problems or little gotchas with the data that you missed when you did the cursory investigation in that step. In other