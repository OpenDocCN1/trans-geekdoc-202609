
Once you’ve documented these decisions, they will need to be applied at scale by however many people are responsible for building your application. Because even the most detailed instructions can be misunderstood, you’ll also find it highly beneficial to train your annotators. Before beginning on the real dataset, have them practice on a specific use case that highlights some of the potential ambiguities they’ll encounter. Provide them with the business context they’ll need to interpret the documented decisions.

# Completeness

In 2018, a Tesla Model 3 on autopilot drove into a semi\-trailer that had been wedged perpendicular to the freeway, shearing off the roof and killing the driver. Analysis showed the Tesla autopilot system hadn’t braked or warned the driver prior to the crash. Why not?

The answer was simple: the autopilot wasn’t taught to recognize a truck parked perpendicular to the stream of traffic on the freeway because that scenario happened so infrequently that the dataset the autopilot was trained on wasn’t rich and diverse or complete enough to cover this scenario successfully. It’s a situation so unusual that human drivers would stop and rubberneck. Tesla must have millions of examples of cars changing lanes suddenly or stopping short, but a perpendicular semi probably happens at most once a year, and even then, Tesla can’t be there every time to collect data on it. Their data didn’t include this outlier, and thus their model was incomplete in a way that had devastating consequences. Machine learning, in general, has an incredibly difficult time with exceptions and outliers. A well\-designed AI system has a fallback option that doesn’t rely on machine learning to deal with outlier scenarios.

Even for more common cases, data completeness can be difficult to achieve. For example, car crashes occur more frequently at night and during bad weather, so an autonomous self\-driving system should certainly be trained to recognize dangerous scenarios in those contexts. But precisely because it’s more dangerous to drive in those conditions, people drive in them less frequently, which means a lot less data exists to use for training.

Of course, the problem isn’t restricted to self\-driving cars. Credit card companies, for example, often have difficulty gathering enough examples of fraudulent transactions to train a model to detect them reliably. The vast majority of transactions aren’t fraudulent, and those that are can have patterns that vary widely. For these companies, achieving completeness is a huge challenge.

In order to get closer to completeness in training data, Tesla and companies like it now focus on those edge cases directly, often generating synthetic data for outlier scenarios by creating them with simulators. This approach is imperfect—it means they have to predict anomalous situations before they happen—but it can help to fill holes in the data that could lead to fatal consequences.

When you create your initial specification document detailing the strategies and decisions that should be used when annotating your data and building your model, you’ll also need to include all the anticipated edge cases the model is intended to support. If you don’t intend to cover a known edge case, document that too. Without explicit documentation of these decisions, it will be extremely difficult to ensure that your data is complete down the line.

# Security

A popular online eyeglasses retailer needed a way to match its traditional brick\-and\-mortar competition, which allowed a customer to try on many pairs of glasses, look in the mirror, and check how they look in different lighting before actually making a purchase. One of the main challenges of the online company was to overcome customers’ reluctance to buy something they would wear every day without trying it on.

To combat this reluctance, the company was developing a rich, augmented reality mobile app that would let a customer try on glasses virtually, using the camera on their phone. To accomplish this, they needed to annotate a huge dataset of people’s faces, identifying different points on the face and how eyeglasses would sit on them.

As they embarked upon the project, security was a huge issue. A leak of the data they were annotating would damage their business by giving their competitors clues as to what they were working on. They were trying to create something innovative by solving a difficult problem. But if the data were stolen, their competitor could begin work on the same thing, and their competitive advantage—a comparatively short time to market—would evaporate.

A leak would also bring up privacy concerns. As we mentioned earlier, a leak of sensitive data can cause issues of trust even when the company is protected from legal liability. You may have explicitly acknowledged Facebook’s right to redistribute images you upload as part of your membership agreement, but if your and your friends’ faces started showing up on billboards without your consent, Facebook would have a significant PR problem on its hands. A good rule of thumb when it comes to data privacy is: just because you can doesn’t mean you should.

It’s important to document the regulations or industry standards you’ll need to comply with, as well as any restrictions on your usage of the data. Knowing these up front will allow you to judge risks later that could take you out of compliance—for example, you might want to ignore a legally optional industry standard, but that may mean restricting your ability to enter a market. You’ll need to outline these contours ahead of time in order to craft a plan to achieve your ultimate goals.

# Governance

Data, as we mentioned earlier, is the new IP. It’s an incredibly important asset for your company, and its use has to be managed accordingly. Otherwise, inconsistencies or misuses of the data will cause problems down the line.

Companies that implement governance effectively set up internal policies that control how data is collected, transformed, and used, ensuring it is trustworthy and that the ways it can be used are clear.

The entire chain of custody of your data should be documented, from the contents of the dataset to the manner in which it was collected to the transformations that have been applied at each step along the way. Without this documentation, models that might be built relying on this data are unaware of the ways the data has been manipulated. The results of that model could end up being inconsistent or flat\-out wrong.

In 2011, Jeremy Howard won a Kaggle® competition to build a model for the University of Melbourne that could predict the success of grant applications. To build his solution, he used a random forest algorithm to identify which fields in the data contributed most to a grant being approved.

Unfortunately, Jeremy was unaware that the data had been transformed slightly from its original state; fields that had been left blank in the original grant applications had been labeled as having a null value instead of being ignored. As a result, he found that the biggest factor contributing to a grant’s approval was the number of null fields. This technically won the contest in the way the rules were outlined, but because it bore no relation to an actual grant approval process, the solution wasn’t of any use to the University of Melbourne. The data had been “cleaned,” a helpful act, but because Jeremy didn’t know it had been, he drew a conclusion and built a model that was useless.

Managing and documenting the chain of custody is also vital for security. It should be very clear at every stage who is able to read and who is able to modify the dataset. Besides preventing leaks, it can be vital for policy compliance.
