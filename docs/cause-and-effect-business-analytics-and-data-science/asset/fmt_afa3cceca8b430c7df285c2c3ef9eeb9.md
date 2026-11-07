
We would like to emphasize that for all `CB-SEMs`, a model is needed. It could be specified *a priori*, based on theory, or developed based on the preliminary construction of a `DAG` from data – see [Chapter 5](#chapter5.xhtml) for details – or by using a combination of these two approaches. But in a process that parallels factor analysis, it is also possible to estimate a more “exploratory” `SEM`, which is generally done using the partial least squares algorithm (see, e.g., [Tenenhaus et al. 2005](#chapter11.xhtml#ref11_16)). We return to this issue below, after first giving another illustration of a `CB-SEM`, also developed in a marketing context.

## 11.5 The Covariance Approach: An Example

In order to illustrate more completely the covariance approach to the estimation of `SEMs`, we draw on an example by [Vij and Farooq (2014)](#chapter11.xhtml#ref11_17) in which the authors investigate the impact of Knowledge Orientation (`KSO`) on performance for different manufacturing and service organizations in the National Capital Region, India. This example is typical of a very large number of such models used in several areas of business studies, notably marketing and information systems.

The data were obtained from 240 questionnaires returned by managerial-level employees. Variables (on a scale of 1–5) are listed in [Table 11.2](#chapter11.xhtml#tbl11_2). The authors identified and validated via a confirmatory factor analysis four factors to represent `KSO`: Idea Sharing Propensity (`ISP`), Good Organizational Climate (`GOC`), Top Management Support (`TMS`), and Knowledge Sharing Culture (`KSC`). In the same fashion, three factors found to represent performance are Satisfaction relative to Major Competitor (`PER_SAT`), Profitability relative to Major Competitor (`PER_PRO`), and Innovativeness Relative to Major Competitor (`PER_INN`). The authors propose and then validate an `SEM`, shown for large organizations (with more than 250 employees) in [Figure 11.8](#chapter11.xhtml#fig11_8); as usual, the manifest variables are shown in boxes and the latent variables (including the `e[i]` error terms) in ovals. The numbers show the path coefficients, which measure the linear association between the variables. The model extracts a single constructed `KSO` from its four factors and a single constructed Performance Relative to Major Competitor (`PER_COM`) from its three factors and then examines the relationship between `KSO` and `PER_COM`.

Table 11.2 Variables for the `KSO` Example [⏎](#chapter11.xhtml#b11tbl11_2)

| Code || Questionnaire Statement (1. Strongly Disagree – 5. Strongly Agree) |
| --- | --- |
| `S1` || A climate of openness and trust permeates my organization. |
| --- | --- |
| `S2` || In our organization, everyone speaks up if they have an opinion or idea to offer. |
| `S3` || We do not share ideas with other people of similar interest, especially when they are based in different departments. |
| `S4` || Knowledge-sharing behavior is built into the performance appraisal system in my organization. |
| `S5` || Our company culture welcomes debates and stimulates discussions. |
| `S6` || In our organization, we are rewarded for sharing knowledge with our colleagues. |
| `S7` || There is no restriction on employees if they want to talk to anyone in the organization, including top management. |
| `S8` || In my organization, relatively more-committed employees are more willing to share their learning and experiences with others. |
| `S9` || Top managers provide most of the necessary help and resources to enable employees to share knowledge. |
| `S10` || My organization's culture encourages and facilitates knowledge sharing. |
| `S11` || Top managers do not support and encourage employees to share their knowledge with colleagues. |
| Code || Compared to the major competitor in your industry, in the last three years, how has your business performed on the following parameters? |
| `CC1` || Sales Growth |
| `CC2` || Return on Investment |
| `CC3` || Market Share |
| `CC4` || Service Quality |
| `CC5` || Customer Satisfaction |
| `CC6` || Employee Satisfaction |
| `CC7` || Employee Turnover |
| `CC8` || Product Innovation |
| `CC9` || Process Innovation |
| `CC10` || Product Quality |

![Figure 11.8 Covariance-based structural equations model of KSO (knowledge sharing orientation and performance). (From Vij and Farooq 2014, Figure 2.) ⏎](images/fig11_8.jpg)

Figure 11.8 Covariance-based structural equations model of `KSO` (knowledge sharing orientation and performance). (From [Vij and Farooq 2014](#chapter11.xhtml#ref11_17), Figure 2.) [⏎](#chapter11.xhtml#b11fig11_8)

This study finds that `KSO` has a positive impact on performance and that this impact depends on the size of the organization. Indeed, the significant Page 318standardized coefficient for `KSO` to `PER_COM` is 0.742 for large organizations (more than 250 employees). For smaller organizations, this coefficient is 0.678. In such cases, the size of the organization is said to be a moderator for the relationship between `KSO` and `PER_COM`. In statistical terms, we might say that size interacts with `KSO` in its relationship with `PER_COM`. On the other hand, the relationship between `KSO` and `PER_COM` does not depend on industry (manufacturing versus services).Page 319

Page 320

## 11.6 The Partial Least Squares Approach

The traditional approach to `SEM` is often referred to as covariance-based `SEM` (`CB-SEM`) because the model can be optimized and solved based just on the covariances among the manifest variables, provided one is willing to assume that the underlying variables are normally distributed. This in turn allows one to test theories and to use standard tools of statistical inference, since “the objective in using \[CB-\]-SEM is to determine whether the a priori model is valid, rather than to ‘find’ a suitable model” ([Shah and Goldstein 2005](#chapter11.xhtml#ref11_14), p. 149). The downside is that normality may be an unrealistic assumption, the system may not solve satisfactorily, and relatively large samples are usually needed.

An alternative approach is to relax the assumption of normality. On the surface, the model looks just the same, but underneath it is quite different. A new solution algorithm is needed because the optimization associated with `CB-SEM` is no longer possible. In most cases, the relationships in the structural (inner) model are now estimated using ordinary least squares, which is why this approach is called partial least squares `SEM` (`PLS-SEM`). This flexibility allows one to estimate more complex models, but it comes at a cost: `PLS-SEM` models may be used for prediction and exploration, but not for testing whether a theory holds or not, or for judging causal effects.

[Hair et al. (2021)](#chapter11.xhtml#ref11_7) argue that the strength of `PL-SEM` is that its “statistical properties provide very robust model estimations with data that have normal as well as extremely non-normal distributional properties” (p. 14).

`PLS-SEM` models have become popular in management, especially since about 2000 (see [Sarstedt et al. 2014](#chapter11.xhtml#ref11_13), Figure 2). [Table 11.3](#chapter11.xhtml#tbl11_3) shows that `PLS-SEM` models have, on average, more latent variables and almost twice as many Page 321measured (manifest) variables as conventional `CB-SEM` models. For instance, [Eberl (2010)](#chapter11.xhtml#ref11_4) uses a `PLS-SEM` model to untangle the effect of corporate reputation (separated into “competence” and “likeability”) on customer satisfaction and hence loyalty.

Table 11.3 Comparison of Model Size, `CB-SEM` versus `PLS-SEM`, in Operations Research and Market Research [⏎](#chapter11.xhtml#b11tbl11_3)

|  || `CB-SEM` || `PLS-SEM` |
| --- | --- | --- |
|  || Per Model |
| Number of indicators (manifest variables) ||  16.3 ||  29.6 |
| --- | --- | --- |
| Number of latent variables ||   4.7 ||   7.9 |
| Number of observations || 246 || 211 |
| Number of parameters ||  37.5 ||  |
