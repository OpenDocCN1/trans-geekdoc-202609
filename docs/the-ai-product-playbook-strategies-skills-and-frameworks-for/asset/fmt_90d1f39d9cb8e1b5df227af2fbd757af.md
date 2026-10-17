
# Model Drift

| Model Drift || A measure of how much a deployed models performance changes over time. || Calculated by comparing current model performance to the performance baseline. || Important to monitor the model after deployment and make sure that it remains useful and doesn't degrade. ||  |

| Mean Squared Error (MSE) || The average squared difference between the predicted and actual values. (For regression problems only). || ![StartFraction left-parenthesis upper S u m o f s q u a r e d e r r o r s right-parenthesis Over left-parenthesis upper N u m b e r o f d a t a p o i n t s right-parenthesis EndFraction](images/c09-disp-05.png)<math xmlns="http://www.w3.org/1998/Math/MathML"><mrow> <mfrac> <mrow> <mi mathvariant="normal">(Sum&#160;of&#160;squared&#160;errors)</mi> </mrow> <mrow> <mi mathvariant="normal">(Number&#160;of&#160;data&#160;points)</mi> </mrow> </mfrac> </mrow> </math>  

![upper M upper S upper E equals StartFraction 1 Over n EndFraction sigma-summation Underscript i equals 1 Overscript n Endscripts left-parenthesis upper Y Subscript i Baseline minus ModifyingAbove upper Y With Ì‚ Subscript i Baseline right-parenthesis squared](images/c09-disp-0001.png)<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><mrow> <mi>M</mi> <mi>S</mi> <mi>E</mi> <mo>=</mo> <mfrac> <mn>1</mn> <mi>n</mi> </mfrac> <mstyle displaystyle="true"><munderover> <mo>&#8721;</mo> <mrow> <mi>i</mi> <mo>=</mo> <mn>1</mn> </mrow> <mi>n</mi> </munderover> <mrow> <msup> <mrow> <mo stretchy="false">(</mo> <msub> <mi>Y</mi> <mi>i</mi> </msub> <mo>&#8722;</mo> <msub> <mrow> <mover accent="true"><mi>Y</mi> <mo stretchy="true">&#770;</mo> </mover> </mrow> <mi>i</mi> </msub> <mo stretchy="false">)</mo> </mrow> <mn>2</mn> </msup> </mrow> </mstyle> </mrow> </math>  || Used when you're predicting a continuous value (e.g., predicting house prices, forecasting sales). Penalizes larger errors more heavily. || Lower MSE is better. Gives you a sense of the magnitude of the errors. |

| Root Mean Squared Error (RMSE) || The square root of the MSE. (For regression problems only). || √MSE  

![upper R upper M upper S upper E equals StartRoot StartFraction sigma-summation Underscript i equals 1 Overscript upper N Endscripts double-vertical-bar upper Y Subscript i Baseline minus ModifyingAbove upper Y With Ì‚ Subscript i Baseline double-vertical-bar Superscript normal 2 Baseline Over upper N EndFraction EndRoot comma](images/c09-disp-0002.png)<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><mrow> <mi>R</mi> <mi>M</mi> <mi>S</mi> <mi>E</mi> <mo>=</mo> <msqrt> <mrow> <mfrac> <mrow> <msubsup> <mstyle mathsize="140" displaystyle="true"><mo>&#8721;</mo> </mstyle> <mrow> <mi>i</mi> <mo>=</mo> <mn>1</mn> </mrow> <mi>N</mi> </msubsup> <msup> <mrow> <mrow> <mo>&#8214;</mo> <mrow> <msub> <mi>Y</mi> <mi>i</mi> </msub> <mo>&#8722;</mo> <msub> <mrow> <mover accent="true"><mi>Y</mi> <mo stretchy="true">&#770;</mo> </mover> </mrow> <mi>i</mi> </msub> </mrow> <mo>&#8214;</mo> </mrow> </mrow> <mrow> <mi mathvariant="normal">&#8202;</mi> <mn>2</mn> </mrow> </msup> </mrow> <mi>N</mi> </mfrac> </mrow> </msqrt> <mo>,</mo> </mrow> </math>  || Same use case as MSE, but the result is in the same units as the target variable, making it more interpretable. || Easier to understand than MSE because it's in the same units as the thing you're predicting (e.g., dollars, inches, etc.). |

| Mean Absolute Error (MAE) || The average absolute difference between the predicted and actual values. (For regression problems only). || ![StartFraction left-parenthesis upper S u m o f s q u a r e d e r r o r s right-parenthesis Over left-parenthesis upper N u m b e r o f d a t a p o i n t s right-parenthesis EndFraction](images/c09-disp-05.png)<math xmlns="http://www.w3.org/1998/Math/MathML"><mrow> <mfrac> <mrow> <mi mathvariant="normal">(Sum&#160;of&#160;squared&#160;errors)</mi> </mrow> <mrow> <mi mathvariant="normal">(Number&#160;of&#160;data&#160;points)</mi> </mrow> </mfrac> </mrow> </math>  

![upper M upper A upper E equals StartFraction 1 Over n EndFraction sigma-summation Underscript i equals 1 Overscript n Endscripts StartAbsoluteValue upper Y Subscript i Baseline minus ModifyingAbove upper Y With Ì‚ Subscript i Baseline EndAbsoluteValue](images/c09-disp-0003.png)<math display="block" xmlns="http://www.w3.org/1998/Math/MathML"><mrow> <mi>M</mi> <mi>A</mi> <mi>E</mi> <mo>=</mo> <mfrac> <mn>1</mn> <mi>n</mi> </mfrac> <mstyle displaystyle="true"><munderover> <mo>&#8721;</mo> <mrow> <mi>i</mi> <mo>=</mo> <mn>1</mn> </mrow> <mi>n</mi> </munderover> <mrow> <mrow> <mo>|</mo> <mrow> <msub> <mi>Y</mi> <mi>i</mi> </msub> <mo>-</mo> <msub> <mrow> <mover accent="true"><mi>Y</mi> <mo stretchy="true">&#770;</mo> </mover> </mrow> <mi>i</mi> </msub> </mrow> <mo>|</mo> </mrow> </mrow> </mstyle> </mrow> </math>  || Used when you're predicting a continuous value, and you want a metric that's less sensitive to outliers than MSE/RMSE. || Less sensitive to extreme errors than MSE/RMSE. Gives you the average size of the error. |

(Note: `TP` = True Positive, `TN` = True Negative, `FP` = False Positive, `FN` = False Negative)

It's important to remember these are tools. And as a PM you should decide which tools are more important for your product. As an example:

*   **High Precision:** Important if the cost of a false positive is high (e.g., flagging a legitimate transaction as fraudulent).

*   **High Recall:** Important if the cost of a false negative is high (e.g., failing to detect a disease in a medical diagnosis).

*   **Low Latency:** Critical for real-time applications (e.g., self-driving cars, chatbots).

*   **High Throughput:** Needed if you are going to process a lot of requests.

This table provides a starting point. The specific metrics you choose will depend on the nature of your AI/ML application and your overall business goals. The next section will delve deeper into selecting the `right` metrics for your specific context. The key is to be able to have data-driven conversations with your team.

## Context Matters: Selecting the Right Metrics for Your AI/ML Application

Choosing the right metrics for your AI/ML project is like choosing the right instruments for a scientific experiment. You need to select the tools that will accurately measure the specific phenomena you're interested in. There's no one-size-fits-all answer; the `best` metrics depend heavily on the specific application, your business goals, and the potential costs of different types of errors. This is where your product judgment comes in.

This isn't just a technical exercise for the data science team. As a Product Manager, you need to be actively involved in selecting metrics because they define *success*. They determine how your AI-powered feature will be evaluated, and ultimately, whether it's considered a win or a loss.

Here's a step-by-step guide to help you navigate this critical process:

### 1. Define Your Business Goals (and Connect Them to User Needs):

**Start with the “why”:** Before you even think about metrics, clearly articulate the *business goals* of your AI/ML project. What problem are you trying to solve? What user need are you trying to address? How will this AI feature contribute to the overall product strategy?

*   **Be specific:** Avoid vague goals like “improve user engagement.” Instead, be specific: “Increase click-through rates on recommended articles by 15 percent,” or “Reduce customer support ticket resolution time by 20 percent.”

*   **Connect to user needs:** Always link your business goals back to user needs. For example, “Reduce customer support ticket resolution time” (business goal) translates to “Help users get their problems solved faster” (user need).

Mapping your business goals to specific user needs and potential AI applications is a critical first step. The following table provides a simple framework for this thought process.

| BUSINESS GOAL || USER NEED || POTENTIAL AI/ML APPLICATION |
