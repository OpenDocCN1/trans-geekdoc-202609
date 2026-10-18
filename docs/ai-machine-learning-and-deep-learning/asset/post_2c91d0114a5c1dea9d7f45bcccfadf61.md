
## FIGURE 19.9 Example tone.

As with the tone of an email-specific message, quality elements can be captured with LIME and anchor explanations. These can be recognized in a direct or indirect way. Expressing specific feelings or appeals belong to this category. These would require an additional interpretation in a neural network rather than just providing a list of words that are relevant for the decision. Appeals can be grouped into rational, emotional, and motivational appeals [29]. Rational appeals deal with the reasoning in different forms such as “one event is a sign of another” [29]. This means that phishing attackers are trying to not just ask for sensitive information without any explanation. They feel that providing reasoning makes them appear less suspicious. In the example presented in Figure 19.10, significant changes in the account’s activity are used as the reason for the update of the user’s account information.

![](img/efffc69cb8cda75bcf341884e3396898_528_0.png)

## FIGURE 19.10 Example reasoning appeal.

As shown in Figure 19.11, emotional appeals deal with different emotions and try to make the email user feel appreciated [29].

![](img/efffc69cb8cda75bcf341884e3396898_529_0.png)

## FIGURE 19.11 Example emotional appeal.

Figure 19.12 presents an example of a motivational appeal. Motivational appeals make use of the needs of humans, and, like emotional appeals, they are based on the specific message that is targeted through that email.

![](img/efffc69cb8cda75bcf341884e3396898_529_1.png)

## FIGURE 19.12 Example motivational appeal.

Another element that often comes up when the detection of phishing is being discussed is time pressure. Time pressure can be expressed by a lot of different words. These words can be part of the set that is significant for the decision of the network. Figure 19.13 presents an example of a time pressure.

![](img/efffc69cb8cda75bcf341884e3396898_530_0.png)

## FIGURE 19.13 Example time pressure.

According to Jakobsson [24], along with time pressure, an inordinate emphasis on security can be characteristic of phishing emails. While phishing attackers try to hide their intention by giving more attention to security, this can reveal their actual goal. Just like the time pressure aspect, security can be expressed by a variety of words, and therefore it can be identified by LIME as well as anchor explanations. An evaluation of whether too much emphasis was placed on security needs to be validated individually for each email.

Though each of the characteristics in Table 19.1 were explained separately, in reality many of the characteristics from Table 19.1 can be found in an email. Figures 19.14 and 19.15 are examples of phishing emails containing motivational, emotional, rational appeals, sent from a specific group of senders, asking for a confirmation of banking details, having a specific style (short, business email, advertising), containing message quality elements, and putting a strong emphasis on security.

![](img/efffc69cb8cda75bcf341884e3396898_530_1.png)

## FIGURE 19.14 Examples of phishing emails from Citibank.

## 19.6.1 Completion of the Artifact

From the comparison of the interpreters, it can be concluded that both the interpreters leave space for further improvement for the completion of the artifact. For example, LIME might classify the same email differently in various runs due to its random properties. That is, the same words could be found as being characteristic for a phishing email as for a spam email [20].

Anchor explanations address the drawback of the local fidelity of LIME but can be improved in other aspects. For example, depending on the email, the computation of anchors for one email can take several hours. This does not provide the desired computation time for explanations in almost real time. Also, the implementation of the algorithm with the alibi package could not always find anchors for the specific precision level, and the anchors sometimes found elements of less content included. For future work, it is recommended that these drawbacks of anchors be fixed by fine-tuning the parameters. This, with the ability to highlight anchors with LIME explanations, can lead to a fast and easily understandable interpreter complementing the decisions of the corresponding phishing detector.

The objective was to get users to use System 2 thinking [9, 58] by raising their attention through highlighting suspicious parts of email text. Raising the user’s attention should aid users in determining whether an email is genuine or phishing by drawing attention to important phrases in emails potentially classified as phishing [41, 55].

## NOTES

- 1. Website: www.csoonline.com/article/2117843/what-is-phishing-how-this-cyber-attack-works-and-how-to-prevent-it.html
- 2. Website: https://cofense.com/
- 3. AppRiver. AppRiver, 2002.
- 4. Alibi anchors. https://docs.seldon.io/projects/alibi/en/stable/methods/Anchors.html. Accessed: 2021-01-08.
- 5. Keras.io. callbacks–keras documentation. https://keras.io/callbacks/. Accessed: 2021-01-05.

32nd International Conference on Neural Information Processing Systems, 590–601.

11. Drake, C. E., Oliver, J. J. & Koontz, E. J. (2004). Anatomy of a Phishing Email. Proceedings of the First Conference on Email and Anti-Spam (CEAS), 1–8.

