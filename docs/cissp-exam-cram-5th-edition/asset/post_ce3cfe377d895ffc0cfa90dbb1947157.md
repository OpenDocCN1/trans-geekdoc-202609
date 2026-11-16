
![](img/cd307d33c10f35ada49ea76811ef60ad_734_0.png)

FIGURE 9.7 Artificial Neural Network

## Programming Languages, Secure Coding Guidelines, and Standards

Programming languages permit the creation of instructions that a computer can understand. The types of tasks that get programmed and the instructions or code used to create a program depend on the nature of the organization. Programming has evolved through five generations of languages, as illustrated in Figure 9.8 and described in the list that follows:

- Generation 1: Machine language, the native language of a computer, consisting of binary ones and zeros.
- Generation 2: Assembly language, human-readable notation that translates easily into machine language.

![](img/cd307d33c10f35ada49ea76811ef60ad_735_0.png)

FIGURE 9.8 Programming Languages

- Generation 3: High-level programming language. The 1960s through the 1980s saw the emergence and growth of many third-generation languages (3GLs), such as Fortran, COBOL, C++, and Pascal.
- Generation 4: Very high-level language. This generation of languages grew from the 1970s through the early 1990s. Fourth-generation languages (4GLs), such as SQL, are typically used to access databases.
- Generation 5: Natural language. Fifth-generation languages (5GLs) took off in the 1990s and were considered the wave of the future. 5GLs are categorized by their use of inference engines and natural language processing. Mercury and Prolog are two examples of fifth-generation languages.

After the code is written, it must be translated into a format that the computer will understand. These are the three most common methods:

- **Assembler**: An assembler translates assembly language into machine language.
- **Compiler**: A compiler translates a high-level language into machine language.
- **Interpreter**: Instead of compiling an entire program, an interpreter translates a program line by line. Interpreters have a fetch-and-execute cycle. An interpreted language is much slower to execute than a compiled or assembled program, but it does not need a separate compilation or assembly step.

Hundreds of different programming languages exist. Many have been written for specific niches or to meet market demands. The following are some examples of common programming languages:

- **ActiveX**: This language provides a foundation for higher-level software services, such as transferring and sharing information among applications. ActiveX controls are a Component Object Model (COM) technology. COM is designed to hide the details of an individual object and focus on the object’s capabilities. An extension to COM is COM+.
- **C, C++, C++, and C#**: The C programming language, which replaced B, was designed by Dennis Ritchie. C was originally designed for UNIX and is very popular and widely used. From a security perspective, some C functions are known to be susceptible to buffer overflows.
- **HTML**: Hypertext Markup Language (HTML) is a markup language that is used to create web pages.
- **Java**: This is a general-purpose computer programming language, developed in 1995 by Sun Microsystems.
- **Visual Basic**: This programming language was designed to be used by anyone and enables rapid development of practical programs.
- **Ruby**: This object-oriented programming language was developed in the 1990s for general-purpose use. It has been used in the development of such projects as Metasploit.
- **Scripting languages**: A scripting language is a type of programming language that is usually interpreted rather than compiled and allows some control over a software application. Perl, Python, and Java are examples of scripting languages.
- **XML**: Extensible Markup Language (XML) is a markup language that specifies rules for encoding documents. XML is widely used on the Internet.

## Object-Oriented Programming

Multiple development frameworks have been created to assist in defining, grouping, and reusing both code and data. Methods include data-oriented system programming, component-based programming, web-based applications, and object-oriented programming. Of these, the most commonly deployed is object-oriented programming (OOP), an object technology that grew from modular programming. OOP allows a programmer to reuse and interchange code between programs in modular fashion without starting over from scratch. It has been widely embraced because it is efficient and results in relatively low programming costs. Because OOP makes use of modules, a programmer can easily modify an existing program. Java and C++ are two examples of OOP languages.

In OOP, objects are grouped into classes, and all objects in a class share a particular structure and behavior. Characteristics from one class can be passed down to another through the process of inheritance. OOP relies on the following concepts:

- **Encapsulation**: This is the process of hiding the functionality of an object inside that object or, for a process, hiding the functionality inside that process’s class. Encapsulation permits a developer to keep information disjointed—that is, to separate distinct elements so that there is no direct unnecessary sharing or interaction between the various parts.
- **Polymorphism**: In general, polymorphism means that one thing has the capability to take on many appearances or make copies of itself. In OOP, polymorphism is used to invoke a method on a class without needing to care about how the invocation is accomplished. Likewise, the specific results of the invocation can vary because objects have different variables that respond differently.
- **Polyinstantiation**: In general, polyinstantiation means that multiple instances of information are being generated. Polyinstantiation is used in many settings. For example, polyinstantiation is used to display different results to different individuals who pose identical queries on identical databases, due to those individuals possessing different security levels. It is widely used by the government and military to unify information bases while protecting sensitive or classified information. Without polyinstantiation, an attacker might be able to aggregate information from various sources to mount an inference attack and determine secret information. Initially, a piece of information by itself appears useless, like a piece to a puzzle, but when you put together several pieces of the puzzle, you begin to form an accurate picture.

Object-oriented design (OOD) is used to bridge the gap between a real-world problem and a software solution. OOD modularizes data and procedures, making it possible to provide a detailed description of how a system is to be built. Object-oriented analysis (OOA) and OOD are sometimes combined as object-oriented analysis and design (OOAD).

## CORBA

Functionality that exists in a different environment from your code can be accessed and shared using vendor-independent middleware known as Common Object Request Broker Architecture (CORBA). CORBA’s purpose is to allow different vendor products, such as computer languages, to work seamlessly across distributed networks of diversified computers. The heart of the CORBA system is the Object Request Broker (ORB), which simplifies the process of requesting server objects for clients. The ORB locates a requested object, transparently activates it as necessary, and then delivers the requested object to the client.

## Security of the Software Environment

The security of software is a critical concern. Protection of the confidentiality, integrity, and availability of data and program variables is one of the top concerns of a security professional. During the software design phase, you should consider risk analysis and mitigation. It’s critical that the software development team identify, understand, and mitigate any risks that might make the organization vulnerable. Total risk refers to the probability and size of a potential loss. Every development project has elements of risk. For example, in an application that will deal with order quantities, the numbers should be positive; if you made it possible for someone to order negative 17 of an item, you would face added risk. Sanitizing inputs and outputs to allow only qualified values reduces the attack surface. Think of the attack surface as all of the potential ways in which an attacker can attack the application. Integrity of your code can be verified with hashing tools such as MD5sum or SHA1sum.

A vulnerability is a flaw, loophole, or weakness in an application that leads it to process critical data insecurely. A threat actor who can exploit vulnerabilities can gain access to software. Some common software vulnerabilities include escalation of privileges, buffer overflow, SQL injection, cross-site request forgery (CSRF), and cross-site scripting (XSS). It is important to remember that fixing security weaknesses and vulnerabilities at the source code level is much cheaper than waiting until later in the process. Penetration testing and fuzzing are much more expensive than fixing a vulnerability before the build process is complete.

Threat modeling is another technique that can be used to reduce risk and calculate the attack surface. Threat modeling details the potential attacks, targets, and any vulnerabilities of an application. It can also help determine the types of controls needed to prevent an attack. For example, when you enter an incorrect username or password, do you get a generic response, or does the application respond with too much data, as shown in Figure 9.9? Just keep in mind that the best practice from a security standpoint is to not identify which entry was invalid and provide only a generic message.
