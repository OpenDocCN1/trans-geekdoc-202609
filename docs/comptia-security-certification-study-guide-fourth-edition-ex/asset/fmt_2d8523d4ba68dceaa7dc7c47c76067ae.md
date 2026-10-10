
### Integer overflow

When data is stored in memory, it is assigned a block of memory of a specific size. An integer overflow error occurs when a block of memory has been created to store an integer value, but the result of the arithmetic operation exceeds the maximum size of the integer type assigned. It has been found that the application has unexpected responses to dealing with integer overflows, thus presenting a security issue.

### Buffer overflow

A buffer overflow occurs when software writes to areas of memory outside the areas it has been assigned.

### Pointer/object dereference

Pointers are a tool programmers use to refer to an area of memory. When a programmer wants to read the contents of memory, they `dereference the pointer`. From a security point of view, make sure you block the execution of untrusted or injected code so that hackers cannot read these areas of memory.

#### Why Application Vulnerabilities Exist

You may be asking why these attacks are successful. There are a number of reasons, but it is key to remember that hackers learn technologies in order to figure out how to break them or use them maliciously.

The following are key reasons why application attacks are successful:

### Improper input handling

Input handling is another job for software programmers. Any time data is passed into an application, the programmer is supposed to validate that data and ensure it is appropriate for the task. If the data is invalid, an error is displayed to the user instead of processing the information. If the programmer does not validate input, hackers can inject malicious data into the application to control the software in a manner that is not desired.

### Improper error handling

Error handling is yet another job of software programmers and includes ensuring that the application traps any errors that occur and then handles those errors appropriately so that the application doesn’t crash. When testing the software, developers are looking for the existence of errors. Improper error handling could lead to the program being exploited.

### Default configuration

When installing software or systems, always make sure to change the default configuration as much as possible. Hackers know the default configurations of products and learn how to exploit systems based on the default configurations. You should change the defaults to make hackers more likely to give up and look for easier targets.

### Misconfiguration/weak configuration

Most vulnerabilities exist because software or the operating system has been misconfigured by the administrator and placed in a nonsecure state. Review the configuration of any newly deployed systems and look to following hardening procedures for those systems.

### Weak cipher suites and implementations

Another common vulnerability in systems today is the use of weak encryption technologies or protocols. For example, you may find that an application is encrypting data with the `DES` or `3DES` symmetric algorithm. This is considered weak encryption, and you should upgrade to a stronger algorithm such as `AES`. Another example would be to replace the use of weaker encryption protocols such as `TLS 1.0` and `TLS 1.1` with the newer implementation, `TLS 1.3`.

### New threats/zero day

One of the biggest types of vulnerabilities to be aware of is the zero-day threat, which is an undisclosed or unknown vulnerability that the vendor is not aware of yet, or just became aware of, and thus has had no opportunity to provide a patch to fix it.

### CERTIFICATION OBJECTIVE 15.02

### Secure Application Development Concepts

An overlooked aspect of security is the security in the applications we use day in and day out. It is important to understand how hackers are compromising systems through applications that are running on company systems. The key lesson here is to understand that, as a network administrator, you can do your job and harden the system and ensure that it is up to date with patches, but if one application installed on the system does not follow secure coding concepts, the system could be easily compromised. In this section you learn about the secure coding concepts used to protect against application attacks.

#### Secure Coding Concepts

As mentioned, a big part of securing systems is to ensure that the applications running on the systems have been developed in a secure way. This is up to the application developers—they need to learn secure ways of developing applications so that hackers cannot hack through the application to gain access to the system.

##### Development Life Cycle Models

A `software development life cycle (SDLC)` outlines the major phases to developing an application. There are six phases to the software development life cycle:

### Requirements gathering and analysis

The first phase involves collecting the requirements for the application.

### Design

After the requirements are collected, you then work on designing the application based on the requirements.

### Implementation (coding)

The implementation phase is also known as the coding phase. During this phase, you write the code for the application.

### Testing

After the coding phase, you then must test the code to verify it does what it is supposed to.

### Deployment

After testing, you are ready to install (deploy) the application to the system or systems that need to have the application.

### Maintenance

During maintenance, you typically receive feedback from the persons using the application. You will need to fix any problems that arise with the application in this phase.

There are different software development life cycle models to choose from. Two of the more popular models are the waterfall model and the agile model. They have the same phases but differ in how you move from one phase to the other:

### Waterfall

With the waterfall model, you progress through each phase of the `SDLC` without the capability of going backward in phases at any time. The point is that you must be sure to complete each phase to its fullest so that there is no need to go back (which was viewed as costly when this model was created).

### Agile

With the agile model, you can take a more iterative approach and go to a previous phase if you realize something was missed or needs to be reworked. For example, you could do some requirements gathering, do some design, and then implement a prototype for the customer to review. Then, based on feedback from the customer, you may have to revisit the first few phases to complete requirements gathering and the design of the application. During testing, you may find that you need to change the design or change the code. The agile model views the capability to go back to a phase as critical to application development.

#### Application Environments

It is critical to run your newly created software through a large number of tests to ensure the software was developed following secure programming concepts. This means that the application is to move through different stages or environments within its lifetime. The following is the order of environments the application moves through:

1. **Development** The development environment is where the application is created and debugged to fix any application errors.

2. **Test** After the application is developed, it should be deployed to a test environment, which has all of the essential elements, such as a test database server, for the application to use as it runs in this environment.

3. **Staging** After testing, the application moves to a staging environment, which is as close to the production environment that you can get (think of it as a “fake production” environment). This is essentially the last testing environment for the application before it moves to production.
