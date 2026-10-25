# The Difference between ML Failure and Success

It turns out that it's easy to mess this up, failing to align the prediction goal with how predictions will be operationalized. Since this is only step 2, such misalignments throw off the project early on. Defining the prediction goal marks a crucial turning point that all ML projects hit soon after their conception. Many projects get it wrong—they neglect to scrupulously flesh out the prediction goal before jumping into the analysis. This is a deadly error, usually resulting in a model that's embalmed rather than embraced. So properly defining the prediction goal is your chance to shine—not by flaunting advanced methods but by exercising restraint and meticulousness.

Let's revisit the classic marketing application, response modeling. It aims to increase profit by targeting marketing. Here's how we described it in the previous chapter:

| Application and desired business outcome | What's predicted (model output) | What's done about it (deployment) |
|---|---|---|
| Response modeling to increase the marketing response rate | Will the customer buy if contacted? | Mail a brochure to those likely to buy. |

As we see here once again, each ML application is defined by *what's predicted* and *what's done about it*. In this bizML step, we're defining the prediction goal—the “what's predicted” part. In a later step, data preparation will use that prediction goal to populate a column of data, which is known to data scientists as the *dependent variable* and in this book is called the *output variable*. With this column in place, the overall dataset is referred to as *labeled* or *supervised* data. After preparing it, an ML algorithm will use the data to train a model that predicts as well as possible. With the current step, we are defining the goal for that predictive model.

The prediction goal has got to be more specific. We must fully define it, in all its detailed glory. For most any response modeling project,