
(7.45)![equation](images/c7-disp-0051.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="block" overflow="scroll"><mi>p</mi><mfenced open="(" close=")"><mrow><mi>y</mi><mo>&#8739;</mo><msub><mi>x</mi><mn>1</mn></msub><mo>,</mo><mo>&#8230;</mo><mo>,</mo><msub><mi>x</mi><mi>n</mi></msub></mrow></mfenced><mo>=</mo><mfrac><mrow><mi>p</mi><mfenced open="(" close=")"><mi>y</mi></mfenced><msubsup><mo>&#8719;</mo><mrow><mi>i</mi><mo>=</mo><mn>1</mn></mrow><mi>n</mi></msubsup><mi>p</mi><mfenced open="(" close=")"><mrow><msub><mi>x</mi><mi>i</mi></msub><mo>&#8739;</mo><mi>y</mi></mrow></mfenced></mrow><mrow><mi>p</mi><mfenced open="(" close=")"><mrow><msub><mi>x</mi><mn>1</mn></msub><mo>,</mo><mo>&#8230;</mo><mo>,</mo><msub><mi>x</mi><mi>n</mi></msub></mrow></mfenced></mrow></mfrac></math>

As `p(x[1], …, x[n])` is constant for any given input, the following classification rule can be deducted:

(7.46)![equation](images/c7-disp-0052.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="block" overflow="scroll"><mi>p</mi><mfenced open="(" close=")"><mrow><mi>y</mi><mo>&#8739;</mo><msub><mi>x</mi><mn>1</mn></msub><mo>,</mo><mo>&#8230;</mo><mo>,</mo><msub><mi>x</mi><mi>n</mi></msub></mrow></mfenced><mo>&#8733;</mo><mi>p</mi><mfenced open="(" close=")"><mi>y</mi></mfenced><msubsup><mo>&#8719;</mo><mrow><mi>i</mi><mo>=</mo><mn>1</mn></mrow><mi>n</mi></msubsup><mi>p</mi><mfenced open="(" close=")"><mrow><msub><mi>x</mi><mi>i</mi></msub><mo>&#8739;</mo><mi>y</mi></mrow></mfenced></math>

The likelihood probability `p(x[i] ∣ y)` is considered known either empirically or by assumption. Gaussian, multinomial, and Bernoulli are among the most popular distributions considered for these probabilities. This results in estimation of a class label as:

(7.47)![equation](images/c7-disp-0053.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="block" overflow="scroll"><mover accent="true"><mi>y</mi><mo stretchy="true">&#38;c.circ;</mo></mover><mo>=</mo><mo mathvariant="italic">arg</mo><munder><mo>max</mo><mi>y</mi></munder><mi>p</mi><mfenced open="(" close=")"><mi>y</mi></mfenced><msubsup><mo>&#8719;</mo><mrow><mi>i</mi><mo>=</mo><mn>1</mn></mrow><mi>n</mi></msubsup><mi>p</mi><mfenced open="(" close=")"><mrow><msub><mi>x</mi><mi>i</mi></msub><mo>&#8739;</mo><mi>y</mi></mrow></mfenced></math>

Naïve Bayes classifiers are simple and work quite well in many real‐world situations. They require a small amount of training data to estimate the necessary parameters [[148]](#c07.xhtml#c7-bib-0148).

Naïve Bayes learners and classifiers can be extremely fast compared to more computationally intensive methods. The decoupling of the class conditional feature distributions means that each distribution can be independently estimated as a one‐dimensional distribution. This in turn helps alleviate the problem of the curse of dimensionality.

### 7.3.14 Hidden Markov Model

HMMs are state‐space machines meant to detect a correct data sequence which may happen within a longer data sequence. HMMs are presented as the state diagrams. Therefore, for each application, an HMM has a certain number of states and knows the probability of each possible event happening in each state. Before moving to an application of HMM to EEG, a good example for better understanding the HMM concept is the detection of QRS in an electrocardiogram (ECG) signal depicted in [Figure 7.16](#c07.xhtml#c7-fig-0016).

From [Figure 7.16](#c07.xhtml#c7-fig-0016), an ECG is recognized when the symbols turn up in a correct sequence in the signal. Assuming the waveform in [Figure 7.16](#c07.xhtml#c7-fig-0016) is the ECG of a healthy subject, the state diagram in [Figure 7.17](#c07.xhtml#c7-fig-0017) classifies the subject as healthy as long as the above ECG sequence is detected in his/her ECG record.

In this diagram, state `Q[0]` is a wait state to detect the beginning of sequence starting from a bar (b). State `Q[1]` is a state which shows a bar has been detected. State `Q[2]` simply demonstrates that a bar and a small hump (p) have been already recognized. `Q[3]` represents the state of the system when a bar, a small hump, and a QRS wave are correctly sequenced. `Q[4]` and `Q[5]` similarly show the states after a bar and a large hump (t) have been respectively added to the data sequence. After detecting the correct sequence, the output is 'the subject is healthy'. After each state, if a wrong symbol or noise is detected, the system output is 'the subject is not healthy'.

![Figure 7.16 A synthetic ECG segment of a healthy individual and its corresponding symbols.](images/c07f016.gif)

[**Figure 7.16**](#c07.xhtml#R_c7-fig-0016) A synthetic ECG segment of a healthy individual and its corresponding symbols.

![Figure 7.17 An HMM for detection of a healthy heart from an ECG sequence.](images/c07f017.gif)

[**Figure 7.17**](#c07.xhtml#R_c7-fig-0017) An HMM for detection of a healthy heart from an ECG sequence.

In places where the objective is to detect a particular heart condition, a separate HMM should be designed to recognize that condition. Beside their applications in biomedical signal analysis and disease recognition, HMMs have a wide range of applications in speech, video, bioscience (such as genomics) and face recognition.

In order to use an HMM for classification, the initial state (`π = π[i]`, where `i = 1, …, N`, where `N` is the number of states) the state probabilities (`A = {a[ij]}`, `i,j = 1, …, N`) and the state transition probabilities (`B = {b[j](k)}`, `j = 1, …, N`, `k = 1, …, T`, where `T` is the observation sequence length) should be known. For training the HMMs (i.e. to find the model parameters) however, a set of observations and the number of states should be known.

There are three major problems (objectives) in using or designing HMMs:

1.  Given the observation sequence `O = o[1], o[2], …, o[T]`, and the model `λ = (A, B, π)` what will be the probability of observation sequence, `p(O|λ)`?

2.  Given the observation sequence and the model as above, how can we find the state sequence `Q = Q[1], …, Q[N]` which generates such an observation sequence?

3.  Given the observations and the number of states how the HMM model can be built up, i.e. how we find `λ = (A, B, π)`.

To solve the first problem, often, the iterative forward‐backward algorithm is used while the Viterbi algorithm is employed to solve the second problem. Finally, a few algorithms, such as the most popular one, Baum‐Welch (Leonard E Baum, 1960s) [[149]](#c07.xhtml#c7-bib-0149), [[150]](#c07.xhtml#c7-bib-0150), can be used to solve the third problem which is the most important one.

To go through forward and backward algorithms, set `λ = (A, B, π)` with random initial conditions (unless some information about the parameters is available already). Then, follow the iterative procedures as shown below.

#### 7.3.14.1 Forward Algorithm

Let `α[i](t) = p(o[1] = y[1], …o[t] = y[t], Q[t] = i ∣ λ)` the probability of observing `y[1], y[2], … y[t]` and being in state `i` at time `t`:

(7.48)![equation](images/c7-disp-0054.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="block" overflow="scroll"><msub><mi mathvariant="normal">&#945;</mi><mi>i</mi></msub><mfenced open="(" close=")"><mn>1</mn></mfenced><mo>=</mo><msub><mi mathvariant="normal">&#960;</mi><mi>i</mi></msub><msub><mi>b</mi><mi>i</mi></msub><mfenced open="(" close=")"><msub><mi>y</mi><mn>1</mn></msub></mfenced></math>

and iterate over `t`:
