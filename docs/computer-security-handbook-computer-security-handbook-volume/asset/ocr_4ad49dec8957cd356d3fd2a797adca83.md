# 39.1 INTRODUCTION.

Software development can affect all of the six fundamental principles of information security as described in Chapter 3 in this Handbook, but the most frequent problems caused by poor software involve integrity, availability, and utility.

Despite the ready availability of packaged software on the open market, such software frequently has to be customized to meet its users’ particular needs. Where this is not possible, programs must be developed from scratch. Unfortunately, during any software development project, despite careful planning, unforeseen problems inevitably arise. Custom software and customized packages frequently are delivered late, are faulty, and do not meet specifications. Generally, software project managers tend to underestimate the impact of technical as well as nontechnical difficulties. Because of this experience, the field of software engineering has developed: its purpose is to find reasonable answers to questions that occur during software development projects.

# 39.2 GOALS OF SOFTWARE QUALITY ASSURANCE.

In the IEEE Glossary of Software Engineering Terminology, quality is defined as “the degree to which a system, component, or process meets customer or user needs or expectations.” In accordance with this definition, software should be measured primarily by the degree to which user needs are met. Because software frequently needs to be adapted to changing requirements, it should be adaptable at reasonable cost. Therefore, in addition to being concerned with correctness, reliability, and usability, the customer also is concerned with testability, maintainability, portability, and compliance with the established standards and procedures for the software and development process. Software quality assurance (SQA) is an element of software engineering that tries to ensure that software meets acceptable standards of completeness and quality. SQA acts as a watchdog overseeing all quality-related activities involved in software development.

The principal goals of SQA are:

+   - Uncover all of a program’s problems.
+   - Reduce the likelihood that defective programs will enter production.
+   - Safeguard the interests of users.
+   - Safeguard the interests of the software producer.

# 39.2.1 Uncover All of a Program’s Problems.

Quality must be built into a product. Testing can only reveal the presence of defects in the product. To ensure quality, SQA monitors both the development process and the behavior of software. The goal is not to pass or certify the software: the goal is to identify all the inadequacies and problems in the software so that they can be corrected.