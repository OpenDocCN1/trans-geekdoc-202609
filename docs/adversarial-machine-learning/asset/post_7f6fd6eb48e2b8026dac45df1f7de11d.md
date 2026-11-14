
OD flow. Alternatively, it can be thought of as a measure of how closely a subspace aligns with the flow’s vector. See 152–154.

- **residual subspace**: In subspace estimation, the residual subspace (or abnormal subspace) is the orthogonal complement to the normal subspace used by the model to describe the observed data; i.e., the error component of each data point lies in the residual subspace. See 136, 139, 152.

- **response space** (Y): The space of values for the response variables; in classification this is a finite set of categories and in binary classification it is ["+", "-"]. See 23, 26.

- **response variable**: An unobserved quantity that is to be predicted based on observable explanatory variables. See 23, _see also_ label.

- **risk** (R(P<sub>Z</sub>, f)): The expected loss of a decision procedure f with respect to data drawn from the distribution P<sub>Z</sub>. See 26, 171, 176, 177, 180, 185, 188.

- **robust statistics**: The study and design of statistical procedures that are resilient to small deviations from the assumed underlying statistical model; e.g., outliers. See 55.

- **RONI**: See vii, 120, 128–132, 243, Glossary: reject on negative impact.

- **scale invariant**: A property that does not change when the space is scaled by a constant factor. See 208.

- **secure learning**: The ability of a learning agent to achieve its security goals in spite of the presence of an adversary that tries to prevent it from doing so. See 7.

- **security goal**: Any objective that a system needs to achieve to ensure the security of the system and/or its users. See 31.

- **security-sensitive domain**: A task or problem domain in which malicious entities have a motivation and a means to disrupt the normal operation of system. In the context of adversarial learning, these are problems where an adversary wants to mislead or evade a learning algorithm. See 3, 5, 6, 29, 31.

- **set indicator function**: The function I<sub>X</sub> [·] associated with the set X that is 1 for any x ∈ X and is 0 otherwise. See 256.

- **shift invariant**: A property that does not change when the space is shifted by a constant amount. See 208.

- **stationarity**: A stochastic process in which a sequence of observations are all drawn from the _same_ distribution. Also, in machine learning, it is often assumed that the training and evaluation data are both drawn from the same distribution—we refer to this as an assumption of stationarity. See 22, 31.

- **support vector machine**: A family of (nonlinear) learning algorithms that find a maximally separating hyperplane in a high-dimensional space known as its reproducing kernel Hilbert space (RKHS). The kernel function allows the method to compute inner products in that space without explicitly mapping the data into the RKHS. See 39, 43, 46, 52, 55, 63, 171, 176.

- **SVM**: See 55, *Glossary*: support vector machine.

- **threat model**: A description of an adversary’s incentives, capabilities, and limitations. See 13, 31.

- **training**: The process of using a training dataset \(\mathbb{D}^{(\text{train})}\) to choose a hypothesis \(f\) from among a hypothesis space, \(\mathcal{F}\). See 25, 33, 34, 40, 44, 131, 134, 142–144.

- **training algorithm** (\(H^{(N)}\)): An algorithm that selects a classifier to optimize a performance measure for a training dataset; also known as an estimating procedure or learning algorithm. See 24, 25, 32, 203, 234, 247.

- **training dataset** (\(\mathbb{D}^{(\text{train})}\)): A dataset used by a training algorithm to construct or select a classifier. See 6, 17, 18, 21, 25, 27, 30–32, 34, 36, 39, 40, 45, 46, 49, 55, 56, 58, 61, 63, 69, 71, 72, 94, 106, 107, 114–116, 119, 120, 128, 134, 162, 171, 197, 247, 278, 281, see also dataset.

- **true-positive rate**: The frequency for which a predictor correctly classifies positive instances. This is a common measure of a predictor’s performance and is one minus the false-negative rate. See 151, see also false-negative rate.

