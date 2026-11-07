
### 5. Amount Spent
While a purchase is good, there are differences between high-amount and low-amount sales. Measuring and modeling the amount spent is another common business activity. Similarly, one can translate sales amount to revenue as a common financial metric or Cost per Revenue as an efficiency measure. As in #4, one can measure Cost per Incremental Revenue using the revenue lift metric as the denominator.

### 6. Retention Rate
While purchase is relevant to acquiring new customers or cross-selling additional products to existing customers, retaining customers is another key marketing metric. Depending on your product or service, retention can be a binary metric (retained or not) or a continuous metric (value retention, e.g., usage of a credit card or balance of a bank account).

### 7. Net Revenue
While having a high sales amount or revenue is good, it is more important to check if it exceeds the marketing expense, whether for the entire marketing campaign, a specific segment, or a particular customer. Subtracting the marketing expense from the revenue is the net revenue metric that is commonly reported and analyzed.

### 8. Return on Investment (ROI)
This is simply Net Revenue (revenue minus marketing expense, also known as Return), divided by marketing expense, which can be measured for the entire campaign, a specific segment, or a particular individual. Again, like other metrics, one can compute the baseline ROI, but it is often more useful to compute Incremental ROI (or Lift in ROI), where the latter is the lift in return (return caused by a treatment) divided by the expense associated with the treatment. The Incremental ROI is also known as Marketing ROI; see [Lenskold (2003)](#chapter7.xhtml#ref7_24) for some examples.

### 9. Lifetime Value (LTV)
While net revenue measures the immediate return of a marketing campaign, LTV (sometimes known as Long Term Value or Customer Lifetime Value, CLV) measures the sum of expected immediate and future values from a customer through the Expected Net Present Value (NPV) formula, typically discounted by estimated future attrition rate (in addition to the usual NPV discount rate). A general LTV formula is, with time `t` being discrete (say, year):

$${LTV}\_{i} = {\\sum\\limits\_{t = 0}^{\\infty}\\frac{{Return}\_{i}\\left( t \\right){~S}\_{i}\\left( t \\right)}{\\left( {1 + r} \\right)^{t}}}~ = {\\sum\\limits\_{t = 0}^{\\infty}\\frac{\\left( Revenue \\right.\_{i}\\left( t \\right){- {Expense}\_{i}\\left( t \\right))~S}\_{i}\\left( t \\right)}{\\left( {1 + r} \\right)^{t}}},~$$

(7.9)

where `r` is the discount rate or hurdle rate in a typical NPV calculation, representing a discount of future values,

`S[i](t)` = Probability of surviving at least to time (year) `t`

$$= \\left( {1 - A\_{i}\\left( 1 \\right)} \\right)\\left( {1 - A\_{i}\\left( 2 \\right)} \\right)\\ldots.\\left( {1 - A\_{i}\\left( {t - 1} \\right)} \\right) = ~{\\prod\\limits\_{k = 1}^{t - 1}\\left( {1 - A\_{i}\\left( k \\right)} \\right)},$$

`A[i](k)` = Attrition rate of individual `i` in year `k`, assuming `S[i](0)` = 1.

In practice, the upper time limit of Eqn. (7.9) is a finite value < ∞, as the value inside the summation approaches zero when `t` gets very large. Additionally, in industries where some kind of risk is considered, the LTV can be further discounted by risk.

While LTV is quite commonly used as a decision metric to establish how much a company should spend on a customer (or a segment) or to help determine the long-term effects of marketing treatments, it is typically not a metric for predictive modeling (as it is not observable and requires many assumptions). Rather, it takes model scores as an input to LTV calculations, as seen in Eqn. (7.9), where the revenue component `Revenue[i](t)` and survival probability `S[i](t)` are typically predicted by models. See [Roberts and Berger (1999)](#chapter7.xhtml#ref7_34) for computations and applications, as well as [Rosset et al. (2003)](#chapter7.xhtml#ref7_35), [Fader et al. (2005)](#chapter7.xhtml#ref7_10), and [Ansari et al. (2008)](#chapter7.xhtml#ref7_2) for alternative methods of computations and applications. While LTV is a good long-term metric for an individual customer or a segment, for treatment prioritization there is a concept called Incremental LTV where the value is driven by a specific treatment, similar to Incremental ROI or Marketing ROI discussed above. The incremental LTV calculation can be accomplished by replacing `Revenue[i](t)` by lift in revenue for a revenue-generating campaign or by replacing `S[i](t)` by lift in survival probability for a retention campaign.

While measurement can include many or all these metrics, as many of them are relatively straightforward to calculate, usually only a couple of them are used for predictive modeling or uplift modeling, given the high time and resource requirement for modeling. Typically, metrics closer to the ultimate goal or action, such as purchase, retention, and amount spent, are used for modeling. When data quantities are insufficient, one would use metrics closer to desire or awareness for modeling, for example, click-through and inquiry. Metrics such as ROI and LTV are typically used for decision-making, such as prioritization of customers for service or prioritization of treatments for customers. As a quick guideline, [Table 7.20](#chapter7.xhtml#tbl7_20) summarizes these metrics and their typical usage for measurement, predictive modeling, or as derived metrics for decision-making.

Table 7.20 List of Metrics and Their Usage [⏎](#chapter7.xhtml#b7tbl7_20)

| Baseline Metric || Lift Metric || Standard Measurement || Potential for Predictive Modeling || Derived Metric for Decision-Making |
| --- | --- | --- | --- | --- |
| Email Open Rate || Incremental (or Lift in) Email Open Rate || ✓ || ✓ ||  |
| --- | --- | --- | --- | --- |
| Inquiry or Visit Rate || Incremental (or Lift in) Inquiry or Visit Rate || ✓ || ✓ ||  |
| Click-through Rate || Incremental (or Lift in) Click-through Rate || ✓ || ✓ ||  |
| Purchase (or Conversion) Rate || Incremental (or Lift in) Purchase (or Conversion) Rate || ✓ || ✓ ||  |
| Amount Spent || Incremental (or Lift in) Amount Spent || ✓ || ✓ ||  |
| Retention Rate || Incremental (or Lift in) Retention Rate || ✓ || ✓ ||  |
| Net Revenue || Lift in Net Revenue ||  ||  || ✓ |
| Return On Investment (ROI) || Marketing (or Incremental) ROI ||  ||  || ✓ |
| Lifetime Value (LTV) || Incremental LTV ||  ||  || ✓ |

## 7.4 Opportunities for Continuous Improvement

While some previous sections focus on the mechanics of experimental design, this section discusses the opportunities to keep improving experiments, which ultimately improves response rates.

After the campaign with the chosen design is executed, response data are collected, models are developed, and attribute combinations that appear to have achieved the best outcome (highest response, highest revenue, etc.) are identified,
