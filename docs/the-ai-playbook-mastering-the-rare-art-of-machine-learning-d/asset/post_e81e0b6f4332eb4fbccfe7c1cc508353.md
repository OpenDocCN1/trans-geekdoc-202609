
## Predicting Intermediate Steps

we aim to predict only for those with a tenure of at least four months. Finally, if a customer disengages but compensates by increasing their use of another one of our products, this doesn’t “count” as defection—that kind of change may not be worth any investment to prevent.

Predicting a partial step also applies to predicting good outcomes rather than bad—to predicting customer engagement rather than disengagement. Consider targeting fundraising activities for a charitable organization, which is very much akin to response modeling for direct marketing:

| Application and desired business outcome | What's predicted (model output) | What's done about it (deployment) |
|---|---|---|
| Targeting fundraising to increase donations | Will the individual make a donation? | Mail a letter to those likely to donate. |

The standard prediction goal is obvious: Will the individual make a donation? In some cases, this is the best tactic, such as for targeting direct mail solicitations.

But in the world of fundraising, direct mail mostly garners only small donations. Soliciting large donations is a different game. The cultivation of major donors can take years of relationship building. These donations are difficult to predict because they’re rare and because it’s tough to tie them to any particular prior action. Instead, one charity predicted an intermediate step toward securing a large donation:

> **Fundraising Prediction Goal (a charitable organization)**: Will the prospective donor agree to an in-person meeting with a gift officer?

If the prospect is willing to meet, this at least signifies an affinity for the charity and marks the beginning of what will hopefully be a long-term relationship.

This approach worked. By driving email, direct mail, and phone outreach with these predictions, the charity identified 40 percent more high-value prospects willing to meet. And in a retrospective evaluation of the model, the model identified 75 percent of major donors who’d already donated.

## Deciding Which Instead of Whether

With the marketing applications we’ve discussed so far, the model drives the choice between an active and passive treatment for each individual: To contact or not to contact—that is the question. Response modeling decides whether to reach out with sales material, and churn modeling decides whether to reach out with a retention offer.

But for EduPay, models needed to decide which ad to show. There was no question of whether to show an ad—one would always be shown. The passive treatment was never an option. In fact, there were a plethora of options: a pool of 291 ads from which to select. These sponsors had lined up, willing to pay each time a user responded to their ad.

Without ML, the ads were already working very well. By displaying the most popular ads first, the system was already generating $1.5 million in monthly revenue. But the choices were one-size-fits all—kind of advertising Hollywood blockbuster movies on television. They weren’t personalized. There was no attempt to target individual users with the ads they’d be most likely to respond to.

We needed a little trick to define the prediction goal for ad selection, as it isn’t straightforward. You can’t simply predict, “Which ad would the user respond to?” The reason for this is that we don’t have the data. We don’t have records tracking any user who was shown all the ads to see which they responded to. We never conducted that or any experiment—the aim was to use data that the business had already organically accumulated.

This is the data collected in the regular course of business, a.k.a. *found data*. It encodes the experience from which the modeling process can learn.

The solution to this dilemma was to develop a model for each ad—291 different models, each predicting whether the user will respond to that ad. This means 291 different prediction goals, each in this form:

**Prediction Goal for Targeting Ads (EduPay): Will the user respond to this ad if it is displayed?**

To choose an ad for a given user, all the models were systematically applied and the choice of which ad to display was based on the predicted probabilities. Some models might say the chances are only a fraction of a percent, and others might go up to a 20 percent probability or even higher—which is a lot, considering that online ads are more often than not simply ignored. In this way, the choice of ad became personalized, the overall odds improved, and the number of responses increased over time.

Ads weren't only selected based on model probabilities. Other factors were also in play, such as the amount the sponsor was willing to pay and eligibility requirements stipulated by the sponsors. We'll visit those and other mechanics of step 6, *model deployment*, when we get to that step's chapter.

## Collaborating on the Prediction Goal

Engage everyone who will touch the analytic model in the development process. . . . The success or failure of analytics and data science initiatives often hinges on whether those on the “front lines” of business actually use and follow them.

> —Tom Warden, Chief Data and Analytics Officer, EMPLOYERS

As you navigate these considerations and formulate the prediction goal in complete detail, you need help from across the enterprise. You can’t go it alone. Every semi-technical aspect that defines what you’re going to predict depends on pragmatic business considerations. For the resulting model to be operationally viable, you’ve got to pull together a multidisciplinary team.

By deeply collaborating, business experts and data scientists can hone down the prediction goal to one at the intersection of two sets of prediction objectives, those held by the business side and those offered by the tech side:

![](img/99a58a0ea5f8204f7fbf446f6593fd4f_105_0.png)

On the top, the range of conceivable prediction goals that could be valuable for the business is limited only by the imagination of your operations and marketing staff. They could find value in predicting all kinds of individual outcomes or behaviors, including who will crash their car, fall in love, default on a payment, quit their job, or commit fraud. The problem is, for a given company, only some of these ideas can be feasibly achieved with modeling—depending, for example, on how well it would need to predict and the availability of pertinent data.

The set on the bottom also contains many possibilities. Many things could be analytically predicted, since we have so much data recording so many different kinds of outcomes and behaviors. The problem is, many such ideas that sound appealing in the lab would never actually be used. Of the many outcomes that could be modeled, only a fraction will be business actionable. For example, a data scientist might turn out a model to target a direct marketing campaign, only to find that marketing managers prefer to contact their entire list without targeting any further. Just because the data scientist has created an effective model doesn’t mean the business is ready to act on it to drive decisions. All too often, a lack of management buy-in or unforeseen business constraints preclude model deployment. This is the main cause of today’s low ML deployment rate.

A shrewd business perspective navigates to a viable prediction goal within the intersection of these two sets—one that’s both achievable and usable. You must enlist the wisest operational experts to inform which predicted behaviors hold potential business value. Ultimately, the prediction goal, in full detail, requires insight and buy-in from your collaborators, including those who run the operations that will be affected and driven by model deployment, such as marketing staff, who must be willing to change their targeting accordingly.

By enlisting this hard-core, multidisciplinary collaboration, you’re breaking boundaries and engaging in a very rare sort of teamwork. You’re involving a larger group in the nitty-gritty, quasi-technical aspects of a prediction goal that has traditionally been below the radar for business stakeholders, such as:

- Whether to predict a final or intermediate outcome
- How far ahead to predict
- Who or what is being predicted—for which kind of customer or other organizational element each prediction will apply

With this sustained business-side involvement, the predictive scores output by your model will deliver the greatest impact. They will be aligned with business strategy and actionable within your company’s