- **unfavorable evaluation distribution**: A distribution introduced by the adversary during the evaluation phase to defeat the learner’s ability to make correct predictions; this is also referred to as *distributional drift*. See 45.

- **VC-dimension**: The VC or Vapnik-Chervonenkis dimension is a measure of the complexity of a family of classifiers, which is defined as the cardinality of the largest set of data points that can be shattered by the classifiers. See 174, 176, 179, 205.

- **vector space**: A set of objects (vectors) that can be added or multiplied by a scalar; i.e., the space is closed under vector addition and scalar multiplication operations that obey associativity, commutativity, and distributivity and has an additive and multiplicative identity as well as additive inverses. See 257, 259.

- **virus detection system**: A detector tasked with identifying potential computer viruses. See 31.

## References

- Aldà, F. & Rubinstein, B. I. P. (2017), The Bernstein mechanism: Function release under differential privacy, in "Proceedings of the 31st AAAI Conference on Artificial Intelligence (AAAI’2017)." Alfeld, S., Zhu, X., & Barford, P. (2016), Data poisoning attacks against autoregressive models, in "Proceedings of the 30th AAAI Conference on Artificial Intelligence (AAAI’2016)," pp. 1452–1458. Alfeld, S., Zhu, X., & Barford, P. (2017), Explicit defense actions against test-set attacks, in "Proceedings of the 31st AAAI Conference on Artificial Intelligence (AAAI’2017)." Alpcan, T., Rubinstein, B. I. P., & Lckie, C. (2016), Large-scale strategic games and adversarial machine learning, in "2016 IEEE 55th Conference on Decision and Control (CDC)," IEEE, pp. 4420–4426. Amsaleg, L., Bailey, J., Erfani, S., Furon, T., Houle, M. E., Radovanović, M., & Vinh, N. X. (2016), The vulnerability of learning to adversarial perturbation increases with intrinsic dimensionality, Technical Report NII-2016-005E, National Institute of Informatics, Japan. Angluin, D. (1988), "Queries and concept learning," Machine Learning 2, 319–342. Apache (n.d.). Apache SpamAssassin. Bahl, P., Chandra, R., Greenstein, A., Kandula, S., Maltz, D. A., & Zhang, M. (2007), Towards highly reliable enterprise network services via inference of multi-level dependencies, in "Proceedings of the 2007 Conference on Applications, Technologies, Architectures, and Protocols for Computer Communications (SIGCOMM)," pp. 13–24. Balfanz, D. & Staddon, J., eds (2008), Proceedings of the 1st ACM Workshop on Security and Artificial Intelligence, AISec 2008. Balfanz, D. & Staddon, J., eds (2009), Proceedings of the 2nd ACM Workshop on Security and Artificial Intelligence, AISec 2009. Barak, B., Chaudhuri, K., Dwork, C., Kale, S., McSherry, F., & Talwar, K. (2007), Privacy, accuracy, and consistency too: A holistic solution to contingency table release, in "Proceedings of the Twenty-Sixth ACM SIGMOD-SIGACT-SIGART Symposium on Principles of Database Systems," pp. 273–282. Barbaro, M. & Zeller Jr, T. (2006), "A face is exposed for AOL searcher no. 4417749," New York Times. Barreno, M. (2008), Evaluating the security of machine learning algorithms. PhD thesis, University of California, Berkeley. Barreno, M., Nelson, B., Joseph, A. D., & Tygar, J. D. (2010), "The security of machine learning," Machine Learning 81(2), 121–148. Barreno, M., Nelson, B., Sears, R., Joseph, A. D., & Tygar, J. D. (2006), Can machine learning be secure?, in "Proceedings of the ACM Symposium on Information, Computer and Communications Security (ASIACCS)," pp. 16–25.

- Barth, A., Rubinstein, B. I. P., Sundararajan, M., Mitchell, J. C., Song, D., & Bartlett, P. L. (2012), "A learning-based approach to reactive security," IEEE Transactions on Dependable and Secure Computing 9(4), 482–493. Special Issue on Learning, Games, and Security.

