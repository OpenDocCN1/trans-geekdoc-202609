
Now consider a slightly different problem: treating a diabetic patient. As in the case of car repair, we have evidence such as recent insulin doses, food intake, blood sugar measurements, and other physical signs. The task is to assess the current state of the patient, including the actual blood sugar level and insulin level. Given this information, we can make a decision about the patient’s food intake and insulin dose. Unlike the case of car repair, here the dynamic aspects of the problem are essential. Blood sugar levels and measurements thereof can change rapidly over time, depending on recent food intake and insulin doses, metabolic activity, the time of day, and so on. To assess the current state from the history of evidence and to predict the outcomes of treatment actions, we must model these changes.

The same considerations arise in many other contexts, such as tracking the location of a robot, tracking the economic activity of a nation, and making sense of a spoken or written sequence of words. How can dynamic situations like these be modeled?

## 14.1.1 States and observations

This chapter discusses discrete-time models, in which the world is viewed as a series of snapshots or time slices.[1](#Chapter14-07.xhtml#sup14-1) We’ll just number the time slices 0, 1, 2, and so on, rather than assigning specific times to them. Typically, the time interval ∆ between slices is assumed to be the same for every interval. For any particular application, a specific value of ∆ has to be chosen. Sometimes this is dictated by the sensor; for example, a video camera might supply images at intervals of 1/30 of a second. In other cases, the interval is dictated by the typical rates of change of the relevant variables; for example, in the case of blood glucose monitoring, things can change significantly in the course of ten minutes, so a one-minute interval might be appropriate. On the other hand, in modeling continental drift over geological time, an interval of a million years might be fine.

*Discrete time* *Time slice*

Each time slice in a discrete-time probability model contains a set of random variables, some observable and some not. For simplicity, we will assume that the same subset of variables is observable in each time slice (although this is not strictly necessary in anything that follows). We will use `Xt` to denote the set of state variables at time `t`, which are assumed to be unobservable, and `Et` to denote the set of observable evidence variables. The observation at time `t` is `Et = et` for some set of values `et`.

Consider the following example: You are the security guard stationed at a secret underground installation. You want to know whether it’s raining today, but your only access to the outside world occurs each morning when you see the director coming in with, or without, an umbrella. For each day `t`, the set `E[t]` thus contains a single evidence variable `Umbrellat` or `Ut` for short (whether the umbrella appears), and the set `Xt` contains a single state variable `Raint` or `Rt` for short (whether it is raining). Other problems can involve larger sets of variables. In the diabetes example, the evidence variables might be `MeasuredBloodSugar[t]` and `PulseRate[t]` while the state variables might include `BloodSugar[t]` and `StomachContents[t]`. (Notice that `BloodSugar[t]` and `MeasuredBloodSugar[t]` are not the same variable; this is how we deal with noisy measurements of actual quantities.)

We will assume that the state sequence starts at `t = 0` and evidence starts arriving at `t = 1`. Hence, our umbrella world is represented by state variables `R0`, `R1`, `R2`,... and evidence variables `U1`, `U2`,.... We will use the notation `a:b` to denote the sequence of integers from `a` to `b` inclusive and the notation `X[a:b]` to denote the set of variables from `X[a]` to `X[b]` inclusive. For example, `U[1:3]` corresponds to `U1`, `U2`, `U3`. (Note that this is different from the notation used in programming languages such as Python and Go, where `U[1:3]` would not include `U[3]`.)

## 14.1.2 Transition and sensor models

With the set of state and evidence variables for a given problem decided on, the next step is to specify how the world evolves (the transition model) and how the evidence variables get their values (the sensor model).

The transition model specifies the probability distribution over the latest state variables, given the previous values, that is, `P(X[t] | X0:t–1)`. Now we face a problem: the set `X0:t–1` is unbounded in size as `t` increases. We solve the problem by making a Markov assumption— that the current state depends on only a finite fixed number of previous states. Processes satisfying this assumption were first studied in depth by the statistician Andrei Markov (1856— 1922) and are called Markov processes or Markov chains. They come in various flavors; the simplest is the first-order Markov process, in which the current state depends only on the previous state and not on any earlier states. In other words, a state provides enough information to make the future conditionally independent of the past, and we have

*Markov assumption* *Markov process* *First-order Markov process*

$\\begin{matrix} \\left. \\mathbf{P}(\\mathbf{X}\_{t} \\middle| \\mathbf{X}\_{0}{}\_{:t - 1})\\ = \\ \\mathbf{P}(\\mathbf{X}\_{t} \\middle| \\mathbf{X}\_{t - 1}). \\right. & {\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\text{(14}\\text{.1)}} \\\\ \\end{matrix}$

Hence, in a first-order Markov process, the transition model is the conditional distribution `P(Xt | X[t–1])`. The transition model for a second-order Markov process is the conditional distribution `P(X[t] | X[t−2],X[t−1])`. [Figure 14.1](#Chapter14-01.xhtml#fig14-1) shows the Bayesian network structures corresponding to first-order and second-order Markov processes.

Description

The states are depicted by elliptical nodes. Both parts have five states with variables labeled as follows from states 1 to 5. X subscript t minus 2, X subscript t minus 1, X subscript t, X subscript t plus 1, X subscript t plus 2. Part (“a”): An arrow from the end of each state points to its successive state. An input arrow from the space point toward the first state. Part (b): An input arrow points horizontally toward the first state. An arrow from the end of each state points to the successive state. An arrow from the space point toward the second state is labeled X subscript t minus 1. An arrow from each state points to its alternate state. An arrow from the fourth state labeled X subscript t plus 1 point outward.

×![](images/Fig-191.jpg)

Figure 14.1(a) Bayesian network structure corresponding to a first-order Markov process with state defined by the variables `Xt`. (b) A second-order Markov process.

Even with the Markov assumption there is still a problem: there are infinitely many possible values of `t`. Do we need to specify a different distribution for each time step? We avoid this problem by assuming that changes in the world state are caused by a time-homogeneous process—that is, a process of change that is governed by laws that do not themselves change over time. In the umbrella world, then, the conditional probability of rain, `P(R[t] | R[t−1])`, is the same for all `t`, and we need specify only one conditional probability table.

*Time-homogeneous*

Now for the sensor model. The evidence variables `Et` could depend on previous variables as well as the current state variables, but any state that’s worth its salt should suffice to generate the current sensor values. Thus, we make a sensor Markov assumption as follows:

*Sensor Markov assumption*

$\\begin{matrix} \\left. \\mathbf{P}(\\mathbf{E}\_{t} \\middle| \\mathbf{X}\_{0:t},\\mathbf{E}\_{1}{}\_{:t - 1})\\ = \\ \\mathbf{P}(\\mathbf{E}\_{t} \\middle| \\mathbf{X}\_{t}). \\right. & {\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\text{(14}\\text{.2)}} \\\\ \\end{matrix}$