12. Embrey, I. & Kaivanto, K. (2018). Many Phish in the C: A Coexisting-Choice-Criteria Model of Security Behavior, Economic Working Paper Series, Lancaster University Management School, 1–23.

13. Fernandez, C. & Provost, F. (2019). Counterfactual Explanations for Data-Driven Decisions. 40th International Conference on Information Systems, ICIS 2019, Munich, Germany, 1–9.

14. Ganesh, H. B., Vinayakumar, R., Anand Kumar, M. & Kp, S. (2018). Distributed Representation using Target Classes: Bag of Tricks for Security and Privacy Analytics. Proceedings of the 1st Anti-Phishing Shared Task Pilot at 4th ACM IWSPA co-located with 8th ACM Conference on Data and Application Security and Privacy (CODASPY 2018), Tempe, Arizona, USA, March 21, 2018.

15. Gerber, S. (2018). 11 Security Strategies to Protect Your Company From Phishing Attacks, TNW News. https://thenextweb.com/news/11-security-strategies-protect-company-phishing-attacks

16. Goerke, T. & Lang, M. (2019). Scoped Rules (anchors). In Interpretable Machine Learning. https://christophm.github.io/interpretable-ml-book/anchors.html

17. Goodfellow, I., Bengio, Y. & Courville, A. (2017). Deep Learning. MIT Press, USA.

18. Guidotti, R., Monreale, A., Ruggieri, S., Turini, F., Pedreschi, D., & Giannotti, F. (2019). A Survey Of Methods For Explaining Black Box Models. ACM Computing Surveys, 51(5), 1–42.

19. Gupta, B. B., Arachchilage, N. A., & Psannis, K. E. (2018). Defending Against Phishing Attacks: Taxonomy of Methods, Current Issues and Future Directions. Telecommunication Systems, 67(2):247–267.

20. Harikrishnan, N.B., Vinayakumar, R, & Kp, S. (2018). A Machine Learning approach towards Phishing Email Detection. Proceedings of the 1st Anti-Phishing Shared Task Pilot at 4th ACM IWSPA co-located with 8th ACM Conference on Data and Application Security and Privacy (CODASPY 2018), Tempe, Arizona, USA, March 21, 2018.

- 21. Harrison, B., Svetieva, E. & Vishwanath, A. (2016). Individual Processing of Phishing Emails. *Online Information Review*, 40(2):265–281.
- 22. Hiransha, M., Unnithan, N. A., Vidyapeetham, R. & Kp, S. (2018). Deep Learning Based Phishing Email Detection. In: R. Verma, A. Das (eds.): *Proceedings of the 1st AntiPhishing Shared Pilot at 4th ACM International Workshop on Security and Privacy Analytics (IWSPA 2018)*, Tempe, Arizona, USA.
- 23. Jagatic, B. T. N., Johnson, N. A., Jakobsson, M. & Menczer, F. (2007). Social Phishing, *Communications of the ACM*, 50(10), 94–100.
- 24. Jakobsson, M. (2007). The Human Factor in Phishing. In *Priv. Secur. Consum. Inf.*, 7, 1–19.
- 25. Kahneman, D. (2012). *Thinking, Fast and Slow*. Penguin Books.
- 26. Karumbailah, S., Wright, R. T., Durcikova, A. & Jensen, M. L. (2016). Phishing Training: A Preliminary Look at the Effects of Different Types of Training. In *Proceedings of the 11th Pre-ICIS Workshop on Information Security and Privacy*, Dublin.
- 27. Klaise, J., Looveren, A. V., Vacanti, G., & Coca, A. (2021). Alibi Explain: Algorithms for Explaining Machine Learning Models. *Journal of Machine Learning Research*, 22, 1–7.
- 28. Kluge, K., & Eckhardt, R. (2020). Explaining the Suspicion: Design of an XAI-based User-Focused Anti-Phishing Measure, *16th International Conference on Wirtschaftsinformatik*, March 2021, Essen, Germany.
- 29. Kim, D. & Kim, J. H. (2013). Understanding Persuasive Elements in Phishing Emails: A Categorical Content and Semantic Network Analysis. *Online Information Review*, 37:835–850.
- 30. Kumaraguru, P., Sheng, S. Acquisti, A. Cranor, L. F. & Hong, J. I. (2010). Teaching Johnny Not To Fall For Phish. *ACM Trans. Internet Techn.*, 10:7:1–7:31.
- 31. LaCour, J. (2019). Phishing Trends and Intelligence Report – The Growing Social Engineering Threat. *Technical report*, PhishLabs Team, 2019.
- 32. Lei, T., Barzilay, R., & Jaakkola, T. (2016). Rationalizing Neural Predictions. *EMNLP 2016 – Conference on Empirical Methods in Natural Language Processing*, 107–117.