- Bassily, R., Smith, A., & Thakurta, A. (2014), Private empirical risk minimization: Efficient algorithms and tight error bounds, in "2014 IEEE 55th Annual Symposium on Foundations of Computer Science (FOCS)," pp. 464–473.

- Beimel, A., Kasiviswanathan, S., & Nissim, K. (2010), Bounds on the sample complexity for private learning and private data release, in "Theory of Cryptography Conference," Vol. 5978 of Lecture Notes in Computer Science, Springer, pp. 437–454.

- Bennett, J., Lanning, S., et al. (2007), The Netflix prize, in "Proceedings of KDD Cup and Workshop," Vol. 2007, pp. 3–6.

- Bertsimas, D. & Vempala, S. (2004), "Solving convex programs by random walks," Journal of the ACM 51(4), 540–556.

- Biggio, B., Corona, I., Maiorca, D., Nelson, B., Srndic, N., Laskov, P., Giacinto, G., & Roli, F. (2013), Evasion attacks against machine learning at test time, in "Machine Learning and Knowledge Discovery in Databases - European Conference, ECML PKDD 2013," pp. 387–402.

- Biggio, B., Fumera, G., & Roli, F. (2010), Multiple classifier systems under attack, in N. E. G. J. K. F. Roli, ed., "Proceedings of the 9th International Workshop on Multiple Classifier Systems (MCS)," Vol. 5997, Springer, pp. 74–83.

- Biggio, B., Nelson, B., & Laskov, P. (2012), Poisoning attacks against support vector machines, in "Proceedings of the 29th International Conference on Machine Learning (ICML-12)," pp. 1807–1814.

- Biggio, B., Rieck, K., Ariu, D., Wressnegger, C., Corona, I., Giacinto, G., & Roli, F. (2014), Poisoning behavioral malware clustering, in "Proceedings of the 2014 Workshop on Artificial Intelligent and Security Workshop, AISec 2014," pp. 27–36.

- Billingsley, P. (1995), Probability and Measure, 3rd edn, Wiley.

- Bishop, C. M. (2006), Pattern Recognition and Machine Learning, Springer-Verlag.

- Blöckl, J., Christin, N., Datta, A., & Sinha, A. (2011), Regret minimizing audits: A learning-theoretic basis for privacy protection, in "Proceedings of the 24th IEEE Computer Security Foundations Symposium," pp. 312–327.

- Blum, A., Dwork, C., McSherry, F., & Nissim, K. (2005), Practical privacy: The SuLQ framework, in "Proceedings of the Twenty Fourth ACM SIGMOD-SIGACT-SIGART Symposium on Principles of Database Systems," pp. 128–138.

- Blum, A., Ligett, K., & Roth, A. (2008), A learning theory approach to non-interactive database privacy, in "Proceedings of the Fortieth Annual ACM Symposium on Theory of Computing (STOC)," pp. 609–618.

- Bodík, P., Fox, A., Franklin, M. J., Jordan, M. I., & Patterson, D. A. (2010), Characterizing, modeling, and generating workload spikes for stateful services, in "Proceedings of the 1st ACM Symposium on Cloud Computing (SoCC)," pp. 241–252.

- Bodík, P., Griffith, R., Sutton, C., Fox, A., Jordan, M. I., & Patterson, D. A. (2009), Statistical machine learning makes automatic control practical for internet datacenters, in "Proceedings of the Workshop on Hot Topics in Cloud Computing (HotCloud)," USENIX Association, pp. 12–17.

- Bolton, R. J. & Hand, D. J. (2002), "Statistical fraud detection: A review," Journal of Statistical Science 17(3), 235–255.

- Bousquet, O. & Elisseeff, A. (2002), "Stability and generalization," Journal of Machine Learning Research 2(Mar), 499–526.
