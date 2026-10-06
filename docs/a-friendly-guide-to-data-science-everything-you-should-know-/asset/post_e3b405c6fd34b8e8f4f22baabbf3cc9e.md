
Although SAS is still around in some companies, the name of the game is R or Python, depending on your opinion. Unless you end up with a job that uses SAS, there’s no reason to learn anything besides R or Python at the beginning. Both are perfectly legitimate languages for data science, both to learn and to develop. They have different strengths, which might dictate which you would choose for a specific purpose, and most data scientists are pretty opinionated about which one they prefer. It’s also common for teams to use one predominantly. On the other hand, there’s no reason to not use both—plenty of teams do this, We’ll talk more about how they’re different and similar in the next sections. R is particularly good for statistics, and it’s popular for visualization in academia, while Python is good for machine learning and general programming, including building production systems.

## Examples of Python and R in Data Science in the Real World

Our first example is a good example of how you don’t have to choose between R and Python and can instead use them where their strengths lie. Then we’ll look at how Python is used in the financial tech world.

## Example 1: Hedging by Using Both

The hedge fund company Amadeus Investment Partners found success using a tech stack (the technical tools a team uses to get their work done) that includes both Python and R, plus SQL and other tools. They have

> “Case Study: How To Build a High Performance Data Science Team” by Matt Dancho and Rafael Nicolas Fermin Cota on Business Science, available at https://www.business-science.io/business/2018/09/18/data-science-team.html

## CHAPTER 11 TOOLS OF THE TRADE: PYTHON AND R

several different roles on their interdisciplinary team, and each role has specific tools it uses. They have technical SMEs who use R, Excel, and some other tools to explore the data. Their data engineers also use R, along with SQL and C++ (an older traditional programming language that's good for performance). Their data scientists use R for EDA and Python for machine learning and deep learning in particular. They also have user interface developers who use both R and Python, along with other tools.

For Amadeus, they prefer R for most data analysis tasks, including exploring the data and visualization. There are some great packages in R for these tasks. But Python excels in the more computationally intensive tasks like machine learning, especially when they're working with the larger datasets that the company uses. It's also interesting that they seem to dictate exactly which tools people should use. A lot of companies allow disparate codebase that can be hard to maintain and reuse. By requiring data scientists to choose their tools, which they like, but it does lead to a data scientists to do their EDA in R, any future work can more easily build on earlier work.

One other point about this company's interesting is that they do something quite unusual in data science: they hire top graduates from business schools and train them to be data scientists, rather than starting with people with technical backgrounds. They find that these graduates are able to pick up both Python and R reasonably quickly, which complements their more general soft skills and business knowledge from their degrees. This speaks to the relative ease of learning these two languages.

## Example 2: Fast and Flexible FinTech

djangostars, a financial technology (FinTech) consultancy and custom software developer, prefers Python in all of its work.³ They have many reasons why they find Python the best language for FinTech, especially for newer companies. One is that it's already preferred among mathematicians and economists, so any work that needs to be put into a system from them is already halfway ready, before “real coding” is getting started. While a lot of FinTech involves data science, there's much more to it that, and Python's great as a multipurpose language. They saying Python combined with Django (a well-established Python-based framework) is a great combination for getting products to market quickly. Additionally, that suite of tools is very flexible and easy to make changes, to something, that's important in FinTech (as opposed to traditional banking). They also found that because Python is relatively easy to learn, it makes collaboration and knowledge transfer to clients smoother because it's so easy for developers and data scientists to explain. Python's very well established, and there are free packages that do almost any imaginable thing.

## The Basics of Computer Programming

Programming languages really are like human languages, just, much simpler. I had a professor who got a computer science degree in the 1980s and convinced his college to count Pascal (another traditional programming language) as his foreign language requirement. That wouldn't happen today, but like human language, programming languages have syntax (the particular words, operators, and the order're written)

> ³“Using Python for FinTech Projects: All You Should Know” by Artur Bachynsky, October 28, 2024, https://djangostars.com/blog/python-for-fintech-projects/

## CHAPTER 11 TOOLS OF THE TRADE: PYTHON AND R

semantics (the meaning made by the specific text written following syntax rules). They also have idioms that develop over time, which are ways of accomplishing specific things that are conventional among programmers even it's not the only way it can be written. A few languages also have fairly strict formatting rules that dictate state—Python is, and Pythonistas fervently believe it's the only way to write nice-looking code.

Computer code is basically a recipe written with the specific syntax of the particular programming language. Almost all programming languages use English words, and there are several words and operators that are used across most languages. Some of the most common operators include those in Table 11-1. These are mostly familiar items we know from basic math. They're largely used the same way in code. I'll talk a bit more these below, and as well.

## Table 11-1. Common operators in many languages, including R and Python

| Assignments and Control | Comparators | Mathematical Operators |
| :--- | :--- | :--- |
| = | > | + |
| | < | - |
| >= | | / |
| <= | | * |
| == | | ^ |
| != | | % |

Some common keywords are in Figure 11-1. Keywords are words that always have a specific meaning in a language and can't (or shouldn't) be used anywhere in the code except in the defined way. All the keywords in Figure 11-1 are used to control the flow of programs, which we'll talk about below.

```
for
while
if
else
break
function
def
return
raise
```
Figure 11-1

Once you know the basics of syntax, you're on your way to learning how to do anything in code. Programming is very systematic, but once you get into it, you'll see how creativity factors in finding good ways to solve problems.

There are a few different high-level ways to go about programming, called paradigms. The ones we will focus on here are procedural and functional, but another common one you'll hear about object-oriented programming, which focuses on a certain type of modular design and can be done in both Python and R (it's easy in Python but a little trickier in R), although a lot of data scientists may never use it. Procedural programming involves a sequence of steps one after another. Functional programming involves the use of functions, which we'll define more further down, but basically having smaller units of code that can be defined and called repeatedly with different or no values for effective use.

Note that this chapter is talking about code, but you're not expected to learn to write code in this chapter. There are some examples of Python and R code in the sections, but they're simply to illustrate ideas and show the differences between the two languages. However, if you are a hands-on learner, there's nothing wrong with getting in a Python or R interpreter and trying things out. It's a great way to learn. Appendix A details how to install them and get started.
