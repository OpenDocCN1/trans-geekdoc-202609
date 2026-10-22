# *ML platform team*

As the traffic grows, this team has been woken up in the middle of the night because of problems with scaling their existing system, so they want to hold off on model updates to prioritize improving the ML platform.

# *Manager*

Wants to maximize the margin, and one way to achieve this might be to let go of the ML team.^14^

> “Recommending the restaurants that users are most likely to click on” and “recommending the restaurants that will bring in the most money for the app” are two different objectives, and in the section [“Decoupling objectives” on page 41], we’ll discuss how to develop an ML system that satisfies different objectives. Spoiler: we’ll develop one model for each objective and combine their predictions.

Let’s imagine for now that we have two different models. Model A is the model that recommends the restaurants that users are most likely to click on, and model B is the model that recommends the restaurants that will bring in the most money for the app. A and B might be very different models. Which model should be deployed to the users? To make the decision more difficult, neither A nor B satisfies the requirement set forth by the product team: they can’t return restaurant recommendations in less than 100 milliseconds.

When developing an ML project, it’s important for ML engineers to understand requirements from all stakeholders involved and how strict these requirements are. For example, if being able to return recommendations within 100 milliseconds is a must-have requirement—the company finds that if your model takes over 100 milliseconds to recommend restaurants, 10% of users would lose patience and close the app—then neither model A nor model B will work. However, if it’s just a nice-to-have requirement, you might still want to consider model A or model B.

Production having different requirements from research is one of the reasons why successful research projects might not always be used in production. For example, ensembling is a technique popular among the winners of many ML competitions, including the famed $1 million Netflix Prize, and yet it’s not widely used in production. Ensembling combines “multiple learning algorithms to obtain better predictive performance than could be obtained from any of the constituent learning algorithms alone.”^15^ While it can give your ML system a small performance improvement, ensembling tends to make a system too complex to be useful in production, e.g.,

^14^ It’s not unusual for the ML and data science teams to be among the first to go during a company’s mass layoff, as have been reported at [IBM](https://oreil.ly/jobmz), [Uber](https://oreil.ly/jobmz), [Airbnb](https://oreil.ly/jobmz). See also Sejuti Das’s analysis “How Data Scientists Are Also Susceptible to the Layoffs Amid Crisis,” *Analytics India Magazine*, May 21, 2020, https://oreil.ly/jobmz.

^15^ Wikipedia, s.v. “Ensemble learning,” https://oreil.ly/5qkgp.