
### 7.3.6 Gaussian Mixture Models (GMM)

(7.31)![equation](images/c7-disp-0035.png)
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block" overflow="scroll">
  <mi>p</mi>
  <mfenced open="(" close=")">
    <mrow>
      <mtext mathvariant="italic">object property</mtext>
      <mo>&#8739;</mo>
      <mtext mathvariant="italic">context</mtext>
    </mrow>
  </mfenced>
  <mo>=</mo>
  <mi>p</mi>
  <mfenced open="(" close=")">
    <mrow>
      <mi>O</mi>
      <mo>&#8739;</mo>
      <mi>v</mi>
    </mrow>
  </mfenced>
  <mo>=</mo>
  <mfrac>
    <mrow>
      <mi>p</mi>
      <mfenced open="(" close=")">
        <mrow>
          <mi>v</mi>
          <mo>&#8739;</mo>
          <mi>O</mi>
        </mrow>
      </mfenced>
    </mrow>
    <mrow>
      <mi>p</mi>
      <mfenced open="(" close=")">
        <mi>v</mi>
      </mfenced>
    </mrow>
  </mfrac>
  <mi>p</mi>
  <mfenced open="(" close=")">
    <mi>O</mi>
  </mfenced>
</math>

where `p(v)` can easily be calculated as:

(7.32)![equation](images/c7-disp-0036.png)
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block" overflow="scroll">
  <mi>p</mi>
  <mfenced open="(" close=")">
    <mi>v</mi>
  </mfenced>
  <mo>=</mo>
  <mi>p</mi>
  <mfenced open="(" close=")">
    <mrow>
      <mi>v</mi>
      <mo>&#8739;</mo>
      <mi>O</mi>
    </mrow>
  </mfenced>
  <mi>p</mi>
  <mfenced open="(" close=")">
    <mi>O</mi>
  </mfenced>
  <mo>+</mo>
  <mi>p</mi>
  <mfenced open="(" close=")">
    <mrow>
      <mi>v</mi>
      <mo>&#8739;</mo>
      <mover accent="true">
        <mi>O</mi>
        <mo stretchy="true">&#175;</mo>
      </mover>
    </mrow>
  </mfenced>
  <mi>p</mi>
  <mfenced open="(" close=")">
    <mover accent="true">
      <mi>O</mi>
      <mo stretchy="true">&#175;</mo>
    </mover>
  </mfenced>
</math>

where `p(v ∣ O)` is the likelihood of the features given the observation (presence of an object) and
![images](images/c7-i0013.png)
<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll">
  <mi>p</mi>
  <mfenced open="(" close=")">
    <mrow>
      <mi>v</mi>
      <mo>&#8739;</mo>
      <mover accent="true">
        <mi>O</mi>
        <mo stretchy="true">&#175;</mo>
      </mover>
    </mrow>
  </mfenced>
</math>
is the likelihood of the features when the object is absent. A GMM is then used to estimate these likelihoods as:

(7.33)![equation](images/c7-disp-0037.png)
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block" overflow="scroll">
  <mi>p</mi>
  <mfenced open="(" close=")">
    <mrow>
      <mi>v</mi>
      <mo>&#8739;</mo>
      <mi>O</mi>
    </mrow>
  </mfenced>
  <mo>=</mo>
  <munderover>
    <mo>&#8721;</mo>
    <mrow>
      <mi>i</mi>
      <mo>=</mo>
      <mn>1</mn>
    </mrow>
    <mi>M</mi>
  </munderover>
  <msub>
    <mi>w</mi>
    <mi>i</mi>
  </sub>
  <mo>&#8901;</mo>
  <mi>G</mi>
  <mfenced open="(" close=")">
    <mrow>
      <mi>v</mi>
      <mo>;</mo>
      <msub>
        <mi mathvariant="normal">&#956;</mi>
        <mi>i</mi>
      </msub>
      <mo>,</mo>
      <msub>
        <mi mathvariant="normal">&#8721;</mi>
        <mi>i</mi>
      </msub>
    </mrow>
  </mfenced>
</math>

