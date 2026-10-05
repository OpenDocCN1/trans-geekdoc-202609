# 15
Clustering with K-Means

We don't always have the luxury of labeled data for supervised learning. A more common case is that a dataset {x_i}_{i=1}^n is not labeled, but we want to identify substructure as groupings. Clustering techniques are also helpful in finding outliers; such points may be located in isolated or small groups. We will begin this chapter by studying concepts to clustering. Then we will learn about k-means clustering and work out a small example. Lastly, we will apply k-means to a nutrition dataset of roughly 9000 foods.

# 15.1 Clustering Concepts

Let's start with a very small example to illustrate the ideas. Suppose that a teacher wishes to group her students by some measure of assessment performance. The assessments may consist of quizzes or exams, for example. After the students are grouped, they can be given more targeted instruction. What is the best way to implement this grouping? We face some questions to be answered early on, including:

+   * Which students should be used in the grouping calculations? We might include in the analysis all current students in a specific class, or we use both current and historical students from a course.
* Which variables should be included? We might include one assessment at a time, all assessments given in a particular course, or only the assessments given before the final exam. For example, if we use a system that identifies students needing support on recent learning, then the clustering could be based on the last exam.
* How do we measure the quality of the groups? To understand the quality of the groups, we might try to correlate the groupings with another variable. It is also important to bear in mind that there is a limit to the number of groups that can be supported by the teacher and teaching assistants.