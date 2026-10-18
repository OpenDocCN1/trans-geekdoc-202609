data set with *N* attack events is obtained. The algorithm consists of repeating the following process *N* times:

+   - Select the root node of the graph.
+   - Identify the child nodes and select the attack/s by simulating discrete random variables using the selection probabilities of the respective levels.
+   - For the nodes selected in the previous step, verify whether the attacker managed to compromise the devices by simulating Bernoulli random variables whose parameters are the vulnerability probabilities.
+   - Save the compromised nodes from the previous step in a vector and with these nodes carry out steps 2 and 3 until there are no more child nodes in the graph.
+   - Create a vector in which each position represents a variable of the Bayesian network; set the value of 1 if the variable (node) was selected and compromised and 0 otherwise.

# 7.6.3  Network Parametrization

The maximum likelihood estimates of equation (7.5.8) are used to obtain the parameters from the data set generated from the attack simulation. Specifically, the following parameters are calculated:

+   - $\Theta_{\mathrm{SECP}}$
+   - $\Theta_{\mathrm{PHCP}\mid\mathrm{SECP}}$
+   - $\Theta_{\mathrm{MICP}\mid\mathrm{SECP}}$
+   - $\Theta_{\mathrm{DOSR}\mid\mathrm{PHCP},\ \mathrm{MICP}}$
+   - $\Theta_{\mathrm{RTPR}\mid\mathrm{PHCP},\ \mathrm{MICP}}$
+   - $\Theta_{\mathrm{PAR}\mid\mathrm{PHCP},\ \mathrm{MICP}}$
+   - $\Theta_{\mathrm{DOSF}\mid\mathrm{DOSR},\ \mathrm{RTPR},\ \mathrm{PAR}}$
+   - $\Theta_{\mathrm{MITMF}\mid\mathrm{DOSR},\ \mathrm{RTPR},\ \mathrm{PAR}}$

# 7.6.4  Results

This section presents the results obtained from the implementation of the model. The number of attacks simulated were 1000. Using exact inference