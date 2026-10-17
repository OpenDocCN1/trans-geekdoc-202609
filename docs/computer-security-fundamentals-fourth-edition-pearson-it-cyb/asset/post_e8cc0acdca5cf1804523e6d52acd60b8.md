
## SecML
could be coupled with modeling and simulation to fine-tune the cybersecurity system before it is put into operation.

The MSD formula naturally leads to the MPE formula. The mean percentage error (MPE) is the mean number of errors from modeling. In other words, what is the mean error of the model versus actual values. This is critical in modeling as it can be used to evaluate the efficacy of the model itself. Figure 15.4 shows the MPE formula.

In this formula, n is the number of different times for which the variable is forecasted, a_t is the actual value of the quantity being forecast, and f_t is the forecast.

In addition to useful formulas for cybersecurity engineering, reliability engineering involves concepts that are applicable to cybersecurity. For example, the concept of mean time between failures (MTBF) estimates the mean time before a component will fail. For an antivirus software solution this could be the mean time before a given file is misidentified as a virus or not being a virus. The mean time between failures can be calculated as shown in Figure 15.5.

Now this formula does appear in some cybersecurity books (including this one) and is addressed in some certification courses. A more accurate explanation of the MTBF formula can be defined as the arithmetic mean value of the reliability function R(t), which can be expressed as the expected value of the density function f(t) of time until failure.

Don’t panic if this is new math to you. That symbol is the definite integral. I believe integration is often covered in Calculus II in many universities. Clearly the MTBF formula has a clear application to cybersecurity. Understanding when a device is expected to fail is useful information. This can be a measure of the efficacy of a given cybersecurity device or component. It can also be useful in evaluating whether any system or subsystem failure is expected or not. Furthermore, an unexpected failure could indicate an attack. However, this also indicates the need for at least basic calculus as a part of a cybersecurity curriculum.

Another concept from reliability engineering is the mean time to repair (MTTR). That is another metric that is currently covered in many cybersecurity books and certification courses. Continuing with the example of an antivirus software suite, what is the mean time after a virus that is not intercepted, for a system to recover from the infection. This data would allow the cybersecurity engineer to objectively evaluate the cybersecurity system in question.

As outlined previously, cybersecurity engineering is appropriately viewed as a subdiscipline of systems engineering. By integrating elements from other domains within systems engineering, cybersecurity can be elevated to a true engineering discipline. This requires integration of reliability engineering and requirements engineering into cybersecurity. Furthermore, implementing robust and effective modeling techniques. The end result of these efforts is a formal cybersecurity engineering discipline. This engineering discipline is then well defined, and the professional requirements much clearer than the current state of the cybersecurity profession.

This section of the chapter is adapted from a paper written by the book's author. That paper first defined Security Modeling Language (SecML) as a new modeling language.

Systems engineering utilizes a number of approaches to modeling systems and subsystems. Modeling is an integral part of design and testing. In fact, there is an entire field of model-based systems engineering. One of the primary modeling methods utilized in systems engineering is system modeling language, SysML. SysML is an extension of the earlier Unified Modeling Language (UML). UML was created by the Object Management Group (OMG) in order to design software. SysML extends that to modeling a wide range of systems. SysML includes 9 diagrams, some of which are taken directly from UML and others of which were created for SysML.

Software engineering also includes a number of other modeling languages. For example, there are domain-specific modeling languages, such as framework-specific modeling languages (FSMLs). FSMLs are used in object-oriented programming. There are multiple, specific modeling languages for a wide range of software engineering applications.

Systems Modeling Language (SysML) was developed for modeling systems and systems of systems. SysML is the primary modeling tool used in systems engineering. It was originally developed as an open source specification that extended Unified Modeling Language (UML). In 2001 INCOSE started the SysML initiative. Eventually INCOSE worked with the Object Management Group (OMG) to create SysML. SysML v1.0 was released in 2007. The current version of SysML is 1.5 and was introduced in 2017. It is specified in ISO Standard 19514:2017, “Information technology: Object management group systems modeling language (OMG SysML).”

As has been discussed, there are specific modeling techniques and even modeling languages for particular engineering disciplines. If cybersecurity engineering is to be truly defined as a separate engineering discipline, it would also benefit from its own modeling language. This would facilitate modeling that is tailored to cybersecurity needs.

An important part of systems engineering is modeling. In fact, there is an entire subdiscipline of systems engineering concerned with modeling. The concept is to facilitate better understanding of a system at any stage in the system development life cycle.

Being able to simulate and model system behavior can even be used during requirements gathering. This fact supports the need for cybersecurity engineering to include a modeling language.

It is clear the modeling is an integral part of engineering, and particularly systems engineering. It is also true that modeling has been used, in a limited fashion in some aspects of cybersecurity. These facts support the need for a cybersecurity specific modeling language.

What is being proposed in this chapter is a modification to SysML in order to facilitate modeling in security. This modeling is termed SecML and is used to model security needs. The SecML definition uses some SysML and UML diagrams and adds a few new diagrams. The concept is to provide a modeling language that is specific to cybersecurity. Software engineering uses UML and systems engineering SysML; it is only natural that cybersecurity engineering should have a modeling language specific to the domain.

## SecML Concepts
The general concept for Security Modeling Language (SecML) is to provide a modeling tool that can be used to effectively model both cyber-attack scenarios and defense postures. Given that cybersecurity involves systems of systems, it is appropriate to begin with SysML as a basis and modify that modeling language to formulate SecML.

Some of the diagram types are very similar to SysML diagrams with only slight modifications. Other diagram types were created explicitly for cybersecurity applications. Unlike UML, the language SysML is based on, the diagrams in SecML are not divided into categories such as structural, behavioral, or interaction diagrams. However, some clearly are oriented towards behavior or structure. It might seem advantageous to divide the diagrams into attack or defense-oriented diagrams; however, this was intentionally not done. Clearly diagram types such as the misuse-case diagram are appropriate for attack modeling. Similarly, the security block diagram (SBD) could be viewed as a defense-oriented diagram type. However, other diagrams such as the security sequence diagram are appropriate for both attack and defense. Therefore, the diagrams are not divided into attack and defense categories.
