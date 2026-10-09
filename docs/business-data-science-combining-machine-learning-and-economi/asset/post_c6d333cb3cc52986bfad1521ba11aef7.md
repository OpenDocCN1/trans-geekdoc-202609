
*For Kirsty, Amelia, and Charlie.*

## CONTENTS

- Preface
- Introduction
- 1 Uncertainty
- 2 Regression
- 3 Regularization
- 4 Classification
- 5 Experiments
- 6 Controls
- 7 Factorization
- 8 Text as Data
- 9 Nonparametrics
- 10 Artificial Intelligence
- Bibliography
- Index

## PREFACE

### WHAT IS THIS BOOK ABOUT?

Over the past decade, business analysis has been disrupted by a new way of doing things. Spreadsheet models and pivot tables are being replaced by code scripts in languages like R, Scala, and Python. Tasks that previously required armies of business analysts are being automated by applied scientists and software development engineers. The promise of this modern brand of business analysis is that corporate leaders are able to go deep into every detail of their operations and customer behavior. They can use tools from machine learning to not only track what has happened but predict the future for their businesses.

This revolution has been driven by the rise of big data—specifically, the massive growth of digitized information tracked in the Internet age and the development of engineering systems that facilitate the storage and analysis of this data. There has also been an intellectual convergence across fields—machine learning and computer science, modern computational and Bayesian statistics, and data-driven social sciences and economics—that has raised the breadth and quality of applied analysis everywhere. The machine learners have taught us how to automate and scale, the economists bring tools for causal and structural modeling, and the statisticians make sure that everyone remembers to keep track of uncertainty.

The term data science has been adopted to label this constantly changing, vaguely defined, cross-disciplinary field. Like many new fields, data science went through an over-hyped period where crowds of people rebranded themselves as data scientists. The term has been used to refer to anything remotely related to data. Indeed, I was hesitant to use the term data science in this book because it has been used so inconsistently. However, in the domain of professional business analysis, we have now seen enough of what works and what doesn’t for data science to have real meaning as a modern, scientific, scalable approach to data analysis. Business data science is the new standard for data analysis at the world's leading firms and business schools.

This book is a primer for those who want to gain the skills to operate as a data scientist at a sophisticated data-driven firm. They will be able identify the variables important for business policy, run an experiment to measure these variables, and mine social media for information about public response to policy changes. They can connect small changes in a recommender system to changes in customer experience and use this information to estimate a demand curve. They will need to do all of these things, scale it to company-wide data, and explain precisely how uncertain they are about their conclusions.

These super-analysts will use tools from statistics, economics, and machine learning to achieve their goals. They will need to adopt the workflow of a data engineer, organizing end-to-end analyses that pull and aggregate the needed data and scripting routines that can be automatically repeated as new data arrives. And they will need to do all of this with an awareness of what they are measuring and how it is relevant to business decision-making. This is not a book about *one of* machine learning, economics, or statistics, nor is it a survey of data science as a whole. Rather, this book pulls from all of these fields to build a toolset for business data science.

This brand of data science is tightly integrated into the process of business decision-making. Early “predictive analytics” (a precursor to business data science) tended to overemphasize showy demonstrations of machine learning that were removed from the inputs needed to make business decisions. Detecting patterns in past data can be useful—we will cover a number of pattern recognition topics—but the necessary analysis for deeper business problems is about *why* things happen rather than *what* has happened. For this reason, we will spend the time to move beyond correlation to causal analysis. This book is closer to economics than to the mainstream of data science, which should help you have a bigger practical impact through your work.

We can't cover everything here. This is not an encyclopedia of data analysis. Indeed, for continuing study, there are a number of excellent books covering different areas of contemporary machine learning and data science. 1 Instead, this is a highly curated introduction to what I see as the key elements of business data science. I want you to leave with a set of best practices that make you confident in what to trust, how to use it, and how to learn more.

I've been working in this area for more than a decade, including as a professor teaching regression (then data mining and then big data) to MBA students, as a researcher working to bring machine learning to social science, and as a consultant and employee at some big and exciting tech firms. Over that time I've observed the growth of a class of generalists who can understand business problems and also dive into the (big) data and run their own analyses. These people are kicking ass, and every company on Earth needs more of them. This book is my attempt to help grow more of these sorts of people.

The target audience for this book includes science, business, and engineering professionals looking to skill up in data science. Since this is a completely new field, few people come out of college with a data science degree. Instead, they learn math, programming, and business from other domains and then need a pathway to enter data science. My initial experience teaching data science was with MBA students at The University of Chicago Booth School of Business. We were successful in finding ways to equip business students with the technical tools necessary to go deep on big data. However, I have since discovered an even larger pool of future business data scientists among the legions of tech workers who want to apply their skills to impactful business problems. Many of these people are scientists: computer scientists, but also biologists, physicists, meteorologists, and economists. As machine learning matures into an engineering discipline, many more are software development engineers.

I've tried for a presentation that is accessible to quantitative people from all of these backgrounds, so long as they have a good foundation in basic math and a minimal amount of computer programming experience. Teaching MBAs and career switchers at Chicago has taught me that nonspecialists can become very capable data scientists. They just need to have the material presented properly. First, concepts need to be stripped down and unified. The relevant data science literature is confused and dispersed across academic papers, conference proceedings, technical manuals, and blogs. To the newcomer it appears completely disjointed, especially since the people writing this material are incentivized to make every contribution seem “completely novel.” But there are simple reasons why good tools work. There are only a few robust recipes for successful data analysis. For example, make sure your models predict well on new data, not the data you used to fit the models. In this book, we'll try to identify these best practices, describing them in clear terms and reinforcing them for every new method or application.

The other key is to make the material concrete, presenting everything through application and analogy. As much as possible, the theory and ideas need to be intuitional in terms of real experience. For example, the crucial idea of “regularization” is to build algorithms that favor simple models and add complexity only in response to strong data signals. We'll introduce this by
