
# CHAPTER 21 PUTTING IT ALL TOGETHER: DATA SCIENCE SOLUTION MANAGEMENT

tweaks based on what came out of the EDA. The experiment code in the Analysis & Modeling swilane was done except adding the market share features, so it was stuck in In Progress. We were still able to get started on some of the code and fine-tune our code for evaluating the experiment results, those we moved to In Progress. We were also able to start validating the datap prep (all parts except what the new data sources) in the Validation & Evaluation swilane. We added one more story to the Visualization & Presentation swilane, for creating the final slide deck, and started on the first slides that just explained the project and other preliminary changes.

| Week 17 | To Do | In Progress | Blocked | Done |
| :--- | :--- | :--- | :--- | :--- |
| Business Understanding | | | | Meet with stakeholders | Create project plan possible (Feb) | Maybe do not get project plan off |
| Data Understanding | EDA on market data source 2 | EDA on market data source 3 | | Meet with data source | EDA on sales data source 1 | EDA on share data source 2 |
| Data Preparation | Refactor data prep/fe | Combine market share data sources | Preprocessing on market share data 2 | Determine query sales source | Determine market | Feature engineering on |
| Analysis & Modeling | Refactor modeling code & organize | Write and run code for model S4 | Write and run experimental (custom) code | Analyze experimental Write and run code for incrementality/consistency | Feature | Feature engineering on |
| Validation & Evaluation | Validate modeling code | Validate data prep code | | | |
| Visualization & Presentation | Determine best visualization | Create visualizations | Create slide deck to show results | | | |

Figure 21-8. The stepwise data data science Kanban board at the end of week 17 on the incrementality project

# CHAPTER 21 PUTTING IT ALL TOGETHER: DATA SCIENCE SOLUTION MANAGEMENT

After the new data sources came in, we scrambled and managed to get everything done and with some long days got everything in time for a deadline that had been looming. See Figure 21-9 for what the board looked like. We did finish the EDA on the two new sources in the Data Understanding swimilane. Then, in the Data Preparation swimlane, we got the preprocessing done on both sources and combined them and finalized the feature engineering code for it. Only the refactoring story remained in that swimlane, and it was saved for later. In the Analysis & Modeling swimlane, we finished all the In Progress stories and only the refactor for later remained. In the Validation & Evaluation swimlane, we did enough validation of the code to feel like it was accurate, although we didn’t have time to do the rigorous code reviews we normally do. Finally, we finished all the Visualization & Presentation stories and presented the deck to the stakeholders.

# CHAPTER 21 PUTTING IT ALL TOGETHER: DATA SCIENCE SOLUTION MANAGEMENT

| Week 21 | To Do | In Progress | Blocked | Done |
| :--- | :--- | :--- | :--- | :--- |
| Business Understanding | | | | Meet with stakeholders | Create explore possible sources | Moho-en (14) | Get project signoff | |
| Data Understanding | | | | Meet with SME on market | EDA on market sales | EDA on not share data source 2 | EDA data source 3 | |
| Data Preparation | Refactor data/ff code & organize | | | | Preprocessing | Combine market shares. | Engineering on shared components coding 1 | |
| Analysis & Modelling | Refactor modeling code & organize | | | | Write and run experiments | Analyze results | Write and run code for model and SBA to calculate incrementality & consistency | |
| Validation & Evolution | | | | | Validate data prep code | Validate modeling code | | | |
| Visualization & Presentation | | | | | Create slide to show results | Give final presentation | Determine best visualization | Create visualizations | |

**Figure 21-9.** The stepwise data science Kanban board at the end of week 21 on the incrementality project.

Hopefully, this gives you a sense of how the Kanban board can work for a data science project. Note that it's common to leave all the stickies on the Done column on a physical board, but obviously can get crowded so sometimes they get moved. On a virtual board, they will stay there if to visible.

# Post-project Work

Projects of all types usually have a start and end. This is true for data science projects, too. We talked about the lifecycle of a data science project, but there's nothing what happens after the project is finished. With software, there's an acknowledged post-completion phase, maintenance. In software, that just means ensuring it's still working. Things are more complicated in data science.

In terms of post-project work, some data analysis and data science projects don't have anything based directly on the project work. This is the situation when you've been asked to perform some analysis and have delivered a report. You might be asked to repeat or update the analysis, but that involves rerunning things (hopefully your code makes it as simple as that), not really tweaking the work from the actual project. In two other typical cases, there are post-project responsibilities. We'll talk about these next.

# Code Maintenance

One scenario when there is work to do after the project is when a dashboard has been created as part of the project that needs to be regularly refreshed, so code is in place to prepare the data for the dashboard, either in the BI tool or outside of it. A second is when a model has been created that will continue to be in use (whether it's queried via an API or used in code you've also written that refreshes regularly or some other scenario).

In both of these cases, any scheduled code or data transformations in a BI tool need to run as expected. The advantage of code is that it will always run the same unless something changes or a transient computer fail occurs. A random computer fail could be something like the network connection lost while relying on data in the cloud ran or a computer simply being down so the job isn't triggered. The point is that the fault lies not with your code, but on the mechanism it relies on run.

# CHAPTER 21 PUTTING IT ALL TOGETHER: DATA SCIENCE SOLUTION MANAGEMENT

Usually, the fix is to just manually kick off the process one time after the other system is back up and running, and it should go back to working the next scheduled time.

The "something changes" scenario is more difficult. This can be a whole sort of things, including database structure changes (removed or added columns in one of your tables, for instance), a change in permissions on the account that's used to connect to a database, a refresh to a table you were moving to a later time than you've allowed for. There are basically an infinite number of possibilities for your code to be bork. This is actually a huge pain, because now you have to figure it out, and if you're unlucky enough to have only an unhelpful error message (very common, unfortunately), it can be anything—so it's time-consuming to troubleshoot. Sometimes you might find something you need to ask someone else about, and if they're busy, you may be stuck until they respond. If you need to get it working, you'll have to keep going until you figure it out.

# Model Drift and Maintenance

One other area that's important when you have a deployed model, whether it's trained and static or retrained regularly, is the idea of model drift. Model drift is the situation where a model's performance changes over time, usually for the worse. So, checking for that, we monitor the performance of the model over time. As an example, let's say you have a model that's in production and forecasts sales at all stores for the next seven days, running every night. The model itself isn't retrained, so the longer it's in place, the more "out of date" the data is. We may see good performance metric values (for instance, MAPE scores less than 10%) on most days. But after it's been running for a year, a lot more of the MAPE
