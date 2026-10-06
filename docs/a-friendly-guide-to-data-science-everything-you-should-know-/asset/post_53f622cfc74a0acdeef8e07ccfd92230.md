
# INTRODUCTION

topic (here's a class about unsupervised learning, here's one about data cleansing, etc.), and this book will keep you from forgetting the larger context for anything you're studying. It's like a roadmap for your degree.

**Career Changers:** If you're planning a move into data science, you will want to understand where everything sits in relation to everything else in the data world. As mentioned, you don't need to make yourself an expert in all areas of data science, but reading this book may help you choose some areas to focus on in your educational journey to a new field.

**Organization Leaders:** If you're thinking about adding data science to your organization, or if you already have data scientists, having a good understanding of the entire discipline of data science will be invaluable and help you understand what's being done, why it takes some time, and when it isn't cheap. This is a more technical book than a lot of data books written for leaders. You can obviously skip or some of the most technical parts, but this greater depth will help you understand why things are how they are.

**Citizen Data Scientists:** A lot of people have cracked their knuckles and started writing data science code through sites like Kaggle. If you're one of them and you only have that kind of experience, this book can give you the bigger picture of the field you're dabbling in. It can help you understand the need to develop rigor and identify areas you want to learn more about, similar to career changers.

# What This Book Covers

The book is divided into three parts—Part I: Foundations, Part II: Doing Data Science, and Part III: The Future. Part I covers the most important concepts and practices to understand before digging into actual data science. Like its name says, Part II looks at the various components that are a part of doing data science. Finally, Part III looks at how you can make data science a part of your future.

xxxiii

# Part I: Foundations

Part I contains nine chapters that are crucial to understanding data science in general. Chapter 1 explores the most fundamental aspect of data science, data itself. Chapters 2, 3, and 4 introduce aspects of statistics because statistics is critical in a lot of data science. Chapter 2 covers descriptive statistics, the heart of the exploratory data analysis that occurs early in most data science projects. Chapter 3 dives into probability and the basics of inferential statistics, sampling, experiment and study design. Chapter 4 completes the discussion of inferential statistics and covers statistical testing.

Chapters 5, 6, and 7 are all about analytics. Chapter 5 introduces data analysis as a distinct field that has been around longer than data science and forms the foundation for a lot of data science work. Chapter 6 dives into data science itself, defining it and discussing how it fits into organizations. Chapter 7 talks about "The New Data Analytics," basically an umbrella term for any analytics being done today nowadays, whether it fits under data analysis or data science or any other area.

Chapters 8 and 9 address some of the considerations that are important when doing data science. Chapter 8 talks about data security and privacy, and Chapter 9 looks at ethics as it pertains to data science.

# Part II: Doing Data Science

Part II contains the bulk of the chapters and talks about the specific areas of data science that got carried out. Chapter 10 addresses domain knowledge, the understanding of a particular area like medicine or retail that people must have if they're going to do good data science in that domain. Chapter 11 talks about the programming aspect of data science, specifically the languages Python and R.

Chapters 12, 13, and 14 all address data specifically. Chapter 12 looks out at data collection and storage. Collection can be manual or automated, and there are many challenges that can arise in the process. Data storage is most commonly in databases nowadays, but there are other possibilities. Chapter 13 talks about preparing data for data science through preprocessing steps. Chapter 14 dives into feature engineering, the additional work that almost always needs to be done on data before data science can be done.

Chapters 15, 16, and 17 talk about machine learning, performance evaluation, and language-related techniques used in data science. Chapter 15 is a long chapter covering the many areas of machine learning, including some common techniques used. Chapter 16 talks about the many ways of measuring how well your machine learning did. Chapter 17 addresses working with language, either as text or speech, covering many processing techniques used to prepare the data for further work.

Chapter 18 dives into the massively important area of visualization and presentation in data science. Visuals and presentations are all of your stakeholders see, so it's important to do this part well.

The remaining chapters in this part address several different areas. Chapter 19 looks at the many fields that are using and can use machine learning and language processing. There are many possibilities. Chapter 20 talks about scalability and the cloud, critical to doing data science today on the large datasets so many organizations have. Chapter 21 looks at data science project management and tracking, a notoriously difficult area of the field. Data science projects often get smushed into systems designed for software development, and they don't fit. Chapter 22 addresses an important area that relates to ethics but also to doing good data science: human cognitive biases and fallacies, and paradoxes of the field. It talks about what they are, how they can manifest and how to deal with them.

# Part III: The Future

Part III has three chapters that discuss various aspects of going into the field of data science. Chapter 23 talks about how important it is to start doing actual data science and how it's easy to do with the many publicly available datasets out there (or your own). Chapter 24 talks about how to learn more about data science, something that you'll always need to be even when you are data scientist. Finally, Chapter 25 addresses data science and related careers and how to break into them.

# Practitioner Profiles

At the end of every chapter, I've included a profile of a professional working in data science or related areas based on an interview I did with each of them. A few of them work in disciplines other than data science and are paired with a given chapter based on its topic. During the interviews, I tried to get each person’s “story”—how they got into data science and tech in general have people with all sorts of backgrounds. This is partially because degree programs in data science are fairly new, so many current practitioners came from other disciplines (physics was one of the most common sources of data scientists). It's a good reminder of how breadth of knowledge is valuable in data science. The profiles also include the practitioners' thoughts on working in the field, again showing how different people like some areas more than others, and personal preference always comes into that. They’re all interesting to read, so don’t skip them.

# PART I: Foundations

# CHAPTER 1

# Working with Numbers: What Is Data, Really?

# Introduction

Anyone who's heard of data science also knows that data is at the heart of it. Whether they know what data science is or not, everyone's comfortable throwing around the word “data”—we've all heard about privacy, security breaches, and groups collecting, stealing, selling data about us.

Data is fundamentally abstracted information that represents something from the real world in a simplified way. That word “represents” is key to understanding data. The only reason data exists because it makes things more tangible, which can help us understand reality in new ways.

Imagine a family reunion with a backyard full of people spread around, chatting, some hanging out by the food table. You know that men are generally taller than women, and you've heard that people are getting taller over the generations. You wonder if these rules hold true in your
