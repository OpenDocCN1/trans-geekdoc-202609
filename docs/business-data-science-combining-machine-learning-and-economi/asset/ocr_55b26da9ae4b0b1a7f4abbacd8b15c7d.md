![](bbox=[0.34, 0.06, 0.71, 0.36])

FIGURE 8.10: MNIR projection $z_{overall}$ against true overall review rating.

These MNIR projections (also called sufficient reduction [SR] projections) are especially useful for sorting documents according to the various attributes. Taking an example from Taddy [2015b], we consider reviews on Yelp.com for a variety of places (restaurants, hotels, landmarks). In addition to the reviewer’s star rating, these reviews also come accompanied with votes from other Yelp users on the quality of the review itself. On Yelp.com you can give a review a vote as funny, useful, or cool. You can run MNIR onto these vote counts as well as a list of other variables that you would like to control for, such as the category of the review subject (e.g., restaurant, bowling alley, or both) and how long this subject has been up on Yelp.

The results illustrate the usefulness of MNIR projections based on partial correlations. Sorting reviews by vote alone is not especially informative because the reviews that get a lot of votes tend to be those that are old or associated with popular subjects. For example, the funniest review by votes in the sample is a nonhumorous review of the Casa Grande national monument in Coolidge, Arizona; this is also the most useful and coolest review by votes.

In contrast, the review with highest MNIR projection $z_{funny}$ is an open letter to the restaurant that is designed to be humorous:

> Dear La Piazza al Forno: you need to talk. I don’t quite know how to say this so I’m just going to come out with it. I’ve been seeing someone else. How long? About a year now. Am I in love?