which is the sum of weighted Gaussians with unknown means and covariance matrices. The parameters `w[i]`, `μ[i]`, and `∑[i]` have to be estimated using a kind of optimization technique. Often expectation maximization [[61]](#c07.xhtml#c7-bib-0061) is used for this purpose.

GMM is a very popular modelling approach for representation of various waveforms including abnormal EEGs. In a study of neonatal seizure detection GMM has been shown to perform well [[62]](#c07.xhtml#c7-bib-0062).

### 7.3.7 Logistic Regression

*Logistic regression* is generally used to estimate the probability of an observation subject to an attribute. It estimates the observation probability from the given features. A logistic function `F(v)` is computed from the features as:

(7.34)![equation](images/c7-disp-0038.png)
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block" overflow="scroll">
  <mtext mathvariant="italic">Logit</mtext>
  <mo>=</mo>
  <mo mathvariant="italic">log</mo>
  <mfrac>
    <mrow>
      <mi>p</mi>
      <mfenced open="(" close=")">
        <mrow>
          <mi>O</mi>
          <mo>&#8739;</mo>
          <mi>v</mi>
        </mrow>
      </mfenced>
    </mrow>
    <mrow>
      <mi>p</mi>
      <mfenced open="(" close=")">
        <mrow>
          <mover accent="true">
            <mi>O</mi>
            <mo stretchy="true">&#175;</mo>
          </mover>
          <mo>&#8739;</mo>
          <mi>v</mi>
        </mrow>
      </mfenced>
    </mrow>
  </mfrac>
  <mo>=</mo>
  <mi>F</mi>
  <mfenced open="(" close=")">
    <mi>v</mi>
  </mfenced>
</math>

where `F(v)` depends on the sequence of attributes (i.e. previous experiences):

(7.35)![equation](images/c7-disp-0039.png)
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block" overflow="scroll">
  <mi>F</mi>
  <mfenced open="(" close=")">
    <mi>v</mi>
  </mfenced>
  <mo>=</mo>
  <msub>
    <mi>a</mi>
    <mn>0</mn>
  </msub>
  <mo>+</mo>
  <munderover>
    <mo>&#8721;</mo>
    <mrow>
      <mi>i</mi>
      <mo>=</mo>
      <mn>1</mn>
    </mrow>
    <mi>D</mi>
  </munderover>
  <msub>
    <mi>a</mi>
    <mi>i</mi>
  </sub>
  <mo>&#8901;</mo>
  <mi>v</mi>
  <mfenced open="(" close=")">
    <mi>i</mi>
  </mfenced>
</math>

and for testing:

(7.36)![equation](images/c7-disp-0040.png)
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block" overflow="scroll">
  <mi>p</mi>
  <mfenced open="(" close=")">
    <mrow>
      <mi>O</mi>
      <mo>&#8739;</mo>
      <mi>v</mi>
    </mrow>
  </mfenced>
  <mo>=</mo>
  <mfrac>
    <mn>1</mn>
    <mrow>
      <mn>1</mn>
      <mo>+</mo>
      <msup>
        <mi>e</mi>
        <mrow>
          <mo form="prefix">&#8722;</mo>
          <mi>F</mi>
          <mfenced open="(" close=")">
            <mi>v</mi>
          </mfenced>
        </mrow>
      </msup>
    </mrow>
  </mfrac>
</math>

To give an example, consider:

Observation `O`: suffering from back pain and
![images](images/c7-i0014.png)
<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll">
  <mover accent="true">
    <mi>O</mi>
    <mo stretchy="true">&#175;</mo>
  </mover>
</math>
: not suffering from back pain

Attribute `ν`: age:

![equation](images/c7-disp-0041.png)
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block" overflow="scroll">
  <mo mathvariant="italic">log</mo>
  <mfrac>
    <mrow>
      <mi>p</mi>
      <mfenced open="(" close=")">
        <mrow>
          <mi>O</mi>
          <mo>&#8739;</mo>
          <mi>v</mi>
        </mrow>
      </mfenced>
    </mrow>
    <mrow>
      <mi>p</mi>
      <mfenced open="(" close=")">
        <mrow>
          <mover accent="true">
            <mi>O</mi>
            <mo stretchy="true">&#175;</mo>
          </mover>
          <mo>&#8739;</mo>
          <mi>v</mi>
        </mrow>
      </mfenced>
    </mrow>
  </mfrac>
  <mo>=</mo>
  <msub>
    <mi>a</mi>
    <mn>0</mn>
  </msub>
  <mo>+</mo>
  <msub>
    <mi>a</mi>
    <mn>1</mn>
  </sub>
  <mo>&#8901;</mo>
  <mfenced open="(" close=")">
    <mrow>
      <mi mathvariant="italic">age</mi>
      <mo>&#8722;</mo>
      <mn>20</mn>
    </mrow>
  </mfenced>
</math>

During the training stage `a[0]` (the log odds for a 20‐year‐old person) and `a[1]` (the log odds ratio when comparing two persons who differ by 1 year in age) are estimated. In the testing stage the probability of having back pain given the age is estimated as:

![equation](images/c7-disp-0042.png)
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block" overflow="scroll">
  <mi>p</mi>
  <mfenced open="(" close=")">
    <mrow>
      <mi>O</mi>
      <mo>&#8739;</mo>
      <mi mathvariant="italic">age</mi>
    </mrow>
  </mfenced>
  <mo>=</mo>
  <mfrac>
    <mn>1</mn>
    <mrow>
      <mn>1</mn>
      <mo>+</mo>
      <msup>
        <mi>e</mi>
        <mrow>
          <mo form="prefix">&#8722;</mo>
          <msub>
            <mi>a</mi>
            <mn>0</mn>
          </msub>
          <mo>+</mo>
          <msub>
            <mi>a</mi>
            <mn>1</mn>
          </msub>
          <mfenced open="(" close=")">
            <mrow>
              <mi mathvariant="italic">age</mi>
              <mo>&#8722;</mo>
              <mn>20</mn>
            </mrow>
          </mfenced>
        </mrow>
      </msup>
    </mrow>
  </mfrac>
</math>

### 7.3.8 Reinforcement Learning

In reinforcement learning an agent learns a good behaviour. This means that it modifies or acquires new behaviours and skills incrementally [[63]](#c07.xhtml#c7-bib-0063). It exploits the local information as well as the restrictions imposed on the application to maximize the influences of numerous tasks over a time period. Therefore, during the process of reinforcement learning, the machine learns by itself based on the penalties and rewards it receives in order to decide on its next step action. Thus, the learning process is sequential. With this algorithm, each node discovers the minimal needed resources to carry out its routine tasks with benefits allocated by the Q‐learning technique. This technique is mainly used to assess the value or quality of action taken by the learning system (embedded in each sensor for the distributed cases) for estimation of the award to be given [[64]](#c07.xhtml#c7-bib-0064) and consequently undertaking the next step.

### 7.3.9 Artificial Neural Networks
