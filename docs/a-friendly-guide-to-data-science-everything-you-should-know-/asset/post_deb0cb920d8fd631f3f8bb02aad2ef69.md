
# CHAPTER 11 TOOLS OF THE TRADE: PYTHON AND R

Data frames are convenient because they allow us to do operations across rows and columns, and even the whole data frame, with single commands. Adding new columns and rows is easy. Grouping data and aggregations can be done in one step. For instance, adding a column Age based on the birth and death dates in the other columns can be done in a single line in both Python and R. In Python it would look something like this:

```
pets_df["Age"] = pets_df["Date_died"] - pets_df["Birth_date"]
```

There would be a little more involved depending on data types and what unit you wanted your Age column in, but this is all you have to do conceptually. It knows to the whole column and subtracts the other column with rows lined up and then adds it to the data frame as a new column at the end. This is much easier than the way it used to be when you worked with tabular data (this was usually going row by row in a loop and doing the computation on each loop, which takes a lot more time than using data frame operations).

Data scientists love data frames for working with lots of tabular data, but the other reasons they love Python and R so much are the statistics, visualization, and machine learning packages that are available in both languages. Table 11-12 shows some of the many packages data scientists use in Python and R. Some are built-in, but most will need to be installed (fortunately this is easy to do). It's beyond the scope of this book to talk about using these packages specifically, but we will talk about machine learning in a later chapter.

# Table 11-12. Data science packages used by data scientists. ML stands for machine learning and NLP for natural language processing

| Python Package | Use | R Package | Use |
| --- | --- | --- | --- |
| pandas | Data frame | data.table | More data frame manipulation |
| numpy | Numeric data manipulation | dplyr | Data manipulation |
| scipy | Builds on numpy | lubridate | Date manipulation |
| datetime | Date manipulation | ggplot2 | Visualization |
| plotly | Visualization | stats | Statistics |
| matplotlib | Visualization | e1071 | ML modeling |
| seaborn | Visualization | xgboost | ML modeling |
| statsmodels | Statistics | randomForest | ML modeling |
| scikit-learn | ML modeling and performance | tensorflow | ML modeling |
| tensorflow | ML modeling | naivebayes | ML modeling |
| torch | ML modeling | metrics | ML performance |
| nltk | NLP modeling | tidymmodels | ML support |
| spacy | NLP modeling | shiny | Presentation |

If you are coding in a cloud platform, you may have other packages that can give you big performance boosts. For instance, if you have access to Spark, you would use Spark data frames instead of Pandas, which would require using different machine learning libraries. Sometimes there are also platform-specific packages that are available. These can be very useful, but sometimes difficult when you're transitioning from one platform to another.

# CHAPTER 11 TOOLS OF THE TRADE: PYTHON AND R

One thing that's somewhat unique to data science programming is the use of notebooks, or systems that allow you to run individual lines of code rather than an entire file. In the old days, you'd have all your code in one file, and to run it, you'd run the entire file. All the steps would have to be run each time between runs, you lose everything that was created during the last run. Notebooks function differently and allow you to run one cell at a time and maintain the variables and other objects you've created. This is a great innovation, especially in data science, because when you're working with large amounts of data, you don't want to repeat time-consuming steps, like transforming a given dataset. A couple other advantages of these notebook-style options are that you can format notebooks for easy presentation and notebooks are also fantastic for sharing with colleagues.

# Conventions and Habits

There are many conventions, standards, and best practices in programming, especially in software engineering. But a lot of data scientists don't learn these because they're learning with smaller pieces of code, working on solving a specific problem. This leads to overall messy code that is especially hard to reuse, a problem that compounds on teams with multiple people writing messy code. It's highly recommended that you try to follow good practices once you've learned them, they're instinctive and you don't have to think about it to write good code.

I talked a little about commenting above. This is definitely one area where developing good habits is worthwhile. Your future coworkers will appreciate you and possibly pick up the habit from you. But even more important is the fact that you will appreciate yourself. It's incredibly common to write code and later not remember how it works or why you wrote it that way. A few comments can go a long way.

# CHAPTER 11 TOOLS OF THE TRADE: PYTHON AND R

Most languages have published standards and best practices, Python and R are no exception. Python’s primary style guide is referred to as PEP 8, with a secondary PEP 257, both of which are over 20 years old and still followed. There are also ways to format your code automatically through packages or coding platforms. R doesn't have such a high-level style guide, and Google published one that a lot of people use. It's relatively short. A lot of new programmers think style is that important, and it's true that you don't need to follow it to learn, but it's really good to develop the habit early on. Style guides exist to make code more maintainable (as in possible to read and understand later). Follow them consciously for a while, and once you've internalized them in no time, so writing clear and highly readable code is second nature.

One thing you will encounter in the programming world is how to name variables and table columns. The style guides address this, but in general, variable names cannot include a space or begin with a digit, and column names may technically allow both, you should stick with convention and avoid them. There's a bit of a war about capitalizing and separating words in a multi-word variable name. Historically, it was common to use camelCase (all but the first word are capitalized), which is often confused with ProperCase (all words are capitalized), but a more recent entrant's gaining steam in Python is called under_case (nothing or everything is separated by an underscore). It's fairly conventional to use under case in Python for functions and variables, but ProperCase for classes. In R, the period is usually used instead of the underscore even though underscores are allowed.

4 "PEP 8—Style Guide for Python Code" available at https://peps.python.org/pep0008/
5 "PEP 257—Docstring Conventions" available at https://peps.python.org/pep0257/
6 "Google’s R Style Guide" available at https://web.stanford.edu/class/cs1091/unrestricted/resources/google-style.html

There are many other conventions that can be followed, depending on the language and team preferences. In some languages it's common to start of all your variables with a single letter v, or with var, and sometimes to include the data type in the variable name. You can have your opinions on all of this, but you will generally go with the style of whatever team you land on.

Following all these rules can be a drag at first, but it pays off in producing code that is easier to read—even if someone else wrote it or it's months after you wrote it. Many data science teams will have their own standards, and you'll need to adapt to and follow it, but if you land on a team without these, you're still better off having your own standards.

# Picking Your Language(s)

If you are trying to decide which language to learn, there are many things that can influence your decision. If you're in a degree program, they probably have a language they use throughout. Obviously learning that you already have some experience in one, it makes sense to stick with that. If you're studying on your own, you can try both out and see which you like better. If you expect to work mostly on the statistics side and probably won't be needing to deploy machine learning models, R might be the right choice. It is slightly stronger in pure statistics than Python. For the same reason, it might also be a good choice if you really want to learn statistics deeply. If you want to be competitive for jobs that might involve developing in other languages, definitely pick Python. Python shares more in common with other popular languages like Java and C than R does. In general, Python's more popular in industry and R in academia. Finally, if you have no idea which to pick and nothing points you to one or the other, I'd recommend picking Python. It's starting to edge out R in popularity, and it's easier to go from Python to other programming
