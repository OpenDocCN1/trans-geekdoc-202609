
## Independence Assertions

Independence assertions are usually based on knowledge of the domain. As the toothache–weather example illustrates, they can dramatically reduce the amount of information necessary to specify the full joint distribution. If the complete set of variables can be divided into independent subsets, then the full joint distribution can be factored into separate joint distributions on those subsets. For example, the full joint distribution on the outcome of `n` independent coin flips, `P(C1,..., Cn)`, has `2n` entries, but it can be represented as the product of `n` single-variable distributions `P(Ci)`. In a more practical vein, the independence of dentistry and meteorology is a good thing, because otherwise the practice of dentistry might require intimate knowledge of meteorology, and vice versa.

When they are available, then, independence assertions can help in reducing the size of the domain representation and the complexity of the inference problem. Unfortunately, clean separation of entire sets of variables by independence is quite rare. Whenever a connection, however indirect, exists between two variables, independence will fail to hold. Moreover, even independent subsets can be quite large—for example, dentistry might involve dozens of diseases and hundreds of symptoms, all of which are interrelated. To handle such problems, we need more subtle methods than the straightforward concept of independence.

## 12.5 Bayes’ Rule and Its Use

On [page 408](#Chapter12-02.xhtml#page_408), we defined the product rule ([Equation (12.4)](#Chapter12-02.xhtml#eq12-4)). It can actually be written in two forms:

$\begin{matrix} \left. P(a \land b) = P(a \middle| b)P(b) \right. & \text{and} & \left. P(a \land b) = P(b \middle| a)P(a). \right. \\ \end{matrix}$

Equating the two right-hand sides and dividing by `P(a)`, we get

$\begin{matrix} \left. P\text{(}b \middle| a\text{)~=}\frac{\left. P\text{(}a \middle| b\text{)}P\text{(}b\text{)} \right.}{P\text{(}a\text{)}}. \right. & {\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\text{(12}\text{.12)}} \\ \end{matrix}$

This equation is known as Bayes’ rule (also Bayes’ law or Bayes’ theorem). This simple equation underlies most modern AI systems for probabilistic inference.

<p class="sidebar">Bayes&#x0027; rule</p>

The more general case of Bayes’ rule for multivalued variables can be written in the `P` notation as follows:

$\left. \mathbf{P}\text{(}Y \middle| X\text{)~=}\frac{\left. \mathbf{P}\text{(}X \middle| Y\text{)~}\mathbf{P}(Y) \right.}{\mathbf{P}(X)}. \right.$

As before, this is to be taken as representing a set of equations, each dealing with specific values of the variables. We will also have occasion to use a more general version conditionalized on some background evidence `e`:

$\begin{matrix} \left. \mathbf{P}\text{(}Y \middle| X,\mathbf{e}\text{)~=}\frac{\left. \mathbf{P}\text{(}X \middle| Y,\mathbf{e}\text{)~}\mathbf{P}(Y \middle| \mathbf{e}) \right.}{\left. \mathbf{P}(X \middle| \mathbf{e}) \right.}.\\, \right. & {\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\text{(12}\text{.13)}} \\ \end{matrix}$

### 12.5.1 Applying Bayes’ rule: The simple case

On the surface, Bayes’ rule does not seem very useful. It allows us to compute the single term `P(b | a)` in terms of three terms: `P(a | b)`, `P(b)`, and `P(a)`. That seems like two steps backwards; but Bayes’ rule is useful in practice because there are many cases where we do have good probability estimates for these three numbers and need to compute the fourth. Often, we perceive as evidence the effect of some unknown cause and we would like to determine that cause. In that case, Bayes’ rule becomes

$\left. P(cause \middle| \ effect) = \frac{\left. P(effect \middle| cause)P(cause) \right.}{P(effect)}. \right.$

The conditional probability `P(effect | cause)` quantifies the relationship in the causal direction, whereas `P(cause | effect)` describes the diagnostic direction. In a task such as medical diagnosis, we often have conditional probabilities on causal relationships. The doctor knows `P(symptoms | disease)` and wants to derive a diagnosis, `P(disease | symptoms)`.

<p class="sidebar">Causal</p> <p class="sidebar">Diagnostic</p>

For example, a doctor knows that the disease meningitis causes a patient to have a stiff neck, say, 70% of the time. The doctor also knows some unconditional facts: the prior probability that any patient has meningitis is 1/50,000, and the prior probability that any patient has a stiff neck is 1%. Letting `s` be the proposition that the patient has a stiff neck and `m` be the proposition that the patient has meningitis, we have

$\begin{array}{l} \left. P\text{(}s \middle| m\text{)~=~0}\text{.7} \right. \\ {\,\\,\\,\\,\\, P\text{(}m\text{)~=~1}/\text{50000}} \\ {\,\\,\\,\\,\\,\\,\\, P\text{(}s\text{)~=~0.01}} \\ \left. P\text{(}m \middle| s\text{)~=}\\,\\frac{\left. P(s \middle| m)P(m) \right.}{P(s)} = \frac{\text{0}\text{.7} \times 1/\\text{50000}}{0.01} = 0.0014.\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,(12.14) \right. \\ \end{array}\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,$

That is, we expect only 0.14% of patients with a stiff neck to have meningitis. Notice that even though a stiff neck is quite strongly indicated by meningitis (with probability 0.7), the probability of meningitis in patients with stiff necks remains small. This is because the prior probability of stiff necks (from any cause) is much higher than the prior for meningitis.

[Section 12.3](#Chapter12-03.xhtml#sec12-3) illustrated a process by which one can avoid assessing the prior probability of the evidence (here, `P(s)`) by instead computing a posterior probability for each value of the query variable (here, `m` and `¬m`) and then normalizing the results. The same process can be applied when using Bayes’ rule. We have

`P(M|s)` = `α`⟨`P(s|m)P(m)`, `P(s|¬m)P(¬m)`⟩.

Thus, to use this approach we need to estimate `P(s| ¬m)` instead of `P(s)`. There is no free lunch—sometimes this is easier, sometimes it is harder. The general form of Bayes’ rule with normalization is

$\begin{matrix} \left. \mathbf{P}(Y \middle| X)\\ = \\alpha\mathbf{P}(X \middle| Y)\\mathbf{P}(Y), \right. & {\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\text{(12}\text{.15)}} \\ \end{matrix}$

where `α` is the normalization constant needed to make the entries in `P(Y | X)` sum to 1.

One obvious question to ask about Bayes’ rule is why one might have available the conditional probability in one direction, but not the other. In the meningitis domain, perhaps the doctor knows that a stiff neck implies meningitis in 1 out of 5000 cases; that is, the doctor has quantitative information in the diagnostic direction from symptoms to causes. Such a doctor has no need to use Bayes’ rule.

Unfortunately, diagnostic knowledge is often more fragile than causal knowledge. If there is a sudden epidemic of meningitis, the unconditional probability of meningitis, `P(m)`, will go up. The doctor who derived the diagnostic probability `P(m | s)` directly from statistical observation of patients before the epidemic will have no idea how to update the value, but the doctor who computes `P(m | s)` from the other three values will see that `P(m | s)` should go up proportionately with `P(m)`. Most important, the causal information `P(s | m)` is unaffected by the epidemic, because it simply reflects the way meningitis works. The use of this kind of direct causal or model-based knowledge provides the crucial robustness needed to make probabilistic systems feasible in the real world.

### 12.5.2 Using Bayes’ rule: Combining evidence
