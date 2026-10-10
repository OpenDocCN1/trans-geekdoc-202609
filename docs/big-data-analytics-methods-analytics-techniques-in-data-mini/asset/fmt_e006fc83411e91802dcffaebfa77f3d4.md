
The properties of an appropriate mathematical model for analytics include: accuracy, prediction, economy, well-posedness and utility (Smye and Clayton 2002). Among constructs used in prior research, several distinct mathematical models can be found, such as: multivariate regression analysis, Markov chains, stochastic processes, Bayesian networks, fuzzy logic, control theory, discrete event simulation, dynamic programming and neural networks.

While control theory has been widely used in systems and other engineering disciplines, it has not widely been applied to prognostics as explained in the next section.

## 5.7 Control Theoretic Approach to Prognostics

A system can be broadly defined as an integrated set of elements that accomplish a defined objective (INCOSE 2000). Any physical entity in the world can be considered as a system that functions as a collection of interrelated systems. The system theory approach in this book covers both feed-forward and feedback mechanisms to deliver a richer framework for prognostics.

Prognostics deal with prediction of some desired quality or characteristic of a system ([Kapur 2010](#bibliography.xhtml#b_9781547401567-016_ref_036)). It’s based on understanding the science of degradation of the underlying system. The traditional systems control theory has been predominantly based on feedback: Using the feedback information from the system (also referred to as the feedback signal), a system’s performance could be diagnosed, then adjusted to fix the problem. Obviously, this poses an issue. Correcting the problems after receiving feedback might be too late in certain mission critical systems and in particular when human physiology is considered.

Instead, a feed-forward model as exemplified by prognostics methods would be more desirable. Prognostics methodology is based on two principles: 1) it uses feed-forward models for prediction or to forecast of the underlying causes of problems by analyzing feed-forward signals; and 2) it suggests changes in input signals to the system in order to prevent the problem from occurring.

Prognostics and health management (PHM) is an engineering discipline that links studies of failure mechanisms to system lifecycle management ([Serdar, Goebel, and Lucas 2008](#bibliography.xhtml#b_9781547401567-016_ref_081)). Other definitions of PHM describe it as a method that permits the assessment of the reliability of a system under its actual application conditions, to determine the advent of failure, and mitigate system risks ([Pecht 2008](#bibliography.xhtml#b_9781547401567-016_ref_062)).

Within the context of systems control theory, the term “diagnostics” pertains to the detection and isolation of faults or failures. “Prognostics” is the process of predicting a future state (of reliability) based on current and historic conditions ([Vichare and Pecht 2006](#bibliography.xhtml#b_9781547401567-016_ref_082)).

Prognostics is the science of predicting the future functionality of a system by estimating the remaining useful life, probability of failure or time to failure for a given system. There are many approaches and modeling frameworks for representing a prognostics system. This is significant whether we are analyzing the failure point of business systems, an aircraft engine or human physiology.

Among many prognostics methods, computing the remaining useful life (RUL) of a system is common. RUL can be estimated from historical and operational data collected from a system. Various methods are used to determine system degradation and predict RUL.

Another method is estimating the probability of failure (POF). POF is the failure probability distribution of the system or a component. Additionally, it’s common to study time to failure (TTF), the time a component is expected to fail. TTF defines the time when a system no longer meets its design specifications.

Prognostics and reliability are interrelated. Reliability is defined as the probability that a product will perform its intended function, satisfactorily for its intended life when operating under specified condition ([Kapur 2010](#bibliography.xhtml#b_9781547401567-016_ref_036)). A clinical definition can be derived from this technical description. Reliability, in the medical sense, is the probability that a patient will not develop certain medical complications during the length stay under medical care of the care provider(s). Reliability is measured by several indicators such as mean time between failure (MTBF), failure rate and percentiles of Life. Each measurement can be computed from corresponding equations that are derived from empirical and statistical distribution functions. Additional treatment of reliability can be found from text by Kapur and Lamberson ([Kapur, Lamberson 1977](#bibliography.xhtml#b_9781547401567-016_ref_037)).

Prognostics models can be classified into three general types ([Eklund 2009](#bibliography.xhtml#b_9781547401567-016_ref_023); [Hines 2009](#bibliography.xhtml#b_9781547401567-016_ref_031); [Peysson et al. 2009](#bibliography.xhtml#b_9781547401567-016_ref_063)). Type I is reliability based. It applies the traditional time to failure analysis by tracking a population of failures and using statistical methods for the estimation of reliability. Some typical life distributions that are used in this type of prognostics include Weibull, exponential and normal distributions. Type I prognostic methods do not incorporate the real time monitoring of operating conditions or environmental conditions.

Type II methods, also known as the stressor-based approaches consider the operational and environmental condition data. Type II considers the failures of a system in its operating environment to provide an average remaining life of a component. Some of the environmental data might include temperature, vibration, humidity and load. The proportional hazard model is an example of a type II prognostic model. Knowing the causes, one can predict reliability of a system. The simplest model in this approach is the regression model: given the operating and environmental conditions, one can predict the system failure and remaining useful life by a regression equation.

Type III prognostic methods are condition-based, namely they characterize the lifetime of a system in operation within its specific environment. They estimate the remaining life of a specific component or the entire system. Among methods used in Type III prognostics are the general path model (GPM),

The cumulative damage model tracks the irreversible accumulation of damage in systems or components. The statistical cumulative damage model considers the number of possible damage states and a transition matrix (for representing a multi-state Markov Chain) to provide a damage prediction for multiple cyclical loads.

The goal of prognostics is to provide continuous prediction. I’ll describe a case study that using an artificial neural network, and other algorithms, continuously predicts a patient’s health status at regular time intervals.

## 5.8 Artificial Neural Networks

Neural networks have been used successfully to predict future onset of events. For example predicting diseases such as recurrence of various types of cancer, cardiac illnesses and to assist physicians with prognostic and decision support. These studies have offered long term predictions for patient health conditions, typically forecasting the disease-free or disease recurrence in the future ranging from a few months to several years.
