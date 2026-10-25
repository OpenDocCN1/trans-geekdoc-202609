collected in the regular course of business, a.k.a. *found data*. It encodes the experience from which the modeling process can learn.

The solution to this dilemma was to develop a model for each ad—291 different models, each predicting whether the user will respond to that ad. This means 291 different prediction goals, each in this form:

**Prediction Goal for Targeting Ads (EduPay): Will the user respond to this ad if it is displayed?**

To choose an ad for a given user, all the models were systematically applied and the choice of which ad to display was based on the predicted probabilities. Some models might say the chances are only a fraction of a percent, and others might go up to a 20 percent probability or even higher—which is a lot, considering that online ads are more often than not simply ignored. In this way, the choice of ad became personalized, the overall odds improved, and the number of responses increased over time.

Ads weren't only selected based on model probabilities. Other factors were also in play, such as the amount the sponsor was willing to pay and eligibility requirements stipulated by the sponsors. We'll visit those and other mechanics of step 6, *model deployment*, when we get to that step's chapter.

# Collaborating on the Prediction Goal

Engage everyone who will touch the analytic model in the development process. . . . The success or failure of analytics and data science initiatives often hinges on whether those on the “front lines” of business actually use and follow them.

> —Tom Warden, Chief Data and Analytics Officer, EMPLOYERS

As you navigate these considerations and formulate the prediction goal in complete detail, you need help from across the enterprise. You can’t go it alone. Every semi-technical aspect that defines what you’re going to predict depends on pragmatic business considerations. For the