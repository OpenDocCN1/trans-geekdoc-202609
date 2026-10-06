# Post-project Work

Projects of all types usually have a start and end. This is true for data science projects, too. We talked about the lifecycle of a data science project, but there's nothing what happens after the project is finished. With software, there's an acknowledged post-completion phase, maintenance. In software, that just means ensuring it's still working. Things are more complicated in data science.

In terms of post-project work, some data analysis and data science projects don't have anything based directly on the project work. This is the situation when you've been asked to perform some analysis and have delivered a report. You might be asked to repeat or update the analysis, but that involves rerunning things (hopefully your code makes it as simple as that), not really tweaking the work from the actual project. In two other typical cases, there are post-project responsibilities. We'll talk about these next.

# Code Maintenance

One scenario when there is work to do after the project is when a dashboard has been created as part of the project that needs to be regularly refreshed, so code is in place to prepare the data for the dashboard, either in the BI tool or outside of it. A second is when a model has been created that will continue to be in use (whether it's queried via an API or used in code you've also written that refreshes regularly or some other scenario).

In both of these cases, any scheduled code or data transformations in a BI tool need to run as expected. The advantage of code is that it will always run the same unless something changes or a transient computer fail occurs. A random computer fail could be something like the network connection lost while relying on data in the cloud ran or a computer simply being down so the job isn't triggered. The point is that the fault lies not with your code, but on the mechanism it relies on run.