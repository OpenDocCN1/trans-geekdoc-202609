
## 11.2 Model Structure

Here we have “error” terms associated with each variable. We have also added curved lines; when they are present, they indicate that we are allowing Page 310correlations among the variables. The model in [Figure 11.2](#chapter11.xhtml#fig11_2) has no structure and may be written as:

`Y[1] = α[1] + β[12]Y[2] + β[13]Y[3] + ε[1]`

`Y[2] = α[2] + β[21]Y[1] + β[23]Y[3] + ε[2]`

`Y[3] = α[3] + β[31]Y[1] + β[32]Y[2] + ε[3]`

`cov(ε[i]ε[j]) ≠ 0, ∀ i, j.`

This model is not identifiable – we cannot estimate the coefficients uniquely – and so we need to impose some structure in order to progress. Often, we do this withouts on a five-point Likert scale, may be thought of as measuring different dimensions of job satisfaction. Denote the responses to these questions by `X[1]`, `X[2]`, and `X[3]`. Then we may graph this as:

Note the direction of the causal paths here: Job satisfaction leads to the responses to the questions. It is not the answers to the questions that cause job satisfaction; instead, they measure it. That is why the model in [Figure 11.4](#chapter11.xhtml#fig11_4) Page 312is a *measurement model*, and it is an integral part of almost every SEM. In the terminology of SEMs, `Z[1]` is a *reflective* latent variable. Formally,

![Figure 11.4 Path diagram with latent variables. ⏎](images/fig11_4.jpg)

Figure 11.4 Path diagram with latent variables. [⏎](#chapter11.xhtml#b11fig11_4)

`X[i] = α[0i] + α[1i] Z[1] + ε[i], i = 1, 2, 3, E(ε[i]) = 0, cov(Z[1]ε[i]) = 0,`

and the challenge is to find the `α`'s that link the latent `Z[1]` to the observable `X[i]`'s. This is discussed in more detail below.

Schematically, our SEM may be represented as in [Figure 11.5](#chapter11.xhtml#fig11_5), simplified only inasmuch as it excludes error terms and correlations among variables. The structural (inner) model is shown in the middle and consists of hypothesized causal relations among the latent variables. Here `Z[1]` and `Z[2]` are exogenous latent variables, but `Z[3]` is an endogenous latent variable because it is determined within the structural model. Note too that the model is recursive, flowing in a single direction; there must be a (hypothesized) causal chain, without any feedback loops. Broadly, we have for the structural model:

![Figure 11.5 Typical basic structural equation model for job performance. (Note: The model for “job satisfaction” is the same as in Figure 11.4. For simplicity, the error terms have been omitted here. Created by authors, inspired by Figure 1 in Sarstedt et al. 2014.) ⏎](images/fig11_5.jpg)

Figure 11.5 Typical basic structural equation model for job performance. (*Note:* The model for “job satisfaction” is the same as in [Figure 11.4](#chapter11.xhtml#fig11_4). For simplicity, the error terms have been omitted here. Created by authors, inspired by Figure 1 in [Sarstedt et al. 2014](#chapter11.xhtml#ref11_13).) [⏎](#chapter11.xhtml#b11fig11_5)

$$Z\_{i} = ~\\beta\_{i0} + ~{\\sum\\limits\_{j}{\\beta\_{ij}~Z\_{j} + ~v\_{i}}},~i = 1,2,3,~E\\left( v\_{i} \\right) = 0.$$

The outer model in [Figure 11.5](#chapter11.xhtml#fig11_5) is concerned with the determinants of the latent variables. Here `Z[1]` (job satisfaction) is a reflective measurement (or Mode A) model. For purposes of illustration, we have defined `Z[2]` (work incentives) Page 313to be a *formative* latent variable, giving a Mode B model. Here the arrows go from the manifest variables (`X[4]`, `X[5]`, `X[6]`) to `Z[2]`. The idea here is that a higher salary is not a reflection of work incentives; it *is* a work incentive, and indeed the work incentives variable (`Z[2]`) is formed by its components. Formally:

`Z[2] = β[20] + β[24] X[4] + β[25] X[5] + β[26] X[6] + δ, E(δ) = 0, cov(δ, X[i]) = 0.`

Here too there is the challenge of finding the appropriate coefficients (the `β`'s), but this is not so much a measurement model as a definitional model. Usually, CB-SEM models cannot easily accommodate formative latent variables, but PLS-SEM can.

To give a better feel for how the measurement models in an SEM may be estimated – for instance, to create the weights that we need to put on the paths from `X[1]`, `X[2]`, and `X[3]` to `Z[1]` – it is helpful to take a short detour to discuss factor analysis. While the algorithms that estimate SEMs will generate these path coefficients, the procedure is very close to that used by factor analysis, and an understanding of how factor analysis works helps us to appreciate the mechanisms behind SEMs.

## 11.3 A Short Detour: Factor Analysis

Consider a teacher who, at the end of every semester, asks every student to complete a course evaluation questionnaire covering perhaps 20 questions related to their experience with the course and teacher. Typical questions include the following.

On a scale of 1 (not at all) to 5 (very much):

| The teacher: || || || || || |

| --- | --- | --- | --- | --- | --- |

| Was well organized || 1 || 2 || 3 || 4 || 5 |

| --- | --- | --- | --- | --- | --- |

| Arrived in class on time || 1 || 2 || 3 || 4 || 5 |

| Explained things clearly || 1 || 2 || 3 || 4 || 5 |

| Showed enthusiasm for the subject || 1 || 2 || 3 || 4 || 5 |

| Was knowledgeable about the subject || 1 || 2 || 3 || 4 || 5 |

Some of the questions are largely redundant – the answers are essentially the same as the answers to other questions – while a few of the questions are informative on their own. Therefore, it might be helpful to reduce the many answers to just a few *factors*.
