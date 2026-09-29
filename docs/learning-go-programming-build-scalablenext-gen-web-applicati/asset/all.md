![](images/cover.jpg)

![image](images/cover.jpg)

# Learning  
Go Programming

![](images/line.jpg)

# *Build Scalable Next-Gen  
Web Application Using Golang*

![](images/line.jpg)

# Shubhangi Agarwal

![](images/logo.jpg)

[www.bpbonline.com](http://www.bpbonline.com)

**FIRST EDITION 2021**

**Copyright © BPB Publications, India**

**ISBN: 978-93-89898-422**

All Rights Reserved. No part of this publication may be reproduced, distributed or transmitted in any form or by any means or stored in a database or retrieval system, without the prior written permission of the publisher with the exception to the program listings which may be entered, stored and executed in a computer system, but they can not be reproduced by the means of publication, photocopy, recording, or by any electronic and mechanical means.

**LIMITS OF LIABILITY AND DISCLAIMER OF WARRANTY**

The information contained in this book is true to correct and the best of author’s and publisher’s knowledge. The author has made every effort to ensure the accuracy of these publications, but publisher cannot be held responsible for any loss or damage arising from any information in this book.

All trademarks referred to in the book are acknowledged as properties of their respective owners but BPB Publications cannot guarantee the accuracy of this information.

**Distributors:**

**BPB PUBLICATIONS**

20, Ansari Road, Darya Ganj

New Delhi-110002

Ph: 23254990/23254991

**MICRO MEDIA**

Shop No. 5, Mahendra Chambers,

150 DN Rd. Next to Capital Cinema,

V.T. (C.S.T.) Station, MUMBAI-400 001

Ph: 22078296/22078297

**DECCAN AGENCIES**

4-3-329, Bank Street,

Hyderabad-500195

Ph: 24756967/24756400

**BPB BOOK CENTRE**

376 Old Lajpat Rai Market,

Delhi-110006

Ph: 23861747

![](images/logo1.jpg)

Published by Manish Jain for BPB Publications, 20 Ansari Road, Darya Ganj, New Delhi-110002 and Printed by him at Repro India Ltd, Mumbai

[www.bpbonline.com](http://www.bpbonline.com/)

# Dedicated to

*My father*  
*Dinesh Chandra Agarwal*

*&*

*My mother*  
*Pushpa Agarwal*

*Who are always with me to love,*  
*support, care and fix all the problems.*

# About the Author

**Shubhangi Agarwal** is an experienced software engineer, who for the past 4 years has been working in information technology industry. In 2017, Shubhangi has started her career with market research industry, moving with IBM India pvt. Ltd., she is currently working as a senior software engineer with Tata Consultancy Services Ltd. In her career, Shubhangi has worked at multiple technologies such as Python, Golang and various backend development events. She is also working as a freelancer helping organizations in their projects and providing the same opportunities to others.

It was back in 2018 that Shubhangi got her taste for writing by her blogs. She shares her views on multiple programming languages, common tech problems & their solution and makes videos on technical content. Shubhangi loves working on latest technologies and sharing the technical insights through her website.

Outside work, Shubhangi loves blogging, photography, travelling, nature and spending time with her family and friends.

If you want to check out her blogs, please visit her website at **[http://momentmate.com/technical/](http://momentmate.com/technical/)**

# About the Reviewer

**Deepak Sharma** is a software developer with a demonstrated history of working in information technology and services industry. He holds a professional degree in Master of Computer Application from Dev Bhoomi Institute of Technology, Dehradun. After working as a data analyst, he is now developing multiple windows application in C, C++ and made a contribution in data & network encryption, HTTP, HTTPS & socket based applications. He was fortunate to review this book. When not programming, he enjoys watching movies and travelling.

**Bhawana Bhatt** is a solution-driven Software Engineer with four year of experience working with Motherson Sumi Systems Limited. She is handling various projects on .Net framework, JavaScript, jQuery, MVC, AngularJs and providing secure, scalable and tested solutions to her clients. She is a master degree holder in Computer Application from Gurukula Kangri Vishwavidyalaya. She is delighted to be part of this book as a technical reviewer. She always welcomes opportunities as well as technical challenges. She enjoys cooking, gardening, crafts and painting.

# Acknowledgement

I want to thank God most of all, because without God I wouldn’t be able to do any of this.

There are a few people I want to thank for the continued and ongoing support they have given me during the writing of this book. First and foremost, I would like to thank my parents and elder sisters, Shuchi and Chanchal who stood by me during every struggle and all my success. I could have never completed this book without their support.

My sincere thanks are due to few friends/TR of this book who encourages and motivate me every time and proves that they are always here for me. Such relations are the perfect example of ‘Quality over Quantity’.

This book wouldn’t have happened if I hadn’t had the support from content editor of BPB Publications. My gratitude goes to the editorial and publishing professionals of BPB Publications for their keen interest and support in bringing out this book

Finally, I would like to thank Manish Jain at BPB Publications for giving me this opportunity to write my first book for them.

# Preface

Golang is developed by Robert Griesemer, Rob Pike, and Ken Thompson in 2007 at Google and publicly announced in November, 2009 as an open-source project. Golang has undergone many alterations and enhancements. Currently we have Go1.15 version that has released on August 2020. Each major Go release is supported until there are two newer major releases. Go is widely used in many organization LinkedIn, Twitter, IBM, Firefox, Docker, YouTube, Alibaba for back-end development.

This book is for the beginners as well as professionals who crave to learn Go language. This book highlights fundamental concepts you will need to learn to do Go programming. In this book, pictorial representation is given to clarify the concept and screenshots are there to describe the process, whenever necessary. To be an adequate Go programmer, a reader must learn it practically by running the programs as specified in this book. These programs will not only perform correctly but it is simple to write and understand. Comments are well mentioned with the programs that describes the purpose of specific statement/block. Output of specific program is thoroughly given so that one can verify it after running the code. Each chapter contain objective that describes how the specific chapter could be useful for a reader. At the end of each chapter, conclusion section refers brief or highlights content of the chapter and establish a link to the next chapter.

This book will help for those who don’t have any programming experience. Specific instructions are given to write and run the first Go program. Good examples are given with each and every concept. After getting the required basic knowledge of Golang, we are creating a small application in Go. All the necessary code is well described in sample programs that can be implemented in all modern browsers. If a reader study and learn the concept mentioned in this book, he’ll be on the way to become a Go Programmer who knows the features of Go language, how it works, how to use and how to build an application by consolidating the front-end and back-end technology in Golang.

The primary goal of this book is to provide information and skills that are necessary to learn Go language. This book contains numerous examples and illustrations that will show you how to install, and run the Go programs, as well as how to integrate Golang with front-end to build an application. Over the 20 chapters in this book, you will learn the following:

**[Chapter 1](#c01.xhtml)** introduces the evaluation of Go language, its success, characteristics and applications. It explains the need of Go language and analogies that makes it different from other programming languages.

**[Chapter 2](#c02.xhtml)** discusses Golang system requirements and how to install them is shown in easy to follow, step-by-step instructions using an actual screenshot.

**[Chapter 3](#c03.xhtml)** assists to start working with Go language. With this chapter one can write first Go program with basic understanding of Golang’s syntax, keywords, identifiers, comments and many others.

**[Chapter 4](#c04.xhtml)** is a key chapter which discusses, in depth, what a variable & constant is and how to declare and initialize them, understanding of format specifiers and then explains various data types we have in Go language.

**[Chapter 5](#c05.xhtml)** covers how the data computation is performed by using operators, type of operators and how to use them with Go language.

**[Chapter 6](#c06.xhtml)** describes the control flow in which various statements, functions or instructions get executed in a program. It gives an idea of several control structures and how to use them in Golang.

**[Chapter 7](#c07.xhtml)** defines what is function in programming language, type of functions, how it works and how to use them in Golang

**[Chapter 8](#c08.xhtml)** introduces an image of package in Go language. This is nothing but a collection of multiple Go source files or other predefined/ custom packages.

**[Chapter 9](#c09.xhtml)** elaborates a data structure – array, collection of same data types.

**[Chapter 10](#c10.xhtml)** clarifies non primitive data type – string and strings package in Go language.

**[Chapter 11](#c11.xhtml)** defines the concept of Pointers, its type and use by various examples.

**[Chapter 12](#c12.xhtml)** describes a user-defined data type – structures, fusion of multiple data types.

**[Chapter 13](#c13.xhtml)** explains composition, a process of reusability the code block.

**[Chapter 14](#c14.xhtml)** elaborates the concept of Interfaces and explains how polymorphism is achieved by using interfaces.

**[Chapter 15](#c15.xhtml)** addresses Golang data type - Maps, contains unordered collection of key-value pair as its element.

**[Chapter 16](#c16.xhtml)** elaborates the concept of concurrency, an ability to share resources with various parts of a program at the same time.

**[Chapter 17](#c17.xhtml)** discusses resource locking/ unlocking mechanism to synchronize the process.

**[Chapter 18](#c18.xhtml)** explains an idiomatic way to handle errors in Go language. This chapter confers about error data type and its uses.

**[Chapter 19](#c19.xhtml)** defines run-time reflection that is used to manipulate the type and value of any object.

**[Chapter 20](#c20.xhtml)** discusses Golang can be used in conjunction with HTML, CSS, Gopherjs, MYSQL to build an application.

# Downloading the code  
bundle and coloured images:

Please follow the link to download the  
***Code Bundle*** and the ***Coloured Images*** of the book:

# [https://rebrand.ly/d4e5c](https://rebrand.ly/d4e5c)

# Errata

We take immense pride in our work at BPB Publications and follow best practices to ensure the accuracy of our content to provide with an indulging reading experience to our subscribers. Our readers are our mirrors, and we use their inputs to reflect and improve upon human errors, if any, that may have occurred during the publishing processes involved. To let us maintain the quality and help us reach out to any readers who might be having difficulties due to any unforeseen errors, please write to us at :

**[errata@bpbonline.com](mailto:errata@bpbonline.com)**

Your support, suggestions and feedbacks are highly appreciated by the BPB Publications’ Family.

Did you know that BPB offers eBook versions of every book published, with PDF and ePub files available? You can upgrade to the eBook version at **[www.bpbonline.com](http://www.bpbonline.com)** and as a print book customer, you are entitled to a discount on the eBook copy. Get in touch with us at **[business@bpbonline.com](mailto:business@bpbonline.com)** for more details.

At **[www.bpbonline.com](http://www.bpbonline.com)**, you can also read a collection of free technical articles, sign up for a range of free newsletters, and receive exclusive discounts and offers on BPB books and eBooks.

# BPB is searching for authors like you

If you're interested in becoming an author for BPB, please visit [**www.bpbonline.com**](http://www.bpbonline.com/) and apply today. We have worked with thousands of developers and tech professionals, just like you, to help them share their insight with the global tech community. You can make a general application, apply for a specific hot topic that we are recruiting an author for, or submit your own idea.

The code bundle for the book is also hosted on GitHub at **[https://github.com/bpbpublications/Learning-Go-Programming](https://github.com/bpbpublications/Learning-Go-Programming)**. In case there's an update to the code, it will be updated on the existing GitHub repository.

We also have other code bundles from our rich catalog of books and videos available at **[https://github.com/bpbpublications](https://github.com/bpbpublications)**. Check them out!

# PIRACY

If you come across any illegal copies of our works in any form on the internet, we would be grateful if you would provide us with the location address or website name. Please contact us at [**business@bpbonline.com**](mailto:business@bpbonline.com) with a link to the material.

# If you are interested in becoming an author

If there is a topic that you have expertise in, and you are interested in either writing or contributing to a book, please visit [**www.bpbonline.com**.](http://www.bpbonline.com/)

# REVIEWS

Please leave a review. Once you have read and used this book, why not leave a review on the site that you purchased it from? Potential readers can then see and use your unbiased opinion to make purchase decisions, we at BPB can understand what you think about our products, and our authors can see your feedback on their book. Thank you!

For more information about BPB, please visit [**www.bpbonline.com**.](http://www.bpbonline.com/)

# [CHAPTER 1](#toc.xhtml#c01)

# [Introduction to Go](#toc.xhtml#c01)

Programming languages enable us to communicate with computers by developing various types of programs and applications. We have multiple programming languages in our technical world such as C, C++, PHP, Python, Ruby, and many others. Go language is one of those growing programming languages that solves many issues that we get from the other languages. Let’s go through the evolution of the Go language, its features, scope, and use in the technical field.

# [Structure](#toc.xhtml#s1a)

In this chapter, we will discuss the following topics:

*   Software essence
*   Evolution of Go language and its success
*   Characteristics of Go language
*   Object-oriented nature of Go language
*   The analogy with other languages
*   Pain points of Go language
*   Application of Go language

# [Objective](#toc.xhtml#s2a)

After studying this chapter, you’ll be able to understand the:

*   Evaluation of Go language
*   Need for Go language
*   Characteristics of Go language
*   How it is different from other programming languages
*   Applications developed in Go language

# [A look at software essence](#toc.xhtml#s3a)

At the time of Go’s initiation, complexity was the major concern in software development. Usually, development used to be done by C++ or Java but there were some challenges with them like security, memory utilization, speed, efficiency, debugging, etc. Software should have the power to function correctly against potential risks produced by malicious attacks. Dead objects shouldn’t exist to avoid resource blocking and improve the efficiency of software.

# [Evolution of Golang and its success](#toc.xhtml#s4a)

By looking at the problems with software development, it was decided that with a rise of networked and multicore computing, a language must support some sort of concurrency and parallelism, garbage collection, and should automate memory management. All that reflected into a thread of discussion, a bunch of ideas, decent strategy, and finally a great development. With Golang, efficient compilation, execution, and ease of programming are all possible with one language.

**Go language** is sponsored by Google and created by Robert Griesemer, Rob Pike, and Ken Thompson have depicted the goals of Golang. It finally came out in public on November 10, 2009. It is an open-source language. Go language’s creators and the community have built many tools which are natively supported by the language core, that in most cases don’t need any third-party library. For example, Go language has HTTP, JSON, HTML template, built-in language natively, and it can build very complex API services without even thinking about finding a library on GitHub. Now, millions of programmers are working on Go and many more are to come.

![](images/image-1.1.jpg)

**Figure 1.1:** Logo change in April 2018

# [Characteristics of Go](#toc.xhtml#s5a)

Go is a statically and fast-compiled language that is designed to be used with multicore architecture for efficient memory utilization. Here are some features of Golang:

*   **Automatic garbage collection**
    
    With this feature, the programmer does not need to worry about how the memory will be managed all around. Currently, “mark-and-sweep” collector is used in Go. It keeps track of all the created objects. Whenever necessary, it first pauses the running process, works on garbage objects, and then frees the process to run again. It also supports concurrency.
    
*   **Concurrency**
    
    To run more than one task simultaneously is called concurrency. Golang provides a different approach to execute multiple functions at the same time. That is possible with Goroutines and channels. In Go, Goroutines can be considered as the functions that can be executed parallelly with other functions. On the other hand, the channel provides functionality to communicate between multiple Goroutines.
    
*   **Static**
    
    Golang is built as a compiled language, and Google developers did a great job with it. Using static linking, it combines all dependent libraries and modules into one single binary file based on OS type and architecture which means that while compiling the backend application, just upload the compiled binary into the server and it will work without installing any dependencies there.
    
*   **Ease testing**
    
    Go language offers a rich library that supports automated testing. Here is a package called `testing` that helps to run the go `test` command which makes the execution of any testing function possible. There are some benchmarks. There are many forms of testing functions that are executed by go `test` commands.
    
*   **Standard library**
    
    The important part of good programming is **code reusability**. The standard library of Go language contains a huge number of packages that provide great functionality for Go applications. It provides packages like OS, runtime, HTTP, XML, and JSON that connect with operating systems and give support for runtime.
    
*   **Cross-platform**
    
    Go is a cross-platform language that can run on Linux, Mac, Free BSD, Windows, iOS, Android, and others.
    
*   **Documentation**
    
    Golang has a command `Godoc` that concentrates on package documentation and serves it as HTML or plain text. With the help of this documentation, the programmer can steer from illustration to the implementation of any function. It defines a package’s functions, constants, variables, and even the type that Go supports.
    

# [Object-oriented nature](#toc.xhtml#s6a)

A standard definition of object-oriented language doesn’t work with Go but it provides the same functionality in some other manner. There is a defined data structure `struct` that integrates fields and methods. Golang has no inheritance but it has a different approach to establish the relation between structs. Object composition establishes a IS-A relationship, whereas interfaces are used to form Has-A relation.

Furthermore, methods in the Go language are more transparent. They are not bound with structs. Go doesn’t support the feature of overloading. In this way, Go language makes things simpler and more convenient.

# [The analogy with other languages](#toc.xhtml#s7a)

In C++, Java, and other object-oriented languages, inheritance, overloading, and generic types are the key features. Here, the Go team focuses on concurrency, garbage collection, and fast compilation to work well with parallel systems. Let’s go through some nuts and bolts of the programming language:

*   **Type-safe**
    
    This refers to a feature to prevent “`type`” errors. Just like C, C++, Java, and Python, Go is also a type-safe language. The Go compiler meets a certain level of validity at the time of compilation. It ensures that if there is “+” operator, then both the operands are of numeric type.
    
*   **Object-oriented**
    
    Go can be considered as a light-weight object-oriented language. However, it supports types and methods that can be defined for any sort of data but have no classes and inheritance. Not everything is an object associated here. Go syntax resembles the C language. It is statically typed and scalable to larger systems like C++ and Java.
    
*   **Inheritance**
    
    Go is not an object-oriented language. It doesn’t support inheritance but it has a feature of composition and interfaces. With composition, it is possible to embed more than two structs together. Multiple methods can be added in interface, and thus, it has a chance to grow. This new concept is more powerful than the class-based inheritance.
    
*   **Overloading**
    
    Go doesn’t have a concept of method and operator overloading unlike C++ and Java. Identifying methods by only their name removes complexity and makes it simple to code.
    
*   **Exception handling**
    
    Unlike C++ and Java, there are no try-catch-finally idioms in Go. It has some built-in functions to signal and recover the exceptional conditions. Go functions return the error as the last value. Here is a simple mechanism: the last value is compared to “nil.” If it is, there is no error; otherwise, there would be an error.
    
*   **Concurrency**
    
    In Java, there is an option of threads for concurrent programming. Java has a lot of utilities to manage those threads but still, it is considered quite expensive and hard to understand. To make it simple, Go has a simple technique for concurrency with the feature of Go routines and channels. Go routines are light-weighted threads, and the channel helps to communicate between Go routines.
    
*   **Garbage collection**
    
    Generally, there are two ways of memory management. One is automatic reference counting and the other one is a garbage collection. Like C# and Java, Go also has a garbage collector. With Objective-C, Swift uses the reference counting technique to manage the resources. Current GC “mark-and-sweep” is used with Go language. It runs on a separate CPU, parallel with main programs, and thus, it helps with multicore architectures.
    

# [Pain points of Go language](#toc.xhtml#s8a)

With multiple features, Golang has some disadvantages. The limitations of Go language are as follows:

*   **Generic Programming**
    
    Go doesn’t have compile-time generics that lead duplicate code or typecast as per requirement. However, there are first-class functions but we can’t reuse the same functions with a different type of collection. It somehow affects efficiency and productivity as well.
    
*   **Tedious error handling**
    
    Error handling is not perfect in the Go language. There is no execution carried out from the compiler to handle the error. It depends on the programmer as to how the functions can be used to return the error whenever it occurs.
    

# [Applications of Golang](#toc.xhtml#s9a)

Go has been gaining popularity since it was first announced in 2009. A few companies are working on the Go language such as IBM, Twitter, Facebook, YouTube, Apple, BBC, Google, and many others. No one can predict the future, but Golang has multiple reasons to grow.

Here are some applications that are developed in the Go language.

*   **Docker**
    
    It is a set of tools to create, deploy, and run the distributed application.
    
    It is an open-source platform that allows the extending of its features if needed.
    
*   **OpenShift**
    
    An open-source cloud computing platform provided as a service by Red Hat.
    
    It provides the service for container-based software deployment and management.
    
*   **Kubernetes**
    
    It is an extensible open-source container cluster management system that promotes seamlessly automated deployment processes.
    
*   **Dropbox**
    
    Dropbox migrated from Python to Go language to scale its system in a more efficient manner and that supports better concurrency and fast execution.
    
*   **InfluxDB**
    
    It is an open-source time-series database that fetches time series data.
    
    It supports the Internet of Things sensor data, application matrices, and real-time analytics.
    

# [Conclusion](#toc.xhtml#s10a)

In this chapter, you learned the pain points of software development and how the evolution of the Go language resolved them. This open-source programming language makes software development easy, efficient, and reliable. We saw some applications of various organizations developed with Go language. We discussed some disadvantages of Go language that we need to remember while programming in Golang. This is all the theoretical knowledge we need to know. Let’s go ahead with the installation of Go language in the next chapter.

# [Questions](#toc.xhtml#s11a)

1.  Who developed the Go language?
2.  How does garbage collection work in Go language?
3.  Which command illustrates Go language documentation?
4.  In what ways is Go language different from other programming languages?
5.  How are fields and methods integrated into Golang?
6.  Go is a “concurrent language.” What does that mean?

# [CHAPTER 2](#toc.xhtml#c02)

# [Environment Setup](#toc.xhtml#c02)

After becoming aware about the Go language, let’s move on to the Golang system requirements and installation process. This chapter defines the system requirements to install Golang, text editors to write Golang programs, and all about the installation and uninstallation process with various operating systems. After installing Go, the first Golang program to check the proper installation is illustrated.

# [Structure](#toc.xhtml#s12a)

In this chapter, we will discuss the following topics:

*   System requirements for Go language
*   Suitable text editors
*   How to install/uninstall Go on your system
*   How to write the first test program on Go

# [Objective](#toc.xhtml#s13a)

After studying this chapter, you’ll be able to:

*   Get the suitable text editor for Go language
*   Install Golang on your system
*   Write a test program on any text editor
*   Run a simple Go program
*   Uninstall Go if there are any issues

# [System requirements](#toc.xhtml#s14a)

Go targets multiple platforms like Linux, Mac, FreeBSD, Windows of 32-bit, and 64-bit x86 processor architectures. In case of any other operating system, one can use gccgo, the compiler of Go language.

Go1.15 is the latest version of Go and was released in 2020. First, it required OpenBSD 6.2, then later, Mac OS 10.10 Yosemite, and then, Windows 7. Supports for previous versions of these operating systems have been removed.

To run a simple Go program, there is a need for text editor and Go compiler. These could be as follows:

*   **Text editors**
    
    Go supports a variety of editor plugins and IDEs to make Go development more productive and seamless. There are most of the well-known text editors that either directly facilitate or through some plugins. Text editors can vary with different operating systems.
    
    Here are some text editors:
    
    1.  **Atom**
        
        **Atom** is a free and open-source text editor for Windows, Linux, and macOS.
        
        It is a cross-platform java-script oriented desktop application from GitHub.
        
    2.  **BBedit**
        
        **BBedit** is a commercial text editor developed for macOS.
        
        Go-bbpackage comes with clippings, ctags standard library completion, better syntax highlighting, and tools.
        
    3.  **Eclipse IDE**
        
        **Eclipse IDE** is the most widely used open-source cross-platform IDE.
        
        GoClipse is an Eclipse extension that adds IDE functionality to Go language.
        
    4.  **Emacs**
        
        **Emacs** is free and loaded by multiple extensible and customizable text editors.
        
        Code auto-completion, code analysis and refactoring, error checking, playground and code snippets are additional features of Emacs.
        
    5.  **Gedit**
        
        **Gedit** is a default text editor for the GNOME desktop.
        
        Go-gedit-plugin is a Go programming plugin for gedit editor.
        
    6.  **Goland**
        
        **Goland** is a commercial cross-platform IDE by JetBrains.
        
        The IDE analyzes the code, connection between symbols, quick navigation, error analysis, formatting and refactoring.
        
    7.  **Notepad++**
        
        **Notepad++** is a distributed source code text editor for Microsoft Windows.
        
        GOnpp plugin provides code completion, function call tips, Go imports integration, and keyboard shortcuts for common Go commands.
        
    8.  **Sublime Text**
        
        **Sublime Text** is a free cross-platform source code editor that supports auto-save, customizable key binding, macros, and many others.
        
        GoSublime is a Golang plugin collection that provides the feature of code completion from Go code, automatically adding/removing package imports, etc.
        
    9.  **Vim**
        
        **Vim (VI improved)** is a free open-source text editor for Unix.
        
        It is designed to use both from a command-line interface and as a standalone application in a graphical user interface.
        
    10.  **Visual Studio**
         
         **Visual Studio** is a commercial IDE for Windows to develop websites, web apps, web services, and mobile apps.
         
         With Visual Studio, the Go extension supports for multiple features like IntelliSense code auto-completion, hover information, signature help, snippet, etc.
         
*   **Cloud-based IDEs**
    
    Development of cloud IDEs is a great innovation in the software industry. In such IDEs, the developer’s atomic services like syntax analysis, build, run, and debug are operated on separate horizontally-scalable microservices. These are some cloud IDEs:
    
    1.  **Cloud9**
        
        **Cloud9** is an online open-source multi-language cloud-based IDE.
        
        It connects with GitHub, Bitbucket, and Google cloud platform repositories.
        
        It has MySQL and other databases; and terminal and immediate windows.
        
    2.  **CodeEnv**
        
        **CodeEnv** is also an open-source multi-language cloud-based IDE.
        
        It is a browser editor that has a feature to edit, build, run, and debug the project.
        
    3.  **Wide**
        
        **Wide** is a web-based IDE for Go language.
        
        It uses a code mirror-based themed programming editor with Gocode-assisted syntax highlighting, auto-completion, and real-time collaboration.
        
    4.  **Micro**
        
        **Micro** is a toolkit for cloud-native development.
        
        It provides an opinionated framework for developing applications with a pluggable architecture.
        
*   **Compiler**
    
    There are several compilers running for Go language that help to set up the Go environment. Two major implementations of Go compiler areas:
    
    1.  **Gc**
        
        **Gc** is a default compiler with a recursive descent parser and it uses a custom loader. It supports popular processors like x86 (32/64bit) and ARM.
        
    2.  **Gccgo**
        
        **Gccgo** is a part of GCC, the GNU compiler collection that supports the front-end. It supports all the processors that GCC supports. Gccgo is slower than Gc but supports more processors and has more powerful optimization and so, a CPU-bound program built by gccgo will run fast.
        
        A third Go compiler also exists which is known as GopherJS. It compiles Go code into java-script code and enables Go to be used for front-end development that runs in all browsers.
        

# [How to install](#toc.xhtml#s15a)

The following procedures prepares an environment to install Go on various platforms.

*   **Windows installation**
    
    Here are the steps to install Go on the Windows machine.
    
    1.  One can visit the Go page on golang.org and download Go.
        
        ![](images/image-2.1.jpg)
        
        **Figure 2.1:** ‘golang.org’ home page
        
    2.  Download MSI or zip file as per the system requirement.
        
        ![](images/image-2.2.jpg)
        
        **Figure 2.2:** Go for multiple OS
        
    3.  Various versions of Golang are listed below:
        
        ![](images/image-2.3.jpg)
        
        **Figure 2.3:** Select as per your system configuration
        
    4.  Follow the prompts: `Run |Next`
        
        ![](images/image-2.4.jpg)
        
        **Figure 2.4:** Run file
        
    5.  Here are some license agreements that need to be accepted to install Golang.
        
        ![](images/image-2.5.jpg)
        
        **Figure 2.5:** Accept License Agreement
        
    6.  Either keep the directory as it is in C drive and go next.
        
        ![](images/image-2.6.jpg)
        
        **Figure 2.6:** Check the directory
        
    7.  Or change the directory as below:
        
        ![](images/image-2.7.jpg)
        
        **Figure 2.7:** Click on change button
        
        ![](images/image-2.8.jpg)
        
        **Figure 2.8:** Set required directory path
        
    8.  Ready to install
        
        ![](images/image-2.9.jpg)
        
        **Figure 2.9:** Install
        
    9.  When the installation is completed, the Go folder is created in the selected directory as:
        
        ![](images/image-2.10.jpg)
        
        **Figure 2.10:** Go’s default directory after installation
        
    10.  If we change the directory path at the time of installation, it would be as:
         
         ![](images/image-2.11.jpg)
         
         **Figure 2.11:** Go’s directory (depending on the given path)
         
    11.  Now, navigate to the bin folder of Go and set it as system path variable. Navigate as follows:
         
         `Control Panel|System and Security|Advance system settings|Environment Variables`
         
         ![](images/image-2.12.jpg)
         
         **Figure 2.12:** Control Panel
         
         ![](images/image-2.13.jpg)
         
         **Figure 2.13:** Advanced system settings
         
    12.  Append bin path at the end of a path variable.
         
         ![](images/image-2.14.jpg)
         
         **Figure 2.14:** Environment Variables
         
         ![](images/image-2.15.jpg)
         
         **Figure 2.15:** Set path
         
    13.  The path is all set. Now create and run the Go sample program. For this, create a workspace for Go projects. It can be on the same directory but the folder must be different from the Go folder.
    14.  Install sublime or any supported text editor and write your first Go program as follows:
         
         `package main`
         
         `import "fmt"`
         
         `func main(){`
         
         `fmt.Printf("hello, world\n")`
         
         `}`
         

**Note: Explanation of this program is in the next chapter.**

Save this file with go extension as `file_name.go` in your workspace.

Ready to run the first Go program? Open command-line interface and navigate to the created workspace. Run command as: go run `file_name.go`

![](images/image-2.16.jpg)

**Figure 2.16:** Run test program

*   Linux/ MacOS X and FreeBSD Installation
    
    Download the package file from the same source as described above and follow the prompts to install Go tools. Go tree is installed in `/usr/local/`go. Now add the bin path to the system path environment variable. There could be a need to restart the open terminal session for the change to reflect. After that, you are ready to run the Go program.
    

# [Uninstalling Go](#toc.xhtml#s16a)

To remove an existing Go installation from your system, delete the Go directory. This is usually in `/usr/local/`go in Linux, macOS, and FreeBSD or `c:\Go` in Windows.

# [Conclusion](#toc.xhtml#s17a)

In this chapter, we saw that Go is available for various platforms like FreeBSD, macOS, Windows, and Linux on its 32-bit and 64-bit processor architectures. We can check our system configuration and install the suitable version of Go. To install any upgraded version, you need to first uninstall the existing one. Multiple text editors and IDEs have been discussed in this chapter and each one has its features. At last, we can check for a successful installation by running a test program on Go. In the next chapter, we’ll discuss the basic structure of the Go program in depth.

# [Questions](#toc.xhtml#s18a)

1.  Which platforms is Go language supported on?
2.  Which compiler works for Go language?
3.  Specify the default compiler in Go language.
4.  Which file extension is used to write Go programs?
5.  Specify the command to run Go programs.

# [CHAPTER 3](#toc.xhtml#c03)

# [Beginning With Go](#toc.xhtml#c03)

In the last chapter, we discussed the installation of the Go language. By now, we hope that Go is all set on your system. In this chapter, we’ll see the basic structure of the Go program, the components it is divided into, and the purpose of these components. In every programming language, keywords and identifiers play an important role. Here, we’ll discuss Golang’s supported keywords and identifiers as well.

# [Structure](#toc.xhtml#s19a)

In this chapter, we will discuss the following topics:

*   Introduction to Go program
*   Keywords
*   Identifiers

# [Objective](#toc.xhtml#s20a)

After studying this chapter, you’ll be able to:

*   Write a simple Go program
*   Use comments in Go program
*   Understand keywords in Go language
*   Understand the role of identifiers in Go

# [Introduction](#toc.xhtml#s21a)

Let’s begin with the basic structure of the Go program. A simple Go program consists of defining the program as a package, importing packages, classes, functions, variables, comments (if required), and the required statements.

`package main`

`import (`

`"fmt"`

`)`

`/* This is a multiline comment */`

`//This is a single line comment`

`func main(){`

`fmt.Printf("Hello World\n")`

`}`

The first line defines the program as a package named main. This statement is necessary for every program that we are creating. As Go is a case-sensitive language, we need to make sure that the name of the package doesn’t start with a capital letter.

`fmt` is a package. It refers to a format that supports formatted I/O functions like `scan` and `printf` and many more. Here, `fmt` is to be used as a string. That’s why we are writing it in double-quotes. `fmt` becomes the prefix for all those functions that are defined in `fmt` package.

The third line refers to comments that are ignored by the compiler. There are two ways to represent the comments. Either use /\* or // to show the comments in Go.

`func` is a keyword that indicates the function declaration. The **function** is simply a piece of code to perform a particular task. It enhances the reusability of code. Every Go program is defined within the function. Here, the name of the function should be similar to the package name. It only runs the main function here, executes the statements defined within the function, and exits when it returns from this function. Other than the main function, we can create other functions also but all these functions would be called within the main function only.

If we don’t keep the package or function name as per standard, it could throw an error as follows:

![](images/3-1.jpg)

**Figure 3.1:** non-main package error

It will show the following error if it is not declared as the main function in Go program.

![](images/3-2.jpg)

**Figure 3.2:** undeclared function error

As described in the previous chapter, we can run this program on the command prompt by using the following command:

`go run file_name.go`

1.  On the next line, we will declare the variables if required. As Go is a statically typed language, variables are not allowed to change their type at run time. We can define the variable as **name:= “Jitendra”**. It’ll identify the type of variable by its value.
2.  "Printf" is a function defined in the fmt package. All the exported names should start with a capital letter.
    
    Function in Go is the root of the family. Program execution starts with a function call; it could be assigned to a variable, passed as an argument. The Go compiler starts the execution from the main package. It takes the appropriate file, compiles it, convert it into the temporary executable form, and runs the program. It completely follows the main function in the main package.
    

# [Keywords](#toc.xhtml#s22a)

Keywords are predefined reserved words specific to the programming language that have special meaning for the compiler. Keywords cannot be used as variables or identifiers. Golang supports 25 keywords. They are as follows:

*   `import` : This keyword is used to import a package in a Go program.
*   `type:` This is used to create a new type as per the requirement.
*   `const:` This specifies a character, numeric, boolean, or string value.
*   `var:` This keyword is used to declare a variable containing a specific name and value.
*   `func:` This keyword is used to declare functions with a specific name, parameter, result type, and body.
*   `package:` This defines packages in Go program that contain variable, constant, and functions.
*   `map:` This keyword declares the data of type map in a Go program.
*   `chan:` The chan keyword is used to define a channel in a Go program.
*   `struct:` A user-defined type "struct" is declared by using this keyword.
*   `interface:` This keyword is used to define a custom data type "interface" in Golang.
*   `if:` If the keyword specifies "if statement," it needs to evaluate the given condition.
*   `else:` else keyword executes the statement if the condition given in the block is false.
*   `for:` This keyword executes for a statement that repeatedly executes a block of code.
*   `range:` This keyword is used with for loop to iterate over a specific given data.
*   `break:` This defines the break statement inside a loop to terminate the current loop execution and resumes the program control next to the loop.
*   `continue:` This defines continue statement inside a loop to jump the program control on the next iteration.
*   `goto:` This executes the goto statement and transfers the program control to a labelled statement.
*   `return`: This executes the return statement by returning the result to the caller.
*   `switch:` This defines the switch statement in the Go program.
*   `case`: This defines various switch cases in a switch statement.
*   `select:` This keyword defines the select statement that works on multiple send/receive channel operations.
*   `default:` This executes the default case in a switch statement.
*   `fallthrough`: This executes the fallthrough statement that transfers the program control to the first statement of the case next to the currently executed case.
*   `defer`: This executes the defer statement that delays the function execution.
*   `go`: This keyword is used to handle Goroutines.

We’ll discuss every keyword in depth in the coming chapters. Here is a brief appearance of these keywords:

`package main` //use of package keyword

`import ("fmt"`

`"time"`

`) //use of import keyword`

`type person struct {` //use of type keyword

`name string`

`age int`

`}` // use of struct keyword

`type interface_example interface{`

`interface_function_int() int`

`interface_function_str() string`

`}` // use of interface keyword

`func interface_function_str() (string){`

`return "returning from function"` //use of return keyword

`}`

`func main() {` //func keyword

`var str = "hello world”"` //var keyword

`const num = 10` //const keyword

`arr := [6] int {10, 20, 30, 40, 50, 60}`

`map_data := map[string]int{`

`"hello":80,`

`"world":45,`

`}` //declare map

`cs1 := make(chan string)` // declare channel

`cs2 := make(chan string)`

`go func() {`

`time.Sleep(1 * time.Second)`

`cs1<- "one"`

`}()`

`fmt.Println(str,num, map_data,cs1)`

`if num>100{` //use of if keyword

`fmt.Println("num is greater than 100")`

`} else {` // use of else keyword

`fmt.Println("num is not greater than 100")`

`}`

`for pos, val := range arr {` //use of for and range keyword

`if (pos==5){`

`break` //break keyword

`}`

`if(pos==1){`

`continue` //continue keyword

`}`

`fmt.Printf("value at index %d is %d\n", pos, val)`

`}`

`fmt.Println(interface_function_str())`

`switch num {` //switch keyword

`case 1:` //use of case keyword

`fmt.Println("one")`

`case 2:`

`fmt.Println("two")`

`case 3:`

`fmt.Println("three")`

`default:` //default keyword

`fmt.Println("No match")`

`}`

`switch num {`

`case 1:`

`fmt.Println("one")`

`case 2:`

`fmt.Println("two")`

`case 10:`

`fmt.Println("three")`

`fallthrough` //use of fallthrough keyword

`default:`

`fmt.Println("default statement")`

`}`

`defer interface_function_str()` //use of defer keyword

`go interface_function_str()` // use of go keyword

`select {`

`case msg1 := <-cs1:`

`fmt.Println("received", msg1)`

`case msg2 := <-cs2:`

`fmt.Println("received", msg2)`

`}` //use of select keyword

`goto gotolabel` //use of goto keyword

`gotolabel:`

`fmt.Println("Inside goto statement")`

`}`

**Output:**

`hello world” 10 map[hello:80 world:45] 0x1183c0c0`

`num is not greater than 100`

`value at index 0 is 10`

`value at index 2 is 30`

`value at index 3 is 40`

`value at index 4 is 50`

`returning from function`

`No match`

`three`

`default statement`

`received one`

`Inside goto statement`

# [Identifiers](#toc.xhtml#s23a)

The identifier is the name of the class, functions, statement label, constant, package name or variables that uniquely identifies an object. It is a fusion of Unicode letters, digits, and underscore. The first letter of the identifier must be a letter or underscore. The name of the identifier is case sensitive in the Go language. We cannot use a reserved word as an identifier. Go provides a special type of identifier called "blank identifier" that is denoted as \_. **Blank identifier** works as a placeholder that can have any value, but we cannot read it in our program. An identifier that has a capital letter as its first letter is called an exported identifier. These identifiers should be declared in package blocks as these are accessible from other packages also. On the other hand, the identifiers that don’t have the first letter in capital are called non-exported identifiers.

Here are some valid and invalid identifiers:

*   **Valid** 
    *   ` _ = 12` //blank identifier
    *   `var Version = 4.0` //exported identifier
    *   `var name = "Ansh"` //non-exported identifiers
    *   `var _12 = "hello world"` //non-exported identifiers
*   **Invalid:** 
    *   `var 12 = "hello world"` //should not start with digits
    *   `var count$ = 23` //can’t have special characters
    *   `var default = 5.0` //can’t use reserve keywords as identifiers.

# [Conclusion](#toc.xhtml#s24a)

In this chapter, we saw the basic structure and components of the Go program. Writing and running a simple Go program is the first step in Go programming. We discussed the supported keywords in the Go language. By identifiers, we come to know the naming convention of packages, classes, functions, or variables. Let’s move forward with Golang variables and data types in the next chapter.

# [Questions](#toc.xhtml#s25a)

1.  What is the role of `fmt` package in Go language?
2.  How to comment lines in Go language?
3.  Which package and function are necessary for the Go program?
4.  Define the use of `fallthrough` keyword in Go language?
5.  What is the blank identifier?
6.  Specify exported and non-exported identifiers in Go language?

# [CHAPTER 4](#toc.xhtml#c04)

# [Variables, Data Types, and Constants](#toc.xhtml#c04)

**Data** is a basic thing that programming works with. We can change some value and some we cannot. On the same concept, variable and constants work in programming languages and we'll get into it in this chapter. In our public life, we see multiple types of values like our age in numeric terms, name as a combination of characters, amount as a decimal value, and many others. The same goes for programming data; it could be of any type such as integer, string, float, etc. In this chapter, we'll learn the Golang supported data types.

# [Structure](#toc.xhtml#s26a)

In this chapter, we will discuss the following topics:

*   Variables
*   Data types
*   Constants
*   Format specifiers

# [Objective](#toc.xhtml#s27a)

After studying this chapter, you’ll be able to:

*   Use variables in Go programs
*   Understand the naming convention of variables very well
*   Understand various data types in Go language
*   Understand how constants work with Go
*   Work with format specifiers

# [Variables](#toc.xhtml#s28a)

**Variable** is the name given to a specific type of value that is stored in memory at a particular location. Declaring a variable simply acquires some space in memory and tells the compiler the name and type of its value. As Go is a statically typed language, we cannot change the type of the variable at runtime. However, the value of a variable could vary as per our need with the same data type. Every variable should be necessarily defined in the Go language. While declaring a variable, it is required to declare its type if we are not assigning its value at the same time. By default, Go compiler takes the value zero for numeric, blank for string, and false for Boolean type data. Go facilitates multiple ways to declare and initialize a variable.

*   `var name_of_variable type_of_variable`
*   `var name_of_variable = value_of_variable` //identifies the type of variable by its value
*   `name_of_variable := value_of_variable`
*   `name_of_firstVariable,name_of_secondVariable:=value_of_firstVariable,value_of_secondVariable` //multiple declaration at the same time
*   `var name_of_firstVariable, name_of_secondVariable type_of_variable`//if all variables are of same type
*   `var (`
    
    `name_of_firstVariable type_of_variable`
    
    `name_of_secondVariable type_of_variable`
    
    `)`
    

Go also has a blank identifier when it is necessary to declare a variable but there is no use of that variable programmatically. We simply put underscore (\_) instead of the variable name to handle such worries.

**Example:**

`var variable1 int //declare int type variable "variable1"`

`fmt.Println(variable1) //print value 0`

`var variable2 string`

`fmt.Println(variable2) //print ""`

`variable1 = 123`

`variable2 = "hello world"`

`fmt.Println(variable1, variable2) //print 123 hello world`

`var variable3 = 123.45`

`fmt.Println(variable3) //print 123.45`

`variable4 := false`

`fmt.Println(variable4) //print false`

`variable5, variable6 := "multiple", 2`

`fmt.Println(variable5, variable6) //print multiple 2`

`var variable7, variable8, variable9 int //declaring multiple variables of same type`

`variable7, variable8, variable9 = 123, 456, 789`

`fmt.Println(variable7, variable8, variable9) //print 123 456 789`

`var(`

`variable10 int`

`variable11 string`

`variable12 bool`

`) //declaring multiple variables of different type at the same type.`

`fmt.Println(variable10, variable11, variable12) //print 0 false`

`variable10, variable11, variable12 = 123, "multiple", true`

`fmt.Println(variable10, variable11, variable12) //print 123 multiple true`

`variable13, variable14 := 123, 456`

`fmt.Println(variable13) //error "variable14 declared and not used"`

`variable15, _:= 123, 456 //use of "blank identifier"`

`fmt.Println(variable15) //print 123`

# [Data types](#toc.xhtml#s29a)

A **data type** is an attribute of data that define what type of data can be stored. There are multiple variables and functions of different types. A data type tells the compiler the amount of space that would be occupied in storage by that particular variable. **Go** is a statically typed language in which the type of variable is declared at compile type and it cannot be changed later. In this way, a lot of small bugs are caught very quickly and so, prevent the data type errors.

![](images/4-1.jpg)

**Figure 4.1:** Data structure

There are two types of data, primitive and non-primitive.

1.  **Primitive data type**
    
    **Primitive data types** are built with programming languages and always have a single value. They cannot be divided into sub-types. Boolean, numeric, and string come in primitive data type in the Go language. Let's talk about them in detail.
    
    *   **Boolean**
        
        A data type that can only have two values, either true or false is the boolean data type. It can be 1 as true or 0 as false.
        
        **Example:**
        
        `var is_Red bool = true`
        
        `fmt.Printf("%v\n", is_Red)`
        
    *   **Numeric**
        
        The data type on which we can perform arithmetic and logical operations is called a numeric data type. It could be an integer or floating-point data type.
        
        **Example:**
        
        `var int32val int32 = 100`
        
        `var int valint = 76 //treats as int32 or int64 depends on implementation`
        
        `fmt.Println(int32val, intval)`
        
        `var int16val int16 = int64val // error “cannot use int32val<type int32> as type int16 in assignment”`
        
        `var int16val int16 = int16(int32val)`
        
        `fmt.Println(int16val) // print 100`
        
        `var int64val int64 = int32val // error “cannot use int32val<type int32> as type int64 in assignment”`
        
        `var int64val int64 = int64(int32val)`
        
        `fmt.Println(int64val) //print 100`
        
        `var uint8val uint8 = int32val // error “cannot use int32val<type int32> as type uint8 in assignment”`
        
        `var uint8val uint8 = uint8(int32val)`
        
        `fmt.Println(uint8val) // print 100`
        
        `int32val = -100`
        
        `uint8val = uint8(int32val)`
        
        `fmt.Println(uint8val) // print 156, as -100 is converting to unsigned integer (using 2’s complement)`
        
        *   **Integer:** In the Go language, we have several integer data types. 
            *   **uint8:** Unsigned 8-bit integers. They range from 0 to 255.
            *   **uint16:** Unsigned 16-bit integers. They range from 0 to 65535.
            *   **uint32:** Unsigned 32-bit integers. They range from 0 to 4294967295.
            *   **uint64:** Unsigned 64-bit integers. They range from 0 to 18446744073709551615.
            *   **int8:** Signed 8-bit integers. They range from -128 to 127.
            *   **int16:** Signed 16-bit integers. They range from -32768 to 32767.
            *   **int32:** Signed 32-bit integers. They range from -2147483648 to 2147483647.
            *   **int64:** Signed 64-bit integers. They range from -9223372036854775808 to 9223372036854775807.
            *   **complex64:** It has float32 real part and float32 imaginary part.
            *   **complex128:** It has float64 real part and float64 imaginary part.
            *   **byte:** It is similar to unsigned 8-bit integers having the same range.
            *   **rune:** It is similar to signed 32-bit integers with the difference of having Unicode code point representation.
        *   **Floating:** In the Go language, we have several floating-point data types. 
            *   **float32:** All 32-bit floating-point numbers.
            *   **float64:** All 64-bit floating-point numbers.
            *   **complex64:** complex64 has float32 real and imaginary parts.
            *   **complex128:** complex128 has float64 real and imaginary parts.
        *   **Error:** The error data type that is used to store error values.
        
        **Note: We will discuss it in the chapter "Error Handling."**
        
    *   **String**
        
        As numeric type defines the collection of numbers, string data type represents the collection of characters. They could be letters, numbers, or any special characters. In the Go language, strings are UTF-8 encoded strings where UTF stands for "Unicode Transformation Format" which supports any Unicode character (any language) and 8 dictates, that every character is defined by using 8-bits. In Go, strings are immutable and so, they consume more space.
        
        **Example:**
        
        `var strval string = "Grow with Golang"`
        
        `var strcopied string = strval`
        
        `fmt.Println("original string is:", strval)`
        
        `fmt.Println("copied string is:", strcopied) //prints "copied string is: Grow with Golang"`
        
        `fmt.Println("Address of strval:", &strval)`
        
        `fmt.Println("Address of strcopied:", &strcopied) // above two lines prints the different memory address of variables`
        
2.  **Non-Primitive data type:**
    
    The data types that can store a batch of values are called non-primitive data types. They are also called derived data types. Primitive data types are a specific source of non-primitive data types. They are also called referenced data types as they contain the address of the dynamically created objects in memory. In Go language, we have the following non-primitive data types.
    
    *   **Pointer**
        
        Every variable stored in memory has a particular location/address. A pointer is an object that stores the address of any value stored in memory. The type of pointer depends on the type of element that has been stored by the pointer. It allows direct access to memory and thus, reduces storage space of the program. Pointer uses two operators, "address of operator" and "indirection operator"\*.
        
        Here is the simple way to declare a pointer:
        
        `var name_of_pointer *type_of_pointer`
        
        **Example:**
        
        `var int valint = 12`
        
        `var pval = &intval`
        
        `fmt.Println(pval) // prints address of intval`
        
        `fmt.Println(*pval) // print value of intval`
        
        `*pval = 78 // change the value of intval through pointer`
        
        `fmt.Println(intval) // print 78`
        
    *   **Array**
        
        The array is a data structure that stores the same type of data elements that can be accessed by their index number. In array, the index number starts at 0, so that the maximum index is one less than the length of the array. The type of array and the space occupied by the array depends on the elements of the array, whether it’s an integer, string, or anything else. We cannot put a different type of element in a single array in the Go language. Here, array behaves like a value. If we assign an array to a variable, it'll copy all of its elements into another array. In the same way, on passing an array to a function, it receives the value of array and not the reference of the array. In Go, at the time of declaration, we have to define the size of the array and how many elements can be stored.
        
        It is declared as:
        
        `var name_of_array[size_of_array] type_of_array_elements`
        
        or
        
        `name_of_array :=[size_of_array] type_of_array_elements{elements_of_array}`
        
        **Example:**
        
        `var arrval[3] string`
        
        `arrval = ["abc","def","ghi"] // error "syntax error"`
        
        `arrval[0] = "abc"`
        
        `arrval[1] = "def"`
        
        `arrval[2] = "ghi" //will assign the values by accessing it's index`
        
        `fmt.Println(arrval) //print [abcdefghi]`
        
        `arrval2 := [3]string{"abc","def","ghi"}`
        
        `fmt.Println(arrval2)` //print [abcdefghi]
        
    *   **Structures**
        
        This composite data type is similar to a database that can store multiple related items that point to a single entity. It groups the data of different types and creates a single type structure. The class also defines the different data types of any object, but the main difference between both of them is that by default, class is private. At the same time, structures are public and easily accessible. In structures, we can only declare the fields but we cannot initialize them at the same time. Structures variables can be declared with the structure declaration or just like how other data types are declared.
        
        The simple way to declare structures is as follows:
        
        `type StructName struct{`
        
        `field1 fieldType1`
        
        `field2 fieldType2`
        
        `}`
        
        In the given example, StructName is a name of structure and field1 and field2 are of types fieldType1 and fieldType2 respectively. Here, fields are accessed as:
        
        `StructName.field1`
        
        **Example:**
        
        `type company struct{`
        
        `company string`
        
        `id string`
        
        `no_of_employees int16`
        
        `}`
        
        `var comp company //creating variable of type company`
        
        `var comp2 company`
        
        `comp.no_of_employees = 90 //accessing the members of structure`
        
        `comp2 = company{"abcpvt. ltd.","SYRP7302",90} // initializing structure`
        
        `var no_of_employees = comp.no_of_employees`
        
        `fmt.Println(no_of_employees) //print 90`
        
        `fmt.Println(comp2.no_of_employees) //print 90`
        
        `fmt.Println(comp2) //print{abcpvt. ltd. SYRP7302 90}`
        
    *   **Slice**
        
        Like Arrays, slice also stores the same type of data collection. However, with slice, we are not bounded by its length. Slice acts as a strong interface with sequences. Unlike arrays, we can extend the length of slice by using the append function. On passing slices to a function, it creates a reference to an array and it does not create a new copy. That is why slices are also of reference type. The make function is used to declare slices. Slices will have the value when we assign a part of array to them and at that time, we can say that slice is referring to an array.
        
        In Go, slices are declared as:
        
        `name_of_slice :=make([] type_of_slice_elements, length_of_slice, capacity_of_slice)`
        
        **Example:**
        
        `slice1 := make([]int,0)`
        
        `fmt.Println(slice1) //print []`
        
        `slice2 := make([]int, 3)`
        
        `slice2[0] = 123`
        
        `slice2[1] = 456`
        
        `slice2[2] = 789`
        
        `fmt.Println(slice2) //print [123 456 789]`
        
        `slice3 := []string{"abc","def","ghi"}`
        
        `fmt.Println(slice3) //print [abcdefghi]`
        
        `slice3 = append(slice3, "jkl")`
        
        `fmt.Println(slice3) //print [abcdefghijkl]`
        
        `slice4 := make([]string,5)`
        
        `copy(slice4, slice3)`
        
        `fmt.Println(slice4) //print [abcdefghijkl]`
        
        `slice2D := make([][]string, 2,3)`
        
        `fmt.Println(slice2D) //prints [[] []]`
        
        `slice2D[0] = []string{"a","b","c"}`
        
        `slice2D[1] = []string{"d", "e"}`
        
        `fmt.Println(slice2D) // print [[a b c] [d e]]`
        
    *   **Map**
        
        **Maps** can be defined by two elements—keys and values where key is a single element while values can be an integer, string, array, structures, or any other map. Maps are like dictionary in that the keys having the same name are not allowed. Although, keys are case-sensitive so that we can keep the keys with the same names but with different cases, if needed. In maps, every element is separated by comma (,) and every key-value pair is separated by colon (:). Maps are easy to extend as there is no need to define their size at the time of declaration. With maps, we can access any record by using keys. That’s why this is also called fast key lookup data structure. While declaring a map, we have to mention the data type of the keys and values both. Like arrays, maps are nil if they don’t. In Go, we have a function called make that is used to allocate and initialize slice, maps, and channels.
        
        We can declare maps as:
        
        `var name_of_variable = make(map[type_of_keys] type_of_values)`
        
        or
        
        `name_of_variable := make(map[type_of_keys] type_of_values)`
        
        **Example:**
        
        `var mapval2 = make(map[int]string)`
        
        `mapval2[1] = "WORLD"`
        
        `mapval2[2] = "INDIA"`
        
        `fmt.Println(mapval2) //prints map[1:WORLD2:INDIA]`
        
        `mapval := make(map[string]int)`
        
        `mapval["first"] = 16`
        
        `mapval["second"] = 32`
        
        `fmt.Println(mapval) //prints map[first:16second:32]`
        
    *   **Channels**
        
        Go is a multicore language and it supports concurrency and parallelism. By using channels, we can send the data to multiple Goroutines (functions) at the same time and thus, avoid the problem of race condition, resource sharing problem, and many others that are difficult to debug. It allows the concurrent execution of multiple Goroutines where we can pass the value through the channel to one Goroutine and can get it again from the other Goroutine. Like maps, channels are also created with the use of the make function. We can also do buffering and iterating over the channels. We use the channel operator to transfer the values from channel to variable
        
        `Channel_name := make(chan type_of_channel)`
        
        **Example:**
        
        `var channelval chan int`
        
        `fmt.Println(channelval) //print undefined channel as <nil>`
        
        `channelval2 := make(chan string)`
        
        `gofunc() {channelval2<- "DONE"}() //passing value to function through channel`
        
        `msg := <-channelval2 //reading channel`
        
        `fmt.Println(msg) //print DONE`
        

# [Constants](#toc.xhtml#s30a)

Constant serves the values that remain fixed throughout the program. We can't reassign the constant with another value. The value a constant hasis called literal. In Go, it is required to have constant value during the compile time. Any attempt to assign the value returned by a function call can cause an error since because of function call, the compiler would not get the value of constant at compile time and thus, it will throw an error. We have a keyword const to declare the constant. Like variables, constants also have multiple ways to declare and initialize the values. The difference is that we cannot declare the constants using = syntax.

*   `const name_of_constant = value_of_constant` //untyped constant
*   `const name_of_constant type_of_constant = value_of_constant` //typed constant
*   `const name_of_firstConstant name_of_secondConstant = value_of_firstConstant, value_of_secondConstant`
*   `const (`
    
    `name_of_firstConstant = value_of_firstConstant`
    
    `name_of_firstConstant = value_of_secondConstant`
    
    `)`
    
*   `const (`
    
    `name_of_firstConstant type_of_ firstConstant = value_of_firstConstant`
    
    `name_of_secondConstant type_of_secConstant = value_of_secConstant`
    
    `)`
    
*   **Numeric constant**
    
    A **numeric constant** can be an integer, float, complex, and rune. Integer constants represent decimal, octal, or hexadecimal values. They could be 32 bit or 64 bit. The floating-point constant values have an integer portion, fractional portion, and an exponent. Complex constants are a combination of real and imaginary values. Run esares imply untyped 32-bit integers. Theycontain the value in the Unicode form or character. Runes give an integer value to each character and that integer value is called the Unicode code point of a character. Here is an example to explain all about numeric constants.
    
    **Example:**
    
    `const untypedConstInt = 123 //untyped integer constant`
    
    `const untypedConstFLoat = 3.97 //untyped floating-point constant`
    
    `const typedConstFloat float64 = 4.87 //typed floating point constant`
    
    `const untypedConstComplex = 56+2i //untyped complex constant`
    
    `const typedConstComplex complex64 = 56+2i //typed complex constant`
    
    `const typedConstComplex1 complex64 = untypedConstInt //typed complex constant`
    
    `fmt.Println(typedConstComplex1) //print 123+0i`
    
    `const untypedConstrune = 'G'`
    
    `fmt.Println(untypedConstrune) //print unicode value of 'G' 71`
    
    `const untypedConstrune1 rune = untypedConstInt`
    
    `fmt.Println(untypedConstrune1) //print 123`
    
*   **String constant**
    
    Any value enclosed within double quotes and declared with const keyword is a **string constant**. Mixing data types is not allowed in Go language. We can convert untyped data to other data types but we can’t convert the types of typed data.
    
    **Example:**
    
    `const untypedConstString = "Golang is a great language" //untyped string constant`
    
    `const typedConstString string = "Golang is a great language"//typed string constant`
    
    `type myString string //creating new type having same structure as string`
    
    `const customName myString = untypedConstString //assigning untyped data`
    
    `const customName myString = typedConstString //error in assigning typed data “conversion not allowed”`
    
*   **Boolean constant**
    
    **Boolean constants** can have two values, either true or false that remain the same in the program. Like string constants, we can't mix the data types with Boolean constants also.
    
    **Example:**
    
    `const untypedConstBoolean = true //untypedboolean constant`
    
    `const typedConstBoolean bool = false //typed boolean constant`
    
    `type myBool bool //creating new type having same structure as bool`
    
    `const customName myBool = untypedConstBoolean //assigning untyped data`
    
    `const customName1 myBool = typedConstBoolean // error in assigning typed data “conversion not allowed”`
    
*   **Iota**
    
    Go supports theIota identifier that increments with `const` declaration. Whenever compiler gets `const block, the iota identifier resets to zero and increments by one after each non-blank line within const block.`
    
    **Example:**
    
    `const // iota resets to zero`
    
    `(`
    
    `C0 = iota // here iota is zero, increments after coming out from this line`
    
    `_ // increments by one, iota is 1 here`
    
    `C1 = iota // iota is 2`
    
    `)`
    
    `fmt.Println("C0:", C0) // print 0`
    
    `fmt.Println("C1:", C1) // print 2`
    
    `const // resets iota to zero`
    
    `(`
    
    `//comments // doesn't consider this line so that iota would be the same.`
    
    `C2 = iota`
    
    `)`
    
    `fmt.Println("C2:", C2) //print 0`
    

# [Format specifiers](#toc.xhtml#s31a)

Format specifiers indicate the format of data contained by a variable during input and output operations. Format specifiers are used as operators with `Printf, Scanf,` and other similar functions for a specific type of data. Various formatting specifiers are used for specifying different data types. Each type of format specifier started with a percentage (%) sign, followed by a character that defined the type of data associated with the input/output function.

Here are the different types of format specifiers for each data type:

 
| **Universal** |
| `%v` || prints the value of a variable in the default format |
| `%#v` || prints the value of a variable in the form of Go-syntax |
| `%T` || tells the type of value |
| `%%` || dictates % sign |

 
| **Boolean** |
| `%t` || prints the boolean value of a variable |

 
| **Integer** |
| `%b` || represents integer value in base 2 |
| `%c` || character corresponding to an integer value |
| `%d` || represents integer value in base 10 |
| `%o` || represents integer value in base 8 |
| `%O` || represents integer value in base 8 with prefix O |
| `%q` || represents a character in Go-syntax corresponding to an integer value |
| `%x` || represents the lower case value in base 16 |
| `%X` || represents the upper case value in base 16 |
| `%U` || represents Unicode format of a value |

 
| **Floating point** |
| `%b` || decimal-less float value with the exponent power of two |
| `%e` || scientific notation of value |
| `%E` || scientific notation of value |
| `%f` || the decimal point with no exponent |
| `%F` || same as %f |
| `%g` || %e for large exponents |
| `%G` || %E for large exponents |
| `%x` || hexadecimal value with two exponents |
| `%X` || hexadecimal value in upper case |

 
| **String** |
| `%s` || represents the value of string variable |
| `%q` || represents the value with double quotes in Go-syntax |
| `%x` || represents string value in base 16 lower case |
| `%X` || represents string value in base 16 upper case |

 
| **Pointer** |
| `%p` || represents the value of pointer type |

Here is an example that explains the format specifiers well:

`package main`

`import "fmt"`

`func main() {`

`var str = "hello"`

`var intval = 78`

`var floatval = 56.8789`

`var complexval = 67+6i`

`var boolval = true`

`var pointerval = &str`

`fmt.Printf("example of %%v, value is: %v \n", intval)`

`fmt.Printf("example of %%#v, value is: %#v \n", str)`

`fmt.Printf("example of %%T, value is: %T \n", intval)`

`fmt.Printf("example of %%, used to print %%\n\n")`

`fmt.Printf("example of %%t, value is: %t\n\n", boolval)`

`fmt.Printf("example of %%b, value is: %b\n", intval)`

`fmt.Printf("example of %%c, value is: %c\n", intval)`

`fmt.Printf("example of %%d, value is: %d\n", intval)`

`fmt.Printf("example of %%o, value is: %o\n", intval)`

`fmt.Printf("example of %%O, value is: %O\n", intval)`

`fmt.Printf("example of %%q, value is: %q\n", intval)`

`fmt.Printf("example of %%x, value is: %x\n", intval)`

`fmt.Printf("example of %%X, value is: %X\n", intval)`

`fmt.Printf("example of %%U, value is: %U\n\n", intval)`

`fmt.Printf("example of %%b, value is: %b\n", floatval)`

`fmt.Printf("example of %%e, value is: %e\n", floatval)`

`fmt.Printf("example of %%E, value is: %E\n", complexval)`

`fmt.Printf("example of %%f, value is: %f\n", floatval)`

`fmt.Printf("example of %%F, value is: %F\n", floatval)`

`fmt.Printf("example of %%g, value is: %g\n", floatval)`

`fmt.Printf("example of %%G, value is: %G\n", floatval)`

`fmt.Printf("example of %%x, value is: %x\n", floatval)`

`fmt.Printf("example of %%X, value is: %X\n\n", floatval)`

`fmt.Printf("example of %%s, value is: %s\n", str)`

`fmt.Printf("example of %%q, value is: %q\n", str)`

`fmt.Printf("example of %%x, value is: %x\n", str)`

`fmt.Printf("example of %%X, value is: %X\n\n", str)`

`fmt.Printf("example of %%p, value is: %p \n", pointerval)`

`}`

**Output:**

`example of %v, value is: 78`

`example of %#v, value is: "hello"`

`example of %T, value is: int`

`example of %, used to print %`

`example of %t, value is: true`

`example of %b, value is: 1001110`

`example of %c, value is: N`

`example of %d, value is: 78`

`example of %o, value is: 116`

`example of %O, value is: %!O(int=78)`

`example of %q, value is: 'N'`

`example of %x, value is: 4e`

`example of %X, value is: 4E`

`example of %U, value is: U+004E`

`example of %b, value is: 8004993526413866p-47`

`example of %e, value is: 5.687890e+01`

`example of %E, value is: (6.700000E+01+6.000000E+00i)`

`example of %f, value is: 56.878900`

`example of %F, value is: 56.878900`

`example of %g, value is: 56.8789`

`example of %G, value is: 56.8789`

`example of %x, value is: %!x(float64=56.8789)`

`example of %X, value is: %!X(float64=56.8789)`

`example of %s, value is: hello`

`example of %q, value is: "hello"`

`example of %x, value is: 68656c6c6f`

`example of %X, value is: 68656C6C6F`

`example of %p, value is: 0x11806108`

# [Conclusion](#toc.xhtml#s32a)

In this chapter, we learned how to name a specific value, declare a variable, and store it in the memory. We learned how various data types work with Go language. Each data type has its importance in the Go language. Some data types are built with a programming language, while some are referenced data types. We'll discuss a few data types thoroughly in the next chapters. Here, we learned the proper use of variables with input/output operations with the use of format specifiers. In the next chapters, we'll see various operators performing several operations on the specific types of data.

# [Questions](#toc.xhtml#s33a)

1.  How is Go language a statically typed language?
2.  What are primitive and non-primitive data types?
3.  How to initialize the variables in structure?
4.  What is the difference between array and slice in Go?
5.  How to declare a map in Go language?
6.  What are the channels in Go?
7.  What is the format specifier in Go?

# [CHAPTER 5](#toc.xhtml#c05)

# [Operators](#toc.xhtml#c05)

In programming, there is a need to compute the data in various ways as per the requirement. Operators make this computation possible by performing a specific operation on a specific type of data. In this chapter, we’ll discuss these operators and how to use them with multiple types of data.

# [Structure](#toc.xhtml#s34a)

In this chapter, we will discuss the following topics:

*   What is an operator?
*   Types of operators
*   Operator precedence

# [Objective](#toc.xhtml#s35a)

After studying this chapter, you will be able to:

*   Use various operators in the Go program
*   Predict which operators work on a single operand
*   Compute the result as needed using these operators

# [Introduction](#toc.xhtml#s36a)

An **operator** is a character that represents a specific mathematical, relational, or logical operation on a single or multiple operands to produce the result. Every programming language is incomplete without operators and operands. Operators can be built-in or user-defined, depending on the programming language. We have an almost similar set of built-in operators in every language. Golang has various operators to perform different types of operations.

# [Types of operators](#toc.xhtml#s37a)

Golang is rich in operators. The operators that we have in the Go language are as follows:

*   **Arithmetic operator**
    
    **Arithmetic operators** are used for performing arithmetic operations like addition, subtraction, multiplication, division, etc. These operators can be applied between one or two operands. According to the number of operands, we can divide the arithmetic operators into two types, binary and unary. Binary operators take two operands and produce a single result, while unary operators perform the operation on a single operand and return a single result.
    
    Here is the list of arithmetic operators:
    
     
    | **Operator** || **Description** |
    | --- | --- |
    | `+` || `Adds two operands` |
    | `-` || `Subtracts the second operand from the first one` |
    | `*` || `Multiplies both operands` |
    | `/` || `Divides the first operand from the second one` |
    | `%` || `Returns remainder on dividing the first operand from the second one` |
    | `++` || `Increments integer/float value by one` |
    | `--` || `decrements integer/float value by one` |
    
    **Example:**
    
    `var a int = 12`
    
    `var b int = 3`
    
    `fmt.Println("ex. of '+' operator:", a+b) // print “ex. of '+' operator: 15”`
    
    `fmt.Println("ex. of '-' operator:", a-b) // print “ex. of '-' operator: 9”`
    
    `fmt.Println("ex. of '*' operator:", a*b) // print “ex. of '*' operator: 36”`
    
    `fmt.Println("ex. of '/' operator:", a/b) // print “ex. of '/' operator: 4”`
    
    `fmt.Println("ex. of '%' operator:", a%b) // print “ex. of '%' operator: 0”`
    
    `a++;`
    
    `fmt.Println("ex. of '++' operator:", a) // print “ex. of '++' operator: 13”`
    
    `b--;`
    
    `fmt.Println("ex. of '--' operator:", b) // print “ex. of '--' operator: 2”`
    
*   **Relational operator**
    
    **Relational operators** stabilize a relation between two entities, divided on the basis of equality or inequalities. Relational operators always work between two operands. These operators are mainly used as conditions that provide a boolean result. Here are some of the types of relational operators that we have in the Go language.
    
     
    | **Operator** || **Description** |
    | --- | --- |
    | `==` || `Returns true if the value of two operands is same.` |
    | `!=` || `Returns true if both operands have different values.` |
    | `<` || `Returns true if the value of the first operand is less than the value of the second operand.` |
    | `>` || `Returns true if the value of the first operand is greater than the value of the second operand.` |
    | `<=` || `Returns true if the value of the first operand is less than or equal to the value of the second operand.` |
    | `>=` || `Returns true if the value of the first operand is greater than or equal to the value of the second operand.` |
    
    **Example:**
    
    `var a int = 12`
    
    `var b int = 3`
    
    `fmt.Println("ex. of '==' operator:", a==b) // print ex. of '==' operator: false`
    
    `fmt.Println("ex. of '!=' operator:", a!=b) // print ex. of '!=' operator: true`
    
    `fmt.Println("ex. of '<' operator:", a<b) // print ex. of '<' operator: false`
    
    `fmt.Println("ex. of '>' operator:", a>b) // print ex. of '>' operator: true`
    
    `fmt.Println("ex. of '<=' operator:", a<=b) // print ex. of '<=' operator: false`
    
    `fmt.Println("ex. of '>=' operator:", a>=b) // print ex. of '>=' operator: true`
    
*   **Logical operator**
    
    **Logical operators** are used between two or multiple boolean operands and they make an appropriate decision by returning the boolean result. If it returns true, further process is takes place. Otherwise, it skips that particular process and continues. We have three types of logical operators in the Go language. These are as follows:
    
     
    | **Operator** || **Description** |
    | --- | --- |
    | `&&``(Logical AND)` || `Returns true if both the values are true, otherwise returns false.` |
    | `||``(Logical OR)` || `Returns true if any of the operands are true, otherwise returns false.` |
    | `!``(Logical NOT)` || `Works with the single operand. It returns true if the value of the operand is false and returns false if the value of the operand is true. It simply reverses the value of the operand.` |
    
    **Example:**
    
    `var a int = 12`
    
    `var b int = 3`
    
    `fmt.Println("ex. of '&&' operator:", a<b && a>b) //print ex. of '&&' operator: false`
    
    `fmt.Println("ex. of '&&' operator:", a<b && a<=b) //print ex. of '&&' operator: false`
    
    `fmt.Println("ex. of '||' operator:", a<b || a>b) // print ex. of '||' operator: true`
    
    `fmt.Println("ex. of '||' operator:", a<b || a>b) // print ex. of '||' operator: true`
    
    `fmt.Println("ex. of '!' operator:", !(a<b && a>b)) // print ex. of '!' operator: true`
    
*   **Bitwise operator**
    
    **Bitwise operators** work as logical operators. The key difference is that a logical operator works on boolean values while a bitwise operator works on bits, the binary representation of any value. While working with bitwise operators, operands are first converted into their binary form and then they perform the specific bitwise operation. These operators work on an individual bit of an operand. Here are the types of bitwise operators:
    
     
    | **Operator** || **Description** |
    | --- | --- |
    | `&``(Bitwise AND)` || `Performs AND operation on every bit of both operands and returns true if both are same and returns 0 if both operands have bit 0 and vice versa.` |
    | `|``(Bitwise OR)` || `Performs OR operation on every bit of both operands and returns true if any of two-bit is 1. Returns 1 if one of the operands has bit 1.` |
    | `^``(Bitwise XOR)` || `Performs XOR operation on every bit of both operands and return true if both bits are different. Returns 1 if one operand has bit 0 and the other one has bit 1, otherwise returns false.` |
    | `<<``(Left shift)` || `Bits of the first operand are shifted on the left for n times wherein n is the value of the second operand.` |
    | `>>``(Right shift)` || `Bits of the first operand are shifted on the right for n times wherein n is the value of the second operand.` |
    
    **Example:**
    
    `var a int = 50`
    
    `var b int = 6`
    
    `fmt.Println("a&b is:", a&b) //prints a&b is: 2`
    
    `fmt.Println("a|b is:", a|b) //prints a|b is: 54`
    
    `fmt.Println("a^b is:", a^b) //prints a^b is: 52`
    
    `fmt.Println("a<<b is:", b<<2) //prints a<<b is: 24`
    
    `fmt.Println("a>>b is:", a>>5) //prints a>>b is: 1`
    
*   **Assignment operator**
    
    **Assignment operators** set or reset the value of a variable. They could be used to assign a value to a new variable or change the value of a variable by evaluating any specific expression. These operators first evaluate an expression given on the right side of the assignment operator and then assign the final result to the variable written on the left of the assignment operator. We have multiple assignment operators in the Go language. These are as follows:
    
     
    | **Operator** || **Description** |
    | --- | --- |
    | `=` || `Assigns the value from the right side to the left side variable.` |
    | `+=` || `Adds the value of the left side variable to the value calculated on the right side and assign the final result to the left side variable.` |
    | `-=` || `Subtracts the value calculated on the right side from the value of the left side variable and assigns the final result to the left side variable.` |
    | `*=` || `Multiplies the value of the left side variable and the value calculated on the right side. Then assigns the final result to the left side variable.` |
    | `/=` || `Divides the value of the left side variable from the value calculated on the right side. Then assigns the final result to the left side variable.` |
    | `%=` || `Gets modulus on performing the above described divide operation and assigns the final result to the left side variable.` |
    | `<<=` || `‘Shifts left’ the value of the left side variable by the value calculated on the right side and assigns the final result to the left side variable.` |
    | `>>=` || `‘Shifts right’ the value of the left side variable by the value calculated on the right side and assign the final result to left side variable.` |
    | `&=` || `Performs bitwise AND operation on the value of the left side variable and the values calculated on the right side. Then assigns the final result to the left side variable.` |
    | `^=|` || `Performs bitwise XOR operation on the value of the left side variable and the values calculated on the right side. Then assigns the final result to the left side variable.` |
    | `|=` || `Performs bitwise OR operation on the value of the left side variable and the values calculated on the right side. Then assigns the final result to the left side variable.` |
    | `:=` || `Assigns the right side value to the left side variable that is previously not defined.` |
    
    **Example:**
    
    `var a int = 50 //simple assignment`
    
    `var b int = 5`
    
    `a += b`
    
    `fmt.Println("ex. of '+=' operator:", a) //prints ex. of '+=' operator: 55`
    
    `a -= b`
    
    `fmt.Println("ex. of '-=' operator:", a) //prints ex. of '-=' operator: 50`
    
    `a *= 3`
    
    `fmt.Println("ex. of '*=' operator:", a) //prints ex. of '*=' operator: 150`
    
    `a /= b`
    
    `fmt.Println("ex. of '/=' operator:", a) //prints ex. of '/=' operator: 30`
    
    `a %= 7`
    
    `fmt.Println("ex. of '%=' operator:", a) //prints ex. of '%=' operator: 2`
    
    `b <<= 2`
    
    `fmt.Println("ex. of '<<=' operator:", b) //prints ex. of '<<=' operator: 20`
    
    `b >>= 2`
    
    `fmt.Println("ex. of '>>=' operator:", b) //prints ex. of '>>=' operator: 5`
    
    `a &= 10`
    
    `fmt.Println("ex. of '&=' operator:", a) //prints ex. of '&=' operator: 2`
    
    `a ^= 10`
    
    `fmt.Println("ex. of '^=' operator:", a) //prints ex. of '^=' operator: 8`
    
    `a |= 10`
    
    `fmt.Println("ex. of '|=' operator:", a) //prints ex. of '|=' operator: 10`
    
    `c := "hello world"`
    
    `fmt.Println("ex. of ':=' operator:", c) //prints ex. of ':=' operator: hello world`
    
*   **Miscellaneous operator**
    
    Go provides some other language specific operators. These are as follows:
    
     
    | **Operator** || **Description** |
    | --- | --- |
    | `Sizeof` || `This operator is used to get the size of any variable of any type. We have two packages, “reflect” and “unsafe” that provide the sizeof function.` |
    | `&``(Address operator)` || `The address operator is a unary operator that provides the address of a variable at which that specified variable is stored in the memory` |
    | `*``(Indication operator)` || `This is also a unary operator that provides the value of a variable stored at the address specified by an operand in the memory.` |
    | `<-``(Receive operator)` || `<=ch is the value received from channel ch` |
    
    **Example:**
    
    `package main`
    
    `import ("fmt"`
    
    `"unsafe"`
    
    `"reflect"`
    
    `)`
    
    `func main(){`
    
    `var a int64 = 100`
    
    `fmt.Println("size of variable a:", unsafe.Sizeof(a)) //prints 8`
    
    `fmt.Println("size of variable a:", reflect.TypeOf(a). Size()) //prints 8`
    
    `fmt.Println("address of variable a:", &a) //prints Address of variable a: 0x1184e068`
    
    `fmt.Println("value of a at specified address:", *(&a)) //prints Address of variable a: 100`
    
    `}`
    

# [Operator precedence](#toc.xhtml#s38a)

**Operator precedence** decides the execution priority of every operator so that expression can be evaluated properly. Operators that have high precedence are evaluated first while evaluating an expression. Associativity comes when we have two or more expressions having the same operator or operators of the same precedence. In this case, the expression is evaluated either left to right or right to left as per their associativity rules.

In the following table, associativity is well-described for every operator.

 
| **Category** || **Operator** || **Associativity** |
| --- | --- | --- |
| `Postfix` || `() [] -> . ++ - -` || `Left to right` |
| `Unary` || `+ - ! ~ ++ - - (type)* &sizeof` || `Right to left` |
| `Multiplicative` || `* / %` || `Left to right` |
| `Additive` || `+ -` || `Left to right` |
| `Shift` || `<<>>` || `Left to right` |
| `Relational` || `<<= >>=` || `Left to right` |
| `Equality` || `== !=` || `Left to right` |
| `Bitwise AND` || `&` || `Left to right` |
| `Bitwise XOR` || `^` || `Left to right` |
| `Bitwise OR` || `|` || `Left to right` |
| `Logical AND` || `&&` || `Left to right` |
| `Logical OR` || `||` || `Left to right` |
| `Assignment` || `= += -= *= /= %=>>= <<= &= ^= |=` || `Right to left` |

# [Conclusion](#toc.xhtml#s39a)

In this chapter, we gained an understanding of the operators in a programming language. We learned the use of arithmetic, relational, logical, bitwise, assignment, and miscellaneous operators supported by Go language. We saw how the operators are parsed concerning each other with the understanding of operator precedence. It decides if an operator needs to perform first in an expression. After getting an idea of operators, it’s time to understand the control flow in a program. Let’s cover it in the next chapter.

# [Questions](#toc.xhtml#s40a)

1.  What type of operators do we have in Go language?
2.  What do unary operators mean?
3.  Which operator performs equality/inequality operation?
4.  Specify logical operators with an example.
5.  How do bitwise operators work with Go language?
6.  Which operator is used to get a value from a channel?
7.  How do we get an address of a variable stored in memory?
8.  What is the associativity of shift operators?

# [CHAPTER 6](#toc.xhtml#c06)

# [Control Structures](#toc.xhtml#c06)

While programming, it is necessary to understand the control flow of the program. It reduces the complexity and also helps in debugging. Our program consists of blocks that perform different types of tasks. A block that works on variables and transfers the control to a specific block on a specific condition is called a control structure. In this chapter, we will be discussing the decision-making process that we need to perform in our programs.

# [Structure](#toc.xhtml#s41a)

In this chapter, we will discuss the following topics:

*   Introduction to control structures
*   Branching statements
*   Looping statements
*   Jumping statements

# [Objective](#toc.xhtml#s42a)

After studying this chapter, you’ll be able to:

*   Run the block of code on the specific condition
*   Optimize your code
*   Override the sequential execution as needed
*   Transfer the control flow in any direction you want

# [Introduction](#toc.xhtml#s43a)

Control structures define the flow of source code. By analyzing certain conditions/ logics, we often need to alter the flow of the execution of a program. Every control statement defines a specific flow of source code. In the Go language, we have three types of control statements. They are covered in the next sections.

# [Branching statements](#toc.xhtml#s44a)

These are decision-making statements consisting of one or multiple conditions. Based on these conditions, the flow of source code is followed.

*   **If/Else**
    
    The `if` statement has a specific condition. If the condition given within `if`, statement is true then a block of `if` statement is followed; otherwise the block of `else` statement is followed. In any program, it is not necessary to have else case. Go program can consist multiple if-else statements by using else if statement. The Go language is strict with unexpected newlines. It gives an error on giving line break before curly brackets at the start of the block.
    
    **Example:**
    
    `package main`
    
    `import "fmt"`
    
    `func main() {`
    
    `var a int = 100`
    
    `var b int = 20`
    
    `if a==b{`
    
    `fmt.Println("a is equal to b")`
    
    `}else if a%b==0{`
    
    `fmt.Println("a is divisible by b")`
    
    `}else{`
    
    `fmt.Println("no match")`
    
    `}`
    
    `}`
    
    **Output:**
    
    `a is divisible by b`
    
*   **Switch**
    
    The `switch` statement is similar to multiple `if-else` statements where multiple cases replace these multiple conditions. The conditional expression that we need to compare is put within the switch statement and the evaluated result is compared with every case value. The case block whose value matches with the evaluated expression is further followed by the compiler. We have an optional default case here which is followed if no case value is matched with the conditional expression.
    
    **Example:**
    
    `package main`
    
    `import "fmt"`
    
    `func main() {`
    
    `var a int = 100`
    
    `switch a{`
    
    `case 20:`
    
    `fmt.Println("value of a is 20")`
    
    `case 50:`
    
    `fmt.Println("value of a is 50")`
    
    `case 100:`
    
    `fmt.Println("value of a is 100")`
    
    `default:`
    
    `fmt.Println("switch loop processed")`
    
    `}`
    
    `}`
    
    **Output:**
    
    `value of a is 100`
    

# [Looping statements](#toc.xhtml#s45a)

**Looping statements** are used for the repetition of a specific block of code based on a specific condition. The looping condition decides the number of times that specific block of code would be repeated.

*   **for**
    
    The `for` loop is used to iterate a specific block of code for a finite number of times. The for loop consists of three parts: initialization of a variable, the condition that defines the number of times iterations will take place, and post statement that is executed after each iteration. Firstly, the variable gets initialized and then it checks the condition. If the condition is true, it follows the block of code within for loop and then post statement is executed. That statement changes the value of the variable which is checked again by the given condition on the next iteration. The iteration is stopped if it finds the condition false. Parentheses are not required in for loop here. To define the code block, braces{} are always used.
    
    **Example:**
    
    `package main`
    
    `import "fmt"`
    
    `func main() {`
    
    `result := 1`
    
    `for i := 1; i< 10; i++ {`
    
    `result *= i`
    
    `}`
    
    `fmt.Println(result)`
    
    `}`
    
    **Output:**
    
    `362880`
    

# [Jumping statements](#toc.xhtml#s46a)

**Jumping statements** are used to skip a specific code or to jump a specific block of code in a program.

*   **break**
    
    The `break` statement is used for immediate termination from the loop at a specific condition. The break statement is used with `for` loop or `switch` statement. In nested loops, the `break` statement stops the execution on a given condition and jumps to the next statement out of the loop.
    
    **Example:**
    
    `package main`
    
    `import "fmt"`
    
    `func main() {`
    
    `var a int = 0`
    
    `for a < 20 {`
    
    `fmt.Printf("value of a: %d\n", a);`
    
    `a++;`
    
    `if a==5 {`
    
    `/* terminate the loop using break statement */`
    
    `break;`
    
    `}`
    
    `}`
    
    `}`
    
    **Output:**
    
    `value of a: 0`
    
    `value of a: 1`
    
    `value of a: 2`
    
    `value of a: 3`
    
    `value of a: 4`
    
*   **Continue**
    
    The `continue` statement is similar to the `break` statement. Instead of terminating from the loop, it skips the current iteration and jumps to the next one. The `continue` statement is also used at specific conditions within a loop.
    
    **Example:**
    
    `package main`
    
    `import "fmt"`
    
    `func main() {`
    
    `var a int = 0`
    
    `for a < 5 {`
    
    `if a ==3 {`
    
    `/* skip the iteration */`
    
    `a = a + 1;`
    
    `continue;`
    
    `}`
    
    `fmt.Printf("value of a: %d\n", a);`
    
    `a++;`
    
    `}`
    
    `}`
    
    **Output:**
    
    `value of a: 0`
    
    `value of a: 1`
    
    `value of a: 2`
    
    `value of a: 4`
    
*   **exit**
    
    The `exit` statement is used to terminate the program execution by forcing a return to the operating system.
    
    **Example:**
    
    `package main`
    
    `import "fmt"`
    
    `import "os"`
    
    `func main() {`
    
    `var a string = "hello"`
    
    `fmt.Println("string value is: ", a)`
    
    `os.Exit(0)`
    
    `a = a+" world"`
    
    `fmt.Println("updated string value is: ", a)`
    
    `}`
    
    **Output:**
    
    `string value is: hello`
    

# [Conclusion](#toc.xhtml#s47a)

In this chapter, we discussed various control statements used to transfer the control to a specific block of code. These control structures are machine independent and easy to maintain. They provide the flexibility to control the statement as needed. By the looping statement, we learned how to run a specific block of code repeatedly. In the next chapter, we’ll see the execution of a specific code block for multiple values by using functions.

# [Questions](#toc.xhtml#s48a)

1.  What is the branching statement in the Go language?
2.  What is the difference between switch and nested if-else statement?
3.  What is the default case in a switch statement?
4.  What do you mean by a looping statement?
5.  What is the use of the break statement?
6.  Which statement is used to skip the execution of a code block for a specific value in a loop?

# [CHAPTER 7](#toc.xhtml#c07)

# [Functions](#toc.xhtml#c07)

While programming, there can be a need to perform a specific task repeatedly for multiple values such as calculating the factorial of 100 numbers. In such a case, we can define a block of code performing that specific task and call that block for every 100 values. In a programming language, such block is called a function. Let's get anunderstanding of functions in this chapter.

# [Structure](#toc.xhtml#s49a)

In this chapter, we will discuss the following topics:

*   Introduction to functions
*   Declaring functions
*   Function arguments and return types
*   Calling functions
*   Call by value
*   Call by reference
*   Named return values
*   Blank identifier
*   Anonymous functions
*   Closures
*   Recursive functions
*   Defer keyword
*   Variadic functions

# [Objectives](#toc.xhtml#s50a)

After studying this chapter, you’ll be able to:

*   Perform repetitive tasks with a single block of code.
*   Reduce complexity by using functions
*   Pass multiple values in a function
*   Return the required type of value from functions
*   Understandvarious ways to use functions that provide flexibility to the user

# [Introduction](#toc.xhtml#s51a)

Functions play a major role in any programming language. Dividing a program into multiple functions reduces complexity, the size of the program, and makes the source code easy to understand. A function is a bunch of statements that perform a specific task and produce an output. The reason for using a function is reusability of any specific code. We can use the code defined within the function again and again with varying input values to get the desired output. The execution of every Go program starts with the main function that is defined in the main package.

*   **main function**
    
    In Go language, we have a package named main that tells the compiler that the package is not a shared library and it should be compiled as an executable program. The `main` package has a main function which is the entrance door for any executable program. The `main` function neither takes any argument nor returns any value. The initialization of the `main` function is done by the `init` function that is executed only once with the execution of the `main` function. We can easily execute all the tasks that we want to perform once throughout the program at the initial phase with `init` function.
    
    **Example:**
    
    `package main`
    
    `import "fmt"`
    
    `func init(){`
    
    `fmt.Println("initialization of main function")`
    
    `}`
    
    `func main() {`
    
    `fmt.Println("Program execution begins")`
    
    `}`
    
    **Output:**
    
    `initialization of main function`
    
    `Program execution begins`
    

# [Declaring functions](#toc.xhtml#s52a)

The first line in function declaration provides the basic information of any function. It is called the signature of the function. It contains `func` keyword, name of the function, an optional list of comma separated input values called arguments (or parameters), and return values with their specific types. Then there is a pair of braces that specifies the body of a function performing a specific task.

**Syntax:**

`func [function_name] (optional_inputval1 type, optional_inputval2 type..) (optional_returnval1 type, optional_returnval2 type){`

`//body of function`

`}`

**Example:**

`func first_function(){`

`fmt.Println("Hi….I am introducing a function")`

`}`

# [Function arguments and return types](#toc.xhtml#s53a)

In the Go language, we can pass zero or a large number of arguments to a function. Similarly, the function can also return zero or multiple numbers of values. On calling the function, passed parameters to a function are called **actual parameters** while the values received by the function in function declaration are called **formal parameters**. On the basis of the signatures mentioned above, let's create a function of two integers. Here is an example that takes two integer input values and returns the sum of them which is also an integer value.

**Example:**

`package main`

`import "fmt"`

`func sum(a int,b int) int{`

`sum_value := a+b`

`fmt.Println("sum is:", sum_value)`

`return sum_value`

`}`

`func main() {`

`a := 90`

`b := 30`

`sum(a, b)`

`}`

**Output:**

`sum is: 120`

If we have multiple parameters of the same type, then we can write the type of parameter with the last parameter value to avoid repetition. This can be done as follows:

`func sum(a, b int) int{`

`sum_value := a+b`

`fmt.Println("sum is:", sum_value)`

`return sum_value`

`}`

Or

`func sum(a, b int, c string) int{`

`sum_value := a+b`

`fmt.Println("sum is:", sum_value)`

`fmt.Println("value of c is:", c)`

`return sum_value`

`}`

Go functions have the capability of returning multiple values. All possible return types are specified inside the parentheses with comma separated. We can also return error type values in the Go language. Thiswill be discussed in the further chapters.

`func sum(a, b int, c string) (int, string){`

`sum_value := a+b`

`fmt.Println("sum is:", sum_value)`

`fmt.Println("value of c is:", c)`

`return sum_value, c`

`}`

# [Calling a function](#toc.xhtml#s54a)

We have declared the function so far. To use the function in a program, we call them within the `main` function with the required parameters. On calling the function, the control is transferred from the main function to the desired **called function**. Called function executes the statements defined within the function and returns to main when it gets the closing brace or any immediate terminate statement from the function. Its name, followed by the required parameters, call a function. We can assign the values in a variable which is returned by the function.

**Example:**

`package main`

`import "fmt"`

`func sum(a, b int, c string) (int, string){`

`sum_value := a+b`

`return sum_value, c`

`}`

`func main() {`

`a := 90`

`b := 30`

`var c string`

`result, c := sum(a, b, "Hello Go")`

`fmt.Println("Values returned from the function are: ", result, c)`

`}`

**Output:**

`Values returned from the function are: 120 Hello Go`

In the Go language, arguments can be passed to a function in two ways, call by value and call by reference.

# [Call by value](#toc.xhtml#s55a)

In this method, the actual value of the variables is passed to a function. These values are copied to formal parameters defined with the function signature. So, the changes performed in formal parameters don’treflect the values of actual parameters/variables.

**Example:**

`package main`

`import "fmt"`

`func call_by_value(x int, y int) {`

`x = x-20`

`y = y-30`

`fmt.Printf("In function, value of a : %d\n", x) //prints 80`

`fmt.Printf("In function, value of b : %d\n", y) //prints 170`

`}`

`func main() {`

`var a int = 100`

`var b int = 200`

`fmt.Printf("Before calling function, value of a : %d\n", a) //prints 100`

`fmt.Printf("Before calling function, value of b : %d\n", b) //prints 200`

`call_by_value(a, b)`

`fmt.Printf("After calling function, value of a : %d\n", a) //prints 100`

`fmt.Printf("After calling function, value of b : %d\n", b) //prints 200`

`}`

**Output:**

`Before calling function, value of a : 100`

`Before calling function, value of b : 200`

`In function, value of a : 80`

`In function, value of b : 170`

`After calling function, value of a : 100`

`After calling function, value of b : 200`

# [Call by reference](#toc.xhtml#s56a)

In this method, the address of a variable is passed as an argument while calling a function. In this case, format parameters have an address of a variable instead of a value. When any changes occur within the function, the changes at that give address are reflected. In this way, changes are also made with actual parameters.

**Example:**

`package main`

`import "fmt"`

`func call_by_reference(x *int, y *int) {`

`*x = *x-20`

`*y = *y-30`

`}`

`func main() {`

`var a int = 100`

`var b int = 200`

`fmt.Printf("Before calling function, value of a : %d\n", a) //prints 100`

`fmt.Printf("Before calling function, value of b : %d\n", b) //prints 200`

`call_by_reference(&a, &b)`

`fmt.Printf("After calling function, value of a : %d\n", a) //prints 80`

`fmt.Printf("After calling function, value of b : %d\n", b) //prints 170`

`}`

# [Named return values](#toc.xhtml#s57a)

The Go function can return the name values as defined with the signature of function. These named return values are themselves defined by the Go that can be used in a function. The name of the return value should be different and not declared earlier in the program.

`func sum(a, b int, c string) (sum_value int, c_val string){`

`sum_value = a+b`

`c_val = c`

`return sum_value, c_val`

`}`

Golang facilitates "naked return" which doesn't have any argument with the return statement but by default, returns all values specified with the signature of the function. Naked return is good in use but is not required in long functions as it is not necessary to return all the values mentioned at the top of the function.

**Example:**

`package main`

`import "fmt"`

`func sum(a, b int, c string) (sum_value int, c_val string){`

`sum_value = a+b`

`c_val = c`

`return`

`}`

`func main() {`

`a := 90`

`b := 30`

`var c string`

`result, c := sum(a, b, "Hello Go")`

`fmt.Println("Values returned from the function are: ", result, c)`

`}`

**Output:**

`Values returned from the function are: 120 Hello Go`

# [Blank Identifier](#toc.xhtml#s58a)

There canbe a case if we are getting some values returned by the function that we don't want to use further in our program. Golang doesn't allow such unused values and throws an error. In such cases, blank identifiers are used. They tell the compiler that this particular variable is not going to be used in the program. The **blank identifier** is dictated by the underscore (\_)which stores the value in a blank variable.

In the following example, we are calling the function sum as declared in the above example. Here, we don't need the variable c; so we are using the blank identifier for it.

**Example:**

`package main`

`import "fmt"`

`func sum(a, b int, c string) (sum_value int, c_val string){`

`sum_value = a+b`

`c_val = c`

`return`

`}`

`func main() {`

`a := 90`

`b := 30`

`result, _ := sum(a, b, "Hello Go")`

`fmt.Println ("Values returned from the function are:", result) // prints “Values returned from the function are: 120”`

`}`

**Output:**

`Values returned from the function are: 120`

# [Using a function as a type](#toc.xhtml#s59a)

In the Go language, we can create our function type. The syntax for creating function type is as follows:

**Syntax:**

`type sub func(a int, b int) int`

The above syntax creates a function type sub that accepts two integer arguments and returns an integer value.

**Example:**

`package main`

`import "fmt"`

`type sub func(a int, b int) int`

`func main() {`

`var result sub = func(a int, b int) int {`

`return a-b`

`}`

`fmt.Println("Result is: ", result(100, 70))`

`}`

**Output:**

`Result is: 30`

# [Anonymous functions](#toc.xhtml#s60a)

A function without any name is called **lambda** or **anonymous function**. These functions are assigned to a variable and that variable is used to call the function. These functions can be defined inside the main function as follows:

`func main() {`

`a := func(){`

`fmt.Println("Introducing anonymous function")`

`}`

`a()`

`}`

Or

In the example given below, we are not using any function name or variable to call the function. Thisis also an example of calling a function without any name.

`func main() {`

`func(){`

`fmt.Println("Introducing anonmyous function")`

`}()`

`}`

Or

`func main() {`

`a := func() string{`

`value := "Introducing anonymous function"`

`return value`

`}`

`value := a()`

`fmt.Println(value)`

`}`

Both will print the same output: `Introducing anonymous function`

# [Return Anonymous functions](#toc.xhtml#s61a)

There canbe some functions that return an anonymous function. Let’s understand them with the help of the example given below:

`package main`

`import "fmt"`

`func return_anon() func(string){//declare type of return value as function`

`return func(message string){`

`fmt.Println(message)`

`}`

`}`

`func main() {`

`return_anon_variable := return_anon()`

`fmt.Println(return_anon_variable) //prints the address of function returned by ‘return_anon’ functionreturn_anon_variable("Hello")`

`}`

**Output:**

`0x47d880`

`Hello`

Here, we have a function `return_an`on that returns a value of `function` type. In the body of the function, we return an anonymous function that prints the value passed in its argument. Now in the `main` function, we capture the value returned by return_anon function that is of type function. `Return_anon_variable` is representing a function. That's why we can use the variable `return_anon_variable` to call the function and pass the required arguments.

# [Closures](#toc.xhtml#s62a)

A closure is a function or function value that references variables from out of its body. These functions can access and assign the values to a variable that are defined somewhere outside the function body. These functions are bound with that referenced variable.

**Example:**

`package main`

`import "fmt"`

`func return_anon() func() int{`

`count := 0`

`return func() int{`

`count++;`

`return count`

`}`

`}`

`func main() {`

`return_anon_variable := return_anon()`

`fmt.Println("value returned by 'return_anon' is:", return_anon_ variable) //prints ‘ox47da70’`

`fmt.Println("count is:", return_anon_variable()) //prints “count is 1”`

`fmt.Println("count is:", return_anon_variable()) //prints “count is 2”`

`return_anon_variable2 := return_anon() //new instance`

`fmt.Println("count is:", return_anon_variable2()) //prints “count is 1”`

`}`

**Output:**

`value returned by 'return_anon' is: 0x47da70`

`count is: 1`

`count is: 2`

`count is: 1`

In the preceding example, the value returned by the function `return_anon` is a closure. Here, the anonymous function is capable of accessing the variable `count`. This anonymous function preserves the value of the `count` variable, and thus keeps track ofthe number of times the function is being called. In the main function, `return_anon_variable` has a value returned by the function that is also a function. That's why when we print its value, it shows the address of that function. Whenever we call the function `return_anon_variable`, the value of the count variable is modified by the anonymous function. Here, `return_anon_variable2` works as a new instance of that function. That's why on calling through this variable, it returns the new value of count. Referencing the variable outside of its body is the key point in closures.

# [Recursive functions](#toc.xhtml#s63a)

A **recursive function** can be defined as a function that calls itself directly or indirectly at a finite number of times until the recursive condition becomes false. Recursive functions should have the termination point at some stage.

`func recursive_function(){`

`recursive_function()`

`}`

The above example is of infinite recursion. No condition will stop the loop and terminate the program. There must be a conditional statement to come out this of infinite recursion to continue the execution.

**Example:**

`package main`

`import "fmt"`

`func factorial(num int) int {`

`if num> 1 {`

`return num * factorial(num-1)`

`} else {`

`return 1`

`}`

`}`

`func main() {`

`num := 10`

`result := factorial(num)`

`fmt.Println("Factorial result is:", result)`

`}`

**Output:**

`Factorial result is: 3628800`

# [The defer keyword](#toc.xhtml#s64a)

The defer keyword is used to execute a function at the end, after executing all the statements specified in the main function. As the compiler gets the defer keyword, the argument values passed within a function are evaluated with the execution of the deferring keyword. When the control returns from the main function, all the deferred functions are executed in the ***Last In FirstOut*** order.

**Example:**

`package main`

`import "fmt"`

`func defer_fun() {`

`fmt.Println("Hi I am introducing deferred function")`

`}`

`func main() {`

`fmt.Println("Before defer statement")`

`defer defer_fun()`

`fmt.Println("After defer statement")`

`}`

**Output:**

`Before defer statement`

`After defer statement`

`Hi I am introducing deferred function`

# [Variadic function](#toc.xhtml#s65a)

**Variadic functions** are flexible with passing arguments. These functions can take an arbitrary number of arguments. It is necessary to specify the type of the last parameter. The symbol specifies that the function can take any number of arguments, whether zero or more.

**Example:**

`func add(args …int) int {`

`total := 0`

`for _, v := range args {`

`total += v`

`}`

`return total`

`}`

`func main() {`

`fmt.Println(add(1, 2, 3))`

`}`

**Output:**

`6`

Here, `args` is a list of passed arguments while calling the function. We can pass any number of integer values as needed.

# [Conclusion](#toc.xhtml#s66a)

In this chapter, we got to know how to reduce the lines of code by using functions. Concepts like "blank identifier," "closures," and "named return values" are new in the Go language. We saw that by using the defer keyword, some of the necessary tasks can be executed at the end. With the use of variadic function, we get the flexibility with the number of arguments in a function. We gain an understanding of functions that call themselves and reduce complexity. In this chapter, we bound the code into a block using the function. Let's learn the function binding in a package in the next chapter.

# [Questions](#toc.xhtml#s67a)

1.  What is the use of functions in Go language?
2.  What is the importance of the main function in Go language?
3.  What is the difference between call by value and call by reference?
4.  What do you understand by named return values in a function?
5.  In what scenario can blank identifiers be used?
6.  What function is used to pass an arbitrary number of arguments?
7.  How to create function type in Go language?
8.  Which keyword is used to call a function at the end of the main function?
9.  What is the use of the anonymous function in Go language?

# [CHAPTER 8](#toc.xhtml#c08)

# [Packages in Go](#toc.xhtml#c08)

In the last chapter, we discussed the function that provides the feature of maintainability and reusability of code. Package facilitates the same functionality. The package is a set of functions or variables than can be accessed in any program by importing the specific package. Packages control the function definition and visibility. Some functions can be accessed outside that package and some cannot be accessed. Let’s understand packages in the Go language.

# [Structure](#toc.xhtml#s68a)

In this chapter, we will discuss the following topics:

*   Introduction to packages
*   Main package
*   fmt package
*   Importing a package
*   Creating a custom package
*   Nested package
*   Installing third party package
*   Circular import
*   Top Go libraries

# [Objectives](#toc.xhtml#s69a)

After studying this chapter, you will be able to:

*   Use/import packages in your Go program
*   Install 3rd party packages in Go
*   Get the importance of main & fmt package in Go programs.
*   Create custom packages as per our requirement
*   Work with nested packages in Go program

# [Introduction](#toc.xhtml#s70a)

A **package** is simply a directory/ folder that organizes multiple .go files. These Go files/source code can be reused in multiple Go applications. As a package represents a directory, the naming convention for a package is the same as a system directory. An underscore is used for naming convention with those files that contain test code or are bound to a specific platform. Every package has its unique name. The package is the starting point for any Go program. When we install Go, a workspace is reserved in the system directory for Go applications. This workspace is divided into multiple subdirectories and files. `src`, pkg, and `bin` directories are some of them at its root. In the `src` directory, we create Go programs that are organized as packages. So it is clear that every Go program is a part of the package. The `bin` directory contains the executable Go programs. The `pkg` directory contains Go package objects. In the `pkg` directory, we have a standard package of Go language that is used for real-world applications.

# [Main package](#toc.xhtml#s71a)

As we have discussed, every Go program is a part of the package, therefore every program is declared within the main package to make a program executable. Every program that is a part of the main package creates an executable binary file that calls the `main` function of the program. The main function is the key to any go program. The `main` package tells the compiler that the source code is an executable program and should not be treated like a shared library. While creating a shared library, there will not be any main package or the main function. For an executable program, package main is the first statement, and thus the entry point.

# [Fmt package](#toc.xhtml#s72a)

`fmt` stands for **format**. The format package implements formatted I/O with various functions. `fmt` packages make it easy to display data to the console. The package or `fmt` directory has various Go files that are used to scan or display data to the console. The key concept is the same as the C language’s `printf/` scanf functions. In Go, we use the symbol %, followed by a letter to indicate a placeholder as %v is a generic placeholder while %s represents a string.

# [Importing package](#toc.xhtml#s73a)

Declaration of the import keyword tells the compiler that the defined packages need to import in the running source code. The path of the package is defined as a string literal within import statement called **import path**. Go searches for the import path in `GOROOT/src` first and then looks for `GOPATH/src` if it doesn’t get the import path in `GOROOT/src`. The imported package can be accessed anywhere in the file but it cannot be used throughout the package in which the source code is defined. In Golang, packages, functions, or variables can be imported from other packages. There are two ways to import multiple packages within the same source code.

`import "fmt"`

`import "math"`

or

`import(`

`"fmt"`

`"math"`

`"github.com/mlowicki/package_name" //importing custom package`

`)`

Imported packages can only refer to exported identifiers from the importing package. Unexported identifiers cannot be accessed as they are the private members of the package. An identifier should follow two basic rules to be an exported identifier. These are as follows:

*   The first letter of an identifier should be in upper case.
*   The identifier should be defined in a package block (outside the function) or it should be any function or field name.

Let’s begin with a simple executable Go program that is defined inside the `src` directory. First, create a directory within `src`, say `first`. Create a file `first.go`. It is not necessary to keep the name of the file same as the directory name; it can be different.

`//first.go`

`package main //represents that the file belongs to main package`

`import "fmt" //import a package named fmt that contains ‘println’ method`

`func main(){`

`fmt.Println("This is Go Program")`

`}`

Compile the program by go `build first.go`. An executable file of the source code within the same directory will be created. To run the source code, we can also run its executable file by `first.exe.`

In the case of a long import path, we can override the import path by an identifier to access exported identifiers of a package. This is called an alias of a package.

**Example:**

`package main`

`import(`

`"fmt"`

`"math"`

`)`

`func main(){`

`fmt.Println(m.Pow(6, 2))`

`}`

We can use \_ to refer to a package. As we discussed in the previous chapters, \_ acts as a null container, so we can just refer to a package by an underscore but we cannot use it. The compiler throws an error if we declare a package but don’t use it in our program. In such scenarios, we can refer to it by an underscore.

`import _ "math"`

Using dot (.) as an alias of a package allows access to all the exported identifiers without using any qualifiers. We can access the exported identifiers directly in our program. Such an import statement is called **dot import** in the Go language.

**Example:**

`package main`

`import (`

`"fmt"`

`."math"`

`)`

`func main() {`

`r := Pow(-6, 2)`

`fmt.Println("example of dot import:", r)`

`}`

# [Creating a custom package](#toc.xhtml#s74a)

We have discussed how and why we use packages. Other than the standard library, we can create our package as per our need. If we are creating an application and we need to perform some specific task again and again, then we can define such a task as a function/Go source file in a package. It is simple to just import a package, access that function, and execute that task.

Consider a program in which we need to create a **Fibonacci series** and the factorial of a number. Instead of performing it in a single program, we’ll create a package having functions for both of them.

We have two environment variables in the Go language, `$GOROOT` and `$GOPATH` at which the Go tool searches for any package. By default, this variable has a specific path but we can set it to another path as per our requirement. We can check all default variables by using the command: go env. It will list down all the variables with their default values.

*   **$GOROOT**
    
    When installing Go, `GOROOT` is the default path where all the installed Go files take place. It is used by the Go tool to find the compiler and standard library of the Go language. `GOROOT` is similar to the `JAVA_HOME` variable in Java. When we compile Go from source, the value of `GOROOT` variable is embedded into the Go tool. We can also set the value of `GOROOT` variable as per our own wish but it is not advisable because in such case, it will override the value in Go tool. In this case, the Go tool will point the compiler from one version and standard libraries from another one.
    
*   **$GOPATH**
    
    Outside `$GOROOT`, the `GOPATH` variable is used to specify the workspace directory for all Go projects or third party libraries. For every program, the Go tool searches the imported package in the `$GOROOT` or `$GOPATH/src` directory. By default, `GOPATH` is set to the user’s home directory in any operating system. We can set multiple paths to the `$GOPATH` variable. In Unix, the values of `GOPATH` variables are separated by a colon while in Windows, these values are separated by a semicolon.
    
    So, the first thing to remember is that the custom package should be created within Go’s `src` directory. We can create nested directories over there.
    

Let’s make a directory named custom\_package within src. Create a package named factFib. Within this package, we’ll create two Go files, one for finding the factorial and the other one for the Fibonacci series.

`//fact.go`

`package factFib`

`func Factorial(num int)int{`

`if num> 1 {`

`return num * Factorial(num-1)`

`} else {`

`return 1`

`}`

`}`

Here is the code for the Fibonacci series:

`// fib.go`

`package factFib`

`import "fmt"`

`func Fibonacci(num int){`

`f1 := 0`

`f2 := 1`

`nextnum := 0`

`for i := 1; i <= num; i++ {`

`fmt.Println(f1)`

`nextnum = f1 + f2`

`f1 = f2`

`f2 = nextnum`

`}`

`}`

Now create an executable Go program to use this package in our workspace. Let’s create a file name `myprogram.go.`

`// myprogram.go`

`package main //indicates this is an executable file`

`import "fmt"`

`import "custom_package/factFib" //importing custom package ‘factFib’`

`func main(){`

`number := 10`

`fmt.Println(factFib.Factorial(number)) //calling exported function ‘Factorial’`

`fmt.Println("Fibonacci series is:")`

`factFib.Fibonacci(10) //calling exported function ‘Fibonacci’`

`}`

Here, while importing the package `factFib`, the tool will look for two directories, either `default_path_of_GOROOT/src/custom_package/factFib` for `$GOROOT` or `default_path_of_GOPATH/src/custom_package/factFib for $GOPATH. Let’s execute the program and see the output.`

**Output:**

`3628800`

Fibonacci series is:

`0`

`1`

`1`

`2`

`3`

`5`

`8`

`13`

`21`

`34`

# [Nested packages](#toc.xhtml#s75a)

In the Go language, we can create a package inside a package. With the nested package, we provide a relative path of the package at the place of the import path.

Let’s begin with creating a nested package named `nested_package` within the package `factFib` that we created previously. Within `nested_package`, create a file `nestedfile.go.`

`// nestedfile.go`

`package nested_package`

`import "fmt"`

`func Nested_function(){`

`fmt.Println("Here is the example of nested package")`

`}`

Use this package in the Go program as shown below:

`// myprogram.go`

`package main`

`import "custom_package/factFib/nested_package"`

`func main(){`

`nested_package.Nested_function() //prints ‘Here is the example of nested package’`

`}`

# [Installing third party package](#toc.xhtml#s76a)

Go facilitates cloning remote code in Go’s `src` package directory. We can get any package from GitHub or anywhere else and use it in our program directly. There is a need to specify the import path of the third party package as GitHub if we are using the package from GitHub.

When someone publishes a code/package on GitHub, they must provide two things: user-name and repository or we can say, package path. To use the package in our code, we can import files from **[http://github.com/user\_name/repo\_name](http://github.com/user_name/repo_name)** and save them in the `src/github.com/user_name/repo_name` directory. We can also import the package by using the link `github.com/user_name/repo_name` (import `github.com/user_name/repo_name`). Here, `repo_name` is the package that we are going to use in our program.

# [Circular import](#toc.xhtml#s77a)

**Circular import** is importing such packages where two or more modules depend on each other. Circular imports are not allowed in the Go language. If the compiler detects any import cycles, it throws a compile-time error.

Let’s consider a case of circular import. Suppose that we have a package on that is accessing an exported member of another package `two`. In the package two, we are importing and accessing the exported member of package one. So here, both the packages are dependent on each other.

`// one/one.go`

`package one`

`import (`

`"fmt"`

`"custom_package/circular_import/two"`

`)`

`func One_function(){`

`One_val := "Variable of package one"`

`fmt.Println(One_val)`

`two.Two_function()`

`}`

Here is the code for package `two.`

`// two/two.go`

`package two`

`import (`

`"fmt"`

`"custom_package/circular_import/one"`

`)`

`func Two_function(){`

`Two_val := "Variable of package two"`

`fmt.Println(Two_val)`

`}`

Now create an executable Go file to use package one. In this file, we are calling an exported method of package one.

`// circularimport.go`

`package main`

`import (`

`"custom_package/circular_import/one"`

`)`

`func main(){`

`one.One_function()`

`}`

On executing this program, the Go compiler will show the following error:

![](images/8-1.jpg)

**Figure 8.1:** Circular import

In `circularimport.go,` on importing package one, it finds the statement to import package two. While importing package two, it again finds the statement to import package one. In this way, cyclic dependency exists here.

An analysis of circular dependency concluded that there is no need to have these dependencies in any Go program. We can create more or less number of packages to avoid such situations.

To overcome such a problem, we can create a new package as an interface and define all the members of package two that are accessed by package one. By doing so, we can import that new package in package one rather than package two. However, in some cases, this won’t be the proper solution. To completely avoid import dependency, we can merge both the packages in a single one. In such a case, all the members can be accessed easily and no circular dependency would be there. Here, we are merging both packages in one as shown below:

`// one/one.go`

`package one`

`import (`

`"fmt"`

`// "custom_package/circular_import/two"`

`)`

`func One_function(){`

`One_val := "Variable of package one"`

`fmt.Println(One_val)`

`Two_function()`

`}`

`func Two_function(){`

`Two_val := "Variable of package two"`

`fmt.Println(Two_val)`

`}`

Here is the output on executing `circulatimport.go.`

**Output:**

`Variable of package one`

`Variable of package two`

# [Top Go libraries](#toc.xhtml#s78a)

Go has a rich set of libraries. Here is a list of some of the top libraries that we have in the Go language:

*   **Go kit** 
    *   The solutions for Go-related microservices in terms of system observability, infrastructure integration, program design, etc.
    *   Avoids common pitfalls.
    *   Builds robust, reliable, and maintainable microservices.
*   **GORM** 
    *   Best ORM library for Golang.
    *   Converts data between incompatible type systems.
    *   Deals with relational database.
    *   Has a feature of callbacks, transactions, logger, associations, composite primary key, and many others.
*   **cli** 
    *   A part of the Data Plane Development Kit (DPDK).
    *   Helps to build command-line applications in Go.
    *   Makes it easy to create flags, bash-completion, routines, and even generated help text.
    *   Provides support for colors and cursor movement.
    *   Has the ability to add and remove commands, files, and directories dynamically.
*   **Vegeta** 
    *   A versatile HTTP load testing tool and library.
    *   Can also be used as a command-line utility.
*   **Fuzzy** 
    *   This package includes a fuzzy matching algorithm.
    *   Provides the results in milliseconds with quality matches.
    *   It is even Unicode aware.
*   **Kubernetes** 
    *   An open-source container orchestration system for application deployment, scaling, and management.
    *   Has automatically generated clients.
    *   Contains a minimal client for the Kubernetes API.
*   **Testify** 
    *   A set of multiple packages that are used to test the code.
    *   The assert package in it provides assertion functions for testing.
    *   The ‘http’ package checks for Http activity.
    *   The mock package makes it possible to mock the object and verify calls.
    *   The suite package provides a basic structure of structs as test suites.
*   **gocheck** 
    *   Helps in error-catching logic with proper error reports.
    *   Provides support for expected failures.
    *   Manages temporary directories.
    *   Facilitates comments surrounding checks on failure reports.
*   **glog** 
    *   Facilitates the use of flags at the command line.
    *   Implements logging analogous to the Google-internal C++ INFO/ERROR/V setup.
    *   Provides functions for warning, error, fatal, info, and others.
*   **color** 
    *   Provides the multiple color option for Go applications
    *   Provides supports for mixing colors.
    *   Facilitates background colors, font style as bold, italic, and many others.

# [Conclusion](#toc.xhtml#s79a)

In this chapter, we learned the use of packages in the Go program. We saw how public and private members are declared in a package and how to access them in code outside the package. In every Go program, the main package is imported first. Here, we understand the need for the main package. We have acquired the concept of nested package and circular import (package dependency) in Go. We learned all about packages in this chapter. In the next few chapters, we’ll thoroughly discuss data types.

# [Questions](#toc.xhtml#s80a)

1.  What is the importance of the main package in Go?
2.  What is the need for fmt package in Go language?
3.  Which path does a do compiler search for to import a package in Go?
4.  How do we declare private members in a package?
5.  What is "dot import" in Go?
6.  How can we create custom packages in Go? Explain with an example.

# [CHAPTER 9](#toc.xhtml#c09)

# [Arrays and Slices](#toc.xhtml#c09)

While discussing data types in the Go language, we see two types of data, primitive and non-primitive. Primitive is an in-built data type in Go while non-primitive is derived from the primitive data type. Array and slices are those non-primitive data types that contain a set of similar type of elements. Let’s go through this chapter and understand the need for arrays and slices.

# [Structure](#toc.xhtml#s81a)

In this chapter, we will discuss the following topics:

*   Introduction to array 
    *   Declaring an array
    *   Initializing an array
    *   Multidimensional array
    *   Functions of an array
*   Introduction to slices 
    *   Declaring slices
    *   Initializing slices
    *   Slices from an array
    *   Slice from slice
    *   Slice from structs
    *   Slice internals
    *   Slice using the make function
    *   Two-dimensional slices
    *   Slice functions

# [Objective](#toc.xhtml#s82a)

After studying this chapter, you’ll be able to:

*   Organize large data in an efficient way that is easy to search and deal with.
*   Work with a large number of data of the same type with a single reference.
*   Understand how slices overcome the issues that we get with arrays.
*   Use various in-built functions that work with arrays and slices.

# [Introduction](#toc.xhtml#s83a)

**Array and slices** are the first two collection types in the Go language. An **array** is a set of similar type of elements such that an element can be accessed by its index value. The index always starts with zero in the array. Arrays are of fixed length in the Go language. Arrays are value types in Golang. On assigning an array to a variable or passing to a function, a complete array will be copied rather than its reference.

# [Declaring an array](#toc.xhtml#s84a)

An array of type T has n no. of values as declared below:

`var name_of_array[n]T`

or

`var a [3] int`

Declare an array that has 3 integer values.

By default, all array elements are initialized with zero if they are of the type integer. If an array is declared of the string type, then it will be initialized with an empty string.

**Example:**

`package main`

`import "fmt"`

`func main() {`

`var array_int[10] int`

`var array_float[10] float32`

`var array_string[10] string`

`var array_complex[10] complex128`

`fmt.Println("Int type array:", array_int)`

`fmt.Println("Float type array:", array_float)`

`fmt.Println("String type array:", array_string)`

`fmt.Println("Complex type array:", array_complex)`

`}`

**Output:**

`Int type array: [0 0 0 0 0 0 0 0 0 0]`

`Float type array: [0 0 0 0 0 0 0 0 0 0]`

`String type array: []`

`Complex type array: [(0+0i) (0+0i) (0+0i) (0+0i) (0+0i) (0+0i) (0+0i) (0+0i) (0+0i) (0+0i)]`

# [Initializing an array](#toc.xhtml#s85a)

Assigning values to an array is called an **array initialization**. After declaring an array, we can initialize it with predefined values by accessing its index as shown below:

`var arr [5] int = [5] int{1, 2, 3, 4, 5}`

`fmt.println(arr) // [1 2 3 4 5]`

Or

`var arr [5]int`

`arr[0] = 1`

`arr[1] = 2`

`arr[2] = 3`

`arr[3] = 4`

`arr[4] = 5`

`fmt.Println(arr) // [1 2 3 4 5]`

We can declare and initialize an array simultaneously with syntax:

`name_of_array := [size] type_of_values {values}`

`arr := [5]int{1, 2, 3, 4, 5}`

`fmt.Println(arr) // [1 2 3 4 5]`

It is not necessary to initialize an array with the same number of values that we define at the time of declaration. We can initialize an array with lesser values; the remaining indexes will have their default values.

**Example:**

`var arr [5]int`

`arr[1] = 2`

`arr[3] = 4`

`fmt.Println(arr) // [0 2 0 4 0]`

Or

`arr := [5]int{1, 2, 3}`

`fmt.Println(arr) // [1 2 3 0 0]`

In Golang, we can use an ellipsis to specify the implicit length. By using an ellipsis, we can initialize an array with as many values as we want. An ellipsis is dictated by three dots within square brackets \[…\]. If we are using an ellipsis, the size of an array is equal to the number of values that we are initializing an array with.

**Example:**

`arr := […] int {1, 4, 7, 2, 7, 9, 3, 5}`

`fmt.Println(arr) // [1 4 7 2 7 9 3 5]`

# [Need for an array](#toc.xhtml#s86a)

Let’s consider an application in which we need to use the names of all the students of a class. Let’s say that we write it as:

`package main`

`import "fmt"`

`func main() {`

`var name1 string = "aman"`

`var name2 string = "rahul"`

`var name3 string = "geet"`

`var name4 string = "preeti"`

`fmt.Printf("Names are %q, %q, %q and %q", name1, name2, name3, name4) //Names are "aman", "rahul", "geet" and "preeti"`

`}`

Here, we are keeping the record of every name, but the problem is that in a large application, we will not know how many students are there. What if we need to add some more names here at run time or delete some records? To overcome such problems, arrays/slices are a great solution. They decrease the program size. Also, we can grow or shrink an array as per our need. Here is the program with arrays:

`func main() {`

`names:=[…] string{"aman", "rahul", "geet", "preeti"}`

`fmt.Printf("Names are %q", names)`

`}`

# [Multidimensional arrays](#toc.xhtml#s87a)

Till now, we have discussed single dimensional arrays. Multidimensional arrays can be defined as arrays of an array. A **multidimensional array** can be broken down into multiple single dimensional arrays. In such arrays, the data is stored in the tabular form (row-major order). The size of a multidimensional array is defined by its dimensions that is equal to the multiplication of the sizes of all dimensions.

These arrays are declared as:

`Name_of_array := [dim1][dim2]..type_of_array{values_of_array}`

The number of square brackets specifies the number of dimensions of the array.

`arr := [3][2] int {`

`{1, 2},`

`{4, 5},`

`{7, 8},`

`}`

`fmt.Println(arr) // [[1 2] [4 5] [7 8]]`

Given above is a two dimensional array of size 3x2. The declaration of an array represents that it contains three single dimensional arrays of the length of two. Like 1D arrays, there is no need to initialize an array with all the elements. Uninitialized arrays will take their default values.

`arr := [3][2] int {`

`{1, 2},`

`{7},`

`}`

`fmt.Println(arr) // [[1 2] [7 0] [0 0]]`

We can initialize multidimensional in another way as well:

`var arr [3] [3] int`

`arr[0] = [3] int {1, 2, 3}`

`arr[1] = [3] int {4, 5, 6}`

`arr[2] = [3] int {7, 8, 9}`

`fmt.Println(arr) //[[1 2 3] [4 5 6] [7 8 9]]`

# [Functions of an array](#toc.xhtml#s88a)

Here are some functions that work with arrays in Go.

*   **Length of an array**
    
    Go provides a built-in function to get the **length of an array**. It tells the number of elements an array can store. As arrays are of fixed size in Go, the compiler throws an error (out of bound) on accessing/inserting an element out of its size.
    
    **Example:**
    
    `func main() {`
    
    `arr1D := […] int {1, 4, 7, 2}`
    
    `arr2D := [3][2] int {`
    
    `{1, 2},`
    
    `{7},`
    
    `}`
    
    `fmt.Println("Length of 1D array", len(arr1D))`
    
    `fmt.Println("Length of 2D array", len(arr2D)) //tells number of rows it can have.`
    
    `}`
    
    **Output:**
    
    `Length of 1D array 4`
    
    `Length of 2D array 3`
    
*   **Array comparison**
    
    Two arrays are called equal if they both are of the same type and size, have the same elements, and all elements are in the same order in both arrays. The comparison operator is dictated as ==. It return the Boolean result true if both the arrays are equal, else false. It first checks for the data type of both arrays and then matches the values by index.
    
    **Example:**
    
    `func main() {`
    
    `arr1 := [4] int {1, 4, 7, 2}`
    
    `arr2 := [4] int {1, 4, 7}`
    
    `arr3 := [3][2] int {`
    
    `{1, 2},`
    
    `{7},`
    
    `}`
    
    `arr4 := [3][2] int {`
    
    `{1, 1},`
    
    `{7},`
    
    `}`
    
    `arr5 := [4] int{1, 4, 7, 0}`
    
    `fmt.Println("arr1 and arr2", arr1==arr2)`
    
    `fmt.Println("arr3 and arr4", arr3==arr4)`
    
    `fmt.Println("arr2 and arr5", arr2==arr5)`
    
    `}`
    
    **Output:**
    
    `arr1 and arr2 false`
    
    `arr3 and arr4 false`
    
    `arr2 and arr5 true`
    
    `arr1` and `arr2` are of the same size but `arr2` takes default value 0 at its last index. So, the result is `false.`
    
    `arr3` and `arr4` are both of the same size, but the elements are different. So, the result is `false.`
    
    `arr2` and `arr5` both have the same size and elements. So, `arr2` and `arr5` are equal and the result is `true.`
    
*   **Copying an array**
    
    **Copying an array** is just assigning an array into another one. Since in Golang, an array behaves like a value instead of reference, so changing any value of one array does not have any effect on the other one.
    
    **Example:**
    
    `func main() {`
    
    `arr1 := [4] int {1, 4, 7, 2}`
    
    `arr2 := arr1`
    
    `arr2[2] = 90`
    
    `fmt.Println("arr1 is", arr1) // [1 4 7 2]`
    
    `fmt.Println("arr2 is", arr2) // [1 4 90 2]`
    
    `}`
    
*   **Passing an array to a function**
    
    An array can be passed as an argument to any function. In a function declaration, the parameter should be defined as an array that tells the compiler that an array is being passed as an argument for function call.
    
    **Example:**
    
    `func main() {`
    
    `arrval := [4] int {1, 4, 7, 2}`
    
    `fmt.Println("sum of array elements is:", sum(arrval))`
    
    `}`
    
    `func sum(arr [4]int) int{`
    
    `sum := 0`
    
    `for i:=0; i<len(arr); i++{`
    
    `sum = sum + arr[i]`
    
    `}`
    
    `return sum`
    
    `}`
    
    **Output:**
    
    `sum of array elements is: 14`
    
*   **Iteration over an array**
    
    On creating an application, there can be many cases in which we might need to iterate over an array. For example, to find the sum of all the elements of an array, we have to access every element of an array. We can easily iterate an array by using for loop as shown below:
    
    **Example:**
    
    `func main() {`
    
    `arr :=[…] int {1, 4, 7, 2, 7, 9, 3, 5}`
    
    `sum := 0`
    
    `for i:=0; i<len(arr); i++{`
    
    `sum = sum +arr[i]`
    
    `}`
    
    `fmt.Println("sum of values:", sum)`
    
    `}`
    
    Here, `len` function is used to get the length of an array. We can use range function instead of the above as shown below:
    
    **Example:**
    
    `func main() {`
    
    `arr := […] int {1, 4, 7, 2}`
    
    `sum := 0`
    
    `for index, value := range arr{`
    
    `fmt.Println("index is:", index)`
    
    `fmt.Println("value is:", value)`
    
    `sum = sum + value`
    
    `}`
    
    `fmt.Println("sum of values:", sum)`
    
    `}`
    
    **Output:**
    
    `index is: 0`
    
    `value is: 1`
    
    `index is: 1`
    
    `value is: 4`
    
    `index is: 2`
    
    `value is: 7`
    
    `index is: 3`
    
    `value is: 2`
    
    `sum of values: 14`
    
    Here, `range arr` always returns two values, index and the value at that index. It is compulsory to write both the variables on the left side. If we write value:= `range arr,` by default it’ll return the indexes, not the values. In case if we don’t need indexes in our program, we can assign it to the blank identifier, otherwise the compiler will give an error.
    
    ![](images/9-1.jpg)
    
    **Figure 9.1:** Array program
    
    ![](images/9-2.jpg)
    
    **Figure 9.2:** Index not used error
    
    Solution of the above issue is shown below:
    
    `func main() {`
    
    `arr := […] int {1, 4, 7, 2}`
    
    `sum := 0`
    
    `for _, value := range arr{`
    
    `sum = sum + value`
    
    `}`
    
    `fmt.Println("sum of values:", sum) // sum of values: 14`
    
    `}`
    
    So far, we have discussed arrays but a few points are missing with arrays in the Go language. As arrays are of fixed size, we cannot append any element at run time. We have to define the size of the array at the compile time. This increases time complexity. With arrays, we are not allowed to use a variable to define its array size. If we declare an array as shown below, the compiler will give an error of non-constant array bound size.
    
    `func main() {`
    

`var size int = 4`

`arrval := [size] int {1, 4, 7, 2}`

`fmt.Println("sum of array elements is:", arrval)`

`}`

# [Slices](#toc.xhtml#s89a)

To overcome the problems we face with arrays, Go provides the more powerful, dynamically typed data type slices. **Slice** is a segment of an array that holds some elements of the same data type. Slices are typed to the elements they contain instead of their size.

# [Declaring slices](#toc.xhtml#s90a)

Just like an array, slices are indexable and declared in the same way as arrays without specifying their size.

`var s [] int`

It declares a nil slice of integer type as slice is called nil if it doesn’t refer to an array.

# [Initializing slices](#toc.xhtml#s91a)

A slice can be initialized with a slice literal as we do with an array without defining its size. As slices are the reference of arrays, while creating slices using literals, it first creates an array and then returns a reference to slice. Basically, slices don’t contain any data. Data is stored by an array and the reference of that array is defined as slice.

**Example:**

`func main() {`

`var slice1 [] int = [] int {1, 2, 3, 5}`

`slice2 := [] int {1, 2, 3, 5}`

`fmt.Println("slice with literal", slice1) // [1 2 3 5]`

`fmt.Println("slice short hand declaration", slice2) // [1 2 3 5]`

`}`

# [Slices from an array](#toc.xhtml#s92a)

Slice is a segment of an array. We can create a slice from an array also. To create a slice from an array, we need to specify two indices, ‘low’ and ‘high’ where low indicates the starting index of an array and high indicates the next of last index. This means that we are getting all array elements from index ‘low’ to ‘high-1.’ These two indices are separated by a colon at the time of the slice declaration. By default, low has 0 indexes and high contains the length of the array. If these indices are not specified, the compiler assumes their default values to create a slice.

**Syntax:**

`var name_of_slice [] type_of_slice := name_of_array[low:high]`

**Example:**

`func main() {`

`var arrayval [10] int = [10] int {1, 2, 3, 4, 5, 6, 7, 8, 9, 10}`

`slice1 := arrayval[3:7]`

`slice2 := arrayval[:6]`

`slice3 := arrayval[5:]`

`slice4 := arrayval[:]`

`fmt.Println("slice from array:", slice1)`

`fmt.Println("slice with default low indice:", slice2)`

`fmt.Println("slice with default high indice:", slice3)`

`fmt.Println("slice with default low and high indice:", slice4)`

`}`

**Output:**

`slice from array: [4 5 6 7]`

`slice with default low indice: [1 2 3 4 5 6]`

`slice with default high indice: [6 7 8 9 10]`

`slice with default low and high indice: [1 2 3 4 5 6 7 8 9 10]`

# [Slice from slice](#toc.xhtml#s93a)

We can create a slice from an existing slice in the same way that we are creating it from an array. Re-slicing doesn’t copy the data but a new slice is created which refers to the original array also.

**Example:**

`func main() {`

`var arrayval [10] int = [10] int {1, 2, 3, 4, 5, 6, 7, 8, 9, 10}`

`slice1 := arrayval[1:8]`

`slice2 := slice1[:6]`

`fmt.Println("slice from array:", slice1)`

`fmt.Println("slice from existing slice", slice2)`

`}`

**Output:**

`slice from array: [2 3 4 5 6 7 8]`

`slice from existing slice [2 3 4 5 6 7]`

Here is an example that shows slices are just reference of an array.

`func main() {`

`var arrayval [10] int = [10] int {1, 2, 3, 4, 5, 6, 7, 8, 9, 10}`

`slice1 := arrayval[1:8]`

`slice2 := slice1[:6]`

`fmt.Println("slice from array:", slice1)`

`fmt.Println("slice from existing slice", slice2)`

`arrayval[2] = 90`

`fmt.Println("slice from array after modifying an array:", slice1)`

`fmt.Println("slice from existing slice after modifying an array", slice2)`

`}`

**Output:**

`slice from array: [2 3 4 5 6 7 8]`

`slice from existing slice [2 3 4 5 6 7]`

`slice from array after modifying an array: [2 90 4 5 6 7 8]`

`slice from existing slice after modifying an array [2 90 4 5 6 7]`

# [Slice from structs](#toc.xhtml#s94a)

A **struct** is a set of a different type of fields. We’ll discuss it in depth later. Just like an array, slices can be initialized with structs also. These are `struct` type of slices.

**Example:**

`func main() {`

`record := []struct {`

`roll_no int`

`name string`

`present bool`

`}{`

`{1, "Rahul", true},`

`{3, "Akansha", false},`

`{5, "Ram", true},`

`}`

`fmt.Println("sructs type slice is:",record) //sructs type slice is: [{1 Rahul true} {3 Akansha false} {5 Ram true}]`

`}`

# [Slice internals](#toc.xhtml#s95a)

Generally, a slice consists of a pointer to an array segment. The length of the array segment and the maximum to which the slice can be expanded.

![](images/9-3.jpg)

**Figure 9.3:** Slice structure

*   **Pointer**
    
    We have already discussed that slices don’t store any data; they only refer to an array or a section of an underlying array. Initializing a slice from an array and modifying the array elements changes the slice value too. We have seen an example of this. Similarly, changing the element value of a slice reflect its referred array.
    
    **Example:**
    
    `func main() {`
    
    `var arrayval [10] int = [10] int {1, 2, 3, 4, 5, 6, 7, 8, 9, 10}`
    
    `slice1 := arrayval[1:8]`
    
    `slice2 := slice1[:6]`
    
    `fmt.Println("original array", arrayval)`
    
    `fmt.Println("slice from array:", slice1)`
    
    `fmt.Println("slice from existing slice", slice2)`
    
    `slice1[0] = 178`
    
    `fmt.Println("array after modifying slice", arrayval)`
    
    `fmt.Println("slice from array after modifying slice:", slice1)`
    
    `fmt.Println("slice from existing slice after modifying slice", slice2)`
    
    `}`
    
    **Output:**
    
    `original array [1 2 3 4 5 6 7 8 9 10]`
    
    `slice from array: [2 3 4 5 6 7 8]`
    
    `slice from existing slice [2 3 4 5 6 7]`
    
    `array after modifying slice [1 178 3 4 5 6 7 8 9 10]`
    
    `slice from array after modifying slice: [178 3 4 5 6 7 8]`
    
    `slice from existing slice after modifying slice [178 3 4 5 6 7]`
    
*   **Length**
    
    **Length** is the number of elements referred by the slice. As arrays, we use the len function to get the length of a slice. It returns the total number of elements that a slice contains.
    
    **Example:**
    
    `func main() {`
    
    `var arrayval [10] int = [10] int {1, 2, 3, 4, 5, 6, 7, 8, 9, 10}`
    
    `slice1 := arrayval[1:8]`
    
    `fmt.Println("length of slice", len(slice1)) //length of slice 7`
    
    `}`
    
*   **Capacity**
    
    For the same slice, its length and capacity could be the same or different. Length is coupled with a slice, while capacity is linked with an array. The **capacity** of a slice is the number of elements in the underlying array from the first element of the slice. This means the capacity of a slice refers to the size up to which a slice can be extended.
    
    In the example given below, the slice contains elements from index 2 to 4 (3 elements). So the length of the slice is 3. Slice can be extended to the maximum index of an array which is 9 here. So the capacity of a slice is the number of the element from index 2 to 9; which is 8 here.
    
    A slice cannot be extended beyond its capacity. Also, a slice cannot be re-sliced below zero.
    
    **Example:**
    
    `func main() {`
    
    `var arrayval [10] int = [10] int {1, 2, 3, 4, 5, 6, 7, 8, 9, 10}`
    
    `slice1 := arrayval[2:5]`
    
    `fmt.Println("length of slice", len(slice1)) // length of slice 3`
    
    `fmt.Println("capacity of slice", cap(slice1)) // capacity of slice 8`
    
    `}`
    

# [Slice using the make function](#toc.xhtml#s96a)

Go provides a built-in function make that is used to create empty slices. Empty slice refers to an empty array. To create such slices, it is necessary to define its size at the time of the slice declaration. To create an empty slice of non-zero length, we declare slices in the following way:

`name_of_slice := make([], type_of_slice, length_of_slice, capacity_of_slice)`

The `make` function creates an array of a specified type and assigns its reference to a slice. Here, the capacity of the slice is optional. By default, the size of a slice to be considered is it's capacity.

`s := make([] int, 5, 10)`

This creates an integer type array of size 10 and assigns a reference to slice s till 5th index.

**Example:**

`func main() {`

`slice1 := make([] int, 2,4)`

`fmt.Println("length of slice", len(slice1)) // length of slice 2`

`fmt.Println("capacity of slice", cap(slice1)) // capacity of slice 4`

`fmt.Println("value of slice", slice1) // value of slice [0 0]`

`slice1[0] = 194`

`slice1[1] = 18`

`fmt.Println("value of slice", slice1) // value of slice [194 18]`

`slice1[2] = 78 // error as length of slice is 2`

`}`

In the above example of assigning the value at the 2nd index, it exits because we have defined its length as 2. After that, we can extend the slice till the 3rd index by appending more elements as its capacity is 4.

*   **Extending slices**
    
    In the Go language, we can extend the capacity of slices. There is a simple process to increase the capacity of a slice. To increase it, create a new slice (that must be larger than the old slice) and copy the content of the slice to a new one. Now, the capacity of the new slice will be greater than the old one. Then, assign this new slice to the old one.
    
    **Example:**
    
    `func main() {`
    
    `slice1 := []int {12, 65, 34, 78, 23, 67}`
    
    `fmt.Println("capacity of slice1:", cap(slice1))`
    
    `slice2 := make([]int, len(slice1), (cap(slice1)+1)*2)`
    
    `for i:= range slice1{`
    
    `slice2[i] = slice1[i]`
    
    `}`
    
    `slice1 = slice2`
    
    `fmt.Println("capacity of slice1:", cap(slice1))`
    
    `}`
    
    **Output:**
    
    `capacity of slice1: 6`
    
    `capacity of slice1: 14`
    

# [Two-dimensional slices](#toc.xhtml#s97a)

Like arrays, we can also create 2D slices. 2D slices can be defined as slices of a slice. We can declare 2D slices in the same way that we do in arrays, without defining their size.

`slice1 := [][] int{`

`[] int {1, 2},`

`[] int {3, 4},`

`[] int {5, 6},`

`}`

While declaring 2D slices using the make function, we define the number of rows as the length of the slice. In 2D slices, the length of the inner slice can vary as required. For uninitialized rows or elements, it takes default values. Here is an example that explains 2D slices.

**Example:**

`func main() {`

`slice1 := [][] int{`

`[] int {1, 2, 78, 54},`

`[] int {0, 3, 4},`

`[] int {5, 6},`

`}`

`fmt.Println("slice1", slice1) // slice1 [[1 2 78 54] [0 3 4] [5 6]]`

`slice2 := make([][]string, 4)`

`slice2[0] = []string{"College", "School"}`

`slice2[1] = []string{"University", "Institute"}`

`fmt.Println("slice2 using make function:", slice2) // slice2 using make function: [[College School] [University Institute] [] []]`

`}`

# [Slice functions](#toc.xhtml#s98a)

After creating slices, it’s time to use slices variously. Slices are richer than arrays as we can perform multiple types of operations with slices. Here are some functions:

*   **Copying a slice using copy function**
    
    `copy()` functions copy the elements from one slice to another one. The copy function follows the following signature:
    
    `func copy(destination, source [] T) int`
    
    This function takes two arguments, the source slice that we want to copy, and the destination slice to which we want to copy the elements. It always returns an integer type of value that is the total number of copied elements. The return value is always the minimum of the length of the source slice and destination slice.
    
    **Example:**
    
    `func main() {`
    
    `slice1 := [] int{23, 56, 47, 58}`
    
    `slice2 := [] int{90, 107, 0, 67, 28, 89}`
    
    `// if(len(des_slice)>len(src_slice))`
    
    `fmt.Println("destination slice if it's length is greater than source slice>>>>>>>>>>>>>")`
    
    `fmt.Println("destination slice before copying elements:", slice2)`
    
    `n := copy(slice2, slice1)`
    
    `fmt.Println("destination slice after copying elements:", slice2)`
    
    `fmt.Println("length of destination slice after copying elements:", len(slice2))`
    
    `fmt.Println("Numnber of copied elements after copying elements:", n)`
    
    `// if(len(des_slice) = len(src_slice))`
    
    `slice3 := [] int{34, 20, 1, 91}`
    
    `fmt.Println("destination slice if it's length is equal to source slice>>>>>>>>>>>>>")`
    
    `fmt.Println("destination slice before copying elements:", slice3)`
    
    `n = copy(slice3, slice1)`
    
    `fmt.Println("destination slice after copying elements:", slice3)`
    
    `fmt.Println("length of destination slice after copying elements:", len(slice3))`
    
    `fmt.Println("Numnber of copied elements after copying elements:", n)`
    
    `// if(len(des_slice)<len(src_slice))`
    
    `slice4 := [] int{34, 20}`
    
    `fmt.Println("destination slice if it's length is less than source slice>>>>>>>>>>>>>")`
    
    `fmt.Println("destination slice before copying elements:", slice4)`
    
    `n = copy(slice4, slice1)`
    
    `fmt.Println("destination slice after copying elements:", slice4)`
    
    `fmt.Println("length of destination slice after copying elements:", len(slice4))`
    
    `fmt.Println("Numnber of copied elements after copying elements:", n)`
    
    `// copying in nil slice`
    
    `slice5 := []int{}`
    
    `fmt.Println("On copying elements to nil slice >>>>>>>>>>>>>")`
    
    `fmt.Println("destination slice before copying elements:", slice5)`
    
    `n = copy(slice5, slice1)`
    
    `fmt.Println("destination slice after copying elements:", slice5)`
    
    `fmt.Println("length of destination slice after copying elements:", len(slice5))`
    
    `fmt.Println("Numnber of copied elements after copying elements:", n)`
    
    `}`
    
    **Output:**
    
    `destination slice if it's length is greater than source slice>>>>>>>>>>>>>`
    
    `destination slice before copying elements: [90 107 0 67 28 89]`
    
    `destination slice after copying elements: [23 56 47 58 28 89]`
    
    `length of destination slice after copying elements: 6`
    
    `Numnber of copied elements after copying elements: 4`
    
    `destination slice if it's length is equal to source slice>>>>>>>>>>>>>`
    
    `destination slice before copying elements: [34 20 1 91]`
    
    `destination slice after copying elements: [23 56 47 58]`
    
    `length of destination slice after copying elements: 4`
    
    `Numnber of copied elements after copying elements: 4`
    
    `destination slice if it's length is less than source slice>>>>>>>>>>>>>`
    
    `destination slice before copying elements: [34 20]`
    
    `destination slice after copying elements: [23 56]`
    
    `length of destination slice after copying elements: 2`
    
    `Numnber of copied elements after copying elements: 2`
    
    `On copying elements to nil slice >>>>>>>>>>>>>`
    
    `destination slice before copying elements: []`
    
    `destination slice after copying elements: []`
    
    `length of destination slice after copying elements: 0`
    
    `Numnber of copied elements after copying elements: 0`
    
    It is clear from this example that the copy function doesn’t add any new value to the destination slice. It is just modifying an element at a particular index if that index is in both the slices.
    
*   **Sort a slice**
    
    In Golang, we have a package sort that provides multiple sorting methods to sort the slice of type `int, float64`, or `string`. These sorting methods always sort a slice in the ascending order.
    
    **Example:**
    
    `package main`
    
    `import (`
    
    `"fmt"`
    
    `"sort"`
    
    `)`
    
    `func main() {`
    
    `slice1 := [] int{23, 0, 105, 58}`
    
    `slice2 := [] string{"Ram", "Akansha", "Mayank"}`
    
    `slice3 := [] float64{75.84, 0.007, 85.62, 0.74637}`
    
    `fmt.Println("slice1 before sorting:", slice1)`
    
    `sort.Ints(slice1)`
    
    `fmt.Println("slice1 after sorting:", slice1)`
    
    `fmt.Println("slice1 before sorting:", slice2)`
    
    `sort.Strings(slice2)`
    
    `fmt.Println("slice1 after sorting:", slice2)`
    
    `fmt.Println("slice1 before sorting:", slice3)`
    
    `sort.Float64s(slice3)`
    
    `fmt.Println("slice1 after sorting:", slice3)`
    
    `}`
    
    **Output:**
    
    `slice1 before sorting: [23 0 105 58]`
    
    `slice1 after sorting: [0 23 58 105]`
    
    `slice1 before sorting: [Ram Akansha Mayank]`
    
    `slice1 after sorting: [Akansha Mayank Ram]`
    
    `slice1 before sorting: [75.84 0.007 85.62 0.74637]`
    
    `slice1 after sorting: [0.007 0.74637 75.84 85.62]`
    
*   **Compare slices**
    
    Two slices are said to be equal if they are both of the same type and contain the same elements. Golang provides a function `DeepEqual` to compare the slices, whether they are equal or not. We can access this function by using the `reflect` package.
    
    **Example:**
    
    `package main`
    
    `import ("fmt"`
    
    `"reflect"`
    
    `)`
    
    `func main() {`
    
    `slice1 := [] int{23, 0, 105, 0}`
    
    `slice2 := [] string{"Ram", "Akansha", "Mayank"}`
    
    `slice3 := [] float64{23, 0, 105, 0}`
    
    `slice4 := make([]int, 4)`
    
    `slice4[0] = 23`
    
    `slice4[1] = 0`
    
    `slice4[2] = 105`
    
    `fmt.Println("Is slice1 equal to slice2:", reflect. DeepEqual(slice1, slice2))`
    
    `fmt.Println("Is slice1 equal to slice3:", reflect.DeepEqual(slice1, slice3))`
    
    `fmt.Println("Is slice1 equal to slice4:", reflect. DeepEqual(slice1, slice4))`
    
    `}`
    
    **Output:**
    
    `Is slice1 equal to slice2: false`
    
    `Is slice1 equal to slice3: false`
    
    `Is slice1 equal to slice4: true`
    
*   **Searching in slice**
    
    In Golang, we can search whether a specific element exists in a slice or not. Go provides a search function that finds an element and returns its position in a particular integer, float, or string slice. The search function works well with a sorted slice in the ascending order. If the element is not found in a particular slice, then it returns an index value at which that specific element fits in a slice.
    
    **Example:**
    
    `package main`
    
    `import ("fmt"`
    
    `"sort"`
    
    `)`
    
    `func main() {`
    
    `slice1 := [] int{0, 9,16,105, 345}`
    
    `slice2 := [] string{"Akansha", "Mayank", "Ram"}`
    
    `slice3 := [] float64{0, 0.001, 5.7}`
    
    `fmt.Println(sort.SearchInts(slice1, 105)) // 3`
    
    `fmt.Println(sort.SearchInts(slice1, 78)) // 3`
    
    `fmt.Println(sort.SearchInts(slice1, 0.0)) // 0`
    
    `fmt.Println(sort.SearchStrings(slice2, "Ram")) // 2`
    
    `fmt.Println(sort.SearchStrings(slice2, "ram")) // 3`
    
    `fmt.Println(sort.SearchFloat64s(slice3, 0.000)) // 0`
    
    `fmt.Println(sort.SearchFloat64s(slice3,5.7)) // 2`
    
    `}`
    
*   **Reverse slice**
    
    The reverse function returns a slice in the reverse/descending order. It works well with sorted or unsorted slices.
    
    **Example:**
    
    `package main`
    
    `import ("fmt"`
    
    `"sort"`
    
    `)`
    
    `func main() {`
    
    `slice1 := [] int{0, 888, 9,16,105, 345}`
    
    `slice2 := [] string{"Soni", "Akansha", "Charu", "Mayank", "Ram"}`
    
    `sort.Sort(sort.Reverse(sort.IntSlice(slice1)))`
    
    `fmt.Println("reverse of slice1:", slice1)`
    
    `sort.Sort(sort.Reverse(sort.StringSlice(slice2)))`
    
    `fmt.Println("reverse of slice2:", slice2)`
    
    `}`
    
    **Output:**
    
    `reverse of slice1: [888 345 105 16 9 0]`
    
    `reverse of slice2: [Soni Ram Mayank Charu Akansha]`
    
*   **Appending slice element**
    
    The **append function** adds a new element at the end of the slice. We can append multiple numbers at the end of the slice. If a slice has less capacity than the number of items that we are appending, then a new slice is allocated of a large capacity and all the elements are copied and appended into the new slice.
    
    **Example:**
    
    `func main() {`
    
    `slice1 := [] int{0, 888, 9, 16, 105, 345}`
    
    `slice1 = append(slice1, 345, 646, 0)`
    
    `fmt.Println("slice1 after appending few elements:", slice1)`
    
    `slice3 := make([]int, 2)`
    
    `slice3 = append(slice3, 56, 67, 48, 90, 46, 26, 57)`
    
    `fmt.Println("slice3 after appanding elements more than it's capacity:", slice3)`
    
    `slice4 := []int{}`
    
    `slice4 = append(slice4, 45, 67)`
    
    `fmt.Println("slice4 after appanding elements in nil slice:", slice4)`
    
    `}`
    
    **Output:**
    
    `slice1 after appending few elements: [0 888 9 16 105 345 345 646 0]`
    
    `slice3 after appending elements more than it's capacity: [0 0 56 67 48 90 46 26 57]`
    
    `slice4 after appending elements in nil slice: [45 67]`
    
    We can append a slice into a slice of the same type using … operator. This operator helps in increasing the capacity of a slice up to the length of the appended slice.
    
    **Example:**
    
    `func main() {`
    
    `slice1 := [] int{0, 888, 9, 16, 105, 345}`
    
    `slice2 := []int{78, 34, 9, 57}`
    
    `slice1 = append(slice1, slice2…)`
    
    `fmt.Println("slice1 after appending slice2", slice1)`
    
    `}`
    
    **Output:**
    
    `slice1 after appending slice2 [0 888 9 16 105 345 78 34 9 57]`
    

# [Conclusion](#toc.xhtml#s99a)

In this chapter, we learned the declaration and initialization of arrays in Go. We learned about various functions such as length, comparison, copy, and iteration with arrays. Here, we understood the need for an array and thus slices. We saw the use of some functions that are used to get a slice from an array, slice, or structs. We also saw that some in-built functions are used to analyze an array. To get a continuous understanding of data types in Go, we’ll discuss another data type called "strings" in the next chapter.

# [Questions](#toc.xhtml#s100a)

1.  How can we declare an array in Go?
2.  How can we initialize multidimensional arrays in Go?
3.  What is the need of a slice over an array?
4.  How can we add elements in a slice?
5.  How can we pass an array in a function?
6.  How can we get a slice from an array for some specific contiguous value?
7.  How can we compare two slices in Go?

# [CHAPTER 10](#toc.xhtml#c10)

# [Strings](#toc.xhtml#c10)

In this chapter, we are going to discuss another non-primitive data type string that is used to represent a text (set of characters, special characters, numbers, etc.). It illustrates the various operations that we can perform on a string in Go language.

# [Structure](#toc.xhtml#s101a)

In this chapter, we will discuss the following topics:

*   Introduction to strings 
    *   Functions with strings
*   The rune data type 
    *   Iterate over strings
*   Multiline strings 
    *   Rune to string conversion
    *   Byte slice to string conversion
    *   Immutable nature
*   Strings package
*   Functions with strings package

# [Objectives](#toc.xhtml#s102a)

After studying this chapter, you’ll be able to:

*   Understand how string works in Go programs
*   Use various in-built functions directly in your program that save time and reduce complexity.
*   Understand the immutable behavior of strings.
*   Get a string from another data type and it use as needed.
*   Gain knowledge of the strings library that Golang provides

# [Introduction](#toc.xhtml#s103a)

The **string** is one of the important categories of Golang data types. In Go, strings are quite different as compared to other languages. In other programming languages, the string is defined as an array of characters but here, ***string is a slice of bytes***. In JavaScript, Python, or any other language, we can define strings within single quote, but Golang doesn’t allow multiple characters or strings to be defined within single quotes. We can define a character with single quotes (‘…’) but strings are always defined with double quotes (“…”).

By default, strings are UTF-8 encoded in Go language. This is a key factor of Go’s string data type. UTF-8 is supported by many languages, so it facilitates easy interaction with other languages. While creating web pages, we need to display Unicode content; here, strings work well with the Go language. UTF-8 takes 8 bits block to represent a character. The number of blocks can vary from 1 to 4. Unicode character set maps each character to a unique number called code points. It is capable of encoding 1,112,064 code points.

Here is a basic example to explain the declaration and initialization of strings.

**Example:**

`func main() {`

`var str string`

`fmt.Printf("By default strings are:%q\n", str)`

`str = "Hello Go"`

`fmt.Println("After assigning a value string is:", str)`

`str_new := "Hello world"`

`fmt.Printf("After shorthand declaration, double quoted value of str_new is:%q\n", str_new)`

`fmt.Printf("Uninterpreted bytes of str_new is:%s\n", str_new)`

`fmt.Printf("base16 notation of str=%x", str)`

`}`

**Output:**

`By default strings are:""`

`After assigning a value string is: Hello Go`

`After shorthand declaration, double quoted value of str_new is:"Hello world"`

`Uninterpreted bytes of str_new is:Hello world`

`base16 notation of str=48656c6c6f20476f`

The above example tells us that by default, strings are empty.

# [Functions with strings](#toc.xhtml#s104a)

Here are some functions that work with strings in Go.

*   **Length of string**
    
    Golang provides the len function to find the length of the string or the number of characters that a string contains. This function encodes the string and then returns the total number of bytes taken by each character.
    
    **Example:**
    
    `func main() {`
    
    `var str string`
    
    `str = "Hello Go"`
    
    `fmt.Println("Length of string 'str' is:", len(str))`
    
    `str_new := "世Hello Go世"`
    
    `fmt.Printf("Length of string 'str_new' is:", len(str_new))`
    
    `}`
    
    **Output:**
    
    `length of string 'str' is: 8`
    
    `length of string 'str_new' is:%!(EXTRA int=14)`
    
    In the example given above, the length of str simply counts the number of characters and return the length as 8. In `str_new`, the length is 14. In this string, character 世 is encoded with 3 bytes in UTF-8. So, the length is 14.
    
*   **Iterate through a string**
    
    As the string is a slice of bytes, we can access each byte/character individually. We can get an individual as a character or their Unicode UTF-8 encoded value.
    
    While iterating, it covers each byte, not character.
    
    **Example:**
    
    `func main() {`
    
    `var str string`
    
    `str = "Hello Go"`
    
    `fmt.Println("characters of str")`
    
    `for itr:=0; itr<len(str); itr++{`
    
    `fmt.Printf("%c ", str[itr])`
    
    `}`
    
    `fmt.Println("\nUTF-8 encoded values of str")`
    
    `for itr:=0; itr<len(str); itr++{`
    
    `fmt.Printf("%x ", str[itr])`
    
    `}`
    
    `str_new := "世Hello Go世"`
    
    `fmt.Println("\ncharacters of str_new")`
    
    `for itr:=0; itr<len(str_new); itr++{`
    
    `fmt.Printf("%c ", str_new[itr])`
    
    `}`
    
    `fmt.Println("\nUTF-8 encoded values of str_new")`
    
    `for itr:=0; itr<len(str_new); itr++{`
    
    `fmt.Printf("%x ", str_new[itr])`
    
    `}`
    
    `}`
    
    **Output:**
    
    `characters of str`
    
    `H e l l o     G o`
    
    `UTF-8 encoded values of str`
    
    `48 65 6c 6c 6f 20 47 6f`
    
    `characters of str_new`
    
    `ä ¸ – H e l l o G o ä ¸ –`
    
    `UTF-8 encoded values of str_new`
    
    `e4 b8 96 48 65 6c 6c 6f 20 47 6f e4 b8 96`
    
    In the example given above, everything works fine but on getting the character of string `str_new`, it prints the character incorrectly. When the character 世 is encoded, it takes 3 bytes. Let’s break down the output where we get UTF-8 encoded values of this string.
    
    ![](images/10-a.jpg)

Here, we can clearly see that 世 occupies three bytes, e4, b8 and 96. On printing the characters, we are assuming that it occupies only one byte. Here, things can go wrong. To overcome such problems, Golang provides a ‘rune’ data type.

# [The rune data type](#toc.xhtml#s105a)

Rune is a built-in data type in the Go language. It is an alias of int32 as we have seen that Unicode UTF-8 encodes the character to a unique number or code point. The `rune` represents these Unicode code points in Go. It is not bound with the number of bytes that a character occupies.

In the previous example, we were iterating through the string that iterates each byte as the string is a slice of bytes, but it leads to an unexpected result. To avoid this, we’ll iterate through the slice of runes by converting a slice into runes.

**Example:**

`func main() {`

`str_new := "世Hello Go世"`

`rune_slice := []rune(str_new)`

`fmt.Println("\ncharacters of str_new")`

`for itr:=0; itr<len(rune_slice); itr++{`

`fmt.Printf("%c ", rune_slice[itr])`

`}`

`fmt.Println("\nUTF-8 encoded values of str_new")`

`for itr:=0; itr<len(str_new); itr++{`

`fmt.Printf("%x ", str_new[itr])`

`}`

`}`

**Output:**

`characters of str_new`

`世 H e l l o     G o 世`

`UTF-8 encoded values of str_new`

`e4 b8 96 48 65 6c 6c 6f 20 47 6f e4 b8 96`

# [Iterate using range keyword](#toc.xhtml#s106a)

Instead of using for loop or runes, we can use the range keyword to iterate over the items of slice or array. It returns an index as integer and the item on that index. For loop covers each byte whereas range covers each index separately. So, the problem we had with for loop never occurs with range keyword.

`for index, item: = range name_of_string{`

`//body`

`}`

On writing one variable on the left side, it only returns the index and not the item at that index. If we only need the item and not the index, we can use \_ at the place of the index variable.

**Example:**

`func main() {`

`str_new := "世Hello Go世"`

`fmt.Println("\nCharacters of str_new")`

`for _, item := range str_new{`

`fmt.Printf("%c ", item)`

`}`

`}`

**Output:**

`Characters of str_new`

`世 H e l l o     G o 世`

# Multiline string

There is another way to define strings which is by using backtick (”). With double quotes, we need to define newline character (\\n) for a new line but with backticks, we can simply give a line break as needed. On putting line break with backtick string, it is considered as a \\n character. There is no need to specify escape characters with backtick as it interprets them as a normal character and prints with the strings.

**Example:**

`str := "Hello`

`Go"`

`fmt.Printf("string with double quotes:%s\n", str) // error`

**Example:**

`func main() {`

`str := "Hello\n Go"`

`fmt.Printf("String with double quotes:%s\n", str)`

`str_new := ‘Hello\n Go’`

`fmt.Printf("String with backtick:%s\n", str_new) //treats \n as normal character`

`str_new = ‘Hello`

`Go’`

`fmt.Printf("Linebreak in string with backtick:%s\n", str_new)`

`}`

**Output:**

`String with double quotes:Hello`

`Go`

`String with backtick: Hello\n Go`

`Linebreak in string with backtick: Hello`

`Go`

# [Convert a slice of runes to string](#toc.xhtml#s107a)

We have already understood how to convert string to rune. In Go, we can also convert the slice of runes to a string. In the example given below, the rune contains a few code points that we are converting to string.

**Example:**

`func main() {`

`rune := [] rune{0x4e16, 0x0048, 0x0065, 0x006c, 0x006c, 0x006f, 0x0047, 0x006f, 0x4e16}`

`str := string(rune)`

`fmt.Println("string from slice of rune:", str)`

`}`

**Output:**

`string from slice of rune: 世HelloGo世`

# [Convert a slice of bytes to string](#toc.xhtml#s108a)

We can convert a slice of byte to string like we converted slice of the rune.

Here is an example:

`func main() {`

`rune := [] byte{228, 184, 150, 72, 101, 108, 108, 111, 71, 111, 228, 184, 150}`

`str := string(rune)`

`fmt.Println("String from a slice of bytes:", str)`

`}`

**Output:**

`String from a slice of bytes:世HelloGo世`

# [Immutable nature of the string](#toc.xhtml#s109a)

In the Go language, we cannot change the value of string once it is defined. That’s why they are called immutable strings. We can say that string is a read-only slice of bytes. We can access any character of a string but on changing its value or extending its length, the compiler throws an error.

**Example:**

`func main() {`

`str := "Hello Go"`

`fmt.Printf("%c", str[3]) // l`

`str[3] = 'y' // cannot assign to str[3]`

`}`

There are certain cases where we need to change the value of the strings. Here, rune helps. We can convert the string to rune type, change the value as required, and then assign the rune to string. Here is a short example:

**Example:**

`func main() {`

`str := "Hello Go"`

`fmt.Printf("Character at third index: %c\n", str[3])`

`rune := []rune(str)`

`rune[3] = 'M'`

`str = string(rune)`

`fmt.Printf("Character at third index after changing its value: %c", str[3])`

`}`

**Output:**

`character at third index: l`

`character at third index after changing its value: M`

The the above example, we saw that the rune represents a character as a Unicode code point (int-32). Thus, each character can be defined as a decimal value and so, it can be compared. We can also perform a few other operations with the help of a character’s code point.

**Example:**

`func main() {`

`if('a'>'A'){`

`fmt. Println("a is greater tha A")`

`}`

`fmt. Println("a is greater than z:", 'a'>'z')`

`for itr:='a'; itr<'m'; itr++{`

`fmt.Print(itr)`

`fmt.Printf(" "+string(itr)+"\n")`

`}`

`}`

**Output:**

`a is greater tha A`

`a is greater than z: false`

`97 a`

`98 b`

`99 c`

`100 d`

`101 e`

`102 f`

`103 g`

`104 h`

`105 i`

`106 j`

`107 k`

`108 l`

# [Strings package](#toc.xhtml#s110a)

In Golang, we have standard library strings that provide multiple functions to work with UTF-8 encoded strings. The strings package is in Go’s src directory that has multiple Go files. The package facilitates several functions to modify and manipulate the strings.

To use a package in a program, we need to import it first. After importing the package, we can access its exported functions with the dot operator. The section given below describes most of the functions that are provided in the strings package. To avoid accessing the `Println` method again and again, we are assigning it a variable `fp` and using this variable in the program.

# [Functions with strings package](#toc.xhtml#s111a)

Here are some functions available in the strings package in Go.

*   **Converting string in uppercase and lowercase**
    
    The `ToUpper` function converts each character of a string into uppercase, whereas the `ToLower` function is used to convert each character of a string into lowercase. With both the functions, the conversion is done with each character, whether it is in lowercase or uppercase. If any character is in uppercase and the `ToUpper` function is applied, it remains in uppercase and vice versa.
    
    **Example:**
    
    `package main`
    
    `import ("fmt"`
    
    `"strings"`
    
    `)`
    
    `func main() {`
    
    `fp := fmt.Println`
    
    `str := "Hello Go"`
    
    `fp("string in uppercase:", strings.ToUpper(str)) // string in uppercase: HELLO GO`
    
    `fp("string in lowercase:", strings.ToLower(str)) // string in lowercase: hello go`
    
    `}`
    
*   **Search for string prefix/suffix**
    
    The `strings` package provides a function called `HasPrefix` that checks whether a string starts with a specified string or not. Similarly, the function `HasSuffix` checks if a string ends with a specified string. Two arguments are passed while calling these functions. The first is the string on which we are checking the prefix/suffix and the second is the string that we are searching for.
    
    **Example:**
    
    `func main() {`
    
    `fp := fmt.Println`
    
    `str := "Hello Go"`
    
    `fp("has prefix He", strings.HasPrefix(str, "He")) // has prefix He true`
    
    `fp("has prefix he", strings.HasPrefix(str, "he")) // has prefix he false`
    
    `fp("has suffix go", strings.HasSuffix(str, "go")) // has suffix go false`
    
    `fp("has suffix Go", strings.HasSuffix(str, "Go")) // has suffix Go true`
    
    `}`
    
*   **Search for specific text**
    
    We have a function called `Contains` that checks if a string exists in another string or not. On the other hand, we have the `ContainsAny` functions which returns true if any character of a string exists in another string,
    
    **Example:**
    
    `func main() {`
    
    `fp := fmt.Println`
    
    `str := "Hello Go"`
    
    `fp("contains ellO", strings.Contains(str, "ellO")) // contains ellO false`
    
    `fp("contains o G:", strings.Contains(str, "o G")) // contains o G: true`
    
    `fp("containsany welcome:", strings.ContainsAny(str, "welcome")) // containsany welcome: true`
    
    `fp("containsany shubh:", strings.ContainsAny(str, "shubh")) // containsany shubh: false`
    
    `}`
    
*   **Number of occurrences in a string**
    
    We have a function to check if a specific string exists in another string or not. The count function tells the number of times a specific string appears within another string. It returns zero if the specified string doesn’t exist in another string.
    
    **Example:**
    
    `func main() {`
    
    `fp := fmt.Println`
    
    `str := "Grow And Grow With Golang"`
    
    `fp("occurences of Gr:", strings.Count(str, "Gr")) // occurences of Gr: 2`
    
    `fp("occurences of welcome:", strings.Count(str, "welcome")) // occurences of welcome: 0`
    
    `}`
    
*   **Find the position of a string**
    
    In the strings package, the Index function is used to get an index of the specified string in another string at the first occurrence. It returns - 1 if the specified string doesn’t exist in another string.
    
    **Example:**
    
    `func main() {`
    
    `fp := fmt.Println`
    
    `str := "Grow And Grow With Golang"`
    
    `fp("position of Gr:", strings.Index(str, "Gr")) // position of Gr: 0`
    
    `fp("position of welcome:", strings.Index(str, "welcome")) // position of welcome: -1`
    
    `}`
    
*   **Find the position of any Unicode codepoint**
    
    The `IndexAny` function searches for Unicode codepoints (character) of the specified string in another string and returns the first index of the first appearing Unicode codepoint. It returns -1 if no Unicode code points appear in another string.
    
    **Example:**
    
    `func main() {`
    
    `fp := fmt.Println`
    
    `str := "Grow And Grow With Golang"`
    
    `fp("position of first appearing Unicode codepoint in Ground:", strings.IndexAny(str, "Ground")) // position of first appearing Unicode codepoint in Ground: 0`
    
    `fp("position of first appearing Unicode codepoint in sub:", strings.IndexAny(str, "sub")) // position of first appearing Unicode codepoint in sub: -1`
    
    `}`
    
*   **Find the position of a string from last**
    
    As the Index function checks for the first occurrence, the `LastIndex` function checks for the last occurrence of a string in another string.
    
    **Example:**
    
    `func main() {`
    
    `fp := fmt.Println`
    
    `str := "Grow And Grow With Golang"`
    
    `fp("last position of Gr:", strings.LastIndex(str, "Gr")) // last position of Gr: 9`
    
    `fp("last position of welcome:", strings.LastIndex(str, "welcome")) // last position of welcome: -1`
    
    `}`
    
*   **Find the position of any Unicode codepoint from last**
    
    The function `LastIndexAny` works the same as `IndexAny`. The difference is that `IndexAny` returns the first occurrence, whereas `LastIndexAny` returns the last occurrence of the Unicode code point if it exists in another string. This function finds a codepoint that appears last in another string and then returns the index of its last occurrence. It returns -1 if no Unicode codepoint exists in another string.
    
    **Example:**
    
    `func main() {`
    
    `fp := fmt.Println`
    
    `str := “Grow And Grow With Golang”`
    
    `fp(“position of last appearing Unicode codepoint in Ground:”, strings.LastIndexAny(str, “Ground”)) // position of last appearing Unicode codepoint in Ground: 23`
    
    `fp(“position of last appearing Unicode codepoint in sub:”,`
    
    `strings.LastIndexAny(str, “sub”)) // position of last appearing Unicode codepoint in sub: -1`
    
    `}`
    
*   **Convert array to string**
    
    In the `strings` package, we have a function called `Join` that concatenates all the elements of the array (string type) with the specified separator and creates a single string.
    
    **Example:**
    
    `func main() {`
    
    `fp := fmt.Println`
    
    `str := [] string {"my", "name", "is", "rahul"}`
    
    `fp(strings.Join(str, "-")) // my-name-is-rahul`
    
    `}`
    
*   **Replacing specified string from the given string**
    
    The `strings` package provides a `Replace` function that returns the copy of the string by replacing a given string with another string. `Replace` function takes four values: the main string on which we are performing this action, the old string that we need to replace, the new string that we need to replace with, and an integer number that tells the number of occurrences of that old string that we need to replace. If an integer value is zero or an old string doesn’t exist in a string, then no replace action is performed. If an integer value is greater than the number of occurrences, it replaces all the occurrences of an old string with a new one.
    
    We have another function called `ReplaceAll` that works the same as the `Replace` function. The difference between them is that `Replace` works on a given number of occurrences while `ReplaceAll` replaces all the occurrences of an old string with a new one.
    
    **Example:**
    
    `func main() {`
    
    `fp := fmt.Println`
    
    `str := "my-name-is-rahul"`
    
    `fp(strings.Replace(str, "-", " ", 0)) // my-name-is-rahul`
    
    `fp(strings.Replace(str, "-", " ", 1)) // my name-is-rahul`
    
    `fp(strings.Replace(str, "-", " ", 9)) // my name is rahul`
    
    `fp(strings.Replace(str, "welcome", " ", 9)) // my-name-is-rahul`
    
    `fp(strings.ReplaceAll(str, "-", " ")) // my name is rahul`
    
    `}`
    
*   **Convert string to array by splitting strings**
    
    The `split` function returns an array of substrings from a string, split by a given separator. If a separator doesn’t exist in a string, then it simply converts a string into an array.
    
    We have another function called `Fields` that splits a string by the whitespace or newline characters and returns an array.
    
    **Example:**
    
    `func main() {`
    
    `fp := fmt.Println`
    
    `str := "my-name-is-rahul"`
    
    `fp(strings.Split(str, "-")) // [my name is rahul]`
    
    `fp(strings.Split(str, "welcome")) // [my-name-is-rahul]`
    
    `fp(strings.Split(str, "")) // [m y - n a m e - i s - r a h u l]`
    
    `fp(strings.Fields("welcome \t in the world of \n Go")) // [welcome in the world of Go]`
    
    `}`
    
*   **Removing specific Unicode code points**
    
    We have a function called `Trim` that removes all the leading and trailing Unicode code points contained in a specific given string from another string. We have many other functions that give support to trim the specific Unicode point as needed. Here is an example that demostrtate this well:
    
    **Example:**
    
    `func main() {`
    
    `fp := fmt.Println`
    
    `str := "-my-name-is-rahul-"`
    
    `fp(strings.Trim(str, "-")) // my-name-is-rahul`
    
    `fp(strings.TrimLeft(str, "-")) // my-name-is-rahul-`
    
    `fp(strings.TrimRight(str, "-")) // -my-name-is-rahul`
    
    `fp(strings.TrimFunc(str, func(c rune) bool {`
    
    `return c >= 23 && c <= 50`
    
    `})) // my-name-is-rahul`
    
    `fp(strings.TrimLeftFunc(str, func(c rune) bool {`
    
    `return c >= 23 && c <= 50`
    
    `})) // my-name-is-rahul-`
    
    `fp(strings.TrimRightFunc(str, func(c rune) bool {`
    
    `return c >= 23 && c <= 50`
    
    `})) // -my-name-is-rahul`
    
    `fp(strings.TrimPrefix(str, "-my-")) // name-is-rahul-`
    
    `fp(strings.TrimSuffix(str, "-rahul-")) // -my-name-is`
    
    `fp(strings.TrimSuffix(str, "welcome")) // -my-name-is-rahul- (Unchanged)`
    
    `str = " -my-name-is-rahul- "`
    
    `fp(strings.TrimSpace(str)) // -my-name-is-rahul-`
    
    `}`
    

# [Conclusion](#toc.xhtml#s112a)

In this chapter, we saw how a string works as a code point in Go. Golang provides various functions to analyze and modify the strings. We have seen multiple ways to get a string from other data types. The concept of rune data type is new in Golang. Golang provides a rich set of libraries and strings package is one of them that facilitates multiple functions for the string. In the next chapter, we’ll discuss another data type called pointer in depth.

# [Questions](#toc.xhtml#s113a)

1.  How is a string declaration different in Go from other languages?
2.  What is a rune in Go?
3.  How can we get a string from rune?
4.  Which function is used to find the index of the string in another one?
5.  How can we access the exported function of the strings package in Go?
6.  How are strings immutable in Go?

# [CHAPTER 11](#toc.xhtml#c11)

# [Pointers](#toc.xhtml#c11)

In this chapter, will discuss the data type **pointers** that play an important role in running the program faster with less memory. **Pointer** allows data sharing and makes a difference between the default (null or zero) and undefined value of a variable. Let's have a look at and understand the concept of pointers in Go.

# [Structure](#toc.xhtml#s114a)

In this chapter, we will discuss the following topics:

*   Introduction to pointers
*   Need for pointers
*   Declare pointers
*   Initializing pointers
*   Dereferencing pointers
*   Manipulating pointers
*   Creating pointers with new
*   Nested pointers
*   Array of pointers
*   Passing pointers to a function

# [Objectives](#toc.xhtml#s115a)

After studying this chapter, you’ll be able to:

*   Optimize your code
*   Use dynamic memory allocation in Go programs
*   Get an address of a variable in a memory
*   Perform many operations on variables by pointers
*   Build complex data structures

# [Introduction](#toc.xhtml#s116a)

**Pointers** are a key concept in the Go language. The pointer is one of the derived data types. When we declare a variable, the Go compiler allocates some space in the system memory according to the type of that variable. That memory space has a unique address to identify that variable. The address is represented by a hexadecimal value. The pointer refers to the data by storing the address of any variable located in the system memory. It makes the data handling task easy by accessing the data directly from its memory. The type of pointer is the same as the type of that variable whose address is stored by the pointer. Therefore, an integer type of pointer holds the address of an integer type of variable. A pointer refers by accessing the value and this is called dereferencing a pointer.

# [Need for pointers](#toc.xhtml#s117a)

The pointer is a variable that stores an address of another variable. Now the question is, why should we use it? Although we can access the variable by its name in a large application, this process takes additional space in the system memory. If we need to pass a large chunk of data through a function, then we can pass only its address instead of passing the complete data. Pointers are used to assign as well as release the memory space. So, pointers do great memory utilization. Also, the execution time is faster with pointers because data is directly accessed by the memory location. Thus, we can conclude the following points as the benefits of pointers:

*   Faster execution time
*   Memory utilization
*   Easy management of variables
*   Dynamic memory allocation

As Go is a concurrent language, we can run multiple tasks simultaneously with the help of Goroutine and channels. While using pointers, it is easy to read data by multiple processes but modifying the data using address is quite dangerous. Go facilitates pointers but the use of pointers is totally in our hands. The wise use of pointers is necessary for the Go language.

# [Declare pointers](#toc.xhtml#s118a)

As the pointer is a variable, the way to declare a pointer is the same as other variables. Here, the asterisk (\*) makes the difference. It tells the compiler that the variable is a pointer. To declare a pointer, we use \* before the type of pointer variable.

**Syntax:**

`var name_of_pointer *type_of_pointer`

**Example:**

`func main() {`

`var pointerv *int`

`fmt.Println("Default value of pointer is:",pointerv) // Default value of pointer is: <nil>`

`}`

Here nothing is assigned to a pointer. So the default value is nil of integer type of pointer. Any uninitialized pointer has a zero value that is nil here.

# [Initializing pointers](#toc.xhtml#s119a)

**Initializing pointers** means assigning an address of a variable to the pointer. Here, an address is denoted by the & operator. We will use two operators: \* to declare a pointer or access the value at a specific address and & to get the address of a specific variable.

**Syntax:**

`name_of_pointer = &name_of_variable`

**Example:**

`func main() {`

`a:= 10`

`var pointerv *int`

`pointerv = &a`

`//1`

`fmt.Println(pointerv) // 0x1184e068`

`//2`

`fmt.Println(&pointerv) // 0x1183e0f8`

`}`

In the example given above, the `statement1` shows the address of variable a and the value stored in the pointer variable. `Statement2` shows the address of the pointer in memory.

# [Dereferencing pointers](#toc.xhtml#s120a)

Getting the value stored in an address pointed by a pointer is called **dereferencing the pointer**. The operator \* is used for accessing the value. This operator is called dereference or indirection operator.

**Example:**

`func main() {`

`a:= 10`

`var pointerv *int`

`pointerv = &a`

`fmt.Println(pointerv) // 0x1184e068`

`fmt.Println(*pointerv) // 10`

`}`

# [Manipulating pointers](#toc.xhtml#s121a)

We can manipulate pointers using the indirection operator. We can access the data by using pointers and we can use it as required. The value at a specific memory location can also be changed by pointers.

**Example:**

`func main() {`

`a:= 10`

`var pointerv *int`

`pointerv = &a`

`fmt.Println(*pointerv) // 10`

`*pointerv = 30`

`fmt.Println("Afer assigning new value")`

`fmt.Println(*pointerv) // 30`

`}`

# [Creating pointers with new](#toc.xhtml#s122a)

Go provides an built-in function called new that is used to allocate memory space at runtime. This function allocates memory according to the passed data type and returns its address to a pointer. The syntax of the new function is as follows:

**Syntax:**

`func new(Type) *Type`

The argument type indicates the data type for which we need to allocate space in memory. The new function returns a pointer of that address that can be assigned in any pointer variable.

**Example:**

`func main() {`

`var a int`

`pointerv:= &a`

`fmt.Println(pointerv) // 0x1184e068`

`pointerv = new(int)`

`fmt.Println(pointerv) // 0x1184e09c`

`fmt.Println(*pointerv) // 0`

`*pointerv =10`

`fmt.Println(*pointerv) // 10`

`}`

In the example given above, pointerv first contains the address of a variable "a" that is `0x1184e068`. Then, we allocate runtime memory space for an integer variable and assign its address to pointerv. Now pointerv has an address of this integer type data, created by a new function that is `0x1184e09c`. After that, we get the value that is referred by `pointer`. Since nothing is assigned at this address, the default value is zero. Now, we dereference the pointer and assign the value to it, which is 10.

# [Nested pointers](#toc.xhtml#s123a)

With the use of the new function, it is clear that a pointer doesn't only hold an address of a variable, but simply holds an address of anything that is allocated in memory. When we declare a pointer, the compiler allocates memory space for the pointers too, depending on the type of pointers. Thus, we can assign an address of a pointer to another pointer easily. We can say it as ***pointer to a pointer*** also. Here is an example of nested pointers:

`func main() {`

`var a int`

`pointerv:= &a`

`fmt.Println("value of pointerv:", pointerv) // value of pointerv: 0x1184e068`

`fmt.Println("Address of pointerv:", &pointerv) // Address of pointerv: 0x1183e0f8`

`pointerv1 := &pointerv`

`fmt.Println("value of pointerv1:", pointerv1) // value of pointerv1: 0x1183e0f8`

`fmt.Println("Address of pointerv1:", &pointerv1) // Address of pointerv1: 0x1183e108`

`pointerv2 := &pointerv1`

`fmt.Println("value of pointerv2:", pointerv2) // value of pointerv2: 0x1183e108`

`fmt.Println("Address of pointerv2:", &pointerv2) // Address of pointerv2: 0x1183e110`

`}`

In the example given above, `pointerv1` and `pointerv2` work as **pointer to a pointer.** They both hold an address of a variable that already holds an address of some other variable.

# [Array of pointer](#toc.xhtml#s124a)

In the Go language, we can create an array of pointers that hold an address of the same type of multiple variables.

**Example:**

`func main() {`

`var a, b int`

`var pointerv[4] *int`

`pointerv[0] = &a`

`pointerv[3] = &b`

`fmt.Println(pointerv) // [0x11810088 <nil> <nil> 0x1181008c]`

`}`

# [Passing pointers to a function](#toc.xhtml#s125a)

In the previous chapters, we discussed functions, passing arguments to functions, etc. While using functions, we can pass a pointer as an argument; or we should say, instead of passing a value, we can pass a reference. Let's understand why there is a need to pass a reference and how can we do it. In the example given below, we need to change the value of the variable "a".

**Example:**

`//Passing by value`

`func main() {`

`a := "Welcome world"`

`pointerv := &a`

`fmt.Println("value of a is:", *pointerv)`

`changeVal(a)`

`fmt.Println("After modification, value of a is:", *pointerv)`

`}`

`func changeVal(y string){`

`y = "Hello Go!"`

`fmt.Println("changed value is:", y)`

`}`

**Output:**

`value of a is: Welcome world`

`changed value is: Hello Go!`

`After modification, value of a is: Welcome world`

Here, it is clear that the value is to be changed in function `changeVal`, but in the main function, it doesn’t reflect. The value in memory is the same as it was. Now, we will pass the reference of "a".

**Example:**

`func main() {`

`a := "Welcome world"`

`pointerv := &a`

`fmt.Println("Value of a is:", *pointerv)`

`changeVal(pointerv)`

`fmt.Println("After modification, value of a is:", *pointerv)`

`}`

`func changeVal(y *string){`

`*y = "Hello Go!"`

`fmt.Println("Changed value is:", *y)`

`}`

**Output:**

`Value of a is: Welcome world`

`Changed value is: Hello Go!`

`After modification, value of a is: Hello Go!`

In the example given above, we are passing the address of "a" that `poinetrv` holds. In the function `changeVal`, we are modifying the value directly at the address of that variable. Here, pointer works well.

**Note:** If someone knows C or C++, they would be familiar with pointer operations, increment, or decrement. The Go language doesn't support arithmetic pointers. On performing such operations, the Go compiler will give an error (invalid operation).

# [Conclusion](#toc.xhtml#s126a)

Here, we have learned about one of the derived data type pointers that refer to the data stored in a memory. We saw how to declare, initialize, and manipulate the pointers with or without the new keyword. We understood the concept of nested pointers, array of pointers, and others to optimize our code. Till now, we have seen a few data types individually. In the next chapter, we'll see the arrangement or relation between various data types that we have in the Go language by using structures.

# [Questions](#toc.xhtml#s127a)

1.  Why do we need pointers?
2.  What is the difference between \* and & with pointers in Go?
3.  How can we create pointers with a new keyword?
4.  How can we pass pointers to a function?
5.  Is it possible to create an array of pointers?
6.  Why do we need nested pointers?

# [CHAPTER 12](#toc.xhtml#c12)

# [Structures](#toc.xhtml#c12)

In Go, arrays are used to store large data of the same type. In various cases, we need to hold several data items of a different type in the same variable. Here, structure plays a key role in the Go language. We can combine the different types of data in a single variable by using structure. Let's cover other aspects of structure that we have in the Go language.

# [Structure](#toc.xhtml#s128a)

In this chapter, we will discuss the following topics:

*   Introduction to structures
*   Declaring structures
*   Initializing structures
*   Accessing field of structures
*   Pointer to structure
*   A struct with a new function
*   Anonymous struct fields
*   Nested structure
*   Passing structs to functions/copying structs
*   Comparing structs

# [Objectives](#toc.xhtml#s129a)

After studying this chapter, you’ll be able to:

*   Combine various data types in a single variable
*   Use structures in your Go program
*   Use pointers to refer to struct in Go

# [Introduction](#toc.xhtml#s130a)

A **struct** is a user-defined composite data type that defines a list of different types of variables in a block of memory. By using struct, a collection of multiple data types are combined and create a single type. An entity that has various properties can be represented by struct. In the Go language, struct works in the same way as classes do in object-oriented programming with some differences. Struct supports for composition as we can create a complex data type by combining different data types in one.

# [Declaring struct](#toc.xhtml#s131a)

A `struct` is nothing but a collection of multiple types of data that is defined under one name and one type. Here is the syntax to declare struct:

**Syntax:**

`type name_of_struct struct{`

`name_of_variable1 type_of_variable1`

`name_of_variable2 type_of_variable2`

`name_of_variable3 type_of_variable3`

`. . .`

`. . .`

`}`

**Example:**

`type student struct{`

`name string`

`rollno int`

`city string`

`}`

Or

`type student struct{`

`name, city string`

`rollno int`

`}`

In the code given above, the `type` keyword tells the compiler that the followed is a new data type. Here, we declared a `struct` named `student`. The student `struct` has various fields like `name, city`, etc. that is of string type and `rollno` that is of type integer. In the second one, we combined the variable of the same data type. Such `structs` are called named struct because here, we create a new `struct` type student.

It is not necessary to declare a new type while declaring structs. We can also create an anonymous structure in the Go language as shown below:

`var student struct{`

`name, city string`

`rollno int`

`}`

Here, instead of creating a new type, we are declaring a variable `student` of the struct type. Let's create a variable of type student (named `struct`).

**Syntax:**

`var type_of_variable name_of_struct`

**Example:**

`func main() {`

`type student struct{`

`name, city string`

`rollno int`

`}`

`var student_var student`

`fmt.Println(student_var) // {0}`

`var student1 struct{`

`name, city string`

`rollno int`

`}`

`fmt.Println(student1) // {0}`

`}`

In the example given above, we have created a variable `student_var` of type student. By default, it has default values for every field: 0 for integer type of variables and blank for string type variables. The same goes for anonymous `structstudent1`.

# [Initializing struct](#toc.xhtml#s132a)

Using struct literal, we can initialize struct variables. While initializing struct, field values should be in the same order that they have been declared in that specific struct. Also, the number of values should be the same as the number of fields declared in a struct.

**Example:**

`func main() {`

`type student struct{`

`name, city string`

`rollno int`

`}`

`var student_var student`

`student_var = student{"rahul", "jaipur", 67}`

`fmt.Println(student_var) // {rahul jaipur 67}`

`}`

In the example given above, values are passed in the same order as they are declared. If we don't pass the values in the same order, the compiler will give an error. To avoid such an issue, we can pass the values with the field's name. On passing the values with the field's name, we can skip the value of any field. In such a case, the default value is taken by that field.

**Example:**

`func main() {`

`type student struct{`

`name, city string`

`rollno int`

`}`

`var student_var student`

`student_var = student{rollno:67, city:"jaipur"} // {jaipur 67}`

`fmt.Println(student_var)`

`// Anonymous struct`

`student1 := struct{`

`name string`

`city string`

`rollno int`

`}{`

`name : "rahul",`

`rollno :67,`

`}`

`fmt.Println(student1) // {rahul 67}`

`}`

# [Accessing struct's field](#toc.xhtml#s133a)

We can access the particular field of a struct by using the dot operator. By accessing fields, we can modify their values and so, struct is called mutable. There is another way to initialize an anonymous struct using the dot operator. Here is an example of using the dot operator.

**Example:**

`func main() {`

`var student struct{`

`name, city string`

`rollno int`

`}`

`student.city = "jaipur"`

`student.rollno = 67`

`fmt.Println(student) // {jaipur 67}`

`type student1 struct{`

`name, city string`

`rollno int`

`}`

`var student_var student1`

`student_var.name = "rahul"`

`student_var.rollno = 67`

`fmt.Println(student_var) // {rahul 67}`

`}`

# [Pointer to struct](#toc.xhtml#s134a)

We can use a pointer with a struct like a normal variable. There are two ways by which a pointer can refer structs. Either first, create a struct and then assign its address to a pointer; or directly create a pointer that points a struct. The second way skips the step of creating the struct type of the variable and taking less memory. With pointers, we can access the struct's field using the dot operator. The following example explains the use of pointers with struct:

**Example:**

`func main() {`

`type student struct{`

`name, city string`

`rollno int`

`}`

`student_var := student{"rahul", "jaipur", 67}`

`p1 := &student_var`

`fmt.Println(p1) // &{rahul jaipur 67}`

`fmt.Println(*p1) // {rahul jaipur 67}`

`fmt.Println((*p1).city) //jaipur`

`fmt.Println(p1.city) //jaipur`

`//Directly create a pointer`

`p2 := &student{"rahul", "jaipur", 67}`

`fmt.Println(p2) // &{rahul jaipur 67}`

`fmt.Println(*p2) // {rahul jaipur 67}`

`fmt.Println((*p2).city) //jaipur`

`fmt.Println(p2.city) //jaipur`

`//Pointer with anonymous struct`

`var student1 struct{`

`name, city string`

`rollno int`

`}`

`annony_point := &student1`

`annony_point.name = "rahul"`

`annony_point.rollno = 67`

`fmt.Println(annony_point) // &{rahul 67}`

`fmt.Println(*annony_point) // {rahul 67}`

`}`

# [A struct with a new function](#toc.xhtml#s135a)

A struct can be created with a new function also. This function allocates memory space according to the size of the struct fields and returns a pointer to it. Initially, all fields have their default values if they are not given.

**Example:**

`func main() {`

`type student struct{`

`name, city string`

`rollno int`

`}`

`p1 := new(student)`

`fmt.Println(*p1) // {0}`

`p1.city = "jaipur"`

`p1.rollno = 67`

`fmt.Println(*p1) // {jaipur 67}`

`//anonymous struct with new`

`annony_point := new(struct{`

`name, city string`

`rollno int`

`})`

`fmt.Println(*annony_point) // {0}`

`annony_point.name = "rahul"`

`fmt.Println(*annony_point) // {rahul 0}`

`}`

# [Anonymous struct fields](#toc.xhtml#s136a)

In the Go language, it is not necessary to define the name of struct fields. If we mention the field type only, it will consider the type as the name of that field.

**Example:**

`func main() {`

`type student struct{`

`string`

`int`

`}`

`a := student{"rahul", 67}`

`fmt.Println(a) // {rahul 67}`

`}`

If we have two or more fields of the same data type, we can use only one field as anonymous. For the others, we have to give the field names. Otherwise, the compiler will give an error (duplicate field) as shown below:

`type student struct{`

`string`

`string`

`int`

`}`

`a := student{"rahul", "jaipur", 67}`

`fmt.Println(a)`

**Output:**

`Error: duplicate field string`

**Example:**

`func main() {`

`type student struct{`

`string`

`city string`

`int`

`}`

`a := student{"rahul","jaipur", 67}`

`fmt.Println(a) // {rahul jaipur 67}`

`}`

# [Nested struct](#toc.xhtml#s137a)

A struct can have another struct as a field and so on. In this way, we can create a nested struct in the Go language.

**Example:**

`func main() {`

`type result struct{`

`math int`

`science int`

`english int`

`isPass bool`

`}`

`type student struct{`

`name, city string`

`rollno int`

`result`

`}`

`a := student{"rahul", "jaipur", 11, result{45, 78, 90, true}}`

`fmt.Println(a) // {rahul jaipur 11 {45 78 90 true}}`

`//anonymous nested struct`

`result_annon := struct{`

`math int`

`science int`

`english int`

`isPass bool`

`}{`

`math: 45,`

`science: 78,`

`english: 90,`

`isPass: true,`

`}`

`student_annon := struct{`

`name, city string`

`rollno int`

`result`

`}{`

`name : "rahul",`

`city : "city",`

`rollno : 11,`

`result : result_annon,`

`}`

`fmt.Println(student_annon) // {rahul city 11 {45 78 90 true}}`

`}`

# [Passing structs to functions/copying structs](#toc.xhtml#s138a)

While copying one struct to another, a new copy is created and then assigned to another variable. In the same way, while passing a struct to another function, a copy of the struct is passed to a function.

**Example:**

`package main`

`import "fmt"`

`func getValue(student_copy1 *student) string{`

`fmt.Println(student_copy1) // &{rahul jaipur 67}`

`return student_copy1.name`

`}`

`type student struct{`

`name, city string`

`rollno int`

`}`

`func main() {`

`a := student{"rahul", "jaipur", 67}`

`student_copy := a`

`fmt.Println(student_copy.rollno) // 67`

`fmt.Println(student_copy) // {rahul jaipur 67}`

`// Passing address of struct to function`

`fmt.Println(getValue(&student_copy)) // rahul`

`}`

# [Comparing structs](#toc.xhtml#s139a)

Since a struct can be copied from one to another variable, it is not wrong to say that a struct is of the value type. Like values, we can also compare two structs. Two structs are said to be equal if their fields and corresponding values are the same.

**Example:**

`func main() {`

`student := struct{`

`name, city string`

`rollno int`

`}{`

`name : "rahul",`

`city : "jaipur",`

`rollno : 11,`

`}`

`student1 := struct{`

`name, city string`

`rollno int`

`}{`

`name : "rahul",`

`city : "jaipur",`

`rollno : 11,`

`}`

`fmt.Println(student==student1) // true`

`student3 := struct{`

`name, city string`

`rollno int`

`}{`

`name : "rahul",`

`city : "jaipur",`

`}`

`fmt.Println(student==student3) // false`

`student4 := struct{`

`name, city string`

`rollno int`

`}{`

`name : "rahul",`

`city : "jaipur",`

`rollno : 0,`

`}`

`fmt.Println(student3==student4) // true`

`}`

# [Conclusion](#toc.xhtml#s140a)

From the examples given above, we have learned how to declare, initialize, and perform various operations with structures. If we talk about object-oriented programming, the concept of structure is quite similar to classes. As class supports inheritance, structure supports composition. Let's understand composition in the next chapter.

# [Questions](#toc.xhtml#s141a)

1.  How can we declare and initialize a structure in Go?
2.  What is the use of a new keyword in structs?
3.  How an we compare two structs in Go?
4.  Which operator is used to access the struct fields in Go?
5.  What do you understand by anonymous fields in structure?
6.  How can we pass structs in the Go functions?

# [CHAPTER 13](#toc.xhtml#c13)

# [Composition](#toc.xhtml#c13)

If you understand the programming languages C++, Java, etc., then you must be aware of classes and inheritance. Go language doesn't support inheritance. In Go language struct behaves as classes and composition works as inheritance. In simple language, composition means a collection of things or putting something together. In this chapter, let's cover the concept of composition.

# [Structure](#toc.xhtml#s142a)

In this chapter, we will discuss the following topics:

*   Introduction to composition
*   Embedding pointers
*   Embedding slices of structs

# [Objectives](#toc.xhtml#s143a)

After studying this chapter, you’ll be able to:

*   Reuse the code by composition
*   Embed multiple structs, a slice of structs, and pointers to struct
*   Build large and efficient APIs by merging multiple smaller parts

# [Introduction](#toc.xhtml#s144a)

In Go language, the **composition** is the embedding of structs and composing data structures. Composition helps to create a large application by merging multiple, single-purpose type or methods. It provides readability and flexibility with a Go application. Let's create a simple program that will explain composition.

**Example:**

`package main`

`import "fmt"`

`type websiteinfo struct{`

`name string`

`url string`

`ageinyear int`

`}`

`func main() {`

`type youtube struct{`

`websiteinfo`

`ytFirstVideo string`

`ytlongestvideo string`

`}`

`type amazon struct{`

`websiteinfo`

`departments string`

`can_sell bool`

`}`

`youtube_var := youtube{websiteinfo{"Youtube", "www.youtube.com", 14}, "me at the zoo", "571 hours, 1 minute and 41 seconds"}`

`amazon_var := amazon{websiteinfo{"Amazon", "www.amazon.com", 25}, "Automotive, computers, electronics etc", true}`

`fmt.Println(youtube_var, amazon_var)`

`fmt.Println("youtube first video:", youtube_var.ytFirstVideo)`

`fmt.Println("youtube url:", youtube_var.websiteinfo.url)`

`fmt.Println("youtube url:", youtube_var.url)`

`fmt.Println("can we sell on amazon:", amazon_var.can_sell)`

`fmt.Println("Amazon url:", amazon_var.websiteinfo.url)`

`fmt.Println("Amazon url:", amazon_var.url)`

`}`

**Output:**

`{{Youtube www.youtube.com 14} me at the zoo 571 hours, 1 minute and 41 seconds} {{Amazon www.amazon.com 25} Automotive, computers, electronics etc. true}`

`youtube first video: me at the zoo`

`youtube url: www.youtube.com`

`youtube url: www.youtube.com`

`can we sell on amazon: true`

`Amazon url: www.amazon.com`

`Amazon url: www.amazon.com`

In the example given above, we have created a struct` websiteinfo` that has three fields. This struct dictates the basic information of any website. Another is structyoutube that has three fields. A struct `websiteinfo` represents the basic information of YouTube and the other two fields represent the first and longest video on YouTube. Structamazon also has three fields. One of them is an anonymous field `websiteinfo` like structyoutube has. Here, struct `websiteinfo` is embedded in both the other structs. It represents that structs `youtube` and amazon are composed of `websiteinfo`.

We are creating a literal `youtube_var` of type youtube. It is a composite literal and a combination of two literals, `websiteinfo` and youtube. The same goes with literal amazon_var. Structyoutube and amazon have full access to all the fields and methods of `structwebsiteinfo` as `websiteinfo` is defined as a field in `structyoutube` and amazon.

We can access the fields of websiteinfo in two ways. First, we can access `structwebsiteinfo` with struct literals (`youtube_var` or `amazon_var`) and then access its field using the dot operator. Second, we can directly access the fields of `websiteinfo` with struct literals using the dot operator.

Now, create a method on websiteinfostruct with the above program.

`func (webinfo websiteinfo) basicInfo(){`

`fmt.Println("Name of website:", webinfo.name)`

`fmt.Println("Url of website:", webinfo.url)`

`fmt.Println("How old is this website:", webinfo.ageinyear)`

`}`

The method `basicInfo` has `websiteinfo` as a receiver type that provides basic information on any website. We can access such a method by the composite literals `youtube_var` and `amazon_var` using the dot operator. There are two ways to access this method, either first access the `structwebsiteinfo` and then access the method basicInfo; or directly access the method `basicInfo` by composite literals.

`youtube_var.websiteinfo.basicInfo()`

`amazon_var.basicInfo()`

As struct `youtube` and `amazon` have access to all the fields and methods of `structwebsiteinfo`, we can define a method on struct youtube as shown below:

`func (yt youtube) youtubeInfo(){`

`fmt.Println("Name of website:", yt.name)`

`fmt.Println("Url of website:", yt.websiteinfo.url)`

`fmt.Println("How old is this website:", yt.ageinyear)`

`fmt.Println("First video on youtube:", yt.ytFirstVideo)`

`fmt.Println("Longest video on youtube:", yt.ytlongestvideo)`

`}`

We can access this method by the youtube literal using dot operator.

`youtube_var.youtubeInfo()`

If required, we can define a method by calling the base method of the embedded struct as shown below:

`func (azn amazon) amazonInfo(){`

`azn.basicInfo()`

`fmt.Println("Departments of amazon:", azn.departments)`

`fmt.Println("Can we sell on amazon:", azn.can_sell)`

`}`

`amazon_var.amazonInfo()`

In the method shown above, we are accessing the `basicInfo` method by the amazon literal and the same is done in the method amazonInfo as in `youtubeinfo`. A complete example of `composition` is shown below:

**Example:**

`package main`

`import "fmt"`

`type websiteinfo struct{`

`name string`

`url string`

`ageinyear int`

`}`

`type youtube struct{`

`websiteinfo`

`ytFirstVideo string`

`ytlongestvideo string`

`}`

`type amazon struct{`

`websiteinfo`

`departments string`

`can_sell bool`

`}`

`func (webinfo websiteinfo) basicInfo(){`

`fmt.Println("Name of website:", webinfo.name)`

`fmt.Println("Url of website:", webinfo.url)`

`fmt.Println("How old is this website:", webinfo.ageinyear)`

`}`

`func (yt youtube) youtubeInfo(){`

`fmt.Println("Name of website:", yt.name)`

`fmt.Println("Url of website:", yt.websiteinfo.url)`

`fmt.Println("How old is this website:", yt.ageinyear)`

`fmt.Println("First video on youtube:", yt.ytFirstVideo)`

`fmt.Println("Longest video on youtube:", yt.ytlongestvideo)`

`}`

`func (azn amazon) amazonInfo(){`

`azn.basicInfo()`

`fmt.Println("Departments of amazon:", azn.departments)`

`fmt.Println("Can we sell on amazon:", azn.can_sell)`

`}`

`func main() {`

`youtube_var := youtube{websiteinfo{"Youtube", "www.youtube.com", 14}, "me at the zoo", "571 hours, 1 minute and 41 seconds"}`

`amazon_var := amazon{websiteinfo{"Amazon", "www.amazon.com", 25}, "Automotive, computers, electronics etc", true}`

`fmt.Println(youtube_var, amazon_var)`

`fmt.Println("youtube first video:", youtube_var.ytFirstVideo)`

`fmt.Println("youtube url:", youtube_var.websiteinfo.url)`

`fmt.Println("youtube url:", youtube_var.url)`

`fmt.Println("can we sell on amazon:", amazon_var.can_sell)`

`fmt.Println("Amazon url:", amazon_var.websiteinfo.url)`

`fmt.Println("Amazon url:", amazon_var.url)`

`youtube_var.websiteinfo.basicInfo()`

`amazon_var.basicInfo()`

`youtube_var.youtubeInfo()`

`amazon_var.amazonInfo()`

`}`

**Output:**

`{{Youtube www.youtube.com 14} me at the zoo 571 hours, 1 minute and 41 seconds} {{Amazon www.amazon.com 25} Automotive, computers, electronics etc true}`

`youtube first video: me at the zoo`

`youtube url: www.youtube.com`

`youtube url: www.youtube.com`

`can we sell on amazon: true`

`Amazon url: www.amazon.com`

`Amazon url: www.amazon.com`

`Name of website: Youtube`

`Url of website: www.youtube.com`

`How old is this website: 14`

`Name of website: Amazon`

`Url of website: www.amazon.com`

`How old is this website: 25`

`Name of website: Youtube`

`Url of website: www.youtube.com`

`How old is this website: 14`

`First video on youtube: me at the zoo`

`Longest video on youtube: 571 hours, 1 minute and 41 seconds`

`Name of website: Amazon`

`Url of website: www.amazon.com`

`How old is this website: 25`

`Departments of amazon: Automotive, computers, electronics etc`

`Can we sell on amazon: true`

# [Embedding pointers](#toc.xhtml#s145a)

Till now, we have used struct values for embedding. We can use a struct reference for embedding or creating methods. In the following example, we are passing the reference of `structwebsiteinfo` to method `basicInfo`.

**Example:**

`package main`

`import "fmt"`

`type websiteinfo struct{`

`name string`

`url string`

`ageinyear int`

`}`

`type youtube struct{`

`websiteinfo`

`ytFirstVideo string`

`ytlongestvideo string`

`}`

`func basicInfo(webinfo *websiteinfo){`

`fmt.Println("Name of website:", webinfo.name)`

`fmt.Println("Url of website:", webinfo.url)`

`fmt.Println("How old is this website:", webinfo.ageinyear)`

`}`

`func youtubeInfo(yt *youtube){`

`fmt.Println("Name of website:", yt.name)`

`fmt.Println("Url of website:", yt.websiteinfo.url)`

`fmt.Println("How old is this website:", yt.ageinyear)`

`fmt.Println("First video on youtube:", yt.ytFirstVideo)`

`fmt.Println("Longest video on youtube:", yt.ytlongestvideo)`

`}`

`func main() {`

`webinfo := websiteinfo{"Youtube", "www.youtube.com", 14}`

`youtube_var := youtube{webinfo, "me at the zoo", "571 hours, 1 minute and 41 seconds"}`

`basicInfo(&webinfo)`

`youtubeInfo(&youtube_var)`

`}`

**Output:**

`Name of website: Youtube`

`Url of website: www.youtube.com`

`How old is this website: 14`

`Name of website: Youtube`

`Url of website: www.youtube.com`

`How old is this website: 14`

`First video on youtube: me at the zoo`

`Longest video on youtube: 571 hours, 1 minute and 41 seconds`

# [Embedding slice of structs](#toc.xhtml#s146a)

Slices of structs can be embedded with another struct in Golang. The following is an example of embedding slices with structs. Here, we are creating a slice of struct of type sites (`site1, site2, site3`) that are embedded with `struct struct_slice`. While embedding the slices of the struct, we cannot define it as an anonymous field; it is necessary to give a name to such fields. After embedding the slice of the struct, we are accessing the method `sitesInfo` that prints every element of the slice.

**Example:**

`package main`

`import "fmt"`

`type websiteinfo struct{`

`name string`

`url string`

`ageinyear int`

`}`

`type sites struct{`

`websiteinfo`

`ytFirstVideo string`

`ytlongestvideo string`

`}`

`type struct_slice struct{`

`sites_struct_slice []sites`

`}`

`func sitesInfo (siteinfo *struct_slice){`

`fmt.Println("Information of website:")`

`for _, v := range siteinfo.sites_struct_slice {`

`fmt.Println(v)`

`}`

`}`

`func sitesName (siteinfo *struct_slice){`

`fmt.Println("Name of website:")`

`for _, v := range siteinfo.sites_struct_slice {`

`fmt.Println(v.name)`

`}`

`}`

`func main() {`

`site1 := sites{websiteinfo{"Youtube", "www.youtube.com", 14}, "youtube first video", "571 hours, 1 minute and 41 seconds"}`

`site2 := sites{websiteinfo{"Facebook", "www.facebook.com", 15}, "facebook first video", "45 minutes"}`

`site3 := sites{websiteinfo{"Twitter", "www.twitter.com", 13}, "twitter first video", "10 minutes"}`

`struct_slice_var := struct_slice{`

`[]sites{site1, site2, site3},`

`}`

`sitesInfo(&struct_slice_var)`

`sitesName(&struct_slice_var)`

`}`

**Output:**

`Information of website:`

`{{Youtube www.youtube.com 14} youtube first video 571 hours, 1 minute and 41 seconds}`

`{{Facebook www.facebook.com 15} facebook first video 45 minutes}`

`{{Twitter www.twitter.com 13} twitter first video 10 minutes}`

`Name of website:`

`Youtube`

`Facebook`

`Twitter`

# [Conclusion](#toc.xhtml#s147a)

In this chapter, we have learned how to get code flexibility and readability by embedding structs in Go. These structures can be embedded by values or by passing reference to a struct. By composition, a struct can contain instances of another struct and thus, provide flexibility. Just as we have composed structs in this chapter, we can do the same for interfaces. In the next chapter, we'll discuss interfaces and their role in the Go language.

# [Questions](#toc.xhtml#s148a)

1.  What is a composition in Go?
2.  What is the need for composition in Go?
3.  Does Go language support inheritance?
4.  How can we achieve composition in Go? Specify with an example.
5.  How can we embed structs using pointers?

# [CHAPTER 14](#toc.xhtml#c14)

# [Interfaces and Polymorphism](#toc.xhtml#c14)

In general terms, the **interface** is a medium to connect two or more different objects. Interfaces are all about defining behavior. In Golang, the concept of interfaces is quite different from that in Java. With the help of interfaces, polymorphism is achieved in the Go language. **Polymorphism** is nothing but a process to describe something in various forms. Let's cover the ideas of interfaces and polymorphism.

# [Structure](#toc.xhtml#s149a)

In this chapter, we will discuss the following topics:

*   Introduction to interface and polymorphism
*   Declaring interface
*   Implementing interface
*   Empty interface
*   Implementing multiple interfaces
*   Type assertion
*   Type switch
*   Embedding interfaces
*   Interfaces as polymorphism

# [Objectives](#toc.xhtml#s150a)

After studying this chapter, you’ll be able to:

*   Organize complex compositions and make the code reusable
*   Use functions with different type of arguments as needed
*   Get type assertion operation work on interface values
*   Use a variable name to store various type of data
*   Use a function with numerous implementations

# [Introduction](#toc.xhtml#s151a)

An **interface** is a reflection of the method declaration that only defines an action, not the implementation of that action. It can be defined as a ***collection of multiple method names, types of input arguments, and return types.*** No variable declaration or implementation is performed in the method body. In the Go language, structs or non-struct types implement the interfaces and define how the action is being performed.

In Go language, polymorphism is achieved by interfaces. In interfaces, no method has a specific implementation. It depends on the type that is implementing an interface and how it defines the method. Multiple types can implement an interface by their desired methods.

# [Declaring Interface](#toc.xhtml#s152a)

Interfaces are declared in the same way as structs are. With structs, we use the keyword `struct`. Here, we use the keyword `interface` to declare interfaces. Instead of declaring multiple fields, we declare various methods with their names, arguments, and return types in interfaces.

**Syntax:**

`type name_of_interface interface{`

`//method declaration`

`}`

**Example:**

`type AirthOperation interface{`

`Add() float32`

`Subtract(float32, float32) float32`

`Multiply(int, int) int`

`}`

In the above example, we created a variable `AirthOperation` of the type interface. This interface defines three methods. The add method may or may not accept the argument but it returns a float type value. The `subtract` methods accept two values of float type and return a float type value. The method `multiply` accepts two integer type arguments and returns an integer type value.

Like structs, we can create a variable of any interface type. Here, we can create a variable of the type `AirthOperation` as shown below:

`var interface_var AirthOperation`

**Example:**

`func main() {`

`type AirthOperation interface{`

`Add() float32`

`Subtract(float32, float32) float32`

`Multiply(int, int) int`

`}`

`var interface_var AirthOperation`

`fmt.Println(interface_var) // <nil>`

`}`

This type of interface doesn't have any value; it's nil as we cannot identify who is implementing this interface. Such a value where we are creating only a variable of an interface value is called the **static value** of the interface. The dynamic value of an interface is obtained by implementing an interface using a type.

# [Implementing interface](#toc.xhtml#s153a)

An interface can be implemented by defining the functions provided by an interface. We can implement an interface by using structs as shown below:

**Example:**

`package main`

`import "fmt"`

`// step 1`

`type AirthOperation interface{`

`Add() float32`

`Subtract(float32, float32) float32`

`Multiply(int, int) int`

`}`

`// step 2`

`type Operandset1 struct{`

`op1 float32`

`op2 float32`

`}`

`//step 3`

`func (operandset1_var Operandset1) Add() float32 {`

`return operandset1_var.op1 + operandset1_var.op2`

`}`

`// step 6`

`type Operandset2 struct{`

`op1 int`

`op2 int`

`}`

`// step 7`

`func (operandset2_var Operandset2) Add(a int, b int) float32 {`

`return float32(a + b)`

`}`

`func main() {`

`// step 4`

`operandset1_var := Operandset1{3.6, 6.9}`

`// step 8`

`operandset2_var := Operandset2{45, 67}`

`// step 5`

`fmt.Println(operandset1_var.Add())`

`// step 9`

`fmt.Println(operandset2_var.Add(operandset2_var.op1, operandset2_var.op2))`

`}`

In the example given above, we are creating two `struct Operandset1` and `Operandset2`. We defined `Add` method two times, with the receiver of `Operandset1` and `Operandse2` types and using it accordingly.

*   **Step 1:** Create the interface `AirthOperation` and declare various methods.
*   **Step 2:** Create `struct Operandset1` that have two fields of type `float32.`
*   **Step 3:** Here, define a method that is declared in interface `AirthOperation` with the receiver of `Operandset1` type.
*   **Step 4:** Create a variable of type `Operandset1` struct.
*   **Step 5:** Call the method that is defined with receiver type `Operandset1` by the variable of `Operandset1` type. It executes the method Add with receiver type `Operandset1`
*   **Step 6:** Create `struct Operandset2` that have two fields of type `int.`
*   **Step 7:** Define Add method again with the receiver of type `Operandset2` that accepts two arguments of integer type.
*   **Step 8:** Create a variable of type `Operandset2`
*   **Step 9:** Call Add method that has a receiver type `Operandset2` with struct field values.

We define `Add` method two times in a different way. One is working on float values and the other one is with integer values. We can implement the methods of the same name according to our need. We can implement the `Subtract` and `Multiply` methods in the same way. A complete example of implementing `AirthOperation` interface is shown below:

**Example:**

`package main`

`import "fmt"`

`type AirthOperation interface{`

`Add() float32`

`Subtract(float32, float32) float32`

`Multiply(int, int) int`

`}`

`type Operandset1 struct{`

`op1 float32`

`op2 float32`

`}`

`func (operandset1_var Operandset1) Add() float32 {`

`return operandset1_var.op1 + operandset1_var.op2`

`}`

`func (operandset1_var Operandset1) Subtract(a float32, b float32) float32 {`

`return a - b`

`}`

`func (operandset1_var Operandset1) Multiply(a float32, b float32) float32 {`

`return a*b`

`}`

`type Operandset2 struct{`

`op1 int`

`op2 int`

`}`

`func (operandset2_var Operandset2) Add(a int, b int) int {`

`return int(a + b)`

`}`

`func (operandset2_var Operandset2) Subtract(a int, b int) int {`

`return (a - b)`

`}`

`func (operandset2_var Operandset2) Multiply(a int, b int) int {`

`return (a * b)`

`}`

`func main() {`

`operandset1_var := Operandset1{3.6, 6.9}`

`operandset2_var := Operandset2{45, 67}`

`fmt.Println("Add method with Operandset1:", operandset1_var.Add())`

`fmt.Println("Subtract method with Operandset1:", operandset1_var. Subtract(operandset1_var.op1, operandset1_var.op2))`

`fmt.Println("Multiply method with Operandset1:", operandset1_var. Multiply(operandset1_var.op1, operandset1_var.op2))`

`fmt.Println("Add method with Operandset2:", operandset2_var. Add(operandset2_var.op1, operandset2_var.op2))`

`fmt.Println("Subtract method with Operandset2:", operandset2_var. Subtract(operandset2_var.op1, operandset2_var.op2))`

`fmt.Println("Multiply method with Operandset2:", operandset2_var. Multiply(operandset2_var.op1, operandset2_var.op2))`

`}`

**Output:**

`Add method with Operandset1: 10.5`

`Subtract method with Operandset1: -3.3000002`

`Multiply method with Operandset1: 24.84`

`Add method with Operandset2: 112`

`Subtract method with Operandset2: -22`

`Multiply method with Operandset2: 3015`

# [Empty interface](#toc.xhtml#s154a)

An interface that doesn't have any method is called an **empty interface**. Since every type implements zero methods, an empty interface can hold any value. In programming, many cases occur where there is no surety of the type of value. To handle such cases, empty interfaces are used. The `print` function is the best example of empty interfaces that are used to print any value.

In the following example, we are creating two structs of integer and string type field value. The `empty_interface` interface doesn't have any method. The method `show_value` accepts empty interface `empty_interface` that can hold any value. The value of such an empty interface is called its dynamic or concrete value.

**Example:**

`package main`

`import "fmt"`

`type empty_interface interface{`

`}`

`func show_value(interface_var empty_interface){`

`fmt.Println(interface_var)`

`}`

`func main() {`

`type string_struct struct{`

`a string`

`}`

`string_struct_var := string_struct{"Hello world"}`

`type float_struct struct{`

`a float32`

`}`

`float_struct_var := float_struct{77.88}`

`show_value(string_struct_var) // {Hello world}`

`show_value(float_struct_var) // {77.88}`

`}`

# [Implementing multiple interfaces](#toc.xhtml#s155a)

In the Go language, multiple interfaces can be implemented by a type. A variable of a specific type is assigned to an interface variable to implement each interface. Here is an example of implementing multiple interfaces with `struct Operandset1.`

**Example:**

`package main`

`import "fmt"`

`type AirthOperation interface{`

`Add() float32`

`}`

`type CompareOperation interface{`

`Compare(float32, float32) bool`

`}`

`type Operandset1 struct{`

`op1 float32`

`op2 float32`

`}`

`func (operandset1_var Operandset1) Add() float32 {`

`return operandset1_var.op1 + operandset1_var.op2`

`}`

`func (operandset1_var Operandset1) Compare(a float32, b float32) bool {`

`return a==b`

`}`

`func main() {`

`operandset1_var := Operandset1{3.6, 6.9}`

`fmt.Println(operandset1_var.Add()) // 10.5`

`fmt.Println(operandset1_var.Compare(operandset1_var.op1, operandset1_var.op2)) // false`

`var AirthOperation_var AirthOperation = operandset1_var`

`fmt.Println(AirthOperation_var.Add()) // 10.5`

`var compareOperation_var CompareOperation = operandset1_var`

`fmt.Println(compareOperation_var.Compare(operandset1_var.op1, operandset1_var.op2)) // false`

`}`

# [Type assertion](#toc.xhtml#s156a)

In general language, to assert means to ***claim something***. Type assertion claims for a type. It provides access to the interface value's underlying concrete value. In the Go language, the type assertion checks for a specific type that whether an interface value holds that type or not. If an interface value holds that specific type, it returns true and the value of that particular type; otherwise, it returns false and zero as a value.

**Syntax:**

`t, ok := i.(T)`

The above statement checks an interface i for a concrete value of type `T`. Type assertion returns two values, ok and t. If an interface contains the value of type T, it returns true to ok and assigns that value of type `T` to variable t on the left side. If an interface doesn't contain any value of type `T`, then ok will be false and zero will be assigned to variable `t.`

**Example:**

`package main`

`import "fmt"`

`type AirthOperation interface{`

`Add() float32`

`}`

`type Operandset1 struct{`

`op1 float32`

`op2 float32`

`}`

`type Operandset2 struct{`

`op1 float32`

`op2 float32`

`}`

`func (operandset1_var Operandset1) Add() float32 {`

`return operandset1_var.op1 + operandset1_var.op2`

`}`

`func main() {`

`var interface_var AirthOperation`

`interface_var = Operandset1{3.6, 6.9}`

`t, ok := interface_var.(Operandset1)`

`fmt.Println(t, ok) // {3.6 6.9} true`

`}`

In the example given above, we are checking whether the interface `AirthOperation` is implemented by a specific type or not. We create an interface variable `interface_var`. Here, the type assertion checks whether the interface is implemented by type `Operandset1` or not. In the above example, we can clearly see that `struct Operandset1` is implementing the interface's Add method. So, type assertion returns true to ok and assigns the struct value to t. If we check for the below, it triggers panic as `struct Operandset2` is not implemented on the interface `AirthOperation.`

`t, ok = a.(Operandset2)`

`fmt.Println(t, ok) // error: impossible type assertion`

# [Type switch](#toc.xhtml#s157a)

A type `switch` allows multiple type assertion in a series. It is similar to a `switch` statement. The `switch` statement is used to compare the value and type `switch` compares the type. It runs the case to see if the type specified in the case statement is held by the interface's value. There is a point in remembering that the "nil" interface always has type `nil.`

**Syntax:**

`switch v := i.(type){`

`case T1:`

`// v is of type T1`

`case T2:`

`// v is of type T2`

`default:`

`// no case matched`

`}`

In the above syntax, i is an interface like we used in type assertion. The keyword T in type assertion is replaced by type here but the purpose is the same. On the left side, value v is the interface's value of `type`. The `switch` statement checks whether the type of `v` is `T1` or `T2` and executes that particular case. It executes default if it doesn't get any matching case.

**Example:**

`package main`

`import "fmt"`

`type AirthOperation interface{`

`Add() float32`

`}`

`type Operandset1 struct{`

`op1 float32`

`op2 float32`

`}`

`type Operandset2 struct{`

`op1 int`

`op2 int`

`}`

`type Operandset3 struct{`

`op1 string`

`op2 string`

`}`

`func main() {`

`check(Operandset1{3.7, 6.7})`

`check(Operandset2{37, 67})`

`check(Operandset3{"abc", "def"})`

`}`

`func check(i interface{}) {`

`switch v := i.(type) {`

`case Operandset1:`

`fmt.Println("Interface has a value of type Operandset1 and the value is", v)`

`case Operandset2:`

`fmt.Println("Interface has a value of type Operandset2 and the value is", v)`

`default:`

`fmt.Println("Default case, Interface doesn't have a value of type", v)`

`}`

`}`

**Output:**

`Interface has a value of type Operandset1 and the value is {3.7 6.7}`

`Interface has a value of type Operandset2 and the value is {37 67}`

`Default case, interface doesn't have a value of type {abc def}`

# [Embedding interfaces](#toc.xhtml#s158a)

Go language doesn't support inheritance but it allows embedding of interfaces. An interface can embed multiple interfaces or any specific method's signature of an interface. Any changes made in the method of interfaces reflects in the embedded interface also. This somehow works as an inheritance as we are acquiring the method implementation from another interface.

The following is an example of embedding interfaces:

`package main`

`import "fmt"`

`type AirthOperation interface{`

`Add() float32`

`}`

`type CompareOperation interface{`

`Compare() bool`

`}`

`type Operation interface{`

`AirthOperation`

`Compare() bool`

`}`

`type Operandset1 struct{`

`op1 float32`

`op2 float32`

`}`

`func (operandset1_var Operandset1) Add() float32 {`

`return operandset1_var.op1 + operandset1_var.op2`

`}`

`func (operandset1_var Operandset1) Compare() bool {`

`return operandset1_var.op1 == operandset1_var.op2`

`}`

`func main() {`

`var Operation_var Operation`

`var CompareOperation_var CompareOperation`

`var AirthOperation_var AirthOperation`

`Operation_var = Operandset1{5.78, 6.8}`

`fmt.Println(Operation_var, Operation_var.Add(), Operation_var. Compare())`

`CompareOperation_var = Operandset1{6.8, 6.8}`

`fmt.Println(CompareOperation_var, CompareOperation_var.Compare())`

`AirthOperation_var = Operandset1{5, 7.8}`

`fmt.Println(AirthOperation_var, AirthOperation_var.Add())`

`}`

**Output:**

`{5.78 6.8} 12.58 false`

`{6.8 6.8} true`

`{5 7.8} 12.8`

# [Interfaces as polymorphism](#toc.xhtml#s159a)

An interface can be implemented by a type that defines the methods declared within an interface. An interface type variable can hold values of different types which implements an interface. Acquiring dynamic values by an interface variable is defined as polymorphism since in a single program, the behavior of interface changes according to the type that is implementing the interface.

In the following example, interface variable `interface_var` can have two types of values `Operandset1` and `Operandset2:`

**Example:**

`package main`

`import "fmt"`

`type AirthOperation interface{`

`Add() float32`

`}`

`type Operandset1 struct{`

`op1 float32`

`op2 float32`

`}`

`type Operandset2 struct{`

`op1 int`

`op2 int`

`}`

`func(operandset1_var Operandset1) Add() float32 {`

`return operandset1_var.op1 + operandset1_var.op2`

`}`

`func(operandset2_var Operandset2) Add() float32 {`

`return float32(operandset2_var.op1 + operandset2_var.op2)`

`}`

`func main() {`

`var interface_var AirthOperation`

`interface_var = Operandset1{5.78, 6.8}`

`fmt.Println(interface_var.Add()) // 12.58`

`interface_var = Operandset2{5, 6}`

`fmt.Println(interface_var.Add()) //11`

`}`

# [Conclusion](#toc.xhtml#s160a)

In this chapter, we saw that an interface is a way of declaring functions. An object that implements the interface defines the functions declared by that specific interface. We learned the concept of type assertion and type switch that checks for specific types in an interface. Here, we see the composition or embedding of interfaces and how these interfaces are used to achieve polymorphism. In the next chapter, we'll discuss one of Golang’s reference type maps that are widely used for accessing values in an efficient way.

# [Questions](#toc.xhtml#s161a)

1.  How do interfaces work in Go?
2.  How can we declare and implement an interface? Specify with an example.
3.  What is the advantage of polymorphism?
4.  How is polymorphism achieved in Go?
5.  Explain the difference between type assertion and type switch in Go.
6.  How are interfaces embedded in Go?

# [CHAPTER 15](#toc.xhtml#c15)

# [Maps](#toc.xhtml#c15)

In large applications, we need to hold the data in an organized way so that the values can be accessed efficiently. The concept of the map is the same as a dictionary, hash tables, etc. These are all defined by the same data structure. Let’s go ahead with maps.

# [Structure](#toc.xhtml#s162a)

In this chapter, we will discuss the following topics:

*   Introduction to maps
*   Declaring a map
*   Initializing a map
*   Map operations
*   Map as a reference type

# [Objectives](#toc.xhtml#s163a)

After studying this chapter, you’ll be able to:

*   Understand the concept of maps
*   Access the values by keys
*   Add, get, update, and delete the keys and values
*   Iterate over maps

# [Introduction](#toc.xhtml#s164a)

The **map** is a type of data structure that stores the value in the form of a key-value pair. Keys are associated with data values that can be changed as required. The map contains unique keys that cannot be changed. The type of map keys could be anything comparable. Keys can be deleted or added in the map data structure. In the map, values are accessed by using the corresponding key similar to how we access an index in the array. Maps are also called hashes or dict in a general programming language.

# [Use of maps](#toc.xhtml#s165a)

The map can be used for the following purposes:

*   Fast lookups and retrieval of values
*   Easy access to value by using keys
*   Deletion of data based on keys
*   Implementing a hash table

# [Declaring a map](#toc.xhtml#s166a)

A map can be declared in the same way as arrays. With map declaration, there is a need to declare the type of keys also. Here is the syntax to declare maps:

`var name_of_map map [type_of_keys] type_of_values`

**Example:**

`func main() {`

`var phone_dict map [string] int64`

`fmt.Println(phone_dict) // map[]`

`}`

In the example given above, variable `phone_dict` is a map that defines the string type of keys to `int` type values. By default, the map contains zero value or nil. Here, `phone_dict` is nil as it doesn’t have any key and so, no value.

# [Initializing a map](#toc.xhtml#s167a)

After declaring a map, it takes its default value as nil. It returns an empty map on reading a nil map that doesn’t have any key but on writing to nil map, the compiler shows an error. Like slices, maps are of reference type. We need to assign them to a variable to initialize them.

**Example:**

`phone_dict1 := map [string] int64{}`

`fmt.Println(phone_dict1) // map[]`

`phone_dict2 := map [string] int64{`

`"Rahul" : 9876543201,`

`"Swati" : 9123456789,`

`}`

`phone_dict2["aayush"] = 9823165748`

`fmt.Println(phone_dict2) // map[Rahul:9876543201 Swati:9123456789 aayush:9823165748]`

`phone_dict1` indicates an empty map, while `phone_dict2` has two keys, `Rahul` and `Swati`. We can get their number by accessing the associated key.

In the Go language, the `make` function is also used to initialize a map. The `make` function allocates and initializes map data structure that allows adding elements in the map. It returns a map value that points to it.

**Example:**

`phone_dict3 := make(map [string] int64)`

`phone_dict3["Rahul"] = 9876543201`

`phone_dict3["Swati"] = 9123456789`

`fmt.Println(phone_dict3) // map[Rahul:9876543201 Swati:9123456789]`

With arrays, if we access an index "out of an array limit," the compiler gives an error. On the other hand, if we access the key that doesn’t belong to that map, it will not give any error. In such a case, it returns the default value of the specified type. The following is a complete example of initializing a map:

**Example:**

`package main`

`import "fmt"`

`func main() {`

`phone_dict1 := map [string] int64{}`

`phone_dict1["Rahul"] = 9876543201`

`fmt.Println(phone_dict1)`

`phone_dict2 := map [string] int64{`

`"Rahul": 9876543201,`

`"Swati": 9123456789,`

`}`

`phone_dict2["aayush"] = 9823165748`

`fmt.Println(phone_dict2["Swati"])`

`phone_dict3 := make(map [string] int64)`

`fmt.Println(phone_dict3) // map[]`

`phone_dict3["Rahul"] = 9876543201`

`phone_dict3["Swati"] = 9123456789`

`fmt.Println(phone_dict3)`

`fmt.Println(phone_dict3["aayush"])`

`}`

**Output:**

`map[Rahul:9876543201]`

`9123456789`

`map[Rahul:9876543201 Swati:9123456789]`

`0`

# [Map operations](#toc.xhtml#s168a)

Various operations can be performed on maps in Go.

*   **Length of Map**
    
    **Length of a map** is defined by the number of keys contained by a map. In the Go language, we have a function len to get the length of a map.
    
    **Example:**
    
    `func main() {`
    
    `phone_dict3 := make(map [string] int64)`
    
    `phone_dict3["Rahul"] = 9876543201`
    
    `phone_dict3["Swati"] = 9123456789`
    
    `fmt.Println(phone_dict3)`
    
    `fmt.Println("length of phone_dict3:", len(phone_dict3))`
    
    `}`
    
    **Output:**
    
    `map[Rahul:9876543201 Swati:9123456789]`
    
    `length of phone_dict3: 2`
    
*   **Check for Keys**
    
    In the Go language, we have a few functions to get all the keys of a map or to check whether a specific key exists in a map or not.
    
    A two-value assignment test is done to check for a key in a map. The syntax to test if a key exists in a map or not is shown below:
    
    `i, ok := map_name[key_name]`
    
    It checks for a key `key_name` in map `map_name`. If a key exists, it returns true to ok, and the value of that key is assigned to variable i. If the key doesn’t exist, then it returns false to ok, and the default value of the value’s type is assigned to variable i. This is quite similar to type assertion in the interface.
    
    **Example:**
    
    `package main`
    
    `import ("fmt"`
    
    `"reflect"`
    
    `)`
    
    `func main() {`
    
    `phone_dict3 := make(map [string] int64)`
    
    `phone_dict3["Rahul"] = 9876543201`
    
    `phone_dict3["Swati"] = 9123456789`
    
    `mapkeys := reflect.ValueOf(phone_dict3).MapKeys()`
    
    `fmt.Println("Keys of phone_dict3", mapkeys)`
    
    `val, ok := phone_dict3["Swati"]`
    
    `fmt.Println(ok, val)`
    
    `val, ok = phone_dict3["Suman"]`
    
    `fmt.Println(ok, val)`
    
    `}`
    
    **Output:**
    
    `Keys of phone_dict3 [Rahul Swati]`
    
    `true 9123456789`
    
    `false 0`
    
*   **Iteration over maps**
    
    We can iterate over a map as slices using map keys. At the same time, for iterating slices, a specific order of iteration is followed depending on the index. With maps, no order is specified. It randomly works on map records. If we want to work on map records in a specific order, we can sort the slice of keys accordingly.
    
    **Example:**
    
    `package main`
    
    `import ("fmt"`
    
    `"sort"`
    
    `)`
    
    `func main() {`
    
    `phone_dict3 := make(map [string] int64)`
    
    `phone_dict3["Rahul"] = 9876543201`
    
    `phone_dict3["Swati"] = 9123456789`
    
    `phone_dict3["Suman"] = 9675463768`
    
    `phone_dict3["Mayank"] = 9342516789`
    
    `phone_dict3["Deepak"] = 8765453678`
    
    `var mapkeys [] string`
    
    `for itr := range(phone_dict3){`
    
    `fmt.Println(itr)`
    
    `mapkeys = append(mapkeys, itr)`
    
    `}`
    
    `sort.Strings(mapkeys)`
    
    `for _, k := range mapkeys {`
    
    `fmt.Println("Key:", k, "Value:", phone_dict3[k])`
    
    `}`
    
    `}`
    
    **Output:**
    
    `Rahul`
    
    `Swati`
    
    `Suman`
    
    `Mayank`
    
    `Deepak`
    
    `Key: Deepak Value: 8765453678`
    
    `Key: Mayank Value: 9342516789`
    
    `Key: Rahul Value: 9876543201`
    
    `Key: Suman Value: 9675463768`
    
    `Key: Swati Value: 9123456789`
    
*   **Delete an element from the map**
    
    We have Go’s built-in function `delete` that is used to delete a specific key from a map. The delete function deletes the specified key and doesn’t return anything. There is no harm if the specified key is not present in a map. It doesn’t give any error in such case.
    
    **Syntax:**
    
    `delete (map_name, key_to_be_deleted)`
    
    **Example:**
    
    `func main() {`
    
    `phone_dict3 := make(map [string] int64)`
    
    `phone_dict3["Rahul"] = 9876543201`
    
    `phone_dict3["Swati"] = 9123456789`
    
    `phone_dict3["Suman"] = 9675463768`
    
    `phone_dict3["Mayank"] = 9342516789`
    
    `phone_dict3["Deepak"] = 8765453678`
    
    `fmt.Println("Before deleting a key:", phone_dict3)`
    
    `delete(phone_dict3, "Suman")`
    
    `fmt.Println("After deleting a key:", phone_dict3)`
    
    `}`
    
    **Output:**
    
    `Before deleting a key: map[Deepak:8765453678 Mayank:9342516789 Rahul:9876543201 Suman:9675463768 Swati:9123456789]`
    
    `After deleting a key: map[Deepak:8765453678 Mayank:9342516789 Rahul:9876543201 Swati:9123456789]`
    
*   **Comparison of maps**
    
    In the Go language, maps can be compared in two ways. The first is by checking whether a map is nil or not. The second is by comparing two maps by differentiating each one’s element.
    
    We can use the operator == to check if a map is nil or not.
    
    To compare two maps individually, Go provides the function `DeepEqual` in the `reflect` package. It returns true if both maps have the same keys and the same key’s associated values, otherwise false.
    
    **Example:**
    
    `package main`
    
    `import ("fmt"`
    
    `"reflect"`
    
    `)`
    
    `func main() {`
    
    `phone_dict := make(map [string] int64)`
    
    `phone_dict["Rahul"] = 9876543201`
    
    `phone_dict["Swati"] = 9123456789`
    
    `phone_dict1 := make(map [string] int64)`
    
    `phone_dict1["Rahul"] = 9876543201`
    
    `phone_dict1["Swati"] = 9123456789`
    
    `fmt.Println(phone_dict==nil)`
    
    `fmt.Println(reflect.DeepEqual(phone_dict, phone_dict1))`
    
    `phone_dict1["Swati"] = 1987654321`
    
    `fmt.Println(reflect.DeepEqual(phone_dict, phone_dict1))`
    
    `}`
    
    **Output:**
    
    `false`
    
    `true`
    
    `false`
    

# [Map as a reference type](#toc.xhtml#s169a)

Like slices, maps are also of referenced type data structure. When we initialize a map and assign it to a variable, it points to the internal structure of a map. Any changes made in the map record reflects in its memory. On assigning the map variable to another variable, both of them refer to the same data structure of the map. Any changes made in one variable reflects another one also as both are referring to the same memory location.

In the following example, we are assigning map variable `phone_dict` to `phone_dict1`. When we change the value of the key Mayank in `phone_dict1`, it reflects the same in `phone_dict` too.

**Example:**

`func main() {`

`phone_dict := make(map [string] int64)`

`phone_dict["Rahul"] = 9876543201`

`phone_dict["Swati"] = 9123456789`

`phone_dict["Suman"] = 9675463768`

`phone_dict["Mayank"] = 9342516789`

`phone_dict["Deepak"] = 8765453678`

`fmt.Println(phone_dict["Mayank"])`

`phone_dict1 := phone_dict`

`phone_dict1["Mayank"] = 1234567890`

`fmt.Println(phone_dict["Mayank"])`

`}`

**Output:**

`9342516789`

`1234567890`

The same goes with function when we pass a map as an argument to a function. Here is an example as shown below:

**Example:**

`package main`

`import "fmt"`

`func change_value(phone_dict1 map[string]int64){`

`phone_dict1["Mayank"] = 1234567890`

`}`

`func main() {`

`phone_dict := make(map [string] int64)`

`phone_dict["Rahul"] = 9876543201`

`phone_dict["Swati"] = 9123456789`

`phone_dict["Suman"] = 9675463768`

`phone_dict["Mayank"] = 9342516789`

`phone_dict["Deepak"] = 8765453678`

`fmt.Println("Before calling function, value of key 'Mayank' is:", phone_dict["Mayank"])`

`change_value(phone_dict)`

`fmt.Println("After calling function, value of key 'Mayank' is:", phone_dict["Mayank"])`

`}`

**Output:**

`Before calling function, value of key 'Mayank' is: 9342516789`

`After calling function, value of key 'Mayank' is: 1234567890`

# [Conclusion](#toc.xhtml#s170a)

Thus, we can say that maps are of reference type in Go and connect keys to value. For fast lookup and retrieval of values, maps can be used. Here, we have learned the declaration, initialization, and various operations that can be performed on maps. After getting an idea of the Golang data types, there is a need to understand one of the key concepts of Golang which is concurrency. Let’s understand it in the next chapter.

# [Questions](#toc.xhtml#s171a)

1.  Specify the declaration and initialization of maps in Go with an example.
2.  How can we use the map as a reference in Go?
3.  What is the default value of the map?
4.  Which function is used to get the length of a map in Go?
5.  What do you understand by map comparison in Go?
6.  How to check whether a specific key exists in a map or not?

# [CHAPTER 16](#toc.xhtml#c16)

# [Concurrency with Go](#toc.xhtml#c16)

**Concurrency** is an extremely important feature of Go that allows the execution of multiple tasks at the same time. In Golang, Goroutines and channels make concurrency possible. Let’s go ahead with learning about it in this chapter.

# [Structure](#toc.xhtml#s172a)

In this chapter, we will discuss the following topics:

*   Introduction to concurrency
*   How parallelism is different from concurrency
*   Goroutines
*   Waiting for Goroutine to finish

# [Objectives](#toc.xhtml#s173a)

After studying this chapter, you’ll be able to:

*   Understrand the key concept of Goroutines
*   Run multiple processes simultaneously
*   Write an efficient code in Go

# [Introduction](#toc.xhtml#s174a)

While creating large applications, it becomes necessary not to wait for any process to complete. Concurrency allows running different parts of a program in an overlapping period without affecting the outcome of a program. It prevents the issues that occur while updating the data by two different processes at a time. For example, banking allows more than one transaction at the same time; or it allows access to the same data from multiple sources at a time. Golang facilitates concurrency with Goroutines and channels. Concurrency is quite similar to the thread that is used in C++, Java, or Python.

# [How parallelism is different from concurrency](#toc.xhtml#s175a)

Running multiple things in parallel at the same time is called **parallelism**. The multicore processor makes parallelism possible. The CPU’s multiple cores run multiple processes at the same time. With concurrency, we run multiple processes but not at the same time. The CPU time is divided among multiple processes that need to run. The fluctuation between the processes is done so fast that it seems that all the different processes are running at the same time. In a single core processor, concurrency is achieved by "context-switching" that divides the time for each process and executes it.

# [Thread](#toc.xhtml#s176a)

**Thread** is a sub-task of a process. A process can be divided into multiple threads that share the same address space and execute independently. Threads have their own register set and stack to perform various operations. Threads allow the maximum CPU utilization and thus, increase the performance of CPU. A thread belongs to the same process and the data within memory can be shared by all the threads. Threads are the sources of concurrency. In single-core processor, each sub-task behaves like a thread and concurrency is achieved by switching between the threads.

# [Goroutines](#toc.xhtml#s177a)

**Goroutines** are ordinary methods or functions with some additional features. Goroutines can be executed concurrently with other methods. Every concurrently running method or function is called a Goroutine in the Go language. Goroutines are called light-weighted threads as they exist in the Go runtime virtual space. Every Go program contains at least one Goroutine. As each Go program contains the main method, it is itself a Goroutine that runs independently. The main method is a root Goroutine; all other Goroutines are executed within the main. Once the compiler reaches the end of the `main` function, it terminates all the created Goroutines. Like threads, all Goroutines run in the same address space in any Go program. With Goroutines, the size of the stack varies according to the need of the program while in thread, the stack size is fixed leading to memory leakage.

Golang has the specific keyword `go` to declare a function as a Goroutine.

`go name_of_function()`

In the following example, we create a function `show_value` that prints the value up to a specific range and after calling this function, we show a message that says that we have called the function.

**Example:**

`func show_value(i int){`

`for i<10{`

`fmt.Println(i)`

`i = i+1`

`}`

`}`

`func main() {`

`show_value(0)`

`fmt.Println("We have called the function")`

`}`

**Output:**

`0`

`1`

`2`

`3`

`4`

`5`

`6`

`7`

`8`

`9`

`We have called the function`

Here, we see that it shows a message when it returns from a function. Suppose we don’t want that and we need to display a message early so that a user can understand that a function is being called. We can use that function as a Goroutine. In such a case, it won’t wait for the function `show_value` to return and will execute the next statement, followed by a Goroutine.

**Example:**

`package main`

`import "fmt"`

`func show_value(i int){`

`for i<10{`

`fmt.Println(i)`

`i = i+1`

`}`

`}`

`func main() {`

`go show_value(0)`

`fmt.Println("We have called the function")`

`}`

**Output:**

`We have called the function`

We can see now that the only message we get is in output but not the values that we are trying to display within a function. The function has executed well but since we used Goroutines in the above example, it will call the Goroutines and then start executing the next statement defined after the Goroutine. So, after calling the Goroutine, it prints a message and then gets the closing block of the main function. On terminating from the main function, all Goroutines are terminated and thus, the execution of `show_value` also gets terminated. Here, to overcome this issue, we can use the `Scanln` function that waits for an input value. Till that time, the execution of Goroutine will take place.

**Example:**

`package main`

`import "fmt"`

`func show_value(i int){`

`for i<10{`

`fmt.Println(i)`

`i = i+1`

`}`

`}`

`func main() {`

`go show_value(0)`

`fmt.Println("We have called the function")`

`fmt.Scanln()`

`}`

**Output:**

`We have called the function`

`0`

`1`

`2`

`3`

`4`

`5`

`6`

`7`

`8`

`9`

We can use a function as a Goroutine or ordinarily in a single program. It depends on the way the function calls. In the following example, we call the method `show_value` as a Goroutine and then the standard method is being called. The output explains how the execution is done.

**Example:**

`package main`

`import ("fmt"`

`"time"`

`)`

`func show_value(i int){`

`for i<10{`

`fmt.Println(i)`

`time.Sleep(200 * time.Millisecond)`

`i = i+1`

`}`

`}`

`func main() {`

`go show_value(0)`

`fmt.Println("We have called a goroutine")`

`show_value(0)`

`fmt.Println("We have called a function")`

`}`

**Output:**

`We have called a goroutine`

`0`

`0`

`1`

`1`

`2`

`2`

`3`

`3`

`4`

`4`

`5`

`5`

`6`

`6`

`7`

`7`

`8`

`8`

`9`

`9`

`We have called a function`

# [Multiple Goroutines](#toc.xhtml#s178a)

We can execute multiple Goroutines in a single program without affecting any other Goroutine. Here is an example of running multiple Goroutines in a program:

**Example:**

`package main`

`import ("fmt"`

`"time"`

`)`

`func show_value(i int){`

`for i<10{`

`fmt.Println(i)`

`time.Sleep(200 * time.Millisecond)`

`i = i+1`

`}`

`}`

`func show_value1(c int){`

`for c<110{`

`fmt.Println(c)`

`time.Sleep(200 * time.Millisecond)`

`c = c+1`

`}`

`}`

`func main() {`

`go show_value(0)`

`fmt.Println("We have called a goroutine show_value")`

`go show_value1(100)`

`fmt.Println("We have called a goroutine show_value1")`

`fmt.Scanln()`

`}`

**Output:**

`We have called a goroutine show_value`

`We have called a goroutine show_value1`

`100`

`0`

`1`

`101`

`2`

`102`

`3`

`103`

`104`

`4`

`105`

`5`

`6`

`106`

`107`

`7`

`8`

`108`

`9`

`109`

# [Goroutines at multiple cores](#toc.xhtml#s179a)

In the Go language, we can fix the number of CPU cores to run Goroutines in a program. There are various ways to run Goroutines on multiple cores of a system. Go provides an environment variable `GOMAXPROCS` that defined the number of cores to be used in a program. This variable takes control at runtime in the Go program. In Go1.5, the default value of this variable is the number of cores. The system detects at start-up according to the running operating system.

# [Waiting for Goroutine to finish](#toc.xhtml#s180a)

In the previous example, we saw that the Goroutine gets terminated because it reaches the end of the main function. Go provides a synchronized mechanism for Goroutines by `WaitGroup` defined in the `sync` package. `WaitGroup` is a struct that contains a field `counter` to indicate the number of Goroutines that we need to wait for. It is used to wait for all the Goroutines to terminate. We have three basic methods that are used to track all the Goroutines that are called in a program.

*   `Add:` This method tells us how many Goroutines need to be waited.
*   `Done:` When a Goroutine terminates, it must call the "Done" method to indicate that the execution of the specific Goroutine has been done.
*   `Wait:` Wait method is used by the `main` Goroutine until the counter is greater than zero. When all the Goroutines get terminated and the counter is zero, the Wait function returns and continues the further execution.
    
    **Example:**
    
    `package main`
    
    `import ("fmt"`
    
    `"time"`
    
    `"sync"`
    
    `)`
    
    `func show_value(i int, wg *sync.WaitGroup){`
    
    `for i<10{`
    
    `fmt.Println(i)`
    
    `time.Sleep(200 * time.Millisecond)`
    
    `i = i+1`
    
    `}`
    
    `wg.Done()`
    
    `}`
    
    `func show_value1(c int, wg *sync.WaitGroup){`
    
    `for c<110{`
    
    `fmt.Println(c)`
    
    `time.Sleep(200 * time.Millisecond)`
    
    `c = c+1`
    
    `}`
    
    `wg.Done()`
    
    `}`
    
    `func main() {`
    
    `var wg sync.WaitGroup`
    
    `wg.Add(2)`
    
    `go show_value(0, &wg)`
    
    `fmt.Println("We have called a goroutine show_value")`
    
    `go show_value1(100, &wg)`
    
    `fmt.Println("We have called a goroutine show_value1")`
    
    `wg.Wait()`
    
    `fmt.Println("Done")`
    
    `}`
    
    **Output:**
    
    `We have called a goroutine show_value`
    
    `We have called a goroutine show_value1`
    
    `100`
    
    `0`
    
    `1`
    
    `101`
    
    `102`
    
    `2`
    
    `103`
    
    `3`
    
    `104`
    
    `4`
    
    `5`
    
    `105`
    
    `6`
    
    `106`
    
    `107`
    
    `7`
    
    `8`
    
    `108`
    
    `109`
    
    `9`
    
    `Done`
    

# [Conclusion](#toc.xhtml#s181a)

In this chapter, we saw how Golang provides flexibility to execute various tasks at the same time so that the time complexity can be reduced. We understand Goroutines and the necessary functions that we have in the Go language. After getting an idea of one of the concurrency constructs, that is, Goroutines, let’s move on to another construct called channel in the next chapter.

# [Questions](#toc.xhtml#s182a)

1.  How can we track Goroutines in Go?
2.  Does the main function work as a Goroutine in Go programs?
3.  What do you understand by WaitGroup?
4.  What is the use of the wait method? Specify with an example.
5.  What is GOMAXPROCS in Go?

# [CHAPTER 17](#toc.xhtml#c17)

# [Mutex and Channels](#toc.xhtml#c17)

**Channels** are like pipelines that connect to concurrently running Goroutines. In the language, a channel has a specific type and that type of values it can transport from one Goroutine to another. Go provides a channel operator through which we can send and receive the data through channels. A **channel operator** is used to sending and receive the data between two channels.

# [Structure](#toc.xhtml#s183a)

In this chapter, we will discuss the following topics:

*   Declaring channels
*   Channel operations
*   Deadlock
*   Closing a channel
*   The direction of a channel
*   Select keyword
*   Data race in Go
*   Mutex

# [Objectives](#toc.xhtml#s184a)

After studying this chapter, you’ll be able to:

*   Perform data sending/receiving operations between Goroutines
*   Work with channels in Go
*   Get an understanding of deadlock
*   Understand the idea of select keyword with channels
*   Understanding Golang lock/unlock concept through a mutex

# [Declaring channels](#toc.xhtml#s185a)

In the Go language, we can declare a channel in two ways, using `var` or `make` method. The `var` keyword reserves the memory for the named variables of a specified type and initializes them with the type’s default value. If we declare a channel variable using the `var` keyword, it creates a nil channel. Declaring a channel with the `make` method also reserves space in storage, initializes memory, and creates an underlying header of a specific type.

**Syntax:**

`var name_of_channel chan type_of_channel`

Or

`Name_of_channel := make(chan type_of_channel)`

**Example:**

`func main(){`

`var ch1 chan int`

`fmt.Println("channel with 'var' keyword:", ch1)`

`ch2 := make(chan string)`

`fmt.Println("channel with 'make' method:", ch2)`

`}`

**Output:**

`channel with 'var' keyword: <nil>`

`channel with 'make' method: 0x1180e180`

In the example given above, channel `ch1` and `ch2` transport integer and string type of data between channels. `ch1` is declared with `var` keyword that initializes it with the default value nil. We cannot transfer the data using nil channels. Therefore, in Go language, channels are mostly declared with the make method. The "make" method provides easy to use channels and returns a value of a specified type. By default, channels are pointers but there is no need to dereference them to access the data.

# [Channel operations](#toc.xhtml#s186a)

Golang facilitates various channel operations as given below:

*   **Send operation with channels**
    
    The send operation sends the data of a specified type to a channel variable. The send operation blocks the channels until no channel is ready to receive the data. While sending data, it first checks for a channel that is ready to receive the data.
    
    **Example:**
    
    `func main(){`
    
    `ch := make(chan int)`
    
    `ch<- 8`
    
    `fmt.Println(ch)`
    
    `}`
    
    The example given above will show an error. Statement `ch<- 8` blocks the channel as no channel is ready to receive the data.
    
*   **Receive operation in channel**
    
    By performing the receive operation, we can get the data from a channel to a variable. While receiving the data from channels, we get two values. The first is the data that a channel sends and the other one indicates the status that whether an operation is successful or not. The idiom for the second value is ok. The value of `ok` variable is `true` if the data is received successfully from the channel and `false` if the channel is closed or empty.
    
    **Example:**
    
    `package main`
    
    `import "fmt"`
    
    `func show_value(c chan int){`
    
    `c <- 8`
    
    `}`
    
    `func main(){`
    
    `c := make(chan int)`
    
    `go show_value(c)`
    
    `a, ok := <-c`
    
    `fmt.Println("value received from channel:", a)`
    
    `fmt.Println("status of operation is:", ok)`
    
    `}`
    
    **Output:**
    
    `value received from channel: 8`
    
    `status of operation is: true`
    
    In the example given above, we are using the Goroutine `show_value` that sends a value to a channel. After calling the Goroutine, a channel is sending the data and on the next line, the channel is ready to receive the data in the main function. As the operation is successful, true is assigned to an ok variable. The sending and receiving channel should be of the same type otherwise the compiler will show an error.
    
    If we execute the same program with the channels declared using the `var` keyword, it will give an error.
    
    **Example:**
    
    `func show_value(c chan int){`
    
    `c <- 8`
    
    `}`
    
    `func main(){`
    
    `var c chan int`
    
    `go show_value(c)`
    
    `a, ok := <-c`
    
    `fmt.Println("value received from channel:", a)`
    
    `fmt.Println("status of operation is:", ok)`
    
    `}`
    
    **Output:**
    
    `error “ [chan send <nil chan>] ”`
    
    We have observed that the send operation blocks a channel if no channel is ready to receive the data. So, we perform the receive operation to avoid such an issue. To overcome such scenarios, we can use buffered channels in Go programs. The following describes buffered and unbuffered channels briefly.
    
*   **Unbuffered channel**
    
    By default, channels are **unbuffered** in the Go language. Such channels accept the send operation if there is a channel ready to receive the data. We saw in the previous examples that on sending data without any corresponding receiver, the compiler gives an error.
    
*   **Buffered channel**
    
    **Buffered channels** can send specified number of values without any corresponding receiver. They store the values sent by a channel in a buffer and return when a corresponding channel is ready to receive the data. The number of values that is allowed to send without any receiver is called the capacity of a channel. The following is the syntax to create buffered channels in the Go language.
    
    **Syntax:**
    
    `name_of_channel := make(chan type_of_channel, capacity_of_channel)`
    
    **Example:**
    
    `func main(){`
    
    `ch := make(chan int, 2)`
    
    `ch<- 8`
    
    `a := <-ch`
    
    `fmt.Println(ch, a)`
    
    `}`
    
    **Output:**
    
    `0x1183c0c0 8`
    
    In the example given above, the capacity of the buffered channel is 2 which indicates that it can send maximum 2 values without waiting for a receiver channel. We can send the second value as shown below:
    
    **Example:**
    
    `func main(){`
    
    `ch := make(chan int, 2)`
    
    `ch<- 8`
    
    `ch<- 99`
    
    `a := <-ch`
    
    `b := <- ch`
    
    `fmt.Println(a, b)`
    
    `}`
    
    **Output:**
    
    `8 99`
    
    In the example given above, it stores the values in a buffer and returns to the corresponding receiver when the channel is ready to receive the data. We can receive the data from two or multiple channels in the same line as shown below:
    
    `a, b := <-ch, <-ch`
    
    In the above program, on sending the third value without a corresponding receiver channel, it will give an error as the capacity of the channel is 2.
    
*   **Find the capacity of the channel**
    
    Golang provides a function cap to get the capacity of a channel. The following example illustrates the use of the cap function with channels.
    
    **Example:**
    
    `func main(){`
    
    `ch := make(chan int, 2)`
    
    `cap_ch := cap(ch)`
    
    `fmt.Println("Capacity of channel is:", cap_ch)`
    
    `for itr := 1; itr<=cap_ch; itr++{`
    
    `ch<- itr*2`
    
    `fmt.Println("value received from channel is:", <-ch)`
    
    `}`
    
    `}`
    
    **Output:**
    
    `Capacity of channel is: 2`
    
    `value received from channel is: 2`
    
    `value received from channel is: 4`
    

# [Deadlock](#toc.xhtml#s187a)

In the previous examples, we saw that on sending data, it waits for a channel that is ready to receive the data. If it doesn’t find any receiver channel, it blocks that Goroutine and passes the control to other Goroutines to run. When it finds the receiver channel in another Goroutine, it unblocks the send operation and runs that Goroutine.

In such cases, if we don’t get any receiver channel in another Goroutins or there is no other Goroutine available in the program, the compiler imagines that all the Goroutines are asleep. The send operation remains blocked until the end of the program. Such a situation is called a deadlock.

The deadlock can occur in two ways depending on the operation that is being blocked.

On sending the data to a channel, it blocks the current Goroutine and schedules other Goroutines with the hope of getting a receiver channel. Here, the "sending operation is getting blocked." On receiving the data from a channel, it checks for an existing value in a channel. If a channel contains no value, it blocks the receive operation until it doesn’t get any value in that channel. So here, the "receive operation is getting blocked." In the Go language, a deadlock occurs if we have at least one blocked operation and no other Goroutine is available to schedule in a program. In such a case, the program crashes and the compiler shows an error. The following example explains a deadlock.

**Example:**

`package main`

`import "fmt"`

`func show(){`

`fmt.Println("Hello")`

`}`

`func main(){`

`str_ch := make(chan string)`

`go show()`

`str_ch<- "Hello world"`

`fmt.Println("Send operation is getting blocked")`

`}`

**Output:**

`Hello`

`fatal error: all goroutines are asleep – deadlock!`

`goroutine 1 [chan send]`

In the example given above, we are calling Goroutines then trying to send a value to a channel. It blocks the send operations as there is no other channel to receive the data. After blocking the main Goroutines, there is no other Goroutine to schedule. Hence, the deadlock occurs.

**Example:**

`package main`

`import "fmt"`

`func show(){`

`fmt.Println("Hello world")`

`}`

`func main(){`

`str_ch := make(chan string)`

`go show()`

`a := <- str_ch`

`fmt.Println("Receive operation is getting blocked", a)`

`}`

**Output:**

`Hello`

`fatal error: all goroutines are asleep – deadlock!`

`goroutine 1 [chan receive]`

In the example given above, after calling `showGoroutine`, we are trying to receive a value from the channel `str_ch`, but no value has been assigned to a channel till now. So, it blocks the current main Goroutine. As it continues, it finds that there is no other Goroutine to schedule. In such a case, a deadlock occurs and the compiler gives a fatal error.

*   **Using multiple Goroutines**
    
    A Go program can have multiple Goroutines with sharing values. Go defines the concept as "Do not communicate by sharing memory. Instead, share memory by communicating."
    
    **Example:**
    
    `package main`
    
    `import "fmt"`
    
    `func square(num_ch chan int){`
    
    `value := <-num_ch`
    
    `sqr_val := value*value`
    
    `num_ch<- sqr_val`
    
    `}`
    
    `func cube(num_ch chan int){`
    
    `value := <-num_ch`
    
    `cube_val := value*value*value`
    
    `num_ch<- cube_val`
    
    `}`
    
    `func main(){`
    
    `num := make(chan int) // 1`
    
    `go square(num) // 2`
    
    `num<- 3 // 3`
    
    `sqr_val := <-num // 4`
    
    `go cube(num) // 5`
    
    `num<- 3 // 6`
    
    `cube_val := <-num // 7`
    
    `fmt.Println("Square of value:", sqr_val) // 8`
    
    `fmt.Println("Cube of value:", cube_val) // 9`
    
    `}`
    
    **Output:**
    
    `Square of value: 9`
    
    `Cube of value: 27`
    
*   First, we are creating a channel called "num" that passes an integer type of value.
*   In the second line, we call the "square" goroutine. In this Goroutine, we are trying to get the value from a channel. But since no value has been assigned to a channel till now, it blocks the receive operation and control is passed to the "main" Goroutine.
*   In the third line, we pass "3" to a channel that further executes the receive operation in the square Goroutine. Then, the final value is passed to a channel called ‘num\_ch’ in the Goroutine.
*   In the fourth line, the channel is ready to receive a value that is sent by the "square" goroutine. Thus, we get a square of 3.
*   In the same way, we get a cube of value in line 5, 6, and 7.

# [Closing a channel](#toc.xhtml#s188a)

While programming, there may be an instance where after creating a channel, we do not want to use it further in our Go program. In such a case, Go provides a method to close a channel that indicates that no value will be sent through a channel. The `close` function is used to close a channel.

While receiving the value from a channel, we can get the status of a channel. It will return true if a channel is open and the receive operation is successful; otherwise, it will return false if a channel is closed.

**Example:**

`package main`

`import "fmt"`

`func cube(value chan int){`

`fmt.Println("In cube goroutine")`

`val := <-value`

`value <- val*val*val`

`}`

`func square(value chan int){`

`fmt.Println("In square goroutine")`

`val := <-value`

`fmt.Println(val)`

`value <- val*val`

`}`

`func main(){`

`num := make(chan int)`

`go square(num)`

`num<- 3`

`sqr_val := <-num`

`go cube(num)`

`num<- 3`

`close(num)`

`cube_val, ok := <-num`

`fmt.Println("Square of value:", sqr_val)`

`fmt.Println("Cube of value:", cube_val, ok)`

`}`

**Output:**

`In square Goroutine`

`3`

`In cube goroutine`

`Square of value: 9`

`Cube of value: 0`

`Panic: send on closed channel`

In the example given above, after calling the cube Goroutine we passed a value to the num channel. Before we received the final value from the channel sent by the cube Goroutine, we closed that channel. This situation lead to a runtime panic. On receiving a value from a closed channel, it returns zero without any error and assigns false to an ok variable.

# [The direction of a channel](#toc.xhtml#s189a)

In the previous examples, we have seen that we can perform, read and write both operations on a channel. By default, Go provides a bidirectional nature of channels.

We can also create unidirectional channels in the Go language that either allow the read operation or receive operation.

The syntax of declaring the unidirectional channel is as follows:

**Receive only channel**

`name_of_channel := make(<- chanint)`

**Send only channel**

`name_of_channel := make(chan -<int)`

Here is an example of send only channel below:

**Example:**

`package main`

`import ("fmt"`

`"sync"`

`)`

`var wg sync.WaitGroup`

`func square(value chan<- int){`

`fmt.Println("defining send only goroutine")`

`val := value`

`fmt.Println(val)`

`wg.Done()`

`}`

`func main(){`

`send_ch := make(chan<- int, 1)`

`wg.Add(1)`

`go square(send_ch)`

`send_ch<- 3`

`wg.Wait()`

`}`

**Output:**

`defining send only Goroutine`

`0x1183c0c0`

In the example given above, we have defined a send only unidirectional channel `send_ch` that only sends a value to a channel. We cannot receive value from such channels. On receiving value from such channels, the compiler gives an error as shown below:

**Example:**

`package main`

`import ("fmt"`

`"sync"`

`)`

`var wg sync.WaitGroup`

`func square(value chan<- int){`

`fmt.Println("defining send only goroutine")`

`val := value`

`fmt.Println(val)`

`val<- value`

`wg.Done()`

`}`

`func main(){`

`send_ch := make(chan<- int, 1)`

`wg.Add(1)`

`go square(send_ch)`

`send_ch<- 3`

`wg.Wait()`

`}`

**Output:**

`Cannot use value <type chan<- int> as type int in send`

In the same way, we can declare receive only channels in the Go language. An example of receiving only channels is shown below:

**Example:**

`package main`

`import ("fmt"`

`"sync"`

`)`

`var wg sync.WaitGroup`

`func square(value <-chan int){`

`fmt.Println("defining receive only goroutine")`

`val := <-value`

`fmt.Println(val)`

`wg.Done()`

`}`

`func main(){`

`receive_ch := make(<-chan int)`

`wg.Add(1)`

`go square(receive_ch)`

`wg.Wait()`

`}`

In the example given above, we created a receive only channel `receive_ch` and called squareGoroutine. Here, we are trying to receive a value from a channel. As there is no value in the channel, it blocks the receive operation and the compiler gives an error "deadlock." We can see the solution to this issue in the next program. We can convert a bidirectional channel to unidirectional for a specific Goroutine.

**Example:**

`package main`

`import "fmt"`

`func receive(receive_ch chan<- int, val int) {`

`receive_ch<- val`

`}`

`func square(receive_ch<-chan int, send_ch chan<- int){`

`fmt.Println("defining send only goroutine")`

`val := <- receive_ch`

`send_ch<- val`

`}`

`func main(){`

`send_ch := make(chan int, 1)`

`receive_ch := make(chan int,1)`

`receive(receive_ch, 6)`

`square(receive_ch, send_ch)`

`fmt.Println(<-send_ch)`

`}`

**Output:**

`defining send only Goroutine`

`6`

# [The select keyword](#toc.xhtml#s190a)

**Select** is used for network communication or to wait for multiple channel operations. The select statement is like a switch that works with multiple cases. With the select statement, the case refers to the channel’s send/receive operation. Select waits for a specific case until it to ready to perform the operation specified in a particular case statement. If no case is defined within a select statement, then it will lead to a deadlock since it didn’t get any case for channel communication. The select statement gets blocked if no case statement is ready to execute. In the case of blocking, it waits for a case that is ready to perform a channel operation. To avoid select blocking, it can have a default case like a switch statement. If no case statement is ready to perform the communication, it proceeds with the default case. If the select statement has multiple cases that are ready to perform the specified channel operation, it selects any random case statement and executes it.

The syntax of the select statement is the same as the switch statement except for the case statement. Here, the case statement defines a channel operation.

**Syntax:**

`select{`

`case send_receive_operation1:`

`// body of case statement 1`

`case send_receive_operation2:`

`// body of case statement 2`

`……`

`……`

`}`

Multiple examples of the select statement that describe the use of the select statement in different ways are as given below.

**Example:**

`package main`

`import ("fmt"`

`"time"`

`)`

`func square(num_ch chan int){`

`value := <-num_ch`

`sqr_val := value*value`

`time.Sleep(5*time.Second)`

`num_ch<- sqr_val`

`}`

`func cube(num_ch chan int){`

`value := <-num_ch`

`cube_val := value*value*value`

`time.Sleep(10*time.Second)`

`num_ch<- cube_val`

`}`

`func main(){`

`sqr_ch := make(chan int)`

`go square(sqr_ch)`

`sqr_ch<- 3`

`cube_ch := make(chan int)`

`go cube(cube_ch)`

`cube_ch<- 5`

`select{`

`case sqr_val := <-sqr_ch:`

`fmt.Println("square of a value is:", sqr_val)`

`case cube_val := <-cube_ch:`

`fmt.Println("Cube of a value is:", cube_val)`

`}`

`}`

**Output:**

`square of a value is: 9`

In the example given above, we have two Goroutines, `square` and `cube`. We are calling both of them by passing a channel value from the main Goroutine. The select statement has two cases. In the first case, receive the value from the channel `sqr_ch` that is sent by the `square` goroutine. In the second case, we receive the value from channel `cube_ch` that is sent by the cube goroutine. In the square goroutine, we have given sleep time for 5 seconds and 10 seconds for the cube goroutine so that the square goroutines will finish its execution first. As the square Goroutine finishes its execution, it will send the value to a channel and `case1` would be ready to execute in the select statement. The select statement executes that case and comes out of its block.

In the example given above, we saw that only one case was ready to execute at a time. The following is an example where both cases are ready to execute at the same time.

**Example:**

`package main`

`import ("fmt"`

`"time"`

`)`

`func square(num_ch chan int){`

`value := <-num_ch`

`sqr_val := value*value`

`time.Sleep(1*time.Second)`

`num_ch<- sqr_val`

`}`

`func cube(num_ch chan int){`

`value := <-num_ch`

`cube_val := value*value*value`

`time.Sleep(1*time.Second)`

`num_ch<- cube_val`

`}`

`func main(){`

`sqr_ch := make(chan int)`

`go square(sqr_ch)`

`sqr_ch<- 3`

`cube_ch := make(chan int)`

`go cube(cube_ch)`

`cube_ch<- 5`

`select{`

`case sqr_val := <-sqr_ch:`

`fmt.Println("square of a value is:", sqr_val)`

`case cube_val := <-cube_ch:`

`fmt.Println("Cube of a value is:", cube_val)`

`}`

`}`

**Output:**

`Cube of a value is: 125`

`Or square of a value is: 9`

Here, the sleep time for both the Goroutines is the same (1 second). So, both the cases would be ready to execute at the same time. In such a case, the select statement randomly picks the case and executes it. The output of this program varies on executing it again and again.

Now, it could be possible that the select statement didn’t find any case statement to execute.

**Example:**

`package main`

`import ("fmt"`

`"time"`

`)`

`func square(num_ch chan int){`

`_ = <-num_ch`

`time.Sleep(1*time.Second)`

`}`

`func cube(num_ch chan int){`

`_ = <-num_ch`

`time.Sleep(1*time.Second)`

`}`

`func main(){`

`sqr_ch := make(chan int)`

`go square(sqr_ch)`

`sqr_ch<- 3`

`cube_ch := make(chan int)`

`go cube(cube_ch)`

`cube_ch<- 5`

`select{`

`case sqr_val := <-sqr_ch:`

`fmt.Println("square of a value is:", sqr_val)`

`case cube_val := <-cube_ch:`

`fmt.Println("Cube of a value is:", cube_val)`

`}`

`}`

**Output:**

`Fatal error: all goroutines are asleep – deadlock!`

`goroutine 1 [select]`

In this case, we sent the value to channels that are received by Goroutines. Now, in both the case statements, we are trying to receive the value from a channel, but the channel doesn’t have any value. As the select statement doesn’t find any ready case statement here, it blocks the select statement and also leads to a deadlock.

To avoid a deadlock, we can add the default statement in select that proceeds the execution if select doesn’t find any ready case statement.

**Example:**

`package main`

`import ("fmt"`

`"time"`

`)`

`func square(num_ch chan int){`

`_ = <-num_ch`

`time.Sleep(1*time.Second)`

`}`

`func cube(num_ch chan int){`

`_ = <-num_ch`

`time.Sleep(1*time.Second)`

`}`

`func main(){`

`sqr_ch := make(chan int)`

`go square(sqr_ch)`

`sqr_ch<- 3`

`cube_ch := make(chan int)`

`go cube(cube_ch)`

`cube_ch<- 5`

`select{`

`case sqr_val := <-sqr_ch:`

`fmt.Println("square of a value is:", sqr_val)`

`case cube_val := <-cube_ch:`

`fmt.Println("Cube of a value is:", cube_val)`

`default:`

`fmt.Println("No case statement is ready to execute!")`

`}`

`}`

**Output:**

`No case statement is ready to execute!`

Here is an example where the select statement doesn’t have any case for channel communication.

**Example:**

`func main(){`

`select{`

`}`

`}`

**Output:**

`Fatal error: all goroutines are asleep – deadlock!`

`goroutine 1 [select <no cases>]`

With this blank select statement, the compiler will give a fatal error and lead to a deadlock.

We saw that a maximum of one case is executed with a select statement at a time. We can execute multiple cases by repeatedly checking if a case is ready to execute.

**Example:**

`package main`

`import ("fmt"`

`"time"`

`)`

`func square(num_ch chan int){`

`value := <-num_ch`

`sqr_val := value*value`

`time.Sleep(5*time.Second)`

`num_ch<- sqr_val`

`}`

`func cube(num_ch chan int){`

`value := <-num_ch`

`cube_val := value*value*value`

`time.Sleep(10*time.Second)`

`num_ch<- cube_val`

`}`

`func main(){`

`sqr_ch := make(chan int)`

`go square(sqr_ch)`

`sqr_ch<- 3`

`cube_ch := make(chan int)`

`go cube(cube_ch)`

`cube_ch<- 5`

`for itr := 1; itr<= 2; itr++{`

`select{`

`case sqr_val := <-sqr_ch:`

`fmt.Println("square of a value is:", sqr_val)`

`case cube_val := <-cube_ch:`

`fmt.Println("Cube of a value is:", cube_val)`

`}`

`}`

`}`

**Output:**

`square of a value is: 9`

`Cube of a value is: 125`

Here, we are executing the select statement two times as we have two cases in the `select` statement. Since the square Goroutine has less sleep time, it will finish its execution first and case1 would be ready to execute. So, a select statement first executes `case1`. On the second time, it finds `case2` that is ready to execute. In this way, the select statement waits for the Goroutine to finish its execution and proceeds with the specified case.

Golang provides the facility to build concurrent programs that sometimes lead to unexpected behavior. Concurrency comes with multiple bugs that are quite hard to debug. The following defines some possible unexpected situations and how to detect and solve them.

# [Data race in Go](#toc.xhtml#s191a)

**Data race** can be defined by a situation where two or multiple threads concurrently access the same memory location and perform at least one write operation. It occurs with the execution of multi-threading programming. The following example defines data race in Go language.

**Example:**

`package main`

`import "fmt"`

`var value = 45`

`func update_value(){`

`if(value==45){`

`value++`

`}`

`fmt.Println(value)`

`}`

`func main(){`

`go update_value() //gr1`

`go update_value() //gr2`

`}`

In the example given above, we have two Goroutines, (`gr1` and `gr2`) and both are accessing the same variable value to update its value. There could be three cases with this program. It depends on the order of execution of the Goroutines `gr1` and `gr2.`

**Case 1:** `gr1` first reads the data and then updates the value according to a specific condition. After the execution of `gr1`, `gr2` reads the data checks for the conditions and updates the data. Here, the order of the Goroutines is synchronized. No concurrent process is running here; the program will provide an accurate result.

 
| `Read_gr1` || `Write_gr1` || `Read_gr2` || `Write_gr2` |
| --- | --- | --- | --- |

**Case 2:** Here, `gr1` first reads the data and then `gr2` reads the data. So, both the Goroutines will read the value 45 in this case. After that `gr1` and `gr2` write a value as the condition is satisfied with both the Goroutines. Here, the the execution goes wrong and gets an unexpected result.

 
| `Read_gr1` || `Read_gr2` || `Write_gr1` || `Write_gr2` |
| --- | --- | --- | --- |

**Case 3:** Here, `gr1` first reads the data and then `gr2` reads the data. So, both the Goroutines will read the value 45 in this case. After that, `gr2` and `gr1` write a value as the condition gets satisfied with both the Goroutines. Here, the execution goes wrong and there is an unexpected result.

 
| `Read_gr1` || `Read_gr2` || `Write_gr2` || `Write_gr1` |
| --- | --- | --- | --- |

# [Race condition](#toc.xhtml#s192a)

A **race condition** is a feature of a program or system that can lead to an unexpected result. A race condition occurs when two or multiple operations are performed at the same time in a program or system. Due to incorrect timing or ordering of operation, it leads to the crash of a program. A race condition is different from a data race. It is not necessary that if a program has a race condition, it must be because of a data race. A program can have a race condition but not a data race.

The following is an example where a data race doesn’t exist but it defines a race condition.

**Example:**

`Thread 1         Thread2`

`lock(1)           lock(1)`

`value = 1         value = 2`

`unlock(1)         unlock(1)`

In the example given above, we used a lock before updating the value of a variable to synchronize the process. There would never be any concurrent process, so data race doesn’t exist here.

We can get race condition with such examples. As we don’t know the order of execution for these threads, it’s hard to determine which process updates the value of a variable. The final value of a variable can be 1 or 2.

# [Check for data race](#toc.xhtml#s193a)

While working with multi-threading, it becomes necessary to protect a program from abnormal behavior to make the program reliable and scalable. Go language provides a "data race detector" tool that tracks all the operations related to static/dynamic memory access and how and when the memory is accessed in a program. Dynamic tracking is done for unsynchronized access to shared variables. This tool looks for a race condition. If a program has a race condition because of a data race, it prints a warning message. The Go race detector tool was introduced with the v1.1 version of Go, integrated with the Go toolchain. This tool supports Linux/amd64, Linux/ppc64le, linuxarm64, FreeBSD/amd64, NetBSD/amd64, Darwin/amd64, and windows/amd64.

To enable the race detector in a program, `-race` flag is raised while executing a program. We can raise the race flag in the following ways:

*   `go test –race package_name`
*   `go run –race program_name`
*   `go build –race command_name`
*   `go install –race package_name`

It is advisable to use a race detector if it is necessary as it consumes the CPU and memory ten times more. Also, we can say that with concurrency, data sharing between Goroutines must be properly synchronized to avoid such erroneous conditions.

# [Mutex](#toc.xhtml#s194a)

In the Go language, **Mutex** provides a mechanism to synchronize the data access between multiple goroutines. Mutex follows the concept of a mutual exclusion lock that allows only one Goroutine to access the memory at a time by the locking and unlocking mechanism.

Till now, we have used channels for synchronized communication between Goroutines. Although channels are also good as they have the built-in property of thread safety and prevent a race condition, it is advisable not to use channels in every situation. With a large application, a channel allows single thread access to memory but the performance penalty occurs with channels if less number of resources is shared between them. Channels and Mutex both have their pros and cons depending on the requirement and the way of programming.

Here, we are going to use the concept of **mutual exclusion lock**, provided by a data structure Mutex. Mutex is defined in the `sync` package available in the src directory. It has an interface locker that encapsulates the functionally of locking and unlocking by declaring two methods, `Lock` and `Unlock`. These two methods are implemented by the mutex struct type. Mutex defines these two methods to lock and unlock a block of code that is executed by only one Goroutine at a time. Data access is synchronized with Mutex by keeping a lock when a shared resource is being used so that no other Goroutine can use it. After using that shared resource, the lock is removed. It prevents race condition between multiple Goroutines if they are accessing the same memory space at a time.

Here is an example that shows how Mutex locks and unlocks a block of code and enables synchronized data access.

**Example:**

`package main`

`import ("fmt"`

`"sync"`

`)`

`type initial_amount struct{`

`amount int`

`sync.Mutex`

`}`

`func (ia *initial_amount) withdraw_amount(withdraw_val int){`

`ia.Lock()`

`ia.amount = ia.amount - withdraw_val`

`ia.Unlock()`

`}`

`func (ia *initial_amount) deposit_amount(deposit_val int){`

`ia.Lock()`

`ia.amount = ia.amount + deposit_val`

`ia.Unlock()`

`}`

`func (ia *initial_amount) get_balance() int {`

`val :=ia.amount`

`return val`

`}`

`func main(){`

`ia := initial_amount{amount: 2000}`

`for itr:= 1; itr<=10; itr++{`

`go ia.deposit_amount(500)`

`go ia.withdraw_amount(300)`

`}`

`final_amount := ia.get_balance()`

`fmt.Println("Final balance is:",final_amount)`

`}`

**Output:**

`Final balance is: 4100`

In the program given above, we create a struct `initial_amount` that has two fields, `amount` and `Mutex`. The amount variable is shared between two Goroutines, `withdraw_amount` and deposit_amount. Here, Mutex is defined as a struct field that locks and unlocks the access to amount variable. `withdraw_amount` withdraws an amount and updates amount variable. Similarly, `deposit_amount` deposits an amount as specified and updates the same amount variable. Both Goroutines are called from the main Goroutine; they will run concurrently. In the `deposit_amount` goroutine, before updating the value of the "amount" variable, we use the lock method so that any other goroutine won’t be able to access the amount variable at the same time. When deposit_amount updates the value, it unlocks the resources to make them available for other Goroutines. In such a way, the access to the amount variable is synchronized.

When we run the above program with the race detector, it prints the output message with a `data race` warning that indicates the data race exists in the above program. In the `get_balace` method, we are accessing the same shared variable `amount` to read its value. While accessing this variable, the lock is being acquired either by `deposit_amount` or `withdraw_amount` method. We can prevent this warning by acquiring a lock before reading the value in `get_balance` method.

`func (ia *initial_amount) get_balance() int {`

`ia.Lock()`

`val := ia.amount`

`ia.Unlock()`

`return val`

`}`

Now run the program with the same race detector tool.

**Output:**

`Final balance is: 3800`

This time, the is quite different as it waits for some time to acquire a lock for the shared variable.

Also, it didn’t get any data race warning here. Now the question is of not getting the correct result.

The get\_balance method is being called before the termination of all Goroutines, so it returns the intermediate value of a variable. We can resolve this issue by using `WaitGroup` as shown below:

**Example:**

`package main`

`import ("fmt"`

`"sync"`

`)`

`var wg sync.WaitGroup`

`type initial_amount struct{`

`amount int`

`sync.Mutex`

`}`

`func (ia *initial_amount) withdraw_amount(withdraw_val int){`

`ia.Lock()`

`ia.amount = ia.amount - withdraw_val`

`ia.Unlock()`

`wg.Done()`

`}`

`func (ia *initial_amount) deposit_amount(deposit_val int){`

`ia.Lock()`

`ia.amount = ia.amount + deposit_val`

`ia.Unlock()`

`wg.Done()`

`}`

`func (ia *initial_amount) get_balance() int {`

`ia.Lock()`

`val := ia.amount`

`ia.Unlock()`

`return val`

`}`

`func main(){`

`ia := initial_amount{amount: 2000}`

`for itr:= 1; itr<=10; itr++{`

`wg.Add(1)`

`go ia.deposit_amount(500)`

`wg.Add(1)`

`go ia.withdraw_amount(300)`

`}`

`wg.Wait()`

`final_amount := ia.get_balance()`

`fmt.Println("final balance is:", final_amount)`

`}`

**Output:**

`final balance is: 4000`

# [RWMutex](#toc.xhtml#s195a)

Any thread either reads the data or modifies it. On performing a write operation, data sharing is not allowed with multiple Goroutines, whereas with a read operation, multiple Goroutines can read the data from the same memory space without any issue. Based on several operations, Golang provides a specific reader/writer Mutex that multiple readers and writers can behold. Like Mutex, **RWMutex** is also available in a sync package. RWMutex is a struct that contains various fields to track the memory access by multiple threads. RWMutex implements multiple methods that provide a specific type of lock/unlocking service.

*   **RLock()**
    
    It is used to acquire a lock rw for reading purpose. Multiple readers can acquire this lock in a single program. RLock is not bound with a specific thread.
    
*   **RUnlock()**
    
    This method releases the acquired lock for a single RLock call that doesn’t affect another running read operation. In the Go language, one thread may RLockrw another thread and it can release that.
    
*   **Lock()**
    
    It locks rw for writing purpose. This type of lock is acquired by only one thread at a time. If another thread acquires a lock for the reading/writing purpose, Lock blocks until the lock is available to acquire.
    
*   **Unlock()**
    
    This method unblocks rw to make it available for another writer thread. On executing Unlock without acquiring the lock, the compiler will give an error at runtime.
    
    There is a point to remember which is that we cannot contain Mutex and RWMutex both as struct field in a single program. In such a case, the compiler will give the error "ambiguous selector." The following example defines thread-safe maps with the use of RWMutex.
    
    **Example:**
    
    `package main`
    
    `import ("fmt"`
    
    `"sync"`
    
    `"time"`
    
    `)`
    
    `type Map_struct struct{`
    
    `map_val map[int] int`
    
    `sync.RWMutex`
    
    `}`
    
    `func (map_data *Map_struct) update_map(keyval int){`
    
    `map_data.Lock()`
    
    `map_data.map_val[keyval] = keyval * 10`
    
    `map_data.Unlock()`
    
    `}`
    
    `func (map_data *Map_struct) read_map(){`
    
    `map_data.RLock()`
    
    `val := map_data.map_val`
    
    `map_data.RUnlock()`
    
    `fmt.Println(val)`
    
    `}`
    
    `func main(){`
    
    `ia := Map_struct{map_val:make(map[int]int)}`
    
    `for itr:= 1; itr<10; itr++{`
    
    `go ia.update_map(itr)`
    
    `go ia.read_map()`
    
    `}`
    
    `time.Sleep(5 * time.Second)`
    
    `}`
    
    **Output:**
    
    `map[1:10 2:20]`
    
    `map[1:10 2:20]`
    
    `map[1:10 2:20 3:30]`
    
    `map[1:10 2:20 3:30 4:40]`
    
    `map[1:10 2:20 3:30 4:40 5:50]`
    
    `map[1:10 2:20 3:30 4:40 5:50 6:60]`
    
    `map[1:10 2:20 3:30 4:40 5:50 6:60 7:70]`
    
    `map[1:10 2:20 3:30 4:40 5:50 6:60 7:70 8:80]`
    
    `map[1:10 2:20 3:30 4:40 5:50 6:60 7:70 8:80 9:90]`
    

In the program given above, we create a struct `Map_struct` that has two fields, `map_val` and RWMutex object. Embedding of RWMutex object allows accessing multiple methods for `map_val`. In the main Goroutine, we initialize the struct and call Goroutines in a loop. Here, we have two Goroutines. read_map reads the map values and update_map modifies the map. `read_map` goroutine puts RLock to perform read operation, and after reading a map, it releases the lock using the `RUnlock`. Goroutine `update_map` acquires the lock for a write operation and after updating the map, it releases the lock using the `Unlock` method. We give time sleep for 5 seconds at the end of the main Goroutine so that all the running Goroutines can finish their execution till that time.

# [Conclusion](#toc.xhtml#s196a)

In this chapter, we got an overview of the channels in Go. We have learned how send/receive operations are performed by using channels in Golang. To avoid some restrictions, Go provides buffered and unbuffered channels that can be used as required. We have grasped here the idea of deadlock, channel direction, select keyword, and others. We have understood the lock/unlock mechanism with Mutex in Go. After getting a deeper understanding of Go, we know that there are multiple cases where we need to handle the errors that we get in Golang program. Let’s see in the next chapter how to handle errors in Go.

# [Questions](#toc.xhtml#s197a)

1.  What are the channels used in Go?
2.  What are the various ways to declare a channel in Go?
3.  How do channels work in Golang?
4.  Explain the use of select keyword with an example.
5.  What do you understand by the capacity of a channel?
6.  What is the difference between buffered and unbuffered channels?
7.  How can we create unidirectional channels?
8.  What is a deadlock in Golang?
9.  How can we close a channel in Go?
10.  What do you understand by Mutex in Go?

# [CHAPTER 18](#toc.xhtml#c18)

# [Error Handling](#toc.xhtml#c18)

**Error handling** is the process of detecting and handling an erroneous situation that can lead to the crash of a program. Compile-time errors occurr with the compilation of the program. Errors that occur at the execution of the program are called runtime errors. Opening a file that doesn’t exist in a directory is the best example of a runtime error. Error handling detects such runtime errors, represents and handles them as specified.

# [Structure](#toc.xhtml#s198a)

In this chapter, we will discuss the following topics:

*   Introduction to Golang errors
*   Error types
*   Errors package
*   Defer statement
*   Panic
*   Recovery

# [Objectives](#toc.xhtml#s199a)

After studying this chapter, you should be able to:

*   Identify abnormal conditions in code
*   Manage a possible error by "error" data type
*   Tackle errors in Go
*   Perform error wrapping, unwrapping, and formatting by using the "errors" package

# [Introduction](#toc.xhtml#s200a)

The Go language has a built-in `error` type to indicate an abnormal condition. The error type is used like other data types—store them in memory, pass them to any function, and many others. In other languages, we use try-catch or try-except for error handling but there is nothing like that here as the Go language doesn’t have exceptions. In Go, errors are handled either by multiple return values or by panic. The following is an example of trying to open a file that doesn’t exist which gives a runtime error.

We can open a file in the Go language with the following syntax:

`func Open(name string) (file *File, err error)`

**Example:**

`package main`

`import ("fmt"`

`"os"`

`)`

`func main(){`

`file, err := os.Open("./example.json")`

`fmt.Println("file status:", file)`

`fmt.Println("error status:", err)`

`}`

**Output:**

`file status: <nil>`

`error status: open ./example.json: The system cannot find the file specified.`

In the example given above, since the file doesn’t exist in the current directory, it returns `nil` instead of the file handler and an error message that occurs while opening a file. Let’s create a file named `example.json` in the current directory and run the program again. In this case, it finds the file and returns the file handler and `nil to err`. Here is the updated output after creating a specified file:

`file status: &{0x1185c420}`

`error status: <nil>`

To handle an error, we can compare the last return value `err to nil`. If the value of `err` is not `nil`, there is an error. If `err` is `nil`, the operation has been done successfully.

**Error type**

`error` is an interface type that contains a single method `Error` of return type string. The default value of the error type is `nil`. The error type is defined as shown below:

`type error interface{`

`Error() string`

`}`

Any type that implements the error interface is considered as an error.

**Example:**

`package main`

`import "fmt"`

`type My_error struct{}`

`func (error_object *My_error) Error() string{`

`return "Unexpected outcome"`

`}`

`func main(){`

`fmt.Println(&My_error{})`

`}`

**Output:**

`Unexpected outcome`

In the program given above, we create a `struct My_error` that has no field. `Struct My_error` is used to implement the `Error` method that returns an error message as a string. We can call an Error method directly in case of any error to find its output.

**Example:**

`package main`

`import "fmt"`

`type My_error struct{}`

`func (error_object *My_error) Error() string{`

`return "Unexpected outcome"`

`}`

`func main(){`

`obj := My_error{}`

`fmt.Println(obj.Error())`

`}`

# [Error package](#toc.xhtml#s201a)

Go has a built-in package called `errors` in the `src` directory. It implements various functions to manipulate errors. It has a function called New that is used to return an error of a specified format.

**Example:**

`package main`

`import ("fmt"`

`"os"`

`"errors"`

`)`

`func main(){`

`file, err := os.Open("./example.json")`

`if(err!=nil){`

`error_msg := errors.New("file operation failed")`

`fmt.Println(error_msg)`

`}`

`if(err==nil){`

`fmt.Println("file opened successfully", file)`

`}`

`}`

**Output:**

`file operation failed`

In the program given above, in the case of an error, we called the New function by passing an error message. This function accepts the error message as a string and returns it as an error type value. Here, the type of `error_msg` is *`errors.errorString` which points to `errors.errorString. errorString` is a struct type that has a string type of a field in the errors package. The struct type `errorString` implements the `Error` method and returns a string type of value. For a better understanding, you must have a look at the errors package in the `src` directory.

# [Defer statement](#toc.xhtml#s202a)

Execution of a specific code can be deferred until the surrounding function returns by using the `defer` statement. An expression in the `defer` statement must be a function call. The arguments passed in the `defer` statement are evaluated as the compiler finds a `defer` keyword, but the execution of the `defer` statement takes place at the end when the function returns. Multiple clean-up operations are performed in the `defer` statement such as closing the files if any file is open.

The defer statement works in the following ways:

*   The `defer` statement pushes a function into the stack that is executed in Last in the first out order. When the surrounding function returns, all functions are called that are stored in the stack. The function that is stored at the end in the stack is executed first.
*   The values passed in the `defer` function arguments are evaluated as the compiler finds the defer statement.
*   In `defer` functions, both the read and write operations can be performed.
*   Return values can be modified in defer functions.
    
    **Example:**
    
    `package main`
    
    `import ("fmt"`
    
    `"os"`
    
    `)`
    
    `func open_file(){`
    
    `defer file.Close()`
    
    `file, err := os.Open("./example.txt")`
    
    `fmt.Println("file status:", file)`
    
    `fmt.Println("error status:", err)`
    
    `}`
    
    `func main(){`
    
    `open_file()`
    
    `}`
    
    **Output:**
    
    `Error: undefined: file`
    
    The program given above has a function called open\_file. When the compiler starts the execution of `open_file`, it gets a `defer` statement. While evaluating the values, it doesn’t get the file object, so it gives an error. We can resolve this issue as shown below.
    
    **Example:**
    
    `package main`
    
    `import ("fmt"`
    
    `"os"`
    
    `)`
    
    `func open_file(){`
    
    `file, err := os.Open("./example.txt")`
    
    `defer file.Close()`
    
    `fmt.Println("file status:", file)`
    
    `fmt.Println("error status:", err)`
    
    `}`
    
    `func main(){`
    
    `open_file()`
    
    `}`
    
    **Output:**
    
    `file status: &{0x1186c420}`
    
    `error status: <nil>`
    
    The following is an example that explains that defer function calls are executed in the LIFO order. We can also execute the defer statement in a loop.
    
    **Example:**
    
    `package main`
    
    `import "fmt"`
    
    `func show_value(){`
    
    `for itr:=0; itr<=10; itr++{`
    
    `defer fmt.Println("value:", itr)`
    
    `}`
    
    `}`
    
    `func main(){`
    
    `show_value()`
    
    `}`
    
    **Output:**
    
    `value: 10`
    
    `value: 9`
    
    `value: 8`
    
    `value: 7`
    
    `value: 6`
    
    `value: 5`
    
    `value: 4`
    
    `value: 3`
    
    `value: 2`
    
    `value: 1`
    
    `value: 0`
    
    Here is another example in which defer is used to update the return value as shown below.
    
    **Example:**
    
    `package main`
    
    `import "fmt"`
    
    `func update_return_value() (i int) {`
    
    `defer func() {i = i+10}()`
    
    `return 1`
    
    `}`
    
    `func main(){`
    
    `fmt.Println("updated return value:", update_return_value())`
    
    `}`
    
    **Output:**
    
    `updated return value: 11`
    

# [Panic](#toc.xhtml#s203a)

**Panic** is another way of error handling. It is used to check for unexpected errors throughout the program. It is somehow similar to exception as it also occurs during runtime. It skips the execution of a function if it returns an error that shows unexpected behavior. Whenever a `Panic` function is called in any function, it stops the execution of that function, executes the defer statement which is given to handle that panic, returns to caller statement, and continues with further execution.

In Go, a runtime error also causes panic in some cases like in out-of-bound accesses, divide by zero, and many others.

**Syntax:**

`Panic (interface {})`

Panic accepts any value as an argument because the empty interface can accept any type of value.

**Example:**

`package main`

`import "fmt"`

`var result int`

`func op(a, b int) int {`

`result = a / b`

`return result`

`}`

`func main(){`

`result = op(10, 0)`

`fmt.Println("Completed")`

`}`

**Output:**

`panic: runtime error: integer divide by zero`

On executing the example shown above, it gives a panic that is caused by a runtime error on dividing a number by zero. When panic occurs, the program gets terminated immediately. We can call a `panic` function on a specific case when a program is showing unexpected behavior and set an error message as required.

**Example:**

`package main`

`import "fmt"`

`var result int`

`func op(a, b int) int {`

`if(b==0){`

`panic("Can't divide a number by zero!")`

`}`

`result = a/b`

`return result`

`}`

`func main(){`

`result = op(10, 0)`

`fmt.Println("Completed")`

`}`

**Output:**

`panic: Can't divide a number by zero!`

Here, everything remains the same but it shows an error message which is what we required. In the same way, panic can be initiated by calling a `panic` function with any possible erroneous condition or a situation that can show unexpected behavior.

**Example:**

`package main`

`import "fmt"`

`func show_value(max int){`

`for itr:=1; itr<=max; itr++{`

`if(itr==5){`

`panic("Not acceptable")`

`}`

`fmt.Println(itr)`

`}`

`}`

`func main(){`

`show_value(10)`

`fmt.Println("Completed")`

`}`

**Output:**

`1`

`2`

`3`

`4`

`panic: Not acceptable`

In the program given above, we do not want to show values more than 4. If a value greater than 4 is passed in a parameter, it prints the values up to 4; and when it comes to 5, it shows panic and stops further execution. In some cases, we might execute some clean-up or other necessary operation before the program terminates. The same can be done by using the defer function that executes after getting the panicking situation.

**Example:**

`package main`

`import "fmt"`

`var result int`

`func op_defer(){`

`fmt.Println("op defer function executed")`

`}`

`func main_defer(){`

`fmt.Println("main defer function executed")`

`}`

`func op(a, b int) int {`

`defer op_defer()`

`if(b==0){`

`panic("Can't divide a number by zero!")`

`}`

`result = a/b`

`return result`

`}`

`func main(){`

`defer main_defer()`

`result = op(10, 0)`

`fmt.Println("Completed")`

`}`

**Output:**

`op defer function executed`

`main defer function executed`

`panic: Can't divide a number by zero!`

# [Recovery](#toc.xhtml#s204a)

Go provides a built-in function called Recover that controls the panicking situation. In the Go language errors handling is done by using the recover function since try-catch, try-except, or other similar methods are used in other languages. In the example given above, we saw that the execution of a program terminates when a panic occurs. The `Recover` function is used inside the defer functions because only defer statements are executed after panicking. The value passed to panic is returned by the `recover` function. If there is no panic in the program, the `recover` function returns `nil.`

**Example:**

`package main`

`import "fmt"`

`var result int`

`func op_defer(){`

`fmt.Println("op defer function executed")`

`}`

`func main_defer(){`

`fmt.Println("main defer function executed")`

`}`

`func op(a, b int) int {`

`defer func() {`

`if r := recover(); r != nil {`

`fmt.Println("Panic recovered", r)`

`op_defer()`

`}`

`}()`

`if(b==0){`

`panic("Can't divide a number by zero!")`

`}`

`result = a/b`

`return result`

`}`

`func main(){`

`defer main_defer()`

`result = op(10, 0)`

`fmt.Println("Completed")`

`}`

**Output:**

`Panic recovered Can't divide a number by zero!`

`op defer function executed`

`Completed`

`main defer function executed`

In the program given above, we called the "op" method from the main Goroutine. When it gets panicked, the program should terminate. However, before the termination, it executes the list of defer calls. While executing the defer function, it gets the `recover` function that takes control of the panic and returns the non-nil value passed in the panic. Here, the recover function resumes the execution of the program and after executing `op_defer` function, it comes back to **function caller statement** in main and continues the further execution. At the end, the defer function of the main Goroutine is called and thus, the program executes smoothly.

# [Conclusion](#toc.xhtml#s205a)

It can be concluded that we can recognize the errors by multiple return values of error type in Go. Golang provides `errors` packages that facilitate various functions to manipulate and analyze the errors in code. All the operations that need to be performed at the end can be done by the `defer` statement. The built-in function, `panic` controls the flow of the program and starts panicking. This panic situation is controlled by the `recover` function. Let’s discuss another feature of Go called reflection in the next chapter.

# [Questions](#toc.xhtml#s206a)

1.  Explain error handling in Go with an example.
2.  What is the purpose of the defer statement?
3.  What is the use of the "New" function for error handling?
4.  In what order are the defer statements executed in Go?
5.  What is the role of panic in error handling?
6.  How do you catch panic with the recover function?

# [CHAPTER 19](#toc.xhtml#c19)

# [Reflection](#toc.xhtml#c19)

**Reflection** is a key feature of a programming language that can be defined as examining the program execution and modifying it at runtime. Reflection plays an important role in object-oriented programming languages.

# [Structure](#toc.xhtml#s207a)

In this chapter, we will discuss the following topics:

*   Introduction to reflection
*   Reflect package
*   Laws of reflection

# [Objectives](#toc.xhtml#s208a)

After studying this chapter, you’ll be able to:

*   Inspect the type of a variable at runtime
*   Create and modify the variables and functions
*   Analyze the struct field in Go

# [Introduction](#toc.xhtml#s209a)

Reflection allows the exploration of any data at runtime without knowing its name defined at compile time. By using reflection, we can inspect the behavior of any method, interface, struct, or any data. Inspecting the source code at runtime is called reflection.

By using reflection, we can get the type, field, and the value of any type. Although in the Go language, every variable is declared with its type but still, there could be many cases where we may need to know the type of a variable at runtime. Here, reflection comes in.

**Example:**

`func main(){`

`slice_val :=[]string {"one", "two", "three", "four", "five", "six"}`

`map_val := map [string] int64{}`

`for itr:=0; itr<len(slice_val); itr++{`

`map_val[slice_val[itr]] = 0`

`}`

`}`

In the example given above, we initialize a slice of string type. We need to use the items of the slice like a key of a map. Here, we have declared a map that has the string type of keys. What if we need to initialize that map at runtime or a slice is of any type? In that case, we would need to find the type of slice at runtime. For that, we could use reflection.

# [The reflect package](#toc.xhtml#s210a)

Go provides a built-in package called `reflect` that provides the functionality of reflection at runtime. We can get the "reflect" package in the src directory. The `reflect` package contains a few variables and methods to manipulate the object of various types. It is used to return the dynamic type of a variable that is static of interface type. As an empty interface can accept any value, we can get the exact type of value that is accepted by an interface with the use of the `reflect` package. The reflect package is mainly used to get the type, value, and kind of a variable.

# [Type](#toc.xhtml#s211a)

The `reflect` package provides the method `TypeOf` to get the type of a variable. This function returns the value of the type `reflect`. The type has various methods to define the property of that type. The signature of this function is as follows:

`funcTypeOf(i interface{}) type`

This function takes an interface as an argument. Any value is accepted by an interface and then analyzed by the `TypeOf` function.

**Syntax:**

`variable_type := reflect.TypeOf(variable)`

**Example:**

`package main`

`import ("fmt"`

`"reflect"`

`)`

`func main(){`

`type student struct{`

`name string`

`age int`

`}`

`stu := student{"Akansha", 17}`

`fmt.Println(stu)`

`stu_type := reflect.TypeOf(stu)`

`fmt.Println("type of 'stu' variable:", stu_type)`

`fmt.Println("type of 'stu_type' variable:", reflect.TypeOf(stu_ type))`

`fmt.Println("name of 'stu' variable type:", stu_type.Name())`

`}`

**Output:**

`{Akansha 17}`

`type of 'stu' variable: main.student`

`type of 'stu_type' variable: *reflect.rtype`

`name of 'stu' variable type: student`

# [Value](#toc.xhtml#s212a)

The reflect package has a method to evaluate the value of a variable.

**Syntax:**

`value := reflect.ValueOf(variable)`

**Example:**

`package main`

`import ("fmt"`

`"reflect"`

`)`

`func main(){`

`type student struct{`

`name string`

`age int`

`}`

`stu := student{"Akansha", 17}`

`fmt.Println(stu)`

`stu_type := reflect.TypeOf(stu)`

`fmt.Println("value of 'stu' variable:", reflect.ValueOf(stu))`

`fmt.Println("value of 'stu_type' variable:", reflect.ValueOf(stu_ type))`

`}`

**Output:**

`{Akansha 17}`

`value of 'stu' variable: {Akansha 17}`

`value of 'stu_type' variable: main.student`

# [Kind](#toc.xhtml#s213a)

Kind is quite a different method of the `reflect` package. The type defines the type of a variable while "kind" defines the source type of a variable type. This function is used with a type to get its source, not with variables.

**Example:**

`package main`

`import ("fmt"`

`"reflect"`

`)`

`func main(){`

`type student struct{`

`name string`

`age int`

`}`

`stu := student{"Akansha", 17}`

`fmt.Println(stu)`

`stu_type := reflect.TypeOf(stu)`

`stu_kind := stu_type.Kind()`

`fmt.Println("type of 'stu' variable:", stu_type.Name())`

`fmt.Println("kind of 'stu_type' variable:", stu_kind)`

`}`

**Output:**

`{Akansha 17}`

`type of 'stu' variable: student`

`kind of 'stu_type' variable: struct`

Here, we can see that student is a type of struct. So, the source type of the `student` type is a struct.

# [NumField()](#toc.xhtml#s214a)

This method is used to get the number of fields contained by a struct. As this function is defined in the reflect package, it only works with type `reflect`.`Value` or `reflect.Type.`

**Example:**

`package main`

`import ("fmt"`

`"reflect"`

`)`

`func main(){`

`type student struct{`

`name string`

`age int`

`}`

`stu := student{"Akansha", 17}`

`stu_value := reflect.ValueOf(stu)`

`num_fields := stu_value.NumField()`

`fmt.Println("number of fields in 'stu':", num_fields, reflect. TypeOf(stu_value))`

`stu_type := reflect.TypeOf(stu)`

`fmt.Println("number of fields in 'stu':", num_fields, reflect. TypeOf(stu_type))`

`}`

**Output:**

`number of fields in 'stu': 2 reflect.Value`

`number of fields in 'stu': 2 *reflect.rtype`

# [Field](#toc.xhtml#s215a)

This function is used to get the value of struct fields. It returns the value of type `reflect.Value.`

**Example:**

`package main`

`import ("fmt"`

`"reflect"`

`)`

`func main(){`

`type student struct{`

`name string`

`age int`

`}`

`stu := student{"Akansha", 17}`

`stu_value := reflect.ValueOf(stu)`

`num_fields := stu_value.NumField()`

`for itr:=0; itr<num_fields; itr++{`

`fmt.Printf("value of %dth field is:%v of type %T\n", itr+1, stu_value.Field(itr), stu_value.Field(itr))`

`}`

`}`

**Output:**

`value of 1th field is:Akansha of type reflect.Value`

`value of 2th field is:17 of type reflect.Value`

# [String(), Int() & Float()](#toc.xhtml#s216a)

In the `reflect` package, the Value function returns the data of type `reflect.Value`. We can convert such values to string or any other type as required.

**Example:**

`package main`

`import ("fmt"`

`"reflect"`

`)`

`func main(){`

`type student struct{`

`name string`

`age int`

`income float32`

`}`

`stu := student{"Akansha", 17, 40000.565}`

`stu_value := reflect.ValueOf(stu)`

`fmt.Printf("Type of name is %T and value is %v\n", stu_value. Field(0), stu_value.Field(0))`

`fmt.Printf("Type of age is %T and value is %v\n", stu_value. Field(1), stu_value.Field(1))`

`fmt.Printf("Type of income is %T and value is %v\n", stu_value. Field(2), stu_value.Field(2))`

`name := reflect.ValueOf(stu.name).String()`

`age := reflect.ValueOf(stu.age).Int()`

`income := reflect.ValueOf(stu.income).Float()`

`fmt.Printf("Type of name is %T and value is %v\n", name, name)`

`fmt.Printf("Type of age is %T and value is %v\n", age, age)`

`fmt.Printf("Type of income is %T and value is %v\n", income, income)`

`}`

**Output:**

`Type of name is reflect.Value and value is Akansha`

`Type of age is reflect.Value and value is 17`

`Type of income is reflect.Value and value is 40000.566`

`Type of name is string and value is Akansha`

`Type of age is int64 and value is 17`

`Type of income is float64 and value is 40000.56640625`

# [Laws of reflection](#toc.xhtml#s217a)

Go defines three laws of reflection that define how reflection works and the points that should be remembered while working with reflection. The three laws of reflection are as follows:

1.  **Reflection goes from interface value to reflection object**
    
    Since an empty interface accepts any value, it makes it quite hard to understand what type of value is stored by an interface. Here, reflection works to get the type and value contained by an interface. The type and value of a variable are evaluated by using the functions `TypeOf` and `ValueOf` as we have already seen in the previous example. The first law of reflection is all about extracting a reflection object from an interface.
    
    **Example:**
    
    `package main`
    
    `import ("fmt"`
    
    `"reflect"`
    
    `)`
    
    `func show_value(i interface{}){`
    
    `value_type := reflect.TypeOf(i)`
    
    `value := reflect.ValueOf(i)`
    
    `fmt.Printf("Passed value is %v of type %v\n", value, value_type.Kind())`
    
    `fmt.Println(reflect.TypeOf(value))`
    
    `fmt.Println(reflect.TypeOf(value_type))`
    
    `}`
    
    `func main(){`
    
    `type student struct{`
    
    `name string`
    
    `age int`
    
    `income float32`
    
    `}`
    
    `stu := student{"Akansha", 17, 40000.565}`
    
    `show_value(stu)`
    
    `}`
    
    **Output:**
    
    `passed value is {Akansha 17 40000.566} of type struct`
    
    `reflect.Value`
    
    `*reflect.rtype`
    
2.  **Reflection goes from reflection object to interface value**
    
    The second law is the inverse of the first law. The second law says the type `reflect.Value` and `reflect.Type` can be converted to interface value. The following is an example of reflection’s second law.
    
    **Example:**
    
    `package main`
    
    `import ("fmt"`
    
    `"reflect"`
    
    `)`
    
    `func show_value(i interface{}){`
    
    `value_type := reflect.TypeOf(i)`
    
    `value := reflect.ValueOf(i)`
    
    `fmt.Println(reflect.TypeOf(value))`
    
    `fmt.Println(reflect.TypeOf(value_type))`
    
    `interface_val := value.Interface()`
    
    `fmt.Println("Interface value is:", interface_val)`
    
    `fmt.Println("Interface value type is:", reflect. TypeOf(interface_val).Kind())`
    
    `}`
    
    `func main(){`
    
    `type student struct{`
    
    `name string`
    
    `age int`
    
    `income float32`
    
    `}`
    
    `stu := student{"Akansha", 17, 40000.565}`
    
    `show_value(stu)`
    
    `}`
    
    **Output:**
    
    `reflect.Value`
    
    `*reflect.rtype`
    
    `Interface value is: {Akansha 17 40000.566}`
    
    `Interface value type is: struct`
    
3.  **To modify a reflection object, the value must be settable**
    
    On getting the value of a variable with the use of the `ValueOf` function, it returns the value of type `reflect.Value`. The third law says that to assign a value to `reflect.Value` type variable, the value must be of `reflect.Value` type. If it is not of the same type, it will show panic.
    
    **Example:**
    
    `package main`
    
    `import ("fmt"`
    
    `"reflect"`
    
    `)`
    
    `func main(){`
    
    `var str string = "Hello"`
    
    `val := reflect.ValueOf(str)`
    
    `fmt.Println(val)`
    
    `val.SetString("World ") // will throw panic`
    
    `}`
    
    **Output:**
    
    `panic: reflect: reflect.Value.SetString using unaddressable value.`
    
    In the example given above, we cannot set the value for type `reflect.Value` as `World` is not addressable. To get rid of such issues, we can first check if a variable is settable or not by using the function `CanSet`.
    
    **Example:**
    
    `package main`
    
    `import ("fmt"`
    
    `"reflect"`
    
    `)`
    
    `func main(){`
    
    `var str string = "Hello"`
    
    `val := reflect.ValueOf(str)`
    
    `fmt.Println(val)`
    
    `fmt.Println(val.CanSet())`
    
    `}`
    
    **Output:**
    
    `Hello`
    
    `false`
    

# [Conclusion](#toc.xhtml#s218a)

Reflection concludes a way to examine the Go program at runtime. It allows getting the type, value, and kind of any variable, function, or struct. Functions and structs are easy to explore with the reflect package that we have in Golang. It provides various functions to examine the behavior of the reflection objects. Golang provides three laws of reflection that wind up reflection techniques and how they work with variables, functions, and structures. Let’s build a web application in the Go language in the next chapter.

# [Questions](#toc.xhtml#s219a)

1.  What is a reflection in Go?
2.  How do you get the type of any variable?
3.  What function is used to get several fields in a structure?
4.  How can we change the type of reflection object?
5.  What do you understand by "kind" property of reflection object?
6.  How to get the value of the struct field in Go?
7.  What are the laws of reflection in Go?

# [CHAPTER 20](#toc.xhtml#c20)

# [Building Web Application](#toc.xhtml#c20)

Till now, we have gained a deep understanding of variables, constants, data types, operators, control structures, functions, packages, and many other features of the Go language. It is time to collaborate all these features and take a step forward to build an application in the Go language.

# [Structure](#toc.xhtml#s220a)

In this chapter, we will discuss the following topics:

*   Introduction to web development
*   HTML
*   JavaScript
*   CSS
*   GopherJS
*   Database
*   Building an application

# [Objectives](#toc.xhtml#s221a)

After studying this chapter, you’ll be able to:

*   Understand the concept of HTML
*   Use any type of CSS with HTML
*   Add JS code with HTML
*   Work on GopherJS
*   Use the database for any Golang project

# [Introduction to web development](#toc.xhtml#s222a)

**Web development** refers to creating web pages, developing a website, and hosting them via the internet or intranet. The website could be a single web page or a large application having multiple web pages accessed with a specific domain name. A website could be a social networking website, an e-commerce website, or any business website.

![](images/20-1.jpg)

**Figure 20.1:** Web structure

A website specifies a location on the internet. In technical dialect, a website is an effect of client-side and server-side scripting.

Client-side scripting refers to the programming that is executed by the browser and manifests on the client's screen as a result. HTML (Hypertext Markup Language) is the standard markup language used for web designing. Today, we have many client-side scripting languages that can be embedded with HTML and used for formatting and validating the web pages. HTML, JavaScript, and CSS are the roots of every web page. Let's get a basic idea of these languages.

# [HTML](#toc.xhtml#s223a)

HTML stands for Hypertext Markup Language. **Hypertext** is a method to connect multiple texts/documents through links. Any language that uses tags to format the elements in a document is called a markup language. A web page contains various elements. HTML elements have two major attributes, id and class, that help to identify an element uniquely.

In HTML, these elements are created by the tags. According to the content, an element can contain various tags. HTML elements can be of two types:

*   **Container elements:** Elements that contain any text, a paragraph, HTML element, or document are called container elements. These type of elements are enclosed by opening and closing tags. A complete HTML document is contained between the `<HTML>` tag. Every container element is in between the start and stop tags. If the stop tag is missing, the additional content is to be considered within the same start tag.

The following are some examples of container tags that we have in HTML.

*   **<html>**
    
    This tag encloses the complete HTML document and defines the format of the content to the web browser. The entire HTML document is in between the start tag <html> and stop tag `</html>`. The content defined within the `<html>` tag is divided into various sections such as `<head>, <body>,` and many others. With multiple types of HTML tags, the basic structure of any HTML file is defined.
    
    `<html>`
    
    `<head>`
    
    `. . . . . . . .`
    
    `</head>`
    
    `<body>`
    
    `. . . . . . . .`
    
    `</body>`
    
    `</html>`
    
*   **<head>**
    
    This tag contains the basic information about a web page. It defines the properties, formatting style, and the path to other external files used in a web page. Specific tags are used within the <head> tag that represents certain information related to the web page, such as the title of the web page, links, CSS, JavaScript code for formatting, etc. These tags are discussed further.
    
    `<head>`
    
    `<title> . . . . </title>`
    
    `<style> . . . . </style>`
    
    `</head>`
    
*   **<title>**
    
    This tag is a part of the head section that defines the title of a web page. The title of a web page is displayed at the top of the web browser and also used as a bookmark text for a web page.
    
    `<title> This is the title of webpage </title>`
    
*   **<body>**
    
    The `<body>` tag contains the main content that we need to show on a web page. It includes text, hyperlinks, images, tables, input controls, frames, and more. It contains some attributes that define the property of a web page. Any web page can have a maximum of one `<body>` tag in it.
    
    `<body>`
    
    `Content of webpage`
    
    `</body>`
    
*   **<div>**
    
    The `<div>` tag is a part of the HTML body. It is a generic block level container tag. This tag groups the text and other HTML elements which makes the block level formatting and styling easy.
    
    `<div> . . . </div>`
    
    Or
    
    `<div id = "id_of_div_element"> . . . . </div>`
    
*   **<span>**
    
    `<span>` is a generic inline container that groups the text and HTML elements in a line. Like the `<div>` tag, we can manipulate the formatting in a batch of HTML elements.
    
    `<span> . . . . </span>`
    
    Or
    
    `<span class = "class_of_span_element"> . . . . </span>`
    
*   **<table>**
    
    In HTML, a table is designed within the `<table>` tag. Since a table consists of multiple rows, columns, headers, and captions, the `<table>` tag contains multiple tags within it to define the same. The tags `<caption>, <th>, <tr>,` and `<td>` are used to specify the caption of the table, the header text of any row or column, the data in a row, and the data in a column correspondingly.
    
    `<table>`
    
    `<caption> Caption of Table </caption>`
    
    `<tr><th> . . . . </th></tr>`
    
    `<tr><td> . . . . </td></tr>`
    
    `</table>`
    
*   **<textarea>**
    
    `<textarea>` specifies the input control textarea that allows the input text in multiple lines. By default, a textarea can contain an unlimited number of characters. In HTML, we can set a limit of the characters it can hold and the size of a textarea.
    
    `<textarea rows = "no_of_rows" cols = "no_of_columns"> . . . . </textarea>`
    
*   **<a>**
    
    The `<a>` tag dictates a hyperlink that is used to navigate from one page to another. The href attribute holds the path of the destination page in this tag.
    
    `<a href = "destination_page_link"> . . . . </a>`
    
*   **<i>**
    
    The text enclosed between `<i>` and `</i>` is shown in italics on the browser.
    
    `<i> ITALIC text </i>`
    
*   **<u>**
    
    The text enclosed between `<u>` and `</u>` is shown as underlined on the browser. However, we can change the property of this tag by adding any class or CSS.
    
    `<u> UNDERLINED text </u>`
    
*   **<b>**
    
    The text enclosed between `<b>` and `</b>` is shown in bold on the browser.
    
    `<b> BOLD text </b>`
    
*   **<p>**
    
    This tag specifies a paragraph that adds some margin before and after the paragraph. By using the margin properties, we can modify the space around the paragraph.
    
    `<p> Content of Paragraph </p>`
    
*   **<sup>**
    
    The text enclosed between `<sup>` and `</sup>` is shown in small font, half a character above the baseline.
    
    `<sup> any text </sup>`
    
*   **<sub>**
    
    The text enclosed between `<sub>` and `</sub>` is shown in small font, half a character below the baseline.
    
    `<sub> any text </sub>`
    
*   **<ol>**
    
    An ordered list is defined by the `<ol>` tag. In such a list, items are ordered alphabetically or numerically to maintain a sequence.
    
    `<ol type = "type_of_list">`
    
    `<li> list item </li>`
    
    `<li> list item </li>`
    
    `. . . .`
    
    `. . . .`
    
    `</ol>`
    
*   **<ul>**
    
    An unordered list is defined by the `<ul>` tag. In such a list, the items are collected in a group with no numerical/alphabetical order and shown with bullets.
    
    `<ul>`
    
    `<li> list item </li>`
    
    `<li> list item </li>`
    
    `. . . .`
    
    `. . . .`
    
    `</ul>`
    

**Empty element:** These elements don’t contain any data. They are also called void or self-closing elements. Some empty elements are as follows:

*   **<input>**
    
    An input field is shown using the `<input>` tag. It could be a text, email, phone number, or something else depending on the "type" attribute of this tag. This tag has many attributes that define various properties of an input field.
    
    `<input type = "type_of_input" name = "name_of_input">`
    
*   **<base>**
    
    This tag is a part of the `<head>` tag that defines the base target for all relative URLs defined in a web page. A document can have a maximum of one `<base>` tag in it.
    
    `<base href = "target_link">`
    
*   **<meta>**
    
    This tag is used within the `<head>` tag that assigns a structured metadata for a web page. In simple words, metadata is info data related to other data. It has two major attributes, name and content. The name attribute specifies the name of the metadata and content specifies the value of the metadata.
    
    `<meta name = "content_name" content = "content_type" >`
    
*   **<br>**
    
    This tag simply adds a line break in a document.
    
    `<br>`
    
*   **<hr>**
    
    `<hr>` stands for "horizontal rule" which inserts a thematic break in a document and divide the content into multiple sections.
    
    `<hr>`
    
*   **<img>**
    
    The `<img>` tag is used to represent an image in a document. This tag contains some attributes that define the source of the image, alternative text for the image, and many other properties.
    
    `<img src= "image_source">`
    
*   **<col>**
    
    `<col>` specifies the properties that are common for all the columns in a table. It takes out the need for repeating the same style for each column.
    
    `<col style = "required_style">`
    

# [JavaScript](#toc.xhtml#s224a)

**JavaScript** is a dynamic type, high level, client-side scripting language. It is used with HTML to create dynamic content. Along with HTML and CSS, JavaScript is the key to web applications. Initially, JavaScript was only used in web browsers but now, it is also used with non-browser applications for server-side deployment.

JavaScript is embedded with HTML content and establishes a connection with HTML DOM (Document Object Model) when a web page is loaded on the browser. DOM represents every HTML element in a tree structure. With JavaScript, we can "add/remove the HTML elements, modify the attributes of elements, create events on elements and perform required activity on existing events."

JavaScript can be embedded within HTML content enclosed by the <script> tag or can be written in a separate file. Based on the place of the JS code, it can be of two types:

# [Internal JavaScript](#toc.xhtml#s225a)

In **Internal JavaScript**, the code is placed in the same file that contains the HTML content. If the JS code contains less number of lines, then it is good to write internal JS as it loads faster than the external JS.

**Example:**

`<!DOCTYPE html>`

`<html>`

`<body>`

`<p id = "para_id">At the time of Go’s initiation, complexity was the major concern in Software Development.</p>`

`<script>`

`document.getElementById("para_id").innerHTML = "Internal Java Script Example";`

`</script>`

`</body>`

`</html>`

**Output:**

![](images/20-2.jpg)

**Figure 20.2:** Output of the above code

# [External JavaScript](#toc.xhtml#s226a)

**External JavaScript** code is written in a separate file and the source of the JS file is given with the HTML content. Suppose an identical JS code needs to be applied to multiple HTML elements. Then, it is better to write the external JS. External JS is easy to modify as compared to internal JS.

**Example:**

`HTML file:`

`<!DOCTYPE html>`

`<html>`

`<head>`

`<script type="text/javascript" src="myjs.js"></script>`

`</head>`

`<body onload="function_onload()">`

`<p id = "para_id">At the time of Go’s initiation, complexity was the major concern in Software Development.</p>`

`</body>`

`</html>`

**myjs.js**

`function function_onload()`

`{`

`var div_ele = document.createElement("div");`

`div_ele.innerHTML = "External Java Script called";`

`document.body.appendChild(div_ele);`

`}`

**Output:**

![](images/20-3.jpg)

**Figure 20.3:** Output of the above code

# [CSS](#toc.xhtml#s227a)

CSS stands for "Cascading Style Sheets" which means passing an approach that improves the appearance of a web page/sheet and helps to beautify the HTML elements.

CSS is not a programming language. It is a styling language that is used for website layout and fonts and creates attractive web pages. It is a free language and can also be used with another markup language such as XHTML, XML, etc. Here, we'll see the use of CSS with HTML. There is no rigid logic with CSS. We can use its syntax as per our required design and how we want to show the HTML elements on a web page. CSS syntax is based on the selector and its declaration. The selector is nothing but an HTML element, and its declaration is the set of properties that we want to add/modify for a particular selector.

![](images/20-4.jpg)

**Figure 20.4:** CSS component

HTML tags, id, or class names are used to access an HTML element. CSS provides various properties that can change the views of a webpage. The following are some properties that can be used for CSS declaration.

![](images/20-5.jpg)

**Figure 20.5:** CSS properties

CSS can be embedded within an HTML element, enclosed between the `<style>` tag, or can be written in a separate file. Based on the placememt of the CSS code, it can be of three types. These are as follows:

*   **Inline CSS**
    
    Changes on a particular HTML element can easily be done with Inline CSS. An **Inline CSS** declaration is used at the time of element declaration within HTML.
    
    **Example:**
    
    `<!DOCTYPE html>`
    
    `<html>`
    
    `<body>`
    
    `<p style="color: red; text-align: center; font-size: 50px ;"> At the time of Go’s initiation, complexity was the major concern in Software Development. Usually the development used to be done with C++ or Java but there were some challenges with them like security, memory utilization, speed, efficiency, debugging etc. Software should have the power to function correctly against some potential risk produced by malicious attacks. </p>`
    
    `</body>`
    
    `</html>`
    
    **Output:**
    
    ![](images/20-6.jpg)
    
    **Figure 20.6:** Output of inline CSS
    
*   **Internal CSS**
    
    **Internal CSS** is defined within the `<style>` tag in the` <head>` section of HTML. It affects all the elements that are defined as a selector. It is useful when there is a need to apply the same CSS on multiple elements. While specifying selector, HTML elements are separated by a comma.
    
    **Example:**
    
    `<!DOCTYPE html>`
    
    `<html>`
    
    `<head>`
    
    `<style>`
    
    `p, div`
    
    `{`
    
    `color: red;`
    
    `text-align: center;`
    
    `font-size: 50px;`
    
    `}`
    
    `</style>`
    
    `</head>`
    
    `<body>`
    
    `<p>At the time of Go’s initiation, complexity was the major concern in Software Development.</p>`
    
    `<div>`
    
    `Usually the development used to be done with C++ or Java but there were some challenges with them like security, memory utilization, speed, efficiency, debugging etc.`
    
    `</div>`
    
    `<span>`
    
    `Software should have the power to function correctly against some potential risk produced by malicious attacks.`
    
    `</span>`
    
    `</body>`
    
    `</html>`
    
    **Output:**
    
    ![](images/20-7.jpg)
    
    **Figure 20.7:** Output of internal CSS
    
*   **External CSS**
    
    The CSS code is defined in a separate file with the `.css` extension and the path of the external CSS file is defined using the `<link>` tag in HTML.
    
    **Example:**
    
    `HTML file:`
    
    `<!DOCTYPE html>`
    
    `<html>`
    
    `<head>`
    
    `<link rel="stylesheet" type="text/css" href="mycss.css">`
    
    `</head>`
    
    `<body>`
    
    `<p>At the time of Go’s initiation, complexity was the major concern in Software Development.</p>`
    
    `<div>`
    
    `Usually the development used to be done with C++ or Java but there were some challenges with them like security, memory utilization, speed, efficiency, debugging etc.`
    
    `</div>`
    
    `<span>`
    
    `Software should have the power to function correctly against some potential risk produced by malicious attacks.`
    
    `</span>`
    
    `</body>`
    
    `</html>`
    
    **CSS file:**
    
    `p, div`
    
    `{`
    
    `color: red;`
    
    `text-align: center;`
    
    `font-size: 20px;`
    
    `}`
    
    `span`
    
    `{`
    
    `color: blue;`
    
    `font-size: 50px;`
    
    `}`
    
    **Output:**
    
    ![](images/20-8.jpg)
    
    **Figure 20.8:** Output of external CSS
    

Client-side scripting languages are limited to web page formatting, data validation, and page navigation. There can be a need to send data on the server or show data from the server to the frontend. In such cases, server-side scripting comes in. Client-side scripting has the code that requests to the server. Server-side scripting runs on a server, matches the client's request, and responds customized and dynamic content to the client. C++, Java, Ruby, and Python are some examples of server-side scripting languages.

# [GopherJS](#toc.xhtml#s228a)

Golang can be used as a frontend language. Golang provides the GopherJS compiler that translates the Go code into JavaScript and runs on the browser. GopherJS supports all the functionalities that Golang works for such as channels, goroutines, packages like `sync`, strings, regexp, cookiejar, url, tar, and many others.

We can write code in Go language that is executed on the server-side. For distributed networks, cloud services or other backend terminologies, Go language is used. We can create an interactive frontend by using GopherJS with any web framework like reactJS and others.

GopherJS provides a JS package that helps to interact with JavaScript APIs by using various built-in functions and data types.

Let's understand how to work with GopherJS in GO. First, install GopherJS and all the dependencies with the following command:

`go get –u github.com/gopherjs/gopherjs`

To run the above command, Git must be install on the system. While installing, GopherJS uses the value of the GOOS variable. linux and darwin are the supported values for the GOOS variable. So, on windows or FreeBSD, there can be a need to set the GOOS environment variable as follows:

`set GOOS=linux`

Create a go file, say `gopher_example.go`

`gopher_example.go`

`package main`

`import "github.com/gopherjs/gopherjs/js"`

`func main() {`

`js.Global.Get("document").Call("write", "Hello I am an example of gopherjs")`

`}`

Now compile Go code to JavaScript by using the following command:

`gopherjs build gopherjs_file_path -o js_file_path`

**Example:**

`gopherjs build gopher_example.go –o myjs.js`

It creates two files, `myjs.js` and `myjs.js.map` in the current directory. The JS file is a raw JavaScript file that we can use for the webpage/website. The js.map file maps Go code to JavaScript. It tracks all the changes done in the Go file.

Now create a basic HTML file and add the path to the JS file as an external JS.

`<!DOCTYPE html>`

`<html>`

`<head>`

`<script type="text/javascript" src="myjs.js"></script>`

`</head>`

`<body>`

`<p id = "para_id">At the time of Go’s initiation, complexity was the major concern in Software Development.</p>`

`</body>`

`</html>`

GopherJS provides JavaScript DOM binding by the `dom` package. The `dom` package enables access to HTML elements of the current document. It can be installed by the following command:

`go get -u honnef.co/go/js/dom`

**Example:**

In the following example, we are asking for the user’s age and verifying it when the user clicks on a button. If the user inputs the age as `50`, it shows the message `Age is valid`, else `Age` is not valid. Create an HTML file with the following code:

`<!DOCTYPE html>`

`<html>`

`<body bgcolor="orange">`

`<div>Enter age:<input type="number" id = "age"><div>`

`<button id="btn_id" type="button">Verify</button>`

`<div id="message"></div>`

`<script type="text/javascript" src="myjs.js"></script>`

`</body>`

`</html>`

Now create a Go file, say `gopherexample.go:`

`package main`

`import "honnef.co/go/js/dom"`

`func main() {`

`d := dom.GetWindow().Document()`

`age_ele := d.GetElementByID("age").(*dom.HTMLInputElement)`

`btn_ele := d.GetElementByID("btn_id").(*dom.HTMLButtonElement)`

`msg_ele := d.GetElementByID("message").(*dom.HTMLDivElement)`

`btn_ele.AddEventListener("click", false, func(event dom.Event) {`

`if age_ele.Value=="50"{`

`msg_ele.SetInnerHTML("Age is valid")`

`} else{`

`msg_ele.SetInnerHTML("Age is not valid")`

`}`

`})`

`}`

Compile the Go file and convert it to JavaScript with the following command:

`gopherjs build gopherexample.go –o myjs.js`

**Output:**

![](images/20-9.jpg)

**Figure 20.9:** output of above code

![](images/20-10.jpg)

**Figure 20.10:** Output if input is valid

![](images/20-11.jpg)

**Figure 20.11:** Output if input is invalid

GopherJS provides jquery bindings as well. Jquery is a JavaScript library, that wraps JavaScript code in various methods for easy use. To use jquery package of Gopherjs, first download jquery which is simply a JS file. We use a reference of the jquery file within the `<script>` tag in the `<head>` section of HTML. Let’s understand the use of the jquery package with Go. Create a HTML file as follows:

`<!doctype html>`

`<html lang="en">`

`<head>`

`<script src="path_of_downloaded_jquery_file"></script>`

`</head>`

`<body bgcolor="orange">`

`<button id ="btn">Show / Hide</button>`

`<div id="msg"> Hello Go</span>`

`<script src="myjquery.js"></script>`

`</body>`

`</html>`

Now create a Go file, say `gopherjs_jquery.go` with the following code:

`package main`

`import "github.com/gopherjs/jquery"`

`var jQuery = jquery.NewJQuery`

`const (`

`btn = "button#btn"`

`msg_ele = "div#msg"`

`)`

`func main() {`

`jQuery(btn).On(jquery.CLICK, func(e jquery.Event) {`

`jQuery(msg_ele).Toggle()`

`})`

`}`

Now compile the above code as shown below:

`gopherjs build gopherjs_jquery.go -o myjquery.js`

**Output:**

The example given above toggles between show and hide on the button click.

# [Database](#toc.xhtml#s229a)

We have learned frontend technology in a better way. In web development, data plays an important role. There should be a secure place to save and fetch data whenever required. For relevant data, the database follows a critical role. The **database** is nothing but an electronic and organized collection of data that can be accessed, updated, and manipulated in various ways. Databases are quite complex, but they make the data easily accessible.

A software/system that manages the database is called the database management system. It defines the format of the data, field name, record, and file structure in a database. It makes the administration, data insertion, modification, retrieval, and deletion easy by using various queries that work on a database. We have so many DBMS in our technological world.

Oracle Database, MySQL, SQLite, Microsoft Access, and PostgreSQL are some examples of the DBMS that we have in our technological world.

Here, we'll continue with MySQL.

*   **MySQL**
    
    **MySQL** is a free open-source relational database management system that uses Structured Query Langauge **(SQL).** MySQL stores the data in a tabular form and establishes the relation between the tables and data. It is a widely used database because of its flexible nature. Data security, workflow control, high performance, transactional support, and on-demand scalability are the key features of MySQL. We can download MySQL from its official website: **[https://dev.mysql.com/](https://dev.mysql.com/)**
    
*   **SQL**
    
    **SQL** stands for Structured Query Language. It is a domain specific language that is used for database communication in a relational database management system. SQL can be used with many database systems like MySQL, MS Access, Oracle, Sybase, and others. We can execute various queries in SQL to perform a different type of operation like database/record creation, data insertion/updation, data retrieval, set permission for tables, views, or procedures and many others. SQL queries consist of many statements that are divided into the following categories:
    
    *   **Data Definition Language (DDL)**
        
        DDL language is used to define the database structure by creating/updating database objects like tables, views, functions, etc. DDL is a sub-set of SQL. It is also called Data Description Language. Some of the DDL statements are as follows:
        
        *   CREATE
        *   ALTER
        *   DROP
        *   TRUNCATE
        *   COMMENT
        *   GRANT
        *   REVOKE
        *   RENAME
        *   PURGE
    *   **DML (Data Manipulation Language)**
        
        DML is a data specific language that is used for data insertion, modification, and deletion in a database. It is used to manipulate the data stored in a database. Some DML statements are as follows:
        
        *   SELECT
        *   INSERT
        *   UPDATE
        *   DELETE
        *   CALL
        *   MERGE
    *   **TCL (Transaction Control Language)**
        
        It handles the data changes (transactions) made by the DML statement in a table. Any change made by a DML statement is not permanent until it is not saved by a TCL statement. Common TCL commands are as follows:
        
        *   COMMIT
        *   ROLLBACK
        *   SAVEPOINT

To run SQL queries, first start the MySQL server on your PC. MySQL doesn't have any built-in GUI tool for Windows. To run MySQL in an easy way, we can download any of the GUI tools like Heidi SQL, MySQL Workbench, Sequel Pro, SQLyog, Navigate for MSQL, etc. Here, we'll continue with SQLyog. **SQLyog** is a customized user interface with a multi-threaded query execution tool. After downloading SQLyog, create a new connection, say Golang\_connection.

![](images/20-12.jpg)

**Figure 20.12:** Name a connection

Set all the fields as per the requirement or leave them as they are and test a connection. For a successful connection, it'll be as follows:

![](images/20-13.jpg)

**Figure 20.13:** successful connection

After creating a successful connection, connect to it.

![](images/20-14.jpg)

**Figure 20.14:** Query area

Now create a database by using the following command.

`CREATE DATABASE databasename;`

Write the query and execute it with F9, that is:

`CREATE DATABASE go_web;`

Refresh the object browser with *F5*, and a new database `go_web` is created.

![](images/20-15.jpg)

**Figure 20.15:** Database creation

Let's create a table containing the information of any user. This table holds various fields of several data types. The following is the query to create a table in a database.

`CREATE TABLE table_name (`

`column1 datatype,`

`column2 datatype,`

`column3 datatype,`

`….`

`);`

**Example:**

`CREATE TABLE user_info (`

`first_name TEXT,`

`last_name TEXT,`

`email TEXT,`

`contact BIGINT,`

`upassword TEXT`

`);`

![](images/20-16.jpg)

**Figure 20.16:** table creation

SQLyog provides shortcuts for almost all SQL statements. One can use them too.

# [Building an application](#toc.xhtml#s230a)

After getting enough understanding of HTML, CSS, JS, and SQL, let's create a web application in the Go language. Go language holds various built-in libraries for web applications. A few necessary web application packages are as follows:

*   `net/http`
    
    This library supports `GET, POST, HEAD, POSTFORM` http requests and prepares the client and server implementation.
    
*   `html/template`
    
    Here, the template package implements data-driven templates for the required HTML output. html package is used for escaping and unescaping HTML text.
    
    One can get any required package in Go by using the following command.
    
    `go get package_name`
    
    First, write a code to run the Go server.
    
    `server.go`
    
    `package main`
    
    `import (`
    
    `"net/http"`
    
    `)`
    
    `func main() {`
    
    `http.ListenAndServe(":8080", nil)`
    
    `}`
    

Here, the function `ListenAndServe` ensures that all the requests are listening on `8080` port. Run this file and the server will run till the program is terminated. If we check on **http://localhost:8080**, there would be an error saying that `404 page not found`. In Golang, we add the handlers to handle each web request. Add the handler to handle the webroot request in the server file as shown below:

`package main`

`import (`

`"log"`

`"html/template"`

`"net/http"`

`)`

`func Signup(w http.ResponseWriter, r *http.Request){`

`t, err := template.ParseFiles("signup.html")`

`if err != nil {`

`log.Print("template parsing error: ", err)`

`}`

`err = t.Execute(w, nil)`

`if err != nil {`

`log.Print("template executing error: ", err)`

`}`

`}`

`func main() {`

`http.HandleFunc("/", Signup)`

`http.ListenAndServe(":8080", nil)`

`}`

Here, the `HandleFunc` function of the http package handles the request going to the web root (“/”) with the `Signup` handler. The handler function takes two arguments. `http.ResponseWriter` collects the response data from the server and sends it to the HTTP client and `http.Request` represents an HTTP client request that is a component of the requested URL. In the handler function, the ParseFiles function parses an HTML file and executes it. Create an HTML file that we are parsing here to handle the web root request.

`signup.html`

`<!DOCTYPE html>`

`<html style="background-image: url(‘signup.jpg’);background-size: cover;">`

`<head>`

`<style type="text/css">`

`.data_form{`

`margin-top: 15%;`

`margin-left: 29%;`

`}`

`.label{`

`font-size: 25px;`

`font-weight: 25px;`

`display: inline-block;`

`min-width: 22%;`

`}`

`.in_field{`

`width: 27%;`

`display: inline-block;`

`}`

`.goforlogin{`

`margin-left: 39%;`

`}`

`div{`

`margin-bottom: 1.5%;`

`}`

`</style>`

`</head>`

`<body>`

`<form action="/AddUser" method="post" class="data_form">`

`<div><span class="label">First Name:</span><span ><input class="in_field" type="text" name ="first_name" required/></span></div>`

`<div><span class="label">Last Name:</span><span><input class="in_field" type="text" name ="last_name"/></span></div>`

`<div><span class="label">Email Id:</span><span><input class="in_field" type="Email" name ="email" required /></span></div>`

`<div><span class="label">Password:</span><span><input class="in_field" type="password" name ="password" required /></span></div>`

`<div><span class="label">Phone Number:</span><span><input class="in_field" type="tel" name ="phone" pattern="[0-9]{10}" required /></span></div>`

`<input type="submit" style="width: 14%;font-size: 20px;margin: 4% 0% 0% 13%;" value="Confirm"/>`

`</form>`

`<a class="goforlogin" href="login.html">Already registered</a>`

`</body>`

`</html>`

Access the server at **http://localhost:8080**

**Output:**

![](images/20-17.jpg)

**Figure 20.17:** Output of the above code

As shown above, a user can register by filling in all the necessary fields. With the submit button, we are directing the user to the AddUser page. To handle this request, we need to add a handler and its corresponding function in the server file. In the code shown below, we are creating the handler AddUser to handle this request.

`server.go`

`package main`

`import (`

`"log"`

`"html/template"`

`"net/http"`

`"database/sql"`

`"fmt"`

`_ "github.com/go-sql-driver/mysql"`

`)`

`func AddUser(w http.ResponseWriter, r *http.Request) {`

`if err := r.ParseForm(); err != nil {`

`fmt.Fprintf(w, "ParseForm() err: %v", err)`

`}`

`fName := r.FormValue("first_name")`

`lName := r.FormValue("last_name")`

`emailId := r.FormValue("email")`

`phoneNo := r.FormValue("phone")`

`password := r.FormValue("password")`

`// Create Database connection`

`db, err := sql.Open("mysql", "root:@/go_web")`

`if err != nil {`

`panic(err.Error())`

`}`

`// Insert data`

`stmtIns, err := db.Query("INSERT INTO user_info VALUES(?,?,?,?,?)",fName,lName,emailId,phoneNo,password)`

`if err != nil {`

`panic(err.Error()) // proper error handling instead of panic in your app`

`}`

`defer stmtIns.Close()`

`t, err := template.ParseFiles("registrationConfirm.html")`

`if err != nil {`

`log.Print("template parsing error: ", err)`

`}`

`err = t.Execute(w, nil)`

`}`

`func main() {`

`http.HandleFunc("/", Signup)`

`http.HandleFunc("/AddUser", AddUser)`

`http.ListenAndServe(":8080", nil)`

`}`

In the above handler `AddUser`, we create a database connection to the MySQL server and insert the user data in a database. After inserting the data in a database, we have directed the user to `registrationConfirm` page. The following is the code of `registrationConfirm.html`

`registrationConfirm.html`

`<html>`

`<body style="background-color:yellow;">`

`You have successfully registered.`

`<a href="/login">Login here</a>`

`</body>`

`</html>`

Here is the output given on registering a user.

![](images/20-18.jpg)

**Figure 20.18:** Output of the above code

A user can log in by clicking on the above or if the user is already registered. In the code given above, we are directing a user to the `login` page. Add a handler to handle this request in the server file.

`package main`

`import (`

`"log"`

`"html/template"`

`"net/http"`

`"database/sql"`

`"fmt"`

`_ "github.com/go-sql-driver/mysql"`

`)`

`func Login(w http.ResponseWriter, r *http.Request){`

`t, err := template.ParseFiles("login.html")`

`// if there is an error`

`if err != nil {`

`log.Print("template parsing error: ", err)`

`}`

`err = t.Execute(w, nil)`

`if err != nil {`

`log.Print("template executing error: ", err)`

`}`

`}`

`func main() {`

`http.HandleFunc("/", Signup)`

`http.HandleFunc("/AddUser", AddUser)`

`http.HandleFunc("/login", Login)`

`http.ListenAndServe(":8080", nil)`

`}`

The login handler parses the HTML content of login.html and shows on the web page.

![](images/20-19.jpg)

**Figure 20.19:** Output of the above code

`login.html`

`<!DOCTYPE html>`

`<html style="background-image: url('login.jpg');background-size: cover;">`

`<head>`

`<style type="text/css">`

`.data_form{`

`margin-top: 15%;`

`margin-left: 29%;`

`}`

`#msg{`

`color:red;`

`font-size: 20px;`

`}`

`.label{`

`font-size: 25px;`

`font-weight: 25px;`

`display: inline-block;`

`min-width: 22%;`

`}`

`.in_field{`

`width: 27%;`

`display: inline-block;`

`}`

`div{`

`margin-bottom: 1.5%;`

`}`

`</style>`

`</head>`

`<body>`

`<form action="/home" method="post" class="data_form">`

`<div><span id="msg"></span></div>`

`<div><span class="label">Email Id:</span><span><input class="in_field" type="Email" name ="email" required /></span></div>`

`<div><span class="label">Password:</span><span><input class="in_field" type="Password" name ="password" required /></span></div>`

`<input type="submit" style="width: 14%;font-size: 20px;margin: 4% 0% 0% 13%;" value="Confirm"/>`

`</form>`

`<script type="text/javascript">`

`varvars = {};`

`var parts = window.location.href.replace(/[?&]+([^=&]+)=([^&]*)/gi, function(m,key,value) {vars[key] = value;});`

`if (vars["msg"]!==undefined){`

`document.getElementById("msg").innerHTML = decodeURI(vars["msg"])`

`}`

`</script>`

`</body>`

`</html>`

On submitting the login form, we are directing the flow to the home page (`/home`). Again, create a handler to handle this request as shown below:

`server.go`

`package main`

`import (`

`"log"`

`"strings"`

`"html/template"`

`"net/http"`

`"database/sql"`

`"fmt"`

`_ "github.com/go-sql-driver/mysql"`

`)`

`func Home(w http.ResponseWriter, r *http.Request){`

`if err := r.ParseForm(); err != nil {`

`fmt.Fprintf(w, "ParseForm() err: %v", err)`

`}`

`user_email := r.FormValue("email")`

`user_password := r.FormValue("password")`

`// Create a Database connection`

`db, err := sql.Open("mysql", "root:@/go_web")`

`fmt.Println(db,err)`

`if err != nil {`

`panic(err.Error())`

`}`

`type UserInfostruct {`

`First_name, Last_name, Email, Password string`

`Contact int64`

`}`

`var info UserInfo`

`// Getting data from Database`

`quer := "SELECT* FROM user_info WHERE email=?"`

`errr := db.QueryRow(quer,user_email).Scan(&info.First_name, &info.Last_name, &info.Email, &info.Contact, &info.Password)`

`if errr != nil {`

`fmt.Println(errr.Error())`

`// No such Email exists`

`if strings.Contains(errr.Error(), "no rows") {`

`http.Redirect(w, r, "http://localhost:8080/login?msg=Invalid Email", 301)`

`}`

`}`

`db.Close() //Close database connection`

`// Check user password`

`if user_password==info.Password{`

`t, err := template.ParseFiles("home.html")`

`if err != nil {`

`log.Print("template parsing error: ", err)`

`}`

`err = t.Execute(w, info)`

`// if there is an error`

`if err != nil {`

`log.Print("template executing error: ", err)`

`}`

`} else {`

`//in case of incorrect password`

`http.Redirect(w, r, "http://localhost:8080/login?msg=Invalid Password", 301)`

`}`

`}`

`func main() {`

`http.HandleFunc("/", Signup)`

`http.HandleFunc("/AddUser", AddUser)`

`http.HandleFunc("/login", Login)`

`http.HandleFunc("/home", Home)`

`http.ListenAndServe(":8080", nil)`

`}`

In the login handler, we can see the `Email Id` and `Password` that the user is trying to log in with. Check if such an email id exists in a database or not. If the email id exists (user is registered), then check if the password is correct. In case of any mismatching, it redirects the user with an error message. If an email id and password are both correct, then the user is redirectedto the home page.

![](images/20-20.jpg)

**Figure 20.20:** Output on invalid email

![](images/20-21.jpg)

**Figure 20.21:** output on invalid password

![](images/20-22.jpg)

**Figure 20.22:** output of above code

Here is the complete server code as shown below:

`server.go`

`package main`

`import (`

`"log"`

`"strings"`

`"html/template"`

`"net/http"`

`"database/sql"`

`"fmt"`

`_ "github.com/go-sql-driver/mysql"`

`)`

`func Signup(w http.ResponseWriter, r *http.Request){`

`t, err := template.ParseFiles("signup.html")`

`if err != nil {`

`log.Print("template parsing error: ", err)`

`}`

`err = t.Execute(w, nil)`

`if err != nil {`

`log.Print("template executing error: ", err)`

`}`

`}`

`func AddUser(w http.ResponseWriter, r *http.Request) {`

`if err := r.ParseForm(); err != nil {`

`fmt.Fprintf(w, "ParseForm() err: %v", err)`

`}`

`fName := r.FormValue("first_name")`

`lName := r.FormValue("last_name")`

`emailId := r.FormValue("email")`

`phoneNo := r.FormValue("phone")`

`password := r.FormValue("password")`

`// Create Database connection`

`db, err := sql.Open("mysql", "root:@/go_web")`

`if err != nil {`

`panic(err.Error())`

`}`

`// insert data`

`stmtIns, err := db.Query("INSERT INTO user_info VALUES(?,?,?,?,?)", fName, lName, emailId, phoneNo, password)`

`if err != nil {`

`panic(err.Error()) // proper error handling instead of panic in your app`

`}`

`defer stmtIns.Close()`

`t, err := template.ParseFiles("registrationConfirm.html")`

`if err != nil {`

`log.Print("template parsing error: ", err)`

`}`

`err = t.Execute(w, nil)`

`}`

`func Login(w http.ResponseWriter, r *http.Request){`

`t, err := template.ParseFiles("login.html")`

`if err != nil {// if there is an error`

`log.Print("template parsing error: ", err)`

`}`

`err = t.Execute(w, nil)`

`if err != nil {`

`log.Print("template executing error: ", err)`

`}`

`}`

`func Home(w http.ResponseWriter, r *http.Request){`

`if err := r.ParseForm(); err != nil {`

`fmt.Fprintf(w, "ParseForm() err: %v", err)`

`}`

`user_email := r.FormValue("email")`

`user_password := r.FormValue("password")`

`// Create a Database connection`

`db, err := sql.Open("mysql", "root:@/go_web")`

`fmt.Println(db,err)`

`if err != nil {`

`panic(err.Error())`

`}`

`type UserInfostruct {`

`First_name, Last_name, Email, Password string`

`Contact int64`

`}`

`var info UserInfo`

`// Getting data from Database`

`quer := "SELECT* FROM user_info WHERE email=?"`

`errr := db.QueryRow(quer,user_email).Scan(&info.First_name, &info.Last_name, &info.Email, &info.Contact, &info.Password)`

`if errr != nil {`

`fmt.Println(errr.Error())`

`// No such Email exists`

`if strings.Contains(errr.Error(), "no rows") {`

`fmt.Println("no rows here")`

`http.Redirect(w, r, "http://127.0.0.1:8080/ login?msg=Invalid Email", 301)`

`}`

`}`

`db.Close() //Close database connection`

`// Check user password`

`if user_password==info.Password{`

`fmt.Println("come",info.First_name)`

`t, err := template.ParseFiles("home.html")`

`if err != nil {`

`log.Print("template parsing error: ", err)`

`}`

`err = t.Execute(w, info)`

`if err != nil {// if there is an error`

`log.Print("template executing error: ", err)`

`}`

`} else {`

`//in case of incorrect password`

`http.’Redirect(w, r, "http://127.0.0.1:8080/login?msg=Invalid Password", 301)`

`}`

`}`

`func main() {`

`http.HandleFunc("/", Signup)`

`http.HandleFunc("/AddUser", AddUser)`

`http.HandleFunc("/login", Login)`

`http.HandleFunc("/home", Home)`

`http.ListenAndServe(":8080", nil)`

`}`

In this way, we have created a short web application in Go language. Implement once for better understanding.

# [Conclusion](#toc.xhtml#s231a)

In this chapter, we have understood the concept of frontend technologies HTML, CSS, and JavaScript. In every project, we need to organize the data properly. Here, databases come and hold the complex data by a formal design and modelling techniques. We have discussed here a Golang compiler called "GopherJS" that compiles the Go code and converts it into JavaScript to run on the browser. At the end, by using frontend and backend technologies, we have created an application in the Go language. Hopefully, you have successfully created an application by this chapter.

# [Questions](#toc.xhtml#s232a)

1.  What are container elements in HTML?
2.  Explain the difference between the div and span tag?
3.  What are self-closing elements in HTML?
4.  What are the three types of CSS?
5.  What do you understand by internal JavaScript?
6.  How do you write an external CSS?
7.  What is a database?
8.  How can we refer a JavaScript file in HTML?
9.  How can we install a package in Go?
10.  What is the role of GopherJS in Go?
11.  What are the different types of queries in SQL?

# [Index](#toc.xhtml#ind)

A

actual parameters [69](#c07.xhtml#page69)

anonymous function

about [76](#c07.xhtml#page76)

returning [76](#c07.xhtml#page76), [77](#c07.xhtml#page77)

append function [118](#c09.xhtml#page118)

applications, Go language

Docker [6](#c01.xhtml#page6)

Dropbox [7](#c01.xhtml#page7)

InfluxDB [7](#c01.xhtml#page7)

Kubernetes [6](#c01.xhtml#page6)

OpenShift [6](#c01.xhtml#page6)

arithmetic operators

about [50](#c05.xhtml#page50)

list [50](#c05.xhtml#page50)

array

about [37](#c04.xhtml#page37), [96](#c09.xhtml#page96)

declaring [96](#c09.xhtml#page96)

initializing [97](#c09.xhtml#page97), [98](#c09.xhtml#page98)

multidimensional array [99](#c09.xhtml#page99)

need for [98](#c09.xhtml#page98), [99](#c09.xhtml#page99)

array function

about [100](#c09.xhtml#page100)

argument passing function [102](#c09.xhtml#page102)

array length function [100](#c09.xhtml#page100)

comparison function [100](#c09.xhtml#page100), [101](#c09.xhtml#page101)

copy function [101](#c09.xhtml#page101)

iteration function [102](#c09.xhtml#page102)\-[104](#c09.xhtml#page104)

array initialization [97](#c09.xhtml#page97)

array of pointers [142](#c11.xhtml#page142)

assignment operators

about [53](#c05.xhtml#page53)

types [53](#c05.xhtml#page53), [54](#c05.xhtml#page54)

B

bitwise operators

about [52](#c05.xhtml#page52)

types [53](#c05.xhtml#page53)

blank identifier [74](#c07.xhtml#page74)

boolean constant [43](#c04.xhtml#page43)

boolean data type [34](#c04.xhtml#page34)

branching statements

about [60](#c06.xhtml#page60)

if/else statement [60](#c06.xhtml#page60)

switch statement [61](#c06.xhtml#page61)

break statement [62](#c06.xhtml#page62)

buffered channel [205](#c17.xhtml#page205)

C

call by reference [72](#c07.xhtml#page72)

call by value [71](#c07.xhtml#page71)

called function [71](#c07.xhtml#page71)

Cascading Style Sheets (CSS)

about [268](#c20.xhtml#page268), [269](#c20.xhtml#page269)

External CSS [271](#c20.xhtml#page271), [272](#c20.xhtml#page272)

Inline CSS [269](#c20.xhtml#page269)

Internal CSS [270](#c20.xhtml#page270)

channel

about [41](#c04.xhtml#page41)

closing [210](#c17.xhtml#page210), [211](#c17.xhtml#page211)

declaring [202](#c17.xhtml#page202)

direction [211](#c17.xhtml#page211)\-[213](#c17.xhtml#page213)

channel operations

about [203](#c17.xhtml#page203)

buffered channel [205](#c17.xhtml#page205)

capacity [206](#c17.xhtml#page206)

receive operation [203](#c17.xhtml#page203), [204](#c17.xhtml#page204)

send operation [203](#c17.xhtml#page203)

unbuffered channel [204](#c17.xhtml#page204)

circular import [90](#c08.xhtml#page90)\-[92](#c08.xhtml#page92)

closure function [77](#c07.xhtml#page77), [78](#c07.xhtml#page78)

cloud-based IDEs [11](#c02.xhtml#page11), [12](#c02.xhtml#page12)

code reusability [4](#c01.xhtml#page4)

compiler [12](#c02.xhtml#page12)

composition [158](#c13.xhtml#page158)\-[160](#c13.xhtml#page160)

concurrency

about [192](#c16.xhtml#page192)

versus parallelism [192](#c16.xhtml#page192)

constant

about [41](#c04.xhtml#page41)

boolean constant [43](#c04.xhtml#page43)

iota identifier [43](#c04.xhtml#page43)

numeric constant [42](#c04.xhtml#page42)

string constant [42](#c04.xhtml#page42)

container tags

<a> tag [263](#c20.xhtml#page263)

<b> [263](#c20.xhtml#page263)

<body> [262](#c20.xhtml#page262)

<div> [262](#c20.xhtml#page262)

<head> [261](#c20.xhtml#page261)

<html> [261](#c20.xhtml#page261)

<i> [263](#c20.xhtml#page263)

<ol> [264](#c20.xhtml#page264)

<p> [264](#c20.xhtml#page264)

<span> [262](#c20.xhtml#page262)

<sub> [264](#c20.xhtml#page264)

<sup> [264](#c20.xhtml#page264)

<table> [263](#c20.xhtml#page263)

<textarea> [263](#c20.xhtml#page263)

<title> [262](#c20.xhtml#page262)

<u> [263](#c20.xhtml#page263)

<ul> [264](#c20.xhtml#page264)

continue statement [63](#c06.xhtml#page63)

control structures

defining [60](#c06.xhtml#page60)

custom package

creating [87](#c08.xhtml#page87)\-[89](#c08.xhtml#page89)

D

database [277](#c20.xhtml#page277)

database management system [277](#c20.xhtml#page277)

Data Definition Language (DDL) [277](#c20.xhtml#page277)

Data Manipulation Language (DML) [278](#c20.xhtml#page278)

data race

checking [223](#c17.xhtml#page223), [224](#c17.xhtml#page224)

in Go language [222](#c17.xhtml#page222), [223](#c17.xhtml#page223)

data type

about [33](#c04.xhtml#page33)

non-primitive data type [37](#c04.xhtml#page37)

primitive data type [34](#c04.xhtml#page34)

deadlock

about [206](#c17.xhtml#page206)\-[208](#c17.xhtml#page208)

multiple Goroutines, using [208](#c17.xhtml#page208), [209](#c17.xhtml#page209)

defer keyword [79](#c07.xhtml#page79)

defer statement

about [237](#c18.xhtml#page237)\-[239](#c18.xhtml#page239)

working [237](#c18.xhtml#page237)

dereference operator [140](#c11.xhtml#page140)

dot import [86](#c08.xhtml#page86)

E

else statement [60](#c06.xhtml#page60)

empty element

about [265](#c20.xhtml#page265)

<base> [265](#c20.xhtml#page265)

<br> [265](#c20.xhtml#page265)

<col> [265](#c20.xhtml#page265)

<hr> [265](#c20.xhtml#page265)

<img> [265](#c20.xhtml#page265)

<input> [265](#c20.xhtml#page265)

<meta> [265](#c20.xhtml#page265)

empty interface [173](#c14.xhtml#page173)

error handling [6](#c01.xhtml#page6)

error package [236](#c18.xhtml#page236), [237](#c18.xhtml#page237)

error type [234](#c18.xhtml#page234), [235](#c18.xhtml#page235)

exit statement [64](#c06.xhtml#page64)

External CSS [271](#c20.xhtml#page271), [272](#c20.xhtml#page272)

External JavaScript [267](#c20.xhtml#page267)

F

Fibonacci series [87](#c08.xhtml#page87)

for loop [62](#c06.xhtml#page62)

formal parameters [69](#c07.xhtml#page69)

format (fmt) [84](#c08.xhtml#page84)

format package [84](#c08.xhtml#page84)

format specifiers

about [44](#c04.xhtml#page44), [46](#c04.xhtml#page46)

types [44](#c04.xhtml#page44), [45](#c04.xhtml#page45)

function arguments [69](#c07.xhtml#page69), [70](#c07.xhtml#page70)

function caller statement [244](#c18.xhtml#page244)

functions

about [24](#c03.xhtml#page24), [68](#c07.xhtml#page68)

calling [71](#c07.xhtml#page71)

declaring [69](#c07.xhtml#page69)

function type

using [75](#c07.xhtml#page75)

G

generic programming [6](#c01.xhtml#page6)

Go language

about [2](#c01.xhtml#page2)

applications [6](#c01.xhtml#page6)

characteristics [3](#c01.xhtml#page3)

data race [222](#c17.xhtml#page222), [223](#c17.xhtml#page223)

evolution [2](#c01.xhtml#page2)

installation [13](#c02.xhtml#page13)

installing, on Windows [13](#c02.xhtml#page13)\-[20](#c02.xhtml#page20)

limitations [6](#c01.xhtml#page6)

system requirements [10](#c02.xhtml#page10)

uninstalling [21](#c02.xhtml#page21)

Go language, features

automatic garbage collection [3](#c01.xhtml#page3)

concurrency [3](#c01.xhtml#page3)

cross-platform [4](#c01.xhtml#page4)

documentation [4](#c01.xhtml#page4)

ease testing [4](#c01.xhtml#page4)

standard library [4](#c01.xhtml#page4)

static [3](#c01.xhtml#page3)

Go language libraries

about [92](#c08.xhtml#page92)

cli [93](#c08.xhtml#page93)

color [94](#c08.xhtml#page94)

fuzzy [93](#c08.xhtml#page93)

glog [94](#c08.xhtml#page94)

gocheck [94](#c08.xhtml#page94)

Go kit [93](#c08.xhtml#page93)

GORM [93](#c08.xhtml#page93)

Kubernetes [93](#c08.xhtml#page93)

testify [93](#c08.xhtml#page93)

vegeta [93](#c08.xhtml#page93)

GopherJS compiler [273](#c20.xhtml#page273)\-[276](#c20.xhtml#page276)

Go program [24](#c03.xhtml#page24), [25](#c03.xhtml#page25)

Goroutines

about [192](#c16.xhtml#page192)\-[195](#c16.xhtml#page195)

methods [198](#c16.xhtml#page198)

multiple cores [198](#c16.xhtml#page198)

multiple Goroutines [196](#c16.xhtml#page196)

WaitGroup [198](#c16.xhtml#page198)

H

HTML elements

container element [261](#c20.xhtml#page261)

Hypertext [261](#c20.xhtml#page261)

Hypertext Markup Language (HTML) [261](#c20.xhtml#page261)

I

identifier

about [30](#c03.xhtml#page30)

basic rules [85](#c08.xhtml#page85)

if statement [60](#c06.xhtml#page60)

immutable string [128](#c10.xhtml#page128)

import path [85](#c08.xhtml#page85)

indirection operator [140](#c11.xhtml#page140)

Inline CSS [269](#c20.xhtml#page269)

interface

about [168](#c14.xhtml#page168)

as polymorphism [179](#c14.xhtml#page179)

declaring [168](#c14.xhtml#page168), [169](#c14.xhtml#page169)

embedding [178](#c14.xhtml#page178)

implementing [169](#c14.xhtml#page169)\-[171](#c14.xhtml#page171)

Internal CSS [270](#c20.xhtml#page270)

Internal JavaScript [266](#c20.xhtml#page266)

iota identifier [43](#c04.xhtml#page43)

J

JavaScript

about [266](#c20.xhtml#page266)

External JavaScript [267](#c20.xhtml#page267)

Internal JavaScript [266](#c20.xhtml#page266)

jumping statements

about [62](#c06.xhtml#page62)

break statement [62](#c06.xhtml#page62)

continue statement [63](#c06.xhtml#page63)

exit statement [64](#c06.xhtml#page64)

K

keywords [25](#c03.xhtml#page25)\-[27](#c03.xhtml#page27)

L

lambda function [76](#c07.xhtml#page76)

logical operators

about [52](#c05.xhtml#page52)

types [52](#c05.xhtml#page52)

looping statements

about [61](#c06.xhtml#page61)

for loop [62](#c06.xhtml#page62)

M

main function [68](#c07.xhtml#page68)

main package [84](#c08.xhtml#page84)

map

about [40](#c04.xhtml#page40), [182](#c15.xhtml#page182)

as reference type [188](#c15.xhtml#page188), [189](#c15.xhtml#page189)

declaring [182](#c15.xhtml#page182)

initializing [182](#c15.xhtml#page182), [183](#c15.xhtml#page183)

usage [182](#c15.xhtml#page182)

map operations

about [184](#c15.xhtml#page184)

comparison function [187](#c15.xhtml#page187), [188](#c15.xhtml#page188)

delete function [187](#c15.xhtml#page187)

iteration function [186](#c15.xhtml#page186)

keys function [185](#c15.xhtml#page185)

map length function [184](#c15.xhtml#page184)

miscellaneous operators

about [55](#c05.xhtml#page55)

types [55](#c05.xhtml#page55)

multidimensional array [99](#c09.xhtml#page99), [100](#c09.xhtml#page100)

multiple Goroutines [196](#c16.xhtml#page196)

multiple interface

implementing [174](#c14.xhtml#page174)

Mutex [224](#c17.xhtml#page224)\-[227](#c17.xhtml#page227)

mutual exclusion lock [224](#c17.xhtml#page224)

MySQL

about [277](#c20.xhtml#page277), [279](#c20.xhtml#page279)\-[281](#c20.xhtml#page281)

URL [277](#c20.xhtml#page277)

N

named return values [73](#c07.xhtml#page73)

named struct [147](#c12.xhtml#page147)

nested package [89](#c08.xhtml#page89), [90](#c08.xhtml#page90)

nested pointers [141](#c11.xhtml#page141), [142](#c11.xhtml#page142)

nested struct [153](#c12.xhtml#page153)

new function

about [141](#c11.xhtml#page141)

used, for creating pointers [141](#c11.xhtml#page141)

used, for creating struct [151](#c12.xhtml#page151)

non-primitive data type

about [37](#c04.xhtml#page37)

array [37](#c04.xhtml#page37)

channel [41](#c04.xhtml#page41)

map [40](#c04.xhtml#page40)

pointer [37](#c04.xhtml#page37)

slice [39](#c04.xhtml#page39)

structures [38](#c04.xhtml#page38)

numeric constant [42](#c04.xhtml#page42)

numeric data type

about [34](#c04.xhtml#page34)

floating-point [36](#c04.xhtml#page36)

integer [35](#c04.xhtml#page35)

O

object-oriented language [4](#c01.xhtml#page4)

operator precedence [56](#c05.xhtml#page56), [57](#c05.xhtml#page57)

operators [50](#c05.xhtml#page50)

operators, types

about [50](#c05.xhtml#page50)

arithmetic operators [50](#c05.xhtml#page50)

assignment operators [53](#c05.xhtml#page53)

bitwise operators [52](#c05.xhtml#page52)

logical operators [52](#c05.xhtml#page52)

miscellaneous operators [55](#c05.xhtml#page55)

relational operators [51](#c05.xhtml#page51)

P

package

about [84](#c08.xhtml#page84)

importing [85](#c08.xhtml#page85), [86](#c08.xhtml#page86)

panic function [240](#c18.xhtml#page240)\-[242](#c18.xhtml#page242)

parallelism

about [192](#c16.xhtml#page192)

versus concurrency [192](#c16.xhtml#page192)

pointers

about [37](#c04.xhtml#page37), [138](#c11.xhtml#page138)

benefits [138](#c11.xhtml#page138)

creating, with new function [141](#c11.xhtml#page141)

declaring [139](#c11.xhtml#page139)

dereferencing [140](#c11.xhtml#page140)

embedding [163](#c13.xhtml#page163)

initializing [139](#c11.xhtml#page139)

manipulating [140](#c11.xhtml#page140)

need for [138](#c11.xhtml#page138)

pointers function [142](#c11.xhtml#page142)\-[144](#c11.xhtml#page144)

primitive data type

about [34](#c04.xhtml#page34)

boolean [34](#c04.xhtml#page34)

numeric [34](#c04.xhtml#page34)

string [36](#c04.xhtml#page36)

programming language

analogy [4](#c01.xhtml#page4)

concurrency [5](#c01.xhtml#page5)

exception handling [5](#c01.xhtml#page5)

garbage collection [5](#c01.xhtml#page5)

inheritance [5](#c01.xhtml#page5)

object-oriented language [5](#c01.xhtml#page5)

overloading [5](#c01.xhtml#page5)

type-safe [5](#c01.xhtml#page5)

R

race condition [223](#c17.xhtml#page223)

recover function [243](#c18.xhtml#page243), [244](#c18.xhtml#page244)

recursive function [78](#c07.xhtml#page78), [79](#c07.xhtml#page79)

reflection

about [248](#c19.xhtml#page248)

laws [254](#c19.xhtml#page254)\-[257](#c19.xhtml#page257)

reflect package

about [248](#c19.xhtml#page248)

field [252](#c19.xhtml#page252)

float() [253](#c19.xhtml#page253)

int() [253](#c19.xhtml#page253)

kind [250](#c19.xhtml#page250), [251](#c19.xhtml#page251)

NumField() [251](#c19.xhtml#page251)

string() [253](#c19.xhtml#page253)

type [248](#c19.xhtml#page248), [249](#c19.xhtml#page249)

value [249](#c19.xhtml#page249)

relational operators

about [51](#c05.xhtml#page51)

types [51](#c05.xhtml#page51)

return types [69](#c07.xhtml#page69), [70](#c07.xhtml#page70)

rune data type

about [125](#c10.xhtml#page125)

immutable string [128](#c10.xhtml#page128), [129](#c10.xhtml#page129)

iterating, with range keyword [126](#c10.xhtml#page126)

multiline string [127](#c10.xhtml#page127)

slice of bytes, converting to string [128](#c10.xhtml#page128)

slice of runes, converting to string [127](#c10.xhtml#page127)

RWMutex [228](#c17.xhtml#page228), [230](#c17.xhtml#page230)

RWMutex, methods

Lock() [228](#c17.xhtml#page228)

RLock() [228](#c17.xhtml#page228)

RUnlock() [228](#c17.xhtml#page228)

Unlock() [229](#c17.xhtml#page229)

S

select keyword [214](#c17.xhtml#page214)\-[221](#c17.xhtml#page221)

slice function

about [112](#c09.xhtml#page112)

append function [118](#c09.xhtml#page118), [119](#c09.xhtml#page119)

comparison function [116](#c09.xhtml#page116)

copy function [112](#c09.xhtml#page112), [115](#c09.xhtml#page115)

reverse function [118](#c09.xhtml#page118)

search function [117](#c09.xhtml#page117)

sort function [115](#c09.xhtml#page115)

slice of structs

embedding [164](#c13.xhtml#page164)

slices

about [39](#c04.xhtml#page39), [96](#c09.xhtml#page96), [105](#c09.xhtml#page105)

declaring [105](#c09.xhtml#page105)

extending [111](#c09.xhtml#page111)

from an array [105](#c09.xhtml#page105)

from structs [107](#c09.xhtml#page107)

initializing [105](#c09.xhtml#page105)

make function [110](#c09.xhtml#page110)

re-slicing [106](#c09.xhtml#page106), [107](#c09.xhtml#page107)

two-dimensional slices [111](#c09.xhtml#page111), [112](#c09.xhtml#page112)

slice structure

about [108](#c09.xhtml#page108)

capacity [109](#c09.xhtml#page109)

length [109](#c09.xhtml#page109)

pointer [108](#c09.xhtml#page108)

SQL queries

DDL [277](#c20.xhtml#page277)

DML [278](#c20.xhtml#page278)

TCL [278](#c20.xhtml#page278)

SQLyog [278](#c20.xhtml#page278), [279](#c20.xhtml#page279)

string [122](#c10.xhtml#page122), [123](#c10.xhtml#page123)

string constant [42](#c04.xhtml#page42)

string data type [36](#c04.xhtml#page36)

string function

about [123](#c10.xhtml#page123)

iteration function [124](#c10.xhtml#page124), [125](#c10.xhtml#page125)

string length function [123](#c10.xhtml#page123)

string package [130](#c10.xhtml#page130)

string package function

about [130](#c10.xhtml#page130)

count function [132](#c10.xhtml#page132)

IndexAny function [132](#c10.xhtml#page132)

Index function [132](#c10.xhtml#page132)

Join function [134](#c10.xhtml#page134)

LastIndexAny function [133](#c10.xhtml#page133)

LastIndex function [133](#c10.xhtml#page133)

replace function [134](#c10.xhtml#page134)

specific text [131](#c10.xhtml#page131)

split function [135](#c10.xhtml#page135)

string prefix/suffix [131](#c10.xhtml#page131)

ToLower function [130](#c10.xhtml#page130)

ToUpper function [130](#c10.xhtml#page130)

trim function [135](#c10.xhtml#page135)

struct

about [107](#c09.xhtml#page107), [146](#c12.xhtml#page146)

anonymous fields [152](#c12.xhtml#page152)

comparing [155](#c12.xhtml#page155)

copying [154](#c12.xhtml#page154)

creating, with new function [151](#c12.xhtml#page151)

declaring [146](#c12.xhtml#page146), [147](#c12.xhtml#page147)

field, accessing [149](#c12.xhtml#page149)

initializing [148](#c12.xhtml#page148)

pointer [150](#c12.xhtml#page150)

struct function [154](#c12.xhtml#page154)

Structured Query Langauge (SQL) [277](#c20.xhtml#page277)

structures [38](#c04.xhtml#page38)

switch statement [61](#c06.xhtml#page61)

T

text editors [10](#c02.xhtml#page10), [11](#c02.xhtml#page11)

third party package

installing [90](#c08.xhtml#page90)

thread [192](#c16.xhtml#page192)

Transaction Control Language (TCL) [278](#c20.xhtml#page278)

two-dimensional slices [111](#c09.xhtml#page111), [112](#c09.xhtml#page112)

type assertion [175](#c14.xhtml#page175), [176](#c14.xhtml#page176)

type switch [176](#c14.xhtml#page176)

U

unbuffered channel [204](#c17.xhtml#page204)

V

variables [32](#c04.xhtml#page32)

variadic function [80](#c07.xhtml#page80)

W

web application

building [282](#c20.xhtml#page282), [283](#c20.xhtml#page283), [285](#c20.xhtml#page285)\-[290](#c20.xhtml#page290), [292](#c20.xhtml#page292), [296](#c20.xhtml#page296)

package [282](#c20.xhtml#page282)

web development [260](#c20.xhtml#page260)