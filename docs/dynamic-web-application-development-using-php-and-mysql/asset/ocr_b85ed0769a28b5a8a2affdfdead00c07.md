We can live without these, but they could provide some benefit to our users. They might be regarded as ‘sugar’ (handy but non-essential).

These are our final two requirements:

+   12. The system should be available 24/7/365 and be able to cope with 10,000 concurrent users.
+   13. The system should have a telepathic user interface.

These will have to be put into the ‘would like to have’ category, at least for the moment. They certainly need some further work before being taken seriously as priority requirements.

What is the point of this exercise? It enables us to schedule the important requirements first when developing the system. Agile approaches would use ‘story cards’ for requirements, with each card representing a user story about what the system should do. By prioritising these cards, we can put them into various iterations, with the most important in the early iterations.

# 2.6 Analysis tools – domain models, use cases and storyboards

In this section, we introduce some basic UML notations that can help us to visualise key features of the application. Even if a development project takes an agile approach that does not worry about extensive formal documentation, using standard notations for descriptive sketches can be very useful as a common communication medium between developers and users.

# The domain model

A useful model to build before getting into details about the system use cases is a domain model that captures the key concepts of the business domain. The domain model helps us to begin to understand how various important concepts of the domain interact in a structural way. Again, we should develop the domain model in a workshop environment. Some analysis methods suggest that the domain model should grow piecemeal out of the use case analysis, but the advantage of developing the domain model early is that it provides a common vocabulary within which the following stages of the analysis can take place. This ensures that, for example, different threads of the analysis do not end up using two different names for the same concept because everyone can work from, and enhance, the same domain model. The model itself captures a few simple ideas:

+   - What are the key concepts in the domain?
+   - Which concepts interact with each other?
+   - How can we describe these interaction relationships?
+   - What is the cardinality of these interactions? (In other words, which relationships are one to one, which are one to many and which are many to many?)

We can begin to identify the core concepts in our domain by identifying nouns in our core requirements. From our set of objectives, we can find 27 nouns (plural nouns have been