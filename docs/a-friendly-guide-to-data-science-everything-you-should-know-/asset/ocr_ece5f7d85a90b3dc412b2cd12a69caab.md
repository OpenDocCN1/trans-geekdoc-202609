# CHAPTER 3 SETTING UP FOR SUCCESS: THE INFERENTIAL STATISTICS FRAMEWORK AND EXPERIMENTS

# # Experiment and Study Design

Most of us have participated in a quick survey online, and while they can be fun, they are almost never actually meaningful because they're full of bias and poorly framed questions. It turns out that creating a rigorous experiment or study isn't a trivial thing, and there has been a great deal of work done in this area over the last 200 years to make it better.

Even if a data scientist doesn't directly design or run experiments, understanding how they are designed and run can be very beneficial to understanding the data and knowing how to work with it.

# # Experiments

Experiments are a staple in the physical sciences, with social scientists—especially psychologists—joining the fun. This is when done well, they produce reliable and rigorous data that can be used to draw real, meaningful conclusions.

To be an experiment in the scientific sense, it needs to be testing a single variable while controlling for all others. There need to be two groups at a minimum, a *control group* that has no change and an *experimental group* that encapsulates the change. There can be multiple experimental groups, but they should be different in the same variable. Study objects (whether human participants or something else) must be assigned randomly to one of these groups. There must also be at least one *response variable*, which is what the experiment is trying to measure—did the experimental groups respond differently from the control group?

There are other things that must be considered, including sample size, how many response variables will there be, what type of statistical techniques will be used to analyze the data, and what level of significance will be used as a threshold for statistical significance. These things are all intertwined in order to ensure that differences that appear significant are truly statistically significant. There are several methods that you can use to