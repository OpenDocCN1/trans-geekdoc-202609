
| Application and desired business outcome | What's predicted, i.e., detected (model output) | What's done about it (deployment) |
| :--- | :--- | :--- |
| Fraud detection to prevent more fraud | Is the transaction fraudulent? | Place a hold on high-risk transactions and/or send them to human auditors. |
| Healthcare diagnosis to improve treatment | Does the patient have the condition? | Flag the patient for additional tests to potentially confirm the diagnosis. |
| Spam filtering so you see less spam | Is the email message spam? | Relegate spam to a separate email folder. |
| Speech recognition to transcribe the spoken word | Is X the word that corresponds with the audio segment? | Label the segment with the word predicted as most likely. |
| Fault detection to decrease the number of broken items | Is the item faulty (e.g., as it rolls off a factory assembly line)? | Inspect items predicted as likely to be faulty. |
| Autonomous driving to lessen human workloads and improve safety | Is there a stop sign in the image? | Bring the vehicle to a stop when a stop sign is detected. |

There are many, many more ways to apply ML. Don't be afraid to invent a new one, according to the exact nature of your business and its main operations. Allow the wide range of established use cases to potentially inspire an original one. New ones crop up all the time. ML has been used to sort cucumbers, predict the outcome of construction projects, detect online trolls and sewage leaks, and catch scooters being illegally ridden on the sidewalk.

I would like to encourage you to also consider social-good applications that benefit society. For example, models can identify those most vulnerable or at risk in order to intervene. The nonprofit Predict Align Prevent applies ML to identify children at risk for maltreatment. The organization’s models improve early detection and intervention. As another example, the US Equal Employment Opportunity Commission predicts discrimination, flagging which groups of people in a specific industry are more susceptible. ML also serves as an important tool for climate technology by, for example, predicting the amount of carbon captured by reforestation and regenerative agriculture projects, predicting supply and demand for renewable energy and storage, and predicting extreme weather risks to real estate and crops (the conference series I founded includes an offshoot focused on this, Predictive Analytics World for Climate Technology).

By deciding on an ML application, you’ve established your deployment goal. Now all you’ve got to do is sell it.

## Getting the Green Light

This book ends with the project’s beginning—the conclusion guides you on how to pitch ML projects. But for now, let’s wrap up step 1 with how UPS and EduPay gained traction for their respective use cases.

When Jack Levis wanted to optimize UPS delivery routes, he had a lot of convincing to do. “The calls I got were incredible. ‘It’s time to stop this. No computer can tell a professional a better way to deliver. You’ve gotta get your head out of the clouds.’”

But Jack had an ace up his sleeve: He was selling potential gains, not just cool technology. And he knew that the key to convincing was disclosing the details of the intended deployment and even demonstrating it in action—literally, as when he took the executive Chuck on that fateful ride.

Jack also knew to enlist while he convinced. As an ML project progresses, selling and educating evolve into collaborating. The stakeholders and line-of-business managers should transform from skeptics to key team members. They run the operations, so they should help inform the changes to those operations. You can’t hash out a fully detailed deployment plan without them. As you indoctrinate, also recruit.

In contrast, when it came to selling operational change, EduPay was at a disadvantage: They had me rather than Jack Levis. I had emerged from academia in love with the tech. And even after the disappointment of the gay.com project, I hadn’t yet learned the lesson: The deployment plan must be sold first.

Fortunately, I wasn't in charge. I was serving as the data scientist, not the project leader. EduPay had come to me with a specific deployment plan already in mind. My job was to devise a technical approach to modeling. I didn't have to sell EduPay on operational change. The company was already set to do so.

The project leader, Melissa, had the wind at her back. After conceiving this project, her brainchild, she'd already secured the approval of her superiors to implement her vision. This has gone smoothly. EduPay was a small company and Melissa had a great deal of autonomy in her ownership of the ad system. Moreover, the change she proposed was relatively incremental: Instead of automating ad-selection decisions for the first time, her goal was merely to change how those automatic decisions were being made. EduPay's system was already selecting which ad to display, based mostly on each ad's overall popularity—now we were going to change it to select which ad to display for each individual user.

## Next Steps

But even with a path to deployment relatively unobstructed, I wasn't ready to train any models for EduPay just yet. Deciding on the value proposition—what's predicted and what's done about it—is only the first pre-production planning step. The next step is to get more specific about what the model will predict—a lot more specific.

As we'll see over the course of the remaining chapters, there was still much to learn from the EduPay project. We may not all be natural-born ML leaders like Jack Levis, but we can learn to do it right.

## 2 Target

### Establish the Prediction Goal

As we discussed in the previous chapter, to plan for machine learning deployment, you must begin by establishing what will be predicted by the model and what will be done about each prediction. In this chapter's step, you more fully define the first of these two, the prediction goal. It must be specified in great detail.

Welcome to a key intersection between tech and biz, where business pragmatics inform the semi-technical details and where business stakeholders must delve into these details. Your mission, should you choose to accept it, is to forge a rare collaboration, enlisting business leaders to weigh in on the caveats and qualifications that determine the prediction goal in all its detailed glory. If you succeed, you will have translated a broadly defined business intention into a well-defined requirement for technical execution.

### The BizML Practice:

- 1. Value: Establish the deployment goal.
- 2. Target: Establish the prediction goal.
- 3. Performance: Establish the evaluation metrics.
- 4. Fuel: Prepare the data.
- 5. Algorithm: Train the model.
- 6. Launch: Deploy the model.

Jack Levis doesn’t remember the exact moment of epiphany when delivery prediction came to him. It’s the kind of great idea that just seems like a given once it’s on the table. But before anyone had conceived of it, UPS couldn’t fully optimize. Recall how Jack formulated the paradox that had been holding the company back:

**The Delivery Paradox:** You can’t optimally plan the truck-loading until you know all the deliveries that will need to be made. But by the time you know all the deliveries, you’ve run out of time to load the trucks.

You can only predict your way out of a paradox like this. The same kind of conundrum arises for optimizing all kinds of logistics, whether you’re carpooling a bunch of kids, any one of whom may call in sick at the last minute; you’re casting big stars in a movie, any one of whom could surprisingly say yes just after you’ve offered the role to someone less famous; or you’re accepting a new consulting client, even though you know that a bigger client opportunity could come tomorrow. But these operations are too small for machine learning. Let’s be real: Your kid’s carpool probably wouldn’t benefit.

When applied to large operations, predictions help, even without unrealistic expectations as to their precision. When UPS predicts a delivery, it’s presumed without being presumptuous. It’s only tentatively treated as a given—just for the purposes of loading the trucks. By the time the trucks roll out, all the packages have become real—they’ve arrived at the shipping center and wound up on a truck. Any predictions that didn’t materialize are discarded.

With such a well-conceived scheme—powerful yet prudent—you might expect Jack to have triggered the ML project ASAP. After all, the prediction goal appears clear and simple: *Predict which addresses will receive a UPS delivery tomorrow.* So crank up the predictive engine and pour in the data.

Not so fast. Jack knew that the devil lurked in the details. Should the model predict which building would receive a package or should it be more granular, predicting for individual apartments or business
