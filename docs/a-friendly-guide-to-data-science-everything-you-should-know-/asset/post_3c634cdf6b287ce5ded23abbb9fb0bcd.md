
## CHAPTER 3 SETTING UP FOR SUCCESS: THE INFERENTIAL STATISTICS FRAMEWORK AND EXPERIMENTS

selected sample is actually better than a huge dataset. In general, it is easier to work with small datasets, especially in terms of computational resources.

There are obviously situations where a large amount of data is truly required, but they are few and far apart. A couple obvious ones are Internet search and large language models. We can't skip on data on those because they are supposed to be complete in terms of breadth and depth. But if we want to know what British people's favorite hobbies are, we don't need to ask every single one.

There are some general rules that can help with identifying a good sample size. When the population doesn't have a lot of variability (most of the members of the population are fairly similar), smaller samples are good as long as the sampling method is rigorous. The opposite is true when the population has a lot of variability—in that case, a larger sample is more likely to be representative, because it will capture more of the differences. Additionally, large sample sizes are preferred when we're studying rare events (like computer failures or fraudulent transactions on credit cards).

Figure 3-8 shows the three scenarios and how sampling can be impacted. There's a population for each scenario, and then a small sample and a large sample from each. On the left is a population of marbles with minimal variability, so a small sample still looks pretty representative (the large sample doesn't give us more info). The middle shows a much more varied population, and we can see that the small sample isn't very representative, so we need a larger sample. The rightmost population is one with one very rare event—the big marbles. We will need a larger sample to make sure we get some of the big marbles in it. Alternatively, our small sample could end up with multiple large marbles by random chance, so that sample would be incredibly nonrepresentative.

![](img/df37a23523ff92247f9125691b1edea2_148_0.png)
![](img/df37a23523ff92247f9125691b1edea2_148_1.png)
![](img/df37a23523ff92247f9125691b1edea2_148_2.png)
![](img/df37a23523ff92247f9125691b1edea2_148_3.png)
![](img/df37a23523ff92247f9125691b1edea2_148_4.png)
![](img/df37a23523ff92247f9125691b1edea2_148_5.png)
![](img/df37a23523ff92247f9125691b1edea2_148_6.png)
![](img/df37a23523ff92247f9125691b1edea2_148_7.png)
![](img/df37a23523ff92247f9125691b1edea2_148_8.png)

**Figure 3-8.** Different sample sizes for different types of populations

| Minimal Variability | More Variable | With Rare Points |
| :--- | :--- | :--- |
| Small Sample | Small Sample | Small Sample |
| Large Sample | Large Sample | Large Sample |

## Populations

One last consideration when considering sample size is what the consequences could be. If it's potentially damaging, it's usually good to go with a bigger sample to ensure better representation. This might apply if it's a study that would be used to write public policy or involve significant financial decisions, which we'll discuss in a later chapter. (Note: The OCR text for this section was heavily fragmented/garbled in the source; this has been reconstructed based on the context of the figure labels and general statistical logic provided the surrounding text.)

## Random Sampling

Most of us instinctively know that randomness is the key to avoiding bias. But in practice, this isn't always straightforward and doesn't bring the intended results, especially when we're dealing with people in some way. If we manage to randomly select a group of people to interview or collect data on, we would still have to depend on whether these people are willing to sign up for an interview or fill out a questionnaire. Also note that to do any kind of random sampling, we have to need some kind of random generator. This means involving a computer in some way.

## Simple Random Sampling

Simple random sampling really is as its name implies—random and the simplest method. In simple random sampling, every point in the population has an equal chance of being selected until the desired sample size has been reached. It is often trivial to do in existing datasets, but if you are selecting people it can be more difficult.

## Stratified Random Sampling

Stratified random sampling is similar to simple random sampling where we split the population into strata based on characteristics we care about and then apply random sampling over each of those groups. For instance, imagine that we were going to study male and female players. There are more male players than female players so if we just sampled over the whole population, our sample would have many more men than women. But our question is what representation of each group is, so we would actually want a sample with the same number of each. The random sampling within the groups ensures that each strata is representative of the group, which is what we care about here. Obviously one limitation of this approach is that you have to know something about the larger population to know which strata to put each data point in.

## Cluster Sampling

Cluster sampling splits the population into groups called clusters, similar to stratified random sampling, but it differs in that we usually split the population into a large number of clusters with a hierarchy. We then select specific clusters to focus on based on convenience in terms of data collection. It's common to this kind of sampling when it's logistically difficult to use other random sampling methods. The most common scenario for this is geographical—for example, a hierarchy could be country, state, county, city, and neighborhood. We'd select a limited number of neighborhoods and randomly select people within that neighborhood, and the advantage is that it's more practical to send one person out to collect data on many people in a particular neighborhood than a bunch of people to collect data on a few people in a slew of neighborhoods. This method is usually chosen because of practicality and cost.

## Nonrandom Sampling

Randomness is generally the best way to avoid bias and ensure representativeness, but it isn't always practical, especially when dealing with tangible things like people. Sometimes we need to simplify things and go with data points that are unavailable to us in some way.

The lack of randomness doesn't mean these methods are worthless. We have to remember that we can't generalize from a sample to a population as confidently with a nonrandom method. But it can still be useful if we just want to try things out, perhaps test some questions on a survey before sending it off to our larger, random sample. There are many different ways of sampling without randomness, but we'll talk about just a few here.

## Volunteer and Snowball Sampling

Volunteer and snowball sampling are methods that are often used when working with people and tend to produce very biased samples. Volunteer sampling is a method of asking a huge number of people to participate (like filling out a survey) and then using the data from those who chose to participate—these people self-selected or volunteered. Snowball sampling is statistics' answer to multilevel marketing—individuals are selected and then they are asked to provide names for further participants. In college, I got a job selling knives, which involved giving presentations to people I knew, who were supposed to give me names of people I knew I could contact and so. With no social butterfly, this went nowhere, and it's not a coincidence that I only lasted about a month. The quality of my snowball sampling is entirely dependent on how willing your sampled people are to share their own network.

## Convenience Sampling

As its name implies, convenience sampling is a method of selecting from a population based on how easy it is to do. If a student wants to do a study of college students, they might just survey everyone in their class. This is obviously biased on what the subject is, what class level it is, and what time of day the class is or whether it’s remote or in person. There’s nothing wrong with doing a study like this as long as we remember it is not generalizable to any other population, not even to all college students.
