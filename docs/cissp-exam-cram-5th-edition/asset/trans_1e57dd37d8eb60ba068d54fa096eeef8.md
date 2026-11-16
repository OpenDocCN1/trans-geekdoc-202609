

to other users at the same clearance level by means of an access matrix.

Although the Bell-LaPadula model goes a long way in defining the operation of secure systems, the model is not perfect. It does not address security issues such as covert channels. It was designed in an era when mainframes were the dominant platform. It was designed for multilevel security and takes only confidentiality into account.

> **提示**
> 重要的是要知道，Bell-LaPadula 模型处理的是保密性。这意味着，读取高于允许级别的信息会危及保密性。

## 完整性

Integrity is a good thing. It is one of the basic elements of the security triad, along with confidentiality and availability. Integrity plays an important role in security because it can be used to verify that unauthorized users are not modifying data, authorized users don't make unauthorized changes, and databases balance and data remains internally and externally consistent. Whereas governmental entities are typically very concerned with confidentiality, other organizations might be more focused on the integrity of information. In general, integrity has four goals:

- Prevent data modification by unauthorized parties
- Prevent unauthorized data modification by authorized parties
- Reflect the real world
- Maintain internal and external consistency

> **注意**
> Some sources list only three goals of security by combining the third and fourth goals into one: maintain internal and external consistency and ensure that the data reflects the real world.

Two security models that address secure systems integrity include Biba and Clark-Wilson models, which are covered in the following sections. The Biba model addresses only the first integrity goal, and the Clark-Wilson model addresses all four goals.

### Biba Model

The Biba model was the first model developed to address integrity concerns. Originally published in 1977, this lattice-based model has the following defining properties:

- **Simple integrity property**: This property states that a subject at one level of integrity is not permitted to read an object of lower integrity.
- **Star (*) integrity property**: This property states that an object at one level of integrity is not permitted to write to an object of higher integrity.
- **Invocation property**: This property prohibits a subject at one level of integrity from invoking a subject at a higher level of integrity.

> **提示**
> The star property in both the Biba and Bell-LaPadula models deals with writes. One easy way to remember these rules is to think, "It's written in the stars!"

The Biba model addresses only the first goal of integrity: protecting the system from access by unauthorized users. Other types of concerns such as confidentiality are not examined. This model also assumes that internal threats are being protected by good coding practices, and it therefore focuses on external threats.

> **提示**
> To remember the purpose of the Biba model, you can think that the *i* in *Biba* stands for integrity.

### Tibetan Monks and the Biba Model

When learning about the CISSP exam Security Architecture and Engineering domain in the classroom, students are eager for examples related to the material on security models. I typically use the well-known story of Tibetan monks.

After a long journey on your search for Shangri-La and true security awareness, you arrive at a Tibetan monastery. You discover that the monks there are huge fans of the Biba model and, like you, have studied for the CISSP exam. As such, they have defined certain rules that you, the commoner, must abide by:

- A Tibetan monk may write a prayer book that can be read by commoners but not one to be read by a high priest.
- A Tibetan monk may read a book written by the high priest but may not read down to a pamphlet written by a commoner.

Consider this story when you are trying to conceptualize the Biba model, and it might make the task a little easier. A final tip is to look at the star (*) property for both the Bell-LaPadula model and the Biba model and notice how both star properties deal with writes. If this property is applied to Bell-LaPadula, a confidentiality model, the result is *no write down*. If the star property is applied to the Biba model, an integrity model, the result is *no write up*. Just by knowing one, you can easily solve the other.

> **提示**
> Remember that the Biba model deals with integrity and, as such, writing to an object of a higher level might endanger the integrity of the system.

### Clark-Wilson Model

The Clark-Wilson model, which was created in 1987, differs from previous models because it was developed to be used for commercial activities. This model addresses all four goals of integrity. The Clark-Wilson model dictates that the separation of duties must be enforced, subjects must access data through an application, and auditing is required. Some terms associated with this model include the following:

- User
- Transformation procedure
- Unconstrained data item
- Constrained data item
- Integrity verification procedure

The Clark-Wilson model features an access control triple, where subjects must access programs before accessing objects (subject–program–object). The access control triple is composed of the user, a transformational procedure, and the constrained data item. It was designed to protect integrity and prevent fraud. Authorized users cannot change data in an inappropriate way. The Clark-Wilson model checks three attributes: tampered, logged, and consistent (TLC).

The Clark-Wilson model differs from the Biba model in that subjects are restricted. This means that a subject at one level of access can read one set of data, whereas a subject at another level has access to a different set of data. The Clark-Wilson model controls the way in which subjects access objects so that the internal consistency of the system can be ensured, and data can be manipulated only in ways that protect consistency. Integrity verification procedures (IVPs) ensure that a data item is in a valid state. Data cannot be tampered with while being changed, and the integrity of the data must be consistent. The Clark-Wilson model requires all changes to be logged.

The Clark-Wilson model is made up of transformation procedures (TPs). Constrained data items (CDIs) are data for which integrity must be preserved. Items not covered under the model are considered unconstrained data items (UDIs).

> Remember that the Clark-Wilson model requires that users be authorized to access and modify data, and it deals with three key terms: tampered, logged, and consistent (TLC).

### Take-Grant Model

The *Take-Grant* model is another confidentiality-based model that supports four basic operations: take, grant, create, and revoke. This model allows subjects with the take right to remove take rights from other subjects. Subjects possessing the grant right can grant this right to other subjects. The create and revoke operations work in the same manner: Someone with the create right can give the create right to others, and those with the revoke right can remove that right from others.

### Brewer and Nash Model

The *Brewer and Nash* model is similar to the Bell-LaPadula model and is also sometimes referred to as the *Chinese Wall* model. It was developed to prevent conflict of interest (COI) problems. The Brewer and Nash model is context oriented in that it prevents a worker consulting for one firm from accessing data belonging to another, thereby preventing any COI. For example, imagine that your security firm does security work for many large firms. If one of your employees could access information about all the firms that your company has worked for, that person might be able to use this data in an unauthorized way.

### Other Models

A security model defines and describes what protection mechanisms are to be used and what these controls are designed to achieve. The previous sections cover some of the most heavily tested models, but you should have a basic understanding of a few more security models, including the following:

- **Graham-Denning model**: This model uses a formal set of eight protection rules for which each object has an owner and a controller. These rules define what you can create, delete, read, grant, or transfer.
- **Harrison-Ruzzo-Ullman model**: This model is similar to the Graham-Denning model and details how subjects and objects can be created, deleted, accessed, or changed.
- **Lipner model**: This model combines elements of the Bell-LaPadula and Biba models to guard both confidentiality and integrity.
- **Lattice model**: This model is associated with MAC. Controls are applied to objects, and the model uses security levels that are represented by a lattice structure; this structure governs information flow. Subjects of the lattice model are allowed to access an object only if the security level of the subject is equal to or greater than that of the object. Overall access limits are set by having a least upper bound and a greatest lower bound for each security level.

> **ExamAlert**
> Spend some time reviewing all the models discussed in this section. Make sure you know which models are integrity based, which are confidentiality based, and the properties of each; you will need to know this information for the CISSP exam.

> **提示**

