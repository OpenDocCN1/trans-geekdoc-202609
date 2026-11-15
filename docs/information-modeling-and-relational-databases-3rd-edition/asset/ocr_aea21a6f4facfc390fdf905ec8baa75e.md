2. The UML class diagram shown is intended to model the situation where each student is currently enrolled as an undergraduate or graduate (but not both) and plans to finally be an undergraduate or graduate (but not both). For example, some current undergraduate students might plan to go on to do a graduate degree while some other current undergraduate students might plan to never progress to a graduate degree.

![](bbox=[0.303, 0.226, 0.646, 0.359])

(a) Explain what is wrong with the use of StudentType as a “powertype” in this schema.

(b) The schema also lacks a textual constraint. Remodel the situation in ORM (include a textual constraint if needed) to address both these deficiencies.

3. Explain clearly in no more than 100 words why Russell’s Paradox really is a paradox.

4. Consider the following ORM schema.

![](bbox=[0.303, 0.513, 0.568, 0.613])

(a) If the subtype is an instance of LaptopModel, is LaptopModel a higher-order type? Answer yes or no.

(b) Provide in no more than 50 words an interpretation that allows one to think of LaptopModel as a first-order type.

# 10.8 Further Constraints Involving Subtyping

In Fig. 10.72(a), the exclusive-or constraint connects the upper parts of the subtyping arrows. In ORM, an arrow from a subtype to a supertype displays a type-level relationship that implies instance-level, identity relationships linking subtype and supertype instances. For example, the exclusive-or constraint in Fig. 10.72(a) is understood to apply to the supertype roles of the instance-level link fact types shown with dashed lines in Fig. 10.72(b).