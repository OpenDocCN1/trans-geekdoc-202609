
为了维护隐私，用户设备必须长期保持安全。通过告知用户随时间发现的设备漏洞，可以减轻数据生命周期（收集、存储和分析）中的隐私风险。更重要的是，该框架可以帮助用户更新他们的智能手机，特别是物联网设备。近一半的用户从不更新物联网设备 [[ROUF2016](#ch13.xhtml#ref13_63)]。此外，如果用户正在使用不再接收更新的（易受攻击的）设备，可以通知他们。

虽然安全和隐私必须是为物联网设备设计数据管理系统的主要考虑因素，但易用性也很重要。例如，如果用户忘记了密码，无法访问智能家居或智能医院记录，会发生什么？因此，考虑用户的多因素认证很重要，我们还需要开发适当的标准。例如，必须考虑 SAML 和 XACML 等标准用于认证和授权。因此，用户界面框架必须与数据管理框架集成，以便我们可以确保物联网设备的安全性、隐私性和易用性。

## 13.5 行为方面

可以从收集的数据中分析用户的行为模式（另见 [[SULL2018](#ch13.xhtml#ref13_71)]）。例如，通过分析收集的海量数据，可以检测到用户的习惯，如吸烟、饮酒和吸毒，以及抑郁和可能的情绪波动。虽然这种数据收集可以通过向用户发送有关潜在治疗和建议的信息来造福用户，但也可能导致侵犯用户隐私。因此，我们需要策略感知的数据收集，以便用户能够从建议中受益，而不侵犯其隐私。

我们现在正处于一个多世纪以来最严重的大流行病期间。虽然人们的身体健康至关重要，但我们也需要收集关于人们情绪的信息，以防止他们自杀。因此，分析收集的数据将极大地有助于预防自杀。然而，这也可能侵犯个人隐私。在第 14 章中，我们讨论了与 COVID-19 相关的隐私问题。

## 13.6 走向形式化框架

为了能够容纳任何解决方案，我们需要开发一个形式化框架。在最近的一章中，我们讨论了基于重写规则的形式化框架的某些方面 [[FERN2016](#ch13.xhtml#ref13_25)]。特别是，我们描述了一个通用框架，用户不仅可以指定其数据如何被管理，还可以限制来自其连接设备的数据收集，以及这些数据的存储和分析。更准确地说，我们讨论了使用数据收集策略来管理来自各种设备（例如物联网设备）的数据传输，并结合策略以确保数据一旦传输，就能以安全和保护隐私的方式存储和共享。换句话说，我们讨论了一个用于安全数据收集、存储和管理的框架，具有逻辑基础，能够验证策略属性。然而，我们的主要关注点在于指定和推理数据收集策略的方面。

虽然 [[FERN2016](#ch13.xhtml#ref13_25)] 中讨论的工作是朝着设计这样一个用于指定和推理安全和隐私策略的形式化框架迈出的第一步，但我们需要探索将这种框架用于我们在第 13.3 节中讨论的隐私感知数据管理框架。这是我们正在追求的一个研究方向，同时我们继续进行数据管理框架的更详细设计。此外，我们还将结果应用于互联网交通系统，如图 13.4 所示。

![图 13.4 隐私感知的互联网交通系统。](images/fig13_4.jpg)

[图 13.4 隐私感知的互联网交通系统。](#ch13.xhtml#Ffig13_4)

## 13.7 总结与方向

本章通过一个激励性示例讨论了保护、收集、存储和分析数据的问题。然后，我们讨论了为数据收集、管理和分析设计隐私感知数据管理框架所涉及的挑战。我们还讨论了信息共享的行为方面，以及隐私感知策略管理形式化框架的某些方面。最后，我们简要讨论了形式化框架的必要性，以便无论实施何种解决方案，都可以指定和推理安全和隐私策略。

本章主要提高了在数据管理的所有层面纳入安全和隐私策略的必要性的认识。下一步是进行框架的详细设计和实现。我们还必须设计形式化框架，以便无论实施何种解决方案，都可以指定和推理策略。最后，我们需要将框架适配到互联网交通系统等应用中。

## 参考文献

*   [[ADOM2005](#ch13.xhtml#Cref13_1)] G. Adomavicius, A. Tuzhilin, Toward the Next Generation of Recommender Systems: A Survey of the State-of-the-Art and Possible Extensions, IEEE Transactions on Knowledge and Data Engineering, Volume 17, # 6, 2005, 734–749.

*   [[ALVI2012](#ch13.xhtml#Cref13_2)] M.S. Alvim, K. Chatzikokolakis, C. Palamidessi, G. Smith, Measuring Information Leakage using Generalized Gain Functions, *Proceedings of CSF 2012: 25th IEEE Computer Security Foundations Symposium*, Cambridge, MA, June 2012, pp. 265–279.

*   [[ALVI2014](#ch13.xhtml#Cref13_3)] M.S. Alvim, K. Chatzikokolakis, A. McIver, C. Morgan, C. Palamidessi, G. Smith. Additive and Multiplicative Notions of Leakage, and their Capacities, *Proceedings of CSF 2014: 27th IEEE Computer Security Foundations Symposium*, Vienna, Austria, July 2014, pp. 308–322.

*   [[ANTO2007](#ch13.xhtml#Cref13_4)] A.I. Anton, E. Bertino, N. Li, T. Yu, A Roadmap for Comprehensive Online Privacy Policy Management, Communications of the ACM, Volume 50, # 7, 2007, 109–116.

*   [[APPL2014](#ch13.xhtml#Cref13_5)] Apple Health Web Site, [https://www.apple.com/ios/whats-new/health/](https://www.apple.com). Accessed on 2014 November.

*   [[ASOK2013](#ch13.xhtml#Cref13_6)] N. Asokan, L.V. Davi, A. Dmitrienko, S. Heuser, K. Kostiainen, E. Reshetova, A.R. Sadeghi, Mobile Platform Security. Synthesis Lectures on Information Security, Privacy, and Trust, Morgan & Claypool Publishers, 2013

*   [[BENS2014](#ch13.xhtml#Cref13_7)] A. Bensoussan, M. Kantarcioglu, S. Hoe. A Trust-Score-Based Access Control in Assured Information Sharing Systems: An Application of Financial Credit Risk Score Model. Risk and Decision Analysis, IOS Press, 2014.

*   [[BOLD2009](#ch13.xhtml#Cref13_8)] A. Boldyreva, N. Chenette, Y. Lee, A. O'Neil, Order-Preserving Symmetric Encryption, EUROCRYPT, Cologne, Germany, 2009, pp. 224–241.

*   [[CHAU2011](#ch13.xhtml#Cref13_9)] K. Chaudhuri, C. Monteleoni, A.D. Sarwate, Differentially Private Empirical Risk Minimization, Journal of Machine Learning and Research Volume 12, 2011, 1069–1109.

*   [[CHEE2012](#ch13.xhtml#Cref13_10)] G.P. Cheek, M. Shehab, Policy-by-Example for Online Social Networks. *Proceedings of 17th ACM Symposium on Access Control Models and Technologies, SACMAT ’12*, Newark, NJ, USA. June 20–22, 2012, pp. 23–32.

*   [[CHEN2014](#ch13.xhtml#Cref13_11)] J. Chen, C.S. Gates, R.W. Proctor, N. Li, Framing of Summary Risk/Safety Information and App Selection. *Proceedings of the 2014 Annual Meeting of the Human Factors and Ergonomics Society*, Santa Monica, CA, HFES, 2014.
