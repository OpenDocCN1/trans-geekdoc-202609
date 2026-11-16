# # Bell-LaPadula

Bell-LaPadula is used in government or military implementations and the intent is to protect confidentiality. Like Biba, it is a state machine model, meaning that subjects and objects exist in a single state at a point in time. Bell-LaPadula also identifies a _secure state_ so all transitions should move from one secure state to another secure state. A secure state means that subjects are in compliance with objects as defined by security policy. Only appropriate levels of access are allowed within this model because they are defined and can be evaluated.

As noted, Bell-LaPadula is focused on confidentiality rather than integrity. As a result, the model defines properties that are different from those that were defined in the Biba Model. The Bell-LaPadula properties are defined as follows:

+   - The Simple Security Property says that a subject at one security level may not read an object at a higher security level.
+   - The * (star) Property says that a subject at one security level may not write to an object at a lower security level.
+   - The Discretionary Security Property uses an access matrix to indicate discretionary access.

Bell-LaPadula provides for two mandatory access control rules (Simple Security and * Property) and a single discretionary access control rule. Mandatory access control is handled by the operating system. Rules are created based on policy and they can’t be manipulated by users of the system. Discretionary access control allows users to set their own access rules based on their needs and the data they control. With discretionary access control, the enterprise doesn’t have control over what subjects are allowed to access objects.

# # Clark-Wilson Integrity Model

The Clark-Wilson model is another one that focuses on integrity rather than confidentiality. This doesn’t mean, though, that it is the same as the Biba Model, even if the end result is intended to be the same. Unlike Biba, Clark-Wilson does not rely on a state machine. It also doesn’t make use of subjects and objects exclusively. Clark-Wilson adds in programs. Rather than a state machine, where a subject would act on an object directly, Clark-Wilson expects that subjects act on data objects only through the use of programs. Also, where Biba is used to protect information at higher levels of classification, Clark-Wilson is used and is applicable across all levels of data classification. The overall objective of Clark-Wilson is to maintain the consistency of the data as it moves from one state to another, meaning every transaction leaves the object in a state that makes sense and is usable.

Rather than defining a state machine, as noted, Clark-Wilson defines data items and only allows access through a small number of known programs. Essentially, the program handles the transaction on the object. The model relies on the subject, object, and access program to be known. If any subject other than those allowed attempt to access the object, even through the known program/transaction, it’s a violation. The same is true for attempting transactions that are not defined by attempting to use other programs. This would also