
# Reproducible research

> The most important tool is the mindset, when starting, that the end product will be reproducible. – Keith Baggerly

Another goal of this book is to help readers understand the importance of reproducible analyses. The hope is to get readers into the habit of making their analyses reproducible from the very beginning. This means we'll be trying to help you build new habits. This will take practice and be difficult at times. You'll see why it is so important for you to keep track of your code and document it well to help yourself later and any potential collaborators as well.

Copying and pasting results from one program into a word processor is not an ideal way to conduct efficient and effective scientific research. It's much more important for time to be spent on data collection and data analysis and not on copying and pasting blocks back and forth across a variety of programs.

In traditional analyses, if an error was made with the original data, we'd need to step through the entire process again: recreate the plots and copy-and-paste all of the new plots and our statistical analysis into our document. This is error prone and a frustrating use of time. We want to help you get away from this tedious activity so that we can spend more time doing science.

> We are talking about computational reproducibility. – Yihui Xie

Reproducibility means a lot of things in different scientific fields. Are experiments conducted in a way that another researcher could follow the steps and get similar results? In this book, we will focus on what is known as computational reproducibility. This refers to being able to pass all of one's data analysis, datasets, and conclusions to someone else and have them get exactly the same results on their machine. This allows for time to be spent interpreting results and considering assumptions instead of the more error prone way of starting from scratch or following a list of steps that may be different machine to machine.

# Final note for students

At this point, if you are interested in instructor perspectives on this book, ways to contribute and collaborate, or the technical details of this book's construction and publishing, then continue with the rest of the chapter. Otherwise, let’s get started with R and RStudio in Chapter 1!

# Introduction for instructors

# Resources

Here are some resources to help you use ModernDive checks. You can find all

- 1. We've included review questions posed as Learning checks in the Appendices of the online version of the book. The solutions to all Learning checks. The Appendices start at https://moderndive.com/v2/appendix.
- 2. Dr. Jenny Smelter and Albert Y. Kim have written a series of labs and problem sets. You can find them at https://moderndive.com/labs.
- 3. You can see the webpages for two courses that use ModernDive:
   - Smith College "SDS192 Introduction to Data Science": https://rudoberyt.github.io/SDS192/
   - Smith College "SDS220 Introduction to Probability and Statistics": https://rudeboybert.github.io/SDS220/

# Why did we write this book?

This book is inspired by:

- Mathematical Statistics with Resampling and R (Chihara and Hesterberg, 2011)
- OpenIntro: Intro Stat with Randomization and Simulation (Diez et al., 2014)
- R for Data Science (Grolemund and Wickham, 2017)

The first book, designed for upper-level undergraduates and graduate students, provides an excellent resource on how to use resampling to impart statistical concepts like sampling distributions using computation instead of large-scale approximations and other mathematical formulas. The last two books are free options for learning about introductory statistics and data science, providing an alternative to the traditionally expensive introductory statistics textbooks.

When looking over the introductory statistics textbooks that currently exist, we found there wasn't one that incorporated newly developed R packages directly into the text, in particular the many packages included in the tidyverse⁷ of packages,

> ⁷http://tidyverse.org/

such as ggplot, dplyr, tidyr, and readr that will be the focus of this book's first part on “Data Science with tidyverse.”

Additionally, there wasn't an open-source and easily reproducible textbook available that exposed new learners to all four of the learning goals we listed in the “Introduction for students” subsection. We wanted to write a book that could develop theory via computational techniques and help master the R language in doing.

# Who is this book for?

This book is intended for instructors of traditional introductory statistics classes using RStudio, who would like to inject more data science topics into their syllabus. RStudio can be used in either the server version or the desktop version. (This is discussed further in Section 1.1.1.) We assume that students taking the class will have no prior algebra, calculus, or programming/coding experience.

Here are some principles and beliefs we keep in mind while writing this text. If you agree with them, this is the book for you.

- 1. Blur the lines between lecture and lab
  - With increased availability and accessibility of laptops and open-source, non-proprietary statistical software, the strict dichotomy between lecture and lab can be loosened.
  - It’s much harder for students to understand the importance of using software if they only use it once a week or less. They forget the syntax in the same way someone learning a foreign language forgets the grammar rules. Frequent reinforcement is key.

- 2. Focus on the entire data/science research pipeline
  - We believe the entirety of Grolemund and Wickham’s data science⁸ as seen in Figure 2 should be taught.
  - We heed George’s call to “minimize prerequisites for students should be answering questions with data as soon as possible.”

- 3. It’s all about the data
  - We leverage R for rich, realistic datasets that are easy-to-load for novices, and hence much more datasets can be explored.
  - We believe that data visualization is a “gateway for statistics.” However, we often hear: “You can’t teach ggplot in stats!”

> ⁸https://r4ds.had.nz/introduction.html

> ⁹https://arxiv.org/abs/1507.05346

> ¹⁰https://scholarship.org/uc/item/84v3

David Robinson¹¹ much more optimistic and found our students have been largely successful in learning it.

- dplyr has made data wrangling much more accessible¹² to novices.

- Use simulation/resampling to introduce statistical inference, not probability/mathematical formulas
- Instead of using formulas, large-sample approximations and probability, we teach statistical concepts using simulation-based inference.

The best textbook is the one you've written yourself. You know your audience, their background, and their priorities. You know your own style and the types of examples and problems you like best. Customization is the ultimate end. We encourage you to take what we've provided and make it work for your own needs. For more about how to make this book your own, see “About this book” later in this Preface.

> ¹http://varianceexplained.org/r/teach_ggplot2_to_beginners/

> ¹²https://chance.amstat.org/2015/04/setting-the-stage/
