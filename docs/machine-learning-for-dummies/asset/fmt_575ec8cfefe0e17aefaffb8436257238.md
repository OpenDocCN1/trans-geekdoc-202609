
![Remember](images/remember.png)As the dataset becomes larger, the computer can use the algorithms found in an application to perform more work. The use of immense datasets, known as `big data`, enables a computer to perform work based on pattern recognition in a nondeterministic manner. Algorithms determine how a machine interprets big data. The algorithm used to perform machine learning affects the outcome of the learning process and, therefore, the results you get. In short, to create a computer setup that can learn, you need a dataset large enough for the algorithms to manage in a manner that allows for pattern recognition, and this pattern recognition needs to use a simple subset to make predictions (statistical analysis) of the dataset as a whole.

Big data exists in many places today. Obvious sources are online databases, such as those created by vendors to track consumer purchases. However, you find many non-obvious data sources, too, and often these non-obvious sources provide the greatest resources for doing something interesting. Finding appropriate sources of big data lets you create machine learning scenarios in which a machine can learn in a specified manner and produce a desired result.

`Statistics`, one of the methods of machine learning that you consider in this book, is a method of describing problems using math. By combining big data with statistics, you can create a machine learning environment in which the machine considers the probability of any given event. However, saying that statistics is the only machine learning method is incorrect. This chapter also introduces you to the other forms of machine learning currently in place.

![Tip](images/tip.png)Before an algorithm can do much in the way of machine learning, you must train it. The training process modifies how the algorithm views big data. It’s essential to understand that `training` is actually using a subset of the data as a method for creating the patterns that the algorithm needs to recognize specific cases from the more general cases that you provide as part of the training.

## Defining Big Data

Big data is substantially different from being just a large database. Yes, big data implies lots of data, but it also includes the idea of complexity and depth. A big data source describes something in enough detail that you can begin working with that data to solve problems for which general programming proves inadequate.

As an example of big data complexity, consider Google’s self-driving cars ([`https://waymo.com/`](https://waymo.com/)). The car must consider not only the mechanics of the car’s hardware and position with space but also the effects of human decisions, road conditions, environmental conditions, and other vehicles on the road, which is why our roads aren’t crowded with them yet (see [`https://www.vox.com/future-perfect/2020/2/14/21063487/self-driving-cars-autonomous-vehicles-waymo-cruise-uber`](https://www.vox.com/future-perfect/2020/2/14/21063487/self-driving-cars-autonomous-vehicles-waymo-cruise-uber)). It’s not hard to imagine some of the human-specific issues that self-driving cars will need to address, such as people taking a nap when they should be watching the road even with the self-driving car in control ([`https://robbreport.com/motors/cars/canadian-police-arrest-sleeping-driver-tesla-autopilot-1234570071/`](https://robbreport.com/motors/cars/canadian-police-arrest-sleeping-driver-tesla-autopilot-1234570071/)).

The data source for a self-driving car (or any other complex endeavor for that matter) contains many variables — all of which affect the vehicle in some way. Traditional programming might be able to crunch all the numbers, but not in real time. You don’t want the car to crash into a wall and have the computer finally decide five minutes later that the car is going to crash into a wall. The processing must prove timely so that the car can avoid the wall.

The acquisition of big data can also prove daunting. The sheer bulk of the dataset isn’t the only problem to consider — also essential is to consider how the dataset is stored and transferred so that the system can process it. In most cases, developers try to store the dataset in memory to allow fast processing. Using a hard drive to store the data would prove too costly, time-wise.

![Remember](images/remember.png)When thinking about big data, you also consider anonymity. Big data presents privacy concerns. However, because of the way machine learning works, knowing specifics about individuals isn’t particularly helpful anyway. Machine learning is all about determining patterns — analyzing training data in such a manner that the trained algorithm can perform tasks that the developer didn’t originally program it to do. Personal data has no place in such an environment.

Finally, big data is so large that humans can’t reasonably visualize it without help. Part of what defines big data as big is the fact that a human can learn something from it, but the sheer magnitude of the dataset makes recognition of the patterns impossible (or would take a really long time to accomplish). Machine learning helps humans make sense of and use big data.

## Considering the Sources of Big Data

Before you can use big data for a machine learning application, you need a source of big data. Of course, the first thing that most developers think about is the huge, corporate-owned database, which could contain interesting information, but it’s just one source. The fact of the matter is that your corporate databases might not even contain particularly useful data for a specific need. The following sections describe locations you can use to obtain additional big data.

### Building a new data source

To create viable sources of big data for specific needs, you might find that you actually need to create a new data source. Developers built existing data sources around the needs of the client-server architecture in many cases, and these sources may not work well for machine learning scenarios because they lack the required depth (being optimized to save space on hard drives does have disadvantages). In addition, as you become more adept in using machine learning, you find that you ask questions that standard corporate databases can’t answer. With this in mind, the following sections describe some interesting new sources for big data.

#### Obtaining data from public sources

Governments, universities, nonprofit organizations, and other entities often maintain publicly available databases that you can use alone or combined with other databases to create big data for machine learning. For example, you can combine several Geographic Information Systems (GIS) to help create the big data required to make decisions such as where to put new stores or factories. The machine learning algorithm can take all sorts of information into account — everything from the amount of taxes you have to pay to the elevation of the land (which can contribute to making your store easier to see).

The best part about using public data is that it’s usually free, even for commercial use (or you pay a nominal fee for it). In addition, many of the organizations that created them maintain these sources in nearly perfect condition because the organization has a mandate, uses the data to attract income, or uses the data internally. When obtaining public source data, you need to consider a number of issues to ensure that you actually get something useful. Here are some of the criteria you should think about when making a decision:

*   The cost, if any, of using the data source

*   The formatting of the data source

*   Access to the data source (which means having the proper infrastructure in place, such as an Internet connection when using Twitter data)

*   Permission to use the data source (some data sources are copyrighted)

*   Potential issues in cleaning the data to make it useful for machine learning
