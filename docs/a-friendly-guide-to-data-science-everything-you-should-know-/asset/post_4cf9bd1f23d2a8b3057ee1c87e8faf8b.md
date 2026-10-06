
## CHAPTER 21 PUTTING IT ALL TOGETHER: DATA SCIENCE SOLUTION MANAGEMENT

scores are in the teens. The solution is to retrain the model, but that will mean you have to evaluate the results and likely test different algorithms and parameters, so this isn't a quick fix.

Another option that's usually better for sales forecasting is to retrain the model regularly, even every night if it's feasible. This will reduce the likelihood of model drift. However, it doesn't remove it completely. In our example, imagine a regular promotion is introduced that wasn't there when you first were forecasting the code that you used to generate the model. That info is probably going to help the model a lot because promotions usually change purchase patterns, but until you modify your code to add the feature, that information is lost and the model will underperform.

One situation requiring adjustments is something new is added that your model didn't consider but that must be there now. For instance, if you're forecasting sales of specific products differently, a new product won't immediately be included. You will need to do the work to include it.

## Post-project Time Management

The important thing to remember here is that if the need for intervention comes after the project is officially over, you won't necessarily have “free” time to work on it. You'll be working on something else at that point. It probably won't be up to you to prioritize the broken code or dashboard over your current work, but it will likely take time away from your current work, which is frustrating for you and everyone else interested in that project.

## Key Takeaways and Next Up

In this chapter I talked about the challenges of managing data science projects. There aren't established ways and people generally cobble together ways of managing projects. I talked about traditional project management, especially in relation to project planning and execution, and then about the software variations on that. I proposed a way of managing data science projects with the stepwise data science Kanban board, which adds swimlanes to define project stages to a typical Kanban board. I then talked about some of the post-project work that has to be done.

In the next chapter, I'll be talking about the various known biases and fallacies that can affect data scientists and data science projects. Knowing about them will help you avoid them or at least mitigate them.

## PRACTITIONER PROFILE: HADLEY KOMBRINK

## Name:** Hadley Kombrink

**Current Title:** Technical project manager

**Current Industry:** Retail, previous healthcare and IT consulting

**Years of Experience:** 6 in managing data science

**Education:**

- Certified Scrum-master
- Master of Public Administration
- BA English and Sociology

The opinions expressed here are Hadley's and not any of her employers, past or present.

## Background

After Hadley finished her undergraduate degree, she went on to do a master's and ended up teaching in the program for several years afterward. But she was also exposed to analytics during that time and enjoyed it. She gravitated toward IT in general and worked for a hospital with a database administrator, where she learned even more. She soon moved into a new role on another IT team, infrastructure project management, where she became a technical project manager. In that role, she managed technical rollouts that could still affect the business, like SharePoint and Internet Explorer. She got to where she felt she knew a little about everything. She worked in a similar role at another job before landing a new role at the hospital as a business solutions analyst.

## CHAPTER 21 PUTTING IT ALL TOGETHER: DATA SCIENCE SOLUTION MANAGEMENT

## Work

Hadley's role as a business solutions analyst, she had a variety of responsibilities and acted as a product owner, Scrum-master, business analyst, and more and managed many types of projects. It also involved a lot of interaction with customers, and she also dabbled in some coding at this point. But the most interesting thing was that there were several positions in the team, including a data scientist, with which is she started learning about that field. She soon found herself specializing in managing data science projects, which she still does today.

## Sound Bites

**Favorite Parts of Managing Data Science Projects:** Variety in the work day and working with different kinds of people with different backgrounds and specialties. She also loves to set priorities and guide business value without being a people manager.

**Least Favorite Parts of Managing Data Science Projects:** Bureaucracy and when she can't see how to make an impact, like when something is beyond her control.

**Favorite Project:** She worked on a mobile device management project at the hospital that involved a lot of people skills. They were trying to get doctors to use their phones for work, but had to convince them that the hospital wouldn't steal their photos or get into the other areas of their phones. She had to really flex her communication skills on project, which was ultimately successful.

**Skills Used Most in Managing Data Science Projects:** Cat herding and various organization techniques like managing emails, to-do lists, and systems to manage and organize project work (like Agile management tools).

**Primary Tools Used Currently:** Hadley still loves pen and paper, especially for to-do lists. For project management, she's used Jira, ServiceNow, and other Agile tools. Also, Google Suite and Canva.

**Future of Data Science:** It's still the future, along with having a strong data foundation for all work. There is still work to be done on data in general. But good communicators will also remain very important.

**What Makes a Good Data Scientist and DS Project Manager:** Data scientists should be very inquisitive, be willing to work with the business and stakeholders, have technical skills, and always consider different options. DS PMs need to be flexible because it's not like management of other technical projects.

**Her Tip for Prospective Data Scientists:** Ask lots of questions and don't have a big ego. Network and forge relationships, and especially find a mentor if possible, as the data science community is small.

> Hadley is an experienced project manager with experience managing data science and other IT projects.

## CHAPTER 22

## Errors in Judgment:
Biases, Fallacies,
and Paradoxes

## Introduction

We all know that people have cognitive biases and fallible memories and beliefs—or at least know we know that other people do it. It's hard to remember that ourselves have them. There's actually a name for that—bias blind spot, where we assume we're less biased than other people. There's no real way to get rid of this lizard brain irrationality altogether, but we can be aware of these inaccurate beliefs and correct for them consciously.

Obviously in a book about data science, we care about more ones that affect our ability to do quality and fair data science, but a lot of them can affect our data science work in surprising ways.

In this chapter, I'm going to cover a variety of biases, fallacies, and paradoxes, how they can manifest in data science work, and what we can do about it. First, we'll look at a couple of examples where biases or fallacies caused problems.

## Examples of Biases and Fallacies in the Real World

The two examples we'll look at include Amazon's sexist screener, which we originally saw in Chapter 9. This example exhibits several different biases we'll talk about the chapter. The second example is a tool used in healthcare that accidentally biased against Black people because it used an economic measure that mistakenly made Black people less than they actually were. It also shows several problems, but especially one paradox that we'll also talk about.

## Example 1: Amazon's Sexist Automatic Resume Filter

In 2014, Amazon started work on a tool to help them identify quality applicants by automatically reviewing their resumes. It was supposed to crawl the Web to find these excellent candidates and bring them into the hiring process. By 2015, Amazon realized that their screner was really sexist, heavily favoring male applicants. This was not the intent, and the company scrapped the project (although they apparently start another attempt). How did the system turn sexist?

This screener was intended to be a classifier that would identify candidates that were worth starting through the evaluation process. The team used years of applicant resumes as the training set and created a
