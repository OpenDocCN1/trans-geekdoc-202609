Given the clear benefit of achieving a certain lift, let’s define it properly:

**Lift:** A multiplier: How many times more often positive cases appear within a group identified by a predictive model, in comparison with how often they appear in general.

Lift captures the multiplicative improvement to operations, the increased return for your efforts, how much more bang you get for your buck. With a lift of three, marketing to the targeted group will be three times as effective. Auditing the flagged group of transactions will find three times as much fraud. Examining the demarcated patients will find three times as many positive diagnoses. In this way, lift quantifies a model’s contribution, even for models that aren’t highly confident or anywhere in the vicinity of a magic crystal ball.

Lift reflects a limitation intrinsic to every model: It predicts less confidently as you target larger groups. The more cases it predicts as positive, the lower the lift will tend to be. Lift is always measured in relation to the group that’s been targeted by the model. In the response modeling example, the model achieved a lift of three for one quarter of the overall population—the 25 percent predicted most likely to buy. If you went further and took one half, the 50 percent predicted most likely to buy, the lift would be lower since this group includes individuals who didn’t make the top 25 percent.

Alternatively, the model could achieve a higher lift if it were used to identify a smaller, more select portion of the population. For example, a model might achieve a lift of 20 for the top 1 percent of the population. But there’s a downside to targeting only such a small group: In exchange for more confident predictions, you end up with a much smaller pool of prospects—for marketing, this means a smaller number of potential buyers to market to.

# **Even a Little Lift Helps a Lot**

Sometimes it makes sense to target a larger group despite that meaning a lower lift. Let’s turn to credit scoring, where the model predicts