# 4.5 DECISION RULES

Decision rules are **bad in depicting linear relationships** between features and output. That is a problem they share with the decision trees. Decision trees and rules can only produce step-like prediction functions, where changes in the prediction are always discrete steps not smooth curves. This is related to the issue that the inputs have to be categorical. In decision trees, they are implicitly categorized by splitting.

# 4.5.6 Software and Alternatives

OneR is implemented in the R package OneR$^{15}$, which was used for the examples in this book. OneR is also implemented in Weka machine learning library$^{16}$ and as available in Java, R and Python. RIPPER is also implemented in Weka. For the examples, I used the R implementation of JRIP in the Weka package$^{17}$, SBRL is available as R package$^{18}$ (which I used for the examples), in Python$^{19}$ or C implementation$^{20}$. Additionally, I recommend the imodel$^{21}$, which implements rule-based models based on Bayesian rule lists, CORELS, OneR, greedy rule lists, and more in a Python package with a unified scikit-learn interface.

I will not try to list all alternatives for decision rule sets and lists, but will will point to some summarizing work. I recommend the book “Foundations of Rule Learning” by Fürkranz et al.$^{22}$. It is an extensive work on learning rules, for those who want to delve deeper into the topic. It provides a holistic framework for thinking about learning rules and presents many rule learning algorithms. I also recommend to check the Weka learners$^{23}$, which implement RIPPER, M5Rules, OneR, PART and many more. IF-THEN rules can be used in linear models as described in this book in the chapter about the RuleFit algorithm.

$15}$https://cran.r-project.org/web/packages/OneR/
16}$https://www.eecs.yorku.edu/tdb/_doc.php?user/sw/weka/doc/weka/classifiers/rules/package-summary.html
$17}$https://cran.r-project.org/web/packages/RWeka/index.html
$18}$https://cran.r-project.org/web/packages/sbrl/index.html
$19}$https://github.com/datascienceinc/Skater
$20}$https://github.com/Hongyuy/shrimod
$21}$https://github.com/elsvier/imod
$22}$Fürkranz, Johannes, Dragan Gamberger, and Nada Lavrač. “Foundations of rule learning.” Springer Science & Business Media. (2012).
$23}$http://weka.sourceforge.net/doc.doc/weka/classifiers/rules/package-summary.html