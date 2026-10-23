Also, the joint probability density function showing the demeanor of a network can be shown as follows:

$$p(v,h)=\frac{1}{Z}\exp(-E(v,h))$$

$$Z=\sum_{v,h}\exp(-E(v,h))$$

From the preceding formulas, the equations for the training of parameters will be determined. We can get the following equation:

$$p(v\mid\theta)=\sum_{h}P(v,h)=\frac{1}{Z}=\sum_{h}\exp(-E(v,h))$$

Hence, the **log likelihood** can be shown as follows:

$$\mathit{In}\,L(\theta\mid v)=\mathit{In}\,p(v\mid\theta)$$

$$=\mathit{In}\,\frac{1}{Z}\sum_{h}\exp(-E(v,h))$$

$$=\mathit{In}\,\frac{1}{Z}\sum_{h}\exp(-E(v,h))-\mathit{In}\,\sum_{v,h}\exp(-E(v,h))$$