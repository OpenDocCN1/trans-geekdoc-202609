
![Remember](images/remember.png)Depending on the kind of PII you obtain, you have the obligation to protect it. Documents, like the one at [`https://www.dol.gov/general/ppii`](https://www.dol.gov/general/ppii) point out some of these requirements. However, if you have obtained medical information, you may have to comply with laws such as Health Information and Accountability Act (HIPAA). Sites such as [`https://www.paubox.com/blog/personally-identifiable-information-hipaa-and-pii-compliance/`](https://www.paubox.com/blog/personally-identifiable-information-hipaa-and-pii-compliance/) tell you how to deal with this sort of information and what PII is included.

The point is that you can’t simply go out and grab PII and expect that everyone will think it’s a good idea. Most people will react negatively to any intrusion into their privacy, whether they left the information out to grab or not. Asking permission and then safeguarding the acquired data is the best route to take. As part of the solution, you must also consider the California Consumer Privacy Act (CCPA), the General Data Protection Regulation (GDPR), and other mandates that require you to obfuscate or delete PII on request (see [`https://www.dataguise.com/blog/how-to-obfuscate-delete-personal-information-of-data-subjects`](https://www.dataguise.com/blog/how-to-obfuscate-delete-personal-information-of-data-subjects)).

## Using Sanitization Techniques

It’s easy to confuse data sanitization with data cleaning (a topic discussed in [Chapter 11](#c11.xhtml)). *Data sanitization* involves removing personal information, such as name, address, telephone number, ID, and so on from a dataset so that identifying a particular individual in a dataset becomes impossible. In addition to text and dataset variables, you must consider every kind of data. For instance, if you are working with collections of photos, it is paramount that you take steps to blur faces and remove car plates from images. Oddly enough, if you perform a Google search using sanitization as a key term, you still get many links dealing with cleaning. Adding privacy as another key term helps find the sorts of articles you actually need. Even so, you may find that you’re not the only one who is confused about the process.

Removing personal information is essential to ensure individual privacy and also meet legal requirements. As mentioned in the opening to this chapter, there are consequences for not ensuring individual privacy. You can apply a number of techniques to meet this goal:

*   **Remove the feature:** When it comes to names, removing the feature will protect privacy, yet keep the data perfectly usable in most cases. This is the best method of sanitization.

*   **Replace the feature:** You may need an ID for the cases in a dataset to identify the case, rather than the user. This process is a little touchier because you can’t create any correlation between the user’s original personal identifier and the new case identifier, which should be a randomized, unique value.

*   **Aggregate features:** With careful aggregation, you can create a new feature that is a mathematical aggregation of several personally identifiable features. A problem occurs when it’s possible to reverse engineer the aggregation into the original values.

*   **Automated sanitization:** You can find algorithms that purport to sanitize data, such as the medical product at [`https://www.researchgate.net/publication/315913699_An_Improved_Data_Sanitization_Algorithm:for_Privacy_Preserving_Medical_Data_Publishing`](https://www.researchgate.net/publication/315913699_An_Improved_Data_Sanitization_Algorithm:for_Privacy_Preserving_Medical_Data_Publishing). However, using automation without oversight can lead to unexpected results. Someone might be able to reverse engineer the process, or the data might become unusable in its new form.

## Avoiding Data Inference

When collecting data, some users will refuse to share personally identifiable information, such as gender and age. One recommendation is to infer this information when a user’s picture or other information is available. For example, a machine learning application might try to infer gender using the person’s name or infer age using facial analysis.

Unfortunately, names that are associated with one gender in a particular culture may be assigned to the other gender in other cultures. People can also choose gender-neutral names from sites like [`https://www.popsugar.com/family/Gender-Neutral-Baby-Names-34485564`](https://www.popsugar.com/family/Gender-Neutral-Baby-Names-34485564), so making an assumption based on name is a bad idea. A person may also identify as being intersex (see [`https://isna.org/faq/what_is_intersex/`](https://isna.org/faq/what_is_intersex/)), rather than male or female, as well as transgender, and so on (you can read more at [`https://interactadvocates.org/faq/intersex-lgbtqia/`](https://interactadvocates.org/faq/intersex-lgbtqia/)), which can bias that person’s perspective on a great many issues.

The problem with age inference is even more profound. For example, a machine learning algorithm will likely infer the wrong age for an albino, which can affect as many as one in 3,000 individuals depending on the part of the world the data comes from ([`https://www.albinism.org/information-bulletin-what-is-albinism/`](https://www.albinism.org/information-bulletin-what-is-albinism/)). If the data is biased toward albinos in any way, you could end up with a lot of old people in the dataset who are actually quite young. The same could be said of premature aging and many other physical changes that can occur naturally.

The bottom line is that it’s not safe to assume anything about a person based on what you think you know about them. Inferring anything is likely to bias your data. If a particular attribute is essential to your analysis and the person hasn’t supplied it, the safest course of action is to remove the case from the dataset.

## Using Generalizations Correctly

Many fields of study today try to incorrectly apply statistics and machine learning outcomes, with the result that an individual ends up being mistreated in some manner. It’s essential to remember that statistics apply to groups, not to individuals. The obverse can also be true: You can’t make a generalization about a group by looking at the group’s individuals. The article at [`https://bigthink.com/Mind-Matters/big-idea-statistics-about-groups-tell-you-nothing-about-individuals`](https://bigthink.com/Mind-Matters/big-idea-statistics-about-groups-tell-you-nothing-about-individuals) discusses both situations to some degree. A problem with many data-gathering techniques is that the individual is asked pointed questions about group membership that end up being untrue because 

*   The individual didn’t understand what group membership meant

*   The individual sees the group in a different perspective from the data gatherer

*   Group membership is ambiguous

*   Group membership is too broad

*   Group membership is too narrow
