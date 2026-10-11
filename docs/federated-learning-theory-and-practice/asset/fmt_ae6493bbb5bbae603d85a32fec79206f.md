
The above analysis may give the impression that FL has only limited benefits in relation to the GDPR. However, FL has a number of important advantages over standard ML in relation to GDPR. Article 25 of GDPR requires *data protection by design*, stating that the data controller shall *implement appropriate technical and organizational measures, such as pseudonymization, which are designed to implement data-protection principles, such as data minimization, in an effective manner and to integrate the necessary safeguards*.

## 21.4 Intellectual property rights relating to federated learning systems

Many of the IP issues in relation to FL are similar to the IP issues in relation to standard ML. However, some special considerations apply to FL, which will be highlighted below.

### 21.4.1 How to protect models created by federated learning

An important question is whether there are any IP rights in the Final Model and who can claim these rights. The most common IP rights relevant for ML models are patents, copyright, and trade secrets. It is possible to receive a patent for algorithms if, to use European terminology, it involves *the use of technical means \[…\] or \[…\] its subject-matter has a technical character*.

An alternative to patents is copyright. Copyright protects the expression of an idea, and covers things like works of literature, music, or paintings.

*Unsupervised learning algorithms and models are unlikely to be regarded as an author's own intellectual creation because the developer plays a small role in the algorithms' functioning. \[…\] Supervised learning algorithms similarly struggle to satisfy \[the requirements for copyright\] as they are often open source, thus not original, with predominantly technical expressions.*

Not all commentators agree with this conclusion.

One such question is who *the person by whom the arrangements necessary for the creation of the work are undertaken* is?

Another issue for FL is that there are potentially many parties who could be entitled to copyright (as well as other IP rights). Copyright, different from patents, is awarded automatically.

Another way to protect algorithms is through trade secrets. For instance, Google, Facebook, and Yahoo use trade secrets to protect their algorithms.

### 21.4.2 Avoiding IP infringement

The FL project needs to ensure that it does not infringe any IP rights. This may happen if conducting the FL project on the local data infringes IP rights in the local data. IP right infringement is also an issue for standard ML, however, this issue is more of a problem for FL because the Aggregator does not have direct control over the data and has to rely on the data sets provided by the Controllers. One way to deal with this issue is to do it contractually. All Participants can enter into an agreement whereby each Controller declares that conducting the FL project does not infringe any IP rights in relation to her local data set. This can be further bolstered by each Controller providing an indemnity to hold other harmless against any loss they may incur if running FL operations on the participants' data set is found to have infringed copyright.

In addition, Participants may be able to take advantage of the *fair use* doctrine. In the absence of a statutory exception for computational uses of copyrighted material, creating models through an FL Process may be *transformative* enough to constitute fair use in jurisdictions that provide protection from liability for such permitted uses. In the United States, where the open-ended fair use doctrine emerged, there is a strong line of cases that have found text and data mining practices and the creation of databases for such material to constitute fair use, particularly on the basis of the *transformative use* doctrine.

Alternatively, there are certain exemptions for text and data mining (*TDM*) under some copyright legislation. The TDM exemptions in copyright law is making inroads in many jurisdictions like the UK, the USA, EU, and Australia.

Although the TDM exception is indeed helpful for collaborative research or study (especially for the purpose of sharing) and data analysis, its usefulness should not, however, be overstated. The exception will apply only where there is analysis performed on the works that have been copied and it is only an exception to copyright infringement and not all other laws protecting data. Hence, data protection laws will still apply if it involves personal data (but note the statutory exceptions that may apply there). Also, the user must have lawful access to the works in the first place if there is one (e.g., through a paid subscription to a subscription-based database) and the work is not made freely available by the copyright holder in the public domain. Rights holders can also implement reasonable measures to maintain the security and stability of their computer systems and networks and the exception does not give the user a right to hack or otherwise circumvent these systems without permission (which is an offence under the computer crime laws in many countries).

## 21.5 Governance structure

The previous sections highlight some of the legal, cultural, and societal issues FL developers need to tackle. In contrast, this section highlights some of legal tools that can be utilized to address some of these issues. This section will sketch out how a successful governance structure can help to deal with some of the key challenges faces by FL. It is important to note that the creation of successful governance structure is not primarily a legal issue, rather it requires business and technological considerations. One problem in analyzing FL governance is that FL structures are highly diverse. An FL Project where the Aggregator has substantial bargaining power, and there are many Controllers with almost no bargaining power, requires a different governance structure than a structure where there is only a small number of Participants who all have substantial bargaining power. Also, if the FL Project is conducted across multiple companies, this will require a different governance structure than if the FL Project is conducted within a single company. Due to size constraints, this section will only analyze the situation where data sets are held by different companies, all the Participants have some bargaining power, and the number or Participants is sufficiently small that meaningful bargaining can take place.

As mentioned in the introduction, one of the key aspects of data sharing is trust. In relation to FL, this means that there needs to be a governance structure that creates trust among Participants, most importantly the Controllers have to trust the Aggregator, and the Aggregator has to trust the Controllers. While it is desirable for there to be trust among the Participants too, this is less important as the Participants do not directly interact with each other. The role of the Aggregator requires trust for several reasons. In some FL Projects, a Controller may receive a benefit in proportion to the quality of the data they contribute, and the Aggregator needs to determine the quality of the data. Another important role of the Aggregator is to distribute the initial model as well as the model updates to the Controllers. The Controller needs to trust that these models do not cause any harm and only *extract* the specific information as agreed. The Aggregator needs to trust the Controller that the Local Data Sets conform to certain parameters, and that the model updates have not been *poisoned*.

In the relevant computer science literature, it is sometimes assumed that the Aggregator can be trusted.

### 21.5.1 Common contractual federated learning projects
