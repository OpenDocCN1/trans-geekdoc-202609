
This issue is compounded by the problem that FL may be subject to *poison attacks*, which are aimed *at manipulating the training process by feeding poisoned local model updates to a coordination server*.^()

It may be said that this is less of a problem because to establish the accuracy of the Final Model it is not necessary to examine the Local Data Sets, as all that is needed is to check the accuracy of the Final Model itself. However, although the accuracy of the Final Model is, of course, crucial, it does not mean that the quality of the underlying data is unimportant. The Final Model may be tested by using a validation set; however, what ultimately matters is how the model performs in the *real world*.^()

How to assure data quality in FL and how to guard against poison attacks is currently a very active area of research in computer science.^()

In summary, it is important to recognize that FL has great potential to overcome the challenges posed by data sharing. However, FL has disadvantages in relation to AI ethics. The trade-off between these two competing considerations may be reducible through improved technology and good governance structure, however, it is unlikely that it can be completely eradicated.

Although governments have largely encouraged the development and use of AI to be done according to general ethical principles to allay concerns of trust and to maintain the ‘human focus’ of such innovation, we are starting to see more concrete rules and regulations of AI emerging. This may be the start of a trend towards stronger regulation of AI. For example, as noted previously, on 21 April 2021, the European Union released its proposal for the AIA with a stronger set of rules for the development and use of AI – from regulation to prohibition – according to the risk that the AI poses. The Regulation, if it comes to pass, will mainly require compliance with rules in an organization's internal processes such as data governance, record-keeping, transparency, and user access to information, human oversight, and maintaining a robust, accurate, and secure database.

High risk AI must meet conformity requirements before they can be launched or used, and there is a post-market monitoring system to detect problems and to mitigate them. This is the start of what will likely become more regulation (and forms of regulation) of AI in the years to come. There is also a new Machinery Regulation requiring use of AI-capable machinery to conduct a conformity assessment. Less than a year later, on 23 February 2022, the European Commission also proposed new rules for the access and use of data that is generated in the EU for the economic sector to maintain fair competition. It is likely that other regional groups or countries will follow suit in a bid to pre-empt issues in the use of AI and to ensure its viability, hence any FL projects should keep track of any legislative requirements that may be mandatory to avoid the consequences and liabilities for non-compliance.

## 21.3 Privacy and personal data rights and the international data protection regime

A key benefit that FL is intended to provide is to enable data sharing in compliance with privacy and data protection regulations.^()

### 21.3.1 Does federated learning involve the processing of data?

One of the GDPR's central provisions is that processing of personal data is only allowed if one (or multiple) of the conditions set out in Article 6(1) are met (e.g., the data subject consents^()

Certainly, if there is a way to conduct research without involving personal data at any stage of the process (e.g., differential privacy), that removes the problem entirely. The question of whether something does or does not constitute personal data may be more complex than one might think. For instance, the use of anonymized data may not exempt the data controller from legal responsibility (and liability), depending on when it was anonymized, whether there are tools to de-anonymize or re-identify, and access to other data that, together with the anonymized data, may re-identify an individual. Once personal data is used, the next question is whether there can nevertheless be a way to reduce the administrative burden and impediments to data collection, use or disclosure. Although data protection laws differ in the level of protection accorded to personal data, all have some form of exception to the obligations under the law, acknowledging conflicting interests and other public policy concerns that require some exemptions to strict compliance with these rules.

Returning to the GDPR, even if FL is considered processing, GDPR provides that *processing \[…\] for statistical purposes shall \[…\] not be considered incompatible with the initial purposes*.^()

Under the data protection regime, the obligation to seek consent to the collection, use and disclosure of personal data can be onerous and costly. Many data protection laws have exceptions based on public policy bases. In the EU and some other countries such as Singapore, there is an exception based on *legitimate interest*. Recital 47 of the GDPR states that:

> *The legitimate interests of a controller, including those of a controller to which the personal data may be disclosed, or of a third party, may provide a legal basis for processing, provided that the interests or the fundamental rights and freedoms of the data subject are not overriding, taking into consideration the reasonable expectations of data subjects based on their relationship with the controller.*

This requires a balancing of the legitimate interest of the data controller (and the importance of the processing in question) against the fundamental rights and freedoms of data subjects (including possible harmful effects). As far as research is concerned as a basis, research that is valuable to the controller, and especially to society in general, will carry a higher weight in such an assessment.

In the case of the GDPR, the ‘reasonable expectation’ or the fairness and foreseeability of the personal data processing is key to the exception, which is quite narrow as compared to a legitimate interest that is based on other grounds or considerations such as whether the legitimate interest simply outweighs any adverse effects on the individual.^()

Some countries' data protection legislation has a more specific exception from the consent obligation for personal data for the purpose of research. It is noteworthy that the Singapore PDPA provides for just such an exception, but only in relation to use and disclosure (and not collection).^()

### 21.3.2 Other issues in relation to the GDPR

It is thought that FL is particularly useful in a cross-border setting by facilitating the training of a model on data sets held in different jurisdictions. This is an important issue because of Chapter 5 of the GDPR, which imposes special requirements on transfers of personal data outside the EU/EEA. A similar regime is created by PDPA which imposes special restrictions on transferring data out of Singapore.^()

Another important question is whether a model or algorithm can be personal data for the purposes of the GDPR. If a model itself can be personal data, then GDPR could not only apply to the Local Data Sets but also to the models created by the FL process. This would, for instance, mean that the Aggregator would need to comply with GDPR in relation to the further use of the models. According to the GDPR, data is personal data if it relates to an *identifiable natural person*.^()
