![](n4upl4fndqg.jpeg)

# Hands-On  
Julia  
Programming

![](n4upl4fndqr.jpeg)

# *An Authoritative Guide to the  
Production-Ready Systems in Julia*

![](n4upl4fndqr.jpeg)

# Sambit Kumar Dash

![](n4upl4fndqs.jpeg)

[www.bpbonline.com](http://www.bpbonline.com)

**FIRST EDITION 2022**

**Copyright © BPB Publications, India**

**ISBN: 978-93-91030-889**

All Rights Reserved. No part of this publication may be reproduced, distributed or transmitted in any form or by any means or stored in a database or retrieval system, without the prior written permission of the publisher with the exception to the program listings which may be entered, stored and executed in a computer system, but they can not be reproduced by the means of publication, photocopy, recording, or by any electronic and mechanical means.

**LIMITS OF LIABILITY AND DISCLAIMER OF WARRANTY**

The information contained in this book is true to correct and the best of author’s and publisher’s knowledge. The author has made every effort to ensure the accuracy of these publications, but publisher cannot be held responsible for any loss or damage arising from any information in this book.

All trademarks referred to in the book are acknowledged as properties of their respective owners but BPB Publications cannot guarantee the accuracy of this information.

![](n4upl4fndqk.jpeg)

[www.bpbonline.com](http://www.bpbonline.com/)

# Foreword

I met Sambit in the early days of Julia. In fact, our first email exchange focused around all the improvements Julia needed in order to become a useful language for data scientists and programmers. In the last few years, Julia has continued to grow and in 2018, the community released Julia 1.0. Over those years, Sambit has made several contributions to several Julia packages for which the Julia community is always grateful. However, code is not sufficient to build a community. It is equally important to have high quality documentation and books that help programmers learn a new language. Hands on Julia Programming is a valuable contribution to a young, modern and exponentially growing language.

The “Why” question is always the most interesting one for anything new. Why did the creators create a new language? Why does it matter? Often, once you understand the motivation that drives an innovation, the rest is easy to follow. Hands on Julia Programming does a great job with setting the stage and getting the reader to really understand the reason and motivation behind Julia. The footnotes that point to JuliaCon presentations and interviews are equally interesting.

From there, Sambit takes the reader through a journey, with hands on the keyboard and covering a lot of ground starting with installing Julia, running the customary “Hello, World”, notebooks, language fundamentals and standard library. The second module covers IDEs, development practices and deployment, whereas the third module covers Julia packages for various data science tasks such as data manipulation, text analysis and deep learning.

Given that Julia solves the two-language problem by combining performance and productivity in one language and that mathematics and machine learning are integral to just about everything, Hands on Julia Programming provides a quick on ramp for programmers to learn Julia and also participate in the open-source community.  
  

**—Viral Shah**  
CEO  
*Julia Computing Inc.*

# Dedicated to

*My Parents*

# About the Author

**Sambit Kumar Dash** is an accomplished business manager with a strong technology focus in bringing technology product ideas to reality, with over 20 years of experience in product and business management, architecture, and research and development.

He has accomplished technology and product knowledge in document technologies, computer security, artificial intelligence, and natural language processing. He has conceived and developed a PDF reader library in the Julia language. This library can be seen at GitHub (**[https://github.com/sambitdash/PDFIO.jl](https://github.com/sambitdash/PDFIO.jl)**). He is passionate about developing new technologies and has eight patent applications in document technologies, computer security, virtualization, and human-computer interfaces. He is currently, developing legal analytics products using AI and Machine Learning through his start-up Lenatics Solutions Private Limited.

Education

*   B.Tech. (Mechanical) IIT Kharagpur
*   M.Tech. (Robotics) IIT Kanpur
*   PGSEM (MBA) IIM Bangalore
*   MBL, NLSIU Bangalore

# About the Reviewers

**Daniel Molina Cabrera** is currently an Associate Professor in Computer Science at University of Granada, Spain. He is a recognized researcher in Artificial Intelligence, particularly in Large Scale Global Optimization, in which he has won two international competitions in 2010 and 2018. Until 2019, he had been chairing IEEE CIS Task Force on Large Scale Optimization. He has published more than 32 research papers for international scientific journals and has more than 4800 citations. He also has many years of experience in programming particularly in automation and web (as back-end developer) and high-level languages like Python and Julia. In both these languages, he has developed several registered packages like DaemonMode.jl. He has been a part of the free software community and open knowledge developing software to make research easier like **tacolab.org** and has given talks in technical conferences like PythonES and JuliaCon 2021.

**Prashant Verma** has over 25 years of experience in Software Development. He holds a Bachelor’s degree in Engineering from MNNIT Allahabad and an MBA (IB) from IIFT. Currently, he is working as an Engineering Manager with Google Cloud Platform managing a team of software engineers working on backup and disaster recovery. Previously, Prashant has worked with Adobe where he was responsible for building PDF readers for mobile platforms, Linux and multiple Unix. He also worked with Amazon, leading their space management team and with Microsoft where he was leading the development of PowerPoint on mobile platforms.

**Tanmay Mohapatra** (**[https://github.com/tanmaykm](https://github.com/tanmaykm)**) has authored and contributed to several Julia packages for parallel and cloud computing. He is currently working as a Principal Software Engineer at Julia Computing Inc.

# Acknowledgement

First of all, I will like to thank my parents and wife, to have supported me during the development of this work. My apologies to them for the numerous family activities and events I postponed in a plea to write the book.

Tanmay Mohapatra introduced me to the Julia Programming Language and helped me with his valuable feedback on several chapters that have made the book better. Niloy Ghosh and Gopal Sharma reviewed parts of the book and provided their valuable inputs as well.

I am grateful to the pioneers of Julia Language Viral Shah, Jeff Bezanson, and Stefan Karpinski for their continuous help and support. Their exchange of notes or discussions on forums to help my interest in the language alive. I will like to thank all the community members and maintainers with who I have interacted as part of contributing to various packages or sharing knowledge over discussions and forum postings that have added to my understanding of the Julia Language.

Special thanks to BPB Publications. Especially to Nrip Jain, for their support, advice, and assistance in creating and publishing this book.

# Preface

Four years back, I started looking at technologies for my venture; there were only Python and R to pick. The Go Language was picking up but not as popular in the AI communities then. The 1.0 version of the Julia Language was not available. There was general skepticism around its efficacy claims.

I heard of Julia from Tanmay. He did not advertise the language for me but just wanted me to take a look. Merely look at it as an open-source project. I liked the language. It had a crisp syntax. The performance benchmarks claimed were impressive; backed by a solid theoretical foundation. The challenges I faced were with lack of consistent package management or environment. In short, no pip or conda to look up. As a developer of the late 90s and early 2000s, I was well-versed with Object-Oriented Programming. So, languages like Python were a natural fit. Julia did not fit that model. It was a small price to pay for the ability to program in a high-performance environment; no need to rewrite for production.

The biggest challenge I faced was the lack of libraries. There were around 1500 libraries, but not every one of them was well maintained or complete in all respects. But, post the 1.0 release, there have been lots of new package additions. The number of packages has reached above 4000. Most new technologies or research are getting translated into new packages in Julia. Once you become conversant, even implementing a part of the code is not hard either. It could be an important criterion in choosing an open-source technology as the code is on a perpetual beta for most software applications today. The Julia community was very welcoming to submitting PRs. There were differences of opinions in exchanges, yet you know the technology and the product gained.

I always ask this question, do skeptics still think of Julia as an experimental language? Do they know they can develop production-ready applications with ease? This book is to affirm and build confidence in the readers; meant for practicing programmers or researchers who would look to Julia for their next production-ready application. Newbies with no prior programming experience may find the book overwhelming due to the cross-domain coverage in the book with significant conceptual shifts. Considering the vast expanse of domains a modern platform encompasses, no one book can give you a complete understanding of the Julia Platform. I will consider my task accomplished; if you find a non-trivial application that you will build with Julia. Secondly, you start looking at Julia repository sources to learn more about the concepts you pick up from the book.

The book is a practitioner's manual. So the exercises are not to test your grasp of the content of a particular chapter; they are thought-provoking. Some of them are addressed in a later chapter as well. If you cannot solve them by the end of a chapter, it is perfectly normal. However, at the end of reading the book, all the exercises shall make you understand the concepts better; drive you towards additional experiments and knowledge acquisition. Some questions may not have a single answer and are of a system design nature.

The book is composed of three sections. The first section consisting of nine chapters will introduce you to the language fundamentals. Unless you are familiar with the language, you are suggested to at least flip through all the chapters to get an overview of the Julia language. Some concepts are detailed; you can skim through them on the first read. The second section comprises five chapters. This section covers programming guidelines, IDEs, debuggers, package management, deployment, etc. You can think of it as a section on tools and techniques. The last section is about a few well-known packages particularly relevant to data analysis and AI/ML. While many other domains have an extensive presence in the Julia ecosystem, we focused on these few packages due to the current focus and interest in the market.

Thanks a lot for choosing the book. I hope you will enjoy learning Julia as I enjoyed introducing you through this book.

# Downloading the code bundle  
and coloured images:

Please follow the link to download the  
***Code Bundle*** and the ***Coloured Images*** of the book:

# [https://rebrand.ly/96ae0c](https://rebrand.ly/96ae0c)

# Errata

We take immense pride in our work at BPB Publications and follow best practices to ensure the accuracy of our content to provide with an indulging reading experience to our subscribers. Our readers are our mirrors, and we use their inputs to reflect and improve upon human errors, if any, that may have occurred during the publishing processes involved. To let us maintain the quality and help us reach out to any readers who might be having difficulties due to any unforeseen errors, please write to us at :

**[errata@bpbonline.com](mailto:errata@bpbonline.com)**

Your support, suggestions and feedbacks are highly appreciated by the BPB Publications’ Family.

Did you know that BPB offers eBook versions of every book published, with PDF and ePub files available? You can upgrade to the eBook version at **[www.bpbonline.com](http://www.bpbonline.com)** and as a print book customer, you are entitled to a discount on the eBook copy. Get in touch with us at **[business@bpbonline.com](mailto:business@bpbonline.com)** for more details.

At **[www.bpbonline.com](http://www.bpbonline.com)**, you can also read a collection of free technical articles, sign up for a range of free newsletters, and receive exclusive discounts and offers on BPB books and eBooks.

# BPB is searching for authors like you

If you're interested in becoming an author for BPB, please visit [**www.bpbonline.com**](http://www.bpbonline.com/) and apply today. We have worked with thousands of developers and tech professionals, just like you, to help them share their insight with the global tech community. You can make a general application, apply for a specific hot topic that we are recruiting an author for, or submit your own idea.

The code bundle for the book is also hosted on GitHub at **[https://github.com/bpbpublications/Hands-on-Julia-Programming](https://github.com/bpbpublications/Hands-on-Julia-Programming)**. In case there's an update to the code, it will be updated on the existing GitHub repository.

We also have other code bundles from our rich catalog of books and videos available at **[https://github.com/bpbpublications](https://github.com/bpbpublications)**. Check them out!

# PIRACY

If you come across any illegal copies of our works in any form on the internet, we would be grateful if you would provide us with the location address or website name. Please contact us at [**business@bpbonline.com**](mailto:business@bpbonline.com) with a link to the material.

# If you are interested in becoming an author

If there is a topic that you have expertise in, and you are interested in either writing or contributing to a book, please visit [**www.bpbonline.com**.](http://www.bpbonline.com/)

# REVIEWS

Please leave a review. Once you have read and used this book, why not leave a review on the site that you purchased it from? Potential readers can then see and use your unbiased opinion to make purchase decisions, we at BPB can understand what you think about our products, and our authors can see your feedback on their book. Thank you!

For more information about BPB, please visit [**www.bpbonline.com**.](http://www.bpbonline.com/)

# Table of Contents

# 

# 

# 

Julia is a fast dynamic language developed keeping high performance as the core objective of the platform. We will outline the capabilities of the language and look forward to programmers and researchers using the language for production environments.

# 

In this chapter, we will cover the following topics:

*   Objectives
*   Purpose of Julia
*   A brief history
*   The book outline
*   Setting up Julia
*   Read-Eval-Print Loop (REPL)
*   Interactive Julia and Jupyter
*   Julia programs

# 

The readers will be able to understand the design considerations of the Julia language. They will get a brief history of the language and the outline of the book. They will also be able to set up the environment and try some simple Julia programs.

# 

A getting started chapter without a program on hello\_world to begin with! Do not get too worried about it; we will get there soon. However, we will like you to understand a little bit about Julia concepts and conventions in order to be able to understand why the language is designed the way it is. This book intends to be a practitioner’s manual and should help you understand the Julia programming platform. We insist you consider Julia as a complete platform beyond a simple programming language to implement practical and production quality software with it. There are a dozen reasons to look at Julia as an alternative to your current scientific programming tools.

# 

Unlike other dynamic languages like Python, R, SPSS, or MATLAB, Julia is designed keeping performance as the central focus of its development. Type determinations and conversions take significant time in most interpreted languages. Julia is fundamentally a **Just-in-Time** (**JIT**) compiled language. The types are determined during runtime and several code segments are compiled based on the types. A multi-dispatch architecture[1](#p21tixfo.html#n4upl4fndg3) based on data types ensures the most efficient implementation is invoked. Julia performance benchmarks are carried out keeping compiled languages like C/C++ in mind. In many of them, Julia almost matches closely to performance levels[2](#p21tixfo.html#n4upl4fndg4) of C/C++. Due to these performance gains, developers can write high-performance libraries in native Julia. This is unlike languages like Python or R that serve as excellent front-end interfaces leaving the backend performing code to native compiled languages like C/C++.

# 

In the world of programming, where COBOL and FORTRAN programs written about half a century ago are still in existence, a decade is definitely a short period of time. Let us look at some of the competing languages such as Python (1990), R (1993), S (1976), SPSS (1968), and MATLAB (the late 1970s). None of these languages were developed with the need for a production-ready data science application development platform. Python started as a general-purpose scripting language; providing easy programming interfaces to develop quick solutions even for non-regular programmers, while R, S, SPSSS, and MATLAB provided excellent prototyping infrastructures for researchers. The first appearance in 2012 gave Julia a new kid in the block image. As you read along, you will realize Julia is really a smart brat. Maintaining backward compatibility with old systems may not be always practical. Python 3.x had many features that were incompatible with Python 2.x; putting programmers into the same level of difficulty to migrate and rewriting in a new language. Julia is modern and built with newer programming paradigms keeping researchers and data scientists in mind[3](#p21tixfo.html#n4upl4fndg5); yet, it integrates effortlessly with native platforms.

# 

Good platforms provide great interfaces and APIs to build flexible and large systems. Better ones embrace industry best practices than reinventing them. Julia is a perfect example of the second kind. It has native integration with LLVM (high-level compiler tools), OpenBLAS (linear algebra), LAPACK (linear algebra), Intel MKL, OpenLibm, Nvidia CUDA, PCRE (regular expressions), and so on. This ensures that the platform is built on proven technologies. Moreover, Julia provides foreign interface binding to languages like C, C++, Python, Java, and FORTRAN. If you are used to the flexibility or power of any such libraries, you can continue to use them in Julia. For example, the Julia plotting interface can easily be federated with Python matplotlib or GR. Packages are continuously being built and maintained for TensorFlow[4](#p21tixfo.html#n4upl4fndg6) for machine learning; Cairo[5](#p21tixfo.html#n4upl4fndg7) for low-level graphics or Qt[6](#p21tixfo.html#n4upl4fndg8) for windowing or Electron JS^(\[[7](#p21tixfo.html#n4upl4fndg9),[8](#p21tixfo.html#n4upl4fndha)\]) for HTML-based client applications, and many more. All these are de-facto industry standard frameworks. Moreover, Julia wrapper packages are being built for commonly used native binary libraries[9](#p21tixfo.html#n4upl4fndhb) like Zlib, OpenSSL and Qt, and so on. And, they are provided as binary distributions.

# 

Julia is designed for researchers who would like to see their contribution made to the production code than having to be rewritten and redesigned for performance and maintainability. The functional programming paradigm ensures any program can be easily extended using compositions than rigidly adhering to pure object-oriented hierarchies. Data encapsulation is a directive. and language constructs do not rigidly block access to underlying attributes of an object.. Multiple dispatch interfaces provide easy polymorphic designs like an object-oriented system. Like most functional programming languages, recursion programming is encouraged where needed while iterative programming is fully supported. Lack of native support for tail-call optimization can be considered a minor bottleneck. It has support for Unicode variables and native set theoretic expressions that help researchers write complete mathematical expressions in Julia. Many researchers in the community develop applications with LaTeX document management systems to be able to present their research in exportable for publications formats. Moreover, some of the works in the Julia community are published in various research publications[10](#p21tixfo.html#n4upl4fndhc). Interactive modes like IJulia and Jupyter provide easy prototyping alongside console-based **REPL**.

# 

Metaprogramming is about generating the code and dynamically executing it. In some languages like C++, templates are based on types and the code is generated for the exact data type during the compilation process. The same exists in Julia as well under parametric data types. While such generic programs are very useful in an object-oriented programming language like C++, Julia goes a step further in virtually creating a complete syntax tree of Julia code and executes the tree-based on input data. This is an extremely flexible kind of metaprogramming that is supported in languages like Lisp or Scheme. Julia has a strong heritage of Lisp and ships with a *FemtoLisp* compiler for some of its low-level parsing functionalities. This not only makes the programs easy to write but also makes functional programming very powerful; there is also a downside of the code becoming too complex for the novice programmers.

# 

The Julia platform is self-sufficient as far as the entire code generation infrastructure is concerned. You do not have to install anything additional if you are installing the platform for normal development work. However, there are integrations with editors like *Emacs*, vi, and *Sublime*[11](#p21tixfo.html#n4upl4fndhd). Fully integrated and managed IDEs are implemented with *Atom* and *Microsoft Code*. You can use these IDEs for functional navigations, line debugging, showing interactive plots, and so on. The toolset integrates seamlessly with source control (git derivatives like *GitHub*, *GitLab*), coverage tools (*CoverAll.io*, *CodeCov*), continuous integration systems (*GitHub Actions*), and so on.

# 

Any platform that is non-extendible is incomplete in today’s world. Julia understands that need and provides a complete package development and management ecosystem. You can use JuliaHub[12](#p21tixfo.html#n4upl4fndhe) to search for the packages you need and deploy them in your environment. With roughly about 4500+ packages, the number is fairly limited in comparison to other platforms like *Python*, *R*, *MATLAB*, and so on. However, for a language that came to a stable interface *version 1.0* in October 2018, this number shows the continual interest in enhancing the platform ecosystem. While some of the functionalities may not exist in Julia, it’s not hard to consider the equivalent C/C++ or Java binaries and integrate them with your Julia code using the native interfaces. The Julia package infrastructure is based on git, which makes it absolutely easy for people to develop their own private repositories. Moreover, a full package and environment management system Pkg provides self-contained environments such that compatibility across packages is maintained.

# 

When you start using Julia, you will realize the system is well suited for cloud-based application development. Julia will work in the backend system for computation layers, leaving the rendering and connection management interfaces to well-defined applications and web servers. While some web-based application servers are developed in Julia, they are mostly experimental. Most code written in Julia is kept in the source code form amenable to JIT compilation. Thus, statically compiled code is not the most common deployment practice in Julia, although the flexibility exists through certain packages[13](#p21tixfo.html#n4upl4fndhf). As a server-based platform, Julia with its collection of packages can be deployed with ease on the cloud platforms like AWS, Azure, or be delivered as *Docker* packages.

# 

Julia is developed as a collection of open-source projects. We will insist on the usage of the term collection of open-source projects as most of the packages used are distributed as open source but may have different licensing than the Julia language. The Julia language is developed under the MIT License[14](#p21tixfo.html#n4upl4fndhg), which provides significant flexibility in terms of using and extending the sources. The same also makes it easy for anyone to include complete Julia or its derivatives as a part of the other applications they are developing. Most packages developed in Julia also follow similar licensing schemes. Make sure you review the licensing flexibilities for the packages[15](#p21tixfo.html#n4upl4fndhh) before you use them in your commercially licensed products.

# 

Just like the licensing, Julia architecturally is designed for federated enterprise environments. One can use their own private repository for applications and packages, deployment on enterprise-centric internal cloud infrastructures, and packages to integrate with enterprise federated authentication and authorization schemes. The Julia language also maintains all major versions like 1.0 as **long-term support** (**LTS**) to cater to enterprise support requirements[16](#p21tixfo.html#n4upl4fndhi). Most importantly, Julia is supported by a *Julia Computing Inc*.[17](#p21tixfo.html#n4upl4fndhj), an enterprise that provides tools, supports Julia, and is actively involved in the community activities of Julia programming. Enterprises interested in tools from Julia computing will be able to obtain various support plans from them. All founding members of the Julia language are currently employed in Julia Computing.

# 

Any open-source software is good as long as there is continued interest in the community. Started with just three researchers and their advisor, the team expanded getting into many academic institutes and researchers showing active interest in it. The language’s main repository has about a thousand contributors, 30,000+ stars[18](#p21tixfo.html#n4upl4fndhk) and 4200+ forks[19](#p21tixfo.html#n4upl4fndhl). Beyond the main language repository, many developers contribute to the 4500+ packages available in the Julia packages ecosystem. The repositories are maintained in GitHub. While most communication is carried out as part of pull requests and issues tracking GitHub, specific project groups interact with Discourse, Slack, and GitHub projects as well. The Julia community conducts JuliaCon[20](#p21tixfo.html#n4upl4fndhm), a conference dedicated to the development and evangelizing of the Julia ecosystem. There are many meetup groups where communities interact and exchange ideas. Free and paid courses are available to understand the ecosystem[21](#p21tixfo.html#n4upl4fndhn) better.

# 

The most important advantage of working on a relatively new programming language like Julia is the flexibility to look into the code and understand the implementation, suggest changes by raising issues, submit PRs, and actively contribute to the environment. The ability and interest to contribute where you can bring in the change you desire definitely needs to be explored for more discerning programmers. For students, contributions into Julia can be funded with *Google Summer of Code* sponsorship[22](#p21tixfo.html#n4upl4fndho) projects; thus, meeting their professional internship needs. If you are a developer who enjoys getting into the thick of action, here is a platform that you can work on as well as contribute to. And the community is one of the most welcoming ones in terms of encouraging changes from almost novice programmers. This also is a quick way to learn and understand the system better.

# 

Julia was conceived about a decade ago but it came to prominence in 2012 as an open-source project. Started by three computer scientists *Jeff Bezanson*, *Stefan Karpinski,* and *Viral B*. *Shah* under the guidance of *Prof. Alan Edelman* of *MIT*, Julia had a very humble beginning as an open-source project. A significant problem they realized was the need to first develop prototypes as researchers and then productize the code into a lower-level precompiled language to get that extra performance of a compiled language. Julia tries to break that barrier of prototype vs. production. The authors of Julia chose the name Julia as a tribute to the mathematical concept of Julia sets. They insist the Julia programming language or Julia language be used while communicating. Julia when used as a proper noun must be used in a gender-neutral form. We will respect the same convention in this book.

# 

The author started working with the system about three years back in search of a programming language that was specifically designed for data science projects. With Julia 1.0 still in the development phases, there was a deeper engagement needed to understand the language. Surprisingly, for a language that is just a few years old, there are quite a few books written. There is good quality documentation already available. However, many books written on pre-1.0 versions are no longer relevant as the interfaces of the language have changed. Secondly, no book provides exposure to the entire Julia ecosystem that an experienced professional will look for. This book is an attempt to address both these needs.

The book is composed of 3 modules and 17 chapters.

# 

This module is focused on understanding the Julia programming language.

# 

This chapter states the rationale and history behind the Julia language, provides the initial installation and configuration process, and shows cases some simple examples toward the end of the chapter.

# 

Julia is an optionally typed language. While there is no necessity for a data type to be specified in a program and the types are inferred automatically during on demand JIT compilation. Yet, Julia provides the flexibility to specify data types. This enables a behavioral polymorphism in a dynamic typed language, secondly, dispatch to specific method becomes easier and enables faster execution and thus performance gains. Types can be simple types like `<strong>int</strong>`, `<strong>float</strong>`, `<strong>Boolean</strong>`, and so on. or user-defined types like structures. They can also be immutable objects like tuples. This chapter will help us take a quick look at all these data types.

# 

Programming is incomplete without a clear-cut control flow of data and instructions. In most cases, the flow is controlled while fulfilling a condition. Sometimes the conditions can be a simple variable comparison with another value or could be repetitive till a particular condition is met. The control flow logic may be needed for taking remedial actions when an exceptional condition occurs. These varied control flows are achieved by specialized language constructs. In Julia, `<strong>if…else</strong>`, `<strong>for</strong>`, `<strong>while</strong>` loops are used for most of the regular loop constructions, while `<strong>try…catch</strong>` are used for exceptional conditions. Similarly, Julia provides tasks-based control flows for parallel execution for cooperative multi-tasking and preemptive multi-tasking with threads.

# 

If data types are nouns of communication, then functions play the role of a verb. Functions provide a mechanism to make small chunks of code that can meaningfully accomplish a task; the task can be repetitive or can represent a logically separable concept. Functions can take multiple inputs and return one or more output values as a tuple. The multiple dispatch architecture of Julia enables different functions are invoked based on the data type of input parameters. This enables a polymorphic behavior of the functions and can be called as **methods**. The polymorphic behavior with parametric data types can enable the implementation of reusable algorithms. Julia does not support automatic promotion across data types but provides enablers for programmers to define their own type conversion and promotion rules. We will take a look at recursion which is considered as a fundamental method of control flow in many algorithmic tasks, hence given emphasis in functional languages. Lastly, we will look at anonymous functions which are similar to the concept of lambda in languages like *Lisp*. Anonymous functions are used as predicates or callbacks in many functional language applications.

# 

Iterations are carried out on a collection of objects to achieve a repetitive task for which a certain predicate is fulfilled. Second, objects are stored in a collection to ensure certain operations are most efficient. For example, linear integer-based iteration along a vector is very efficient while a dictionary is ideal to match a value for a given key. Similarly, sets are useful data types for checking for membership. Julia provides certain standard data types like `<strong>Array</strong>`, `<strong>Dict</strong>`, and `<strong>Set</strong>`. While these address the needs of a specific class of computational problems, it is insufficient to address a vast majority of issues faced in the scientific computing. Hence, Julia provides an iteration architecture that can be implemented by custom data structures. `<strong>DataStructures.jl</strong>` package provides a class of commonly used data structures.

# 

Programming for mathematics or scientific discipline is incomplete without matrix and matrix operations. Arrays are a foundation to that concept. Arrays can be one, two, or multi-dimensional. While one-dimensional arrays are called **Vectors** and two-dimensional **Matrix**, there are arrays that can be sparse. For example, a diagonal matrix has only the diagonal elements filled in. Similarly, dense representation of arrays can have a large number of elements filled in. It will be important to understand the array representations, the indexing schemes that can be represented by the arrays, how to access a small subset of an array and conduct localized operations on them or any representational aspects that can make it easier for using linear algebra operations.

# 

Strings are used for the textual presentation of information; when no other structure can represent the data effectively data can be presented as strings. Julia strings follow the Unicode specification and are encoded using the UTF-8 encoding. However, transformations can be carried out into other encodings with ease. Strings can also be considered as collections of characters. In this chapter, we will look at methods applicable to strings and their applications. Non-standard strings can be developed for custom applications while they continue to support the String framework. Regular expressions are another important concept that is utilized extensively for text pattern matching. Julia utilizes the PCRE engine for regular expressions. Lastly, we shall see how formatted outputs can be created for objects for output to terminals or file systems.

# 

Metaprogramming is conceptually a mechanism of dynamically generating code that can be run later. This late binding approach provides the flexibility in creating code segments based on the dynamic states of the application. Most of such codes are written as macros. As part of this chapter, we will analyze how to write macros. Some macros like the string literals have special meanings and they aid compact representation of string-like sequences. We will also review generated functions that can help create complex non-standard dispatch rules. Lastly, we will look at the implementations of certain commonly used macros and understand their intent and implementation.

# 

Standard libraries are the heart of a programming language. Julia functionalities are arranged in various modules. Core, Base, and Main are some of the predefined modules. In this chapter, we will touch upon a few APIs from the Base modules. Then look at additional modules that represent the standard libraries. Julia has a rich set of predefined functionalities for commonly used tasks.

# 

This module familiarizes the reader with the development environment.

# 

Every programming language has certain suggested guidelines in writing programs for better readability, maintainability, and performance. Some are purely on the basis of style guides suggested by the language development practices, some are design guidelines that help in keeping the code extendable and maintainable over the complete life cycle. Lastly, guidelines that help write high-performance code. We will discuss the first two in this chapter and the last one as we elaborate on performance management in the next chapter.

# 

Performance is the key to scientific computing and for Julia it is one of the fundamental design considerations[23](#p21tixfo.html#n4upl4fndhp). Hence, there is utmost focus in ensuring every code written in Julia can easily be timed and can be reviewed for any anomalies that can lead to a performance penalty. Julia provides general guidelines for performance improvements, provides many tools to analyze performance bottlenecks and carry out benchmark against standards. In this chapter, we will review many such tools that will aid in the improvement of code performance.

# 

**Integrated development environments** (**IDE**) are becoming common in today’s application development. As much as they provide a wide variety of views of multiple files and their interrelations, they also help in accomplishing tasks like compilation, running the code and viewing results with visualizations. As a scientific computing language, algorithm-driven applications are developed in Julia. REPL is used extensively to try out small chunks of code before they are finally added to the larger application. Debugging line by line using a line debugger is also carried out in some circumstances. We will look at Julia’s integration with editors like emacs and vi. Also, work with *Atom* and *Microsoft Code* for a complete IDE experience.

# 

Although, named as package management, this chapter is about code organization for easier management and deployment of applications. Managing code may become complex as it may depend on other components. There may be dependency issues due to version incompatibilities. The code needs to be tested automatically on check-in, continuous integration frameworks should be able to run and any version management needed should be carried out with ease. In Julia, code is typically composed of projects, packages, and modules. Packages are well-defined organizations of code that help manage continuous integration, automated testing, document creation, and deployment with the least effort. There is an inherent structure between package management and git APIs that makes the package management part of the development process. Moreover, Julia provides environments that can be used to establish an isolated and consistent package sets for specific application requirements.

# 

Any application is as good as it’s deployed in the cloud in a production environment. We will review how effectively Julia can be used to invoke AWS services and deploy solutions using the AWS cloud services. Similarly, Julia can be used easily in the Azure environment. There is also a strong integration framework with Kubernetes.

# 

The last module introduces a few packages that are commonly used in data science and related applications.

# 

Data is central to all data science applications. Data may be available in various file types. We will begin with `<strong>FileIO</strong>` set of data acquisition APIs that will help read data from various file types into Julia. We will also look into `<strong>PDFIO</strong>`, a package designed to read PDF files. Further, the data can be read into `<strong>DataFrames</strong>` for some specific data transformation tasks. We will also see how the data can be sampled effectively for various data-centric applications. We will review Julia Plotting in the visualization of data.

# 

Text Analytics is the science of obtaining meaningful insights from unstructured text data. While natural language processing is a form of text analytics, text analytics can be carried out even with simpler techniques and rules. Simple pattern matching and regular expressions can provide some minimal level of text analytics. `<strong>TextAnalysis.jl</strong>` and related packages will be utilized to show some advanced text analysis in Julia.

# 

Neural networks have become the lingua franca of machine learning techniques. The `<strong>Flux.jl</strong>` package in Julia provides excellent APIs to model neural networks of various complexities. As part of this chapter, we will delve into how to write simple deep learning models and try to solve some simple problems using neural networks. Most of the models are picked up from `<strong>model-zoo</strong>` sample code for neural network modeling with the Flux APIs.

# 

Julia platform binaries are available for the following operating systems:

*   Linux (x86 and ARM)
*   Windows
*   Mac OS
*   FreeBSD (x86)

In all our discussions in this book, we will keep the focus on Windows and Linux (x86) platforms only.

# 

Pre-built binary packages for Julia are available in the Julia language website at: **[https://julialang.org/downloads/](https://julialang.org/downloads/)**

While certain Linux distributions may be packaging Julia as a part of their releases, please ensure you are installing the latest releases from Julia Language website.

Julia binaries are typically named as: `<strong>julia-&lt;version&gt;-&lt;arch&gt;.&lt;package-ext&gt;</strong>`

For example, Julia 1.6.1 Linux x86 64-bit package is named as: `<strong>julia-1.6.1-linux-x86_64.tar.gz</strong>`

Similarly, the Windows 64-bit version is named as: `<strong>julia-1.6.1-win64.exe</strong>`

# 

Julia Platform is evolving continuously. Hence, it may be advisable to use the latest minor version while learning from this book. The current stable version released is *Julia 1.6*. Julia minor releases introduce a lot of new features and worthwhile to take a look at periodically. However, *Julia 1.0.x* version is a long term supported version for Julia. The blog article provides a detailed explanation of the versioning process for Julia: **[https://julialang.org/blog/2019/08/release-process/](https://julialang.org/blog/2019/08/release-process/)**

**Note: This book is written based on the Julia version 1.6.x, which is the current released version of Julia. The concepts described in the book are generic in nature and are applicable to a later version of the language. However, it is possible some of the outputs from a later version of Julia may not match to the results and examples provided in this book. Hence, the sources used in the book are provided as Jupyter notebooks in a GitHub repository at: [https://github.com/bpbpublications/Hands-on-Julia-Programming](https://github.com/bpbpublications/Hands-on-Julia-Programming). Readers are requested to access the repository for the latest updates to the source code.**

# 

Julia binaries being mere `<strong>.tar.gz</strong>` packages, they can be easily installed in the user’s home directory. We suggest the following instructions for a simple installation in your home directory.

1.  Open a terminal with a bash shell.
2.  Use the following commands to create a directory julia-versions and enter into the directory:
    
    `<strong>$ mkdir ~/julia-versions $ cd ~/julia-versions</strong>`
    
3.  Now un-archive the package downloaded in the Julia-versions folder.
    
    `<strong>$ tar -xvzf julia-x.y.z-linux-x86_64.tar.gz</strong>`
    
4.  Now change the directory to the home directory and create a symbolic link to the Julia version installed.
    
    `<strong>$ cd $ ln –s ~/julia-versions/julia-x.y.z julia</strong>`
    
5.  Add Julia bin directory to the bash startup script (`<strong>.bashrc</strong>` or `<strong>.bash_profile</strong>`) `<strong>PATH</strong>` variable by following this command:
    
    `<strong>$ export PATH=”/home/user/julia/bin:$PATH”</strong>`
    
6.  Re-launch the bash shell again.

# 

Julia provides an installer for the Windows platform. The installer can be launched by a user without any administrator privileges. Here are the recommended steps on a Windows platform:

1.  Click on the installer executable to launch it.
2.  Browse to the path where you will like to install Julia: ![](n4upl4fndqb.jpeg)
    
    **Figure 1.1:** Julia Windows Installer
    
    The default path is: `<strong>%LOCALAPPDATA%\Programs\Julia x.y.z</strong>`
    
3.  Add the Julia bin directory: `<strong>%LOCALAPPDATA%\Programs\Julia x.y.z\bin</strong>` to the environment variable following steps described in the link: **[https://julialang.org/downloads/platform/#windows](https://julialang.org/downloads/platform/#windows)**

# 

Now that, you have installed and configured the variables as suggested in the previous steps, on the command prompt type `<strong>julia</strong>`. You should see the version information of Julia and a `<strong>julia</strong>` prompt. This is called as a **REPL** which you can use for typing your code and quickly verifying the results

![](n4upl4fndqc.jpeg)

Let us try few experiments at the REPL prompt.

`<strong>julia&gt; 2 + 2</strong>`

`<strong>4</strong>`

`<strong>julia&gt; 2.0 + 2</strong>`

`<strong>4.0</strong>`

`<strong>julia&gt; println("Hello, World!!!")</strong>`

`<strong>Hello, World!!!</strong>`

The examples are rather trivial save after every computation the results are printed. If you do not want to print something in the REPL use a semicolon (;) symbol at the end of the sentence. However, using a semicolon will have no effect where explicit `<strong>println</strong>` is used. Now let’s look at the same samples using semicolons.

`<strong>julia&gt; 2 + 2;</strong>`

`<strong>julia&gt; 2.0 + 2;</strong>`

`<strong>julia&gt; println("Hello, World!!!");</strong>`

`<strong>Hello, World!!!</strong>`

Why is this behavior then? We will keep the answer to the next chapter when we discuss data types and the concept of nothing.

REPL provides a shell-based console to interactively interact with Julia. However, this is not very helpful for graphical output like plots or images.

# [24](#p21tixfo.html#n4upl4fndhq)

Jupyter is designed for creating interactive browser compatible shells for languages like Julia, Python and R. Simple web-based notebooks can be created for tutorials and training materials. In Julia, this integration is carried out by a package called `<strong>IJulia</strong>`. The following steps need to be carried out in the `<strong>julia</strong>` shell to be able to configure Jupyter and Launch a Jupyter Notebook.

`<strong>julia&gt;]<a id="ftn25a" href="#ftn25"><sup>25</sup></a>add IJulia</strong>`

``<strong>Updating registry at `~/.julia/registries/General` …</strong>``

`<strong>julia&gt; using IJulia</strong>`

`<strong>[Info: Precompiling IJulia [7073ff75-…-fcdaad2a7d2a] julia&gt; notebook()</strong>`

``<strong>[Info: running `/home/sambit/anaconda3/bin/jupyter notebook`</strong>``

At the end of the command, a new browser window will open up with Jupyter as shown in the following screenshot:

![](n4upl4fndqd.jpeg)

**Figure 1.2:** Jupyter browser window launched from Julia REPL

Create a new notebook with *Julia 1.6.0* as the kernel using the GUI as shown as follows:

![](n4upl4fndqe.jpeg)

**Figure 1.3:** Creating a new notebook with Julia 1.6.0 kernel

Lastly, type in the commands and run them as shown in the following screenshot:

![](n4upl4fndqf.jpeg)

**Figure 1.4:** An interactive Jupyter notebook with sample code

You can type in and run; the results are shown in the same browser window.

# 

While interactive expressions are quick ways to try something on a terminal and review the outputs, real-world applications require large chunks of code pieces be run. In Julia, you type all the relevant code in a file. The Julia programs conventionally have an extension of `<strong>.jl</strong>`. Open the text editor of your choice and type in the following code in a file and save as `<strong>example01.jl</strong>`.

`# example01.jl`

`println("2 + 2 = ", 2+2)`

`println("2 + 2.0 = ", 2+2.0)`

`println("Hello World!!!")`

The code we wrote earlier is provided. A `<strong>println</strong>` command is used in every line to showcase the line is run and output is printed on the terminal.

At the command prompt run `<strong>julia</strong>`. Then at the julia prompt invoke the command as shown and you should see the output:

`<strong>$ julia</strong>`

`<strong>julia&gt; include("example01.jl")</strong>`

`<strong>2 + 2 = 4</strong>`

`<strong>2 + 2.0 = 4.0</strong>`

`<strong>Hello World!!!</strong>`

Another way to run a Julia program will be to run at the command line as shown:

`<strong>$ julia example01.jl 2 + 2 = 4 2 + 2.0 = 4.0 Hello World!!!</strong>`

We will learn more details about how to write complex programs and organize them in a later chapter. `<strong>include</strong>` is also used to embed the code from one julia file into another.

# 

Julia is a very powerful language. Although designed for data science applications, the language can be used as a general-purpose language. We started looking at various capabilities the language offers and went onto understand how the book is organized. We installed Julia. We launched the REPL and Jupyter notebooks to try out a few simple Julia language features. Now that the environment is set up, we will take a deep dive into the Julia Platform. In the next chapter, we will look into the type system in Julia, how a dynamic typed language interprets data types internally, and look deeper into a few code examples highlighting the same.

# 

1.  Install Julia on the machine of your choice and start the REPL.
2.  Install IJulia and Jupyter. Make sure you can run Julia code in the Jupyter notebook.

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

[1](#p21tixfo.html#n4upl4fndhr) Stefan Karpinski, The Unreasonable Effectiveness of Multiple Dispatch, JuliaCon 2019, **[https://www.youtube.com/watch?v=kc9HwsxE1OY](https://www.youtube.com/watch?v=kc9HwsxE1OY)**

[2](#p21tixfo.html#n4upl4fndhs) Julia Micro-Benchmarks **[https://julialang.org/benchmarks/](https://julialang.org/benchmarks/)**

[3](#p21tixfo.html#n4upl4fndht) Peter Norvig, Director of Research at Google, would have preferred Julia over Python for his research work, Gradient Descent Podcast, **[https://www.youtube.com/watch?v=hVW1mwLtDcI](https://www.youtube.com/watch?v=hVW1mwLtDcI)**

[4](#p21tixfo.html#n4upl4fndhu) TensorFlow.jl GitHub Repository **[https://github.com/malmaud/TensorFlow.jl](https://github.com/malmaud/TensorFlow.jl)**

[5](#p21tixfo.html#n4upl4fndhv) Cairo.jl GitHub Repository

[6](#p21tixfo.html#n4upl4fndhw) QML.jl GitHub Repository

[7](#p21tixfo.html#n4upl4fndhx) Blink.jl (**[https://github.com/JuliaGizmos/Blink.jl](https://github.com/JuliaGizmos/Blink.jl)**)

[8](#p21tixfo.html#n4upl4fndhy) Electron.jl (**[https://github.com/davidanthoff/Electron.jl](https://github.com/davidanthoff/Electron.jl)**)

[9](#p21tixfo.html#n4upl4fndhz) JuliaBinaryWrappers **[https://github.com/JuliaBinaryWrappers](https://github.com/JuliaBinaryWrappers)**

[10](#p21tixfo.html#n4upl4fndh0) Research, Julia Language Website, **[https://julialang.org/research/](https://julialang.org/research/)** last accessed 4^(th) Dec 2020

[11](#p21tixfo.html#n4upl4fndh1) JuliaEditorSupport, GitHub Repositories, **[https://github.com/JuliaEditorSupport](https://github.com/JuliaEditorSupport)**

[12](#p21tixfo.html#n4upl4fndh2) JuliaHub, **[https://juliahub.com/ui/Home](https://juliahub.com/ui/Home)**

[13](#p21tixfo.html#n4upl4fndh3) PackageCompiler, **[https://github.com/JuliaLang/PackageCompiler.jl](https://github.com/JuliaLang/PackageCompiler.jl)**

[14](#p21tixfo.html#n4upl4fndh4) Julia Language is licensed under the MIT License. An exception statement is made on specific components that may have different licenses. **[https://github.com/JuliaLang/julia/blob/master/LICENSE.md](https://github.com/JuliaLang/julia/blob/master/LICENSE.md)**

[15](#p21tixfo.html#n4upl4fndh5) JuliaHub provides UI to search based on licenses

[16](#p21tixfo.html#n4upl4fndh6) Julia’s Release Process, **[https://julialang.org/blog/2019/08/release-process/](https://julialang.org/blog/2019/08/release-process/)**

[17](#p21tixfo.html#n4upl4fndh7) Julia Computing, **[https://juliacomputing.com/](https://juliacomputing.com/)**

[18](#p21tixfo.html#n4upl4fndh8) In a GitHub repository, a user can assign a star to a repository. This is one way to suggest, a developer is interested in the repository. Some people use these stars as bookmarks for future references.

[19](#p21tixfo.html#n4upl4fndh9) Julia GitHub repository, **[https://github.com/JuliaLang/julia](https://github.com/JuliaLang/julia)** as on 4^(th) Dec. 2020.

[20](#p21tixfo.html#n4upl4fndia) This annual conference is being organized from 2014. JuliaCon, 2020, **[https://juliacon.org/2020/](https://juliacon.org/2020/)**

[21](#p21tixfo.html#n4upl4fndib) The Julia Community, **[https://julialang.org/community/](https://julialang.org/community/)**

[22](#p21tixfo.html#n4upl4fndic) Julia Seasons of Contribution, **[https://julialang.org/jsoc/](https://julialang.org/jsoc/)**

[23](#p21tixfo.html#n4upl4fndid) Jeff Bezanson Stefan Karpinski Viral B. Shah Alan Edelman, Why We Created Julia?, 14^(th) Feb 2012, Julia Blogs, **[https://julialang.org/blog/2012/02/why-we-created-julia/](https://julialang.org/blog/2012/02/why-we-created-julia/)**

[24](#p21tixfo.html#n4upl4fndie) `<strong>Pluto</strong>` is another notebook technology that is exclusively developed for the Julia environment. For details, refer to **[https://github.com/fonsp/Pluto.jl](https://github.com/fonsp/Pluto.jl)**

\] in the beginning of a command, makes the REPL to enter into a pkg mode. In this mode, package management tasks like adding, removing, or updating packages can be carried out.

Any open-source software is good as long as there is continued interest in the community. Started with just three researchers and their advisor, the team expanded getting into many academic institutes and researchers showing active interest in it. The language’s main repository has about a thousand contributors, 30,000+ stars18 and 4200+ forks19. Beyond the main language repository, many developers contribute to the 4500+ packages available in the Julia packages ecosystem. The repositories are maintained in GitHub. While most communication is carried out as part of pull requests and issues tracking GitHub, specific project groups interact with Discourse, Slack, and GitHub projects as well. The Julia community conducts JuliaCon20, a conference dedicated to the development and evangelizing of the Julia ecosystem. There are many meetup groups where communities interact and exchange ideas. Free and paid courses are available to understand the ecosystem21 better.

Any open-source software is good as long as there is continued interest in the community. Started with just three researchers and their advisor, the team expanded getting into many academic institutes and researchers showing active interest in it. The language’s main repository has about a thousand contributors, 30,000+ stars18 and 4200+ forks19. Beyond the main language repository, many developers contribute to the 4500+ packages available in the Julia packages ecosystem. The repositories are maintained in GitHub. While most communication is carried out as part of pull requests and issues tracking GitHub, specific project groups interact with Discourse, Slack, and GitHub projects as well. The Julia community conducts JuliaCon20, a conference dedicated to the development and evangelizing of the Julia ecosystem. There are many meetup groups where communities interact and exchange ideas. Free and paid courses are available to understand the ecosystem21 better.

Julia’s Release Process, **[https://julialang.org/blog/2019/08/release-process/](https://julialang.org/blog/2019/08/release-process/)**

JuliaHub provides UI to search based on licenses

Julia Language is licensed under the MIT License. An exception statement is made on specific components that may have different licenses. **[https://github.com/JuliaLang/julia/blob/master/LICENSE.md](https://github.com/JuliaLang/julia/blob/master/LICENSE.md)**

PackageCompiler, **[https://github.com/JuliaLang/PackageCompiler.jl](https://github.com/JuliaLang/PackageCompiler.jl)**

Julia GitHub repository, **[https://github.com/JuliaLang/julia](https://github.com/JuliaLang/julia)** as on 4^(th) Dec. 2020.

In a GitHub repository, a user can assign a star to a repository. This is one way to suggest, a developer is interested in the repository. Some people use these stars as bookmarks for future references.

Julia Computing, **[https://juliacomputing.com/](https://juliacomputing.com/)**

JuliaHub, **[https://juliahub.com/ui/Home](https://juliahub.com/ui/Home)**

JuliaEditorSupport, GitHub Repositories, **[https://github.com/JuliaEditorSupport](https://github.com/JuliaEditorSupport)**

Research, Julia Language Website, **[https://julialang.org/research/](https://julialang.org/research/)** last accessed 4^(th) Dec 2020

Stefan Karpinski, The Unreasonable Effectiveness of Multiple Dispatch, JuliaCon 2019, **[https://www.youtube.com/watch?v=kc9HwsxE1OY](https://www.youtube.com/watch?v=kc9HwsxE1OY)**

Cairo.jl GitHub Repository

TensorFlow.jl GitHub Repository **[https://github.com/malmaud/TensorFlow.jl](https://github.com/malmaud/TensorFlow.jl)**

Peter Norvig, Director of Research at Google, would have preferred Julia over Python for his research work, Gradient Descent Podcast, **[https://www.youtube.com/watch?v=hVW1mwLtDcI](https://www.youtube.com/watch?v=hVW1mwLtDcI)**

Julia Micro-Benchmarks **[https://julialang.org/benchmarks/](https://julialang.org/benchmarks/)**

JuliaBinaryWrappers **[https://github.com/JuliaBinaryWrappers](https://github.com/JuliaBinaryWrappers)**

Electron.jl (**[https://github.com/davidanthoff/Electron.jl](https://github.com/davidanthoff/Electron.jl)**)

Blink.jl (**[https://github.com/JuliaGizmos/Blink.jl](https://github.com/JuliaGizmos/Blink.jl)**)

QML.jl GitHub Repository

The Julia platform is self-sufficient as far as the entire code generation infrastructure is concerned. You do not have to install anything additional if you are installing the platform for normal development work. However, there are integrations with editors like *Emacs*, vi, and *Sublime*11. Fully integrated and managed IDEs are implemented with *Atom* and *Microsoft Code*. You can use these IDEs for functional navigations, line debugging, showing interactive plots, and so on. The toolset integrates seamlessly with source control (git derivatives like *GitHub*, *GitLab*), coverage tools (*CoverAll.io*, *CodeCov*), continuous integration systems (*GitHub Actions*), and so on.

Performance is the key to scientific computing and for Julia it is one of the fundamental design considerations23. Hence, there is utmost focus in ensuring every code written in Julia can easily be timed and can be reviewed for any anomalies that can lead to a performance penalty. Julia provides general guidelines for performance improvements, provides many tools to analyze performance bottlenecks and carry out benchmark against standards. In this chapter, we will review many such tools that will aid in the improvement of code performance.

Unlike other dynamic languages like Python, R, SPSS, or MATLAB, Julia is designed keeping performance as the central focus of its development. Type determinations and conversions take significant time in most interpreted languages. Julia is fundamentally a **Just-in-Time** (**JIT**) compiled language. The types are determined during runtime and several code segments are compiled based on the types. A multi-dispatch architecture1 based on data types ensures the most efficient implementation is invoked. Julia performance benchmarks are carried out keeping compiled languages like C/C++ in mind. In many of them, Julia almost matches closely to performance levels2 of C/C++. Due to these performance gains, developers can write high-performance libraries in native Julia. This is unlike languages like Python or R that serve as excellent front-end interfaces leaving the backend performing code to native compiled languages like C/C++.

`<strong>Pluto</strong>` is another notebook technology that is exclusively developed for the Julia environment. For details, refer to **[https://github.com/fonsp/Pluto.jl](https://github.com/fonsp/Pluto.jl)**

Jeff Bezanson Stefan Karpinski Viral B. Shah Alan Edelman, Why We Created Julia?, 14^(th) Feb 2012, Julia Blogs, **[https://julialang.org/blog/2012/02/why-we-created-julia/](https://julialang.org/blog/2012/02/why-we-created-julia/)**

Julia Seasons of Contribution, **[https://julialang.org/jsoc/](https://julialang.org/jsoc/)**

The Julia Community, **[https://julialang.org/community/](https://julialang.org/community/)**

This annual conference is being organized from 2014. JuliaCon, 2020, **[https://juliacon.org/2020/](https://juliacon.org/2020/)**

The most important advantage of working on a relatively new programming language like Julia is the flexibility to look into the code and understand the implementation, suggest changes by raising issues, submit PRs, and actively contribute to the environment. The ability and interest to contribute where you can bring in the change you desire definitely needs to be explored for more discerning programmers. For students, contributions into Julia can be funded with *Google Summer of Code* sponsorship22 projects; thus, meeting their professional internship needs. If you are a developer who enjoys getting into the thick of action, here is a platform that you can work on as well as contribute to. And the community is one of the most welcoming ones in terms of encouraging changes from almost novice programmers. This also is a quick way to learn and understand the system better.

Julia is designed for researchers who would like to see their contribution made to the production code than having to be rewritten and redesigned for performance and maintainability. The functional programming paradigm ensures any program can be easily extended using compositions than rigidly adhering to pure object-oriented hierarchies. Data encapsulation is a directive. and language constructs do not rigidly block access to underlying attributes of an object.. Multiple dispatch interfaces provide easy polymorphic designs like an object-oriented system. Like most functional programming languages, recursion programming is encouraged where needed while iterative programming is fully supported. Lack of native support for tail-call optimization can be considered a minor bottleneck. It has support for Unicode variables and native set theoretic expressions that help researchers write complete mathematical expressions in Julia. Many researchers in the community develop applications with LaTeX document management systems to be able to present their research in exportable for publications formats. Moreover, some of the works in the Julia community are published in various research publications10. Interactive modes like IJulia and Jupyter provide easy prototyping alongside console-based **REPL**.

When you start using Julia, you will realize the system is well suited for cloud-based application development. Julia will work in the backend system for computation layers, leaving the rendering and connection management interfaces to well-defined applications and web servers. While some web-based application servers are developed in Julia, they are mostly experimental. Most code written in Julia is kept in the source code form amenable to JIT compilation. Thus, statically compiled code is not the most common deployment practice in Julia, although the flexibility exists through certain packages13. As a server-based platform, Julia with its collection of packages can be deployed with ease on the cloud platforms like AWS, Azure, or be delivered as *Docker* packages.

In the world of programming, where COBOL and FORTRAN programs written about half a century ago are still in existence, a decade is definitely a short period of time. Let us look at some of the competing languages such as Python (1990), R (1993), S (1976), SPSS (1968), and MATLAB (the late 1970s). None of these languages were developed with the need for a production-ready data science application development platform. Python started as a general-purpose scripting language; providing easy programming interfaces to develop quick solutions even for non-regular programmers, while R, S, SPSSS, and MATLAB provided excellent prototyping infrastructures for researchers. The first appearance in 2012 gave Julia a new kid in the block image. As you read along, you will realize Julia is really a smart brat. Maintaining backward compatibility with old systems may not be always practical. Python 3.x had many features that were incompatible with Python 2.x; putting programmers into the same level of difficulty to migrate and rewriting in a new language. Julia is modern and built with newer programming paradigms keeping researchers and data scientists in mind3; yet, it integrates effortlessly with native platforms.

Any platform that is non-extendible is incomplete in today’s world. Julia understands that need and provides a complete package development and management ecosystem. You can use JuliaHub12 to search for the packages you need and deploy them in your environment. With roughly about 4500+ packages, the number is fairly limited in comparison to other platforms like *Python*, *R*, *MATLAB*, and so on. However, for a language that came to a stable interface *version 1.0* in October 2018, this number shows the continual interest in enhancing the platform ecosystem. While some of the functionalities may not exist in Julia, it’s not hard to consider the equivalent C/C++ or Java binaries and integrate them with your Julia code using the native interfaces. The Julia package infrastructure is based on git, which makes it absolutely easy for people to develop their own private repositories. Moreover, a full package and environment management system Pkg provides self-contained environments such that compatibility across packages is maintained.

# 24

Unlike other dynamic languages like Python, R, SPSS, or MATLAB, Julia is designed keeping performance as the central focus of its development. Type determinations and conversions take significant time in most interpreted languages. Julia is fundamentally a **Just-in-Time** (**JIT**) compiled language. The types are determined during runtime and several code segments are compiled based on the types. A multi-dispatch architecture1 based on data types ensures the most efficient implementation is invoked. Julia performance benchmarks are carried out keeping compiled languages like C/C++ in mind. In many of them, Julia almost matches closely to performance levels2 of C/C++. Due to these performance gains, developers can write high-performance libraries in native Julia. This is unlike languages like Python or R that serve as excellent front-end interfaces leaving the backend performing code to native compiled languages like C/C++.

Julia is developed as a collection of open-source projects. We will insist on the usage of the term collection of open-source projects as most of the packages used are distributed as open source but may have different licensing than the Julia language. The Julia language is developed under the MIT License14, which provides significant flexibility in terms of using and extending the sources. The same also makes it easy for anyone to include complete Julia or its derivatives as a part of the other applications they are developing. Most packages developed in Julia also follow similar licensing schemes. Make sure you review the licensing flexibilities for the packages15 before you use them in your commercially licensed products.

Good platforms provide great interfaces and APIs to build flexible and large systems. Better ones embrace industry best practices than reinventing them. Julia is a perfect example of the second kind. It has native integration with LLVM (high-level compiler tools), OpenBLAS (linear algebra), LAPACK (linear algebra), Intel MKL, OpenLibm, Nvidia CUDA, PCRE (regular expressions), and so on. This ensures that the platform is built on proven technologies. Moreover, Julia provides foreign interface binding to languages like C, C++, Python, Java, and FORTRAN. If you are used to the flexibility or power of any such libraries, you can continue to use them in Julia. For example, the Julia plotting interface can easily be federated with Python matplotlib or GR. Packages are continuously being built and maintained for TensorFlow4 for machine learning; Cairo5 for low-level graphics or Qt6 for windowing or Electron JS^(\[7,8\]) for HTML-based client applications, and many more. All these are de-facto industry standard frameworks. Moreover, Julia wrapper packages are being built for commonly used native binary libraries9 like Zlib, OpenSSL and Qt, and so on. And, they are provided as binary distributions.

Good platforms provide great interfaces and APIs to build flexible and large systems. Better ones embrace industry best practices than reinventing them. Julia is a perfect example of the second kind. It has native integration with LLVM (high-level compiler tools), OpenBLAS (linear algebra), LAPACK (linear algebra), Intel MKL, OpenLibm, Nvidia CUDA, PCRE (regular expressions), and so on. This ensures that the platform is built on proven technologies. Moreover, Julia provides foreign interface binding to languages like C, C++, Python, Java, and FORTRAN. If you are used to the flexibility or power of any such libraries, you can continue to use them in Julia. For example, the Julia plotting interface can easily be federated with Python matplotlib or GR. Packages are continuously being built and maintained for TensorFlow4 for machine learning; Cairo5 for low-level graphics or Qt6 for windowing or Electron JS^(\[7,8\]) for HTML-based client applications, and many more. All these are de-facto industry standard frameworks. Moreover, Julia wrapper packages are being built for commonly used native binary libraries9 like Zlib, OpenSSL and Qt, and so on. And, they are provided as binary distributions.

Julia is developed as a collection of open-source projects. We will insist on the usage of the term collection of open-source projects as most of the packages used are distributed as open source but may have different licensing than the Julia language. The Julia language is developed under the MIT License14, which provides significant flexibility in terms of using and extending the sources. The same also makes it easy for anyone to include complete Julia or its derivatives as a part of the other applications they are developing. Most packages developed in Julia also follow similar licensing schemes. Make sure you review the licensing flexibilities for the packages15 before you use them in your commercially licensed products.

^(\[7,8\]) 

Just like the licensing, Julia architecturally is designed for federated enterprise environments. One can use their own private repository for applications and packages, deployment on enterprise-centric internal cloud infrastructures, and packages to integrate with enterprise federated authentication and authorization schemes. The Julia language also maintains all major versions like 1.0 as **long-term support** (**LTS**) to cater to enterprise support requirements16. Most importantly, Julia is supported by a *Julia Computing Inc*.17, an enterprise that provides tools, supports Julia, and is actively involved in the community activities of Julia programming. Enterprises interested in tools from Julia computing will be able to obtain various support plans from them. All founding members of the Julia language are currently employed in Julia Computing.

^(\[7,8\]) 

Just like the licensing, Julia architecturally is designed for federated enterprise environments. One can use their own private repository for applications and packages, deployment on enterprise-centric internal cloud infrastructures, and packages to integrate with enterprise federated authentication and authorization schemes. The Julia language also maintains all major versions like 1.0 as **long-term support** (**LTS**) to cater to enterprise support requirements16. Most importantly, Julia is supported by a *Julia Computing Inc*.17, an enterprise that provides tools, supports Julia, and is actively involved in the community activities of Julia programming. Enterprises interested in tools from Julia computing will be able to obtain various support plans from them. All founding members of the Julia language are currently employed in Julia Computing.

Good platforms provide great interfaces and APIs to build flexible and large systems. Better ones embrace industry best practices than reinventing them. Julia is a perfect example of the second kind. It has native integration with LLVM (high-level compiler tools), OpenBLAS (linear algebra), LAPACK (linear algebra), Intel MKL, OpenLibm, Nvidia CUDA, PCRE (regular expressions), and so on. This ensures that the platform is built on proven technologies. Moreover, Julia provides foreign interface binding to languages like C, C++, Python, Java, and FORTRAN. If you are used to the flexibility or power of any such libraries, you can continue to use them in Julia. For example, the Julia plotting interface can easily be federated with Python matplotlib or GR. Packages are continuously being built and maintained for TensorFlow4 for machine learning; Cairo5 for low-level graphics or Qt6 for windowing or Electron JS^(\[7,8\]) for HTML-based client applications, and many more. All these are de-facto industry standard frameworks. Moreover, Julia wrapper packages are being built for commonly used native binary libraries9 like Zlib, OpenSSL and Qt, and so on. And, they are provided as binary distributions.

Good platforms provide great interfaces and APIs to build flexible and large systems. Better ones embrace industry best practices than reinventing them. Julia is a perfect example of the second kind. It has native integration with LLVM (high-level compiler tools), OpenBLAS (linear algebra), LAPACK (linear algebra), Intel MKL, OpenLibm, Nvidia CUDA, PCRE (regular expressions), and so on. This ensures that the platform is built on proven technologies. Moreover, Julia provides foreign interface binding to languages like C, C++, Python, Java, and FORTRAN. If you are used to the flexibility or power of any such libraries, you can continue to use them in Julia. For example, the Julia plotting interface can easily be federated with Python matplotlib or GR. Packages are continuously being built and maintained for TensorFlow4 for machine learning; Cairo5 for low-level graphics or Qt6 for windowing or Electron JS^(\[7,8\]) for HTML-based client applications, and many more. All these are de-facto industry standard frameworks. Moreover, Julia wrapper packages are being built for commonly used native binary libraries9 like Zlib, OpenSSL and Qt, and so on. And, they are provided as binary distributions.

Any open-source software is good as long as there is continued interest in the community. Started with just three researchers and their advisor, the team expanded getting into many academic institutes and researchers showing active interest in it. The language’s main repository has about a thousand contributors, 30,000+ stars18 and 4200+ forks19. Beyond the main language repository, many developers contribute to the 4500+ packages available in the Julia packages ecosystem. The repositories are maintained in GitHub. While most communication is carried out as part of pull requests and issues tracking GitHub, specific project groups interact with Discourse, Slack, and GitHub projects as well. The Julia community conducts JuliaCon20, a conference dedicated to the development and evangelizing of the Julia ecosystem. There are many meetup groups where communities interact and exchange ideas. Free and paid courses are available to understand the ecosystem21 better.

Any open-source software is good as long as there is continued interest in the community. Started with just three researchers and their advisor, the team expanded getting into many academic institutes and researchers showing active interest in it. The language’s main repository has about a thousand contributors, 30,000+ stars18 and 4200+ forks19. Beyond the main language repository, many developers contribute to the 4500+ packages available in the Julia packages ecosystem. The repositories are maintained in GitHub. While most communication is carried out as part of pull requests and issues tracking GitHub, specific project groups interact with Discourse, Slack, and GitHub projects as well. The Julia community conducts JuliaCon20, a conference dedicated to the development and evangelizing of the Julia ecosystem. There are many meetup groups where communities interact and exchange ideas. Free and paid courses are available to understand the ecosystem21 better.

# 

# 

# 

Types are central to the Julia language. Although they need not be explicitly defined, Julia language tries to infer the types. There are types predefined in the system. Users can define their own types as well. Some types can be modified with parameters. This chapter shall familiarize you with some of these concepts.

# 

In this chapter, we will cover the following topics:

*   Types in Julia
*   Built-in types
*   User-defined types
*   Any
*   Parametric data types
*   Operations on types
*   Printing data types

# 

The user shall be able to understand the type system of Julia, understand the system defined, and user-defined types. Thus, they shall be able to understand their importance and usage in Julia programming.

# 

Dynamic typed programming languages are not known to have well-developed type systems. In Python data types are optional. People use various packages like Numpy to define numerical data types. Julia type system is dynamic and almost always inferred at the time of instantiation of a variable. The data types are known before the execution of a code segment or **just-in-time** (**JIT**) compilation of the Julia code. In short, Julia natively supports data types that can be defined or inferred for any variable or literal before they are used. Before we delve deeper into data types, let us understand a bit about variables, constants, and literals.

# 

Variables in Julia are associated names with values. Names are typically alphanumeric representations starting with an alphabet. Rather than getting to a syntactically accurate definition of what can constitute names, we will list out a few valid variables in Julia.

`<strong>julia&gt; a = 1</strong>`

`<strong>1</strong>`

`<strong>julia&gt; abc = 1</strong>`

`<strong>1</strong>`

`<strong>julia&gt; 1abc = 2</strong>`

`<strong>ERROR: syntax: "1" is not a valid function argument name around</strong>`

`<strong>REPL[3]:1</strong>`

`<strong>Stacktrace:</strong>`

`<strong>[1] top-level scope at REPL[3]:1</strong>`

`<strong>julia&gt; πi = 30</strong>`

`<strong>30</strong>`

`<strong>julia&gt; aπi = 30</strong>`

`<strong>30</strong>`

As can be seen, a variable name cannot begin as a number. A variable can contain a Unicode character. There are limitations to the name of a variable and the author will like to suggest reviewing the Julia documentation[1](#qpxadky7.html#n4upl4fndmd) for a detailed understanding of variable nomenclature. Keywords in Julia cannot be used as variables. Julia has very few keywords. Some of them are: `<strong>baremodule</strong>`, `<strong>begin</strong>`, `<strong>break</strong>`, `<strong>catch</strong>`, `<strong>const</strong>`, `<strong>continue</strong>`, `<strong>do</strong>`, `<strong>else</strong>`, `<strong>elseif</strong>`, `<strong>end</strong>`, `<strong>export</strong>`, `<strong>false</strong>`, `<strong>finally</strong>`, `<strong>for</strong>`, `<strong>function</strong>`, `<strong>global</strong>`, `<strong>if</strong>`, `<strong>import</strong>`, `<strong>let</strong>`, `<strong>local</strong>`, `<strong>macro</strong>`, `<strong>module</strong>`, `<strong>quote</strong>`, `<strong>return</strong>`, `<strong>struct</strong>`, `<strong>true</strong>`, `<strong>try</strong>`, `<strong>using</strong>`, `<strong>while</strong>`. Julia also has multiword keywords (mutable struct, abstract type, and so on) and infix operator (in, isa, and so on) keywords. The author will suggest a detailed review of the keywords in the language documentation for an elaborate understanding.

# 

Some languages like C/C++ have separate declarative definitions from initializations. Here is a simple example in C/C++ highlighting the same.

`<strong>…</strong>`

`<strong>int i;&nbsp;&nbsp; /* Definition of i as an integer type */</strong>`

`<strong>i = 10;&nbsp;&nbsp;/* Initialization of i now */</strong>`

`<strong>int j = 20; /* Definition and initialization in the same statement */</strong>`

`<strong>…</strong>`

Julia does not differentiate the two. Most Julia variables get defined on initialization to the type of interest. In fact, the type is assigned to the variable as a part of the initialization process. However, explicit assignment to a specific type is also possible though not advised. The variable assignment to a specific type is not permitted for global variables in a REPL set up. However, the same can be carried out for variables defined inside a function.

`<strong>julia&gt; i::Int=1</strong>`

`<strong>ERROR: syntax: type declarations on global variables are not yet supported</strong>`

`<strong>Stacktrace:</strong>`

`<strong>[1] top-level scope at REPL[8]:1</strong>`

`<strong>julia&gt; function f()</strong>`

`<strong>i::Int=5</strong>`

`<strong>return i</strong>`

`<strong>end</strong>`

`<strong>f (generic function with 1 method)</strong>`

`<strong>julia&gt; f()</strong>`

`<strong>5</strong>`

The behavior is apparent as all variables are assumed to be initialized before use. An uninitialized variable will error on use as shown as follows:

`<strong>julia&gt; i</strong>`

`<strong>ERROR: UndefVarError: i not defined</strong>`

`<strong>julia&gt; function f()</strong>`

`<strong>i</strong>`

`<strong>return i</strong>`

`<strong>end</strong>`

`<strong>f (generic function with 1 method)</strong>`

`<strong>julia&gt; f()</strong>`

`<strong>ERROR: UndefVarError: i not defined</strong>`

`<strong>Stacktrace:</strong>`

`<strong>[1] f() at .\REPL[12]:2</strong>`

`<strong>[2] top-level scope at REPL[13]:1</strong>`

# 

Constants can be considered as variables that cannot be modified. However, Julia does not follow a rigid condition for mutability of constant variables. It rather warns of a potential override of a constant expression.

`<strong>julia&gt; const ICONSTANT=1</strong>`

`<strong>1</strong>`

`<strong>julia&gt; ICONSTANT=5</strong>`

`<strong>WARNING: redefinition of constant ICONSTANT. This may fail, cause incorrect answers, or produce other errors.</strong>`

`<strong>5</strong>`

`<strong>julia&gt; ICONSTANT</strong>`

`<strong>5</strong>`

While in the preceding example, the constant is overridden these kinds of usage must be avoided and can lead to potential errors in execution.

# 

Literals are constant expressions that represent a value. Sometimes they are also referred to as r-values as they appear in the right-hand side of a variable definition. They also are representation of a value in their atomic representational forms. Here are some literal expressions of various types.

`<strong>julia&gt; 2&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;# Integer</strong>`

`<strong>2</strong>`

`<strong>julia&gt; 2.0&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;# Double precision Float (Float64)</strong>`

`<strong>2.0</strong>`

`<strong>julia&gt; 2f0&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;# Single precision Float (Float32)</strong>`

`<strong>2.0f0</strong>`

`<strong>julia&gt; "string"&nbsp;&nbsp; # String</strong>`

`<strong>"string" julia&gt; 'a'&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;# Char</strong>`

`<strong>'a': ASCII/Unicode U+0061 (category Ll: Letter, lowercase)</strong>`

As we delve further into types, we will review the literals in further details in the context of specific types. In general, variables are initialized as `<strong>var = &lt;literals&gt;</strong>`.

# 

Transferring values from one variable to another and vice versa is considered one of the first programming samples. Here is a typical code for the same in say C/C++.

`<strong>int i=1, j=2, t;</strong>`

`<strong>t = i;</strong>`

`<strong>i = j;</strong>`

`<strong>j = t;</strong>`

`<strong>/* Now i = 2 and j = 1 */</strong>`

The same code in Julia may look like this:

`<strong>julia&gt; i=1; j = 2;</strong>`

`<strong>julia&gt; i, j = j, i</strong>`

`<strong>(2, 1)</strong>`

`<strong>julia&gt; i</strong>`

`<strong>2</strong>`

`<strong>julia&gt; j</strong>`

`<strong>1</strong>`

Tuples are special purpose immutable collections that are created when you specify comma separated values in Julia. They also can be denoted by enclosing several commas separated values within braces.

`<strong>julia&gt; 1, 2</strong>`

`<strong>(1, 2)</strong>`

`<strong>julia&gt; a = (2, 3)</strong>`

`<strong>(2, 3)</strong>`

`<strong>julia&gt; typeof(a)</strong>`

`<strong>Tuple{Int64,Int64}</strong>`

`<strong>julia&gt; a[1]</strong>`

`<strong>2</strong>`

`<strong>julia&gt; a[1] = 5</strong>`

`<strong>ERROR: MethodError: no method matching setindex!(::Tuple{Int64,Int64}, ::Int64, ::Int64)…</strong>`

As can be seen, the elements of Tuple can be accessed by indexing. But, elements of a Tuple cannot be modified. Following are some examples of multiple assignments to variables from a Tuple based on the position of variables.

`<strong>julia&gt; i, j = 1, 2</strong>`

`<strong>(1, 2)</strong>`

`<strong>julia&gt; i</strong>`

`<strong>1</strong>`

`<strong>julia&gt; j</strong>`

`<strong>2</strong>`

`<strong>julia&gt; i = 1, 2 #i is a Tuple</strong>`

`<strong>(1, 2)</strong>`

`<strong>julia&gt; i</strong>`

`<strong>(1, 2)</strong>`

`<strong>julia&gt; i, = 1, 2 #i is an Int</strong>`

`<strong>(1, 2)</strong>`

`<strong>julia&gt; i</strong>`

`<strong>1</strong>`

`<strong>julia&gt; i, j = 1, 2, 3 #i and j get assigned 3 is ignored</strong>`

`<strong>(1, 2, 3)</strong>`

`<strong>julia&gt; i</strong>`

`<strong>1</strong>`

`<strong>julia&gt; j</strong>`

`<strong>2</strong>`

# 

Julia has many built-in types defined in the language. Many of the types are defined in Julia libraries. And the language provides flexibility to extend these as well. Moreover, the types defined are not reserved keywords. Following are a few commonly used types in the language.

# 

`<strong>Nothing</strong>` is a type for the value nothing. In many other languages like C/C++ the use of similar values like void is pretty much used for similar purposes. However, in Julia nothing is not a keyword.

`<strong>julia&gt; typeof(nothing)</strong>`

`<strong>Nothing</strong>`

We also introduced a method `<strong>typeof</strong>` that provides the information on the type to which a value belongs to. The usage of nothing is fairly common where there is a conditional possibility of an uninitialized variable in the code.

`<strong>julia&gt; a = nothing</strong>`

`<strong>julia&gt; i = 5</strong>`

`<strong>5</strong>`

`<strong>julia&gt; if i &lt; 5</strong>`

`<strong>a = 5</strong>`

`<strong>end</strong>`

`<strong>julia&gt; typeof(a)</strong>`

`<strong>Nothing</strong>`

Here, if `<strong>i</strong>` becomes less than 5 then a gets assigned to a value of 5. Otherwise, it remains as a nothing. Nothing and nothing also are used extensively in function arguments and return types.

# 

Following are some of the data types that are defined in Julia as numerical data types.

# 

`<strong>true</strong>` and `<strong>false</strong>` are of type Bool in Julia. Numerically, `<strong>true</strong>` has a value of 1 and `<strong>false</strong>` has a value of 0.

# 

Integral numeric types are categorized as unsigned and signed numbers with various byte sizes. The signed number types are: `<strong>Int8</strong>`, `<strong>Int16</strong>`, `<strong>Int32</strong>`, `<strong>Int64</strong>`, and `<strong>Int128</strong>`. The equivalent unsigned numbers are: `<strong>UInt8</strong>`, `<strong>UInt16</strong>`, `<strong>UInt32</strong>`, `<strong>UInt64</strong>`, and `<strong>UInt128</strong>`, respectively.

`<strong>julia&gt; typeof(1)</strong>`

`<strong>Int64</strong>`

The default numerical type for a number literal is `<strong>Int</strong>`, which maps to an `<strong>Int32</strong>` or an `<strong>Int64</strong>` depending on the architecture of the machine.

However, for the unsigned numbers literals are specified by `0&lt;representation specifier&gt;&lt;number&gt;.`

`<strong>julia&gt; typeof(0b1), typeof(0o7), typeof(0xff) (UInt8, UInt8, UInt8)</strong>`

The numbers are all mapped to `<strong>UInt8</strong>` while they are in the binary, octal, and hexadecimal representations. The size of the number is determined from the minimal size of bytes needed to fit the literal.

`<strong>julia&gt; typeof(0xf), typeof(0xfff), typeof(0xfffff), typeof(0xfffffffff), typeof(0xfffffffffffffffff)</strong>`

`<strong>(UInt8, UInt16, UInt32, UInt64, UInt128)</strong>`

As with most other languages, +/- can be used in Julia as sign qualifiers.

# 

Julia has `<strong>Float16</strong>`, `<strong>Float32</strong>` and `<strong>Float64</strong>` to represent half, single and double precision floating point numbers as per the IEEE 754 standards specifications. The literals can use **f** or **e** as an exponent separator for `<strong>Float32</strong>` and `<strong>Float64</strong>`, respectively.

`<strong>julia&gt; typeof(1.0), typeof(1e0), typeof(1.e4) (Float64, Float64, Float64)</strong>`

`<strong>julia&gt; typeof(1.0f0), typeof(1f-6), typeof(1.f4) (Float32, Float32, Float32)</strong>`

# 

Types in Julia can be derived from an abstract type. Most object-oriented languages would consider this kind of relationship as a means to describe objects in a class hierarchy. The abstract types are merely conceptual representations like interfaces and have no data elements in them.

`<strong>julia&gt; abstract type MyAbstractType end</strong>`

`<strong>julia&gt; struct MyConcreteType &lt;: MyAbstractType</strong>`

`<strong>member</strong>`

`<strong>end</strong>`

`<strong>julia&gt; a = MyConcreteType(5)</strong>`

`<strong>MyConcreteType(5)</strong>`

`<strong>julia&gt; a isa MyAbstractType</strong>`

`<strong>true</strong>`

While we will delve into this concept in detail later, a type can be derived only from one abstract type. Infix operator `<strong>isa</strong>` is used to say if a particular object is of a specific type. Here type can be a concrete type or an abstract type. Following is the type hierarchy of the numeric types in Julia:

![](n4upl4fndrd.jpeg)

**Figure 2.1:** Hierarchy of numeric types

# 

Primitive types are data types that LLVM[2](#qpxadky7.html#n4upl4fndme) supports. Julia compiles the code to LLVM equivalent and subsequently to a native CPU machine code for execution in a **JIT** fashion. Hence, it is quite logical to bring in the LLVM types into Julia. These primitive types are bit values. Here are a set of primitive types defined in Julia[3](#qpxadky7.html#n4upl4fndmf).

`<strong>primitive type &lt;&lt;name&gt;&gt; &lt;: &lt;&lt;supertype&gt;&gt; &lt;&lt;bits&gt;&gt; end</strong>`

`<strong>primitive type Float16 &lt;: AbstractFloat 16 end</strong>`

`<strong>primitive type Float32 &lt;: AbstractFloat 32 end</strong>`

`<strong>primitive type Float64 &lt;: AbstractFloat 64 end</strong>`

`<strong>primitive type Bool &lt;: Integer 8 end</strong>`

`<strong>primitive type Char &lt;: AbstractChar 32 end</strong>`

`<strong>primitive type Int8&nbsp;&nbsp;&nbsp;&nbsp;&lt;: Signed&nbsp;&nbsp; 8 end</strong>`

`<strong>primitive type UInt8&nbsp;&nbsp; &lt;: Unsigned 8 end</strong>`

`<strong>primitive type Int16&nbsp;&nbsp; &lt;: Signed&nbsp;&nbsp; 16 end</strong>`

`<strong>primitive type UInt16&nbsp;&nbsp;&lt;: Unsigned 16 end</strong>`

`<strong>primitive type Int32&nbsp;&nbsp; &lt;: Signed&nbsp;&nbsp; 32 end</strong>`

`<strong>primitive type UInt32&nbsp;&nbsp;&lt;: Unsigned 32 end</strong>`

`<strong>primitive type Int64&nbsp;&nbsp; &lt;: Signed&nbsp;&nbsp; 64 end</strong>`

`<strong>primitive type UInt64&nbsp;&nbsp;&lt;: Unsigned 64 end</strong>`

`<strong>primitive type Int128&nbsp;&nbsp;&lt;: Signed&nbsp;&nbsp; 128 end</strong>`

`<strong>primitive type UInt128 &lt;: Unsigned 128 end</strong>`

While users can define their own primitive types, it is advisable to use the already defined primitive types and define newer ones when the existing ones cannot serve the purpose. Second, primitive types of the same bit values are not essentially interchangeable or can be converted seamlessly. The type hierarchy plays an important role in the behavior of such types.

`<strong>julia&gt; UInt32(3f-1)</strong>`

`<strong>ERROR: InexactError: UInt32(0.3)</strong>`

Even though they are both 32-bit entities, a single-precision float cannot be represented as an unsigned integer in every situation. Third, you cannot create primitive types of arbitrary bit sizes. Only bit sizes that are multiples of 8-bits are supported.

`<strong>julia&gt; primitive type MyType1 40 end</strong>`

`<strong>julia&gt; primitive type MyType2 4 end</strong>`

`<strong>ERROR: invalid number of bits in primitive type MyType2 …</strong>`

# 

Julia interoperates seamlessly with languages that operate on a binary interface like C/C++, FORTRAN, and other natively compiled languages. In such a condition, it is imperative to expect certain data types defined in Julia are consistent in binary layout to be used by these natively compiled languages. Such types are known as **Bit Types**. The primitive types are all of bit typed data types. Certain composite data types are bit types. We will discuss about them further when we encounter them. The bit types can be queried with the function `<strong>isbits</strong>` on an instance and `<strong>isbitstype</strong>` on a type.

`<strong>julia&gt; a = 10</strong>`

`<strong>10</strong>`

`<strong>julia&gt; isbits(a)</strong>`

`<strong>true</strong>`

`<strong>julia&gt; isbitstype(Int)</strong>`

`<strong>true</strong>`

# 

Rational[4](#qpxadky7.html#n4upl4fndmg) and Complex data types though numeric types are not primitive types. They are created using composite data types that we will review as part of user-defined types.

# 

Char is a character represented as a 32-bit value. It can be a valid UCS-4 representation of a Unicode character. We will discuss in details Char and its relationship with String in the chapter on Strings. `<strong>AbstractChar</strong>` abstract type is provided such that one can develop her own char-like data types.

# 

Strings are collection of characters. While most of the strings are composed of Unicode character codes, they can store other kinds of binary data as well. `<strong>AbstractString</strong>` abstract type is provided so that advanced users can define custom string types. We will discuss these in detail in a later chapter.

# 

While Julia provides quite a few built-in types, there is always a need to have data types that are composite and may require various attributes be grouped together.

# 

These types cannot have their attributes modified once they are defined. These immutable data types are represented as `<strong>struct</strong>` in Julia.

`<strong>julia&gt; struct Rectangle</strong>`

`<strong>h::Float64</strong>`

`<strong>w::Float64</strong>`

`<strong>end</strong>`

`<strong>julia&gt; r = Rectangle(10.0, 20.0)</strong>`

`<strong>Rectangle(10.0, 20.0)</strong>`

`<strong>julia&gt; r.h = 15</strong>`

`<strong>ERROR: setfield! immutable struct of type Rectangle cannot be changed …</strong>`

As can be seen, `<strong>Rectangle</strong>` is a `<strong>struct</strong>` defined and which is initialized with values `<strong>10.0</strong>` and `<strong>20.0</strong>`. The values of attributes cannot be modified. The initialization is carried out with `<strong>Rectangle (10.0, 20.0)</strong>`. This is a special purpose function. We shall know more about when we discuss functions and methods.

# 

Suppose we were to make the `<strong>Rectangle</strong>` mutable we could have created a mutable struct as shown as follows:

`<strong>julia&gt; mutable struct MRectangle</strong>`

`<strong>h::Float64</strong>`

`<strong>w::Float64</strong>`

`<strong>end</strong>`

`<strong>julia&gt; mr = MRectangle(10.0, 20.0)</strong>`

`<strong>MRectangle(10.0, 20.0)</strong>`

`<strong>julia&gt; mr.h = 15.0</strong>`

`<strong>15.0</strong>`

`<strong>julia&gt; mr</strong>`

`<strong>MRectangle(15.0, 20.0)</strong>`

As can be seen, the attribute values are modified after instantiating the object. Composite data types in Julia can also be derived from an `<strong>abstract type</strong>`.

`<strong>julia&gt; abstract type Shape end</strong>`

`<strong>julia&gt; struct Rectangle &lt;: Shape</strong>`

`<strong>w::Float64</strong>`

`<strong>h::Float64</strong>`

`<strong>end</strong>`

`<strong>julia&gt; struct Square &lt;: Shape</strong>`

`<strong>l::Float64</strong>`

`<strong>end</strong>`

# 

The composite types in Julia have member attributes and no member functions or methods. The Julia multi-dispatch architecture is used to make functions behave like methods[5](#qpxadky7.html#n4upl4fndmh) for specific types, but they are not the same as methods in an object-oriented language. There is a special category of functions that can be a member of a type. Those are called **constructors**. We will review constructors in details as we discuss about functions. The type information of members is not always to be specified in a composite type.

`<strong>julia&gt; mutable struct A<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; member<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; end<br>julia&gt; a = A(5)<br>A(5)<br>julia&gt; typeof(a.member)<br>Int64</strong>`

`<strong>julia&gt; a1 = A("String")<br>A("String")<br>julia&gt; typeof(a1.member)<br>String</strong>`

# 

While in the preceding example, the ambiguity is resolved when an object is instantiated, one can never be sure of the type as dynamically member attribute can be assigned to another type.

`<strong>julia&gt; a.member = "String"<br>"String"<br>julia&gt; typeof(a.member)<br>String</strong>`

`<strong>a.member</strong>` which was of type `<strong>Int64</strong>`, now is of `<strong>String</strong>` type. Julia presumes such unspecified types as `<strong>Any</strong>`. Scenarios where it is not possible to be deterministic about type, Julia would presume the type as `<strong>Any</strong>`. Use of `<strong>Any</strong>` is not desirable from a performance perspective. Every time an object of type `<strong>Any</strong>` is accessed, it is another redirection to access the actual object. Size of the object Any will not be available ahead in time. It will be a pointer pointing to another location in the memory where the actual object resides:

![](n4upl4fndre.jpeg)

**Figure 2.2:** (a) Member defined as Any (b) member defined as a Float32

# 

`<strong>Any</strong>` as a type introduces unnecessary indirections, and hence can be inefficient. Sometimes the types do not necessarily affect the algorithm but introduce a different bit size of the data. For example, the `<strong>Rational</strong>` data type introduced earlier in the context of numeric data types the numerator and denominator can be any of the Integral data types like `<strong>Int8</strong>`, `<strong>Int16</strong>`, `<strong>Int32</strong>`, `<strong>Int64,</strong>` or `<strong>Int128</strong>`. The definition of the `<strong>Rational</strong>` data type is given as follows[6](#qpxadky7.html#n4upl4fndmi):

`<strong>:</strong>`

`<strong>struct Rational{T&lt;:Integer} &lt;: Real<br>&nbsp;&nbsp;&nbsp;&nbsp;num::T<br>&nbsp;&nbsp;&nbsp;&nbsp;den::T<br>end</strong>`

The two attributes of the type `<strong>num</strong>` and `<strong>den</strong>` are of the type `<strong>T</strong>` where `<strong>T</strong>` is a subtype of Integer. `<strong>Rational</strong>` is a subtype of Real. Here are some observations on the parametric data types.

`<strong>julia&gt; Rational{Any}<br>ERROR: TypeError: in Rational, in T, expected T&lt;:Integer, got Type{Any}<br>…</strong>`

`<strong>Any is not a subtype of Integer. Hence it is not possible to instantiate Rational{Any}.</strong>`

`<strong>julia&gt; Rational{Int32} &lt;: Rational<br>true<br>julia&gt; Rational{Int32} &lt;: Rational{Integer}<br>false</strong>`

This behavior is particularly important to understand. Although `<strong>Int32</strong>` is a subtype of Integer, the parametric representation `<strong>Rational{Int32}</strong>` is not a subtype of `<strong>Rational{Integer}</strong>`. However `<strong>Rational{Int32}</strong>` is a subtype of Rational.

Just like concrete data types, abstract data types can be parameterized as well.

`<strong>julia&gt; abstract type Shape{T&lt;:AbstractFloat} end<br>julia&gt; struct Rectangle{T&lt;:AbstractFloat} &lt;: Shape{T}<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; w::T<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; h::T<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; end<br>julia&gt; struct Square{T&lt;:AbstractFloat} &lt;: Shape{T}<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; s::T<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; end</strong>`

One can use the preceding scheme to develop two sets of functionalities say for `<strong>Float32</strong>` or `<strong>Float64</strong>`. The type generated for `<strong>Rectangle{Float32}</strong>` is a different from `<strong>Rectangle{Float64}</strong>` and they get generated during compilation while instantiating the concrete type.

While parameterization of types is a very useful feature of the Julia language, parameterization can be carried out for integral values as well.

`<strong>julia&gt; struct Point{T&lt;:AbstractFloat, N}<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; x::Vector{T}<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; end</strong>`

`<strong>julia&gt; p = Point{Float32, 2}([1f0, 2f0])<br>Point{Float32,2}(Float32[1.0, 2.0])</strong>`

As can be seen, `<strong>N</strong>` used in the type is an integer used as a type parameter.

# 

There are certain operations that are applicable to a type. We have seen some of them so far but we will be elaborating on them in this section.

# 

This function provides the concrete type associated with an instance of a type.

`<strong>julia&gt; a = 1//2<a id="ftn7a" href="#ftn7"><sup>7</sup></a><br><br>1//2<br>julia&gt; typeof(a)<br>Rational{Int64}</strong>`

`<strong>Aliases</strong>`

Types themselves are of instances of `<strong>DataType</strong>` type.

`<strong>julia&gt; typeof(Int)<br>DataType<br>julia&gt; typeof(Rational{Int})<br>DataType</strong>`

Like any other instance object they can be compared and assigned. Here is a code snippet from base/boot.jl.[8](#qpxadky7.html#n4upl4fndmj)

`<strong>if Int ===<a id="ftn9a" href="#ftn9"><sup>9</sup></a> Int64<br>&nbsp;&nbsp;&nbsp;&nbsp;const UInt = UInt64<br>else<br>&nbsp;&nbsp;&nbsp;&nbsp;const UInt = UInt32<br>end</strong>`

`<strong>Int</strong>` object is compared with `<strong>Int64</strong>` and if they are the same then `<strong>UInt</strong>` is initialized as `<strong>UInt64</strong>` otherwise it is initialized as `<strong>UInt32</strong>`. Thus `<strong>UInt</strong>` acts as an alias for `<strong>UInt64</strong>` or `<strong>UInt32</strong>` based on the machine architecture.

# 

Provides information if an instance is of a specific type. `<strong>isa</strong>` can also be used as an infix operator.

`<strong>ulia&gt; isa(1, Number)<br>true<br>julia&gt; isa(1, Matrix)<br>false<br>julia&gt; isa(1, Int)<br>true<br>julia&gt; 1 isa Number<br>true</strong>`

# 

This function returns the immediate super type of a type.

`<strong>julia&gt; supertype(Int32)<br>Signed</strong>`

`<strong>&lt;:</strong>`

This operator is used to denote if a type is a subtype of another type.

`<strong>julia&gt; Int32 &lt;: Integer<br>true<br>julia&gt; Int32 &lt;: AbstractFloat<br>false<br>julia&gt; Int32 &lt;: Real<br>true<br>julia&gt; Int32 &lt;: Signed<br>true</strong>`

# 

When complex data types are defined, the data needs to be presented in a meaningful fashion. By default, all the members will be printed as a tuple.

`<strong>julia&gt; struct A<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; a1::Int32<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; a2::Float64<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; end<br>julia&gt; a = A(1, 2)<br>A(1, 2.0)</strong>`

Second, the data is always printed on the REPL. To suppress printing of data on a REPL one can end the statement with a semicolon (;).

`<strong>julia&gt; a;<br>julia&gt; a<br>A(1, 2.0)</strong>`

But, why is this behavior? Let’s look at some more examples.

`<strong>julia&gt; b = 2.0<br>2.0<br>julia&gt; a; b<br>2.0</strong>`

With a semicolon separating the line the output of the last expression is only printed which is b in this case.

`<strong>julia&gt; nothing</strong>`

`<strong>Nothing</strong>` does not mark the output by default. When a semicolon is used as the end of a statement the behavior is similar to adding a `<strong>nothing</strong>` at the end of semicolon. Hence no output gets printed.

`<strong>julia&gt; a<br>A(1, 2.0)<br>julia&gt; a;<br>julia&gt; a; nothing</strong>`

# 

By default to show an output on a REPL the associated show method is called on the data type.

`<strong>julia&gt; struct A<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; a1::Int32<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; a2::Float64<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; end<br>julia&gt; a = A(1, 2)<br>A(1, 2.0)<br>julia&gt; function Base.show(io::IO, a::A)<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; println(io, "a1: ", a.a1, " a2: ", a.a2)<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; end<br>julia&gt; a<br>a1: 1 a2: 2.0</strong>`

# 

While `<strong>show</strong>` is used to display the data on any kind of output device, print can be used to output the textual representation only. When no specific `<strong>print</strong>` routine is introduced show is used internally when `<strong>print</strong>` is called.

`<strong>julia&gt; print(a)<br>a1: 1 a2: 2.0</strong>`

# 

This function can be used to convert any type to its string representation. When no proper conversion method is provided, the print function is internally invoked to get a textual representation of the data type.

`<strong>julia&gt; string(a)<br>"a1: 1 a2: 2.0\n"</strong>`

The usage of `<strong>print</strong>` or underlying `<strong>show</strong>` can be clearly seen in the preceding code. Moreover, the extra end of line in the `<strong>String</strong>` can be attributed to the use of `<strong>println</strong>` which adds an EOL to the statement.

# 

Although a dynamically typed language, types in Julia are fundamental to the language. They are inferred during the JIT compilation and to a large extent contribute to performance gains of the Julia language. While we got a brief outline of the data types in this chapter, a significant part of the data types get exposed as we learn about functions and methods in . The use of multiple dispatch interfaces through data types is a significant part of the language fundamentals that we will cover as well.

# 

1.  Is there any literals defined for half precisions floats (Float16)? How can one initialize them?
2.  Using the alias `Int` how can one determine if a machine is a 32-bit machine or a 64-bit machine?
3.  Can tuples have more than 2 elements?
4.  The default printing of a `struct` is the struct name followed by the members as tuples within braces. Is there any advantage to having such a representation? (You may need to understand the constructor to be able to appreciate it).
5.  Can a member of a composite type be `nothing`? Is there any advantage to such a case?

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

[1](#qpxadky7.html#n4upl4fndmk) Julia Documentation (Manual--> Variables) **[https://docs.julialang.org/en/v1/manual/variables/](https://docs.julialang.org/en/v1/manual/variables/)**

[2](#qpxadky7.html#n4upl4fndml) The LLVM Project is a collection of modular and reusable compiler and toolchain technologies. The tool provides an intermediate language that helps in writing compilers in a platform-neutral manner. **[https://llvm.org/](https://llvm.org/)**

[3](#qpxadky7.html#n4upl4fndmm) Primitive Types, Julia Documentation, **[https://docs.julialang.org/en/v1/manual/types/#Primitive-Types](https://docs.julialang.org/en/v1/manual/types/#Primitive-Types)**

[4](#qpxadky7.html#n4upl4fndmn) Rational numbers are a representation of fraction with an integer numerator and an integer denominator. They are real numbers. However, rational numbers are relatively less used in computations. The fractions are mostly represented as floating point numbers.

[5](#qpxadky7.html#n4upl4fndmo) Most object-based languages have member attributes and methods. The methods provide the flexibility of polymorphism. However, Julia types do not have any member methods. When a polymorphic behavior is simulated using a function with different function parameters, they are called as methods. For most practical usage, functions and methods are similar. Here is an example of a method f():  
*f(x) = 2x*  
*f(x, y) = x\*y*

[6](#qpxadky7.html#n4upl4fndmp) Code sample is taken from the Julia Language GitHub repository at base/rational.jl. Some of the advanced expressions are not included.

Rational division operator, written as <<numerator>>//<<denominator>>.

[8](#qpxadky7.html#n4upl4fndmq) Julia GitHub Repository

Bitwise equality, typically shall mean two objects are the same. This operator cannot be overridden. Types are objects as well.

Julia GitHub Repository

Rational numbers are a representation of fraction with an integer numerator and an integer denominator. They are real numbers. However, rational numbers are relatively less used in computations. The fractions are mostly represented as floating point numbers.

Primitive Types, Julia Documentation, **[https://docs.julialang.org/en/v1/manual/types/#Primitive-Types](https://docs.julialang.org/en/v1/manual/types/#Primitive-Types)**

Code sample is taken from the Julia Language GitHub repository at base/rational.jl. Some of the advanced expressions are not included.

Most object-based languages have member attributes and methods. The methods provide the flexibility of polymorphism. However, Julia types do not have any member methods. When a polymorphic behavior is simulated using a function with different function parameters, they are called as methods. For most practical usage, functions and methods are similar. Here is an example of a method f():  
*f(x) = 2x*  
*f(x, y) = x\*y*

The LLVM Project is a collection of modular and reusable compiler and toolchain technologies. The tool provides an intermediate language that helps in writing compilers in a platform-neutral manner. **[https://llvm.org/](https://llvm.org/)**

Julia Documentation (Manual--> Variables) **[https://docs.julialang.org/en/v1/manual/variables/](https://docs.julialang.org/en/v1/manual/variables/)**

As can be seen, a variable name cannot begin as a number. A variable can contain a Unicode character. There are limitations to the name of a variable and the author will like to suggest reviewing the Julia documentation1 for a detailed understanding of variable nomenclature. Keywords in Julia cannot be used as variables. Julia has very few keywords. Some of them are: `<strong>baremodule</strong>`, `<strong>begin</strong>`, `<strong>break</strong>`, `<strong>catch</strong>`, `<strong>const</strong>`, `<strong>continue</strong>`, `<strong>do</strong>`, `<strong>else</strong>`, `<strong>elseif</strong>`, `<strong>end</strong>`, `<strong>export</strong>`, `<strong>false</strong>`, `<strong>finally</strong>`, `<strong>for</strong>`, `<strong>function</strong>`, `<strong>global</strong>`, `<strong>if</strong>`, `<strong>import</strong>`, `<strong>let</strong>`, `<strong>local</strong>`, `<strong>macro</strong>`, `<strong>module</strong>`, `<strong>quote</strong>`, `<strong>return</strong>`, `<strong>struct</strong>`, `<strong>true</strong>`, `<strong>try</strong>`, `<strong>using</strong>`, `<strong>while</strong>`. Julia also has multiword keywords (mutable struct, abstract type, and so on) and infix operator (in, isa, and so on) keywords. The author will suggest a detailed review of the keywords in the language documentation for an elaborate understanding.

Primitive types are data types that LLVM2 supports. Julia compiles the code to LLVM equivalent and subsequently to a native CPU machine code for execution in a **JIT** fashion. Hence, it is quite logical to bring in the LLVM types into Julia. These primitive types are bit values. Here are a set of primitive types defined in Julia3.

Primitive types are data types that LLVM2 supports. Julia compiles the code to LLVM equivalent and subsequently to a native CPU machine code for execution in a **JIT** fashion. Hence, it is quite logical to bring in the LLVM types into Julia. These primitive types are bit values. Here are a set of primitive types defined in Julia3.

Like any other instance object they can be compared and assigned. Here is a code snippet from base/boot.jl.8

The composite types in Julia have member attributes and no member functions or methods. The Julia multi-dispatch architecture is used to make functions behave like methods5 for specific types, but they are not the same as methods in an object-oriented language. There is a special category of functions that can be a member of a type. Those are called **constructors**. We will review constructors in details as we discuss about functions. The type information of members is not always to be specified in a composite type.

Rational4 and Complex data types though numeric types are not primitive types. They are created using composite data types that we will review as part of user-defined types.

`<strong>Any</strong>` as a type introduces unnecessary indirections, and hence can be inefficient. Sometimes the types do not necessarily affect the algorithm but introduce a different bit size of the data. For example, the `<strong>Rational</strong>` data type introduced earlier in the context of numeric data types the numerator and denominator can be any of the Integral data types like `<strong>Int8</strong>`, `<strong>Int16</strong>`, `<strong>Int32</strong>`, `<strong>Int64,</strong>` or `<strong>Int128</strong>`. The definition of the `<strong>Rational</strong>` data type is given as follows6:

# 

# 

# 

Branching and control flows are at the heart of imperative style of programming. As much a functional programming language, Julia has support for all well-known imperative styles and constructs. This chapter shall expose you to most of them.

# 

In this chapter, we will cover the following topics:

*   Compound statements
*   Conditional execution
*   Iterative execution
*   Exception handling
*   Parallel execution

# 

In this chapter, the reader shall be able to understand compound statements. We will discuss branching and control flows like `<strong>if…else</strong>`, loops like `<strong>while</strong>` and `<strong>for</strong>` and exception handling. Control flows are core to programming logic and help build complex applications.

# 

# 

Any set of statements between a block of `<strong>begin</strong>` and `<strong>end</strong>` are considered a large compound execution unit.

`<strong>julia&gt; z = begin<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; x = 1<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; y = 2<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; x + y<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; end<br>3<br>julia&gt; z<br>3</strong>`

The value of the final expression in the block is considered as the value of the compound block. The same expression can be written as a single line using semicolons and braces.

`<strong>julia&gt; z = (x = 1; y = 2; x+y)<br>3</strong>`

The following are valid compound statements as well.

`<strong>julia&gt; z = (x = 1;<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; y = 2;<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; x + y)<br>3</strong>`

`<strong>julia&gt; z = begin x=1; y=2; x+y end<br>3</strong>`

# 

Conditional statements are the heart of any programming language. They provide avenues to define branching in the code and are foundations for iterative programming. Branching with local `<strong>goto</strong>` is good enough to emulate any iterative model in a programming language.

# 

`<strong>if…else</strong>` are the most common form of conditional execution in Julia. A typical if the condition may look as shown as follows:

`<strong>if &lt;Boolean condition&gt;<br>&nbsp;&nbsp;&nbsp;&nbsp;#do something<br>else<br>&nbsp;&nbsp;&nbsp;&nbsp;#do the something else<br>end</strong>`

The `<strong>else</strong>` part is optional. The condition has to be Boolean. An integer with the same value as Boolean true or false are not substitutes for the same.

`<strong>julia&gt; if 1<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; println("I am here")<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; end</strong>`

`<strong>ERROR: TypeError: non-boolean (Int64) used in boolean context</strong>`

`<strong>julia&gt; if Bool(1)<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; println("I am here")<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; end<br>I am here</strong>`

The `<strong>if</strong>` expression returns the value of that branch which got executed.

`<strong>julia&gt; i = 1<br>1<br>julia&gt; str = if i &gt; 1<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "Greater"<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; else<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "Less"<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; end<br>"Less"<br>julia&gt; str<br>"Less"</strong>`

The same expression is also represented as a ternary operator using`<strong>?</strong>` and:

`<strong>julia&gt; str = i &gt; 1 ? "Greater" : "Less"<br>"Less"</strong>`

While whitespaces are normally not expected in most expressions, here whitespaces are mandated around `<strong>?</strong>` and `<strong>:</strong>`.

`<strong>julia&gt; str = i &gt; 1? "Greater" : "Less"<br>ERROR: syntax: space required before "?" operator<br>julia&gt; str = i &gt; 1 ? "Greater": "Less"<br>ERROR: syntax: space required before colon in "?" expression</strong>`

# 

`<strong>switch…case</strong>` expressions are typically used when a large number of comparisons are needed as a multiple branching operation. An example `<strong>switch…case</strong>` statement in C/C++ may look something like this.

`<strong>res = “”<br>switch (val) {<br>case 1: res = “One”; break;<br>case 2: res = “Two”; break;<br>case 3: res = “Three”; break;<br>case 4: res = “Four”; break;<br>…<br>default: res = “Unknown”; break<br>}</strong>`

Java and other languages have similar constructs as well. However, such expressions do not exist in Julia. There has been large number of debates around the inclusion or exclusion of similar structures in Julia[1](#a0tlnmnq.html#n4upl4fndor). While a concise representation, two significant issues are known about the `<strong>switch…case</strong>` construct are: the fallback to the next case needing a specific break statement; second, the C/C++ switch statement works only on integral types.

Julia addresses the need for such construct with `<strong>if…else if…else</strong>` structure. The following can clarify the syntax:

`<strong>julia&gt; val = 3<br>3<br>julia&gt; if val == 1<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "one"<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; elseif val == 2<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "two"<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; elseif val == 3<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <a id="page43"></a>"three"<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; elseif val == 4<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "four"<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; else<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"unknown"<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; end<br><br>"three"</strong>`

`<strong>else if vs. elseif</strong>`

Let us look at the following code snippet:

`<strong>julia&gt; if val == 1<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "one"<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; elseif val == 2<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "two"<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; elseif val == 3<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "three"<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; elseif val == 4<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "four"<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; else if val &gt;= 5<br>ERROR: syntax: use "elseif" instead of "else if"</strong>`

`<strong>julia&gt; if val == 1<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "one"<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; elseif val == 2<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "two"<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; elseif val == 3<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "three"<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; elseif val == 4<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "four"<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; else<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; if val &gt;= 5<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "above five"<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; else<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; "below five"<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; end<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; end<br>"three"</strong>`

As can be seen, `<strong>else if</strong>` is a syntactic error. Hence, no ambiguity can arise due to `<strong>elseif</strong>` and `<strong>if</strong>` following an `<strong>else</strong>` expression.

# 

Structured branching like `<strong>if…elseif…else</strong>` is the most preferred mode for conditional execution in a programming language. However, some languages have additional `<strong>goto</strong>` statements to branch the execution to a specific location in the code. Julia also has such a provision using macro `<strong>@goto</strong>` and `<strong>@label</strong>`. They have the following limitations:

1.  They are confined to a specific code block. `<strong>@goto</strong>` can take to a `<strong>@label</strong>` scoped within the same code block.
2.  They cannot be used across functions. However, exceptions are ideal to be used across functions in an execution stack.
3.  They affect the readability of the code. Hence, normally not used in most structured programming languages.

The combination of structured branching and iterations makes the usage of unstructured branching redundant in most Julia programs. The following is a code using `<strong>@goto</strong>` and `<strong>@label</strong>` to compute the sum of consecutive numbers from 1 to 10:

`<strong>julia&gt; begin<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; s = 0<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; n = 10<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; @label loop<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; s = s + n<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; n = n - 1<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; if n &gt; 0<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; @goto loop<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; end<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; s<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; end<br>55</strong>`

The same could have been very easily written using iterative execution using a for loop as shown.

`<strong>julia&gt; s = 0<br>0<br>julia&gt; for i = 1:10<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; s = s + i<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; end<br>julia&gt; s<br>55</strong>`

Definitely, the iterative execution is much simpler a syntax than implementing the sum of a sequence through unstructured branching.

# 

While we realized iterative execution of code using unstructured branching and goto, as a high-level language Julia provides specific language constructs that aid iterative execution. The most common of them are `<strong>for</strong>` and `<strong>while</strong>`, which we will review next.

# 

`<strong>julia&gt; s = 0;<br>julia&gt; for i = 1:10<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; s = s + i<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; end<br>julia&gt; s<br>55</strong>`

In the preceding code snippet, we enumerated from 1 to 10 and added the values to `<strong>s</strong>`. In the for loop, the parameter `<strong>i</strong>` is assigned to a Range object 1:10 which has a step size of 1. The same could have been written as 1:1:10 denoting `<strong>&lt;initial value&gt;:&lt;step size&gt;:&lt;final value&gt;</strong>`. Now if we modify the code to add only the odd values.

`<strong>julia&gt; s = 0;<br>julia&gt; for i = 1:2:10<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; println(i)<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; s = s + i<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; end<br>1<br>3<br>5<br>7<br>9<br>julia&gt; s<br>25</strong>`

As can be seen, changing the range object with step size to 2 was sufficient to achieve the intended result.

# 

Now let us ignore from the sum all the numbers those are divisible by 3.

`<strong>julia&gt; s = 0;<br>julia&gt; for i = 1:10<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; if i % 3 == 0<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; continue<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; end<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; println(i)<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; s = s + i<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; end<br>1<br>2<br>4<br>5<br>7<br>8<br>10<br>julia&gt; s<br>37</strong>`

In this case, `<strong>continue</strong>` is used to skip all the numbers divisible by 3 to be added to `<strong>s</strong>`. `<strong>continue</strong>` ensures the code block subsequent to the expression are excluded from computation while the iterator is still active, while usage of break in the code will terminate the loop.

`<strong>julia&gt; s = 0;<br>julia&gt; for i = 1:10<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; if i % 3 == 0<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; break<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; end<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; println(i)<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; s = s + i<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; end<br>1<br>2<br>julia&gt; s<br>3</strong>`

# 

Not just `<strong>Range</strong>` objects, `<strong>for</strong>` can be used with other sequence objects with iterators as well. We will discuss this in greater detail when we look at iterator interfaces in a later chapter. Here is a code snippet of one such example with `<strong>for…in</strong>` syntax.

`<strong>julia&gt; for i in [5 10 15]<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; println(i)<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; end<br>5<br>10<br>15</strong>`

# 

A single `<strong>for</strong>` loop can iterate over multiple `<strong>Range</strong>` objects. The effect will be iterating over the Cartesian product of the ranges with the outer loops being specified on the left.

`<strong>julia&gt; for i=1:3, j=1:2<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; println((i, j))<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; end<br>(1, 1)<br>(1, 2)<br>(2, 1)<br>(2, 2)<br>(3, 1)<br>(3, 2)</strong>`

The inner ranges can also be influenced by the values of the outer ranges as well.

`<strong>julia&gt; for i=1:3, j=1:i<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; println((i, j))<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; end<br>(1, 1)<br>(2, 1)<br>(2, 2)<br>(3, 1)<br>(3, 2)<br>(3, 3)</strong>`

The `<strong>for</strong>` loop here is a single loop and will get terminated on a `<strong>break</strong>` statement. The `<strong>break</strong>` does not just terminate the inner loop as in the case of a nested `<strong>for</strong>` loop.

`<strong>julia&gt; for i=1:3, j=1:2<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; println((i, j))<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; if i == j<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; break<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; end<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; end<br>(1, 1)</strong>`

`<strong>julia&gt; for i=1:3<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; for j=1:2<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; println((i, j))<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; if i == j<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; break<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; end<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; end<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; end<br>(1, 1)<br>(2, 1)<br>(2, 2)<br>(3, 1)<br>(3, 2)</strong>`

# 

In Julia, for is used with iterators and range objects. However, `<strong>while</strong>` is more flexible and can act on any condition. The execution of the loop continues as long as the condition is true. Here is the general syntax of the same.

`<strong>while &lt;Boolean_condition is true&gt;</strong>`

`<strong>&lt;loop&gt;</strong>`

`<strong>end</strong>`

Now, if we were to consider the same example of adding numbers 1–10 then the code will look like following:

`<strong>julia&gt; s, n = 0, 10;<br>julia&gt; while n &gt; 0<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; s = s + n<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; n = n – 1<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; end<br>julia&gt; s<br>55</strong>`

Execution can be skipped or discontinued by using `<strong>continue</strong>` and `<strong>break</strong>` respectively as we observed with the `<strong>for</strong>` loop.

# 

`<strong>while</strong>` loop evaluates the condition at the beginning of the repetitive evaluation and if the condition evaluates to `<strong>true</strong>` executes the loop. In some cases, one-time execution of the loop is required irrespective of the condition and continuation is carried out by evaluating the condition at the end of the loop. These categories of constructs are typically called the `<strong>do…while</strong>` loops.

`<strong>do</strong>`

`<strong>loop</strong>`

`<strong>while Boolean_condition_is_true</strong>`

Julia does not have this construct available currently. While there are significant discussions around this feature, as a general guideline it is not that difficult to manage with a workaround.

`<strong>skip_eval = true</strong>`

`<strong>while skip_eval || Boolean_condition_is_true<br><br>&nbsp;&nbsp;&nbsp;&nbsp;if skip_eval<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;skip_eval = false<br>&nbsp;&nbsp;&nbsp;&nbsp;end<br>&nbsp;&nbsp;&nbsp;&nbsp;loop<br>end&nbsp;&nbsp;</strong>`

Here is a loop to continuously read the REPL till ‘`<strong>q</strong>`’ is entered as input.

`<strong>julia&gt; skip_eval, ch = true, Char(0)<br>(true, '\0')<br>julia&gt; println("press q &lt;enter&gt; to end the loop")<br>press q &lt;enter&gt; to end the loop<br>julia&gt; while skip_eval || ch != 'q'<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; skip_eval = false<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ch = read(stdin, Char)<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; end</strong>`

`<strong>a<br>q</strong>`

# 

When an exceptional condition occurs in a program, it may not be possible for the function executing to return a valid value or bring the program to a recoverable state. Some programs may report an errors and terminate execution. However, it may be desirable to recover from such conditions and bring the program to a recoverable state while reporting the abnormal condition. Second, the recovered state must be in the call stack across multiple depths of function calls. Hence, it is possible exceptions can lead to a control flow move to another function in the call stack and not just the callers address space.

# 

`<strong>julia&gt; try<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; sqrt(-1)<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; catch e<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; println(e)<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; end<br>DomainError(-1.0, "sqrt will only return a complex result if called with a complex argument. Try sqrt(Complex(x)).")</strong>`

The code anticipated to have an exceptional condition is placed in a section after `<strong>try</strong>`. The exception handling code is added to the section after `<strong>catch. end</strong>` expression ends the `<strong>try</strong>` block.

The code without a `<strong>try…catch</strong>` block will report the following in a REPL:

`<strong>julia&gt; sqrt(-1)<br>ERROR: DomainError with -1.0:<br><a id="page50"></a>sqrt will only return a complex result if called with a complex argument. Try sqrt(Complex(x)).<br>Stacktrace:<br>&nbsp;[1] throw_complex_domainerror(::Symbol, ::Float64) at .\math.jl:33<br>&nbsp;[2] sqrt at .\math.jl:573 [inlined]<br>&nbsp;[3] sqrt(::Int64) at .\math.jl:599<br>&nbsp;[4] top-level scope at REPL[10]:1</strong>`

As can be seen, the REPL has provided a default `<strong>try…catch</strong>` implementation that takes in the `<strong>DomainError</strong>` exception and prints an error with a stack trace. Julia has quite a few standard exceptions like `<strong>ErrorException</strong>`, `<strong>DomainError</strong>`, `<strong>ArgumentError</strong>`, `<strong>BoundsError</strong>`, and so on. All errors are derived from an abstract type `<strong>Exception</strong>`.

# 

While `<strong>catch</strong>` provides options to capture and take action on an exception, one can decide to propagate the exception further than handling it using the function `<strong>rethrow</strong>`. The error printed is the default error handling of the REPL

`<strong>julia&gt; try<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; sqrt(-1)<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; catch e<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; rethrow()<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; end<br>ERROR: DomainError with -1.0:<br>sqrt will only return a complex result if called with a complex argument. Try sqrt(Complex(x)).<br>Stacktrace:<br>&nbsp;[1] throw_complex_domainerror(::Symbol, ::Float64) at .\math.jl:33<br>&nbsp;[2] sqrt at .\math.jl:573 [inlined]<br>&nbsp;[3] sqrt(::Int64) at .\math.jl:599<br>&nbsp;[4] top-level scope at REPL[11]:2</strong>`

One can also `<strong>throw</strong>` a custom exception when some unwanted condition arises. The thrown object does not have to be of Exception type always. It can be any object. An integer is thrown as the following example:

`<strong>julia&gt; try<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; throw(1)<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; catch e<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; println(typeof(e))<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; end<br>Int64</strong>`

Exceptions are to be used for managing exceptional conditions. If the behavior is a mere representation of a regular condition in the code flow other control flows like `<strong>if…else</strong>` may be used. Second, exceptions add to significant execution overheads. Hence, they must be used judiciously only when required.

# 

When a resource is in use, an exceptional situation may force exit the function execution abruptly, the resources in such cases cannot be reclaimed. The `<strong>finally</strong>` clause ensures the code is executed in normal execution as well as exceptional conditions ensuring the resources are reclaimed. In the sample, the file handle `<strong>f</strong>` will be closed even when there is an exception as it is otherwise.

`<strong>julia&gt; f = open("file")<a id="ftn2a" href="#ftn2"><sup>2</sup></a><br>julia&gt; try<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; b = read(f)<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; finally<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; close(f)<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; end</strong>`

# 

What value do the exception objects add with such an elaborate architecture? They affect execution speed as every time there is a stack unwinding, there is a need to verify the exception objects. One of the major advantages they provide is the ability to track the stack where the exception occurred. Thus, one can get a trace of the error propagation. Second, the formation of an exception object provides the ability to provide enough information regarding the error.

`<strong>julia&gt; sqrt(-1)<br>ERROR: DomainError with -1.0:<br>sqrt will only return a complex result if called with a complex argument. Try sqrt(Complex(x)).</strong>`

`<strong>Stacktrace:<br>&nbsp;[1] throw_complex_domainerror(::Symbol, ::Float64) at .\math.jl:33<br>&nbsp;[2] sqrt at .\math.jl:573 [inlined]<br>&nbsp;[3] sqrt(::Int64) at .\math.jl:599<br>&nbsp;[4] top-level scope at REPL[1]:1</strong>`

`<strong>DomainError</strong>` has two attributes. The `<strong>val</strong>` attribute representing the value that led to the error and the `<strong>msg</strong>` attribute elaborating on the message details. You can define your own exception by creating it as a subtype of the `<strong>Exception</strong>` abstract type.

`<strong>julia&gt; struct MyException &lt;: Exception<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; params1<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; params2<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; …<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; paramsn<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; end</strong>`

# 

Stack traces are very important sets of information obtained from exception handling. The function `<strong>catch_backtrace()</strong>` reports the stack trace at the point the exception was raised and `<strong>stacktrace()</strong>` function provides interpretation of the same.

`<strong>julia&gt; try<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; sqrt(-1)<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; catch e<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; stacktrace(catch_backtrace())<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; end<br>16-element Array{Base.StackTraces.StackFrame,1}:<br>&nbsp;throw_complex_domainerror(::Symbol, ::Float64) at math.jl:33<br>&nbsp;sqrt at math.jl:573 [inlined]<br>&nbsp;sqrt(::Int64) at math.jl:599<br>&nbsp;top-level scope at REPL[17]:2<br>&nbsp;eval(::Module, ::Any) at boot.jl:331<br>&nbsp;eval_user_input(::Any, ::REPL.REPLBackend) at REPL.jl:134<br>&nbsp;repl_backend_loop(::REPL.REPLBackend) at REPL.jl:195<br>&nbsp;start_repl_backend(::REPL.REPLBackend, ::Any) at REPL.jl:180<br>&nbsp;run_repl(::REPL.AbstractREPL, ::Any; …) at REPL.jl:292<br>&nbsp;run_repl(::REPL.AbstractREPL, ::Any) at REPL.jl:288<br>&nbsp;(::Base.var"#806#808"{…})(::Module) at client.jl:399<br>&nbsp;#invokelatest#1 at essentials.jl:710 [inlined]<br>&nbsp;invokelatest at essentials.jl:709 [inlined]<br>&nbsp;run_main_repl(::Bool, …) at client.jl:383<br>&nbsp;exec_options(::Base.JLOptions) at client.jl:313<br>&nbsp;_start() at client.jl:506</strong>`

# 

Julia supports parallel programming as part of the language/platform features. The parallel programming interfaces are designed around a task framework that utilizes a cooperating multiprogramming architecture. The experimental thread Application Programming Interface (API) utilizes the operating system threads as a preemptive multiprogramming interface. We will review both these interfaces as we discuss the functions and methods in details.

# 

Julia provides multiple control flow architectures to aid branching, iterative programming, parallel execution, and exception handling. One aspect that can be considered as a part of branching strategy is recursive programming that benefits significantly due to the multiple dispatch architecture of the Julia functions. In the next chapter, we will look at the Julia functions and methods. Branching and control flow being a fundamental concepts of a programming language; we will review some of these concepts with functions and methods as well.

# 

1.  Use unstructured branching to implement a `<strong>do…while</strong>` condition and add 10 numbers.
2.  Write a loop that adds numbers that are divisible by 5 between 51 and 100.
3.  Error messages are shown when an undefined variable is being used as has been discussed in . Is that an exception handling scenario as well? If so what kind of exceptions are being used.
4.  What is the difference between `<strong>continue</strong>` and `<strong>break</strong>`? Discuss with examples.
5.  What is the limitation of using a single `<strong>for</strong>` loop in iterating over multiple ranges or iterators? Why should one utilize multiple for loops for iterating?

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

[1](#a0tlnmnq.html#n4upl4fndos) **[https://github.com/JuliaLang/julia/issues/18285](https://github.com/JuliaLang/julia/issues/18285)**

The `file` must exist in the current working directory. You can see the current working directory using the function `pwd()`.

Java and other languages have similar constructs as well. However, such expressions do not exist in Julia. There has been large number of debates around the inclusion or exclusion of similar structures in Julia1. While a concise representation, two significant issues are known about the `<strong>switch…case</strong>` construct are: the fallback to the next case needing a specific break statement; second, the C/C++ switch statement works only on integral types.

**[https://github.com/JuliaLang/julia/issues/18285](https://github.com/JuliaLang/julia/issues/18285)**

# 

# 

# 

Most of the code can be typed in a shell-like REPL interface as if you are writing a script. But the real capabilities can be unearthed when you use functions, pass around data into, or out of them. Use the power of multiple dispatch interfaces. Learning about functions and methods becomes a foundational need in Julia programming.

# 

In this chapter, we will cover the following topics:

*   Introduction
*   Short form
*   Input arguments
*   Return value
*   Recursion
*   Polymorphic methods
*   Type interaction

# 

In this chapter, the reader shall be able to understand functions, and their many syntactic forms. We will review operators and their mathematical relationships functions with the variable number of arguments. We shall discuss the polymorphic behavior of functions, multiple return values, and most importantly recursion.

# 

No production application is developed in one single file with a sequence of program statements. Most programmers will like to segregate programs into small chunks of executable units. This addresses two issues. First, it creates reusable units that can be invoked several times from various places in the larger program. Second, small units can be easily unit tested. Thus, they improve code reliability. In this chapter, we will try to find a solution for the 8-queens problem programmatically, and in doing so understand functions in Julia.

# 

This is a classic problem in the field of algorithms and artificial intelligence. The goal is to place maximum number of queens on a chessboard such that no queen attacks the other. A possible arrangement is shown as follows. However, this solution is not unique. We will write a program to arrive at an arrangement for the 8-queens:

![](n4upl4fndqm.jpeg)

**Figure 4.1:** Eight queens problem - one of many possible solutions

Before we design the complete solution to the problem, we must have a program unit that takes inputs of two queen locations and report if the queens are attacking each other.

# 

These small programming units in Julia are called `<strong>functions</strong>`. We will create a function that takes as inputs positions of two queens and returns if the queens’ paths are overlapping. Here are the conditions when the queens will attack each other.

1.  Queens have the same x or y coordinates: *x[2]\= x[1] or y[2] = y[1]*
2.  Queens are at diagonals to each other, which means: *|x[2]\-x[1] |=|y[2] - y[1] |*

If two sides are in the same sign, we get: *x[1] - y[1]\= x[2] - y[2].* Similarly, if they are in the opposite signs we will get: *x[1] + y[1]\= x[2] + y[2].*

Based on the observations we have the following function in Julia:

`<strong>julia&gt; function attacks(x1, y1, x2, y2)<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; if x1 == x2<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; return true<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; elseif y1 == y2<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; return true<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; elseif x1 - y1 == x2 - y2<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; return true<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; elseif x1 + y1 == x2 + y2<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; return true<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; else<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; return false<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; end<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; end<br>julia&gt; attacks(1, 2, 4, 5)<br>true<br>julia&gt; attacks(1, 2, 4, 6)<br>false</strong>`

The `<strong>function…end</strong>` are the delimiters within which a function is defined. The `<strong>return</strong>` statement is used to return the final output from the function. A function can have multiple `<strong>return</strong>` statements. The preceding function has several return statements; all returning `<strong>Bool</strong>` values.

# [1](#zhs8j9hj.html#n4upl4fndj1)

In the preceding function, we used a few operators in conjunction with a few variables. It is clear that + and – are addition and subtraction binary operators between two numbers. C/C++ programmers will be able to identify the ‘==’ as the equality operator between two numbers. Operators are treated like normal functions in Julia and they can return a value. The ‘==’ operator returns a `<strong>Bool</strong>` value. The function is made up of only `<strong>if</strong>` conditions and `<strong>Bool</strong>` return values; we can rewrite the function with a simple combination of logical ‘or’ operator written as (||).

`<strong>julia&gt; function attacks(x1, y1, x2, y2)<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; return x1 == x2 || y1 == y2 || x1 - y1 == x2 - y2 || x1 + y1 == x2 + y2<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; end</strong>`

# 

The `<strong>return</strong>` keyword though recommended is not mandatory for a Julia function. When not specified, the value of the expression before the `<strong>end</strong>` statement is returned as the return value of the function. Thus, the following is another representation of the function stated previously:

`<strong>julia&gt; function attacks(x1, y1, x2, y2)<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; x1 == x2 || y1 == y2 || x1 - y1 == x2 - y2 ||<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; x1 + y1 == x2 + y2<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; end</strong>`

Julia further simplifies the function to look more like a mathematical expression. The same function can also be written as:

`<strong>julia&gt; attacks(x1, y1, x2, y2) =<br>&nbsp;&nbsp;&nbsp;&nbsp;(x1 == x2 || y1 == y2 || x1 - y1 == x2 - y2 ||<br>&nbsp;&nbsp;&nbsp;&nbsp; x1 + y1 == x2 + y2)<br>attacks (generic function with 1 method)</strong>`

Julia provides the flexibility of representing complex compound expressions by specifying them between `<strong>begin…end</strong>`. However, it is not considered a good practice to define the short functional form of Julia functions that are longer than a single statement. Although the following is a valid Julia function, as a style guideline it is discouraged.

`<strong>julia&gt; attacks(x1, y1, x2, y2) = begin<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; if x1 == x2<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; return true<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; elseif y1 == y2<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; return true<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; elseif x1 - y1 == x2 - y2<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; return true<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; elseif x1 + y1 == x2 + y2<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; return true<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; else<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; return false<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; end<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;end<br>attacks (generic function with 1 method)</strong>`

# 

Functions in Julia can be like any other object and can be assigned to a variable. We could define an anonymous function and assign into the variable `<strong>attacks_var</strong>` by the following code:

`<strong>julia&gt;attacks_var = (x1, y1, x2, y2)-&gt;<br>&nbsp;&nbsp;&nbsp;&nbsp;(x1 == x2 || y1 == y2 ||<br>&nbsp;&nbsp;&nbsp;&nbsp; x1 - y1 == x2 - y2 || x1 + y1 == x2 + y2)<br>#1 (generic function with 1 method)<br>julia&gt; attacks_var(1, 2, 3, 4)<br>true</strong>`

`<strong>attacks_var</strong>` though behaves like a function is actually a variable to which an anonymous function is assigned. This gives substantial flexibility to Julia and the functionality can be perceived similar to a lambda expression in *Python* or *Lisp*.

# 

The function `<strong>attacks</strong>` has four input arguments, and it returns whether the queens have overlapping paths.

# 

What happens if we call the method with 5 or 3 arguments?

`<strong>julia&gt; attacks(1, 2, 3, 4, 5)<br>ERROR: MethodError: no method matching attacks(::Int64, ::Int64, ::Int64, ::Int64, ::Int64)<br>Closest candidates are:<br>&nbsp;&nbsp;&nbsp;&nbsp;attacks(::Any, ::Any, ::Any, ::Any) at REPL[1]:1</strong>`

`<strong>julia&gt; attacks(1, 2, 3)<br>ERROR: MethodError: no method matching attacks(::Int64, ::Int64, ::Int64)<br>Closest candidates are:<br>&nbsp;&nbsp;&nbsp;&nbsp;attacks(::Any, ::Any, ::Any, ::Any) at REPL[1]:1</strong>`

Errors are reported stating the function is only defined to consider 4 arguments or input parameters. However, the function can take any type as a data input. This is possible as the parameter type is `<strong>Any</strong>`, considering no parameter types are specified in the function definition.

Input parameters are optional. Following is a function with no input parameters:

`<strong>julia&gt; function hello_world()<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; println("Hello World!!!")<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; end<br>hello_world (generic function with 1 method)<br>julia&gt; hello_world()<br>Hello World!!!</strong>`

# 

It is possible to define functions in Julia that take variable number of arguments (`<strong>varargs</strong>`). The arguments are matched using pattern matching and recursion. Here are a few examples:

`<strong>julia&gt; mysum(x, y…) = x + mysum(y…)<br>mysum (generic function with 1 method)<br>julia&gt; mysum(x) = x<br>mysum (generic function with 2 methods)<br>julia&gt; mysum(1, 2)<br>3<br>julia&gt; mysum(1, 2, 3)<br>6<br>julia&gt; mysum(1, 2, 3, 4, 5, 6, 7)<br>28</strong>`

Let us look at another function that computes maximum values from the arguments.

`<strong>julia&gt; mymax(x, y…) = mymax(x, mymax(y…))<br>mymax (generic function with 1 method)<br>julia&gt; mymax(x, y) = x &gt; y ? x : y<br>mymax (generic function with 2 methods)<br>julia&gt; mymax(1, 2, 3)<br>3<br>julia&gt; mymax(3, 2, 1)<br>3<br>julia&gt; mymax(4, 10, 3, 2, 1)<br>10</strong>`

What happens when you specify `<strong>mymax(x)</strong>`? Naturally, it must give an error as there is no function that takes only one argument as input.

`<strong>julia&gt; mymax(1)<br>ERROR: MethodError: no method matching mymax()<br>Closest candidates are:<br>&nbsp;&nbsp;mymax(::Any, ::Any) at REPL[7]:1<br>&nbsp;&nbsp;mymax(::Any, ::Any…) at REPL[6]:1</strong>`

It can easily be fixed by adding a single argument function as follows:

`<strong>julia&gt; mymax(x) = x<br>mymax (generic function with 3 methods)<br>julia&gt; mymax(1)<br>1</strong>`

Let us find out how many methods are defined for `<strong>mymax</strong>`.

`<strong>julia&gt; methods(mymax)<br># 3 methods for generic function "mymax":<br>[1] mymax(x) in Main at REPL[12]:1<br>[2] mymax(x, y) in Main at REPL[7]:1<br>[3] mymax(x, y…) in Main at REPL[6]:1</strong>`

We have 3 `<strong>mymax</strong>` methods with 1, 2, and the variable number of arguments.

# 

Let us modify the `<strong>mymax</strong>` function slightly so that single argument function is not created.

`<strong>julia&gt; mymax(x, y…) = mymax(x, mymax(y…))<br>mymax (generic function with 1 method)<br>julia&gt; mymax(x, y=x) = x &gt; y ? x : y<br>mymax (generic function with 3 methods)<br>julia&gt; methods(mymax)<br># 3 methods for generic function "mymax":<br>[1] mymax(x) in Main at REPL[2]:1<br>[2] mymax(x, y) in Main at REPL[2]:1<br>[3] mymax(x, y…) in Main at REPL[1]:1<br>julia&gt; mymax(1)<br>1</strong>`

We introduced only two functions; one with variable number of parameters and the other with 2 parameters but having a default parameter. The system generated 3 functions internally one with one parameter that maps to the function with 2 parameters but with a default parameter.

# 

When a `<strong>…</strong>` operator is used in a function definition, the behavior is called `<strong>slurping</strong>`. It tries to take many inputs and represent them as a single variable.

`<strong>julia&gt; function test(args…)<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; println(typeof(args))<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; end<br>test (generic function with 1 method)<br>julia&gt; test(1, 2, 3, 4.0)<br>Tuple{Int64,Int64,Int64,Float64}</strong>`

Since, `<strong>args</strong>` is a Tuple one can access the parameter values by indexing as well. Some implementations can use recursion to work with `<strong>varargs</strong>` functions as we have observed with the `<strong>mymax</strong>` and `<strong>mysum</strong>` methods earlier.

Let us get back to our queens `<strong>attacks</strong>` function again. It is natural for queens to be represented as a tuple of x and y location for example, (1, 2). However, the function we created has 4 parameters. In such cases, splatting helps. The `<strong>…</strong>` operator in a function argument flattens the collections and passes individual values as function inputs.

`<strong>julia&gt; q1 = (1, 2);<br>julia&gt; q2 = (3, 4);<br>julia&gt; attacks(q1…, q2…)<br>true</strong>`

While slurping and splatting provide significant benefits to functional programming in Julia, they may not be the most performance-friendly operators. Hence, they must be used sparingly and judiciously where required.

# 

All Julia functions return a value either explicitly or implicitly. We saw these examples as a part of our various definitions of `<strong>attacks</strong>` functions previously. Can a function return nothing at all? Well, such functions will still return `<strong>nothing</strong>` which is a singleton instance of type `<strong>Nothing</strong>`. The `<strong>hello_world()</strong>` function shown previously is an example of the same.

`<strong>julia&gt; a = hello_world()<br>Hello World!!!<br>julia&gt; typeof(a)<br>Nothing</strong>`

# 

Let us take the example of the verbose attacks function again but introducing some minor modifications to the same. We removed the `<strong>else</strong>` statement from the function returning a `<strong>false</strong>`.

`<strong>julia&gt; function attacks(x1, y1, x2, y2)<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; if x1 == x2<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; return true<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; elseif y1 == y2<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; return true<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; elseif x1 - y1 == x2 - y2<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; return true<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; elseif x1 + y1 == x2 + y2<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; return true<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; end<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; end<br>attacks (generic function with 1 method)<br>julia&gt; attacks(1, 2, 3, 4)<br>true<br>julia&gt; attacks(1, 2, 3, 5)<br>julia&gt; a = attacks(1, 2, 3, 4)<br>true<br>julia&gt; b = attacks(1, 2, 3, 5)<br>julia&gt; typeof(a), typeof(b)<br>(Bool, Nothing)</strong>`

A programmer may find it acceptable to use nothing instead of `<strong>false</strong>` in her code. But, such practices are not desirable due to a possible type of stability issue. A caller to the function may get a `<strong>Bool</strong>` or `<strong>Nothing</strong>` based on the input to the function. These kinds of inconsistencies can lead to the caller not be able to allocate the proper resources for the return value and may do many additional allocations than needed or may have to assign Any as a type for the return type. There are some instances of code performance being affected due to type stability issues. We will discuss these in detail in a chapter on performance; it is generally a good idea to return a consistent type of return value from a function. Second, type safety issues cannot be eliminated completely. They do not always adversely affect the performance. Julia provides tools to identify them. We will discuss them in detail later. Return types are not the only source of type safety issues. Since Julia types are optional, varieties of input arguments, and interaction of input arguments with constant expressions can lead to type safety issues as well. We shall review some of these with examples in the chapter on performance management.

# 

Most programming languages insist that a function returns only one value. The same applies to Julia as well. Julia has a `<strong>Tuple</strong>` type which can be used to return multiple values as a `<strong>Tuple</strong>`. We will extend the `<strong>attacks</strong>` function to return to us why the paths are intersecting as another return value along with the Bool value.

`<strong>julia&gt; function attacks_with_reason(x1, y1, x2, y2)<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; if x1 == x2</strong>`

`<strong>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; return true, :x<a id="ftn2a" href="#ftn2"><sup>2</sup></a></strong>`

`<strong>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; elseif y1 == y2<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; return true, :y<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; elseif x1 - y1 == x2 - y2<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; return true, :diag<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; elseif x1 + y1 == x2 + y2<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; return true, :xdiag<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; else<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; return false, :na<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; end<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; end<br>attacks_with_reason (generic function with 1 method)<br>julia&gt; attacks_with_reason(1, 2, 3, 4)<br>(true, :diag)<br>julia&gt; attacks_with_reason(1, 2, 3, 1)<br>(false, :na)<br>julia&gt; attacks_with_reason(1, 2, 3, 2)<br>(true, :y)<br>julia&gt; attacks_with_reason(1, 2, 2, 1)<br>(true, :xdiag)</strong>`

# 

Recursion is a commonly used programming paradigm in functional programming and is equally popular in Julia as well. In recursive programming, the following processes are followed:

1.  The function should call itself for a subset of the problem.
2.  There must be an assured termination condition where the recursion must stop.
3.  The results are to be aggregated to present the output.

We will apply all these conditions to develop our solution for the 8-queens puzzle. So far we have found out a mechanism to know if a queen attacks another. We will approach the problem by adding another queen to each row from top to bottom one at a time recursively. Suppose we decide to consider a chessboard of size 8×8.

1.  We will consider the 8th row and add a queen on the 8th row starting column location 1.
2.  Then we will add a queen to the 7th row. 
    1.  We start from column 1 and keep increasing the count such that we can place a queen at some column such that no other queen is attacked. We will use the `<strong>attacks</strong>` function we developed earlier for the same.
    2.  If a queen can be placed, it is placed and the function is called recursively to check if a queen can be placed in the 6th row and so on for the 5th and 4th row till we reach the first row.
    3.  If we fail to place a queen, we skip that row.
        
        Similarly, we keep adding the queen to the 5th, 4th rows, and so on. till we reach the first row.
        
3.  If we are able to add a queen to the first row we return 0.
4.  If we fail to add a queen to a row we return -1.
5.  When we fail to add a queen to a row we backtrack and try adding a queen in the previous row at a different location and redo the activity again.
6.  The Julia `<strong>varargs</strong>` function as a recursive method is very useful as it provides a natural mechanism of keeping track of all the columns added.

The proposed approach is not confined to an 8-queens problem on a standard chessboard but can be utilized for boards of any size say an N-queens problem.

`<strong>julia&gt; attacks(x1, y1, x2, y2) =<br>&nbsp;&nbsp;&nbsp;&nbsp;(x1 == x2 || y1 == y2 || x1 - y1 == x2 - y2 ||<br>&nbsp;&nbsp;&nbsp;&nbsp; x1 + y1 == x2 + y2)<br>attacks (generic function with 1 method)<br><br>julia&gt; function queens(N, xs…)<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; lxs = length(xs)<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; c = N - lxs&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;## Step 6<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; if c == 0&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;## Step 3<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; println("Final Positions: ", reverse(xs))<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; return 0<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; end<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; for i=1:N&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;## Step 1 &amp; 2<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; res = false&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;## Step 2(a)<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; for j=1:lxs<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; res = res || attacks(xs[j], N-j+1, i, c)<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; end<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; res &amp;&amp; continue<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; v = queens(N, xs…, i)&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;## Step 2(c)<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; v &lt; 0 || return v<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; end<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; return -1&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;## Step 4<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; end<br>queens (generic function with 1 method)</strong>`

`<strong>julia&gt; queens(8)<br>Final Positions: (4, 2, 7, 3, 6, 8, 5, 1)<br>0</strong>`

To observe the behavior of the varargs as a part of recursion one can add a `<strong>println</strong>` statement to the beginning of the function call.

`<strong>julia&gt; function queens(N, xs…)<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; println(xs)<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; lxs = length(xs)<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; c = N – lxs<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; …</strong>`

`<strong>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; end</strong>`

The output of `<strong>queens(8)</strong>` is as follows:

`<strong>julia&gt; queens(8)<br>()<br>(1,)<br>(1, 3)<br>(1, 3, 5)<br>(1, 3, 5, 2)<br>(1, 3, 5, 2, 4)<br>(1, 3, 5, 2, 8)<br>(1, 3, 5, 7)<br>…<br>(1, 5, 7, 2)<br>(1, 5, 7, 2, 4)<br>(1, 5, 7, 2, 4, 8)<br>(1, 5, 7, 2, 6)<br>(1, 5, 7, 2, 6, 3)<br>(1, 5, 7, 2, 6, 8)<br>(1, 5, 8)<br>(1, 5, 8, 2)<br>(1, 5, 8, 2, 4)<br>(1, 5, 8, 2, 4, 7)<br>(1, 5, 8, 2, 4, 7, 3)<br>(1, 5, 8, 2, 7)<br>(1, 5, 8, 2, 7, 3)<br>(1, 5, 8, 2, 7, 3, 6)<br>(1, 5, 8, 6)<br>(1, 5, 8, 6, 3)<br>(1, 5, 8, 6, 3, 7)<br>(1, 5, 8, 6, 3, 7, 2)<br>(1, 5, 8, 6, 3, 7, 2, 4)<br>Final Positions: (4, 2, 7, 3, 6, 8, 5, 1)</strong>`

`<strong>0</strong>`

![](n4upl4fndqn.jpeg)

**Figure 4.2:** The solution as per the output of the code

# 

Let us look at the code for computing cumulative sum for any natural number.

`<strong>function mycumsum(n)<br>&nbsp;&nbsp;&nbsp;&nbsp; if n &lt;= 0<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; return 0<br>&nbsp;&nbsp;&nbsp;&nbsp; else<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; return n + mycumsum(n-1)<br>&nbsp;&nbsp;&nbsp;&nbsp; end<br></strong>`

While this code is fairly simple after every function calls the computation from the previous call has to be aggregated and added to the current function stack variable. Thus, at every function call, the stack frame has to be constructed before a new function is called. Why?

![](n4upl4fndqo.jpeg)

**Figure 4.3:** In a function call, stack frame has to be created and all internal temporary variables are stored on the stack. %0 has to be retained during stack unwinding to compute the return value. Each row is a stack frame before the call is made to the recursive function

Let us rewrite this function in the following manner with an accumulator (`<strong>acc</strong>`) in the function argument.

`<strong>julia&gt; function mycumsum(n, acc=0)<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; if n &lt;= 0<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; return acc<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; else<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; return mycumsum(n-1, n+acc)<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; end<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<br>mycumsum (generic function with 2 methods)<br>julia&gt; mycumsum(4)<br>10<br>julia&gt; mycumsum(10)<br>55</strong>`

There is no further computation after the recursive function call. The aggregation is to be carried out through the accumulator. There is no need to construct a stack frame on every function call.

![](n4upl4fndqp.jpeg)

**Figure 4.4:** When each recursive function is called a new frame is created. The computations are carried out in the forward direction. There is no need for an unwinding of the stack for result aggregation as the last function call has the computed result. Unwinding is only needed to pass the return value and reclaiming of the resources

Hence, the function call can be replaced with a jump instruction. Some functional programming languages like *Lisp* or *Lua* identify such conditions programmatically and eliminate the stack frame creation. This process is called `<strong>Tail Call Optimization</strong>` (`<strong>TCO</strong>`). In functional programming, recursion is given higher importance over iterative programming. Stack frame creation consumes memory. Hence, deep recursive function calls can lead to stack overflow. Unlike Lisp, Julia does not have native support for TCO[3](#zhs8j9hj.html#n4upl4fndj2).

![](n4upl4fndqq.jpeg)

**Figure 4.5:** A TCO optimizing compiler would have converted to an iteratitive code

Although Julia is a functional programming language, it also has complete iterative programming support. Some programmers have used Julia macros and generative programming to emulate TCO-like behavior.

# 

In object-oriented programming, polymorphism is used to describe the change of behavior of a method based on the objects that it is acting upon. Simply put, the `<strong>area</strong>` method called on a `<strong>rectangle</strong>` object will be a different computation from the `<strong>area</strong>` method called on a `<strong>triangle</strong>` object. We saw functions behave differently based on the number of arguments in earlier examples. In this section, we shall see functions can behave differently based on the types of arguments. In Julia, when functions of the same name have different behaviors depending on the type and count of the arguments, they are called `<strong>methods</strong>`.

# 

The following example shows two `<strong>area</strong>` functions: one for `<strong>Triangle</strong>` and the other for the `<strong>Rectangle</strong>` type. Since both the shapes are subtypes of a parent abstract type `<strong>Shape</strong>`, we shall modify the default `<strong>show</strong>` method so that the relevant `<strong>area</strong>` function is called from the `<strong>show</strong>` method. `<strong>Base.show</strong>` is the default method that is called to display an object on the REPL.

`<strong>abstract type Shape end</strong>`

`<strong>struct Rectangle &lt;: Shape<br>&nbsp;&nbsp;&nbsp;&nbsp;w::Float32<br>&nbsp;&nbsp;&nbsp;&nbsp;h::Float32<br>end<br><br>struct Triangle &lt;: Shape<br>&nbsp;&nbsp;&nbsp;&nbsp;a::Float32<br>&nbsp;&nbsp;&nbsp;&nbsp;b::Float32<br>&nbsp;&nbsp;&nbsp;&nbsp;c::Float32<br>end</strong>`

`<strong>area(r::Rectangle)=r.w*r.h<br><br>function area(t::Triangle)<br>&nbsp;&nbsp;&nbsp;&nbsp;a, b, c = t.a, t.b, t.c<br>&nbsp;&nbsp;&nbsp;&nbsp;s = (a + b + c)/2<br>&nbsp;&nbsp;&nbsp;&nbsp;return sqrt(s*(s-a)*(s-b)*(s-c))<br>end</strong>`

`<strong>julia&gt;r, t = Rectangle(3, 4), Triangle(3, 4, 5)<br>(Rectangle(3.0f0, 4.0f0), Triangle(3.0f0, 4.0f0, 5.0f0))<br>julia&gt; area(r)<br>12.0f0<br>julia&gt; area(t)<br>6.0f0<br>julia&gt; Base.show(io::IO, s::Shape) =<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; print(io, "Shape Type:", typeof(s), " Area:", area(s))<br>julia&gt; r<br>Shape Type:Rectangle Area:12.0<br>julia&gt; t<br>Shape Type:Triangle Area:6.0</strong>`

# [4](#zhs8j9hj.html#n4upl4fndj3)

In a typical object-oriented language, a method is associated with an object. Based on the object type a specific function is called. This kind of method dispatch is called as a `<strong>single dispatch interface</strong>`. However, languages that support multiple dispatch interfaces do not associate a function to a specific type. Depending on the runtime type of the object they resolve to the relevant method interface and invoke the most relevant method. `<strong>area</strong>` method is not a method for the `<strong>Rectangle</strong>` type or the `<strong>Triangle</strong>` type. Rather based on the object type they are to be looked up from a multiple dispatch lookup. This architecture is also seen with languages like *Lisp*.

# 

Objects can have inherent constraints. When created they must be enforced so that invalid objects are not created. Constructors ascertain such behaviors. In the `<strong>Rectangle</strong>` or `<strong>Triangle</strong>` types, one can create invalid objects by providing negative values for the sides.

`<strong>struct RectangleA<br>&nbsp;&nbsp;&nbsp;&nbsp;w::Float32<br>&nbsp;&nbsp;&nbsp;&nbsp;h::Float32<br>&nbsp;&nbsp;&nbsp;&nbsp;function RectangleA(w::Real, h::Real)<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(w &gt; 0 &amp;&amp; h &gt; 0) ||<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;error("invalid rectangle with non-positive h or w")<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;return new(w, h)<br>&nbsp;&nbsp;&nbsp;&nbsp;end<br>end</strong>`

The creation of the object now invokes the constructor.

`<strong>julia&gt; a = RectangleA(1.0, -4.0)<br>ERROR: invalid rectangle with non-positive h or w<br>Stacktrace:<br>…</strong>`

`<strong>julia&gt; a = RectangleA(1//5<a id="ftn5a" href="#ftn5"><sup>5</sup></a>, 4//5)<br>Rectangle(0.2f0, 0.8f0)<br>julia&gt; a = RectangleA(1, 4)<br>Rectangle(1.0f0, 4.0f0)<br>julia&gt; a = RectangleA(1.0, 4.0)<br>Rectangle(1.0f0, 4.0f0)<br>julia&gt; a = RectangleA(1.0, 4)<br>Rectangle(1.0f0, 4.0f0)</strong>`

The constructors can take any `<strong>Real</strong>` number as a parameter and they ensure no non-positive value is permitted as part of the arguments. Suppose we were to create two additional constructors to construct squares.

`<strong>RectangleA(a=1.0)=RectangleA(a, a)<br><br>julia&gt; RectangleA()<br>RectangleA(1.0f0, 1.0f0)<br>julia&gt; RectangleA(2.0)<br>RectangleA(2.0f0, 2.0f0)<br>julia&gt; methods(RectangleA)<br># 3 methods for type constructor:<br>[1] RectangleA() in Main at REPL[7]:1<br>[2] RectangleA(w::Real, h::Real) in Main at REPL[1]:4<br>[3] RectangleA(a) in Main at REPL[7]:1</strong>`

We created the two constructors with one statement as the other one was created due to the default argument. You can see now 3 constructors are created. Two of them are outer constructors, declared outside of the type definition. One inner constructor declared within the type definition. The internal constructors are created for ensuring construction constraints are enforced. The external constructors are used mostly for convenience and providing construction flexibility. When no constructors are provided then a default constructor is provided that initializes the attributes of the type. In the preceding `<strong>RectangleA</strong>` example, the following default inner constructor will be created when no other inner constructor is defined:

`<strong>RectangleA(h::Float32, w::Float32)=new(h, w)</strong>`

The function `<strong>new</strong>` is a special function that can be used only inside the inner constructor. It creates the object while initializing the parameters in the order in which they are defined.

# 

The constructor must return a well-initialized object. In Julia, the objects are expected to be initialized properly at the end of a call to the constructor. While there are cases where compound objects may not be initialized due to performance reasons they are more of exceptions than the rule. The constructor must return an object of the type it is trying to construct.

# 

In , when we discussed the parametric data types, we did not elaborate on their impact on function and dispatch interfaces or on the constructors. In the following `<strong>RectangleB</strong>` type we create, we will like to use any of the Real types as parametric types for the Rectangle attributes.

`<strong>struct RectangleB{T &lt;: Real}<br>&nbsp;&nbsp;&nbsp;&nbsp;w::T<br>&nbsp;&nbsp;&nbsp;&nbsp;h::T<br>end</strong>`

`<strong>julia&gt; RectangleB(2//3, 1//4)<br>RectangleB{Rational{Int64}}(2//3, 1//4)</strong>`

`<strong>julia&gt; RectangleB(1f0, 2f0)<br>RectangleB{Float32}(1.0f0, 2.0f0)</strong>`

`<strong>julia&gt; RectangleB(2//3, 1f0)<br>ERROR: MethodError: no method matching RectangleB(::Rational{Int64}, ::Float32)<br>Closest candidates are:<br>&nbsp;&nbsp;RectangleB(::T, ::T) where T&lt;:Real at REPL[6]:2</strong>`

The default constructor `<strong>RectangleB(::T, ::T)</strong>` where `<strong>T&lt;:Real</strong>` is created but `<strong>T</strong>` can be only one specific type. It cannot be of `<strong>Rational{Int64}</strong>` and `<strong>Float32</strong>` the same time.

`<strong>julia&gt; RectangleB{Int}('a', 1f0)<br>RectangleB{Int64}(97, 1)</strong>`

However, when we specify the parameter type as part of the constructor explicitly, types are converted to the proper ones.

# 

Let us create two methods called `<strong>aspect_ratio</strong>` and `<strong>area</strong>`. Aspect ratio is the ratio of the width to height in a rectangle. Area is multiplication of height with width in case of a rectangle. We have seen an implementation of the area method in an earlier example.

`<strong>area(r::RectangleB)=r.w*r.h</strong>`

`<strong>aspect_ratio(r::RectangleB)=r.w/r.h</strong>`

`<strong>r, r1, r2 = RectangleB(1//2, 2//3), RectangleB(1.5, 0.5), RectangleB(1, 2)</strong>`

`<strong>julia&gt; area(r), area(r1), area(r2)<br>(1//3, 0.75, 2)</strong>`

`<strong>julia&gt; aspect_ratio(r), aspect_ratio(r1), aspect_ratio(r2)<br>(3//4, 3.0, 0.5)</strong>`

While `<strong>area</strong>` function returned values as `<strong>Rational{Int}</strong>` and `<strong>Int</strong>` depending on the parametric type of Rectangle the same seems to have been ignored in the function `<strong>aspect_ratio</strong>`. The operator (/) is explicitly a floating-point division operator. The rational or division operator in Julia is (//). Let us introduce two additional methods for `<strong>aspect_ratio</strong>` specifically for the integer and rational types.

`<strong>aspect_ratio(r::RectangleB{T}) where T&lt;:Union{Integer, Rational} = r.w//r.h<br><br>julia&gt; aspect_ratio(r), aspect_ratio(r1), aspect_ratio(r2)<br>(3//4, 3.0, 1//2)</strong>`

Clearly, the method for `<strong>Rational</strong>` and `<strong>Integer</strong>` types get dispatched to the new method while the rest of the numeric types like the Float64 get dispatched to the older method. `<strong>T&lt;:Union{Integer, Rational}</strong>` essentially means the type can be derived from either an Integer type or can be of a Rational type. Union is used extensively in Julia to represent where the types are of one of the types. One could instead use 3 methods instead of using a Union like the following examples as well.

`<strong>aspect_ratio(r::RectangleB{T}) where T&lt;:Integer = r.w//r.h</strong>`

`<strong>aspect_ratio(r::RectangleB{T}) where T&lt;:Rational = r.w//r.h</strong>`

It is important to understand the dispatch rules from the perspective of how the subtype relationship flows down into the parametric types.

`<strong>julia&gt; RectangleB{Rational{Int}} &lt;: RectangleB{Rational}<br>false<br>julia&gt; RectangleB{Rational{Int}} &lt;: RectangleB<br>true<br>julia&gt; RectangleB{Rational} &lt;: RectangleB<br>true</strong>`

The subtype relationship is only relevant up to the immediate parametric type. `<strong>RectangleB{Rational{Int}}</strong>` is not a subtype of `<strong>RectangleB{Rational}</strong>` while it is a subtype of `<strong>RectangleB</strong>`.

# 

Let us look at the some of the examples as follows:

`<strong>julia&gt; 1f0+2<br>3.0f0<br>julia&gt; 1f0+2.0<br>3.0</strong>`

We added a `<strong>Float32</strong>` to an `<strong>Int</strong>` and the result returned was a `<strong>Float32</strong>`. Similarly, we added `<strong>Float32</strong>` to `<strong>Float64</strong>` and got a `<strong>Float64</strong>` as a result. All these seemed very natural. It seemed `<strong>Int</strong>` got promoted to a `<strong>Float32</strong>` and then the addition was performed. Unlike other programming languages, the type promotions in Julia are not implicit. Any conversions of types need to be carried out explicitly. Julia core library internally has many such rules defined which are called explicitly so that we see these seamless transitions.

# 

The typical method of initializing any value is by a constructor. For example, you can convert an integral floating-point value like 1.0 to `<strong>Int</strong>` by specifying `<strong>Int(1.0)</strong>`. But, `<strong>Int(1.5)</strong>` will throw an `<strong>InexactError</strong>`. In most cases, this is to be carried out by an explicit call by the programmer. But, sometimes the conversion is to be carried out by an implicit call. In such a case a `<strong>convert(T, x)</strong>` is called.

`<strong>julia&gt; function f()<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; i::Int = 0<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; i = 1.5<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; return i<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; end<br>f (generic function with 1 method)</strong>`

`<strong>julia&gt; f()<br>ERROR: InexactError: Int64(1.5)<br>Stacktrace:<br>&nbsp;[1] Int64 at .\float.jl:710 [inlined]<br>&nbsp;[2] convert(::Type{Int64}, ::Float64) at .\number.jl:7<br>&nbsp;[3] f() at .\REPL[88]:3<br>&nbsp;[4] top-level scope at REPL[89]:1</strong>`

`<strong>i</strong>` is a variable defined to be of type `<strong>Int</strong>`. Now when a value of `<strong>1.5</strong>` is assigned to it, convert method is invoked which throws an `<strong>InexactError</strong>`. For numeric types the convert method invokes the `<strong>T(x)</strong>` or the constructor that in this case will be `<strong>Int64(1.5)</strong>`. A more elaborate case was shown in the preceding `<strong>RectangleB</strong>` example.

`<strong>julia&gt; RectangleB{Int}('a', 1.0)<br>RectangleB{Int64}(97, 1)</strong>`

In this case, the fact that the `<strong>RectangleB{Int}</strong>` is provided as the constructor, `<strong>convert(Int, ‘a’)</strong>` and `<strong>convert(Int, 1.0)</strong>` are implicitly invoked and `<strong>Char</strong>` and `<strong>Float64</strong>` are converted to `<strong>Int</strong>`.

``<strong>julia&gt; RectangleB{Int}("abc", 1.0)<br>ERROR: MethodError: Cannot `convert` an object of type String to an object of type Int64<br>Closest candidates are:<br>&nbsp;&nbsp;convert(::Type{T}, ::T) where T&lt;:Number at number.jl:6<br>&nbsp;&nbsp;convert(::Type{T}, ::Number) where T&lt;:Number at number.jl:7<br>&nbsp;&nbsp;convert(::Type{T}, ::Ptr) where T&lt;:Integer at pointer.jl:23</strong>``

Non-existence of convert method from `<strong>String</strong>` to `<strong>Int</strong>` is making the constructor fail.

# 

Let us look at the `<strong>RectangleP</strong>` type again.

`<strong>struct RectangleP{T &lt;: Real}<br>&nbsp;&nbsp;&nbsp;&nbsp;w::T<br>&nbsp;&nbsp;&nbsp;&nbsp;h::T<br>end</strong>`

When no constructor is specified, a default constructor is defined which looks as follows:

`<strong>struct RectangleP{T&lt;:Real}<br>&nbsp;&nbsp;&nbsp;&nbsp;w::T<br>&nbsp;&nbsp;&nbsp;&nbsp;h::T<br>&nbsp;&nbsp;&nbsp;&nbsp;RectangleP(w::T, h::T) where T&lt;:Real=new{T}(w, h)<br>end</strong>`

`<strong>julia&gt; RectangleP(1, 2.0)<br>ERROR: MethodError: no method matching Rectangle(::Int64, ::Float64)<br>Closest candidates are:<br>&nbsp;&nbsp;RectangleP(::T, ::T) where T&lt;:Real at REPL[96]:4</strong>`

`<strong>RectangleP(1, 2.0) is failing. Is there a way to address this?</strong>`

`<strong>function RectangleP(w::T1, h::T2) where {T1&lt;:Real, T2&lt;:Real}<br>&nbsp;&nbsp;&nbsp;&nbsp;w1, h1 = promote(w, h)<br>&nbsp;&nbsp;&nbsp;&nbsp;return RectangleP(w1, h1)<br>end<br><br>julia&gt; RectangleP(1, 2.0)<br>RectangleP{Float64}(1.0, 2.0)</strong>`

We defined an outer constructor that supports two parameters. The parameters can be derived from `<strong>Real</strong>` but different from each other. We call the `<strong>promote</strong>` `<strong></strong>`method on the parameters to obtain the promoted function arguments and subsequently create the `<strong>RectangleP</strong>` from the promoted arguments. It is understood here that in a promotion of `<strong>Int</strong>` and `<strong>Float64</strong>`, `<strong>Float64</strong>` will be the promoted type. This behavior will be clear in the following example. Suppose we were to find the minimum sized `<strong>RectangleP</strong>` that can fit inside each of the two `<strong>RectangleP</strong>` objects.

`<strong>julia&gt; function minrect(r1::RectangleP, r2::RectangleP)<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; w = r1.w &lt; r2.w ? r1.w : r2.w<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; h = r1.h &lt; r2.h ? r1.h : r2.h<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; return RectangleP(w, h)<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; end<br>minrect (generic function with 1 method)<br>julia&gt; minrect(RectangleP(1, 2), RectangleP(2.0, 0.5))<br>RectangleP{Float64}(1.0, 0.5)<br>julia&gt; minrect(RectangleP(1, 2), RectangleP(3.0, 4.0))<br>RectangleP{Int64}(1, 2)</strong>`

While the preceding code is not wrong you can notice an anomaly of the function returning a `<strong>RectangleP{Float64}</strong>` or `<strong>RectangleP{Int}</strong>` based on the input data. This is definitely not desirable from a type stability perspective. When `<strong>RectangleP{Float64}</strong>` and `<strong>RectangleP{Int}</strong>` come into interaction we can create a `<strong>Base.promote_rule</strong>` such that the right promotion happens.

`<strong>Base.promote_rule(::Type{RectangleP{T}}, ::Type{RectangleP{S}}) where {T&lt;:Real, S&lt;:Real} = RectangleP{promote_type(S, T)}<br><br>Base.convert(::Type{RectangleP{T}}, x::RectangleP{S}) where {T&lt;:Real, S&lt;:Real} = S === T ? x : RectangleP(T(x.w), T(x.h))</strong>`

`<strong>function minrect(tr1::RectangleP, tr2::RectangleP)<br>&nbsp;&nbsp;&nbsp;&nbsp;r1, r2 = promote(tr1, tr2)<br>&nbsp;&nbsp;&nbsp;&nbsp;w = r1.w &lt; r2.w ? r1.w : r2.w<br>&nbsp;&nbsp;&nbsp;&nbsp;h = r1.h &lt; r2.h ? r1.h : r2.h<br>&nbsp;&nbsp;&nbsp;&nbsp;return RectangleP(w, h)<br>end</strong>`

`<strong>julia&gt; minrect(RectangleP(1, 2), RectangleP(3.0, 4.0))<br>RectangleP{Float64}(1.0, 2.0)</strong>`

To be consistent we have to make sure the promotion happens to a consistent type. As `<strong>Float64</strong>` vs `<strong>Int64</strong>` promotion will happen to `<strong>Float64</strong>`, we will like to ensure between `<strong>RectangleP{Float64}</strong>` and `<strong>RectangleP{Int}</strong>` promotion happens to `<strong>RectangleP{Float64}</strong>`. Second, we create a convert method to convert from `<strong>RectangleP{S}</strong>` to `<strong>RectangleP{T}</strong>`. When promote is invoked in `<strong>minrect</strong>`, the `<strong>promote_rule</strong>` and convert methods are invoked internally. And the data is converted to `<strong>RectangleP{Float64}</strong>`. Hence, the final return type will be `<strong>RectangleP{Float64}</strong>`.

# 

Functions are central to Julia. With type variations and dispatch architecture, Julia gets the utmost power from functions and methods. We looked at various use cases of the functions and methods as well as discussed on complexities that arise out of parametric data types. In the next chapter, we shall look at collections and get to understand how to iterate through them and extract and store data in them.

# 

1.  In the 8-Queens puzzle, we get only one solution to the puzzle. Are there other solutions possible? Extend the code to find all possible solutions.
2.  As you increase the board size the time taken to solve the N-queens puzzle would increase. The author in his set up finds the wait time for solving for board size of 30 extremely high. What is it for you? How will make the program efficient to reduce that limit?
3.  With Julia not supporting terminal call optimizations the possibility of stack overflow can be significant. How do you think you can overcome stack overflow?
4.  Julia constructors behave differently when the parametric types are explicitly specified. Why is that so?
5.  What are the differences between inner and outer constructors? Are outer constructors essential?

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

[1](#zhs8j9hj.html#n4upl4fndj4) Julia has an elaborate set of operators and symbols that can be part of the Unicode set. With inline operators, you can write expressions like mathematical equations. We will keep a simplistic view that operators are functions in Julia. However, readers are requested to look into the Julia documentation (**[https://docs.julialang.org/en/v1/manual/mathematical-operations/](https://docs.julialang.org/en/v1/manual/mathematical-operations/)**) for a detailed understanding of the precedence and associativity of the operators.

:x is of type Symbol. Symbols are special purpose types in Julia used to create custom keywords. We shall review them in Chapter-8 Metaprogramming.

[3](#zhs8j9hj.html#n4upl4fndj5) Julia Github Issue 4964 (**[https://github.com/JuliaLang/julia/issues/4964](https://github.com/JuliaLang/julia/issues/4964)**)

[4](#zhs8j9hj.html#n4upl4fndj6) Wikipedia article on Multiple Dispatch (`<strong><a href="https://en.wikipedia.org/wiki/Multiple_dispatch">https://en.wikipedia.org/wiki/Multiple_dispatch</a></strong>`)

1//5 is a representation of a fraction in Julia.

# 4

Hence, the function call can be replaced with a jump instruction. Some functional programming languages like *Lisp* or *Lua* identify such conditions programmatically and eliminate the stack frame creation. This process is called `<strong>Tail Call Optimization</strong>` (`<strong>TCO</strong>`). In functional programming, recursion is given higher importance over iterative programming. Stack frame creation consumes memory. Hence, deep recursive function calls can lead to stack overflow. Unlike Lisp, Julia does not have native support for TCO3.

# 1

Julia has an elaborate set of operators and symbols that can be part of the Unicode set. With inline operators, you can write expressions like mathematical equations. We will keep a simplistic view that operators are functions in Julia. However, readers are requested to look into the Julia documentation (**[https://docs.julialang.org/en/v1/manual/mathematical-operations/](https://docs.julialang.org/en/v1/manual/mathematical-operations/)**) for a detailed understanding of the precedence and associativity of the operators.

Julia Github Issue 4964 (**[https://github.com/JuliaLang/julia/issues/4964](https://github.com/JuliaLang/julia/issues/4964)**)

Wikipedia article on Multiple Dispatch (`<strong><a href="https://en.wikipedia.org/wiki/Multiple_dispatch">https://en.wikipedia.org/wiki/Multiple_dispatch</a></strong>`)

# 

# 

# 

Every programming language provides a certain minimal set of data structures to represent a plurality of data elements as containers; namely arrays, dictionaries, sets and lists, and so on. The collections that Julia provides are the subject matter of discussion for this chapter.

# 

In this chapter, we will cover the following topics:

*   Predefined data structures
*   Tuple
*   Ranges
*   Array
*   Associative collection
*   Iteration
*   Iteration framework
*   Generators and comprehensions

# 

In this chapter, the reader shall be able to learn arrays, tuples, dictionaries, and sets. The collections provide the basis of solutions for some of the algorithms. They implement an iterator framework that can help iterate over individual elements of the collection. Generators and comprehensions provide on-demand collection-like interfaces that can be used for iterations as well.

# 

In 1975, *Niklaus Wirth*, a well-known computer exponent and author of the programming language PASCAL wrote a book *Algorithms + Data Structures = Programs*[1](#xjo4a1bi.html#n4upl4fndnn); clearly highlighting the importance of data structures and algorithms in programming. There is hardly any modern programming language that does not provide in-built support for data structures. Julia is no exception either. Many data structures are defined in the core Julia language and a wide range of data structures are defined in packages like `<strong>DataStrctures.jl</strong>`. In this chapter, our focus will be the data structures defined in the language without the need to use any additional packages. To name a few:

1.  Tuples
2.  Arrays
3.  Dictionaries
4.  Sets

While these are a few prominent ones defined inside Julia’s core language, there are many minor ones used for specialized applications. We probably cannot talk about all of them in one chapter but will keep discussing them off and on in various contexts if needed.

# 

Tuples are so common in Julia that many a times we tend to ignore them as a specialized data structure. In , we had seen a few of the properties of a Tuple. Here is a summary of its functions:

1.  Immutable
2.  Heterogeneous
3.  Can be used in pattern matching
4.  The elements can be accessed as an index

Here are some of the examples:

`<strong>julia&gt; a = (1, "string", 1.0)<br>(1, "string", 1.0)<br>julia&gt; typeof(a)&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; # Heterogeneous<br>Tuple{Int64,String,Float64}<br>julia&gt; a[1]&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;# Accessed as Index<br>1<br>julia&gt; a[1] = 6&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;# Immutable<br>ERROR: MethodError: no method matching setindex!(::Tuple{Int64,String,Float64}, ::Int64, ::Int64)<br>Stacktrace:<br>&nbsp;[1] top-level scope at REPL[29]:1<br>julia&gt; b, c = a&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;# Pattern Matching<br>(1, "string", 1.0)<br>julia&gt; b<br>1<br>julia&gt; c<br>"string"</strong>`

We also saw some of its usage of Tuple type in the variable argument functions.

# 

`<strong>NTuple{N, T}</strong>` is a parametric definition of a `<strong>Tuple</strong>` that has `<strong>N</strong>` elements of type `<strong>T</strong>`.

`<strong>julia&gt;&nbsp;&nbsp;NTuple{3, Int}<br>Tuple{Int64,Int64,Int64}</strong>`

You can create a method that takes a tuple argument like this:

`<strong>f(::NTuple{3, Int}) instead of f(::Tuple{Int64,Int64,Int64}).</strong>`

When you want to create a `<strong>Tuple</strong>` of `<strong>N</strong>` parameters of a specific pattern, you could use the function `<strong>ntuple</strong>`.

`<strong>julia&gt; a = ntuple(x-&gt;4, 10)<br>(4, 4, 4, 4, 4, 4, 4, 4, 4, 4)<br>julia&gt; typeof(a)<br>NTuple{10,Int64}</strong>`

`<strong>julia&gt; a = ntuple(i-&gt;i*1.0, 10)<br>(1.0, 2.0, 3.0, 4.0, 5.0, 6.0, 7.0, 8.0, 9.0, 10.0)<br>julia&gt; typeof(a)<br>NTuple{10,Float64}</strong>`

# 

`<strong>Tuple</strong>` can be used as a collection of items. This means they can be iterated upon and will have typical functions that collections will have like `<strong>length</strong>`.

`<strong>julia&gt; length(a)<br>10<br>julia&gt; for i=1:length(a)<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; println(a[i])<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; end<br>1.0<br>2.0<br>3.0<br>4.0<br>5.0<br>6.0<br>7.0<br>8.0<br>9.0<br>10.0</strong>`

# 

One pertinent observation in the type `<strong>NTuple</strong>` is, it has a parameter of Integer type. The same is applicable to any mutable or immutable types as well. Let us create a `<strong>Point</strong>` type that can be used for 2 or 3 dimensions.

`<strong>struct Point{N}<br>&nbsp;&nbsp;&nbsp;&nbsp;data::NTuple{N, Float32}<br>&nbsp;&nbsp;&nbsp;&nbsp;Point(d…)=new{length(d)}(d)<br>end</strong>`

`<strong>const Point2D=Point{2}<br>const Point3D=Point{3}<br><br>function dist(p1::Point2D, p2::Point2D)<br>&nbsp;&nbsp;&nbsp;&nbsp;dx, dy = (p1.data[1] - p2.data[1], p1.data[2] - p2.data[2])<br>&nbsp;&nbsp;&nbsp;&nbsp;return sqrt(dx*dx+dy*dy)<br>end</strong>`

`<strong>function dist(p1::Point3D, p2::Point3D)<br>&nbsp;&nbsp;&nbsp;&nbsp;dx, dy, dz = (p1.data[1] - p2.data[1],<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;p1.data[2] - p2.data[2],<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;p1.data[3] - p2.data[3])<br>&nbsp;&nbsp;&nbsp;&nbsp;return sqrt(dx*dx+dy*dy+dz*dz)<br>end</strong>`

`<strong>julia&gt; dist(Point(1, 2), Point(3, 4))<br>2.828427f0<br>julia&gt; dist(Point(1, 2, 3), Point(3, 4, 5))<br>3.4641016f0</strong>`

The preceding example, we could define a `<strong>Point2D</strong>` and `<strong>Point3D</strong>` as an alias on `<strong>Point{N}</strong>`. We defined two `<strong>dist</strong>` functions for both the types and ensured the dispatch is available based on the integer value of 2 or 3. `<strong>Point{2}</strong>` and `<strong>Point{3}</strong>` are two distinct types. With the `<strong>NTuple</strong>` as a collection type, let us try to have a `<strong>dist</strong>` method that works well for `<strong>Point{N}</strong>`.

`<strong>function dist(p1::Point{N}, p2::Point{N}) where N<br>&nbsp;&nbsp;&nbsp;&nbsp;sumval = 0f0<br>&nbsp;&nbsp;&nbsp;&nbsp;<a id="page82"></a>for i=1:N<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;d = p1.data[i] - p2.data[i]<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;sumval += d*d<br>&nbsp;&nbsp;&nbsp;&nbsp;end<br>&nbsp;&nbsp;&nbsp;&nbsp;return sqrt(sumval)<br>end</strong>`

`<strong>julia&gt; dist(Point(1, 2), Point(3, 4))<br>2.828427f0<br>julia&gt; dist(Point(1, 2, 3), Point(3, 4, 5))<br>3.4641016f0</strong>`

Would it have been wrong if we had used `<strong>Point</strong>` without the parametric form `<strong>Point{N}? Point{2}</strong>` and `<strong>Point{3}</strong>` are two different types. So the `<strong>dist</strong>` function would have been compiled for two different types. We could have created a single `<strong>dist</strong>` function.

`<strong>function dist(p1::Point, p2::Point)<br>&nbsp;&nbsp;&nbsp;&nbsp;N = length(p1.data)<br>&nbsp;&nbsp;&nbsp;&nbsp;sumval = 0f0<br>&nbsp;&nbsp;&nbsp;&nbsp;for i=1:N<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;d = p1.data[i] - p2.data[i]<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;sumval += d*d<br>&nbsp;&nbsp;&nbsp;&nbsp;end<br>&nbsp;&nbsp;&nbsp;&nbsp;return sqrt(sumval)<br>end</strong>`

`<strong>julia&gt; dist(Point(1, 2), Point(3, 4))<br>2.828427f0<br>julia&gt; dist(Point(1f0, 2f0, 3f0), Point(1, 2))<br>ERROR: BoundsError: attempt to access (1.0f0, 2.0f0) at index [3]<br>Stacktrace:<br>…</strong>`

We can now pass parameters of a `<strong>Point{2}</strong>` and `<strong>Point{3}</strong>` to the same function. Only one method is created. There are no two methods to be compiled for `<strong>Point{2}</strong>` and `<strong>Point{3}</strong>` versions. What is the correct approach? Unfortunately, this is a design decision and not a programming language concept. Do you think `<strong>Point2D</strong>` and `<strong>Point3D</strong>` are interoperable and we should support an interoperable `<strong>dist</strong>` method for `<strong>Point{N1}</strong>` and `<strong>Point{N2}</strong>`? Here is one possible implementation.

`<strong>function dist(p1::Point{N}, p2::Point{N}) where N<br>&nbsp;&nbsp;&nbsp;&nbsp;sumval = 0f0<br>&nbsp;&nbsp;&nbsp;&nbsp;for i=1:N<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;d = p1.data[i] - p2.data[i]<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;sumval += d*d<br>&nbsp;&nbsp;&nbsp;&nbsp;end<br>&nbsp;&nbsp;&nbsp;&nbsp;return sqrt(sumval)<br>end</strong>`

`<strong>function dist(p1::Point{N1}, p2::Point{N2}) where {N1, N2}<br>&nbsp;&nbsp;&nbsp;&nbsp;N1 &gt; N2 &amp;&amp; return dist(p2, p1)<br>&nbsp;&nbsp;&nbsp;&nbsp;tp = Point(p1.data…, ntuple(i-&gt;0f0, N2-N1)…)<br>&nbsp;&nbsp;&nbsp;&nbsp;return dist(tp, p2)<br>end</strong>`

*   We created a method for the `<strong>Point{N}</strong>` with same dimension `<strong>N</strong>`.
*   Then we created a method where `<strong>Point</strong>` of different dimensions can be inputs.
*   Here, we assumed dimension of the first argument will be less than the second.
*   If that is not true we call the method by flipping the arguments. Thus ensuring the first parameter has a lesser dimension than the second (N1 < N2).
*   We create a `<strong>temporary point</strong>` (`<strong>tp</strong>`) with the same dimension as `<strong>p2</strong>` by filling zeros for the higher dimensions and call the `<strong>dist(tp, p2)</strong>`.

# 

Let us look at the following control flow of the code:

`<strong>if val == 1<br>&nbsp;&nbsp; f1()<br>elseif val == 2<br>&nbsp;&nbsp; f2()<br>elseif val == 3<br>&nbsp;&nbsp; f3()<br>else<br>&nbsp;&nbsp; f4()<br>end</strong>`

Can these functions use multiple-dispatch instead of using `<strong>if…elseif…else</strong>`?

`<strong>struct MyVal{N}<br>&nbsp;&nbsp;&nbsp;&nbsp;MyVal(N)=new{N}()<br>end</strong>`

`<strong>f(::MyVal{N}) where N = N</strong>`

`<strong>function f(::MyVal{1})<br>&nbsp;&nbsp;&nbsp;&nbsp;println(“Called from 1”)<br>end</strong>`

`<strong>julia&gt; f(MyVal(2))<br>2<br>julia&gt; f(MyVal(1))<br>Called from 1</strong>`

*   `<strong>MyVal{N}</strong>` defines types based on value of `<strong>N</strong>`.
*   Method `<strong>f</strong>` works for all value of `<strong>MyVal{N}</strong>`.
*   A specialized method `<strong>f</strong>` was defined only for `<strong>MyVal{1}</strong>`.
*   Now `<strong>f(MyVal(2))</strong>` invoked the generic method and `<strong>f(MyVal(1))</strong>` invoked the specific method.

# 

When a type has no attribute in it, only one object is created for it. Such objects are called `<strong>singletons</strong>`. The value type created is also a singleton as the type has no attributes.

`<strong>julia&gt; MyVal(1) === MyVal(1)<br>true<br>julia&gt; MyVal(1) === MyVal(2)<br>false</strong>`

`<strong>MyVal{1}</strong>` is a different type from `<strong>MyVal{2}</strong>`. Hence, the objects created as a part of the initializations are two different objects. Value parameters though are possible in Julia, it may not be the most optimally performing method. Julia natively provides a type `<strong>Val{N}</strong>` that is inline of the principles as suggested. We will discuss further on this in the chapter for performance management in Julia.

**Note**: Not just **Integer** types, even a **Symbol** can be used as a value type parameter as well.

`<strong>julia&gt; MyVal(:a)<br>MyVal{:a}()</strong>`

# 

Sometimes we require contiguous numbers or numbers with fixed step sizes both increasing and reducing in values. These are called as **ranges**. Here are some examples:

# 

`<strong>julia&gt; a=1:5<br>1:5<br>julia&gt; typeof(a)<br>UnitRange{Int64}</strong>`

`<strong>a</strong>` is a `<strong>UnitRange</strong>` that means it has all the numbers from 1 to 5. The step of increment in `<strong>UnitRange</strong>` is always 1.

`<strong>julia&gt; for i=a<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; println(i)<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; end<br>1<br>2<br>3<br>4<br>5</strong>`

# 

`<strong>julia&gt; b=1:2:5<br>1:2:5<br>julia&gt; typeof(b)<br>StepRange{Int64,Int64}<br>julia&gt; for i=b<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; println(i)<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; end<br>1<br>3<br>5</strong>`

`<strong>b</strong>` is a `<strong>StepRange</strong>` with numbers in intervals of 2.

# 

`<strong>julia&gt; c=5:-1:1<br>5:-1:1<br>julia&gt; typeof(c)<br>StepRange{Int64,Int64}<br>julia&gt; for i=c<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; println(i)<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; end<br>5<br>4<br>3<br>2<br>1</strong>`

`<strong>c</strong>` is a `<strong>StepRange</strong>` with a negative step of −1. So when iterated we print from 5 to 1 in decreasing order.

Ranges are used for iterations, indices, and initializing collections. They can have more complex parameters and also can have floating points for the initial value, steps, and final values. We will review the involved range objects in a later chapter. Here is just an example of a range with floating-point values.

`<strong>julia&gt; d=1:2.1:6.0<br>1.0:2.1:5.2<br>julia&gt; typeof(d)<br>StepRangeLen{Float64,Base.TwicePrecision{Float64},Base.TwicePrecision{Float64}}</strong>`

# 

Arrays can be thought of as contiguous memory locations of a specific type that hold objects as a container. They can be accessed through indices and iterated. Unlike a `<strong>Tuple</strong>`, arrays are mutable. Elements in arrays can be appended, removed, or modified. Even other data structures like queues and stacks can be implemented keeping arrays as containers. In this section, we will introduce the basics of arrays while the details shall be explained in a dedicated chapter on the arrays.

Arrays are represented as `<strong>Array{T, N}</strong>`, where `<strong>T</strong>` is type and `<strong>N</strong>` is number of dimensions. The `<strong>Array{T, 1}</strong>` or one-dimension array is aliased as `<strong>Vector</strong>` and `<strong>Array{T, 2}</strong>` as `<strong>Matrix</strong>`. Both these have special meanings in the scientific computations.

`<strong>julia&gt; v = [1, 2, 3]<br>3-element Vector{Int64}:<br>&nbsp;1<br>&nbsp;2<br>&nbsp;3</strong>`

`<strong>julia&gt; m = [1 2 3]<br>1×3 Matrix{Int64}:<br>&nbsp;1&nbsp;&nbsp;2&nbsp;&nbsp;3</strong>`

`<strong>v</strong>` is a `<strong>Vector{Int64}</strong>` or an `<strong>Array{Int64,1}</strong>`. Similarly, `<strong>m</strong>` is a `<strong>Matrix{Int64}</strong>` or an `<strong>Array{Int64, 2}</strong>`. A multi-dimensional array can be constructed by a combination of symbols comma (,) and semicolon (;) inside a pair of square brackets ([]).

`<strong>julia&gt; m1 = [1 2 3; 4 5 6]<br>2×3 Matrix{Int64}:<br>&nbsp;1&nbsp;&nbsp;2&nbsp;&nbsp;3<br>&nbsp;4&nbsp;&nbsp;5&nbsp;&nbsp;6<br>julia&gt; m2 = [1 2; 3 4; 5 6]<br>3×2 Matrix{Int64}:<br>&nbsp;1&nbsp;&nbsp;2<br>&nbsp;3&nbsp;&nbsp;4<br>&nbsp;5&nbsp;&nbsp;6</strong>`

As can be seen semicolon (;) acts as a row separator in the definition.

# 

The array members can be accessed through indices. Here are some examples using the preceding defined matrices `<strong>m1</strong>` and `<strong>m2</strong>`:

`<strong>julia&gt; m1[1, 2]<br>2<br>julia&gt; m1[2, 2]<br>5<br>julia&gt; m2[1, 2]<br>2<br>julia&gt; m2[2, 2]<br>4</strong>`

Thus, the array members are accessed as:

`<strong>array[row_index, column_index].</strong>`

The data in an array is stored as a contiguous block of memory assigned to a location. The index points to the specific location of the array based on the index values. The following image shows the memory layout for both `<strong>m1</strong>` and `<strong>m2</strong>`:

![](n4upl4fndrj.jpeg)

**Figure 5.1:** Memory layout of m1 and m2

Unlike C/C++ where data would have been stored as 1, 2, 3, 4, 5, and 6, in both cases the order in Julia looks substantially different. Julia stores data in the row major ordering as in the case of FORTRAN. This essentially means the data will be stored as if all the elements in the rows are kept next to each other and then the next column. This can be a bit confusing for programmers who are used to programming in C/C++ or Python. Second, indices in Julia begin from 1 instead of 0 as in the case of FORTRAN. Being a language for scientific computation and FORTRAN still being popular in the community, this choice is not entirely out of place.

# 

While for small array sizes it may not be relevant, for large to very large array sizes where memory paging can be significant, running inner loops on rows and outer loops on columns may be beneficial. In a multi-dimensional array, the dimension to the right must constitute the outer loop and dimensions to the left must be specified as the inner loop. The recommended pseudo code is given as follows:

`<strong>for col=1:100000<br>&nbsp;&nbsp;&nbsp;&nbsp;for row=1:1000<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;do_something(m[row, col])<br>&nbsp;&nbsp;&nbsp;&nbsp;end<br>end</strong>`

# 

# 

Here are some sample constructors:

`<strong>julia&gt; Array{Int}(undef, 1, 2)<br>1×2 Matrix{Int64}:<br>&nbsp;2728944785&nbsp;&nbsp;4294967297<br>julia&gt; Array{Int}(undef, 2)<br>2-element Vector{Int64}:<br>&nbsp;1<br>&nbsp;1<br>julia&gt; Array{Int, 2}(undef, (2, 3))<br>2×3 Matrix{Int64}:<br>&nbsp;150&nbsp;&nbsp;377672960&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 41<br>&nbsp;41&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;152&nbsp;&nbsp;377672961<br>julia&gt; Array{Float32}(undef, (2, 3))<br>2×3 Matrix{Float32}:<br>&nbsp;1.55068f-25&nbsp;&nbsp;1.55069f-25&nbsp;&nbsp;1.09216f-24<br>&nbsp;0.0&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;0.0&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;0.0</strong>`

`<strong>undef</strong>` is a special type of object that is used to define arrays containing undefined values. Julia objects are generally initialized while instantiating them. The array being a container type, sometimes there is a need to define them when the internal values are not known. The generic constructor is of type `<strong>Array{T,N}(undef, dims)</strong>` where `<strong>dims</strong>` is a Tuple of size N or a vararg parameter with N values. Specifying the N in the template parameters is optional. One can call the functions as `<strong>Array{T}(undef, dims)</strong>` as well.

For an `<strong>Array{T,N}</strong>` when T is of an `<strong>isbits</strong>` type, the Array is allocated completely with uninitialized bit patterns. So values printed are not predictable. For example:

`<strong>julia&gt; struct A<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; i::Int<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; f::Float64<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; end<br>julia&gt; a = A(1, 1); isbits(a)<br>true<br>julia&gt; aarr = Array{A}(undef, (2, 2))<br>2×2 Matrix{A}:<br>&nbsp;A(164260512, 8.08607e-316)&nbsp;&nbsp;A(163663952, 1.81629e-315)<br>&nbsp;A(164260512, 8.08607e-316)&nbsp;&nbsp;A(163679936, 1.84617e-315)</strong>`

Now let us look at the following scenario of an array of non-bits type:

`<strong>julia&gt; struct T<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; a::A<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; b<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; end<br>julia&gt; b = T(A(1, 1), 1); isbits(b)<br>false<br>julia&gt; barr = Array{T}(undef, (2, 2))<br>2×2 Matrix{T}:<br>&nbsp;#undef&nbsp;&nbsp;#undef<br>&nbsp;#undef&nbsp;&nbsp;#undef</strong>`

When `<strong>isbits</strong>` is `<strong>false</strong>`, while the `<strong>Array</strong>` allocated has the container allocated, the actual objects are not initialized. The actual objects need to be assigned for a proper initialization of the array.

`<strong>julia&gt; barr[1,1] = barr[2,1] = barr[1,2] = barr[2,2] = b<br>T(A(1, 1.0), 1)<br>julia&gt; barr<br>2×2 Matrix{T}:<br>&nbsp;T(A(1, 1.0), 1)&nbsp;&nbsp;T(A(1, 1.0), 1)<br>&nbsp;T(A(1, 1.0), 1)&nbsp;&nbsp;T(A(1, 1.0), 1)</strong>`

You can also realize the mutable nature of arrays and the elements can be assigned after the array has been initialized with `<strong>undef</strong>` values.

Just like generic `<strong>Array{T,N}</strong>` of N dimensions, `<strong>Vector{T}</strong>`, and `<strong>Matrix{T}</strong>` can have similar constructors as well.

`<strong>julia&gt; Vector{Int}(undef, 3)<br>3-element Vector{Int64}<a id="ftn2a" href="#ftn2"><sup>2</sup></a>:<br>&nbsp;230300096<br>&nbsp;397935296<br>&nbsp;336143200<br>julia&gt; Matrix{Int}(undef, 3, 3)<br>3×3 Matrix{Int64}:<br>&nbsp;163998752&nbsp;&nbsp;163998752&nbsp;&nbsp;163998752<br>&nbsp;163998752&nbsp;&nbsp;163998752&nbsp;&nbsp;163998752<br>&nbsp;163998752&nbsp;&nbsp;163998752&nbsp;&nbsp;163998752</strong>`

While constructors are one way to initialize Array, there are other convenience methods as well that we will review next.

# 

`<strong>julia&gt; zeros(Float32, (2, 3))<br>2×3 Matrix{Float32}:<br>&nbsp;0.0&nbsp;&nbsp;0.0&nbsp;&nbsp;0.0<br>&nbsp;0.0&nbsp;&nbsp;0.0&nbsp;&nbsp;0.0<br>julia&gt; ones(Float32, (2, 3))<br>2×3 Matrix{Float32}:<br>&nbsp;1.0&nbsp;&nbsp;1.0&nbsp;&nbsp;1.0<br>&nbsp;1.0&nbsp;&nbsp;1.0&nbsp;&nbsp;1.0<br>julia&gt; ones(UInt8, (2, 3))<br>2×3 Matrix{UInt8}:<br>&nbsp;0x01&nbsp;&nbsp;0x01&nbsp;&nbsp;0x01<br>&nbsp;0x01&nbsp;&nbsp;0x01&nbsp;&nbsp;0x01</strong>`

Given the type and the dimensions, the function creates an `<strong>Array</strong>` filled with zeros or ones in the type specified.

# 

Let us look at the two pieces of following code:

`<strong>julia&gt; zb = zeros(Bool, (8, 8))<br>8×8 Matrix{Bool}:<br>&nbsp;0&nbsp;&nbsp;0&nbsp;&nbsp;0&nbsp;&nbsp;0&nbsp;&nbsp;0&nbsp;&nbsp;0&nbsp;&nbsp;0&nbsp;&nbsp;0<br>&nbsp;…<br>&nbsp;0&nbsp;&nbsp;0&nbsp;&nbsp;0&nbsp;&nbsp;0&nbsp;&nbsp;0&nbsp;&nbsp;0&nbsp;&nbsp;0&nbsp;&nbsp;0<br>julia&gt; sizeof(zb)<br>64<br>As can be seen a Bool&gt; variable takes a byte of storage and this array requires 64 bytes of data.</strong>`

`<strong>julia&gt; z = falses(8, 8)<br>8×8 BitMatrix:<br>&nbsp;0&nbsp;&nbsp;0&nbsp;&nbsp;0&nbsp;&nbsp;0&nbsp;&nbsp;0&nbsp;&nbsp;0&nbsp;&nbsp;0&nbsp;&nbsp;0<br>&nbsp;…<br>&nbsp;0&nbsp;&nbsp;0&nbsp;&nbsp;0&nbsp;&nbsp;0&nbsp;&nbsp;0&nbsp;&nbsp;0&nbsp;&nbsp;0&nbsp;&nbsp;0<br>julia&gt; sizeof(z)<br>8</strong>`

The size of the `<strong>z</strong>` is only 8 bytes (64-bits), as all the entries are elements are represented with a single bit. Instead of an `<strong>Array</strong>`, a `<strong>BitArray</strong>` is created though. `<strong>BitArray</strong>` is an efficient storage of array when the elements are Boolean values as one bit is used to store a bit of information than a byte. Similar to falses, trues(dims) initializes `<strong>BitArrays</strong>` with true bit values.

# 

`<strong>fill(val, dims)</strong>` creates an array of `<strong>val</strong>` values. The type of the Array depends on the type of the `<strong>val</strong>` value.

`<strong>julia&gt; a = fill(5.0, (2, 2))<br>2×2 Matrix{Float64}:<br>&nbsp;5.0&nbsp;&nbsp;5.0<br>&nbsp;5.0&nbsp;&nbsp;5.0</strong>`

`<strong>julia&gt; a = fill(5, (2, 2))<br>2×2 Matrix{Int64}:<br>&nbsp;5&nbsp;&nbsp;5<br>&nbsp;5&nbsp;&nbsp;5</strong>`

`<strong>similar(a, elem_type, dims)</strong>` creates an uninitialized Array of `<strong>elem_type</strong>` by using the default type of array elements of a and/or dims dimensions.

`<strong>julia&gt; b = similar(a, Int)<br>2×2 Matrix{Int64}:<br>&nbsp;665953152&nbsp;&nbsp;665953936<br>&nbsp;665953600&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;0</strong>`

# 

`<strong>collect(elem_type, collection)</strong>` is a utility method that creates an `<strong>Array</strong>` from all the data in a collection.

`<strong>julia&gt; collect(1:3)<br>3-element Vector{Int64}:<br>&nbsp;1<br>&nbsp;2<br>&nbsp;3<br>julia&gt; collect(Float64, 1:2:3)<br>2-element Vector{Float64}:<br>&nbsp;1.0<br>&nbsp;3.0</strong>`

# 

Arrays are allocated as a linear contiguous memory and the indices are an overlay on top of them in a row-major format. reshape is a convenient method to achieve the same.

`<strong>julia&gt; a = collect(1:16)<br>16-element Vector{Int64}:<br>&nbsp;1<br>&nbsp;2<br>&nbsp;3<br>&nbsp;…<br>&nbsp;16<br>julia&gt; b = reshape(a, (4, 4))<br>4×4 Matrix{Int64}:<br>&nbsp;1&nbsp;&nbsp;5&nbsp;&nbsp; 9&nbsp;&nbsp;13<br>&nbsp;2&nbsp;&nbsp;6&nbsp;&nbsp;10&nbsp;&nbsp;14<br>&nbsp;3&nbsp;&nbsp;7&nbsp;&nbsp;11&nbsp;&nbsp;15<br>&nbsp;4&nbsp;&nbsp;8&nbsp;&nbsp;12&nbsp;&nbsp;16<br>julia&gt; c = reshape(b, (2, 8))<br>2×8 Matrix{Int64}:<br>&nbsp;1&nbsp;&nbsp;3&nbsp;&nbsp;5&nbsp;&nbsp;7&nbsp;&nbsp; 9&nbsp;&nbsp;11&nbsp;&nbsp;13&nbsp;&nbsp;15<br>&nbsp;2&nbsp;&nbsp;4&nbsp;&nbsp;6&nbsp;&nbsp;8&nbsp;&nbsp;10&nbsp;&nbsp;12&nbsp;&nbsp;14&nbsp;&nbsp;16</strong>`

`<strong>julia&gt; d = reshape(c, (8, 2))<br>8×2 Matrix{Int64}:<br>&nbsp;1&nbsp;&nbsp; 9<br>&nbsp;2&nbsp;&nbsp;10<br>&nbsp;3&nbsp;&nbsp;11<br>&nbsp;4&nbsp;&nbsp;12<br>&nbsp;5&nbsp;&nbsp;13<br>&nbsp;6&nbsp;&nbsp;14<br>&nbsp;7&nbsp;&nbsp;15<br>&nbsp;8&nbsp;&nbsp;16</strong>`

While the shape of the array changes the row-major ordering of the data still maintains the sequence.

# 

These methods create a new `<strong>Array</strong>` object combining the input arrays. `<strong>vcat</strong>` creates an `<strong>Array</strong>` where the input arrays are placed along the dimension 1. On a set of matrices, the effect may seem like the arrays are placed one below the other.

`<strong>julia&gt; vcat([1 2; 3 4], [5 6; 7 8], [9 10; 11 12])<br>6×2 Matrix{Int64}:<br>&nbsp;&nbsp;1&nbsp;&nbsp; 2<br>&nbsp;&nbsp;3&nbsp;&nbsp; 4<br>&nbsp;&nbsp;5&nbsp;&nbsp; 6<br>&nbsp;&nbsp;7&nbsp;&nbsp; 8<br>&nbsp;&nbsp;9&nbsp;&nbsp;10<br>&nbsp;11&nbsp;&nbsp;12</strong>`

`<strong>hcat</strong>` creates an `<strong>Array</strong>` where the input arrays are placed along the dimension 2. On a set of matrices, the effect may seem like the arrays are placed one to the right to the other.

`<strong>julia&gt; hcat([1 2; 3 4], [5 6; 7 8], [9 10; 11 12])<br>2×6 Array{Int64,2}:<br>&nbsp;1&nbsp;&nbsp;2&nbsp;&nbsp;5&nbsp;&nbsp;6&nbsp;&nbsp; 9&nbsp;&nbsp;10<br>&nbsp;3&nbsp;&nbsp;4&nbsp;&nbsp;7&nbsp;&nbsp;8&nbsp;&nbsp;11&nbsp;&nbsp;12</strong>`

`<strong>hvcat(rows::Tuple{Int}, arrays…)</strong>` forms rows by using the `<strong>rows</strong>` tuples data given in the first argument and the rows thus formed are stacked one over the other to form the final array.

`<strong>julia&gt; hvcat((2, 2, 2), [1, 2], [3, 4], [5, 6], [7, 8], [9, 10], [11, 12])<br>6×2 Matrix{Int64}:<br>&nbsp;&nbsp;1&nbsp;&nbsp; 3<br>&nbsp;&nbsp;2&nbsp;&nbsp; 4<br>&nbsp;&nbsp;5&nbsp;&nbsp; 7<br>&nbsp;&nbsp;6&nbsp;&nbsp; 8<br>&nbsp;&nbsp;9&nbsp;&nbsp;11<br>&nbsp;10&nbsp;&nbsp;12</strong>`

In the preceding example, the vectors are placed side-by-side in groups of 2. Thus, 3 intermittent matrices are created. They are:

![](n4upl4fndrk.jpeg)

Now, stacking them one over the other one gets the desired output.

`<strong>julia&gt; hvcat(6, [1, 2], [3, 4], [5, 6], [7, 8], [9, 10], [11, 12])<br>2×6 Matrix{Int64}:<br>&nbsp;1&nbsp;&nbsp;3&nbsp;&nbsp;5&nbsp;&nbsp;7&nbsp;&nbsp; 9&nbsp;&nbsp;11<br>&nbsp;2&nbsp;&nbsp;4&nbsp;&nbsp;6&nbsp;&nbsp;8&nbsp;&nbsp;10&nbsp;&nbsp;12</strong>`

Similarly, in the preceding example, 6 vectors shall be placed next to each other to form a Matrix.

# 

In an associative collection, the elements of a collection are stored as a key and value pair. The values can be accessed through an indexed key or an efficient search over the keys. Some of the well-known collections are dictionaries, multi-dictionaries, sets (although sets only keep the keys and values are ignored). Most associative collections are derived from the abstract type `<strong>AbstractDict{K, V}</strong>`.

# 

`<strong>Dict{K,V}</strong>` is a simple associative collection used in Julia. Parametric type `<strong>K</strong>` is used as a key and type `<strong>V</strong>` as a value. The only requirement is there must be a hash function defined for the type `<strong>K</strong>`.

`<strong>julia&gt; d = Dict("a"=&gt;1, "c"=&gt;2, "b"=&gt;3)<br>Dict{String,Int64} with 3 entries:<br>&nbsp;&nbsp;"c" =&gt; 2<br>&nbsp;&nbsp;"b" =&gt; 3<br>&nbsp;&nbsp;"a" =&gt; 1<br>julia&gt; d["b"]<br>3<br>julia&gt; d["a"] = 5<br>5<br>julia&gt; println(d)<br>Dict("c" =&gt; 2,"b" =&gt; 3,"a" =&gt; 5)</strong>`

`<strong>Dict{K,V}</strong>` cannot hold multiple values for the same key. Repetition of keys in the definition overwrites the previously defined value.

`<strong>julia&gt; d = Dict("a"=&gt;1, "c"=&gt;2, "b"=&gt;3, "a"=&gt;4)<br>Dict{String,Int64} with 3 entries:<br>&nbsp;&nbsp;"c" =&gt; 2<br>&nbsp;&nbsp;"b" =&gt; 3<br>&nbsp;&nbsp;"a" =&gt; 4</strong>`

# 

`<strong>get(dict, key, defval)</strong>` method is used to extract information from a `<strong>Dict</strong>` object. Here are a few examples of the same:

`<strong>julia&gt; get(d, "a", 3)<br>4<br>julia&gt; get(d, "e", 0)<br>0</strong>`

When the key is part of the `<strong>Dict</strong>`, the value associated with the key is returned. However, when the key is not available the default value specified in the function is returned.

Mostly, `<strong>Dict{K,V}</strong>` objects are used like arrays with keys being the index. `<strong>getindex</strong>` or its alias ([]) are used to obtain values from the dictionaries. Unlike the get methods `<strong>getindex</strong>` throws an ErrorException when a key is not found in the dictionary.

`<strong>julia&gt; getindex(d, "e")<br>ERROR: KeyError: key "e" not found<br>Stacktrace:<br>&nbsp;[1] getindex(::Dict{String,Int64}, ::String) at .\dict.jl:467<br>&nbsp;[2] top-level scope at REPL[21]:1<br>julia&gt; getindex(d, "a")<br>4<br>julia&gt; d["e"]<br>ERROR: KeyError: key "e" not found<br>Stacktrace:<br>&nbsp;[1] getindex(::Dict{String,Int64}, ::String) at .\dict.jl:467<br>&nbsp;[2] top-level scope at REPL[23]:1</strong>`

`<strong>get!(dict, key, value)</strong>` method is similar to the `<strong>get(dict, key, defval)</strong>` method but will insert the key with value where the key is not available in the dict. In the preceding example:

`<strong>julia&gt; get!(d, "a", 0)<br>4<br>julia&gt; get!(d, "e", 0)<br>0<br>julia&gt; d<br>Dict{String,Int64} with 4 entries:<br>&nbsp;&nbsp;"c" =&gt; 2<br>&nbsp;&nbsp;"e" =&gt; 0<br>&nbsp;&nbsp;"b" =&gt; 3<br>&nbsp;&nbsp;"a" =&gt; 4</strong>`

**Note:** It is a general convention in Julia to add a bang(!) character to the end of the function name that mutates the parameter values. Since the `<strong>get!(dict, key, value)</strong>` method changes the object `<strong>dict</strong>`, the bang character is added to the end.

# 

Just like get methods, `<strong>setindex!</strong>` method or the alias ([]) used as l-value.

`<strong>julia&gt; d["e"] = 10<br>10</strong>`

Or more uncommon usage:

`<strong>julia&gt; setindex!(d, 11, "e")<br>Dict{String,Int64} with 4 entries:<br>&nbsp;&nbsp;"c" =&gt; 2<br>&nbsp;&nbsp;"e" =&gt; 11<br>&nbsp;&nbsp;"b" =&gt; 3<br>&nbsp;&nbsp;"a" =&gt; 4</strong>`

# 

For the `<strong>Dict{K,V}</strong>` to properly work, `<strong>hash(k::K, h::Int)</strong>` should be implemented. The function returns a unique integer for every instance of `<strong>k</strong>`. This uniqueness ensures only one key is stored in a `<strong>Dict{K,V}</strong>`.

# 

`<strong>Set</strong>` is a collection where only one instance of an element can reside. The ordering of elements in the `<strong>Set</strong>` is unimportant. The following example highlights some of the `<strong>Set</strong>` methods.

`<strong>julia&gt; s = Set([2 3 4 5 1 2 3])<br>Set{Int64} with 5 elements:<br>&nbsp;&nbsp;4<br>&nbsp;&nbsp;2<br>&nbsp;&nbsp;3<br>&nbsp;&nbsp;5<br>&nbsp;&nbsp;1<br>julia&gt; 6 in s<br>false<br>julia&gt; 5 in s<br>true<br>julia&gt; t = Set([4 5 7 8 9])<br>Set{Int64} with 5 elements:<br>&nbsp;&nbsp;7<br>&nbsp;&nbsp;4<br>&nbsp;&nbsp;9<br>&nbsp;&nbsp;5<br>&nbsp;&nbsp;8</strong>`

# 

`<strong>julia&gt; union(s, t)<br>Set{Int64} with 8 elements:<br>&nbsp;&nbsp;7<br>&nbsp;&nbsp;4<br>&nbsp;&nbsp;9<br>&nbsp;&nbsp;2<br>&nbsp;&nbsp;3<br>&nbsp;&nbsp;5<br>&nbsp;&nbsp;8<br>&nbsp;&nbsp;1<br>julia&gt; intersect(s, t)<br>Set{Int64} with 2 elements:<br>&nbsp;&nbsp;4<br>&nbsp;&nbsp;5<br>julia&gt; union!(s, t)<br>Set{Int64} with 8 elements:<br>&nbsp;&nbsp;7<br>&nbsp;&nbsp;4<br>&nbsp;&nbsp;9<br>&nbsp;&nbsp;2<br>&nbsp;&nbsp;3<br>&nbsp;&nbsp;5<br>&nbsp;&nbsp;8<br>&nbsp;&nbsp;1<br>julia&gt; s<br>Set{Int64} with 8 elements:<br>&nbsp;&nbsp;7<br>&nbsp;&nbsp;4<br>&nbsp;&nbsp;9<br>&nbsp;&nbsp;2<br>&nbsp;&nbsp;3<br>&nbsp;&nbsp;5<br>&nbsp;&nbsp;8<br>&nbsp;&nbsp;1</strong>`

`<strong>union!</strong>` works like union but updates the first argument. Just like `<strong>union</strong>`, `<strong>symdiff</strong>` and `<strong>setdiff</strong>` methods are defined for symmetric difference and set difference as well. `<strong>issubset</strong>` method provides the subset relationship of one set with another.

# 

Iteration is one of the fundamental operations of a collection. We shall observe how various iteration operations can be used with collections.

# 

The classic `<strong>for</strong>` loop in Julia is a mapping of an index variable to a range object and iterating over it.

`<strong>julia&gt; for i=5:-2:1<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; println(i)<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; end<br>5<br>3<br>1</strong>`

The loop is not limited to range objects only. One can use other kinds of collections as well. Here are some examples:

`<strong>julia&gt; b = [1.0 2 3; 4 5 6; 7 8 9];<br>julia&gt; for i=b<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; println(i)<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; end<br>1.0<br>4.0<br>7.0<br>2.0<br>5.0<br>8.0<br>3.0<br>6.0<br>9.0</strong>`

Instead of `<strong>for…=</strong>`, `<strong>for…in</strong>` can be used as well. This representation of for loop is similar to the previous only the syntax that looks more conducive to a collection. Let us look at the usage of this against a dictionary object.

`<strong>julia&gt; for p in d<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; println(p)<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; end<br>"e" =&gt; 2<br>"b" =&gt; 4<br>"a" =&gt; 1<br>"d" =&gt; 3</strong>`

The `<strong>Dict{K,V}</strong>` elements are stored as `<strong>Pair{K,V}</strong>` and are default printed as: k => v.

`<strong>julia&gt; for (k, v) in d<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; println("Key:", k," Value:", v)<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; end<br>Key:e Value:2<br>Key:b Value:4<br>Key:a Value:1<br>Key:d Value:3</strong>`

# 

Let us look at a function that takes an array as an input and returns square of all the values as an array.

`<strong>function collect_square(v)<br>&nbsp;&nbsp;&nbsp;&nbsp;a = similar(v)<br>&nbsp;&nbsp;&nbsp;&nbsp;for i=1:length(v)<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;a[i] = v[i]*v[i]<br>&nbsp;&nbsp;&nbsp;&nbsp;end<br>&nbsp;&nbsp;&nbsp;&nbsp;return a<br>end<br>julia&gt; collect_square(1:4)<br>4-element Vector{Int64}:<br>&nbsp;&nbsp;1<br>&nbsp;&nbsp;4<br>&nbsp;&nbsp;9<br>&nbsp;16</strong>`

If we were to extend this function to return values after computing any arbitrary function instead of a square, we can extend it in the following way:

`<strong>function collect_function(f::Function, v)<br>&nbsp;&nbsp;&nbsp;&nbsp;a = similar(v)<br>&nbsp;&nbsp;&nbsp;&nbsp;for i=1:length(v)<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;a[i] = f(v[i])<br>&nbsp;&nbsp;&nbsp;&nbsp;end<br>&nbsp;&nbsp;&nbsp;&nbsp;return a<br>end<br>julia&gt; collect_function(x-&gt;x^3, 1:4)<br>4-element Vector{Int64}:<br>&nbsp;&nbsp;1<br>&nbsp;&nbsp;8<br>&nbsp;27<br>&nbsp;64</strong>`

An alternate approach to calling the same method is `<strong>function…do</strong>` notation as shown.

`<strong>julia&gt; collect_function(1:4) do x<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; return x^3<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; end<br>4-element Vector{Int64}:<br>&nbsp;&nbsp;1<br>&nbsp;&nbsp;8<br>&nbsp;27<br>&nbsp;64</strong>`

`<strong>map</strong>` is a function with similar notations. It maps each value of a collection elements and applies a function to each element and returns the result of function evaluations as a collection.

`<strong>julia&gt; map(1:4) do x<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; return x^3<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; end<br>4-element Vector{Int64}:<br>&nbsp;&nbsp;1<br>&nbsp;&nbsp;8<br>&nbsp;27<br>&nbsp;64</strong>`

# 

We saw a few examples of sequences and collections being iterated over using the for loop. This is practically possible because all such types implement the iteration framework. If you were to write a custom iterator, you may need to implement this framework. While some basic ideas are highlighted here, you are suggested to read the Julia documentation[3](#xjo4a1bi.html#n4upl4fndno) for the relevant details.

`<strong>julia&gt; v = collect(3:2:10)<br>4-element Vector{Int64}:<br>&nbsp;3<br>&nbsp;5<br>&nbsp;7<br>&nbsp;9<br>julia&gt; for i=v<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; println(i)<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; end<br>3<br>5<br>7<br>9</strong>`

The same can be written in the following form:

`<strong>julia&gt; next = iterate(v)<br>(3, 2)<br>julia&gt; while next !== nothing<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; value, state = next<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; println(value)<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; next = iterate(v, state)<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; end<br>3<br>5<br>7<br>9</strong>`

# 

`<strong>iterate(collection)</strong>` returns the first item and initial state or nothing if no values exist.

In the return value `<strong>(3, 2)</strong>` in the preceding example, `<strong>3</strong>` is the value of the first element and `<strong>2</strong>` is an internal parameter representing the state. Although, it may seem like the index of the next value, one should not assume the same as those are completely implementation specific.

`<strong>iterate(collection, state)</strong>` returns the next item and next state or nothing if no additional items exist.

`<strong>iterate</strong>` methods must be implemented by all iterator types.

# 

These are methods that need to be optionally defined by the iterator authors.

`<strong>IteratorSize(IterType)</strong>` is a helper method that says if the iterator has a length or a shape. Based on which size or/and length methods must be defined for the collection iterator.

`<strong>julia&gt; Base.IteratorSize(Vector{Int})<br>Base.HasShape{1}()</strong>`

`<strong>IteratorEltype(IterType)</strong>` is a helper method that decides the if the iterator has a specific element type.

`<strong>julia&gt; Base.IteratorEltype(Vector{Int})<br>Base.HasEltype()</strong>`

`<strong>eltype(IterType)</strong>` returns the type of the first parameter of the `<strong>iterate</strong>` method.

`<strong>julia&gt; eltype(Vector{Int})<br>Int64</strong>`

A detailed explanation of the methods can be seen from Julia’s documentation.

# 

We create a `<strong>Squares</strong>` type that will provide a sequence of squares of numbers up to the value stored in the type.

`<strong>struct Squares<br>&nbsp;&nbsp;&nbsp;&nbsp;value::Int<br>end</strong>`

`<strong>Base.iterate(s::Squares) = s.value &lt;= 0 ? nothing : (1, 2)<br><br>Base.iterate(s::Squares, state) = s.value &lt; state ? nothing :&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<br>&nbsp;&nbsp;&nbsp;&nbsp;(state*state, state+1)<br><br>julia&gt; for i=Squares(3)<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; println(i)<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; end<br>1<br>4<br>9</strong>`

While the preceding one works for simple `<strong>for</strong>` loop. Trying to create an array with `<strong>collect</strong>` the method will not work.

`<strong>julia&gt; collect(Squares(3))<br>ERROR: MethodError: no method matching length(::Squares)<br>…</strong>`

So we add a `<strong>length</strong>` method to achieve the same.

`<strong>julia&gt; Base.length(s::Squares)=s.value<br>julia&gt; collect(Squares(3))<br>3-element Vector{Any}:<br>&nbsp;1<br>&nbsp;4<br>&nbsp;9</strong>`

While an `<strong>Array</strong>` is populated properly the type is of `<strong>Any</strong>`. Defining the `<strong>eltype(IteratorType)</strong>` method will ensure the proper type of `<strong>Array</strong>` is created.

`<strong>Base.eltype(::Type{Squares})=Int<br><br>julia&gt; eltype(Squares)<br>Int64<br><br>julia&gt; collect(Squares(3))<br>3-element Vector{Int64}:<br>&nbsp;1<br>&nbsp;4<br>&nbsp;9</strong>`

**Note:** `<strong>Type{Squares}</strong>` **is a special type whose only instance object is** `<strong>Squares</strong>`**. This is needed as** `<strong>eltype</strong>` **is a function of the type itself and not an instance of the type.**

# 

In Julia, arrays and collections are used extensively in scientific computations. It is rather imperative that the language provides easy access to creation and manipulation of arrays. Comprehension representations provide the ease of creating such arrays.

`<strong>julia&gt; [i*i for i=1:3]<br>3-element Vector{Int64}:<br>&nbsp;1<br>&nbsp;4<br>&nbsp;9<br>julia&gt; [i*j for i=1:3, j=1:3]<br>3×3 Matrix{Int64}:<br>&nbsp;1&nbsp;&nbsp;2&nbsp;&nbsp;3<br>&nbsp;2&nbsp;&nbsp;4&nbsp;&nbsp;6<br>&nbsp;3&nbsp;&nbsp;6&nbsp;&nbsp;9</strong>`

In the preceding examples, comprehensions are used to create a single dimension and multi-dimensional array. Following is an example where an index may depend on another.

`<strong>julia&gt; [i*j for i=1:3 for j=i:3]<br>6-element Vector{Int64}:<br>&nbsp;1<br>&nbsp;2<br>&nbsp;3<br>&nbsp;4<br>&nbsp;6<br>&nbsp;9</strong>`

Comprehensions compute the complete arrays, it may also help to have a delayed execution iterator where the computation of the values happens when demanded than for all the elements. These are called **generators**.

`<strong>julia&gt; gen=(i*j for i=1:3 for j=i:3)<br>Base.Iterators.Flatten{Base.Generator{UnitRange{Int64},var"#6#7"}}(Base.Generator{UnitRange{Int64},var"#6#7"}(var"#6#7"(), 1:3))<br>julia&gt; for v=gen<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; println(v)<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; end<br>1<br>2<br>3<br>4<br>6<br>9</strong>`

# 

Collections provide a simple yet scalable interface for a class of algorithms and a unified iterator interface to access the elements. In this chapter, we reviewed a few simple data structures defined in the core Julia language. However, for a computation-centric language as Julia is, these are only the tip of the iceberg. You are requested to review the `<strong>DataStructures.jl</strong>` package to get more elaborate understanding of the data structures that are available for Julia. Similarly, if you are implementing custom data structures, you are advised to implement the iterator interface for your data structures to be compatible with the iteration framework of Julia language like `<strong>for</strong>`, `<strong>while</strong>` loops, and so on.

# 

1.  In initializing arrays space (), comma (`,`), and semicolon (`;`) symbols are used. Are there any special operators like meaning they carry when they are enclosed within square brackets (`[]`)?
2.  Pick up one datastructure of your choice and implement it in Julia. Write the basic operations you will need for the datastructure. Write an iterator interface for the same so that you can iterate the datastructure using the `<strong>for…in</strong>` syntax.
3.  The `<strong>Dict</strong>` type requires hash function must be defined for the keys. Try to implement a `<strong>MyDict</strong>` type that behaves like `<strong>Dict</strong>` but does not mandate the keys should have a `hash` function.
4.  `<strong>Dict</strong>` uses the `<strong>hash</strong>` function. But, `<strong>hash</strong>` function exists for almost all Julia types. Why is the `hash` function being used? Are there other functionalities that may not work if `hash` functions are not defined?
5.  Create a generator that iterates from 1 to 100 and returns all the numbers excepting numbers divisible by 3.

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

[1](#xjo4a1bi.html#n4upl4fndnp) Wirth, Nicklaus, Algorithms + Data Structures = Programs, Prentice-Hall, 1976.

In Julia versions 1.5 and earlier, you may see `Matrix` type being printed as `Array{T, 2}` and `Vector` type as `Array{T, 1}`. The `Matrix` and `Vector` types are aliases of `Array{T, N}`.

[3](#xjo4a1bi.html#n4upl4fndnq) Julia documentation on iteration interface. (**[https://docs.julialang.org/en/v1/manual/interfaces/#man-interface-iteration](https://docs.julialang.org/en/v1/manual/interfaces/#man-interface-iteration)**)

Julia documentation on iteration interface. (**[https://docs.julialang.org/en/v1/manual/interfaces/#man-interface-iteration](https://docs.julialang.org/en/v1/manual/interfaces/#man-interface-iteration)**)

Wirth, Nicklaus, Algorithms + Data Structures = Programs, Prentice-Hall, 1976.

We saw a few examples of sequences and collections being iterated over using the for loop. This is practically possible because all such types implement the iteration framework. If you were to write a custom iterator, you may need to implement this framework. While some basic ideas are highlighted here, you are suggested to read the Julia documentation3 for the relevant details.

In 1975, *Niklaus Wirth*, a well-known computer exponent and author of the programming language PASCAL wrote a book *Algorithms + Data Structures = Programs*1; clearly highlighting the importance of data structures and algorithms in programming. There is hardly any modern programming language that does not provide in-built support for data structures. Julia is no exception either. Many data structures are defined in the core Julia language and a wide range of data structures are defined in packages like `<strong>DataStrctures.jl</strong>`. In this chapter, our focus will be the data structures defined in the language without the need to use any additional packages. To name a few:

# 

# 

# 

In the previous chapter, we looked at simple arrays along with other forms of collections. We also iterated over collections. However, arrays have a substantial role to play in Julia in providing high-performance containers that are memory managed with the ability to transfer data between native applications. In this chapter, we will look at some of the advanced applications of the arrays. Sometimes, operations are defined on arrays; or given simple syntactic modifications can conduct complex array operations.

# 

In this chapter, we will cover the following topics:

*   Containers
*   Dimensions
*   Indexing
*   Slicing
*   Broadcasting
*   Reduction
*   Abstract array types
*   Sparse arrays
*   Linear algebra

# 

The reader shall be able to learn use cases of arrays, vectors, and matrices, abstract data types associated with arrays so that they can design their own array types. Arrays have various indexing schemes. They can be sliced into parts, composed into views of arrays that reduce large-scale allocations. Sparse arrays reduce allocation of space or memory.

# 

Arrays are the most common collections used for various operations as they are mutable, extendible and when properly used are efficient. Some of the topics discussed in this chapter may be advanced for novice users. So, it may be recommended to review parts of this chapter later as you gather experience with the language.

Vector as a container is a very common use case. Some data structures like stacks, queues, binary heaps are normally implemented using one-dimensional arrays or vectors. Julia provides simple functions to handle these cases without a need to implement anything additional. The following are a few examples showing the capability of a vector being used as a stack.

`<strong>julia&gt; a = []<br>Any[]<br>julia&gt; push!(a, 5)<br>1-element Vector{Any}:<br>&nbsp;5<br>julia&gt; push!(a, 5, 6, 7, 8)<br>5-element Vector{Any,1}:<br>&nbsp;5<br>&nbsp;5<br>&nbsp;6<br>&nbsp;7<br>&nbsp;8<br>julia&gt; pop!(a)<br>&nbsp;8</strong>`

The application of the preceding methods will lead to the vector be modified in the following manner. At the end of the operation, you can also empty the container with a method `<strong>empty!(vector)</strong>`.

`<strong>julia&gt; length(a)<br>4<br>julia&gt; isempty(a)<br>false<br>julia&gt; empty!(a)<br>Any[]<br>julia&gt; isempty(a)<br>true</strong>`

Let us look at the array operating as a queue.

`<strong>julia&gt; push!(a, 1, 2, 3, 4, 5)<br>5-element Vector{Any}:<br>&nbsp;1<br>&nbsp;2<br>&nbsp;3<br>&nbsp;4<br>&nbsp;5<br>julia&gt; popfirst!(a)<br>1<br>julia&gt; a<br>4-element Vector{Any}:<br>&nbsp;2<br>&nbsp;3<br>&nbsp;4<br>&nbsp;5<br>julia&gt; pushfirst!(a, 1)<br>5-element Vector{Any}:<br>&nbsp;1<br>&nbsp;2<br>&nbsp;3<br>&nbsp;4<br>&nbsp;5</strong>`

`<strong>pushfirst!(v, value)</strong>` is a method that adds a `<strong>value</strong>` to the beginning of the vector.

**While** `<strong>pushfirst!</strong>` **and** `<strong>popfirst!</strong>` **methods exist, they are not the most efficient ones as inserting and deleting the first element may need to copy or move elements.**

# 

Arrays can be of any dimension. While we studied mostly vectors (dimension 1) and matrices (dimension 2) in the previous chapter, we will look at some more of the higher dimension arrays in this chapter.

`<strong>julia&gt; a = reshape(collect(1:24), 4, 3, 2)</strong>`

`<strong>4×3×2 Array{Int64, 3}:</strong>`

`<strong>[:, :, 1] =</strong>`

`<strong>&nbsp;1&nbsp;&nbsp;5&nbsp;&nbsp; 9</strong>`

`<strong>&nbsp;2&nbsp;&nbsp;6&nbsp;&nbsp;10</strong>`

`<strong>&nbsp;3&nbsp;&nbsp;7&nbsp;&nbsp;11</strong>`

`<strong>&nbsp;4&nbsp;&nbsp;8&nbsp;&nbsp;12</strong>`

`<strong>[:, :, 2] =</strong>`

`<strong>&nbsp;13&nbsp;&nbsp;17&nbsp;&nbsp;21</strong>`

`<strong>&nbsp;14&nbsp;&nbsp;18&nbsp;&nbsp;22</strong>`

`<strong>&nbsp;15&nbsp;&nbsp;19&nbsp;&nbsp;23</strong>`

`<strong>&nbsp;16&nbsp;&nbsp;20&nbsp;&nbsp;24</strong>`

`<strong>julia&gt; ndims(a)<br>3<br>julia&gt; size(a)<br>(4, 3, 2)<br>julia&gt; size(a, 3)<br>2</strong>`

`<strong>reshape</strong>` takes in a collection and creates an array of specified shape. `<strong>ndims</strong>` provides the number of dimensions in the array while size provides the number of elements in each of the dimensions. The array size in a specific dimension is reported by `<strong>size (array, dim)</strong>`. The memory layout of the array is shown in the following figure:

![](n4upl4fndp9.jpeg)

**Figure 6.1:** Array shown in 3-D with row-major indexing in Julia

# 

Arrays are indexed using the expression of type `<strong>A[I_1, I_2, …, I_n]</strong>`. I_i are the indexes that can be of various types that we shall explore in this section.

# 

The simplest form of index expressions can be scalars or numbers. Here are some examples:

`<strong>julia&gt; a = reshape(collect(1:24), 4, 3, 2, 1)<br>4×3×2×1 Array{Int64,4}:<br>[:, :, 1, 1] =<br>&nbsp;1&nbsp;&nbsp;5&nbsp;&nbsp; 9<br>&nbsp;2&nbsp;&nbsp;6&nbsp;&nbsp;10<br>&nbsp;3&nbsp;&nbsp;7&nbsp;&nbsp;11<br>&nbsp;4&nbsp;&nbsp;8&nbsp;&nbsp;12<br>[:, :, 2, 1] =<br>&nbsp;13&nbsp;&nbsp;17&nbsp;&nbsp;21<br>&nbsp;14&nbsp;&nbsp;18&nbsp;&nbsp;22<br>&nbsp;15&nbsp;&nbsp;19&nbsp;&nbsp;23<br>&nbsp;16&nbsp;&nbsp;20&nbsp;&nbsp;24<br>julia&gt; a[1, 2, 1, 1]<br>5</strong>`

# 

The index expression can be ranges as well. `<strong>Colon(:)</strong>` has a special meaning the all the indices in the dimension.

`<strong>julia&gt; a[:, 1, 1, 1]<br>4-element Vector{Int64}:<br>&nbsp;1<br>&nbsp;2<br>&nbsp;3<br>&nbsp;4<br>julia&gt; a[2:3, 1, 1, 1]<br>2-element Vector{Int64}:<br>&nbsp;2<br>&nbsp;3<br>julia&gt; a[1:2:3, 1, 1, 1]<br>2-element Vector{Int64}:<br>&nbsp;1<br>&nbsp;3</strong>`

As can be seen, range objects can be of any of the integral range types like `<strong>UnitRange</strong>`, `<strong>StepRange</strong>`, and so on. Multiple range indices can be used as index expressions as well. This leads to multidimensional arrays with elements picked up from locations that are specified in the ranges.

`<strong>julia&gt; a[1:2:3, 1:2:3, 1, 1]<br>2×2 Matrix{Int64}:<br>&nbsp;1&nbsp;&nbsp; 9<br>&nbsp;3&nbsp;&nbsp;11</strong>`

# 

When the index expressions are vectors or non-scalars additional dimensions are introduced to the output. Here are some examples:

`<strong>julia&gt; a[1:2:3, 1:2:3, [1], [1]]<br>2×2×1×1 Array{Int64,4}:<br>[:, :, 1, 1] =<br>&nbsp;1&nbsp;&nbsp; 9<br>&nbsp;3&nbsp;&nbsp;11</strong>`

An array of 2×2×1×1 is created instead of an array of 2×2 as shown in the preceding example. The index vectors by default are assumed to be of one dimension with row vector.

`<strong>julia&gt; a[1:2:3, [1; 3], 1, 1]<br>2×2 Matrix{Int64}:<br>&nbsp;1&nbsp;&nbsp; 9<br>&nbsp;3&nbsp;&nbsp;11<br>julia&gt; a[1:2:3, [1, 3], 1, 1]<br>2×2 Matrix{Int64}:<br>&nbsp;1&nbsp;&nbsp; 9<br>&nbsp;3&nbsp;&nbsp;11</strong>`

When the indices are not in the row order the output will not be able to merge into a 2×2 matrix in this case:

`<strong>julia&gt; b = a[1:2:3, [1 3], 1, 1]<br>2×1×2 Array{Int64,3}:<br>[:, :, 1] =<br>&nbsp;1<br>&nbsp;3<br>[:, :, 2] =<br>&nbsp;9<br>&nbsp;11</strong>`

A matrix of 2×1×2 is generated. Similarly, one can create a more involved matrix by providing a multi-dimensional index.

`<strong>julia&gt; a[:, [2], [1], [1]]<br>4×1×1×1 Array{Int64,4}:<br>[:, :, 1, 1] =<br>&nbsp;5<br>&nbsp;6<br>&nbsp;7<br>&nbsp;8<br>julia&gt; a[[1 2; 3 4], [2], [1], [1]]<br>2×2×1×1×1 Array{Int64,5}:<br>[:, :, 1, 1, 1] =<br>&nbsp;5&nbsp;&nbsp;6<br>&nbsp;7&nbsp;&nbsp;8</strong>`

Here, the introduction of a multi-dimensional index in the first index added an additional dimension to the matrix. The matrix has 2×2×1×1×1 dimensions. The first 2 columns are a rearrangement of the 1st column of `<strong>a[:, [1], [1], [1]]</strong>` based on the index parameter `<strong>[1 2; 3 4]</strong>`.

# 

We discussed in the previous chapter that the arrays are stored as a contiguous memory location in a row-major fashion and the indexing is carried out as an overlay over the underlying data. The data underlying can be accessed as a single integer index. Such kind of indexing is called as `<strong>linear indexing</strong>`.

`<strong>julia&gt; a = reshape(collect(1:6), (2, 3))<br>2×3 Matrix{Int64}:<br>&nbsp;1&nbsp;&nbsp;3&nbsp;&nbsp;5<br>&nbsp;2&nbsp;&nbsp;4&nbsp;&nbsp;6<br>julia&gt; a[5]<br>5<br>julia&gt; a[1, 3]<br>5</strong>`

There is a type called `<strong>LinearIndices</strong>` that helps in creating this mapping.

`<strong>julia&gt; LinearIndices(a)<br>2×3 LinearIndices{2,Tuple{Base.OneTo{Int64},Base.OneTo{Int64}}}:<br>&nbsp;1&nbsp;&nbsp;3&nbsp;&nbsp;5<br>&nbsp;2&nbsp;&nbsp;4&nbsp;&nbsp;6</strong>`

# 

Cartesian indexing is a tuple of numbers as the dimension of the array that represent one element.

`<strong>julia&gt; A = reshape(collect(1:6), 3, 2)<br>3×2 Matrix{Int64}:<br>&nbsp;1&nbsp;&nbsp;4<br>&nbsp;2&nbsp;&nbsp;5<br>&nbsp;3&nbsp;&nbsp;6<br>julia&gt; ci = CartesianIndices(A)<br>3×2CartesianIndices{2,Tuple{Base.OneTo{Int64},Base.OneTo{Int64}}}:<br>&nbsp;CartesianIndex(1, 1)&nbsp;&nbsp;CartesianIndex(1, 2)<br>&nbsp;CartesianIndex(2, 1)&nbsp;&nbsp;CartesianIndex(2, 2)<br>&nbsp;CartesianIndex(3, 1)&nbsp;&nbsp;CartesianIndex(3, 2)</strong>`

Usage of cartesian or linear index depends on the object and organization of the data. We will review further details on these topics later as we look at views and sub-arrays.

# 

Boolean indices act more like filters over the data.

`<strong>julia&gt; x = reshape(collect(1:16), 4, 4)<br>4×4 Matrix{Int64}:<br>&nbsp;1&nbsp;&nbsp;5&nbsp;&nbsp; 9&nbsp;&nbsp;13<br>&nbsp;2&nbsp;&nbsp;6&nbsp;&nbsp;10&nbsp;&nbsp;14<br>&nbsp;3&nbsp;&nbsp;7&nbsp;&nbsp;11&nbsp;&nbsp;15<br>&nbsp;4&nbsp;&nbsp;8&nbsp;&nbsp;12&nbsp;&nbsp;16<br>julia&gt; filter = map(ispow2, x)<br>4×4 Matrix{Bool}:<br>&nbsp;1&nbsp;&nbsp;0&nbsp;&nbsp;0&nbsp;&nbsp;0<br>&nbsp;1&nbsp;&nbsp;0&nbsp;&nbsp;0&nbsp;&nbsp;0<br>&nbsp;0&nbsp;&nbsp;0&nbsp;&nbsp;0&nbsp;&nbsp;0<br>&nbsp;1&nbsp;&nbsp;1&nbsp;&nbsp;0&nbsp;&nbsp;1<br>julia&gt; x[filter]<br>5-element Vector{Int64}:<br>&nbsp;1<br>&nbsp;2<br>&nbsp;4<br>&nbsp;8<br>16</strong>`

While it may seem logical indexing is carried out only to pick up specific values where the filter value is true, in the combination of range indices interesting variations can be observed. For example, the following example picks up the 2nd and 3rd row entirely.

`<strong>julia&gt; x[[false, true, true, false], :]<br>2×4 Matrix{Int64}:<br>&nbsp;2&nbsp;&nbsp;6&nbsp;&nbsp;10&nbsp;&nbsp;14<br>&nbsp;3&nbsp;&nbsp;7&nbsp;&nbsp;11&nbsp;&nbsp;15</strong>`

# 

Most of the examples, we worked with indices were related to extracting information from arrays or what are known as `<strong>l-valued expressions</strong>`. However, similar expressions can be used for assigning values to array elements as well.

`<strong>julia&gt; a = reshape(collect(1:24), 4, 3, 2, 1);<br>julia&gt; a[:, 2, 1, 1] = fill(25, 4)<br>4-element Vector{Int64}:<br>&nbsp;25<br>&nbsp;25<br>&nbsp;25<br>&nbsp;25<br>julia&gt; a<br>4×3×2×1 Array{Int64,4}:<br>[:, :, 1, 1] =<br>&nbsp;1&nbsp;&nbsp;25&nbsp;&nbsp; 9<br>&nbsp;2&nbsp;&nbsp;25&nbsp;&nbsp;10<br>&nbsp;3&nbsp;&nbsp;25&nbsp;&nbsp;11<br>&nbsp;4&nbsp;&nbsp;25&nbsp;&nbsp;12</strong>`

`<strong>[:, :, 2, 1] =</strong>`

`<strong>&nbsp;13&nbsp;&nbsp;17&nbsp;&nbsp;21</strong>`

`<strong>&nbsp;14&nbsp;&nbsp;18&nbsp;&nbsp;22</strong>`

`<strong>&nbsp;15&nbsp;&nbsp;19&nbsp;&nbsp;23</strong>`

`<strong>&nbsp;16&nbsp;&nbsp;20&nbsp;&nbsp;24</strong>`

# 

For ease of traversal in collections, sometimes specialized keywords like begin and end are used as indices. Even such indices can be used along with some numerical operations. The elements of the preceding array can be accessed as shown:

`<strong>julia&gt; a[begin, :, 2, 1], a[begin+1, :, 2, 1]</strong>`

`<strong>([13, 17, 21], [14, 18, 22])</strong>`

`<strong>julia&gt; a[end, :, 2, 1], a[end-1, :, 2, 1]</strong>`

`<strong>([16, 20, 24], [15, 19, 23])</strong>`

# 

The following methods are defined for arrays or all collections like `<strong>Dict</strong>` that support indexed access of elements.

`<strong>getindex(X, i)</strong>` returns the value of the element at location `<strong>i</strong>` when `<strong>X[i]</strong>` is accessed. In a multidimensional array, the same is extended to using expression `<strong>getindex(X, I_1, I_2, …, I_n)</strong>` when `<strong>X[I_1, I_2, …, I_n]</strong>` is accessed.

`<strong>setindex!(X, v, i)</strong>` assigns value `<strong>v</strong>` to the array element at location `<strong>i</strong>`. In a multi-dimensional array, the same can translate to expression of the form `<strong>X[I_1, I_2, …, I_n] = v</strong>` that invokes `<strong>setindex!(X, v, I_1, I_2, …, I_n)</strong>` internally.

`<strong>firstindex(X)</strong>` provides the index when the expression `<strong>X[begin]</strong>` is used. `<strong>firstindex(X, dim)</strong>` can be used for specific dimension dim as well.

`<strong>lastindex(X)</strong>` provides the index when the expression `<strong>X[end]</strong>` is used. Just like `<strong>firstindex</strong>`, `<strong>lastindex</strong>` also can have dimension as a parameter as well.

`<strong>julia&gt; firstindex(a)<br>1<br>julia&gt; lastindex(a)<br>24<br>julia&gt; lastindex(a, 1)<br>4<br>julia&gt; lastindex(a, 2)<br>3<br>julia&gt; lastindex(a, 3)<br>2<br>julia&gt; lastindex(a, 4)<br>1</strong>`

# 

Slicing is using a portion of an array by specifying an index. Following are a few examples:

`<strong>julia&gt; a = reshape(collect(1:9), 3, 3)<br>3×3 Matrix{Int64}:<br>&nbsp;1&nbsp;&nbsp;4&nbsp;&nbsp;7<br>&nbsp;2&nbsp;&nbsp;5&nbsp;&nbsp;8<br>&nbsp;3&nbsp;&nbsp;6&nbsp;&nbsp;9<br>julia&gt; a[:, 1]<br>3-element Vector{Int64}:<br>&nbsp;1<br>&nbsp;2<br>&nbsp;3<br>julia&gt; a[1, :]<br>3-element Vector{Int64}:<br>&nbsp;1<br>&nbsp;4<br>&nbsp;7<br>julia&gt; a[1, 2:3]<br>2-element Vector{Int64}:<br>&nbsp;4<br>&nbsp;7</strong>`

While most of the examples are fairly straight forward, we will like to bring to your attention `<strong>a[1, :]</strong>` and `<strong>a[1, 2:3]</strong>`. Both these should have been row matrices. However, Julia would return a single dimension vector.

`<strong>julia&gt; b = a[1:2, :]<br>2×3 Matrix{Int64}:<br>&nbsp;1&nbsp;&nbsp;4&nbsp;&nbsp;7<br>&nbsp;2&nbsp;&nbsp;5&nbsp;&nbsp;8<br>julia&gt; b[1, 2] = 10<br>10<br>julia&gt; b<br>2×3 Matrix{Int64}:<br>&nbsp;1&nbsp;&nbsp;10&nbsp;&nbsp;7<br>&nbsp;2&nbsp;&nbsp; 5&nbsp;&nbsp;8<br>julia&gt; a<br>3×3 Matrix{Int64}:<br>&nbsp;1&nbsp;&nbsp;4&nbsp;&nbsp;7<br>&nbsp;2&nbsp;&nbsp;5&nbsp;&nbsp;8<br>&nbsp;3&nbsp;&nbsp;6&nbsp;&nbsp;9</strong>`

The end result of slicing with indices will allocate a new array. As can be seen, the mutating array `<strong>b</strong>` does not affect the data in `<strong>a</strong>`. This leads to large number of allocations and can fragment the application memory pool. Secondly, it can affect the performance with non-value add allocations. Let us rewrite the example:

`<strong>julia&gt; v = @view a[1:2, :]<br>2×3 view(::Matrix{Int64}, 1:2, :) with eltype Int64:<br>&nbsp;1&nbsp;&nbsp;4&nbsp;&nbsp;7<br>&nbsp;2&nbsp;&nbsp;5&nbsp;&nbsp;8<br>julia&gt; v[1, 2] = 10<br>10<br>julia&gt; v<br>2×3 view(::Matrix{Int64}, 1:2, :) with eltype Int64:<br>&nbsp;1&nbsp;&nbsp;10&nbsp;&nbsp;7<br>&nbsp;2&nbsp;&nbsp; 5&nbsp;&nbsp;8</strong>`

The macro `<strong>@view</strong>` (we will discuss macros in a later chapter) creates a view around the array while referring to the same objects of array a. Since a view has no data of its own, mutating the view also leads to modification of the data in the underlying container array.

`<strong>julia&gt; a<br>3×3 Matrix{Int64}:<br>&nbsp;1&nbsp;&nbsp;10&nbsp;&nbsp;7<br>&nbsp;2&nbsp;&nbsp; 5&nbsp;&nbsp;8<br>&nbsp;3&nbsp;&nbsp; 6&nbsp;&nbsp;9</strong>`

# 

Let us look at some matrix operations.

`<strong>julia&gt; a = reshape(collect(1:9), 3, 3)<br>3×3 Matrix{Int64}:<br>&nbsp;1&nbsp;&nbsp;4&nbsp;&nbsp;7<br>&nbsp;2&nbsp;&nbsp;5&nbsp;&nbsp;8<br>&nbsp;3&nbsp;&nbsp;6&nbsp;&nbsp;9<br>julia&gt; b = reshape(collect(9:-1:1), 3, 3)<br>3×3 Matrix{Int64}:<br>&nbsp;9&nbsp;&nbsp;6&nbsp;&nbsp;3<br>&nbsp;8&nbsp;&nbsp;5&nbsp;&nbsp;2<br>&nbsp;7&nbsp;&nbsp;4&nbsp;&nbsp;1<br>julia&gt; a + b<br>3×3 Matrix{Int64}:<br>&nbsp;10&nbsp;&nbsp;10&nbsp;&nbsp;10<br>&nbsp;10&nbsp;&nbsp;10&nbsp;&nbsp;10<br>&nbsp;10&nbsp;&nbsp;10&nbsp;&nbsp;10</strong>`

Each element of `<strong>a</strong>` is added to the corresponding element of `<strong>b</strong>` and the final result is an array of the same dimension as the input arrays. This is possible as for matrices or arrays the operator + is defined as an element type operation. Let us look at multiplication operation or operator (*).

`<strong>julia&gt; a * b<br>3×3 Matrix{Int64}:<br>&nbsp;&nbsp;90&nbsp;&nbsp;54&nbsp;&nbsp;18<br>&nbsp;114&nbsp;&nbsp;69&nbsp;&nbsp;24<br>&nbsp;138&nbsp;&nbsp;84&nbsp;&nbsp;30</strong>`

The result returned is not an element-wise multiplication but a matrix multiplication or also known as `<strong>array inner product</strong>`. If we were to do an element-wise operation on the arrays we could use the broadcast method for the same.

`<strong>julia&gt; broadcast(*, a, b)<br>3×3 Matrix{Int64}:<br>&nbsp;&nbsp;9&nbsp;&nbsp;24&nbsp;&nbsp;21<br>&nbsp;16&nbsp;&nbsp;25&nbsp;&nbsp;16<br>&nbsp;21&nbsp;&nbsp;24&nbsp;&nbsp; 9</strong>`

The same can be written as an inline dot notation (.\*).

`<strong>julia&gt; a .* b<br>3×3 Matrix{Int64}:<br>&nbsp;&nbsp;9&nbsp;&nbsp;24&nbsp;&nbsp;21<br>&nbsp;16&nbsp;&nbsp;25&nbsp;&nbsp;16<br>&nbsp;21&nbsp;&nbsp;24&nbsp;&nbsp; 9</strong>`

What if the array `<strong>a</strong>` and `<strong>b</strong>` are of different sizes? Can they interact at an elements level? Keeping `<strong>a</strong>` as the preceding one, let us make `<strong>b</strong>` row and column vector and observe the results.

`<strong>julia&gt; a = reshape(collect(1:9), 3, 3)<br>3×3 Matrix{Int64}:<br>&nbsp;1&nbsp;&nbsp;4&nbsp;&nbsp;7<br>&nbsp;2&nbsp;&nbsp;5&nbsp;&nbsp;8<br>&nbsp;3&nbsp;&nbsp;6&nbsp;&nbsp;9<br>julia&gt; b = [1 2 3]<br>1×3 Matrix{Int64}:<br>&nbsp;1&nbsp;&nbsp;2&nbsp;&nbsp;3<br>julia&gt; a .+ b<br>3×3 Matrix{Int64}:<br>&nbsp;2&nbsp;&nbsp;6&nbsp;&nbsp;10<br>&nbsp;3&nbsp;&nbsp;7&nbsp;&nbsp;11<br>&nbsp;4&nbsp;&nbsp;8&nbsp;&nbsp;12</strong>`

Similarly, when `<strong>b</strong>` is a column vector:

`<strong>julia&gt; b = [1, 2, 3]<br>3-element Vector{Int64}:<br>&nbsp;1<br>&nbsp;2<br>&nbsp;3<br>julia&gt; a .+ b<br>3×3 Matrix{Int64}:<br>&nbsp;2&nbsp;&nbsp;5&nbsp;&nbsp; 8<br>&nbsp;4&nbsp;&nbsp;7&nbsp;&nbsp;10<br>&nbsp;6&nbsp;&nbsp;9&nbsp;&nbsp;12</strong>`

When one of the arrays is a row or column vector, they are broadcast along the length of the vector if the dimensions are matching to the other vector in that direction. Although spoken in the context of arrays, the broadcast can be applied to any collection type. Here is an example showing element-wise concatenation of strings across collections.

`<strong>julia&gt; broadcast(string, ("one","two","three","four"), ": ", 1:4)<br>4-element Vector{String}:<br>&nbsp;"one: 1"<br>&nbsp;"two: 2"<br>&nbsp;"three: 3"<br>&nbsp;"four: 4"</strong>`

`<strong># You can write the preceding example as:<br># string.(("one","two","three","four"), ": ", 1:4)<br># dot(.) following the string would invoke the broadcast method.</strong>`

There is only one entry for ": " and that is repeated 4 times to be consistent with mapping with other collections being broadcast.

# 

One may wonder the effect of `<strong>broadcast</strong>` can be easily simulated with `<strong>repeat</strong>`. `<strong>repeat</strong>` takes the elements of the array and repeats them along each of the dimensions specified.

`<strong>julia&gt;v = [1, 2]</strong>`

`<strong>2-element Vector{Int64}:</strong>`

`<strong>&nbsp;1</strong>`

`<strong>&nbsp;2</strong>`

`<strong>julia&gt;repeat(v, 2, 3) #Repeats twice in dim 1 and thrice in dim 2</strong>`

`<strong>4×3 Matrix{Int64}:</strong>`

`<strong>&nbsp;1&nbsp;&nbsp;1&nbsp;&nbsp;1</strong>`

`<strong>&nbsp;2&nbsp;&nbsp;2&nbsp;&nbsp;2</strong>`

`<strong>&nbsp;1&nbsp;&nbsp;1&nbsp;&nbsp;1</strong>`

`<strong>&nbsp;2&nbsp;&nbsp;2&nbsp;&nbsp;2</strong>`

Such an argument is not entirely untrue. However, every call to `<strong>repeat</strong>` would allocate arrays and will add performance penalties. `<strong>broadcast</strong>` eliminates the need for such additional allocations.

`<strong>julia&gt; a + repeat(b, 1, 3)<br>3×3 Matrix{Int64}:<br>&nbsp;2&nbsp;&nbsp;5&nbsp;&nbsp; 8<br>&nbsp;4&nbsp;&nbsp;7&nbsp;&nbsp;10<br>&nbsp;6&nbsp;&nbsp;9&nbsp;&nbsp;12</strong>`

# 

It is worthwhile to revisit the `<strong>map</strong>` function we discussed earlier as we discuss `<strong>broadcast</strong>`. Unlike `<strong>broadcast</strong>` that repeats elements if needed, `<strong>map</strong>` function does a one-to-one mapping. As can be seen in the following example, the `<strong>map</strong>` function reports only a length 3 array matching to the minimum dimensions of `<strong>a</strong>` and `<strong>b</strong>`.

`<strong>julia&gt; a<br>3×3 Matrix{Int64}:<br>&nbsp;1&nbsp;&nbsp;4&nbsp;&nbsp;7<br>&nbsp;2&nbsp;&nbsp;5&nbsp;&nbsp;8<br>&nbsp;3&nbsp;&nbsp;6&nbsp;&nbsp;9<br>julia&gt; b<br>3-element Vector{Int64}:<br>&nbsp;1<br>&nbsp;2<br>&nbsp;3<br>julia&gt; map(+, a, b)<br>3-element Vector{Int64}:<br>&nbsp;2<br>&nbsp;4<br>&nbsp;6</strong>`

# 

Reduction operations on arrays are like summarizations. Similar to database aggregation and group by clauses, one can have aggregations with arrays along rows and columns. Mapping array elements to specific functions and reducing the results by rows and columns are rather common outcomes. Just like `<strong>broadcast</strong>`, `<strong>map</strong>` and `<strong>reduce</strong>` methods ensure intermediate allocations are minimized.

`<strong>julia&gt; a = reshape(collect(1:16), (2, 2, 2, 2))<br>2×2×2×2 Array{Int64,4}:<br>[:, :, 1, 1] =<br>&nbsp;1&nbsp;&nbsp;3<br>&nbsp;2&nbsp;&nbsp;4<br>[:, :, 2, 1] =<br>&nbsp;5&nbsp;&nbsp;7<br>&nbsp;6&nbsp;&nbsp;8<br>[:, :, 1, 2] =<br>&nbsp;&nbsp;9&nbsp;&nbsp;11<br>&nbsp;10&nbsp;&nbsp;12<br>[:, :, 2, 2] =<br>&nbsp;13&nbsp;&nbsp;15<br>&nbsp;14&nbsp;&nbsp;16<br>julia&gt; reduce(+, a)<br>136</strong>`

Given the collection `<strong>a</strong>`, `<strong>reduce</strong>` method applies the binary operation (+) on all the elements and returns the sum of all the elements.

# 

Let us replace the previous example from operator + to operator –. The left to right associativity will have a completely different result from right to left associativity. Julia provides two methods `<strong>foldl</strong>` and `<strong>foldr</strong>`, that are essentially representations of `<strong>reduce</strong>` method with left and right associativity respectively. We can use the associativity operator (=>) to look closely at the differences.

`<strong>julia&gt; foldl(=&gt;, [1, 2, 3, 4])<br>((1 =&gt; 2) =&gt; 3) =&gt; 4<br>julia&gt; foldr(=&gt;, [1, 2, 3, 4])<br>1 =&gt; (2 =&gt; (3 =&gt; 4))<br>julia&gt; reduce(=&gt;, [1, 2, 3, 4])<br>((1 =&gt; 2) =&gt; 3) =&gt; 4</strong>`

By replacing operator (=>) with operator (-) one can observe the difference in the results.

`<strong>julia&gt; foldl(-, [1, 2, 3, 4])<br>-8<br>julia&gt; foldr(-, [1, 2, 3, 4])<br>-2<br>julia&gt; reduce(-, [1, 2, 3, 4])<br>-8</strong>`

# 

The collection can be mapped to a specific function and the result can be reduced to an aggregated result. A specialized function called `<strong>mapreduce</strong>` simultaneously combines both these operations.

`<strong>julia&gt; mapreduce(x-&gt;x*x, +, [1, 2, 3, 4])<br>30</strong>`

The preceding example calculates the sum of squares of the collection.

# 

All the mapping and reduction methods we worked on are as applicable to other collections as they are to arrays. `<strong>mapslices</strong>` is a special function that is closely associated with arrays and array slices in particular.

`<strong>julia&gt; a = reshape(collect(1:16), 2, 2, 2, 2);<br>julia&gt; mapslices(sum, a, dims=[1, 2])<br>1×1×2×2 Array{Int64,4}:<br>[:, :, 1, 1] =<br>&nbsp;10<br>[:, :, 2, 1] =<br>&nbsp;26<br>[:, :, 1, 2] =<br>&nbsp;42<br>[:, :, 2, 2] =<br>&nbsp;58</strong>`

The function applies the `<strong>sum</strong>` function on the first 2 dimensions of the array and reports the result.

# 

So far we observed arrays have two distinct operations. First, it provides a container for the storage of data and second, it provides various methods to access and modify the data. Iteration, indexing, and slicing can be considered as various access methods for the data. The concrete types like `<strong>Array{T,N}</strong>` fulfil both needs but are rigid in storage requirements. For example, a matrix with only diagonal elements will require only `<strong>N</strong>` elements to store the data. A tri-diagonal matrix, whose diagonal and previous and next parallel to diagonal elements are defined requires only `<strong>3N-2</strong>` elements to store the data. Using an `<strong>Array{T,2}</strong>` or Matrix to store such data will be wasteful considering `<strong>N*N</strong>` storage will be required. `<strong>AbstractArray{T,N}</strong>` is an interface to address such needs. The following are some of the functionalities that are expected to be implemented by derived types such that they work seamlessly with other array types.

1.  A `<strong>size</strong>` interface to provide the size of the array in all dimensions defined for it.
2.  Indexing interfaces `<strong>getindex</strong>` and `<strong>setindex!</strong>` to access and modify data of the array.
3.  Iterator interfaces for the array to behave like a collection.
4.  A similar interface to convert from specialized array to equivalent `<strong>Array{T,N}</strong>` type as and when required.
5.  Lastly, an axes method to support non-standard indexing like index starting at 0 instead of 1 and so on.

While we suggest the reader to go through the Julia documentation[1](#zfp2b22u.html#n4upl4fndgb) to get a complete understanding of the concept, we show some of the implementations using a sample code for an easier understanding.

**Note:** `<strong>AbstractVector{T}</strong>` **and** `<strong>AbstractMatrix{T}</strong>` **are aliases for** `<strong>AbstractArray{T,1}</strong>` **and** `<strong>AbstractArray{T,2}</strong>` **respectively.**

We implement an identity matrix. Identity matrices have diagonal elements defined as 1 and all other elements as 0s. Since, they have fixed patterns, `<strong>setindex!</strong>` method is not required.

`<strong>struct MyIdentity{T} &lt;: AbstractMatrix{T}</strong>`

`<strong>l::Int</strong>`

`<strong>end</strong>`

`<strong>Base.size(m::MyIdentity)=(m.l, m.l)</strong>`

`<strong>Base.size(m::MyIdentity, d)=(d == 1 || d == 2) ? m.l :</strong>`

`<strong>error("Invalid dimensions")</strong>`

`<strong>function Base.getindex(m::MyIdentity{T}, i, j) where {T}</strong>`

`<strong>1 &lt;= i &lt;= m.l &amp;&amp; 1 &lt;= j &lt;= m.l || error("Invalid indices")</strong>`

`<strong>i == j &amp;&amp; return one(T)</strong>`

`<strong>return zero(T)</strong>`

`<strong>end</strong>`

Just this simple definition can deliver an elaborate identity matrix with almost all necessary functionalities.

`<strong>julia&gt; a = MyIdentity{Int}(3)<br>3×3 MyIdentity{Int64}:</strong>`

`<strong>&nbsp;1&nbsp;&nbsp;0&nbsp;&nbsp;0<br>&nbsp;0&nbsp;&nbsp;1&nbsp;&nbsp;0<br>&nbsp;0&nbsp;&nbsp;0&nbsp;&nbsp;1<br>julia&gt; a[2, 1]<br>0<br>julia&gt; a = MyIdentity{Float32}(3)<br>3×3 MyIdentity{Float32}:<br>&nbsp;1.0&nbsp;&nbsp;0.0&nbsp;&nbsp;0.0<br>&nbsp;0.0&nbsp;&nbsp;1.0&nbsp;&nbsp;0.0<br>&nbsp;0.0&nbsp;&nbsp;0.0&nbsp;&nbsp;1.0<br>julia&gt; size(a)<br>(3, 3)<br>julia&gt; size(a, 2)<br>3</strong>`

`<strong>julia&gt; length(a)<br>9</strong>`

Just defining `<strong>size</strong>` and `<strong>getindex</strong>` method takes care of defining most of the behavior of the matrix. This is due to the defaults defined in the Julia base. Now if we multiply a vector is multiplied with the `<strong>MyIdentity{T}</strong>` matrix, we should get the same vector.

`<strong>julia&gt; a[5] # Linear Indexing<br>1.0f0</strong>`

`<strong>julia&gt; a*[1,2,3]<br>3-element Vector{Float32}:</strong>`

`<strong>&nbsp;1.0</strong>`

`<strong>&nbsp;2.0</strong>`

`<strong>&nbsp;3.0</strong>`

# 

Sparse arrays are an extension of the `<strong>AbstractArray</strong>` concept we discussed earlier. The essence of sparse array is to reduce the overall storage needed for the array. In many numerical applications, the most values in any random row and column combination can be 0s, while a non-zero value appears only in certain locations. For example, the diagonal matrices have data only on the diagonal elements. Sparse arrays go a step further and allow value to be stored in a vector and one or more index vectors storing the location of the value[2](#zfp2b22u.html#n4upl4fndgc).

**Note: Sparse arrays are part of the module** `<strong>SparseArrays</strong>` **in the** `<strong>stdlib</strong>` **of Julia. Make sure to import the symbols by the command** `<strong>using</strong>` `<strong>SparseArrays</strong>` **before using any of the types or methods related to sparse arrays. We will discuss about modules in details in a later chapter.**

# 

`<strong>using SparseArrays</strong>`

`<strong>struct SparseVector{Tv,Ti&lt;:Integer} &lt;:</strong>`

`<strong>AbstractSparseVector{Tv,Ti}</strong>`

`<strong>n::Int&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;# Length of the sparse vector</strong>`

`<strong>nzind::Vector{Ti}&nbsp;&nbsp; # Indices of stored values</strong>`

`<strong>nzval::Vector{Tv}&nbsp;&nbsp; # Stored values, typically nonzeros</strong>`

`<strong>end</strong>`

`<strong>nzval</strong>` is the storage vector for all the non-zero values and `<strong>nzind</strong>` is the index location of the values where `<strong>n</strong>` is the length of the sparse vector.

`<strong>Julia&gt; using SparseArrays</strong>`

`<strong>julia&gt; I = [1, 4, 3, 5]; V = [1, 2, -5, 3];</strong>`

`<strong>julia&gt; R = sparsevec(I,V)</strong>`

`<strong>5-element SparseVector{Int64,Int64} with 4 stored entries:</strong>`

`<strong>&nbsp;&nbsp;[1]&nbsp;&nbsp;=&nbsp;&nbsp;1</strong>`

`<strong>&nbsp;&nbsp;[3]&nbsp;&nbsp;=&nbsp;&nbsp;-5</strong>`

`<strong>&nbsp;&nbsp;[4]&nbsp;&nbsp;=&nbsp;&nbsp;2</strong>`

`<strong>&nbsp;&nbsp;[5]&nbsp;&nbsp;=&nbsp;&nbsp;3</strong>`

A 5-element vector is created as the maximum value of the index was 5 in the `<strong>I</strong>` vector. Members of vector `<strong>R</strong>` can be accessed like a normal vector.

`<strong>julia&gt; R[2]</strong>`

`<strong>0</strong>`

`<strong>findnz</strong>` method provides all index locations where non-zero values are stored. Essentially, given a sparse vector or matrix it reports the `<strong>nzind</strong>` and `<strong>nzval</strong>` vectors.

`<strong>julia&gt; findnz(R)</strong>`

`<strong>([1, 3, 4, 5], [1, -5, 2, 3])</strong>`

# 

Taking the concept of the sparse vector a step further, one can store a matrix adding a vector for the second dimension. However, for better storage management the following approach is typically used.

1.  Column indices are stored in a vector in an increasing order.
2.  Rows are stored in a second vector, and in increasing order when there is a clash in the column indices.
3.  Values are stored in a separate vector defined for the same.

This concept is called `<strong>compressed sparse column</strong>` (`<strong>CSC</strong>`). While the format is highly storage efficient, it is not insertion or modification friendly as any insertion may need all the values in the vectors to be shifted to the right.

`<strong>struct SparseMatrixCSC{Tv,Ti&lt;:Integer} &lt;:</strong>`

`<strong>AbstractSparseMatrix{Tv,Ti}</strong>`

`<strong>m::Int&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;# Number of rows</strong>`

`<strong>n::Int&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;# Number of columns</strong>`

`<strong>colptr::Vector{Ti}&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;# Column j is in</strong>`

`<strong>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;#&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;colptr[j]:(colptr[j+1]-1)</strong>`

`<strong>rowval::Vector{Ti}&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;# Row indices of stored values</strong>`

`<strong>nzval::Vector{Tv}&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; # Stored values, typically nonzeros</strong>`

`<strong>end</strong>`

`<strong>julia&gt; I = [1, 4, 3, 5]; J = [4, 7, 18, 9]; V = [1, 2, -5, 3];</strong>`

`<strong>julia&gt; S = sparse(I, J, V)</strong>`

`<strong>5×18 SparseMatrixCSC{Int64, Int64} with 4 stored entries:</strong>`

`<strong>⠀⠈⠀⡀⠀⠀⠀⠀⠠</strong>`

`<strong>⠀⠀⠀⠀⠁⠀⠀⠀⠀julia&gt; findnz(S)</strong>`

`<strong>([1, 4, 5, 3], [4, 7, 9, 18], [1, 2, 3, -5])</strong>`

`<strong>julia&gt; S[1, 2]</strong>`

`<strong>0</strong>`

`<strong>julia&gt; size(S)</strong>`

`<strong>(5, 18)</strong>`

Just like the sparse vector examples, `<strong>SparseMatrixCSC</strong>` has similar functions to create, access, and manipulate the matrices. We will leave the details of using these data structures to the reader and suggest an understanding of the language documentation for the same in the interest of space and complexities they can add.

# 

While sparse data structures are good for storage, they may not be the best for indexing and iterations. Be very cautious of data access complexities while using these structures. Even simple index access may need to scan a good portion of the index and data vectors. While incremental access of non-zero values for iterations may be efficient, random access for a specific index may not be as efficient.

# 

While most of the concepts we reviewed so far were representational aspects of arrays, vectors, and matrices, this section is about the application of the same in addressing mathematical and scientific computing. The Julia linear algebra functionalities are aggregated into a module called `<strong>LinearAlgebra</strong>` under the `<strong>stdlib</strong>`. So before using the methods and data structures you will need to use the following statement.

`using LinearAlgebra`

Julia linear algebra module can be thought of as 3 distinct parts.

1.  Basic matrix and vector operations native to Julia
2.  LAPACK functions
3.  BLAS functions

The basic module contains matrix operations like, transpose (`<strong>tr</strong>`), inverse (`<strong>inv</strong>`), dot product (`<strong>dot</strong>`), and so on. There are further methods like single-valued decomposition (`<strong>svd</strong>`), lower and upper triangular decomposition, etc. An eigen module that provides eigen value computation of various matrix types. We will not delve deeper into these concepts here. However, we suggest the readers to look into the language documentation[3](#zfp2b22u.html#n4upl4fndgd). We will look into some of the methods in later chapters selectively as we need them.

# 

Being a scientific programming language for the research community, Julia provides advanced array, vectors, and matrix representations and methods. We looked into some of the concepts here and introduced the existence of some of the advanced topics. While arrays are one of the key data structures of Julia, strings are an equally important aspect to programming. We will look at strings next chapter that will help us understand text handling better.

# 

1.  Implement a binary heap using a `<strong>Vector</strong>`.
2.  How the array indexes are translated in View types created through `<strong>@view</strong>` macro? Is it possible to have an array where some of the indices in a particular dimension are invalid?
3.  Create a `<strong>MyTridiagonal</strong>` matrix using `<strong>AbstractMatrix</strong>` interface and broadcast add (+) operation with a row matrix of the size of one of its dimensions.
4.  If you were to represent a diagonal matrix, should you use the `<strong>SparseMatrixCSC</strong>`? Why will it not be a good idea to do so?
5.  Does Julia provide any linear algebraic methods for LU decomposition of a Matrix? If so, showcase the application of the same using an example.

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

[1](#zfp2b22u.html#n4upl4fndge) Abstract Arrays Interface, Julia Documentation, **[https://docs.julialang.org/en/v1/manual/interfaces/#man-interface-array](https://docs.julialang.org/en/v1/manual/interfaces/#man-interface-array)**

[2](#zfp2b22u.html#n4upl4fndgf) Sparse Arrays, Julia Documentation, **[https://docs.julialang.org/en/v1/stdlib/SparseArrays/#Sparse-Arrays](https://docs.julialang.org/en/v1/stdlib/SparseArrays/#Sparse-Arrays)**

[3](#zfp2b22u.html#n4upl4fndgg) Linear Algebra, Julia Language Documentation, **[https://docs.julialang.org/en/v1/stdlib/LinearAlgebra/](https://docs.julialang.org/en/v1/stdlib/LinearAlgebra/)**

Sparse arrays are an extension of the `<strong>AbstractArray</strong>` concept we discussed earlier. The essence of sparse array is to reduce the overall storage needed for the array. In many numerical applications, the most values in any random row and column combination can be 0s, while a non-zero value appears only in certain locations. For example, the diagonal matrices have data only on the diagonal elements. Sparse arrays go a step further and allow value to be stored in a vector and one or more index vectors storing the location of the value2.

The basic module contains matrix operations like, transpose (`<strong>tr</strong>`), inverse (`<strong>inv</strong>`), dot product (`<strong>dot</strong>`), and so on. There are further methods like single-valued decomposition (`<strong>svd</strong>`), lower and upper triangular decomposition, etc. An eigen module that provides eigen value computation of various matrix types. We will not delve deeper into these concepts here. However, we suggest the readers to look into the language documentation3. We will look into some of the methods in later chapters selectively as we need them.

While we suggest the reader to go through the Julia documentation1 to get a complete understanding of the concept, we show some of the implementations using a sample code for an easier understanding.

Linear Algebra, Julia Language Documentation, **[https://docs.julialang.org/en/v1/stdlib/LinearAlgebra/](https://docs.julialang.org/en/v1/stdlib/LinearAlgebra/)**

Abstract Arrays Interface, Julia Documentation, **[https://docs.julialang.org/en/v1/manual/interfaces/#man-interface-array](https://docs.julialang.org/en/v1/manual/interfaces/#man-interface-array)**

Sparse Arrays, Julia Documentation, **[https://docs.julialang.org/en/v1/stdlib/SparseArrays/#Sparse-Arrays](https://docs.julialang.org/en/v1/stdlib/SparseArrays/#Sparse-Arrays)**

# 

# 

# 

Text is one of the commonest data types used in computation today. Text can represent a specific expression in a specific natural language like a sentence in English, a binary dump of arbitrary characters like a binary array of bytes, multi-lingual representation of expressions where a sentence may contain words from another language. We shall review how text is represented in Julia.

# 

In this chapter, we will cover the following topics:

*   Background
*   String
*   String methods
*   Encodings
*   Character array
*   Custom strings

# 

The readers will be able to understand the abstract data types associated with strings, so that they can design their own string types. They will learn the access and transformation schemes associated with strings including accessing substrings. They will learn about search, regular expressions, concatenations, and other operations common to strings. The knowledge of encodings will help the reader in multilingual and complex string types.

# 

A sentence may contain symbols and characters from multiple languages. For example, mathematical symbols and expressions in Greek can be used in an English sentence. Lastly, the text is often used as the representation of the last resort for entities for which there may not be an alternate expression as in the case of textual keywords. Although Julia symbols are pretty likely candidates for the last scenario, the text is used for many such cases as well[1](#5ozsl153.html#n4upl4fndkx). In this chapter, we will try to delve in some details into all the aspects discussed previously. The versatility of text usage brings many representational challenges and we must conceptually understand the design of the Julia language. While the structure of text can get to complexities of document structures and representations we will keep the scope of the discussion to the concept of strings.

# 

Strings are a collection of characters that act as a text representation. While they can be meaningful sentences in a specific language, they can be completely meaningless collection of characters.

*This is a valid sentence.*

*Abccnajkvnkavnak*

Both preceding lines represent valid strings but they are all not valid sentences in English.

# 

A collection of characters makes a string. In the preceding example:

\[' ', 'T', 'a', 'c', 'd', 'e', 'h', 'i', 'l', 'n', 's', 't', 'v'\] characters make the sentence *This is a valid sentence.*

The order and placement of the characters in a collection are important as well.

# 

The character as written has no meaning for a computer. In a computer, every entity is represented as a mathematical value or a binary equivalent of a number. Such a number is called the **encoding**. In a computer that utilizes **American Standard Code for Information Interchange** (**ASCII**) as the encoding scheme, the character **a** is represented as the code value 97 or 0x61. ASCII is only one of the representations of an encoding that can represent the character set of the English language. Another one is Extended **Binary Coded Decimal Interchange Code** (**EBCDIC**). This one used to be preferred in IBM mainframes but not popular any longer. We will discuss about a few encodings for a conceptual understanding here before we start working on Julia language constructs for text - A bit of theoretical understanding before we dive into some concrete coding. This introduction may deviate from chronological accuracies as developing an intuitive understanding is the main focus here.

# 

7-bit character notation with a goal to represent all printable characters in English and also a few non-printable characters used for inter-device communication like serial or parallel communication channels. ASCII is designed in a manner such that the upper case and lower-case alphabets are grouped within specific ranges; similarly, all numbers are grouped within a range. This makes programming and identifying characters with ease. This was something that EBCDIC lacked. By the same time bytes had become the computation unit in the microprocessors and that left 1-bit free to fit in additional 128 characters. **American National Standard Institute** (**ANSI**) considered commonly used additional non-English characters and tried to fit 128 of them as an ANSI character code. Operating system vendors like Microsoft and Apple came up with their own character encodings like Windows-1252 encoding or Mac Roman Encoding, and so on. They all essentially supported the general ASCII specification of character codes from 0 to 127 but added a unique character set for each of the character codes from 128 to 255 for their own conveniences. That led to an encoding war of sorts while displaying and translating documents across various operating systems and devices. The industry started using the term *upper ASCII or extended ASCII* which essentially is the character code 128–255 that changed from standard to standard.

# 

The ISO-8859 is a set of encodings with a character defined for code sections 1–15, each representing a class of European languages that can be represented together - sometimes also called as Latin-1, Latin-2 encodings. All such code pages have 0–127 support the basic ASCII characters, while 128–255 may support a special class of European regional languages like Cyrillic, Baltic, etc. This kind of arrangement ensured the European languages are supported in the computer with ease. Typically, a multi-language document or screen would use some form of code page switch command and switch the character encoding to be picked up from the new code page. The advantage of course remained that all strings can be represented as a binary dump of 8-bit values.

# 

‘C’ Language that was introduced in the late 1970s used a very simple paradigm for text. Any binary 8-bit byte array is a string. The last byte of the array must terminate with the character code (0) or NULL. Called as NULL terminated strings or c-strings, this concept ensured that the code interpretation is kept outside of the string manipulations. The C language per se implements all string methods completely disregarding the encoding interpretation inside the language and expects programmers to handle it in the application or system they are developing. For a lack of better term, some computer systems like GNU Linux call it as the C encoding. In some systems like UNIX, C encoding is the default encoding of the system.

# 

As adoptions of computers became prevalent, it got clearer that computing cannot be kept confined to a specific region any longer. Second, data interchange also required the data be able to be presented in any computational system available. Third, the memory that was needed to represent text could be increased beyond one byte as both storage and RAM available in a computer had got cheaper. A single-byte restriction on characters was not needed. A group of computer scientists and linguists from various organizations and academics came together under an organization Unicode Consortium and introduced a **Universal Coded Character Set** (**UCS**). The first set of characters introduced in 1991 had about 7000 characters represented by a 2-byte character representation called UCS-2. However, very soon the characters started to grow as more languages were added to the specification. And, it was decided to take up 4 bytes for each character in a representation called UCS-4. In reality, the Unicode specification defines 16 planes of codes each of 65536 (216) size, where only few values are actually used. Technically, only 20 bits of the 32-bits are really used for practical purposes. However, many computer systems went on to implement wide character in the operating systems, Windows developed a native 16-bit operating system with Windows NT and discontinued the older Windows 95 code base. The code needed to be compiled for 8-bit and 16-bit versions separately by using macros in the late 90s and early parts of the millennia.

# 

One part of the world was busy rewriting operating system cores to support wide characters. Even some UNIX-derived systems have wide characters implemented as 4 bytes as well. Ken Thompson came up with this novel idea of reusing the C-encoding as the basis for Unicode characters. But, C-encoding or c-strings could not be used as the UCS-2 and UCS-4 has whole bytes of data to be set as NULL. And that would make the character unsuitable for c-strings as for the C language the string termination character was defined to be 0. For example, the UCS-2 code character ‘a’ will be U+0061 that has a leading byte of 0.

He wanted the Unicode characters to be represented in a manner such that:

1.  ASCII character shall remain valid in the new encoding that means no transformation must be carried out to any character in the range of 0x00-0x7F.
2.  For any character that has a value of 128 or higher must be represented by a multi-byte character.
3.  The new encoding must have a leading byte telling how many bytes to read subsequently.
4.  In case of an ambiguity, the code that is represented with the least number of bytes shall be chosen.
5.  The patterns used for the leading and trailing bytes must be such that if there is any violation of the same it will be easy to identify the character sequence is corrupt, helping in easier transfer over wire even without any redundancy checks like CRC.
6.  This scheme ensured other than the actual NUL character no other character can have a byte that is all zeros.

Here is how the scheme finally looked like:

![](n4upl4fndq2.jpeg)

**Figure 7.1:** UTF-8 Representation of the Unicode Characters

The preceding representation is called as **UTF-8**. What about encodings beyond 21-bits? So far Unicode specification does not utilize more than 21-bits of information but the scheme can accommodate up to 36-bits of information covering the whole UCS-4 range. Similar to UTF-8, UTF-16 has been introduced as well that considers character codes to be extended to 2-bytes of characters at a time. There is also UTF-32 transformation scheme as well.

# 

Julia has native support for Unicode in the language. Even variables and constant can use Unicode characters in them. Internally, Julia Strings (`<strong>String</strong>` type) are stored as Unicode character streams in UTF-8 encoding. Even the characters (`<strong>Char</strong>`) in Julia are represented as up to 4-byte values in the UTF-8 encoding. Raw bytes are represented as `<strong>UInt8</strong>` are not `<strong>Char</strong>` in Julia. However, as a language Julia supports constructs to represent strings in other encodings of choice. One can also develop her own character codes and strings using the Julia interfaces. You may need to exchange information with native C/C++ applications and that may require string information to be interchanged as a `<strong>Cstring</strong>` from Julia code. `<strong>Cstring</strong>` is a zero terminated string as expected in the C language.

# 

Let us look at the representation of a in various fonts:

![](n4upl4fndq3.jpeg)

**Figure 7.2:** Character'a' written with glyphs from various fonts

The font and glyphs provide the visual look and feel of a character. As a programming language, Julia does not provide any mechanism for controlling fonts or glyph selection. These are typically in the realm of a word processing or rendering software like Microsoft Word, Adobe InDesign, and so on.

Now that we understand the aspects of text computation, let us try to evaluate how Julia addresses the needs.

# 

In Julia, `<strong>String</strong>` objects can be initialized with the following literals expressions.

`<strong>julia&gt; str = "This is a string"<br>"This is a string"</strong>`

Strings are immutable. Once created, they cannot be modified. Here is another way to define strings where the formatting and new line characters are preserved. No additional quoting is required for special characters.

`<strong>julia&gt; str = """</strong>`

`<strong>This is a preformatted</strong>`

`<strong>"string" """</strong>`

`<strong>" \nThis is a preformatted \n\"string\" "</strong>`

Strings can have information computed in other variables and included for computation of final output.

`<strong>julia&gt;a = "Jack";</strong>`

`<strong>julia&gt;b = "Jill";</strong>`

`<strong>Julia&gt;c = "100";</strong>`

`<strong>julia&gt;str = "$a owes $b $c dollars"<br>"Jack owes Jill 100 dollars"</strong>`

Special characters used in a string like quotes(“) or backslash(\\) needs to be escaped with a backslash(\\).

`<strong>julia&gt;str = "This is a \"quoted\\&nbsp;&nbsp;' string"</strong>`

`<strong>"This is a \"quoted\\&nbsp;&nbsp;' string"</strong>`

Let us look at various methods to interact with the strings in the next section.

**Note: Strings are immutable. Hence, they can reside in the system memory without being overwritten even when garbage is collected. A memory debugger can be used to read random memory locations. If you have sensitive data like passwords, you should consider using a byte or character array structure and overwrite the memory location once the data is consumed. Dereferencing the memory object and forcibly calling garbage collection may not be the most secure option.**

# 

We shall review some of the standard methods on strings.

# 

String objects can be compared amongst themselves using the standard comparison operators `<strong>isequal(==)</strong>`, `<strong>isless(&lt;)</strong>` or greater than (>). The dictionary ordering is typically used for comparisons.

`<strong>julia&gt; s1 = "abc"</strong>`

`<strong>julia&gt; s2 = "def"</strong>`

`<strong>julia&gt; s1 &lt; s2<br>true</strong>`

`<strong>julia&gt; s2 &gt; s1<br>true<br>julia&gt; s1 = "abc"</strong>`

`<strong>julia&gt; s2 = "abc"</strong>`

`<strong>julia&gt; s1 == s2<br>true</strong>`

‘egal’ operator (`<strong>===</strong>`) that compares across objects, for immutable String objects, shall compare bitwise.

`<strong>julia&gt; s1 === s2</strong>`

`<strong>true</strong>`

# 

Just like arrays and collections, strings are also natural collections of the sequence of characters. So it is expected when you iterate over a String, you will be able to enumerate the characters.

`<strong>julia&gt; s = "Julia";</strong>`

`<strong>julia&gt; for c in s</strong>`

`<strong>println(c)</strong>`

`<strong>end</strong>`

`<strong>J</strong>`

`<strong>u</strong>`

`<strong>l</strong>`

`<strong>i</strong>`

`<strong>a</strong>`

Just like other collections, Julia strings also support 1-based indexing and present characters at every location.

`<strong>julia&gt; s[1], s[2], s[3], s[4], s[5]<br>('J', 'u', 'l', 'i', 'a')</strong>`

`<strong>begin</strong>` and `<strong>end</strong>` can be used very much like used with other types of collections as well.

`<strong>julia&gt; s[begin], s[begin+2], s[end-1], s[end]<br>('J', 'l', 'i', 'a')</strong>`

Let us take a string with multi-byte UTF-8 characters in them.

`<strong>julia&gt; s = "\u2200 x \u2203 y"<br>"∀ x ∃ y"<br>julia&gt; length(s)&nbsp;&nbsp; # No of characters in the String<br>7<br>julia&gt; sizeof(s)&nbsp;&nbsp; # No of bytes in the String</strong>`

`<strong>11</strong>`

`<strong>julia&gt; s[1]<br>'∀': Unicode U+2200 (category Sm: Symbol, math)</strong>`

`<strong>julia&gt; s[2]<br>StringIndexError("∀ x ∃ y", 2)</strong>`

`<strong>Stacktrace:</strong>`

`<strong>&nbsp;[1] string_index_err(::String, ::Int64) at .\strings\string.jl:12</strong>`

`<strong>&nbsp;[2] getindex_continued(::String, ::Int64, ::UInt32) at .\strings\string.jl:220<br>…</strong>`

`<strong>julia&gt; s[4]<br>' ': ASCII/Unicode U+0020 (category Zs: Separator, space)</strong>`

So, `<strong>getindex</strong>` method takes the byte index as input and returns a valid character. However, when the index does not map to a valid character an exception is thrown as the case in `<strong>s[2]</strong>`. However, the `<strong>for…in</strong>` the loop works iterating over the characters.

`<strong>julia&gt; for c in s</strong>`

`<strong>println(c)</strong>`

`<strong>end<br>∀</strong>`

`<strong>x</strong>`

`<strong>∃</strong>`

`<strong>y</strong>`

An alternate approach using index variable is with method `<strong>nextind()</strong>`. The method shall return the next index that has a valid character.

`<strong>julia&gt; i, l = firstindex(s), lastindex(s);</strong>`

`<strong>julia&gt; while i &lt;= l</strong>`

`<strong>println(s[i])</strong>`

`<strong>i = nextind(s, i)</strong>`

`<strong>end<br>∀</strong>`

`<strong>x</strong>`

`<strong>∃</strong>`

`<strong>y</strong>`

# 

One of the simplest ways to split a string into substring is by using indexing and concatenation with operator (\*).

`<strong>julia&gt; str = "This is a String"</strong>`

`<strong>julia&gt; str[1:4]</strong>`

`<strong>"This"<br>julia&gt; str[1:4]*str[end-6:end]</strong>`

`<strong>"This String"</strong>`

*   Since strings are immutable, every substring or concatenation operation shall allocate intermediate strings before they are concatenated. A repeated sequence of a text pattern can be created using `<strong>repeat</strong>` function or the alias operator (^).
    
    `<strong>julia&gt; repeat("A:-", 5)<br>"A:-A:-A:-A:-A:-"</strong>`
    
    `<strong>julia&gt; "A:="^4<br>"A:=A:=A:=A:="</strong>`
    
*   `<strong>join()</strong>` combines an input collection of strings. One can optionally provide a delimiter like a comma (,) and a last joining word like an `and’.
    
    `<strong>julia&gt; join(["1", "2", "3", "4", "5"])</strong>`
    
    `<strong>"12345"</strong>`
    
    `<strong>Julia&gt; join(["Jack", "Jill", "Cathy", "Trevor"], ", ", " and ")</strong>`
    
    `<strong>"Jack, Jill, Cathy and Trevor"</strong>`
    
*   `<strong>chomp()</strong>` removes the last end-of-line character in a string.
    
    `<strong>julia&gt; str = "This is a\nString\n"</strong>`
    
    `<strong>Julia&gt; chomp(str)</strong>`
    
    `<strong>"This is a\nString"</strong>`
    
*   `<strong>chop()</strong>` removes characters from head and tail. By default, no character is chopped from the head and only one character is chopped off from the tail. However, keyword head and tail can be used to specify specific number of characters to be chopped off from head and tail respectively.
    
    `<strong>julia&gt; chop("October")<br>"Octobe"</strong>`
    
    `<strong>Julia&gt; chop("October", head=2, tail=3)<br>"to"</strong>`
    
*   `<strong>split()</strong>` method breaks up a `<strong>String</strong>` along the space characters and returns an array of `<strong>SubString</strong>` objects.
    
    `<strong>julia&gt; s = "\u2200 x \u2203 y"</strong>`
    
    `<strong>julia&gt; ss = split(s)<br>4-element Array{SubString{String},1}:</strong>`
    
    `<strong>&nbsp;"∀"</strong>`
    
    `<strong>&nbsp;"x"</strong>`
    
    `<strong>&nbsp;"∃"</strong>`
    
    `<strong>&nbsp;"y"</strong>`
    
*   `<strong>String</strong>` objects are immutable and any expression that extracts a part of a string, allocates a new `<strong>String</strong>`. `<strong>SubString</strong>` is a view into a `<strong>String</strong>` object. In the preceding example all the split `<strong>SubString</strong>` objects in the array point to the same `<strong>String</strong>` object. A `<strong>SubString</strong>` object extends the `<strong>AbstractString</strong>` interface, hence can be used to convert to a `<strong>String</strong>` object when required. `<strong>split()</strong>` method supports delimiters as well.
    
    `<strong>julia&gt; s = "\u2200,x,\u2203,y"</strong>`
    
    `<strong>julia&gt; ss = split(s, ',', limit=2)<br>2-element Array{SubString{String},1}:</strong>`
    
    `<strong>&nbsp;"∀"</strong>`
    
    `<strong>&nbsp;"x,∃,y"<br><br>julia&gt; s = "\u2200,x,\u2203,y"</strong>`
    
    `<strong>Julia&gt; ss = rsplit(s, ',', limit=2)<br>2-element Array{SubString{String},1}:</strong>`
    
    `<strong>&nbsp;"∀,x,∃"</strong>`
    
    `<strong>&nbsp;"y"</strong>`
    
    `<strong>split()</strong>` example uses comma (,) as a delimiter and limits the number of split parts to 2. Very similar to `<strong>split</strong>` that splits the string from the left, `<strong>rsplit</strong>` splits the string from the right.
    
*   `<strong>lpad</strong>` and `<strong>rpad</strong>` add a prefix or suffix to a string and brings it to a specific length.
    
    `<strong>julia&gt; lpad("string", 10, "p")</strong>`
    
    `<strong>"ppppstring"<br>julia&gt; rpad("string", 10, "s")<br>"stringssss"</strong>`
    
*   `<strong>strip</strong>` function removes the space characters from both sides of the string. A method of the same function can selectively take an array of characters to be removed from both ends. A predicate evaluates to true can be used to strip at both ends as well. `<strong>lstrip</strong>` and `<strong>rstrip</strong>` are two functions that work similar to strip but only works on the left and right ends of the string respectively.
    
    `<strong>julia&gt; strip("&nbsp;&nbsp;&nbsp;&nbsp; string 123&nbsp;&nbsp;")</strong>`
    
    `<strong>"string 123"</strong>`
    
    `<strong>julia&gt; strip(" {a}&nbsp;&nbsp;&nbsp;&nbsp; string 123&nbsp;&nbsp;", ['{', 'a', '}', ' '])</strong>`
    
    `<strong>"string 123"</strong>`
    
    `<strong>julia&gt; strip("&nbsp;&nbsp;&nbsp;&nbsp; string 123&nbsp;&nbsp;aaa") do x</strong>`
    
    `<strong>&nbsp;&nbsp;&nbsp;&nbsp;return x == ' ' || x == 'a'</strong>`
    
    `<strong>end</strong>`
    
    `<strong>"string 123"</strong>`
    

# 

Some functions in line with their expected outcomes:

`<strong>julia&gt; uppercase("Julia")</strong>`

`<strong>"JULIA"</strong>`

`<strong>julia&gt; lowercase("JUliA")</strong>`

`<strong>"julia"</strong>`

`<strong>julia&gt; titlecase("hands on programming in julia")</strong>`

`<strong>"Hands On Programming In Julia"</strong>`

`<strong>julia&gt; uppercasefirst("julia")</strong>`

`<strong>"Julia"</strong>`

`<strong>julia&gt; lowercasefirst("Julia")</strong>`

`<strong>"julia"</strong>`

# 

Pattern matching functions can be classified into various categories. A few of them are given as follows:

*   `<strong>startswith()</strong>`, `<strong>endswith()</strong>` and `<strong>contains()</strong>` search a part of a string in the beginning, end and anywhere in the string and return if they are present in the string. `<strong>occursin(needle, haystack)</strong>` is another form for `<strong>contains(haystack, needle)</strong>`.
    
    `<strong>julia&gt; str = "Introduction to Julia";</strong>`
    
    `<strong>julia&gt; startswith(str, "Intro")</strong>`
    
    `<strong>true<br>julia&gt; endswith(str, "Julia")<br>true<br>julia&gt; contains(str, "to")<br>true</strong>`
    
    `<strong>julia&gt; occursin("to", str)<br>true</strong>`
    
*   `<strong>findfirst</strong>` and `<strong>findnext</strong>` assist in searching for a sequence of patterns along the `<strong>String</strong>` object. `<strong>findlast</strong>` provides the last occurrence of the pattern.
    
    `<strong>julia&gt; r = findfirst("o", "Introduction to Julia");</strong>`
    
    `<strong>julia&gt; while r !== nothing</strong>`
    
    `<strong>println(r)</strong>`
    
    `<strong>r = findnext("o", "Introduction to Julia", r.stop+1)</strong>`
    
    `<strong>end<br>5:5</strong>`
    
    `<strong>11:11</strong>`
    
    `<strong>15:15</strong>`
    
    `<strong>julia&gt; findlast("o", "Introduction to Julia")<br>15:15</strong>`
    
*   `<strong>replace</strong>` changes a searched input pattern to another text of choice.
    
    `<strong>julia&gt; replace("Introduction to Julia", "o"=&gt;"a")</strong>`
    
    `<strong>"Intraductian ta Julia"</strong>`
    

# 

Regular expressions are a pattern matching language construct that enables computer programmers to define complex patterns that can be matched to text strings. These patterns are used substantially in compiler designs and tokenizers, and so on. A few commonly used applications for UNIX that are used for pattern matching with regular expressions (regex) are `<strong>lex</strong>`, `<strong>grep</strong>`, and `<strong>egrep</strong>`. Programming languages like PERL, Python, and R, and so on also provide extended regex syntax support than the standard ones supported by `<strong>grep</strong>`. **PERL Compatible Regular Expressions** (**PCRE**) library[2](#5ozsl153.html#n4upl4fndky) is integrated into Julia. Hence, Julia’s support for regex is as capable as it is with any of the other languages. While we showcase here some examples of regex, this is not a section dedicated to all nuances of regex. We will request the reader to get a good grasp over regex from another authoritative text on the topic.

As can be seen, a `<strong>Regex</strong>` object is created as part of the example. It is matched against a string. The matched is stored in a `<strong>RegexMatch</strong>` object.

`<strong>julia&gt; rx = Regex("a.a")</strong>`

`<strong>r"a.a"<br>julia&gt; m = match(rx, "abracadabra")<br>RegexMatch("aca")<br>julia&gt; m.match</strong>`

`<strong>"aca"</strong>`

An offset match matches to `<strong>“ada”</strong>` instead of `<strong>“aca”</strong>`.

`<strong>julia&gt; m = match(rx, "abracadabra", 5)<br>RegexMatch("ada")</strong>`

In the following example, a `<strong>@r_str</strong>` macro (to be discussed in details in the next chapter) is used to initialize the `<strong>Regex</strong>` object. The `<strong>rx</strong>` object has a capture group defined and matched regular expression can keep the captures in the captures attribute.

`<strong>julia&gt; rx = r"a(.)a";</strong>`

`<strong>julia&gt; m = match(rx, "abracadabra");</strong>`

`<strong>julia&gt; m.captures<br>1-element Array{Union{Nothing, SubString{String}},1}:</strong>`

`<strong>&nbsp;"c"</strong>`

The similar example is now shown with a named capture. The captured data can be collected by indexing the `<strong>RegexMatch</strong>` with the captured group name.

`<strong>julia&gt; rx = Regex("a(?&lt;key&gt;.)a");</strong>`

`<strong>julia&gt; m = match(rx, "abracadabra");</strong>`

`<strong>julia&gt; m.captures<br>1-element Array{Union{Nothing, SubString{String}},1}:</strong>`

`<strong>&nbsp;"c"<br>julia&gt; m["key"]<br>"c"</strong>`

You can match the pattern to several occurrences in a `<strong>String</strong>` as well.

`<strong>julia&gt; rx = r"a.a"</strong>`

`<strong>julia&gt; m = eachmatch(rx, "abracadabra", overlap=true)<br>Base.RegexMatchIterator(r"a.a", "abracadabra", true)</strong>`

`<strong>julia&gt; collect(m)<br>2-element Array{RegexMatch,1}:</strong>`

`<strong>&nbsp;RegexMatch("aca")</strong>`

`<strong>&nbsp;RegexMatch("ada")</strong>`

Both, `<strong>“aca”</strong>` and `<strong>“ada”</strong>` are matched as overlapping strings are allowed. When `<strong>overlap</strong>` parameter is set to `<strong>false</strong>` only `<strong>“aca”</strong>` is matched.

`<strong>julia&gt; m = eachmatch(rx, "abracadabra", overlap=false)</strong>`

`<strong>Base.RegexMatchIterator(r"a.a", "abracadabra", false)<br>julia&gt; collect(m)<br>1-element Array{RegexMatch,1}:</strong>`

`<strong>&nbsp;RegexMatch("aca")</strong>`

Not just `<strong>match</strong>` or `<strong>eachmatch</strong>`, regex matches are also accepted as pattern arguments in functions like `<strong>findfirst</strong>`, `<strong>findnext</strong>`, `<strong>occursin</strong>`, `<strong>replace</strong>`, `<strong>split</strong>`, `<strong>rsplit</strong>`, `<strong>startswith</strong>` and `<strong>endswith</strong>` as well.

# 

`<strong>String</strong>` objects in Julia are essentially Unicode representations. Is there any specific transformation they follow? Can the transformations be set to something else? Some of these questions are natural to a reader’s mind. If you recall the discussion in iterations, the `<strong>nextind()</strong>` method aligns the index to the next UTF-8-character location. This assures that the `<strong>String</strong>` objects are essentially UTF-8 representations. However, you can extract the UTF-8, 16, and 32 array representations through a function transcode.

`<strong>julia&gt; s = "\u2200 x \u2203 y"<br>"∀ x ∃ y"</strong>`

`<strong>julia&gt; transcode(UInt16, s)<br>7-element Array{UInt16,1}:</strong>`

`<strong>&nbsp;0x2200</strong>`

`<strong>&nbsp;0x0020</strong>`

`<strong>&nbsp;0x0078</strong>`

`<strong>&nbsp;0x0020</strong>`

`<strong>&nbsp;0x2203</strong>`

`<strong>&nbsp;0x0020</strong>`

`<strong>&nbsp;0x0079<br>julia&gt; transcode(UInt32, s)<br>7-element Array{UInt32,1}:</strong>`

`<strong>&nbsp;0x00002200</strong>`

`<strong>&nbsp;0x00000020</strong>`

`<strong>&nbsp;0x00000078</strong>`

`<strong>&nbsp;0x00000020</strong>`

`<strong>&nbsp;0x00002203</strong>`

`<strong>&nbsp;0x00000020</strong>`

`<strong>&nbsp;0x00000079</strong>`

`<strong>transcode</strong>` also converts an array of UTF bytes to a `<strong>String</strong>` object.

`<strong>julia&gt; transcode(String, transcode(UInt16, s))</strong>`

`<strong>"∀ x ∃ y"</strong>`

# 

Here are some functions that are fairly intuitive. However, all these methods work on Unicode characters in all languages where the relevance of such a functionality exists and is not just confined to ASCII character set or English characters. This is possible as they utilize the character category definitions from the Unicode tables to ascertain these properties. For example, all the characters that belong to the `<strong>Lu</strong>` or `<strong>Lt</strong>` categories are returned as part of `<strong>isuppercase</strong>` method. Similarly, category `<strong>Zs</strong>` is picked up when `<strong>isspace</strong>` method is queried for a character.

`<strong>julia&gt; isascii("∀ x ∃ y"), isascii("abcd ef")</strong>`

`<strong>(false, true)</strong>`

`<strong>julia&gt; iscntrl('a'), iscntrl('\x1')</strong>`

`<strong>(false, true)</strong>`

`<strong>julia&gt; isdigit(‚a‘), isdigit(‚9‘)</strong>`

`<strong>(false, true)</strong>`

`<strong>julia&gt; isxdigit('a'), isxdigit('x')</strong>`

`<strong>(true, false)</strong>`

`<strong>julia&gt; isletter('1'), isletter('a')</strong>`

`<strong>(false, true)</strong>`

`<strong>julia&gt; isnumeric('1'), isnumeric('௰') #No 10 in Tamil (Indian) Language</strong>`

`<strong>(true, true)</strong>`

`<strong>julia&gt; isuppercase('A'), islowercase('a')</strong>`

`<strong>(true, true)</strong>`

`<strong>julia&gt; isspace('\n'), isspace('\r'), isspace(' '), isspace('\x20')</strong>`

`<strong>(true, true, true, true)</strong>`

As we worked with strings and encodings, we realized some functions provide properties of individual characters. Thus, it is important for us to convert a String into an array of characters. We shall look into that in the next section.

# 

`<strong>String</strong>` objects are collections of characters as we have seen earlier. But, they cannot be modified. You do not get to operate on them as flexibly as you will like to as an array or other container types. However, there are a lot of functions you can use to transform the `<strong>String</strong>` objects and create alternate `<strong>String</strong>` objects. However, if required you can convert a String to a Char Array by simply using the `<strong>collect</strong>` method.

`<strong>julia&gt; collect("∀ x ∃ y")</strong>`

`<strong>7-element Array{Char,1}:</strong>`

`<strong>&nbsp;'∀': Unicode U+2200 (category Sm: Symbol, math)</strong>`

`<strong>&nbsp;' ': ASCII/Unicode U+0020 (category Zs: Separator, space)</strong>`

`<strong>&nbsp;'x': ASCII/Unicode U+0078 (category Ll: Letter, lowercase)</strong>`

`<strong>&nbsp;' ': ASCII/Unicode U+0020 (category Zs: Separator, space)</strong>`

`<strong>&nbsp;'∃': Unicode U+2203 (category Sm: Symbol, math)</strong>`

`<strong>&nbsp;' ': ASCII/Unicode U+0020 (category Zs: Separator, space)</strong>`

`<strong>&nbsp;'y': ASCII/Unicode U+0079 (category Ll: Letter, lowercase)</strong>`

You can also use the `<strong>transcode</strong>` method to obtain UTF-8, 16, 32 transformation vectors of a `<strong>String</strong>` object as shown previously. Once you have an array of `<strong>Char</strong>`, you could use it in any way desired with array operations.

# 

Rome was not built in a day; nor was the Julia String API. While `<strong>String</strong>` remains a UTF-8 representation wrapped inside a collection that delivers `<strong>Char</strong>` objects as `<strong>eltype</strong>`.

`<strong>julia&gt; eltype("abcd")</strong>`

`<strong>Char</strong>`

This architecture was extended further to define an abstract `<strong>AbstractString</strong>` type that would consider `<strong>AbstractChar</strong>` as an element type. Julia in the pre-1.0 incarnations had many such implementations like `<strong>ASCIIString</strong>`, `<strong>UTF8String</strong>`, and so on., which essentially were providing the basis of some of the encoding schemes that are commonly used[3](#5ozsl153.html#n4upl4fndkz). Many classic string types are functionally merged into the `<strong>String</strong>` type and some are moved into an optional package called `<strong>LegacyStrings.jl</strong>`. While there are no significant benefits of using that package, they can be a good source of reference for people interested to try out and implement their own string types. If you are interested in implementing your own string types make sure you have `<strong>AbstractString</strong>` and `<strong>AbstractChar</strong>` interfaces implemented. There are not many requirements for the abstract types save they expect you to have the easier conversion to and from `<strong>String</strong>` and `<strong>Char</strong>` objects respectively if needed.

# 

This interface essentially demands that any derived character should have a Unicode representation value. Similarly, given a valid Unicode value one must be able to create a character.

`<strong>struct MyChar &lt;:&nbsp;&nbsp;AbstractChar end</strong>`

`<strong>MyChar(::UInt32)&nbsp;&nbsp;&nbsp;&nbsp;# returns the MyChar with valid codepoint<br>codepoint(::MyChar) # returns the Unicode value in UInt32</strong>`

The constructor must throw an error if the `<strong>codepoint</strong>` input value is not within the encoding range.

# 

`<strong>AbstractString</strong>` interface is far more elaborate and makes certain assumptions on the internal composition of the string object as well. For example, these interfaces define assumptions on how many minimum bytes you will need to define a character in the string. If you use the `<strong>LegacyStrings</strong>` you will realize `<strong>ASCIIString</strong>` utilizes a `<strong>codeunit</strong>` of a `<strong>UInt8</strong>` while `<strong>UTF16String</strong>` utilizes a `<strong>codeunit</strong>` of `<strong>UInt16</strong>`. But both have a same size of internal data length in the code units.

`<strong>julia&gt;]add LegacyStrings;</strong>`

`<strong>julia&gt; using LegacyStrings;<br>julia&gt; s = ASCIIString("abcd");</strong>`

`<strong>julia&gt; codeunit(s)</strong>`

`<strong>UInt8<br>julia&gt; ncodeunits(s)<br>4<br>julia&gt; s16 = UTF16String(transcode(UInt16, "abcd\0")); # NULL termination<br>julia&gt; codeunit(s16)</strong>`

`<strong>UInt16</strong>`

`<strong>julia&gt; ncodeunits(s16)</strong>`

`<strong>4</strong>`

`<strong>julia&gt; eltype(s), eltype(s16)<br>(Char, Char)</strong>`

**Note: The** `<strong>add</strong>` **and** `<strong>using</strong>` **commands are used in the context of package management and module usage in Julia. We will discuss about them in details when we discuss about package management.**

Although, the `<strong>ASCIIString</strong>` and `<strong>UTF16String</strong>` in the preceding example have completely different internal representations of the stored internal data, they utilize `<strong>Char</strong>` as the iterated `<strong>eltype</strong>`. No additional character types are defined for both these data types.

Other than the aforementioned methods, the derived types of `<strong>AbstractString</strong>` need to implement all the iteration and indexing methods like `<strong>iterate</strong>`, `<strong>getindex</strong>`, `<strong>nextind</strong>`, `<strong>prevind</strong>`, `<strong>lastindex</strong>`, `<strong>firstindex</strong>` and some collections-related methods like length as well[4](#5ozsl153.html#n4upl4fndk0).

# 

Strings are fundamental to many text transformations and analyses in a programming language. We discussed the encodings supported in Julia. How Julia can address various text matching scenarios. We also looked at how to support various custom encodings using abstract types. Packages like `<strong>StringEncodings.jl</strong>` are wrappers around the Unix `<strong>iconv</strong>` libraries that can be used to convert strings from any encoding to the other effortlessly. Next we shall review how meta-programming capabilities of Julia can be utilized to dynamically create code and execute them.

# 

1.  Write a method to validate a sequence of bytes as UTF-8 encoded stream. Make all necessary assumptions needed for the same.
2.  Write a method to match closed brackets to the open brackets in a sentence. What regular expression you can use for the same? Note: Brackets can be nested as well.
3.  Implement a string type that can represent all ISO-8859-1 characters as elements.
4.  Write a method that would match a palindrome string.
5.  Will `<strong>String(“abc”) === String(“abc”)</strong>` return `<strong>true</strong>` or `<strong>false</strong>`? Explain the behavior by looking at the implementation from the Julia Language source repository.

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

[1](#5ozsl153.html#n4upl4fndk1) In Julia, symbols begin with a : character. One can represent keywords in a file with symbols like :key1, :key2, etc. In JSON objects keywords are written as text as well like {“key1”: value1, “key2”: 32,…}.

[2](#5ozsl153.html#n4upl4fndk2) PERL Compatible Regular Expressions, Wikipedia, **[https://en.wikipedia.org/wiki/Perl\_Compatible\_Regular\_Expressions](https://en.wikipedia.org/wiki/Perl_Compatible_Regular_Expressions)**

[3](#5ozsl153.html#n4upl4fndk3) Stringapalooza, Issue 16107, Julia GitHub Repository **[https://github.com/JuliaLang/julia/issues/16107](https://github.com/JuliaLang/julia/issues/16107)**

[4](#5ozsl153.html#n4upl4fndk4) GitHub repository of `ASCIIString` in `LegacyStrings.jl` **[https://github.com/JuliaStrings/LegacyStrings.jl/blob/master/src/ascii.jl](https://github.com/JuliaStrings/LegacyStrings.jl/blob/master/src/ascii.jl)**

Regular expressions are a pattern matching language construct that enables computer programmers to define complex patterns that can be matched to text strings. These patterns are used substantially in compiler designs and tokenizers, and so on. A few commonly used applications for UNIX that are used for pattern matching with regular expressions (regex) are `<strong>lex</strong>`, `<strong>grep</strong>`, and `<strong>egrep</strong>`. Programming languages like PERL, Python, and R, and so on also provide extended regex syntax support than the standard ones supported by `<strong>grep</strong>`. **PERL Compatible Regular Expressions** (**PCRE**) library2 is integrated into Julia. Hence, Julia’s support for regex is as capable as it is with any of the other languages. While we showcase here some examples of regex, this is not a section dedicated to all nuances of regex. We will request the reader to get a good grasp over regex from another authoritative text on the topic.

This architecture was extended further to define an abstract `<strong>AbstractString</strong>` type that would consider `<strong>AbstractChar</strong>` as an element type. Julia in the pre-1.0 incarnations had many such implementations like `<strong>ASCIIString</strong>`, `<strong>UTF8String</strong>`, and so on., which essentially were providing the basis of some of the encoding schemes that are commonly used3. Many classic string types are functionally merged into the `<strong>String</strong>` type and some are moved into an optional package called `<strong>LegacyStrings.jl</strong>`. While there are no significant benefits of using that package, they can be a good source of reference for people interested to try out and implement their own string types. If you are interested in implementing your own string types make sure you have `<strong>AbstractString</strong>` and `<strong>AbstractChar</strong>` interfaces implemented. There are not many requirements for the abstract types save they expect you to have the easier conversion to and from `<strong>String</strong>` and `<strong>Char</strong>` objects respectively if needed.

A sentence may contain symbols and characters from multiple languages. For example, mathematical symbols and expressions in Greek can be used in an English sentence. Lastly, the text is often used as the representation of the last resort for entities for which there may not be an alternate expression as in the case of textual keywords. Although Julia symbols are pretty likely candidates for the last scenario, the text is used for many such cases as well1. In this chapter, we will try to delve in some details into all the aspects discussed previously. The versatility of text usage brings many representational challenges and we must conceptually understand the design of the Julia language. While the structure of text can get to complexities of document structures and representations we will keep the scope of the discussion to the concept of strings.

Other than the aforementioned methods, the derived types of `<strong>AbstractString</strong>` need to implement all the iteration and indexing methods like `<strong>iterate</strong>`, `<strong>getindex</strong>`, `<strong>nextind</strong>`, `<strong>prevind</strong>`, `<strong>lastindex</strong>`, `<strong>firstindex</strong>` and some collections-related methods like length as well4.

GitHub repository of `ASCIIString` in `LegacyStrings.jl` **[https://github.com/JuliaStrings/LegacyStrings.jl/blob/master/src/ascii.jl](https://github.com/JuliaStrings/LegacyStrings.jl/blob/master/src/ascii.jl)**

In Julia, symbols begin with a : character. One can represent keywords in a file with symbols like :key1, :key2, etc. In JSON objects keywords are written as text as well like {“key1”: value1, “key2”: 32,…}.

Stringapalooza, Issue 16107, Julia GitHub Repository **[https://github.com/JuliaLang/julia/issues/16107](https://github.com/JuliaLang/julia/issues/16107)**

PERL Compatible Regular Expressions, Wikipedia, **[https://en.wikipedia.org/wiki/Perl\_Compatible\_Regular\_Expressions](https://en.wikipedia.org/wiki/Perl_Compatible_Regular_Expressions)**

# 

# 

# 

Julia is significantly influenced by Lisp and also ships a Lisp variant interpreter (*FemtoLisp*) for some of its internal parsing. Hence, it is only natural for it to embrace metaprogramming that is one of the most flexible features of the Lisp derivatives. We shall review how metaprogramming is embraced by Julia in this chapter.

# 

In this chapter, we will cover the following topics:

*   Background
*   Macros
*   Custom string literals
*   Generated functions
*   Commonly used macros

# 

The reader shall be able to understand expressions and structures in Julia. They shall be able to manipulate expressions programmatically. They will learn about macros and how macros are distinctive from functions. They will be able to define their own string literal types. In the end, the readers shall learn about generated functions and their usage in Julia.

# 

Metaprogramming[1](#olitpqt8.html#n4upl4fndar) essentially utilizes data to generate code that can be executed in the same context of the application. Some languages will carry out such code generation during compilation; some will consider this as a part of the execution. While the stage when the code is generated and infused into the execution unit may vary and depend on the language’s internal architecture, all languages will generate the code in the base language before post processing on them. Here is an example from C/C++

`<strong>#define twice(x) 2*(x)</strong>`

`<strong>int main()</strong>`

`<strong>{</strong>`

`<strong>int y = twice(2);</strong>`

`<strong>}</strong>`

If you run it through a C/C++ preprocessor you will get an output like this.

`<strong>#line 1 "a.c"</strong>`

`<strong>int main()</strong>`

`<strong>{</strong>`

`<strong>int y = 2*(2);</strong>`

`<strong>}</strong>`

You can see the preprocessor replaced the twice macro to values that are in the code. Once, the preprocessor is run the newly generated code will be compiled in the C-compiler. Let us look at the template metaprogramming of the same code in the C++ language.

`<strong>template &lt;typename T&gt;</strong>`

`<strong>T twice(T x) {</strong>`

`<strong>return 2*x</strong>`

`<strong>}</strong>`

`<strong>int main()</strong>`

`<strong>{</strong>`

`<strong>int y = twice(2);</strong>`

`<strong>}</strong>`

Running through the preprocessor will not change the code substantially. And, one may likely to believe this is not metaprogramming. But, this also is a form of metaprogramming. While compiling the template type for the function `<strong>twice&lt;T&gt;</strong>` will be resolved and `<strong>twice&lt;int&gt;()</strong>` function will be generated. Template-based metaprogramming is supported in Julia and we have already seen this in the chapter on functions and methods. Julia has the ability to convert any text string and intern it as code that can be executed within the context of the program. While to some it may sound exciting, it also can create concerns on security ramifications of the same. This concept is very similar to Lisp-like languages in executing macros.

# 

Abstract Syntax Trees (ASTs) are a syntactical construct of a code expression in computer science. The structural form makes it easier to understand the code by a machine and eliminates operator precedence or the usage of brackets to modify the precedence. The AST of a code snippet in Julia is a valid object in Julia. Thus you have the flexibility to take a piece of code generate the AST of it and manipulate or act on the AST as a Julia object to create interesting derivative ASTs that can be executed. This is the foundation of Julia’s metaprogramming architecture. Simply put you can generate any valid code string, and execute it in the context of the program by effectively manipulating it. Let us see some of these in action in the following example:

`<strong>julia&gt; s = "1+1"<br>"1+2"<br>julia&gt; ex = Meta.parse(s)<br>:(1 + 1)<br>julia&gt; typeof(ex)<br>Expr<br>julia&gt; dump(ex)<br>Expr<br>&nbsp;&nbsp;head: Symbol call<br>&nbsp;&nbsp;args: Array{Any}((3,))<br>&nbsp;&nbsp;1: Symbol +<br>&nbsp;&nbsp;2: Int64 1<br>&nbsp;&nbsp;3: Int64 2</strong>`

We took a valid string that can be a Julia expression. We parsed it with a Julia parser and the output is returned in an interned string format. The interned string format is of type `<strong>Expr</strong>`. The dump method provides the AST of the expression. The following can be discerned from the AST:

1.  `<strong>ex</strong>` is of type `<strong>Expr</strong>`.
2.  `<strong>ex.head</strong>` is a call symbol.
3.  `<strong>ex.args</strong>` have 3 elements.
4.  `<strong>args[1]</strong>` is Symbol + that will be invoked by call.
5.  `<strong>args[2]</strong>` and `<strong>[3]</strong>` are arguments to the function call.

Let us evaluate the expression and we should get `<strong>2</strong>`.

`<strong>julia&gt; eval(ex)<br>2</strong>`

Let us modify the interned expression `<strong>ex</strong>` and change `<strong>ex.args[1]</strong>` from `<strong>+</strong>` to `<strong>-</strong>`.

`<strong>julia&gt; ex.args[1] = :(-);<br>julia&gt; dump(ex)<br>Expr<br>&nbsp;&nbsp;head: Symbol call<br>&nbsp;&nbsp;args: Array{Any}((3,))<br>&nbsp;&nbsp;&nbsp;&nbsp;1: Symbol -<br>&nbsp;&nbsp;&nbsp;&nbsp;2: Int64 1<br>&nbsp;&nbsp;&nbsp;&nbsp;3: Int64 1<br>julia&gt; eval(ex)<br>0</strong>`

A simple modification of the argument in the call sequence could change the function to be called for evaluation.

# 

`<strong>Symbol</strong>` objects are used as function names and terminals in the Julia AST. The character (`<strong>:</strong>`) preceding a token can be used to quickly define a `<strong>Symbol</strong>` as well. `<strong>Symbol</strong>` constructor is also available. It would concatenate all the arguments to form a symbol.

`<strong>julia&gt; Symbol("A")</strong>`

`<strong>:A</strong>`

`<strong>julia&gt; Symbol("A", "_", 5, "32")</strong>`

`<strong>:A_532</strong>`

`<strong>julia&gt; :A_532</strong>`

`<strong>:A_532</strong>`

`<strong>julia&gt; :(==)</strong>`

`<strong>:(==)</strong>`

When a symbol is defined using a colon, some alphabets may need disambiguation like the == operator in this case. You can use the colon character (:) to define an expression or interned string than use the `<strong>Expr</strong>` constructor or `<strong>Meta.parse</strong>` a string as we did in the previous section.

`<strong>julia&gt; ex = :(z = 1 + 2);</strong>`

`<strong>julia&gt; typeof(ex)</strong>`

`<strong>Expr</strong>`

The Expr generated here has two parts to the AST.

1.  Part one an assignment to a variable.
2.  And a call to the operator + whose result is the r-value of the assignment.

`<strong>julia&gt; dump(ex)</strong>`

`<strong>Expr</strong>`

`<strong>head: Symbol =</strong>`

`<strong>args: Array{Any}((2,))</strong>`

`<strong>1: Symbol z</strong>`

`<strong>2: Expr</strong>`

`<strong>head: Symbol call</strong>`

`<strong>args: Array{Any}((3,))</strong>`

`<strong>1: Symbol +</strong>`

`<strong>2: Int64 1</strong>`

`<strong>3: Int64 2</strong>`

`<strong>julia&gt; eval(ex)</strong>`

`<strong>3</strong>`

`<strong>julia&gt; z</strong>`

`<strong>3</strong>`

Assignment expression introduces a new assigned variable `<strong>z</strong>` to the program state. Thus, manipulations of expressions and evaluations can modify the program states. When operating on them one has to be careful on the scope of variables.

# 

While one can design expressions by choice, it is not very useful unless you get to include pre-evaluated expressions. For example:

`<strong>julia&gt; x = 5;</strong>`

`<strong>julia&gt; ex = :($x + 1)</strong>`

`<strong>:(5 + 1)</strong>`

You could introduce computation expressions in inline evaluations as well. For example:

`<strong>julia&gt; ex = :($(x*x)+1)</strong>`

`<strong>:(25 + 1)</strong>`

`<strong>julia&gt; y = eval(ex)</strong>`

`<strong>26</strong>`

This technique is also known as **interpolation** in Julia programming.

# 

So far we have seen simple expressions as interned strings, their ASTs. However, the real life functions and expressions can be much elaborate. It is natural to have doubts if there are any specific limitations to expressions that can be manipulated programmatically.

`<strong>julia&gt; ex = quote</strong>`

`<strong>x = 1</strong>`

`<strong>y = 2</strong>`

`<strong>x + y</strong>`

`<strong>end</strong>`

`<strong>quote</strong>`

`<strong>#= In[38]:2 =#</strong>`

`<strong>x = 1</strong>`

`<strong>#= In[38]:3 =#</strong>`

`<strong>y = 2</strong>`

`<strong>#= In[38]:4 =#</strong>`

`<strong>x + y</strong>`

`<strong>end</strong>`

The multiline expression is included between a `<strong>quote…end</strong>`. As you can see line number expressions are added to track line numbers for line debugging purposes. A dump of the expression will show a more detailed view of the AST. The longer AST has the following features:

1.  It starts with a `<strong>head</strong>` attribute of the type block.
2.  The line nodes and subsequent expressions are available as a part of the `<strong>args</strong>` array.
3.  The line has a line number part and a file part that sets the context of the expression.
    
    `<strong>julia&gt; dump(ex)</strong>`
    
    `<strong>Expr</strong>`
    
    `<strong>head: Symbol block</strong>`
    
    `<strong>args: Array{Any}((6,))</strong>`
    
    `<strong>1: LineNumberNode</strong>`
    
    `<strong>line: Int64 2</strong>`
    
    `<strong>file: Symbol In[38]</strong>`
    
    `<strong>2: Expr</strong>`
    
    `<strong>head: Symbol =</strong>`
    
    `<strong>args: Array{Any}((2,))</strong>`
    
    `<strong>1: Symbol x</strong>`
    
    `<strong>2: Int64 1</strong>`
    
    `<strong>3: LineNumberNode</strong>`
    
    `<strong>line: Int64 3</strong>`
    
    `<strong>file: Symbol In[38]</strong>`
    
    `<strong>4: Expr</strong>`
    
    `<strong>head: Symbol =</strong>`
    
    `<strong>args: Array{Any}((2,))</strong>`
    
    `<strong>1: Symbol y</strong>`
    
    `<strong>2: Int64 2</strong>`
    
    `<strong>5: LineNumberNode</strong>`
    
    `<strong>line: Int64 4</strong>`
    
    `<strong>file: Symbol In[38]</strong>`
    
    `<strong>6: Expr</strong>`
    
    `<strong>head: Symbol call</strong>`
    
    `<strong>args: Array{Any}((3,))</strong>`
    
    `<strong>1: Symbol +</strong>`
    
    `<strong>2: Symbol x</strong>`
    
    `<strong>3: Symbol y</strong>`
    

Let us modify the assignment in the line # 2 from `<strong>x = 1</strong>` to `<strong>z = 1</strong>`.

`<strong>julia&gt; ex.args[2].args[1]=:z<br>:z</strong>`

`<strong>julia&gt; ex</strong>`

`<strong>quote</strong>`

`<strong>#= In[38]:2 =#</strong>`

`<strong>z = 1</strong>`

`<strong>#= In[38]:3 =#</strong>`

`<strong>y = 2</strong>`

`<strong>#= In[38]:4 =#</strong>`

`<strong>x + y</strong>`

`<strong>end</strong>`

`<strong>julia&gt; eval(ex)</strong>`

`<strong>7</strong>`

`<strong>julia&gt; z</strong>`

`<strong>1</strong>`

A new variable `<strong>z</strong>` is created with the value of `<strong>1</strong>` and `<strong>x</strong>` with a value of `<strong>5</strong>` is picked up from the previous section. Hence, the `<strong>ex</strong>` expression evaluates to `<strong>7</strong>`.

# 

Let us look at some more complex quote expressions, where one `<strong>quote…end</strong>` is included inside another quote expression.

`<strong>julia&gt; e = :(1 + 1);</strong>`

`<strong>julia&gt; eval(:e)</strong>`

`<strong>:(1 + 1)</strong>`

`<strong>julia&gt; eval(e)</strong>`

`<strong>2</strong>`

In the preceding example, `<strong>eval</strong>` of the symbol `<strong>:e</strong>`, evaluates to the contents of the variable `<strong>e</strong>`. However, the `<strong>eval</strong>` on the variable `<strong>e</strong>` actually evaluates the expression, and hence the difference.

We will relook at a similar concept in nested quotes.

`<strong>julia&gt; e = :(1+2)</strong>`

`<strong>julia&gt; ex = quote</strong>`

`<strong>quote</strong>`

`<strong>$e</strong>`

`<strong>end</strong>`

`<strong>end</strong>`

`<strong>quote</strong>`

`<strong>#= In[32]:3 =#</strong>`

`<strong>$(Expr(:quote, quote</strong>`

`<strong>#= In[32]:4 =#</strong>`

`<strong>$(Expr(:$, :e))</strong>`

`<strong>end))</strong>`

`<strong>end</strong>`

`<strong>julia&gt; eval(ex)</strong>`

`<strong>quote</strong>`

`<strong>#= In[32]:4 =#</strong>`

`<strong>1 + 2</strong>`

`<strong>end</strong>`

In the preceding example, `<strong>$e</strong>` is bound to the inner quote and is equivalent to `<strong>eval(:e)</strong>`. Hence, the expression `<strong>1+2</strong>` appears in between `<strong>quote…end</strong>`.

`<strong>julia&gt; ex = quote</strong>`

`<strong>quote</strong>`

`<strong>&nbsp;$$e</strong>`

`<strong>end</strong>`

`<strong>end</strong>`

`<strong>quote</strong>`

`<strong>#= In[34]:2 =#</strong>`

`<strong>$(Expr(:quote, quote</strong>`

`<strong>#= In[34]:3 =#</strong>`

`<strong>$(Expr(:$, :(1 + 2)))</strong>`

`<strong>end))</strong>`

`<strong>end</strong>`

`<strong>julia&gt; eval(ex)</strong>`

`<strong>quote</strong>`

`<strong>#= In[34]:3 =#</strong>`

`<strong>3</strong>`

`<strong>end</strong>`

When `<strong>$$e</strong>` is used instead of `<strong>$e</strong>`, `<strong>eval(eval(:e))</strong>` is computed and thus the computed value 3 is placed between `<strong>quote…end</strong>`.

# 

The following function can generate and return an interned expression from input parameters.

`<strong>Julia&gt; function math_exp(op, p1, p2)</strong>`

`<strong>p1f, p2f = map(x-&gt; x isa Number ? 2x :</strong>`

`<strong>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; error("Parameters have to be numbers"),</strong>`

`<strong>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; (p1, p2))</strong>`

`<strong>return Expr(:call, op, p1f, p2f)</strong>`

`<strong>end</strong>`

`<strong>julia&gt; ex = math_exp(:+, 2, 3)</strong>`

`<strong>:(4 + 6)<br>julia&gt; eval(ex)<br>10</strong>`

The function returns a Julia expression. However, you will need an additional `<strong>eval</strong>` call to compute the values.

# 

Functions can return an expression but one has to explicitly call `<strong>eval</strong>` to evaluate the expression. Macros return expressions that are automatically evaluated as shown:

`<strong>julia&gt; macro sayhello()</strong>`

`<strong>return :(println("Hello, World!!!"))</strong>`

`<strong>end</strong>`

`<strong>@sayhello (macro with 1 method)</strong>`

`<strong>julia&gt; @sayhello()</strong>`

`<strong>Hello, World!!!</strong>`

`<strong>julia&gt; macro sayhello(name)</strong>`

`<strong>return :(println("Hello, ", $name, "!!!"))</strong>`

`<strong>end</strong>`

`<strong>@sayhello (macro with 2 methods)</strong>`

`<strong>julia&gt; @sayhello("John")</strong>`

`<strong>Hello, John!!!</strong>`

# 

Macros can be called in any of the following forms:

`<strong>@mymacro(param1, param2, …, paramN) or<br>@mymacro param1 param2 … paramN</strong>`

Thus, the two `<strong>@sayhello</strong>` macros can be invoked as follows:

`<strong>julia&gt; @sayhello</strong>`

`<strong>Hello, World!!!</strong>`

`<strong>julia&gt; @sayhello "John"</strong>`

`<strong>Hello, John!!!</strong>`

Let us add a more complex expression.

`<strong>julia&gt; @sayhello begin</strong>`

`<strong>1 + 3</strong>`

`<strong>end</strong>`

`<strong>Hello, 4!!!</strong>`

Just like methods follow multiple dispatch architecture, the same is applicable to the macros as well. Introducing a new macro `<strong>@sayhello(x::Int)</strong>` can affect the behavior in the following ways:

`<strong>julia&gt; macro sayhello(x::Int)</strong>`

`<strong>println("Calling Int ", x)</strong>`

`<strong>return :(println("Hello Int, ", $x))</strong>`

`<strong>end</strong>`

`<strong>@sayhello (macro with 3 methods)<br>julia&gt; @sayhello 21</strong>`

`<strong>Calling Int 21</strong>`

`<strong>Hello Int, 21</strong>`

`<strong>julia&gt; x = 21;</strong>`

`<strong>julia&gt; @sayhello x</strong>`

`<strong>Hello, 21!!!</strong>`

When an `<strong>Int</strong>` literal is used as a parameter, the macro specifically `<strong>@sayhello(::Int)</strong>` is called. However, when the variable `<strong>x</strong>` is used as a parameter the `<strong>@sayhello(x)</strong>` is called. Macros take AST objects as input parameters. Hence, the call `<strong>@sayhello x</strong>` will be interpreted as `<strong>sayhello</strong>` being called with Symbol `<strong>x</strong>` as a parameter and not `<strong>21</strong>` as a parameter. The following example will clarify the statement further:

`<strong>julia&gt; macro intype(x)</strong>`

`<strong>println(typeof(x))</strong>`

`<strong>end</strong>`

`<strong>@intype (macro with 1 method)</strong>`

`<strong>julia&gt; @intype begin</strong>`

`<strong>x = 5</strong>`

`<strong>end</strong>`

`<strong>Expr</strong>`

`<strong>julia&gt; @intype x</strong>`

`<strong>Symbol</strong>`

`<strong>julia&gt; @intype 21</strong>`

`<strong>Int64</strong>`

`<strong>julia&gt; @intype "John"</strong>`

`<strong>String</strong>`

# 

These are essentially convenience macros used in place of constructors. We have already seen examples of these macros in the context of regular expressions in the chapter on Strings. The regular expression macro as defined Julia is shown as follows:

`<strong>macro r_str(p)</strong>`

`<strong>Regex(p)</strong>`

`<strong>end</strong>`

One can invoke a regular expression match expression as shown.

`<strong>julia&gt; m = match(r"a.a", "abracadabra")</strong>`

`<strong>RegexMatch("aca")</strong>`

Expression `<strong>r"…"</strong>` is equivalent to calling the macro `<strong>@r_str()</strong>`. Let us create a custom expression for capitalized strings.

`<strong>julia&gt; struct CapsString</strong>`

`<strong>s::String</strong>`

`<strong>CapsString(s::String)=new(uppercase(s))</strong>`

`<strong>end</strong>`

`<strong>julia&gt; macro C_str(s)</strong>`

`<strong>CapsString(s)</strong>`

`<strong>end</strong>`

`<strong>julia&gt; C"This is upper case string"</strong>`

`<strong>CapsString("THIS IS UPPER CASE STRING")</strong>`

# 

Functions and methods are invoked in Julia using the multiple dispatch architecture. However, sometimes one may desire to create more complex dispatch models than the language supports and build their own. The generated functions help in these scenarios. Let us consider a simple dispatch scenario.

`<strong>julia&gt; f(x::Integer) = x^2;</strong>`

`<strong>julia&gt; f(x) = x;</strong>`

`<strong>julia&gt; f(4)</strong>`

`<strong>16</strong>`

`<strong>julia&gt; f("John")</strong>`

`<strong>"John"</strong>`

In the preceding example, using the standard dispatch rules, the `<strong>f(4)</strong>` shall invoke the `<strong>f(::Integer)</strong>` and `<strong>f("John")</strong>` the `<strong>f(x)</strong>`. If one has to build a custom dispatch rule one can use the `<strong>@generated</strong>` macro to create a function as follows:

`<strong>julia&gt; @generated function genf(x)</strong>`

`<strong>if x &lt;: Integer</strong>`

`<strong>return :(x^2)</strong>`

`<strong>else</strong>`

`<strong>return :x</strong>`

`<strong>end</strong>`

`<strong>end</strong>`

`<strong>genf (generic function with 1 method)</strong>`

In the preceding function, only the type of `<strong>x</strong>` is used in the generated function. The value of `<strong>x</strong>` is ignored. The function returns an expression that is expected of the function based on the custom dispatch process.

`<strong>julia&gt; genf(4)</strong>`

`<strong>16<br>julia&gt; genf("John")</strong>`

`<strong>"John"</strong>`

When these methods are invoked the function with the Integer argument is compiled and cached. Subsequent call to `<strong>genf(3)</strong>` shall invoke the compiled expression and can be more efficient. For a more elaborate example of generated macro, we suggest you to refer to the Julia documentation[2](#olitpqt8.html#n4upl4fndas).

**Note:**

*   **The cache generation for the function is non-deterministic. Hence function used with generators must not have side effects. They should not modify global variables as well.**
*   **Generated functions are to be used for complex dispatch rules that are hard to disambiguate. It is always more efficient to use the language default dispatch rules for standard scenarios.**

# 

Julia has many in-built macros that are used to ease some of the tasks. We have already been exposed to them in the previous chapters like `<strong>@view</strong>`, `<strong>@goto</strong>`, `<strong>@label</strong>`, and so on. We will understand a few in this section and appreciate their implementation.

# 

Every macro has access to a variable `<strong>__source__</strong>` that has access to filename, line number and `<strong>__module__</strong>` that has the name of the module where the macro is defined.

`<strong>julia&gt; macro test()</strong>`

`<strong>println(__module__)</strong>`

`<strong>println(__source__)</strong>`

`<strong>end</strong>`

`<strong>@test (macro with 1 method)</strong>`

`<strong>julia&gt; @test</strong>`

`<strong>Main</strong>`

`<strong>#= In[6]:1 =#</strong>`

These are used to develop some utility location macros like `<strong>@__FILE__</strong>`, `<strong>@__LINE__</strong>` and `<strong>@__DIR__</strong>` as well.

`<strong>function macro_usage()</strong>`

`<strong>println("Dir:", @__DIR__, " file:", @__FILE__, " Line no:", @__LINE__)</strong>`

`<strong>end</strong>`

`<strong>julia&gt; macro_usage()<br>Dir:C:\mydir\GitHub\HOPJ\Chapter-8 file:In[9] Line no:2</strong>`

**Note:** `<strong>@__FILE__</strong>` **macro does not return a filename when the code is being used in a REPL or IJulia context. It returns the command identifier.**

# 

When a large amount of boilerplate code is to be generated, `<strong>@eval</strong>` can be used effectively.

`<strong>julia&gt; struct MyNumber<br>&nbsp;&nbsp;&nbsp;&nbsp;v::Float64<br>end</strong>`

Let us say we would like to define all mathematical methods like `<strong>sin</strong>`, `<strong>cos</strong>` and, `<strong>tan</strong>` on these numbers. The code may look like:

`<strong>Base.sin(m::MyNumber)=Base.sin(m.v)<br>Base.cos(m::MyNumber)=Base.cos(m.v)<br>Base.tan(m::MyNumber)=Base.tan(m.v)</strong>`

The repetitive code can be avoided by the following expression:

`<strong>julia&gt; for op in [:sin, :cos, :tan]</strong>`

`<strong>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; eval(quote</strong>`

`<strong>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Base.$op(m::MyNumber)=Base.$op(m.v)</strong>`

`<strong>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; end)</strong>`

`<strong>end</strong>`

The `<strong>eval(quote…end)</strong>` is a commonly used expression in many Julia applications. The same is represented as the macro `<strong>@eval</strong>` and the expression looks as follows:

`<strong>julia&gt; for op in [:sin, :cos, :tan]</strong>`

`<strong>@eval Base.$op(m::MyNumber)=Base.$op(m.v)</strong>`

`<strong>end</strong>`

# 

`<strong>@assert</strong>` is a macro that validates an expression for its truth value and throws an `<strong>AssertionError</strong>` if the expression evaluates to `<strong>false</strong>`. Other languages like C/C++ also have such macros. In some languages, the assertion validation only works when the code is executed in the debug mode and ignored during optimized released mode code. Julia also recommends the usage of the `<strong>assert</strong>` macro for debug operations only. Hence, it should not be used as program logic. The simplest form for `<strong>assert</strong>` is as follows and a complete code can be seen at the Julia GitHub repository[3](#olitpqt8.html#n4upl4fndat):

`<strong>macro myassert(ex, msg)</strong>`

`<strong>return :($(ex) ? nothing : throw(AssertionError($msg)))</strong>`

`<strong>end</strong>`

`<strong>julia&gt; @myassert 1==0 "1 is not same as 0"<br>AssertionError: 1 is not same as 0</strong>`

`<strong>Stacktrace:</strong>`

`<strong>&nbsp;[1] top-level scope at In[24]:4</strong>`

`<strong>&nbsp;…</strong>`

The actual `<strong>assert</strong>` macro does not restrict the number of parameters that can be passed to it but only utilizes the first message as the valid message. If there is no message then it utilizes the `<strong>ex</strong>` as the message.

`<strong>macro myassert(ex, msgs…)</strong>`

`<strong>msg = isempty(msgs) ? ex : msgs[1]</strong>`

`<strong>msg = msg isa AbstractString ? String(msg) : string(msg)</strong>`

`<strong>return :($(ex) ? nothing : throw(AssertionError($msg)))</strong>`

`<strong>end</strong>`

`<strong>julia&gt; @myassert 1==0<br>AssertionError: 1 == 0</strong>`

`<strong><br></strong>`

`<strong>Stacktrace:</strong>`

`<strong>&nbsp;[1] top-level scope at In[34]:10<br>…</strong>`

The final code is a bit different from the preceding one as it addresses a few error conditions that the simple sample code does not address. It is apt that `<strong>assert</strong>` is defined as a macro as `<strong>ex</strong>` parameter can be any expression in Julia.

# 

`<strong>@time</strong>` macro is used to compute the elapsed time and allocations made in executing a code block.

`<strong>julia&gt; @time begin</strong>`

`<strong>sleep(0.3)</strong>`

`<strong>1+1</strong>`

`<strong>end</strong>`

`<strong>&nbsp;0.310595 seconds (15 allocations: 672 bytes)</strong>`

`<strong>2</strong>`

A part of the `<strong>@time</strong>` macro is implemented like the following code:

`<strong>macro mytime(ex)</strong>`

`<strong>return quote</strong>`

`<strong>local elapsedtime = time_ns()</strong>`

`<strong>local val = $(ex)</strong>`

`<strong>elapsedtime = time_ns() - elapsedtime</strong>`

`<strong>println("Elapsed time: ", elapsedtime/1e9)</strong>`

`<strong>val</strong>`

`<strong>end</strong>`

`<strong>end</strong>`

`<strong>val</strong>` is computed before `<strong>elapsedtime</strong>`. Hence, both are needed to be stored in a local variable. Since, the return value is a quoted expression. If the variables `<strong>val</strong>` and `<strong>elapsedtime</strong>` are not explicitly defined as local, variables `<strong>val</strong>` and `<strong>elapsedtime</strong>` from the global scope would have been overwritten. This is only true for the return `<strong>Expr</strong>` from a macro and does not affect variables used in the macro like `<strong>msg</strong>` in the previous example.

# 

Metaprogramming is elaborate and can be fairly complex in Julia. We looked at a few scenarios and understood how they can be used in developing applications with Julia. We also understood the concept of macros and how we can use them effectively. People who are getting the first exposure to metaprogramming may find the concept complex. With experience and practice, you will be able to appreciate the concepts better. In the next chapter, we shall look at the standard libraries of Julia language and some of the functionalities the libraries offer.

# 

1.  Why is operator precedence not relevant for an AST?
2.  Write a custom string literal to convert the input to lower case alphabets.
3.  Why is `<strong>@assert</strong>` macro in Julia’s implementation so complex? What are the other useful cases it addresses that the simple code suggested in the chapter does not?
4.  What value does the `<strong>@view</strong>` macro add to the subarray type?
5.  Use the `<strong>@eval</strong>` macro and show how you can implement object composition effectively using this macro.

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

[1](#olitpqt8.html#n4upl4fndau) Metaprogramming, Wikipedia, **[https://en.wikipedia.org/wiki/Metaprogramming](https://en.wikipedia.org/wiki/Metaprogramming)**

[2](#olitpqt8.html#n4upl4fndav) Generated Functions, Julia Documentation, **[https://docs.julialang.org/en/v1/manual/metaprogramming/#Generated-functions](https://docs.julialang.org/en/v1/manual/metaprogramming/#Generated-functions)**

[3](#olitpqt8.html#n4upl4fndaw) Julia GitHub Repository, **[https://github.com/JuliaLang/julia/blob/788b2c77c10c2160f4794a4d4b6b81a95a90940c/base/error.jl#L189-L209](https://github.com/JuliaLang/julia/blob/788b2c77c10c2160f4794a4d4b6b81a95a90940c/base/error.jl#L189-L209)**

Julia GitHub Repository, **[https://github.com/JuliaLang/julia/blob/788b2c77c10c2160f4794a4d4b6b81a95a90940c/base/error.jl#L189-L209](https://github.com/JuliaLang/julia/blob/788b2c77c10c2160f4794a4d4b6b81a95a90940c/base/error.jl#L189-L209)**

Generated Functions, Julia Documentation, **[https://docs.julialang.org/en/v1/manual/metaprogramming/#Generated-functions](https://docs.julialang.org/en/v1/manual/metaprogramming/#Generated-functions)**

Metaprogramming, Wikipedia, **[https://en.wikipedia.org/wiki/Metaprogramming](https://en.wikipedia.org/wiki/Metaprogramming)**

When these methods are invoked the function with the Integer argument is compiled and cached. Subsequent call to `<strong>genf(3)</strong>` shall invoke the compiled expression and can be more efficient. For a more elaborate example of generated macro, we suggest you to refer to the Julia documentation2.

`<strong>@assert</strong>` is a macro that validates an expression for its truth value and throws an `<strong>AssertionError</strong>` if the expression evaluates to `<strong>false</strong>`. Other languages like C/C++ also have such macros. In some languages, the assertion validation only works when the code is executed in the debug mode and ignored during optimized released mode code. Julia also recommends the usage of the `<strong>assert</strong>` macro for debug operations only. Hence, it should not be used as program logic. The simplest form for `<strong>assert</strong>` is as follows and a complete code can be seen at the Julia GitHub repository3:

Metaprogramming1 essentially utilizes data to generate code that can be executed in the same context of the application. Some languages will carry out such code generation during compilation; some will consider this as a part of the execution. While the stage when the code is generated and infused into the execution unit may vary and depend on the language’s internal architecture, all languages will generate the code in the base language before post processing on them. Here is an example from C/C++

# 

# 

# 

Julia is an elaborate programming system. A programming system provides functionalities that are beyond the basic programming language. Most modern languages provide complete runtime programming systems that work seamlessly with the underlying operating system giving a sense of platform-independent experience to the developers.

# 

In this chapter, we will cover the following topics:

*   Background
*   Standard modules
*   System
*   Filesystem
*   Parallel programming
*   I/O and network
*   Constants
*   Notable modules

# 

In this chapter, the reader shall be able to understand, how Julia’s code is organized as modules. We shall review some commonly used methods that help users access files, file systems, work with I/O frameworks. We shall review multithreading and asynchronous programming. We shall review the interaction with the operating system.

# 

Providing elaborate runtime environments has become the basic paradigm of most programming languages today. Java is probably one of the early adopters of this philosophy. Subsequently, most programming languages like Perl, Python, Ruby, R, SPSS, and so on have continued with a similar philosophy. For example, when C/C++ programming was the most popular among developers, operating systems like Windows would release a Windows Runtime Library in C/C++ language when a new version of the Windows operating system was released. Programmers would integrate the same with their application code for proper interoperability and compatibility. Now it is expected that the runtime that ships with a programming language will ensure such compatibility with the operating system. This will ensure application programmers will have to worry less about the nuances of the operating systems internals and their behavioral changes across versions. Given this backdrop, it is only logical to expect the same in the Julia Programming System as well.

**Note: `stdlib`. `stdlib` is just one of the libraries of Julia. The scope of this chapter is encompassing all the Julia Language components that ship with the language runtime including the `stdlib`.**

**We will provide a conceptual overview of the libraries and suggest the reader to look for the details in the Julia documentation.**

# 

Julia is a large programming environment. It has the core language and abstracted subsystems for many operating system functionalities. We will discuss some of these in subsequent sections. This needs hierarchical organization and avoidance of namespace collision as two functions with the same name can reside in two different namespaces serving two different purposes. For example, the `<strong>length</strong>` of a `<strong>Line</strong>` is completely a different purpose from a `<strong>length</strong>` of a one-dimensional Array.

Here is how Julia addresses such cases:

`<strong>module m1</strong>`

`<strong>function f()</strong>`

`<strong>println("Defined in m1.f")</strong>`

`<strong>end</strong>`

`<strong>function g()</strong>`

`<strong>println("Defined in m1.g")</strong>`

`<strong>end</strong>`

`<strong>function h()</strong>`

`<strong>println("Defined as m1.h")</strong>`

`<strong>end</strong>`

`<strong>export f</strong>`

`<strong>end</strong>`

`<strong>module m2</strong>`

`<strong>function f()</strong>`

`<strong>println("Defined in m2.f")</strong>`

`<strong>end</strong>`

`<strong>function g()</strong>`

`<strong>println("Defined in m2.g")</strong>`

`<strong>end</strong>`

`<strong>export g</strong>`

`<strong>end</strong>`

We defined two modules `<strong>m1</strong>` and `<strong>m2</strong>` in the execution environment (IJulia or REPL). We have defined two methods `<strong>f</strong>` and `<strong>g</strong>`. We want to get an understanding of the names defined in the modules `<strong>m1</strong>` and `<strong>m2</strong>`. This can be carried out by the method `<strong>names()</strong>`.

`<strong>julia&gt; names(m1)</strong>`

`<strong>2-element Array{Symbol,1}:</strong>`

`<strong>:f</strong>`

`<strong>:m1</strong>`

`<strong>julia&gt; names(m2)</strong>`

`<strong>2-element Array{Symbol,1}:</strong>`

`<strong>:g</strong>`

`<strong>:m2</strong>`

As can be seen the module names `<strong>m1</strong>` and `<strong>m2</strong>` are defined in the respective namespace of modules. However, only function `<strong>f</strong>` is available in the namespace of module `<strong>m1</strong>` and function `<strong>g</strong>` in the namespace of module `<strong>m2. names()</strong>` function only reports the symbols exported from the module. Now let us use the function `<strong>f</strong>` in the code.

`<strong>julia&gt; f()</strong>`

`<strong>UndefVarError: f not defined</strong>`

`<strong>Stacktrace:</strong>`

`<strong>[1] top-level scope at In[6]:1</strong>`

`<strong>[2] include_string(::Function, ::Module, ::String, ::String) at .\loading.jl:1091</strong>`

`<strong>…</strong>`

`<strong>f</strong>` is only defined within the modules but not accessible to the outer execution environment. However, calling `<strong>f()</strong>` by qualifying the module name executes the function properly.

`<strong>julia&gt; m1.f()</strong>`

`<strong>Defined as m1.f</strong>`

`<strong>julia&gt; m2.f()</strong>`

`<strong>Defined as m2.f</strong>`

You can access all exported names from a module with the command `<strong>using</strong>`.

`<strong>julia&gt; using .m1</strong>`

`<strong>julia&gt; f()</strong>`

`<strong>Defined as m1.f</strong>`

`<strong>julia&gt; g()</strong>`

`<strong>UndefVarError: g not defined</strong>`

`<strong>Stacktrace:</strong>`

`<strong>[1] top-level scope at In[10]:1</strong>`

`<strong>[2] include_string(::Function, ::Module, ::String, ::String) at .\loading.jl:1091</strong>`

`<strong>…</strong>`

The only `<strong>f</strong>` is able to be called as `<strong>m1</strong>` is exported the function `<strong>f</strong>` only. Function `<strong>g</strong>` is not exported. Hence the symbol is not accessible to be called. The second point to note here is the dot(.) before `<strong>m1</strong>` in the using statement. The module is defined in the current environment. `<strong>m1</strong>` is a member module of the current module. It is not the highest-level module. The `<strong>.m1</strong>` clarifies that the hierarchy of the module.

`<strong>julia&gt; using Main.m2</strong>`

`<strong>julia&gt; g()</strong>`

`<strong>Defined as m2.g</strong>`

One could also use, `<strong>Main.m2</strong>` instead of `<strong>.m2</strong>` that is the relative position of the module `<strong>m2</strong>`, while `<strong>Main.m2</strong>` is the fully qualified module name. `<strong>Main</strong>` is the highest level of the Julia execution environment. When a call is being made from a REPL or IJulia environment, the module namespace where all the interactions occur is the `<strong>Main</strong>` module. We will look at some of the predefined modules in the next section. You can import a non-exported function like `<strong>m1.g()</strong>` by using command specifically a requesting for the access. However, it will not succeed as there is already `<strong>g()</strong>` available from `<strong>m2.g()</strong>`.

`<strong>julia&gt; using .m1: g</strong>`

`<strong>WARNING: ignoring conflicting import of m1.g into Main</strong>`

`<strong>julia&gt; g()</strong>`

`<strong>Defined as m2.g</strong>`

However, `<strong>m1.h()</strong>` can be accessed by the `<strong>using</strong>` command although it has not been exported from `<strong>m1</strong>`.

`<strong>julia&gt; using .m1: h</strong>`

`<strong>julia&gt; h()</strong>`

`<strong>Defined as m1.h</strong>`

We got a brief understanding of the Julia module design. We will be reviewing a few details along with the discussion on packages in a later chapter. For now, you may be able to use the various functionalities defined in the standard modules defined in the Julia runtime.

# 

In the previous section, we saw code can be organized as modules. We also understood, functions defined in one module can be used in another module. Some of the modules are in-built into the Julia system. When a Julia execution environment is launched it is launched with a module `<strong>Main</strong>` initialized. The function `<strong>varinfo()</strong>` reports the variables defined in the current execution environment.

`<strong>julia&gt; varinfo()</strong>`

`<strong>name&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;size summary</strong>`

`<strong>–––––––––––––––– ––––––––––– –––––––</strong>`

`<strong>Base&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Module</strong>`

`<strong>Core&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Module</strong>`

`<strong>InteractiveUtils 198.387 KiB Module</strong>`

`<strong>Main&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Module</strong>`

`<strong>m1&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;5.866 KiB Module&nbsp;&nbsp;</strong>`

`<strong>m2&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;4.992 KiB Module</strong>`

As can be seen, `<strong>Main</strong>`, `<strong>Core</strong>`, and `<strong>Base</strong>` were reported to have been available. `<strong>InteractiveUtils</strong>` is loaded due to the REPL. When launching the Julia environment with IJulia the same may not be loaded. Modules `<strong>m1</strong>` and `<strong>m2</strong>` that are defined previously are loaded as well. Let’s define a few variables.

`<strong>julia&gt; varinfo()</strong>`

`<strong>name&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;size summary</strong>`

`<strong>–––––––––––––––– ––––––––––– –––––––</strong>`

`<strong>Base&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Module</strong>`

`<strong>Core&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Module</strong>`

`<strong>InteractiveUtils 198.387 KiB Module</strong>`

`<strong>Main&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Module</strong>`

`<strong>m1&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;5.866 KiB Module</strong>`

`<strong>m2&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;4.992 KiB Module</strong>`

`<strong>ans&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;8 bytes Int64</strong>`

`<strong>&nbsp;x&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;8 bytes Int64</strong>`

In the preceding table:

*   A variable `<strong>ans</strong>` may be reported in the REPL environment as that stores the last value printed on the REPL screen.
*   Core module contains the central language features without which the system may not operate at all. Data types like `<strong>String</strong>`, `<strong>Int</strong>`, and so on are defined in the `<strong>Core</strong>` module.
*   Base module has language features as well. However, in some sense they can be considered peripheral than the Core module. For example, File `<strong>Input/Output</strong>` (`<strong>IO</strong>`) is defined in the `<strong>Base</strong>` module. While IO is a fundamental feature of the system one can build applications that do not need to use IO directly. However, many internal system components may require IO for implementing their functionalities.

Hence, one can think of `<strong>Base</strong>`, `<strong>Core,</strong>` and `<strong>Main</strong>` as the building block modules of Julia. The modules `<strong>m1</strong>` and `<strong>m2</strong>` we defined appear as sub-modules of the `<strong>Main</strong>` module. They will be used selectively on need basis. We will explore those in the subsequent sections.

**Note: Julia has support for functionalities that require interaction with an operating system. We will review a few of these in this chapter. The treatment cannot be exhaustive in the book. The reader is suggested to refer to the Julia documentation for a detailed understanding.**

# 

While working in Julia, there is a need to quickly access the system shell to access a command, launch an editor, or any such functionalities. If you are in the Julia REPL you could just type a semicolon (;) and that will launch a system sub-shell within the REPL for quick shell access. You could run the shell of your choice like `<strong>cmd</strong>` and invoke the shell command of your choice.

`<strong>julia&gt; ;</strong>`

`<strong>shell&gt; cmd</strong>`

`<strong>Microsoft Windows [Version 10.0.18363.1139]</strong>`

`<strong>(c) 2019 Microsoft Corporation. All rights reserved.</strong>`

`<strong>C:\Users\juser&gt;dir</strong>`

`<strong>Volume in drive C has no label.</strong>`

`<strong>Volume Serial Number is E285-F8B9</strong>`

`<strong>Directory of C:\Users\juser</strong>`

`<strong>19-11-2020&nbsp;&nbsp;15:05&nbsp;&nbsp;&nbsp;&nbsp;&lt;DIR&gt;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;.</strong>`

`<strong>19-11-2020&nbsp;&nbsp;15:05&nbsp;&nbsp;&nbsp;&nbsp;&lt;DIR&gt;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;..<br>…</strong>`

`<strong>2 File(s)&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;769 bytes</strong>`

`<strong>20 Dir(s)&nbsp;&nbsp;41,198,710,784 bytes free</strong>`

`<strong>C:\Users\juser&gt;^C</strong>`

You could also launch the same using the `<strong>run</strong>` function on a command object.

``<strong>julia&gt; run(`cmd –c dir`)</strong>``

`<strong>Volume in drive C has no label.</strong>`

`<strong>Volume Serial Number is E285-F8B9</strong>`

`<strong>Directory of C:\Users\HOPJ\Chapter-9</strong>`

`<strong>19-11-2020&nbsp;&nbsp;18:01&nbsp;&nbsp;&nbsp;&nbsp;&lt;DIR&gt;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;.</strong>`

`<strong>19-11-2020&nbsp;&nbsp;18:01&nbsp;&nbsp;&nbsp;&nbsp;&lt;DIR&gt;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;..</strong>`

`<strong>18-11-2020&nbsp;&nbsp;12:26&nbsp;&nbsp;&nbsp;&nbsp;&lt;DIR&gt;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;.ipynb_checkpoints</strong>`

`<strong>19-11-2020&nbsp;&nbsp;18:01&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;16,850 Chapter-9 Standard Libraries.ipynb</strong>`

`<strong>1 File(s)&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 16,850 bytes</strong>`

`<strong>3 Dir(s)&nbsp;&nbsp;41,193,525,248 bytes free</strong>`

``<strong>Process(`cmd /c dir`, ProcessExited(0))</strong>``

`<strong>Cmd</strong>` objects are created by quoting an external command with backticks(`). There are also explicit constructors for `<strong>Cmd</strong>` objects as well[1](#iesbkwfi.html#n4upl4fndmr).

There may be a need to do system-specific operations based on the type of the operating system. Moreover, there are cases where the code to be run is specific to the OS and may not exist on other platforms leading to compilation errors. In such cases, such code can be placed with a `<strong>@static</strong>` macro. That way the code that is not applicable to an operating system will not be checked.

`<strong>julia&gt; using Main.Sys</strong>`

`<strong>julia&gt; @static if iswindows()</strong>`

`<strong>do_something_windows_specific()</strong>`

`<strong>end</strong>`

On a non-windows machine, such code will not be evaluated due to the `<strong>@static</strong>` macro. There are machine OS-specific test methods like `<strong>isunix</strong>`, `<strong>islinux</strong>`, `<strong>isapple</strong>`, `<strong>isbsd</strong>`, `<strong>isfreebsd</strong>`, and `<strong>iswindows</strong>` in the `<strong>Base.</strong>` `<strong>Sys</strong>` module.

# 

`<strong>Filesystem</strong>` is a module under the Base module that helps provide file-level access to Julia programs in a platform-independent manner. For example, if you would like to copy a file in the Unix like systems, commands like ``<strong>cp source.ext dest.ext</strong>`` vs. in Windows ``<strong>copy source.ext dest.ext</strong>`` have to be used. Julia will provide a simple platform-independent method `<strong>cp()</strong>` that you can use both with Unix as well as Windows systems. There are many such methods that you could use in your code from the Julia environment.

Some are listed here for understanding their functionalities.

`<strong>julia&gt; old_dir = pwd()</strong>`

`<strong>"C:\\Users\\juser\\OneDrive\\Documents\\GitHub\\HOPJ\\Chapter-9"</strong>`

`<strong>julia&gt; cd("..")</strong>`

`<strong>julia&gt; pwd()</strong>`

`<strong>"C:\\Users\\juser\\OneDrive\\Documents\\GitHub\\HOPJ"</strong>`

`<strong>julia&gt; cd(old_dir)</strong>`

`<strong>julia&gt; pwd()</strong>`

`<strong>"C:\\Users\\juser\\OneDrive\\Documents\\GitHub\\HOPJ\\Chapter-9"</strong>`

In the preceding example:

1.  We queried and cached the present working directory by method `<strong>pwd</strong>`.
2.  We changed the directory with `<strong>cd()</strong>`.
3.  We changed back the directory to the cached value.

You can get the listing of a directory using `<strong>readdir()</strong>`. However, it may not be most useful as it does not let you know if the reported array is a directory or file. By default, the `<strong>readdir()</strong>` lists the present working directory.

`<strong>julia&gt; readdir()&nbsp;&nbsp;#Same as readdir(pwd())</strong>`

`<strong>10-element Array{String,1}:</strong>`

`<strong>".git"</strong>`

`<strong>".ipynb_checkpoints"</strong>`

`<strong>"Chapter-2"</strong>`

`<strong>"Chapter-3"</strong>`

`<strong>"Chapter-4"</strong>`

`<strong>"Chapter-5"</strong>`

`<strong>"Chapter-6"</strong>`

`<strong>"Chapter-7"</strong>`

`<strong>"Chapter-8"</strong>`

`<strong>"Chapter-9"</strong>`

There is also another method called `<strong>walkdir()</strong>`, which traverses the complete directory tree that can be used to access each file and directory in the directory. `<strong>joinpath()</strong>` helps join the parts of a path with the correct file separator like backslash (\) in Windows and slash (/) in Unix-like operating systems.

`<strong>julia&gt; for (root, dirs, files) in walkdir("Chapter-9")</strong>`

`<strong>println("Directories in $root")</strong>`

`<strong>for dir in dirs</strong>`

`<strong>println(joinpath(root, dir)) # path to directories</strong>`

`<strong>end</strong>`

`<strong>println("Files in $root")</strong>`

`<strong>for file in files</strong>`

`<strong>println(joinpath(root, file)) # path to files</strong>`

`<strong>end</strong>`

`<strong>end</strong>`

`<strong>Directories in Chapter-9</strong>`

`<strong>Chapter-9\.ipynb_checkpoints</strong>`

`<strong>Files in Chapter-9</strong>`

`<strong>Chapter-9\Chapter-9 Standard Libraries.ipynb</strong>`

`<strong>Directories in Chapter-9\.ipynb_checkpoints</strong>`

`<strong>Files in Chapter-9\.ipynb_checkpoints</strong>`

`<strong>Chapter-9\.ipynb_checkpoints\Chapter-9 Standard Libraries-checkpoint.ipynb</strong>`

`<strong>stat</strong>` command in Julia returns a `<strong>stat</strong>` structure that is equivalent to the Unix `<strong>stat</strong>` command containing various file parameters like size, creation time, and so on. of the file.

`<strong>julia&gt; fs = stat("Chapter-9 Standard Libraries.ipynb")</strong>`

`<strong>StatStruct(mode=0o100666, size=21901)</strong>`

`<strong>isdir</strong>`, `<strong>isfile,</strong>` and `<strong>islink</strong>` can return true, if a name is a directory, a regular file, or a symbolic link. `<strong>mkdir()</strong>` and `<strong>rmdir()</strong>` like functions can create and delete directories. In short, Julia provides elaborate methods to manipulate files as one would use system calls or shell commands to achieve.

# 

Julia provides flexibility in parallel programming with solutions for asynchronous computing, multithreading, and distributed computing.

1.  **Asynchronous programming**: A programming paradigm where parts of code are broken into small independent and parallel tasks. The tasks can be synchronized on specific conditions and can communicate over channels.
2.  **Multithreading**: Julia by default runs as a single-threaded application. However, it can be made to run with a number of threads where the operating system supports it. Julia provides APIs where applications can take advantage from such threads available to them.
3.  **Distributed computing**: goes beyond the realm of a single process. Two-independent processes that cannot normally share any resources among themselves can communicate over a message passing interface designed specifically for Julia. Packages like `<strong>MPI.jl</strong>` support industry standard MPI protocols as well.

We will look into the Julia’s way of addressing these scenarios in this section.

# 

![](n4upl4fndrf.jpeg)

**Figure 9.1:** Task state transition based on various actions

Julia asynchronous programming model can be understood from the preceding figure:

1.  A new task created is added to the scheduler’s runnable task queue by the `<strong>schedule</strong>` method.
2.  When a task is executing it can call `<strong>yield</strong>` and relinquish the control to the scheduler to schedule the next runnable task.
3.  A task can `<strong>wait</strong>` on a condition and move to the condition’s wait queue.
4.  When the condition is met, `<strong>notify</strong>` can be called on the condition and that will move all the tasks assigned to the condition to the runnable queue of the scheduler.

Tasks are not functions. They can be switched easily as there is no need to recreate a stack frames as is needed to be carried out for functions. How the scheduler decides on the task to pick up is dependent on the architecture of the Julia runtime. For example, a scheduler with the availability of multiple thread execution may be able to pick up multiple tasks for execution. Similarly, the condition is another system-dependent entity. For example, the condition can be a file being locked, a device being busy or a channel being full or empty.

# 

A `<strong>Task</strong>` object can be constructed by passing a function with no parameters as a parameter to its constructor. The `<strong>Task</strong>` object thus created has not run yet and will be put on the scheduler queue when the `<strong>schedule</strong>` function is called on it.

`<strong>julia&gt; t = Task() do</strong>`

`<strong>sleep(10)</strong>`

`<strong>println("done")</strong>`

`<strong>end</strong>`

`<strong>julia&gt; schedule(t)</strong>`

The prompt returns immediately on the call `<strong>schedule(t)</strong>` as the call only places the task on the queue. The printing is carried out after 10 s.

`<strong>julia&gt; t = Task() do</strong>`

`<strong>sleep(10)</strong>`

`<strong>println("done")</strong>`

`<strong>end</strong>`

`<strong>julia&gt; schedule(t); wait(t)</strong>`

A call to `<strong>wait</strong>` will ensure the execution shall wait till the task is completed. `<strong>@task x</strong>` is a common way to take any arbitrary code and make a `<strong>Task</strong>` object out of it by `<strong>Task(()-&gt;x)</strong>`.

`<strong>t = @task begin</strong>`

`<strong>sleep(10)</strong>`

`<strong>println("done")</strong>`

`<strong>end</strong>`

An asynchronous task is one where a `<strong>Task</strong>` is followed by a call to `<strong>schedule()</strong>` and often represented by macro `<strong>@async</strong>`. If a wait is called on the task then the call would wait for the task to complete. Such system will be called a synchronous task. A macro `<strong>@sync</strong>` can address such a need.

# 

Channels are shared memory queues that can help design producer and consumer kinds of data interchange between tasks. A channel can have a fixed number of data elements of a specific type or of type `<strong>Any</strong>` if no specific type is specified.

`<strong>julia&gt; c = Channel(8)</strong>`

`<strong>Channel{Any}(sz_max:8,sz_curr:0)</strong>`

You can also create a channel with a specific type of data in the queue like an `<strong>Int</strong>`.

`<strong>julia&gt; c = Channel{Int}(8)</strong>`

`<strong>Channel{Int64}(sz_max:8,sz_curr:0)</strong>`

Let us use an asynchronous producer to write to the channel.

`<strong>@async begin</strong>`

`<strong>for i = 1:6</strong>`

`<strong>println("Adding $i to channel")</strong>`

`<strong>put!(c, i)</strong>`

`<strong>end</strong>`

`<strong>end</strong>`

An asynchronous consumer reads from channel as well.

`<strong>@async begin</strong>`

`<strong>for i = 1:6</strong>`

`<strong>v = take!(c)</strong>`

`<strong>println("Removing value: $v")</strong>`

`<strong>end</strong>`

`<strong>end</strong>`

The results are printed in spurts and as soon as the channel is filled up the producer waits. Similarly, as soon as the channel gets emptied the consumer waits.

`<strong>Adding 1 to channel</strong>`

`<strong>Adding 2 to channel</strong>`

`<strong>Adding 3 to channel</strong>`

`<strong>Adding 4 to channel</strong>`

`<strong>Removing value: 1</strong>`

`<strong>Removing value: 2</strong>`

`<strong>Removing value: 3</strong>`

`<strong>Removing value: 4</strong>`

`<strong>Adding 5 to channel</strong>`

`<strong>Adding 6 to channel</strong>`

`<strong>Removing value: 5</strong>`

`<strong>Removing value: 6</strong>`

Finally, channels can be closed with a `<strong>close</strong>` call. Once the channel is closed, no further communication can take place through them.

# 

Locks are synchronization objects used to synchronize tasks. If a resource can be accessed by more than one task, it may be best managed under a lock to avoid the state be modified when they are being accessed. The basic premise of a lock is a condition. When the condition is notified then the tasks waiting on it are released as discussed earlier. Typical lock code looks like the following:

`<strong>lock(c)</strong>`

`<strong>try</strong>`

`<strong>while !condition_to_wait</strong>`

`<strong>wait(c)</strong>`

`<strong>end</strong>`

`<strong>finally</strong>`

`<strong>unlock(c)</strong>`

`<strong>end</strong>`

A smarter way to address this scenario would be to use the `<strong>lock…do</strong>` syntax with the `<strong>lock(f, cond)</strong>` function that automatically includes the `<strong>unlock()</strong>` call.

`<strong>lock(c) do</strong>`

`<strong>// Access the resource when the lock is active</strong>`

`<strong>work_on_resource()</strong>`

`<strong>end</strong>`

Locks are particularly crucial for multithreading scenarios where there is a possibility of simultaneous access of resources by tasks.

# 

Julia process starts with a single thread when launched. However, it can be launched with multiple threads by using the command `<strong>julia –t &lt;no_of_threads&gt;</strong>` or `<strong>julia –threads &lt;no_of_threads&gt;</strong>`. The same can be achieved by setting the environment variable `<strong>JULIA_NUM_THREADS</strong>` to the required number of threads[2](#iesbkwfi.html#n4upl4fndms). By starting Julia with `<strong>julia –t 4</strong>`, the following code provides the number of active threads in the Julia environment.

`<strong>julia&gt; Threads.nthreads()</strong>`

`<strong>4</strong>`

`<strong>@spawn</strong>` will use any available thread and run a task on it.

`<strong>julia&gt; Threads.@spawn for i=1:100</strong>`

`<strong>sleep(1)</strong>`

`<strong>println("Step: $i")</strong>`

`<strong>&nbsp;end</strong>`

`<strong>Task (runnable) @0x0000000016a73990</strong>`

`<strong>julia&gt; Step: 1</strong>`

`<strong>Step: 2</strong>`

`<strong>Step: 3</strong>`

`<strong>Step: 4</strong>`

`<strong>…</strong>`

`<strong>Step: 100</strong>`

The values are printed serially as the task is running on a single thread of the 4 currently available.

If you will like to parallelize the `for` loop, you could use the `<strong>Threads.@threads</strong>` macro. As can be seen, the printing is now in parallel. One could clearly see the `<strong>for</strong>` loop has been split into 4 different threads of execution.

`<strong>julia&gt; Threads.@threads for i=1:100</strong>`

`<strong>sleep(1)</strong>`

`<strong>println("Step: $i")</strong>`

`<strong>end</strong>`

`<strong>Step: 26</strong>`

`<strong>Step: 51</strong>`

`<strong>Step: 1</strong>`

`<strong>Step: 76</strong>`

`<strong>Step: 77</strong>`

`<strong>Step: 52</strong>`

`<strong>Step: 2</strong>`

`<strong>Step: 27</strong>`

`<strong>…</strong>`

`<strong>Step: 100</strong>`

`<strong>Step: 25</strong>`

`<strong>Step: 50</strong>`

`<strong>Step: 75</strong>`

When multiple threads are being executed in a program, synchronizing across them can be a concern. Locks are useful programming paradigms to address those needs. `<strong>Threads.Conditions()</strong>` are thread-safe condition objects and must be used for thread safety. The second issue is low-level atomic operations. Some of the LLVM defined low-level atomic operations are supported by Julia. Lastly, finalizers and garbage collection may get affected with multithreaded programs. We will suggest the user reviews the manuals on multithreading for a better understanding of the topic[3](#iesbkwfi.html#n4upl4fndmt):

# 

![](n4upl4fndrg.jpeg)

**Figure 9.2:** Distributed computing architecture in Julia

The distributed architecture in Julia has all the similar models discussed in the earlier chapters related to asynchronous programming as well as multithreading programming. However, there are certain additional complexities that are due to the distributed architecture.

1.  A master process governs the computing infrastructure management.
2.  It utilizes a `<strong>LocalManager</strong>` to launch and manage Julia worker processes where the local load can be executed in the same machine.
3.  There is also a `<strong>SSHManager</strong>` that can connect to a remote host over an SSL connection and communicate any remote actions to be carried out.
4.  The connection management is kept outside of the architecture and it is presumed all needed security restrictions and protocols are handled by the network layer.
5.  A remote worker can be launched by the master process and a new id will be assigned to the worker process. Id 1 is reserved for the master process.
6.  Any code to be launched by a worker is launched by a `<strong>remotecall</strong>`. The remote call may return an object of type Future that can be waited on by a `<strong>fetch</strong>` call to get the output of the remote call.
7.  The other mode of data exchange is a `<strong>RemoteChannel</strong>` that can be set up in one of the processes while other worker processes can `<strong>put!()</strong>` data in it or `<strong>take!()</strong>` data from it. Just like local `<strong>Channel</strong>` objects they provide an easy way to program publish and subscribe models.
8.  Many remote connections may not need to exactly know the specifics of the machine where the workload needs to be run. They use macros like `<strong>@spawnat</strong>` with :`<strong>Any</strong>` as parameter such that the workload can be launched at any of the machines. The Future object thus returned will be able to tunnel through the proper SSH connection to communicate to the correct worker in another physical machine.
9.  Similarly, the code to be run by all the worker processes must be available to them. One option may be to deploy it as a package such that the package is available in all the processes. But the package needs to be selected by using in each individual processes separately.

While Julia provides an elaborate distributed architecture, we will keep the discussion minimal for the sake of brevity and reduce the complexity it will bring into the text. However, interested readers are advised to refer to the Julia documentation manual on Multiprocessing and Distributed Computing[4](#iesbkwfi.html#n4upl4fndmu).

# 

Input and Output (I/O or IO) is about reading and writing data from various devices. Julia can communicate to various I/O devices through the operating system. However, Julia creates high-level stream-based interfaces to connect to TTYs, files, and network sockets. I/O-based methods are applicable to all these different kinds of devices under the hood. Some Julia methods will support `<strong>IO</strong>` as an argument which is an abstract type to a high-level stream interface from which specific IO devices are derived.

# 

`<strong>Base.stdin</strong>`, `<strong>Base.stdout</strong>`, and `<strong>Base.stderr</strong>` are the standard streams used for input, output, and errors if no other are specified. For an interactive environment like REPL, the terminal can act as all three. You can configure them to redirect to other locations as well by using `<strong>redirect_stdout</strong>` like functions.

`<strong>julia&gt; write(stdout, "Hello World")</strong>`

`<strong>Hello World</strong>`

`<strong>11</strong>`

`<strong>11</strong>` number of bytes were written by `<strong>write()</strong>`.

`<strong>julia&gt; write(stdout, "\u2200 x \u2203 y")</strong>`

`<strong>∀ x ∃ y</strong>`

`<strong>11</strong>`

The write command returns the number of bytes written and irrespective of the number of characters to be written.

**Note:** `<strong>read()</strong>` **from** `<strong>stdin</strong>` **may not work from Jupyter notebooks and any such code in the examples should be executed in the REPL environment.**

# 

Reading text from `<strong>stdin</strong>` is fairly common on TTY terminals. But it is equally important to know when to stop reading. Often the data are read to a fixed-sized buffer and the reading stops when the required data is read.

`<strong>julia&gt; read(stdin, Char)</strong>`

`<strong>a</strong>`

`<strong>'a': ASCII/Unicode U+0061 (category Ll: Letter, lowercase)</strong>`

Expected one character and as soon as we got one, the read command is completed. The method returned the data into a `<strong>Char</strong>` constant. The same for a `<strong>String</strong>` can lead to a never-ending condition.

`<strong>julia&gt; read(stdin, String)</strong>`

`<strong>abcd</strong>`

`<strong>ccsdcsacd</strong>`

`<strong>cdsacdss</strong>`

`<strong>ERROR: InterruptException:</strong>`

`<strong>…</strong>`

You can use *ctrl-C*; that will raise an interrupt exception and come out of the `<strong>read</strong>` method but your `<strong>String</strong>` could not be read[5](#iesbkwfi.html#n4upl4fndmv). This is a perfect place to use the `<strong>readline</strong>` method. `<strong>readline</strong>` will read one line till the `<strong>end of line</strong>` (`<strong>EOL</strong>`) character is got.

`<strong>julia&gt; readline(stdin)</strong>`

`<strong>12345</strong>`

`<strong>"12345 "</strong>`

However, for multiline inputs, `<strong>eachline(stdin)</strong>` provides an iterator for picking up each line from the terminal. The following code terminates reading further on a blank new line.

`<strong>julia&gt; for line in eachline(stdin)</strong>`

`<strong>isempty(line) &amp;&amp; break</strong>`

`<strong>println(line)</strong>`

`<strong>&nbsp;end</strong>`

`<strong>1st line</strong>`

`<strong>1st line</strong>`

`<strong>2nd line</strong>`

`<strong>2nd line</strong>`

Similar to reading, writing also requires the output to be displayed as a text where the terminal supports.

`<strong>julia&gt; print(stdout, 0x61)</strong>`

`<strong>97</strong>`

`<strong>Julia&gt; write(stdout, 0x61);</strong>`

`<strong>a</strong>`

In the preceding example, while print tries to display the numeric value of the `<strong>UInt8</strong>`, the write method does a text output to the terminal.

# 

`<strong>read()</strong>` and `<strong>write()</strong>` operations are generally used to read and write binary streams of data into object arrays where they wait for a specific size of data to be read or till the end of file is reached.

`<strong>julia&gt; read(stdin, 4)</strong>`

`<strong>abcd</strong>`

`<strong>4-element Array{UInt8,1}:</strong>`

`<strong>0x61</strong>`

`<strong>0x62</strong>`

`<strong>0x63</strong>`

`<strong>0x64</strong>`

In the preceding example, only 4 bytes are read from the `<strong>stdin. read</strong>` method has many other variations as well including `<strong>read(io, String)</strong>` that will read a complete `<strong>io</strong>` as a single string and `<strong>read(filepath)</strong>` that will read the whole file represented by a `<strong>filepath</strong>` as a single byte array.

# 

File I/O in Julia is very similar to stream operations. Following are some of the generic steps in a Julia file operation:

1.  Open the file and obtain the relevant stream handle.
2.  Access the relevant location in the stream.
3.  Read from or write data into the file.
4.  Close the stream handle.

While the file may not be buffered the streams are buffered with a small memory in the cache for a look ahead or rollback. While streams in Julia have interfaces to many operations, they may be limited by the internal capabilities of the device. For example, if a file is read only it cannot be opened for write. Thus write operations on a read only stream shall fail.

`<strong>julia&gt; write("hello.txt", "Hello World")</strong>`

`<strong>11</strong>`

`<strong>julia&gt; f = open("hello.txt", "r");</strong>`

`<strong>julia&gt; data = read(f);</strong>`

`<strong>julia&gt; write(f, "This is second line")</strong>`

`<strong>ArgumentError: write failed, IOStream is not writeable</strong>`

`<strong>Stacktrace:</strong>`

`<strong>[1] unsafe_write(::IOStream, ::Ptr{UInt8}, ::UInt64) at .\iostream.jl:363</strong>`

`<strong>[2] write(::IOStream, ::String) at .\strings\io.jl:183</strong>`

`<strong>…</strong>`

`<strong>julia&gt; close(f)</strong>`

`<strong>julia&gt; write(stdout, data)</strong>`

`<strong>Hello World</strong>`

`<strong>11</strong>`

In the preceding example shown:

1.  `<strong>write(filename, data)</strong>` will create a new file and write `data` into it. The number of bytes written is returned by the function.
2.  Subsequently, we open the file in the read only mode by `<strong>open(filename, mode)</strong>` and read the data from the file as a byte array.
3.  Try to write additional data into the read only stream, which fails as expected.
4.  Close the stream.
5.  Write the data read into `<strong>stdout</strong>` to be printed.

`<strong>open(fn, filename, mode)</strong>` is an alternate method that closes the opened file handle.

`<strong>open("hello.txt", "r") do f</strong>`

`<strong>data = read(f)</strong>`

`<strong>write(stdout, data);</strong>`

`<strong>end</strong>`

`<strong>Hello World</strong>`

`<strong>11</strong>`

For many data science problems, files are used for archiving. Reading from and writing to files based on file path is considered convenient as the code shown as follows:

`<strong>julia&gt; write("hello.txt", "Hello World");</strong>`

`<strong>julia&gt; data = read("hello.txt");</strong>`

`<strong>julia&gt; write(stdout, data);</strong>`

`<strong>Hello World</strong>`

File position-based operations like `<strong>seek</strong>`, `<strong>seekstart</strong>`, `<strong>seekend,</strong>` and `<strong>position</strong>` are supported by the APIs as well. We used `<strong>read</strong>` method that would read till the EOF in one shot. While convenient it may not be most memory efficient. Some applications like parsers may read a file byte by byte like the following code:

`<strong>open("hello.txt", "r") do f</strong>`

`<strong>while !eof(f)</strong>`

`<strong>b = read(f, 1)</strong>`

`<strong>write(stdout, b)</strong>`

`<strong>end</strong>`

`<strong>end</strong>`

`<strong>Hello World</strong>`

In the preceding example, `<strong>eof(f)</strong>` provides the necessary check to stop the file traversal.

# 

Julia **standard library** (`<strong>stdlib</strong>`) contains a module `<strong>DelimitedFiles</strong>` that helps read and write data in delimited values where each row represents a record. **Comma separated values** (**CSV**) used extensively in spreadsheets to export and import data is one such format. Following code can help write data into a CSV like format with a line of header:

`<strong>using DelimitedFiles</strong>`

`<strong>x = collect(1:100);</strong>`

`<strong>y = Float64.(collect(101:200));</strong>`

`<strong>open("values.csv", "w") do f</strong>`

`<strong>println(f, "X,Y")</strong>`

`<strong>writedlm(f, [x y], ',')</strong>`

`<strong>end</strong>`

Similarly, the data can be read back into variables `<strong>data</strong>` and `<strong>header</strong>` by the following code:

`<strong>julia&gt; data, header = readdlm("values.csv", ',', header=true)</strong>`

`<strong>julia&gt; size(data, 1)</strong>`

`<strong>100</strong>`

`<strong>julia&gt; header</strong>`

`<strong>1×2 Array{AbstractString,2}:</strong>`

`<strong>"X"&nbsp;&nbsp;"Y"</strong>`

# 

When the system has `<strong>curl</strong>`, `<strong>fetch,</strong>` or `<strong>wget</strong>` installed, Julia provides a `<strong>download(url, [localfile])</strong>` method to download files over ftp, http, or SSL-based communication channels. However, it cannot be used for generic network communications needed for internet-based application development. The API returns the local file to which the downloaded file was written to.

`<strong>julia&gt;download("https://github.com/JuliaLang/julia/releases/download/v1.5.3/julia-1.5.3.tar.gz", "julia-1.5.3.tar.gz")<br>"julia-1.5.3.tar.gz"</strong>`

TCP sockets are used for client-server communications and application development over the internet. While in most cases you may not need to use raw sockets for communication and may be able to use protocol-specific APIs available with Julia packages like `<strong>HTTP.jl</strong>`, it may be worthwhile to be aware of the `<strong>Sockets</strong>` module in the standard library.

The basics of networked client–server communication can be described in the following basic workflow:

1.  A server binds to a communication end (port) and listens on it continuously.
2.  A client connects to the same port and obtains a communication socket handle.
3.  Client writes a request to the server as commands.
4.  The server responds back with response data.
5.  When the client obtains the data it needed it closes the connection.
6.  On exceptional conditions, the server may also terminate the connection as well.

Both client and server running as background tasks are shown as follows:

**Server Code (Background Task-1):**

`<strong>julia&gt; using Sockets</strong>`

`<strong>julia&gt; @async begin</strong>`

`<strong>server = listen(3000)</strong>`

`<strong>while true</strong>`

`<strong>s = accept(server)</strong>`

`<strong>@async while isopen(s)</strong>`

`<strong>msg = readline(s, keep=true)</strong>`

`<strong>write(s, "Server Response: $msg")</strong>`

`<strong>end</strong>`

`<strong>end</strong>`

`<strong>end</strong>`

**Client Reads Server Response (Background Task-2):**

`<strong>julia&gt; c = connect(3000)</strong>`

`<strong>julia&gt; @async while isopen(c)</strong>`

`<strong>println(stdout, readline(c, keep=true))</strong>`

`<strong>end</strong>`

**Client Sends Request Code (Foreground Task):**

`<strong>julia&gt; for i = 1:5</strong>`

`<strong>println(c, "Client Msg id: $i")</strong>`

`<strong>end<br></strong>`

`<strong>Server Response: Client Msg id: 1</strong>`

`<strong>Server Response: Client Msg id: 2</strong>`

`<strong>Server Response: Client Msg id: 3</strong>`

`<strong>Server Response: Client Msg id: 4</strong>`

`<strong>Server Response: Client Msg id: 5</strong>`

`<strong>Julia&gt; close(c)</strong>`

The sample code can be considered to have three parts.

1.  The server is running in the background and listening to port 3000. 
    1.  Once a client connects on the port 3000 the server accepts the connection and gets a socket to respond to the client through that connection.
    2.  The server spawns another parallel task so that client and server can communicate over it while the main server task keeps listening on the port 3000 indefinitely waiting for the next client to communicate.
    3.  In the new task, the server reads the client request and appends its own message and writes it back to the socket for the client to read.
2.  The client connects to the server on port 3000. 
    1.  On connection success, it reads continuously whatever the server writes on the socket and writes to the `<strong>stdout</strong>`.
3.  The client sends the server a request over the foreground task.

Once the communication task is completed, the client can `<strong>close</strong>` the connection with the server. The server shall continue to run the background waiting for other clients to connect.

# 

In the chapter on Strings we realized, the Strings being immutable make them unsuitable for modifications. However, one may need to continuously modify large chunks of memory or append new data to it. Here is a simple way to use memory as an IO that can be later aggregated as a `<strong>String</strong>`.

`<strong>julia&gt; io = IOBuffer();</strong>`

`<strong>julia&gt; println(io, "This is Line 1");</strong>`

`<strong>julia&gt; println(io, "This is Line 2");</strong>`

`<strong>julia&gt; str = String(take!(io))</strong>`

`<strong>"This is Line 1\nThis is Line 2\n"</strong>`

The reverse scenario is of memory mapping. A file can be mapped to a memory address. The data in the file can be accessed as if one accesses a memory location. Memory mapping often improves access speed to the file data and is also helpful where large a chunk of data may not fit into the computer memory. Mapped memory can be utilized as a shared memory for inter-process communications. Memory-mapped functions are defined in the standard library module `<strong>Mmap</strong>`.

`<strong>Step 1</strong>`: Creating a file that we will like to memory map.

`<strong>A = fill(10, (5, 20))</strong>`

`<strong>A[2, 3] = 20</strong>`

`<strong>open("mmap.bin", "w+") do f</strong>`

`<strong>write(f, size(A, 1))</strong>`

`<strong>write(f, size(A, 2))</strong>`

`<strong>write(f, A)</strong>`

`<strong>end</strong>`

`<strong>Step 2</strong>`: Memory mapping the file and read value and ensure the correct data is populated.

`<strong>using Mmap</strong>`

`<strong>f = open("mmap.bin", "r")</strong>`

`<strong>nr = read(f, Int)</strong>`

`<strong>nc = read(f, Int)</strong>`

`<strong>A2 = Mmap.mmap(f, Matrix{Int}, (nr, nc))</strong>`

`<strong>println("A2[1, 1]: ", A2[1, 1], " A2[2, 3]: ", A2[2, 3])</strong>`

`<strong>close(f)</strong>`

**Step 3: Cleaning Up**

`<strong>A2 = nothing</strong>`

`<strong>GC.gc()</strong>`

`<strong>rm("mmap.bin")</strong>`

In operating systems like Windows, where files are locked for reading and writing, the file cannot be removed till the array allocated with mmap is not reclaimed. Calling `<strong>GC.gc()</strong>` ensures the garbage collector is called to clean up the unreferenced array `<strong>A2</strong>`. However, calling the garbage collector manually is not considered an efficient practice in Julia and should be kept to a minimum.

# 

There are some standard constants that are used in a system to provide information on file paths, the number of threads, and so on. Julia has quite a few of them predefined as part of its library. Many are obvious from their nomenclature; some we will discuss as part of this section. There are hundreds of such constants in the language and elaborate explanation is beyond the scope of the book. Please refer to the Julia documentation for a detailed understanding.

`<strong>julia&gt; VERSION</strong>`

`<strong>v"1.5.2"</strong>`

`<strong>julia&gt; Sys.BINDIR</strong>`

`<strong>"D:\\Users\\juser\\AppData\\Local\\Programs\\Julia 1.5.2\\bin"</strong>`

`<strong>julia&gt; Sys.CPU_THREADS</strong>`

`<strong>4</strong>`

`<strong>julia&gt; Sys.WORD_SIZE</strong>`

`<strong>64</strong>`

`<strong>julia&gt; Sys.KERNEL</strong>`

`<strong>:NT</strong>`

`<strong>julia&gt; Sys.MACHINE</strong>`

`<strong>"x86_64-w64-mingw32"</strong>`

`<strong>julia&gt; Sys.ARCH</strong>`

`<strong>:x86_64</strong>`

`<strong>Julia&gt; Sys.ENV</strong>`

`<strong>Base.EnvDict with 48 entries:</strong>`

`<strong>"ALLUSERSPROFILE"&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; =&gt; "C:\\ProgramData"</strong>`

`<strong>"APPDATA"&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; =&gt; "C:\\Users\\usr\\AppData\\Roaming"</strong>`

`<strong>"COMMONPROGRAMFILES"&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;=&gt; "C:\\Program Files\\Common Files"</strong>`

`<strong>⋮&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; =&gt; ⋮</strong>`

There are also constants defined in other sub-modules. Mathematical constants like `<strong>pi</strong>` and `<strong>e</strong>`, and so on. are also defined in the language as well.

`<strong>julia&gt; MathConstants.pi</strong>`

`<strong>pi = 3.1415926535897…</strong>`

`<strong>julia&gt; MathConstants.e</strong>`

`<strong>e = 2.7182818284590…</strong>`

# 

The standard library has many additional modules that can be beneficial to programmers as they provide utility functions. We outline a few commonly used ones here.

# 

`<strong>Dates</strong>` module provides user presentation of date and time functionalities. While we saw `<strong>@time</strong>` macro in the earlier chapter that helps debugging and profiling of `<strong>code</strong>`, `<strong>Date,</strong>` and `<strong>DateTime</strong>` types represent the time in user presentation formats. For example, `<strong>Date</strong>` has the ability to present with day, month, and year and `<strong>DateTime</strong>` can additionally present with hours, minutes, and seconds. However, these representations are devoid of any time zone information. Anyone needing to use time zone with date and time will need to use the `<strong>TimeZones.jl</strong>` package. `<strong>Date</strong>` and `<strong>DateTime</strong>` both internally keep track of time in elapsed `<strong>Int64</strong>` and are immutable types. For example, a function now reports the current time as a `<strong>DateTime</strong>` object.

`<strong>julia&gt; using Dates</strong>`

`<strong>julia&gt; now()</strong>`

`<strong>2020-11-27T22:52:36.318</strong>`

`<strong>DateTime</strong>` and `<strong>Date</strong>` constructors can be constructed by providing a part of the data. Defaults to first day and first month when those are not provided. Any time parameter not provided defaults to 0s.

`<strong>julia&gt; DateTime(2020)</strong>`

`<strong>2020-01-01T00:00:00</strong>`

`<strong>julia&gt; t = DateTime(2020, 10, 31, 01, 02, 03)</strong>`

`<strong>2020-10-31T01:02:03</strong>`

`<strong>julia&gt; Date(2020)</strong>`

`<strong>2020-01-01</strong>`

`<strong>Date</strong>` and `<strong>DateTime</strong>` types can be converted from one another. Time data are set to zeros when `<strong>DateTime</strong>` is converted to `<strong>Date</strong>`.

`<strong>julia&gt; d = Date(t)</strong>`

`<strong>2020-10-31</strong>`

`<strong>julia&gt; DateTime(d)</strong>`

`<strong>2020-10-31T00:00:00</strong>`

`<strong>DateTime</strong>` and `<strong>Date</strong>` can be compared to each other as well as within the same types.

`<strong>julia&gt; t &gt; d # t is DateTime and d is a Date</strong>`

`<strong>true</strong>`

`<strong>julia&gt; DateTime(2020) &lt; now() # both date time</strong>`

`<strong>true</strong>`

`<strong>julia&gt; DateTime(2020) == Date(2020)</strong>`

`<strong>true</strong>`

The difference of a `<strong>Date</strong>` from another `<strong>Date</strong>` or `<strong>DateTime</strong>` from another `<strong>DateTime</strong>` can lead to a type that is subtype of the Period type. Some of the commonly used period types are `<strong>Year</strong>`, `<strong>Day</strong>`, `<strong>Month</strong>`, `<strong>Hour</strong>`, `<strong>Minute</strong>`, `<strong>Second,</strong>` and `<strong>Millisecond</strong>`. A combination of these types can form a `<strong>CompositePeriod</strong>` type. `<strong>Periods</strong>` can be combined with `<strong>Date</strong>` and `<strong>DateTime</strong>` to produce a `<strong>Date</strong>` and `<strong>DateTime</strong>` as appropriate.

`<strong>julia&gt; p = Month(3) + Day(10) + Hour(15)</strong>`

`<strong>3 months, 10 days, 15 hours</strong>`

`<strong>julia&gt; typeof(p)</strong>`

`<strong>Dates.CompoundPeriod</strong>`

`<strong>julia&gt; now() + p</strong>`

`<strong>2021-03-11T01:24:53.251</strong>`

`<strong>julia&gt; Date(now())+ Day(300)</strong>`

`<strong>2021-09-24</strong>`

`<strong>julia&gt; now() - DateTime(2020)</strong>`

`<strong>28728026709 milliseconds</strong>`

`<strong>julia&gt; now() - Date(2020)</strong>`

`<strong>MethodError: no method matching -(::DateTime, ::Date)</strong>`

`<strong>…</strong>`

`<strong>julia&gt; Date(now()) - Date(2020)</strong>`

`<strong>332 days</strong>`

Accessor constructors are defined to estimate the Period elapsed from the previous larger period. For example, `<strong>Month()</strong>` shall compute the elapsed months from the previous new year or `<strong>Day()</strong>` from the previous completion of the month. However, `<strong>Week()</strong>` computes the elapsed weeks from the new year. The functions in lower case return the quantity in `<strong>Int64</strong>` instead of a Period.

`<strong>julia&gt; Year(now())</strong>`

`<strong>2020 years</strong>`

`<strong>julia&gt; Month(now())</strong>`

`<strong>11 months</strong>`

`<strong>julia&gt; Day(now())</strong>`

`<strong>28 days</strong>`

`<strong>julia&gt; Week(now())</strong>`

`<strong>48 weeks</strong>`

`<strong>julia&gt; year(now())</strong>`

`<strong>2020</strong>`

Julia provides many interesting functions called `<strong>adjustors</strong>` that help in computing a specific date. For example, finding the next Thanks Giving Holiday (4th Thursday of the month of November) can be based on the following code:

`<strong>julia&gt; tonext(today()) do d</strong>`

`<strong>dayofweek(d) == Thursday &amp;&amp;</strong>`

`<strong>dayofweekofmonth(d) == 4 &amp;&amp;</strong>`

`<strong>month(d) == November</strong>`

`<strong>end</strong>`

`<strong>2021-11-25</strong>`

# 

Julia is extensively used in backend server programming. This essentially would mean long-running processes must be tracked for errors and failures. A good logging framework is needed for such a system. The Logging module in the standard library serves that purpose to certain extent. Messages in Julia can be logged in various log levels. Here are some examples in increasing order of severity of their logging levels.

`<strong>julia&gt; @error "This is an error"<br>┌ Error: This is an error<br>└ @ Main REPL[1]:1<br>julia&gt; @warn "This is a warning"<br>┌ Warning: This is a warning<br>└ @ Main REPL[2]:1<br>julia&gt; @info "This is an info"<br>[Info: This is an info<br>julia&gt; @debug "This is debug message $(sum(rand(10)))"<br>julia&gt;</strong>`

The debug message was not computed at all as the default log level is set at `<strong>info</strong>` level and `<strong>debugs</strong>` level falls below that level. Depending on the system terminal capabilities and logger used the log messages may be rendered in various colors and highlights. The shown renderings are from the REPL’s default rendering. For example, line numbers are not reported in the case of info messages.

When parameters to the macros are not strings they will be shown as keys followed by their actual computed values.

`<strong>julia&gt; A = ones((3, 4))</strong>`

`<strong>julia&gt; @info "A is all ones" A</strong>`

`<strong>┌ Info: A is all ones</strong>`

`<strong>│&nbsp;&nbsp; A =</strong>`

`<strong>│&nbsp;&nbsp;&nbsp;&nbsp;3×4 Array{Float64,2}:</strong>`

`<strong>│&nbsp;&nbsp;&nbsp;&nbsp; 1.0&nbsp;&nbsp;1.0&nbsp;&nbsp;1.0&nbsp;&nbsp;1.0</strong>`

`<strong>│&nbsp;&nbsp;&nbsp;&nbsp; 1.0&nbsp;&nbsp;1.0&nbsp;&nbsp;1.0&nbsp;&nbsp;1.0</strong>`

`<strong>└&nbsp;&nbsp;&nbsp;&nbsp; 1.0&nbsp;&nbsp;1.0&nbsp;&nbsp;1.0&nbsp;&nbsp;1.0</strong>`

Every application has a logger registered that takes the log event as an input and renders effectively based on the logger capabilities. The capabilities include the stream where the application logs shall be written, like a file system or `<strong>stderr</strong>` or any other stream. So far we have been using the global logger. The global logger can be overwritten by the use of the method `<strong>global_logger(logger::AbstractLogger)</strong>`. An application can set a local logger with a method `<strong>with</strong>`_`<strong>logger(f, logger)</strong>` as well. The following code will write the logs to a file using a `<strong>SimpleLogger</strong>`.

`<strong>julia&gt; using Logging</strong>`

`<strong>julia&gt; open("file.log", "w") do f</strong>`

`<strong>with_logger(SimpleLogger(f)) do</strong>`

`<strong>@info "This is my simple info log"</strong>`

`<strong>@error "This is an error written to file"</strong>`

`<strong>@warn "This is a warning message"</strong>`

`<strong>@info "Current logger is same as global logger"<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;current_logger() == global_logger()</strong>`

`<strong>end</strong>`

`<strong>end</strong>`

`<strong>julia&gt; write(stdout, read("file.log"));</strong>`

`<strong>┌ Info: This is my simple info log</strong>`

`<strong>└ @ Main In[72]:3</strong>`

`<strong>┌ Error: This is an error written to file</strong>`

`<strong>└ @ Main In[72]:4</strong>`

`<strong>┌ Warning: This is a warning message</strong>`

`<strong>└ @ Main In[72]:5</strong>`

`<strong>┌ Info: Current logger is same as global logger</strong>`

`<strong>│&nbsp;&nbsp; current_logger() == global_logger() = false</strong>`

`<strong>└ @ Main In[72]:6</strong>`

`<strong>julia&gt; @info "Current logger is same as global logger" current_logger() == global_logger()</strong>`

`<strong>┌ Info: Current logger is same as global logger</strong>`

`<strong>│&nbsp;&nbsp; current_logger() == global_logger() = true</strong>`

`<strong>└ @ Main In[72]:10</strong>`

Since the local logger has overridden the current logger inside the `<strong>with_logger</strong>` block, the current logger is different from the global logger. However, outside the `<strong>with_logger</strong>` block the `<strong>current_logger()</strong>` is the same as the `<strong>global_logger()</strong>`. `<strong>SimpleLogger</strong>` provides a very simple interface to override the logging stream and the message levels to be shown in the logger. Log events can also have modules, message identifiers, files, line numbers, maximum times a log message should be shown and exceptions that are to be shown as part of logs.

Anyone interested in implementing her own logger can create a subtype of the `<strong>AbstractLogger</strong>` type and implement the methods needed for the `<strong>AbstractLogger</strong>`. The details are documented in the Julia documentation on the `<strong>Logging</strong>` module[6](#iesbkwfi.html#n4upl4fndmw).

# 

`<strong>Statistics</strong>` module in Julia standard library provides methods for computing central tendencies. These are only simple functions for the computation of means, medians, correlations, standard deviations and covariance, and so on. More sophisticated statistics functions are provided by packages like `<strong>BaseStats.jl</strong>`. Listed here are a few simple statistics functions in action.

`<strong>julia&gt; using Statistics</strong>`

`<strong>julia&gt; mean(1:10)</strong>`

`<strong>5.5</strong>`

`<strong>julia&gt; median(1:10)</strong>`

`<strong>5.5</strong>`

`<strong>julia&gt; std(1:10)</strong>`

`<strong>3.0276503540974917</strong>`

`<strong>julia&gt; var(1:10)</strong>`

`<strong>9.166666666666666</strong>`

`<strong>julia&gt; cor(1:10, rand(10))</strong>`

`<strong>-0.5776975622356152</strong>`

`<strong>julia&gt; cor(1:10, 11:20)</strong>`

`<strong>1.0</strong>`

`<strong>julia&gt; cov(1:10, rand(10))</strong>`

`<strong>-0.25738214577938084</strong>`

# 

Random numbers are used extensively in data sciences to initialize data. They are also useful as sample creation for various probability distributions. A cryptographically secured random number is also a requirement for encryption and decryption algorithms. Here are some examples:

`<strong>julia&gt; using Random</strong>`

`<strong>julia&gt; rand(Int, 2)</strong>`

`<strong>2-element Array{Int64,1}:</strong>`

`<strong>-6387591687841801404</strong>`

`<strong>-5718816187088355789</strong>`

`<strong>julia&gt; rand(2, 3)</strong>`

`<strong>2×3 Array{Float64,2}:</strong>`

`<strong>0.395316&nbsp;&nbsp;0.413728&nbsp;&nbsp; 0.738543</strong>`

`<strong>0.505417&nbsp;&nbsp;0.0773799&nbsp;&nbsp;0.560448</strong>`

`<strong>)</strong>`

`<strong>julia&gt; rand!(zeros(2, 3))</strong>`

`<strong>2×3 Array{Float64,2}:</strong>`

`<strong>0.30912&nbsp;&nbsp; 0.797688&nbsp;&nbsp; 0.324596</strong>`

`<strong>0.586434&nbsp;&nbsp;0.0213767&nbsp;&nbsp;0.110147<br>julia&gt; rand(1:4, (2, 3))<br>2×3 Array{Int64,2}:<br>&nbsp;2&nbsp;&nbsp;3&nbsp;&nbsp;1<br>&nbsp;2&nbsp;&nbsp;2&nbsp;&nbsp;4</strong>`

`<strong>rand()</strong>` methods generate uniform random numbers of a specific type, data range or any shape or output desired. Given a pre-allocated array `<strong>rand!()</strong>` function can fill new random values into the same array. Similar to `<strong>rand</strong>` methods, `<strong>randn</strong>` methods fill random numbers in a normal distribution and `<strong>randexp</strong>` in an exponential distribution of data.

The first parameter of `<strong>rand</strong>` methods is optional and is called the random engine (`<strong>rng</strong>`). Julia utilizes *Mersenne Twister* library for random number generation. One can initialize own *Mersenne Twister* with enough entropy such that the pseudo-random sequence generated by the random number generators is secured enough. Not providing an engine shall use the engine initialized as part of Julia runtime. Julia also provides methods for random permutations, random subsequences and random cyclic permutations, and so on.

# 

The standard libraries in Julia are a necessity to access the operating system and address day to day programming needs of developers. While some may have the effectiveness of being utility methods, many methods are a necessity to interact with other systems in the ecosystem. We did a short walkthrough of the libraries and understood the Julia module architecture. This brings us to a closure on the first part of the text that introduces the Julia programming language. In the next part, we shall work on understanding the Julia development environment like the IDEs, debuggers, package manager, interaction with native libraries, and cloud deployment architectures. We will also understand the best practices of Julia programming and performance considerations that need to be adhered to for production-ready Julia application.

# 

1.  Can a module be defined inside another module? If so, how will its functions be exported externally?
2.  Write a command to launch a command prompt window or a Unix terminal window from a Julia REPL. How is it any different from using semicolon (`;`) in the REPL to switch to the shell mode in the REPL? Look at the Julia source code to find how REPL is able to achieve the same.
3.  Traverse a directory and list all the PDF files. PDF files have a file extension of `<strong>“.pdf”</strong>`.
4.  Read a text file and rewrite it with additional line spacing between the lines.
5.  Write a function to give the date of n days from today.
6.  Given a `Vector` of numbers rearrange the elements in a random order.

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

[1](#iesbkwfi.html#n4upl4fndmx) Running External Programs, Julia Documentation, **[https://docs.julialang.org/en/v1/manual/running-external-programs/#Running-External-Programs](https://docs.julialang.org/en/v1/manual/running-external-programs/#Running-External-Programs)**

[2](#iesbkwfi.html#n4upl4fndmy) You can launch Julia as shown: $ JULIA\_NUM\_THREADS=4 julia . If you are using IJulia, you could follow the following steps.  
`ENV[“JULIA_NUM_THREADS”] = 4`  
`using IJulia`  
`notebook()`

[3](#iesbkwfi.html#n4upl4fndmz) Multi-Threading, Julia Documentation Manuals, **[https://docs.julialang.org/en/v1/manual/multi-threading/](https://docs.julialang.org/en/v1/manual/multi-threading/)**

[4](#iesbkwfi.html#n4upl4fndm0) Multiprocessing and Distributed Computing, Julia Documentation Manual, **[https://docs.julialang.org/en/v1/manual/distributed-computing/](https://docs.julialang.org/en/v1/manual/distributed-computing/)**

[5](#iesbkwfi.html#n4upl4fndm1) An alternative method will be to use `ctrl-D` on a new line after the input is supplied or 2 consecutive `ctrl-D` characters to notify end of input.

[6](#iesbkwfi.html#n4upl4fndm2) Logging, Standard Libraries, Julia Documentation, **[https://docs.julialang.org/en/v1/stdlib/Logging/](https://docs.julialang.org/en/v1/stdlib/Logging/)**

Running External Programs, Julia Documentation, **[https://docs.julialang.org/en/v1/manual/running-external-programs/#Running-External-Programs](https://docs.julialang.org/en/v1/manual/running-external-programs/#Running-External-Programs)**

Multi-Threading, Julia Documentation Manuals, **[https://docs.julialang.org/en/v1/manual/multi-threading/](https://docs.julialang.org/en/v1/manual/multi-threading/)**

You can launch Julia as shown: $ JULIA\_NUM\_THREADS=4 julia . If you are using IJulia, you could follow the following steps.  
`ENV[“JULIA_NUM_THREADS”] = 4`  
`using IJulia`  
`notebook()`

An alternative method will be to use `ctrl-D` on a new line after the input is supplied or 2 consecutive `ctrl-D` characters to notify end of input.

Multiprocessing and Distributed Computing, Julia Documentation Manual, **[https://docs.julialang.org/en/v1/manual/distributed-computing/](https://docs.julialang.org/en/v1/manual/distributed-computing/)**

Logging, Standard Libraries, Julia Documentation, **[https://docs.julialang.org/en/v1/stdlib/Logging/](https://docs.julialang.org/en/v1/stdlib/Logging/)**

Julia process starts with a single thread when launched. However, it can be launched with multiple threads by using the command `<strong>julia –t &lt;no_of_threads&gt;</strong>` or `<strong>julia –threads &lt;no_of_threads&gt;</strong>`. The same can be achieved by setting the environment variable `<strong>JULIA_NUM_THREADS</strong>` to the required number of threads2. By starting Julia with `<strong>julia –t 4</strong>`, the following code provides the number of active threads in the Julia environment.

When multiple threads are being executed in a program, synchronizing across them can be a concern. Locks are useful programming paradigms to address those needs. `<strong>Threads.Conditions()</strong>` are thread-safe condition objects and must be used for thread safety. The second issue is low-level atomic operations. Some of the LLVM defined low-level atomic operations are supported by Julia. Lastly, finalizers and garbage collection may get affected with multithreaded programs. We will suggest the user reviews the manuals on multithreading for a better understanding of the topic3:

`<strong>Cmd</strong>` objects are created by quoting an external command with backticks(`). There are also explicit constructors for `<strong>Cmd</strong>` objects as well1.

Anyone interested in implementing her own logger can create a subtype of the `<strong>AbstractLogger</strong>` type and implement the methods needed for the `<strong>AbstractLogger</strong>`. The details are documented in the Julia documentation on the `<strong>Logging</strong>` module6.

While Julia provides an elaborate distributed architecture, we will keep the discussion minimal for the sake of brevity and reduce the complexity it will bring into the text. However, interested readers are advised to refer to the Julia documentation manual on Multiprocessing and Distributed Computing4.

You can use *ctrl-C*; that will raise an interrupt exception and come out of the `<strong>read</strong>` method but your `<strong>String</strong>` could not be read5. This is a perfect place to use the `<strong>readline</strong>` method. `<strong>readline</strong>` will read one line till the `<strong>end of line</strong>` (`<strong>EOL</strong>`) character is got.

# 

# 

# 

Programming is a bigger art than science. Most programmers take artistic pride in their craft. They master the art over a period of time and gain expertise in one style of programming for substantial periods of their career. People who are used to programming imperative style of programming or object-oriented programming may find Julia a bit confusing. This chapter shall be able to familiarize these distinctions.

# 

In this chapter, we will cover the following topics:

*   Background
*   Guidelines for maintainability
*   Functional programming principles
*   Commonly used patterns
*   Contributing to open source

# 

In this chapter, the reader shall be able to understand, how Julia code is to be written. The community follows certain style guidelines that most Julia programmers follow. We will review certain patterns of functional programming and how they are used in Julia.

# 

Julia has many features that are LISP like. At the same time, it also has enough constructs for the imperative style of programming. While computer programmers prefer the imperative style of coding, mathematicians, and researchers tend to prefer functional programming for its ease in representing programs as mathematical function equivalents. We will delve into some of these differences in a subsequent section.

The second part of the programming is general guidelines and styles of code writing. These help in maintaining the code base. One potential example can be of coding standards, conventions of functions, and variable nomenclature. Unlike a language like Python, Julia does not syntactically depend on whitespace positions. This means one can easily write code that can become hard to read for another programmer. Julia community follows stringent recommendations or practices as a part of the code that is checked into the Julia GitHub repository. Most Julia programmers tend to appreciate and follow it in their code. We will discuss about some of these aspects when we talk about coding for maintainability.

# 

One of the classic requirement classifications[1](#e7p95xmz.html#n4upl4fndm3) in the software industry is FURPS:

1.  Functionality
2.  Usability
3.  Reliability
4.  Performance
5.  Supportability

Supportability is particularly of interest here as good support mandates readable code. Coding conventions help bridge the need for a larger class of developers. We will look at the style guidelines[2](#e7p95xmz.html#n4upl4fndm4) suggested in the Julia documentation.

1.  **Use Functions**: It is very easy for a REPL-based language to be mistaken as a scripting language. The dynamically typed, with all code written in a global scope (`<strong>Main</strong>` module), gives the language a flavor of a scripting language. However, using proper functions makes the code maintainable; moreover as functions can be written in a type-safe manner, they can be optimized better.
2.  **Code must be generalized and not type specific**: This concept can be explained easily with the following code:
    
    `<strong>julia&gt; addone(x) = x + one(x);<br>julia&gt; addone(5), addone(5.0), addone(5f0)<br>(6, 6.0, 6.0f0)</strong>`
    
    Julia has many methods like `<strong>one()</strong>` and `<strong>zero()</strong>` that use the type of the operand and judiciously provide values that do not require explicit type promotion in calculations. The same principle can be applied to your code making it easily extensible.
    
3.  **Keep the function scope narrow if that is the intent**: Where a function argument expects a specific type, the type must be specified. This ensures a run time error does not propagate further and no additional assertion is needed.
    
    `<strong>calc1() = 2, 1</strong>`
    
    `<strong>calc2() = 1.1, 1.2</strong>`
    
    `<strong>myvalidate(x::Int, y::Int) = x == y</strong>`
    
    `<strong>julia&gt; myvalidate(calc1()…)<br>false</strong>`
    
    `<strong>julia&gt; myvalidate(calc2()…)<br>MethodError: no method matching myvalidate(::Float64, ::Float64)</strong>`
    
    While `<strong>calc1()</strong>` is the proper kind of computation, `<strong>calc2()</strong>` is definitely erroneous, and `<strong>myvalidate()</strong>` ensures the error is localized. Second, any explicit type conversion if needed must be carried out by the caller and not the callee.
    
    `<strong>function myvalidate2(x, y)</strong>`
    
    `<strong>xi, yi = Int(x), Int(y)</strong>`
    
    `<strong>return xi == yi</strong>`
    
    `<strong>end</strong>`
    
    `<strong>julia&gt; myvalidate2(2, 3.0) # Not good style</strong>`
    
    `<strong>false</strong>`
    
    `<strong>julia&gt; myvalidate(2, Int(3.0)) # Better style</strong>`
    
    `<strong>false</strong>`
    
4.  **Append exclamation mark (!) to function that change parameters**: Where parameter values are modified the function name should have a clear indicator of an exclamation mark. The same will be further clarified in subsequent sections.
    
    `<strong>function double!(v::Vector)</strong>`
    
    `<strong>for i=firstindex(v):lastindex(v)</strong>`
    
    `<strong>v[i] *= 2</strong>`
    
    `<strong>end</strong>`
    
    `<strong>return v</strong>`
    
    `<strong>end<br>julia&gt; double!([1,2,3])</strong>`
    
    `<strong>3-element Array{Int64,1}:</strong>`
    
    `<strong>2</strong>`
    
    `<strong>4</strong>`
    
    `<strong>6</strong>`
    
5.  **Avoid complex data types**: Data types particularly used in conjunction with collections must be kept simpler. `<strong>Vector{Union{Int, Float, Function, MyType}}</strong>` should better be specified as `<strong>Vector{Any}</strong>`. It may be more efficient for the compiler to have simpler types. Similarly, `<strong>Union{Function, AbstractString}</strong>` can suggest possible improper design choice in the code.
6.  **Naming conventions**: Julia coders are used to certain naming conventions. Here are some: 
    *   Types start with capital letters and can be in Camel case: `<strong>MyType</strong>`, `<strong>AbstractArray{T}</strong>`, and so on.
    *   Module names follow the same convention as regular types.
    *   Functions must be in all lower case. 
        *   Simple predicates with merged words: `<strong>beginswith</strong>`, `<strong>isequal</strong>`, `<strong>haskey,</strong>` etc.
        *   Longer names particularly multipurpose functions are to be separated with an underscore (\_): `<strong>remotecall_fetch()</strong>`
    *   Global constants or environment variables as all capitals: `<strong>ENV</strong>`
7.  **Use function arguments matching to** `<strong>Base</strong>`: Here are some commonly used practices. 
    *   When functions or lambda are used as arguments they are best assigned to the beginning of the parameter such that they can be written as `<strong>function…</strong>``<strong>do</strong>` syntax.
        
        `<strong>mymap(f, arr) = f.(arr)</strong>`
        
        `<strong>julia&gt; mymap([1, 2, 3]) do x</strong>`
        
        `<strong>2x</strong>`
        
        `<strong>end</strong>`
        
    *   Similarly, the `<strong>Vararg</strong>` parameters appear at the end of the function arguments. `<strong>IO</strong>` parameters are typically the first arguments of the functions. `<strong>::Type{T}</strong>` kind of parameters constitute the first argument of the functions.
8.  **Judicious usage of static parameters**: Static parameters are recommended only when the parameters are actually needed.
    
    `<strong>double(x::T) where {T&lt;:Real} = 2x</strong>`
    
    `<strong>double(x::Real) = 2x</strong>`
    
    Both methods are equivalent. Only one method is created and the second method overwrites the first one. `<strong>methods()</strong>` call will list only one method. The parameter `<strong>T</strong>` though declared is not used in the function body. Hence, is considered redundant and optimized away.
    
    `<strong>julia&gt; methods(double)</strong>`
    
    `<strong># 1 method for generic function double:</strong>`
    
    `<strong>&nbsp;double(x::Real) in Main at In[20]:1</strong>`
    
    However, the following method is a very relevant method to have.
    
    `<strong>myeltype(v::Vector{T}) where {T&lt;:Real} = T</strong>`
    
    `<strong>julia&gt; myeltype([1.0, 2, 3])</strong>`
    
    `<strong>Float64</strong>`
    
9.  **Use lambdas only when needed**: Lambdas are very useful when you need a function without polluting the name space. Second, they are a very clean interface for `<strong>function…do</strong>` kind of syntax. However, when the function already has a defined name there is no value added in wrapping the function in a lambda. For example, `<strong>map(f, array)</strong>` is preferred over `<strong>map(x-&gt;f(x), array)</strong>`.
10.  **Do not overload** `<strong>Base</strong>` **methods for well-defined data types**: The following code will make the idea clear.
     
     `<strong>module MyModule</strong>`
     
     `<strong>Base.:(*)(x::Symbol, y::Symbol) =</strong>`
     
     `<strong>Symbol(string(x)*string(y))</strong>`
     
     `<strong>end</strong>`
     
     `<strong>julia&gt; :a*:b</strong>`
     
     `<strong>:ab</strong>`
     
     The preceding code is not confined to `<strong>MyModule</strong>` only. It can be accessed from anywhere after the `<strong>MyModule</strong>` is loaded. That can be risky as inadvertently one may change the behavior of a type that you have not defined. Unlike classical object-oriented languages, Julia is relatively flexible in terms of data hiding, private and public distinction. Hence, these kinds of guidelines are necessary for better system design.
     
11.  **Use try…catch only when absolutely needed**: Exception is a useful feature but exception handling also means the stacks have to be tracked and exceptions have to be specifically identified and required actions have to be taken. Ideal programming practice should ensure exceptions only occur sparingly, while normal failures due to inputs or checking for conditions while branching are handled as part of regular workflows. This ensures performance overheads of exception handling are limited.

# 

While in the previous section, we saw a few style issues that may affect performance or general programming paradigm constraints, there are some style issues related to code readability, presentation, and overall acceptance of code in for a community. Here is an example in C/C++, what is your style?

`<strong>int main(int argc, char** argv){</strong>`

`<strong>…</strong>`

`<strong>return 0;</strong>`

`<strong>…</strong>`

`<strong>}</strong>`

`<strong>Or</strong>`

`<strong>int main(int argc, char** argv)</strong>`

`<strong>{</strong>`

`<strong>…</strong>`

`<strong>return 0;</strong>`

`<strong>…</strong>`

`<strong>}</strong>`

There is nothing wrong in either. However, a group of programmers prefers one over the other while debating over the right way to program in C/C++. The same exists in Julia as well. Some packages prefer one style over the other. They all have their reasons supporting their preference. A general guideline is to follow the style the community adheres to. We will look at a few here but we will suggest preferring the Julia GitHub repository style is the best one, as most developers are used to the same. However, if you have a preference for another style make sure you follow it consistently. Nothing looks worse than an inconsistent style of code.

1.  **Indentation**: Space is always a better way to indent than tabs. People can set tabs to different shift locations and that may affect the indentation. The best way is to convert tabs to spaces when checking in code to avoid these tab inconsistencies. Many editors would automatically do this for you. Julia language GitHub repository has a preference for four spaces. Some packages prefer a two-space indent as well. Due to short cut eval in branching many a times the high depth of indents may not be needed. Here is an example:
    
    `<strong>for i = 1:200<br>&nbsp;&nbsp;&nbsp;&nbsp;if a != 0</strong>`
    
    `<strong>if b != 0</strong>`
    
    `<strong>&nbsp;# Do something</strong>`
    
    `<strong>end</strong>`
    
    `<strong>end</strong>`
    
    `<strong>end</strong>`
    
    `<strong>vs.</strong>`
    
    `<strong>for i = 1:200</strong>`
    
    `<strong>(a == 0 || b == 0) &amp;&amp; continue</strong>`
    
    `<strong># Do something</strong>`
    
    `<strong>end</strong>`
    
    As you can see, shortcut evaluations save substantial indentation depth to permit wider indent spaces.
    
2.  **Usage of brackets**: Braces are not commonly used unless there is a real need to break the normal operator precedence[3](#e7p95xmz.html#n4upl4fndm5) in Julia.
    
    `<strong>if a == 0 &amp;&amp; b == 0</strong>`
    
    `<strong># Do something</strong>`
    
    `<strong>end</strong>`
    
    `<strong>is preferred over:</strong>`
    
    `<strong>if (a == 0) &amp;&amp; (b == 0)</strong>`
    
    `<strong># Do something</strong>`
    
    `<strong>end</strong>`
    
    Thus, it is advised to use minimal braces and only when absolutely needed.
    
3.  **Whitespaces around operators**: Julia does not depend on whitespaces for syntax in most cases. However, in some places, whitespaces are mandated. For example, in tertiary branching `<strong>i &gt; 0 ? 1 : -1</strong>`, space is expected around question mark (?) and colon (:). `<strong>elseif</strong>` is a single word; else if is a syntax error. In general, it is considered a good practice to use whitespaces around all operators.
    
    `<strong>x = x + 1</strong>` is preferred over `<strong>x=x+1</strong>`.
    
    However, in a function argument such whitespaces may not be provided.
    
    `<strong>f(arg1, key=v+1)</strong>` is preferred over `<strong>f(arg1, key = v + 1)</strong>`.
    
4.  **Define multiline functions with the verbose syntax**: The following code is also a definition of a function but definitely not very readable.
    
    `<strong>F(x) = begin</strong>`
    
    `<strong>if iseven(x)</strong>`
    
    `<strong>2x</strong>`
    
    `<strong>else</strong>`
    
    `<strong>3x</strong>`
    
    `<strong>end</strong>`
    
    `<strong>end</strong>`
    
    The preferred styles are stated as follows:
    
    `<strong>function F(x)</strong>`
    
    `<strong>if iseven(x)</strong>`
    
    `<strong>return 2x</strong>`
    
    `<strong>else</strong>`
    
    `<strong>return 3x</strong>`
    
    `<strong>end</strong>`
    
    `<strong>end</strong>`
    
    `<strong>or</strong>`
    
    `<strong>F(x) = iseven(x) ? 2x : 3x</strong>`
    
    The short form is to be used for single-line mathematical constructs and the longer form for multiple lines in the function body.
    
5.  **Character length limits of a line**: This varies from project to project. Julia GitHub repository prefers character limits to be set to 92 characters. Some projects also suggest 120 characters and some even do not place a limit. However, a limit is useful to make the code consistent and readable. The author prefers 80 characters as you can edit two files side by side if you are using an editor like emacs on a 1080p monitor. Whatever value is decided all the contributors must comply with it.

Please refer to the code formatting guidelines of Julia language[4](#e7p95xmz.html#n4upl4fndm6) for a better understanding of some of the other formatting-related suggestions. Certain other organizations and individuals have come up with their own styles^([5](#e7p95xmz.html#n4upl4fndm7),[6](#e7p95xmz.html#n4upl4fndm8)) that are quite popular in the community as well.

# 

Functional programming is nothing new. In fact, it is the oldest form of programming that came into existence due to research of Alonzo Church on Lambda Calculus[7](#e7p95xmz.html#n4upl4fndm9). Even before the *Von Neumann* concept of computers became mainstream, where the computer had memory and a state machine transitioned it based on every step of action taken. The memory is tracked on every step of the execution of the code. This style of sequential programming is known as **Imperative Programming**.

# 

Let’s traverse a list and print all the values.

`<strong>julia&gt; a = [1, 2, 3];</strong>`

`<strong>julia&gt; for i=firstindex(a):lastindex(a)</strong>`

`<strong>println(a[i])</strong>`

`<strong>&nbsp;end</strong>`

`<strong>1</strong>`

`<strong>2</strong>`

`<strong>3</strong>`

The declarative statement of traversing the list is explained in a fairly detailed stepwise fashion in imperative programming.

1.  Start from the first index of the array and initialize the counter (`<strong>i</strong>`).
2.  If the counter (`<strong>i</strong>`) is less than or equal to the last index of the array. 
    1.  Pick up the value stored at the counter (`<strong>i</strong>`) location of the array (`<strong>a</strong>`)
    2.  Print the value to the `<strong>stdout</strong>`.
    3.  Increment the counter (`<strong>i</strong>`) by 1.
3.  Go to 2.

Contrast that to the code as follows:

`<strong>foreach(println, a)</strong>`

The closest English statement that explains the code is traverse the array and print all the values to `<strong>stdout</strong>`. This is a declarative style of programming. Julia provides you all the constructs of imperative programming, while providing the flexibility of declarative programming as well. While the declarative style of programming is the core of functional programming, there are a few other attributes as well.

# 

The mathematical definition of a function is a mapping. You input a parameter from the domain of a function and the output obtained is a mapping to a value that is in the range of the function:

![](n4upl4fndrh.jpeg)

**Figure 10.1:** Function f mapping from domain A to range B

The mapping is rigid for example `<strong>y1 = f(x1)</strong>`. And `<strong>f</strong>` can never change the value of `<strong>x1</strong>`. This essentially means the function cannot change the state of the input and the input data are immutable. You can associate it with the ability to define immutable types as a struct. Functions in Julia, that can change the input parameters are suggested to be with a name ending with a bang (!). Those are the functions that can cause a side effect.

`<strong>julia&gt; a = [1, 2, 3];</strong>`

`<strong>julia&gt; pop!(a)</strong>`

`<strong>3</strong>`

`<strong>julia&gt; a</strong>`

`<strong>2-element Array{Int64,1}:</strong>`

`<strong>1</strong>`

`<strong>2</strong>`

The preceding `<strong>pop!()</strong>` method changes the array state and introduces a side effect. The side effects get harder to track when the function is dependent on global variables whose states can change as the function no longer return the same output for the same input.

# 

Higher-order functions act like functions of other functions. They essentially can be considered as a function of a function:

![](n4upl4fndri.jpeg)

**Figure 10.2:** g o f(x) = g(f(x)) is a higher order function h(x)

In the preceding example, `<strong>h = g ∘ f</strong>` is a function composition. Julia supports such definitions as well.

`<strong>julia&gt; f(x) = 2x;</strong>`

`<strong>julia&gt; g(x) = x*x;</strong>`

`<strong>julia&gt; h = g ∘ f</strong>`

`<strong>julia&gt; h(3)</strong>`

`<strong>36</strong>`

Had `<strong>h</strong>` been a function of `<strong>f</strong>` as a parameter? These functional types are common in mathematics. Derivative of a function is such a relationship. `<strong>map()</strong>` function also takes a function as an argument that we have seen several times earlier. These are essentially higher-order functions. They help in declarative programming.

# 

In the section on functions with no side effects, we discussed about immutability. `<strong>String</strong>` and `<strong>struct</strong>` types are immutable as well. Hence a function with no side effects can allocate additional temporary memory while manipulating strings or collections of `<strong>struct</strong>` data types. A large number of small allocations may act as a performance penalty. Usage of `<strong>map</strong>`, `<strong>reduce,</strong>` or `<strong>mapreduce</strong>` can help minimize temporary space allocations and can make immutable functions more efficient.

We discussed a few aspects of functional programming. Those interested in a concise conceptual understanding of functional programming with multiple programming languages can refer to *Functional Thinking*[8](#e7p95xmz.html#n4upl4fndna). It is natural for the readers to wonder if they should follow an imperative style or functional style. Julia is rather a flexible language in that respect. Although at many places you will find declarative programs, recursive functions, comprehensions, or similar features, Julia is not prescriptive about any specific style of programming. The language provides equally useful constructs to program in an imperative style. Sometimes immutability may lead to increased intermediate variable allocations, affecting the performance of the code. In such conditions, it may be ideal to use functions with side effects.

# 

In the previous section, we visited the functional programming basics and looked at how they are relevant to programming in Julia. However, the application of the principles of functional programming in any language can vary based on the language capabilities. In this section, we shall look at a few commonly used patterns and how to implement them in Julia. A detailed treatment on this topic is available in *Hands-On Design Patterns and Best Practices with Julia*[9](#e7p95xmz.html#n4upl4fndnb).

# 

Any function definition in Julia can act as an interface. Suppose we would like to create a module for 2-D geometry and realize the 2-D shapes must have methods for area and bounding box. The interface may look something like this.

`<strong>module geom</strong>`

`<strong># All shape objects must have implementation for the following methods.</strong>`

`<strong># area(x): shall return the area of a 2-D shape</strong>`

`<strong>function area end</strong>`

`<strong># bbox(x): shall return the bounding box of a 2-D shape</strong>`

`<strong>function bbox end</strong>`

`<strong>end</strong>`

The interfaces are mere directives. However, one can make them hard interfaces by forcing a default implementation that throws an error.

`<strong>julia&gt; module geom</strong>`

`<strong>area(x) = throw(Base.MethodError(area, (x,)))</strong>`

`<strong>bbox(x) = throw(Base.MethodError(bbox, (x,)))</strong>`

`<strong>struct Rectangle</strong>`

`<strong>x; y; w; h</strong>`

`<strong>end</strong>`

`<strong>export Rectangle, area, bbox</strong>`

`<strong>end</strong>`

`<strong>Main.geom</strong>`

`<strong>julia&gt; using .geom</strong>`

`<strong>julia&gt; r = Rectangle(0, 0, 10, 20)</strong>`

`<strong>Rectangle(0, 0, 10, 20)</strong>`

`<strong>julia&gt; area(r)</strong>`

`<strong>ERROR: MethodError: no method matching area(::Rectangle)</strong>`

`<strong>…</strong>`

The default implementation can be an identity function that returns the input, thus making the interface act as a soft interface.

`<strong>julia&gt; module geom1</strong>`

`<strong>area(x) = identity(x)</strong>`

`<strong>bbox(x) = identity(x)</strong>`

`<strong>struct Rectangle</strong>`

`<strong>&nbsp;x; y; w; h</strong>`

`<strong>end</strong>`

`<strong>export Rectangle, area, bbox</strong>`

`<strong>end</strong>`

`<strong>julia&gt; r = geom1.Rectangle(0, 0, 10, 20)</strong>`

`<strong>Main.geom1.Rectangle(0, 0, 10, 20)</strong>`

`<strong>julia&gt; geom1.area(r)</strong>`

`<strong>Main.geom1.Rectangle(0, 0, 10, 20)</strong>`

# 

The function `<strong>area</strong>` and `<strong>bbox</strong>` do not carry any meaning for a generic type `<strong>Any</strong>`. One way to enforce the interface on shapes like `<strong>Rectangle</strong>`, `<strong>Triangle,</strong>` or `<strong>Circle</strong>` types will be by deriving them from a super type of `<strong>Shape</strong>`.

`<strong>julia&gt; module geom2</strong>`

`<strong>abstract type Shape end</strong>`

`<strong>area(x::Shape) = nothing</strong>`

`<strong>bbox(x::Shape) = nothing</strong>`

`<strong>struct Rectangle &lt;: Shape</strong>`

`<strong>&nbsp;x; y; w; h</strong>`

`<strong>end</strong>`

`<strong>end</strong>`

`<strong>julia&gt; r = geom2.Rectangle(0, 0, 10, 20)</strong>`

`<strong>Main.geom2.Rectangle(0, 0, 10, 20)</strong>`

`<strong>julia&gt; geom2.area(r)</strong>`

We can introduce a `<strong>Polygon</strong>` to the module. Polygons are closed shapes of multiple points joined by straight lines.

`<strong>julia&gt; module geom2</strong>`

`<strong>…</strong>`

`<strong>struct Polygon &lt;: Shape</strong>`

`<strong>pts::Vector{Tuple{Any, Any}}</strong>`

`<strong>end</strong>`

`<strong>…</strong>`

`<strong>end</strong>`

Suppose we were to consider shapes where the straight lines are not closed, we will get a `<strong>PolyLine</strong>` type. For an open shape, there is no concept of area. So, the function `<strong>area()</strong>` should throw an error. Generally, a good object-oriented design the isa relationship must be complete in every respect. A `<strong>Polygon</strong>` and `<strong>PolyLine</strong>` both must exhibit all the properties of a `<strong>Shape</strong>`. If area(`<strong>::PolyLine</strong>`) throws an error, `<strong>PolyLine</strong>` isa `<strong>Shape</strong>` relationship shall be compromised. So, one may suggest introducing `<strong>OpenShape</strong>` and `<strong>ClosedShape</strong>` as abstract types. `<strong>area()</strong>` function will exist only for `<strong>ClosedShape</strong>`. Here is a possible implementation for the same.

`<strong>julia&gt; module geom3</strong>`

`<strong>abstract type Shape end</strong>`

`<strong>bbox(x::Shape) = nothing</strong>`

`<strong>abstract type OpenShape end</strong>`

`<strong>struct PolyLine &lt;: OpenShape</strong>`

`<strong>pts::Vector{Tuple{Any, Any}}</strong>`

`<strong>end</strong>`

`<strong>abstract type ClosedShape end</strong>`

`<strong>area(x::ClosedShape) = nothing</strong>`

`<strong>struct Rectangle &lt;: ClosedShape</strong>`

`<strong>&nbsp;x; y; w; h</strong>`

`<strong>end</strong>`

`<strong>struct Polygon &lt;: ClosedShape</strong>`

`<strong>pts::Vector{Tuple{Any, Any}}</strong>`

`<strong>end</strong>`

`<strong>end</strong>`

If we would like to introduce `<strong>Circle</strong>` and `<strong>Arc</strong>` to the module, both are shapes that do not have any straight lines in them. If we were to introduce more classifications like `<strong>LinearShape</strong>` and `<strong>NonLinearShape</strong>` as new abstract types, we really cannot scale it well enough as Julia does not have multiple inheritances. We will end up creating artificial types like `<strong>NonLinearClosedShape</strong>` to accommodate a `<strong>Circle</strong>` and a `<strong>NonLinearOpenShape</strong>` for the `<strong>Arc</strong>`. While inheriting from abstract types is a good way to enforce the interface, with single inheritance limitations it may not be practical to conceptualize it for a large number of classifications. However, the solution that may work out in such conditions is traits.

# 

Traits were identified by *Tim Holy*, a Julia contributor, and he proposed a modeling philosophy to distinguish functional differences from `<strong>isa</strong>` relationships. These functional differentiations are called **Holy Traits** or simply Traits. If we were to look at our `<strong>geom</strong>` module we can simplify the design by the following concepts:

1.  All geometric shapes derive from abstract type `<strong>Shape</strong>`.
2.  All shapes have a bounding box which can be obtained from a call to `<strong>bbox(::Shape)</strong>`.
3.  Some shapes have the trait of having a valid enclosed area. For those shapes, the `<strong>area()</strong>` function shall be implemented. It will not be implemented for other shapes.

From the preceding description, all geometric shapes must be derived from `<strong>Shape</strong>` only. All the shapes will have a `<strong>bbox()</strong>` method.

`<strong>module geom4</strong>`

`<strong>abstract type Shape end</strong>`

`<strong>bbox(x::Shape) = nothing</strong>`

`<strong>struct PolyLine &lt;: Shape</strong>`

`<strong>pts::Vector{Tuple{Any, Any}}</strong>`

`<strong>end</strong>`

`<strong>struct Rectangle &lt;: Shape</strong>`

`<strong>&nbsp;x; y; w; h</strong>`

`<strong>end</strong>`

`<strong>struct Polygon &lt;: Shape</strong>`

`<strong>pts::Vector{Tuple{Any, Any}}</strong>`

`<strong>end</strong>`

`<strong>### Here, we will add the traits code ###</strong>`

`<strong>end</strong>`

But only some of the shapes will have the `<strong>area()</strong>` method. Those will be plugged into the highlighted area. The trait has essentially two attribute-less types; one for the existence of the trait and the other for non-existence of the trait.

`<strong>abstract type HasAreaTrait end</strong>`

`<strong>struct HasArea &lt;: HasAreaTrait end</strong>`

`<strong>struct HasNoArea &lt;: HasAreaTrait end</strong>`

We will also specify which shape has the trait which does not. By default, a shape has no area.

`<strong>HasAreaTrait(::Type) = HasNoArea()</strong>`

`<strong>HasAreaTrait(::Type{Polygon}) = HasArea()</strong>`

`<strong>HasAreaTrait(::Type{Rectangle}) = HasArea()</strong>`

Lastly, we have to make sure the area function utilizes the trait properly.

`<strong>area(x::T) where {T&lt;:Shape} = area(HasAreaTrait(T), x)<br>area(::HasArea, x::T) where {T &lt;: Shape} =<br>&nbsp;&nbsp;&nbsp;&nbsp;error("area(::HasArea, $T) method must be implemented")<br>area(::HasArea, r::Rectangle) = r.w*r.h</strong>`

Here are results:

`<strong>julia&gt; geom4.area(geom4.Rectangle(0, 0, 10, 20))</strong>`

`<strong>200</strong>`

`<strong>pl = geom4.PolyLine([(0, 0), (10, 0), (10, 20), (0, 20)])</strong>`

`<strong>area(::Rectangle)</strong>` gets dispatched to `<strong>area(::HasArea, ::Rectangle)</strong>` through the traits framework which is implemented and returns 200.

`<strong>julia&gt; geom4.area(geom4.Polygon([(0, 0), (10, 0), (10, 20), (0, 20)]))</strong>`

`<strong>area(::HasArea, Main.geom4.Polygon) method must be implemented</strong>`

`<strong>…</strong>`

`<strong>area(::Polygon)</strong>` gets dispatched to `<strong>area(::HasArea, ::Polygon)</strong>` which is the generic parametric method asking for specific implementation.

`<strong>julia&gt; geom4.area(geom4.PolyLine([(0, 0), (10, 0), (10, 20), (0, 20)]))</strong>`

`<strong>MethodError: no method matching area(::Main.geom4.HasNoArea, ::Main.geom4.PolyLine)</strong>`

`<strong>Closest candidates are:</strong>`

`<strong>area(!Matched::Main.geom4.HasArea, ::T) where T&lt;:Main.geom4.Shape at In[24]:26</strong>`

`<strong>…</strong>`

`<strong>area(::PolyLine)</strong>` gets dispatched to `<strong>area(::HasNoArea, ::PolyLine)</strong>` which is not implemented. Hence, the generic `<strong>MethodError</strong>` is reported.

Traits are very useful patterns used in several places in Julia. Collections are a varied set of functionalities and one may see several such patterns in their implementations. For example, most collections have the support for the iterator framework. And iterator behaviors are differentiated as traits.

# 

Sometimes we will like to introduce additional functionality for a type while a significant part of the functionality already exists. However, only certain additional functionality may be needed. Julia types do not inherit attributes from concrete types. Thus the only way to extend an object is by composing the object and delegating it to the composed type. This will get clearer when we look at the following example.

Let us say we want to introduce a Square type that has all the functions defined for a Rectangle type at the same time it has a constructor that only takes 3 parameters as the width and height are the same.

`<strong>module geom4</strong>`

`<strong>abstract type Shape end</strong>`

`<strong>bbox(x::Shape) = nothing</strong>`

`<strong>struct Rectangle &lt;: Shape</strong>`

`<strong>&nbsp;x; y; w; h</strong>`

`<strong>end</strong>`

`<strong>bbox(x::Rectangle) = x</strong>`

`<strong>### Square has Rectangle as an attribute ###</strong>`

`<strong>struct Square &lt;: Shape</strong>`

`<strong>r::Rectangle</strong>`

`<strong>Square(x, y, w) = new(Rectangle(x, y, w, w))</strong>`

`<strong>end</strong>`

`<strong>abstract type HasAreaTrait end</strong>`

`<strong>struct HasArea &lt;: HasAreaTrait end</strong>`

`<strong>struct HasNoArea &lt;: HasAreaTrait end</strong>`

`<strong>HasAreaTrait(::Type) = HasNoArea()</strong>`

`<strong>HasAreaTrait(::Type{Rectangle}) = HasArea()</strong>`

`<strong>area(x::T) where {T&lt;:Shape} = area(HasAreaTrait(T), x)</strong>`

`<strong>area(::HasArea, x::T) where {T &lt;: Shape} = error("area(::HasArea, $T) method must be implemented")</strong>`

`<strong>area(::HasArea, r::Rectangle) = r.w*r.h</strong>`

`<strong>### Code for delegation ###</strong>`

`<strong>for op in [:bbox, :area]</strong>`

`<strong>@eval $op(s::Square) = ($op)(s.r)</strong>`

`<strong>end</strong>`

`<strong>end</strong>`

A `<strong>Square</strong>` object has an instance of a `<strong>Rectangle</strong>` as its attribute. Thus, `<strong>bbox</strong>` and `<strong>area</strong>` that are already defined for the `<strong>Rectangle</strong>` object are used for the `<strong>Square</strong>` object. `<strong>Lazy.jl</strong>`[10](#e7p95xmz.html#n4upl4fndnc) package has a few additional macros like `<strong>@forward</strong>` defined to aid delegation.

# 

Type attributes in Julia are public and transparent. There is hardly any data encapsulation possible. However, sometimes one may need data hiding and accessor methods (getter and setter) are used to access such variables. One possible reason can be data validation before setting values.

`<strong>module geom</strong>`

`<strong>mutable struct Rectangle</strong>`

`<strong>_x; _y; _w; _h</strong>`

`<strong>function Rectangle(x, y, w, h)</strong>`

`<strong>(w &lt;= 0 || h &lt;= 0) &amp;&amp;</strong>`

`<strong>&nbsp;error("width and height must be positive")</strong>`

`<strong>new(x, y, w, h)</strong>`

`<strong>end</strong>`

`<strong>end</strong>`

`<strong>w(r::Rectangle) = r._w</strong>`

`<strong>function w!(r::Rectangle, tw)<br></strong>`

`<strong>tw &lt;= 0 &amp;&amp; error("width cannot be negative")</strong>`

`<strong>r._w = tw</strong>`

`<strong>end</strong>`

`<strong>end</strong>`

`<strong>w()</strong>` and `<strong>w!()</strong>` are kept as the getter and setter methods; while `<strong>_w</strong>` being the attribute starting with an underscore (`<strong>_</strong>`) is kind of a directive that such attribute should not be accessed directly.

# 

About 10–15 years back, young graduating students would approach organizations or even employees working in various organizations seeking live projects. Many of these students had almost no exposure to programming, had just picked up coding from various coaching or training programs, and had no understanding of any real-life system. Undoubtedly, they had difficulty in finding opportunities as software professionals. Today, if such a student approaches, I will ask her if she has looked at *GitHub*, *GitLab*, or any of these open source repositories for contribution. Of course, the learning curve can be high for active coding, but soon one will realize a lot of good coding is about reading other people's code as much as it is developing code afresh. It is equally helpful for experienced developers who would like to switch gears and learn a new trait.

It is difficult to find an organization today that does not use any open-source code. At the same time, very few people working in organizations contribute to open source. We believe there is significant value in contributing to open source. Some adding to the organization and some to the individual:

*   **Visibility**: Most open source contributions, change history, and discussions are available in the comments and code contributions. The clarity of your understanding, your ability to influence and convince the ideas you have becomes apparent from your discussions.
*   **Learning**: You get to learn new ideas from fellow contributors and maintainers. Moreover, looking at the code and reading through the change comments and threads give you enough learning experience.
*   **Remote working**: Before the pandemic hit world embraced remote working on a large scale, there was inherent skepticism to working remotely. The open-source communities working across the globe made people better workers who can contribute remotely.
*   **Fear of the unknown**: Most organizations find it hard to use third-party open-source software as they believe it will be hard to use as there may not be any good maintainer for the project. Contributing makes you get over some of the unknowns of the project. You interact with people active on the project. You can reach out to them in case of need.
*   **Giving back**: As an organization, you may have used open-source technologies. Contributing back directly by active contribution is an alternative to monetary payout.

# 

Julia is one of the most forthcoming communities in terms of accepting contributions. Anyone can submit to the code base through GitHub **pull requests** (**PR**). One of the reviewers reviews the PRs for the correctness and merges them into the codebase. It may take several iterations to update the code. The code is checked for algorithmic and logical correctness. The coding and style guidelines are given the similar level of importance as well. Not just the core language, one can contribute to any of the 4000+ packages that are being actively developed as well.

# 

Programming guidelines help a programmer understand the nuances of a language and how to write maintainable code for the community of developers. In this chapter, we looked at a few programming styles, code formatting, and style considerations. In the end, we looked at a few patterns relevant to Julia. We also explored aspects of functional programming. Practice is the only way for someone to master a programming paradigm. While we discussed a few pointers on how some functionalities work, there is a lot that remains on the part of the reader to work on various use cases to get familiarity with the language. In the next chapter, we will look at ways to improve the performance of Julia applications and any practices that can aid such coding.

# 

1.  How can one define functions in Julia? Is there a concept of forward declaring a function in Julia?
2.  `<strong>map()</strong>` and `<strong>foreach()</strong>` both act on each element of a collection. Is there any situation where one should use one over the other?
3.  Iterator behaviors in collections are implemented as traits. Explain how this is implemented for `<strong>Array</strong>` and `<strong>Dict</strong>` collections. Is there any difference between the two implementations?
4.  What are hard and soft interfaces? Show both with some examples.
5.  Introduce your own integer type that will be read and written as a roman numeral. Use the delegation pattern to enhance your implementation. You can refer to the Julia package `<strong>RomanNumerals.jl</strong>`.

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

[1](#e7p95xmz.html#n4upl4fndnd) FURPS, Wikipedia, **[https://en.wikipedia.org/wiki/FURPS](https://en.wikipedia.org/wiki/FURPS)**

[2](#e7p95xmz.html#n4upl4fndne) Style Guide, Julia Documentation, **[https://docs.julialang.org/en/v1/manual/style-guide/](https://docs.julialang.org/en/v1/manual/style-guide/)**

[3](#e7p95xmz.html#n4upl4fndnf) Operator Precedence and Associativity, Julia Documentation, **[https://docs.julialang.org/en/v1/manual/mathematical-operations/#Operator-Precedence-and-Associativity](https://docs.julialang.org/en/v1/manual/mathematical-operations/#Operator-Precedence-and-Associativity)**

[4](#e7p95xmz.html#n4upl4fndng) Notes for Julia Contributors **[https://github.com/JuliaLang/julia/blob/master/CONTRIBUTING.md](https://github.com/JuliaLang/julia/blob/master/CONTRIBUTING.md)**

[5](#e7p95xmz.html#n4upl4fndnh) Blue: a Style Guide for Julia, **[https://github.com/invenia/BlueStyle](https://github.com/invenia/BlueStyle)**

[6](#e7p95xmz.html#n4upl4fndni) YASGuide - Yet Another Style Guide For Julia, **[https://github.com/jrevels/YASGuide](https://github.com/jrevels/YASGuide)**

[7](#e7p95xmz.html#n4upl4fndnj) Mike Loukides, What is Functional Programming, O’reilly Radar Blogs, 8^(th) Dec 2020. **[https://www.oreilly.com/radar/what-is-functional-programming/](https://www.oreilly.com/radar/what-is-functional-programming/)**

[8](#e7p95xmz.html#n4upl4fndnk) Neal Ford, Functional Thinking, O’Reilly Media, 2014

[9](#e7p95xmz.html#n4upl4fndnl) Tom Kwong, Stefan Karpinski, Hands-On Design Patterns and Best Practices with Julia, Packt Publishing, January 2020

[10](#e7p95xmz.html#n4upl4fndnm) Lazy.jl, **[https://github.com/MikeInnes/Lazy.jl](https://github.com/MikeInnes/Lazy.jl)**

We discussed a few aspects of functional programming. Those interested in a concise conceptual understanding of functional programming with multiple programming languages can refer to *Functional Thinking*8. It is natural for the readers to wonder if they should follow an imperative style or functional style. Julia is rather a flexible language in that respect. Although at many places you will find declarative programs, recursive functions, comprehensions, or similar features, Julia is not prescriptive about any specific style of programming. The language provides equally useful constructs to program in an imperative style. Sometimes immutability may lead to increased intermediate variable allocations, affecting the performance of the code. In such conditions, it may be ideal to use functions with side effects.

FURPS, Wikipedia, **[https://en.wikipedia.org/wiki/FURPS](https://en.wikipedia.org/wiki/FURPS)**

Operator Precedence and Associativity, Julia Documentation, **[https://docs.julialang.org/en/v1/manual/mathematical-operations/#Operator-Precedence-and-Associativity](https://docs.julialang.org/en/v1/manual/mathematical-operations/#Operator-Precedence-and-Associativity)**

In the previous section, we visited the functional programming basics and looked at how they are relevant to programming in Julia. However, the application of the principles of functional programming in any language can vary based on the language capabilities. In this section, we shall look at a few commonly used patterns and how to implement them in Julia. A detailed treatment on this topic is available in *Hands-On Design Patterns and Best Practices with Julia*9.

Style Guide, Julia Documentation, **[https://docs.julialang.org/en/v1/manual/style-guide/](https://docs.julialang.org/en/v1/manual/style-guide/)**

Tom Kwong, Stefan Karpinski, Hands-On Design Patterns and Best Practices with Julia, Packt Publishing, January 2020

Neal Ford, Functional Thinking, O’Reilly Media, 2014

Blue: a Style Guide for Julia, **[https://github.com/invenia/BlueStyle](https://github.com/invenia/BlueStyle)**

Notes for Julia Contributors **[https://github.com/JuliaLang/julia/blob/master/CONTRIBUTING.md](https://github.com/JuliaLang/julia/blob/master/CONTRIBUTING.md)**

Mike Loukides, What is Functional Programming, O’reilly Radar Blogs, 8^(th) Dec 2020. **[https://www.oreilly.com/radar/what-is-functional-programming/](https://www.oreilly.com/radar/what-is-functional-programming/)**

YASGuide - Yet Another Style Guide For Julia, **[https://github.com/jrevels/YASGuide](https://github.com/jrevels/YASGuide)**

*   **Usage of brackets**: Braces are not commonly used unless there is a real need to break the normal operator precedence3 in Julia. 
    
    `<strong>if a == 0 &amp;&amp; b == 0</strong>`
    
    `<strong># Do something</strong>`
    
    `<strong>end</strong>`
    
    `<strong>is preferred over:</strong>`
    
    `<strong>if (a == 0) &amp;&amp; (b == 0)</strong>`
    
    `<strong># Do something</strong>`
    
    `<strong>end</strong>`
    
    Thus, it is advised to use minimal braces and only when absolutely needed.
    

Please refer to the code formatting guidelines of Julia language4 for a better understanding of some of the other formatting-related suggestions. Certain other organizations and individuals have come up with their own styles^(5,6) that are quite popular in the community as well.

^(5,6) ^(5,6) 

Functional programming is nothing new. In fact, it is the oldest form of programming that came into existence due to research of Alonzo Church on Lambda Calculus7. Even before the *Von Neumann* concept of computers became mainstream, where the computer had memory and a state machine transitioned it based on every step of action taken. The memory is tracked on every step of the execution of the code. This style of sequential programming is known as **Imperative Programming**.

Lazy.jl, **[https://github.com/MikeInnes/Lazy.jl](https://github.com/MikeInnes/Lazy.jl)**

A `<strong>Square</strong>` object has an instance of a `<strong>Rectangle</strong>` as its attribute. Thus, `<strong>bbox</strong>` and `<strong>area</strong>` that are already defined for the `<strong>Rectangle</strong>` object are used for the `<strong>Square</strong>` object. `<strong>Lazy.jl</strong>`10 package has a few additional macros like `<strong>@forward</strong>` defined to aid delegation.

One of the classic requirement classifications1 in the software industry is FURPS:

Supportability is particularly of interest here as good support mandates readable code. Coding conventions help bridge the need for a larger class of developers. We will look at the style guidelines2 suggested in the Julia documentation.

# 

# 

# 

Performance is the core feature and basic premise on which the Julia language has been developed. Hence, it is only natural to understand the various tools and techniques available with the system that help write high-performance code.

# 

In this chapter, we will cover the following topics:

*   Background
*   Benchmarking
*   Code generation tools
*   Profiling
*   Guidance for high-performance code

# 

In this chapter, the reader shall be able to code for better performance. We shall look at the benchmark tools and understand how to profile the code. Julia code generation is a staged process and we can look at the generated code at various stages of generation as a means to understand the optimizations carried out. In the end, we will review some of the patterns and styles that help the user in writing high-performance code.

# 

*The first principle of optimization is don’t*[1](#9ztdqvro.html#n4upl4fndif). The recommendation was given by *Kernighan* and *Pike*, the masters of Unix operating system, in their seminal book *The Practice of Programming*. Nothing much has changed over two decades. A correctly working program is far superior to an incorrect fast program. However, many workarounds are taken in ensuring a program behaves close to the performance that is acceptable. There is nothing like absolute performance or code optimized for all conditions. The code that is high performing in today’s standards may be much less in computational capability than a relatively simpler application in the future. Voyager, the first manmade object to leave the solar system, had much lesser computing power than a modern-day cell phone[2](#9ztdqvro.html#n4upl4fndig). One does not have to really optimize every bit of code manually. The code compiled by many of the optimal code generators and compilers are far superior to manually optimized code in most cases. Modern languages like Julia utilize LLVM to handle the cross-platform optimal code generation and address many of the well-known optimization issues during compilation or code generation. One may ask if the hardware is cheap and easily accessible, why do we need to bother about optimized code? The answer lies in however cheaper hardware may get you will need to squeeze that extra bit from it.

# 

Running several applications over a single processor on a single thread is not true simultaneous multitasking. The operating system preempts the tasks based on a schedule, letting the processor to execute one task at a time. The user gets a feeling that all the tasks are running simultaneously, while they are only executed for small intervals and switched over to the next. In **Graphical User Interfaces** (**GUI**)-based applications, the responsiveness of the user interface to user inputs is given higher importance over the execution of other background tasks to completion. With multitasked applications running long computationally intensive tasks on single-processor systems, the usual practice is to process UI events intermittently to keep the UI responsive. This is known as **idle loop processing**[3](#9ztdqvro.html#n4upl4fndih) in the Windows systems. Here the optimal response time is given priority over raw execution speed. Hence, sheer execution speed of the code may not be the objective of all code optimization projects.

When processors did not have trigonometric functions as part of the instruction sets, computations of trigonometric functions would be time consuming as they were to be computed by software emulations. The performance-sensitive applications like game programs would simulate the behavior with the following mathematical equations.

![](n4upl4fndqh.jpeg)

They would essentially keep lookup values for *sinθ* and *cosθ* at 15- or 30-degree intervals and compute intermediate values using the incremental equations given previously. Tables generated at 15-degree intervals using the preceding equations are still within significant range of accuracy.

`<strong>julia&gt; n = 6;</strong>`

`<strong>δ = pi/180*(90/n);<br>sinδ, cosδ = δ, (1 - δ*δ/2);</strong>`

`<strong>m = Matrix{Float64}(undef, (n+1, 2));</strong>`

`<strong>m[1, 1], m[1, 2] = 0.0, 1.0;</strong>`

`<strong>for i = 1:n</strong>`

`<strong>m[i+1, 1] = m[i, 1]*cosδ + m[i, 2]*sinδ</strong>`

`<strong>m[i+1, 2] = m[i, 2]*cosδ - m[i, 1]*sinδ</strong>`

`<strong>end</strong>`

`<strong>julia&gt; m<br>7×2 Array{Float64,2}:</strong>`

`<strong>0.0&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;1.0</strong>`

`<strong>0.261799&nbsp;&nbsp; 0.965731</strong>`

`<strong>0.505655&nbsp;&nbsp; 0.864097</strong>`

`<strong>0.714547&nbsp;&nbsp; 0.702104</strong>`

`<strong>0.87387&nbsp;&nbsp;&nbsp;&nbsp;0.490976</strong>`

`<strong>0.97246&nbsp;&nbsp;&nbsp;&nbsp;0.245371<br><br>&nbsp;1.00337&nbsp;&nbsp; -0.0176268</strong>`

`<strong>julia&gt; m1 = [[sin(i*δ) for i=0:n] [cos(i*δ) for i=0:n]]<br>7×2 Array{Float64,2}:</strong>`

`<strong>0.0&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 1.0</strong>`

`<strong>0.258819&nbsp;&nbsp;0.965926</strong>`

`<strong>0.5&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 0.866025</strong>`

`<strong>0.707107&nbsp;&nbsp;0.707107</strong>`

`<strong>0.866025&nbsp;&nbsp;0.5</strong>`

`<strong>0.965926&nbsp;&nbsp;0.258819</strong>`

`<strong>1.0&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 6.12323e-17</strong>`

`<strong>julia&gt; using Statistics</strong>`

`<strong>julia&gt; mean(m1-m), std(m1-m)<br>(0.0009570353971457324, 0.00784842483267987)</strong>`

Such a crude estimation can produce reasonably accurate computation while keeping the computation fast enough. With modern CPUs with in-built trigonometric functions as instructions, these tradeoffs may not be needed. However, performance versus accuracy tradeoff is common in an optimization which this serves to illustrate. And, they are mostly domain specific.

# 

Cloud computing resources can be added to a project or problem at demand. However, the cost of resources is adding significant cost to the projects. Adding more hardware or processing power can solve significantly bigger problems. They are adding to the overall cost as well. For example, smartphones today are able to handle on device speech recognition and many computationally complex tasks involving deep learning and neural computing. This was not possible with advanced desktops a decade back. The hardware of smartphones today is more advanced than the decade-old desktops. So, adding more resources to solve complex problems is never a solution. Optimal utilization of resources to reduce cost overruns is a necessity. Hence, performance management will always be a need for every software system.

# 

Computer scientists usually give maximum focus in perfecting this part of the problem. The gains that a well-chosen algorithm can provide to a problem are often unmatched by any amount of tweaking done around a poorly suited one. Whenever you have a code that is not performing right, it is best to take a look at the core design and understand if it has the right algorithm in place. Keeping performance focus in the design phase reduces significant rework costs. For example, *binary search has a complexity of O(log n) while the complexity of array search is linear time or O(n)*. Intuitively it seems that binary search will always perform over a linear search. But, with modern day processor cache and the efficiency of the memory management of arrays, it may be efficient to use linear search for smaller arrays[4](#9ztdqvro.html#n4upl4fndii). While B-tree is the choice of database indexes for disk-based storage; binary trees may be the data structure of choice for in-memory databases. One needs to look at the right data structures considering the complete system performance and not just theoretical asymptotic time complexity or the worst-case performance.

# 

An absolute performance optimization across the code base helps no one. Overtly optimized code is hard to understand and may end up being tailored for a specific platform. Julia recommends writing code that is readable and uses the appropriate algorithm leaving the code generation and the lower-level target-specific optimization to the JIT compiler and the LLVM toolset. It provides tools that help in profiling the code and finding where the performance bottlenecks can be seen. From the programmer’s perspective, the ability to write generalized higher-level code that remains performant on across platforms is always preferred over platform-specific fixes. If optimization is essential in a code base, it is best to localize to a small set of functions.

# 

Most people who start optimizing the code struggle to find what should be the target performance for them. Can they achieve the set target? This is essentially comparing your results to an industry benchmark. Julia took an extreme position of benchmarking the performance closest to compiled code in C. Compiled code in C is a bare executable and the C-runtime is very lightweight. It is preloaded as many of the operating systems use the same runtime. Julia may not have a corresponding comparison to the C-based system.

The Julia runtime needs to be loaded on the execution of a program for the first time and it will exit on completion of the execution. Second, Julia is a JIT-compiled language. Julia code executed sparingly may not have been compiled to native binaries before it is invoked. A part of the time may be spent in compiling the code to the native format when the code is invoked. To bring both the systems to a comparable state, Julia proponents would suggest the performance be measured in a steady-state condition. A steady state is reached when all the Julia code is run at least once and they are compiled to native binaries by the JIT compiler. While detractors of the language do not agree with the benchmark as they think the loading time has not been considered as a part of the process. Julia community publishes a set of micro-benchmarks[5](#9ztdqvro.html#n4upl4fndij) for many competitive platforms taking few algorithmic tasks:

![](n4upl4fndqi.jpeg)

**Figure 11.1:** Julia vs Competiting Platforms[6](#9ztdqvro.html#n4upl4fndik)

As can be seen in many of the tasks, Julia outperforms the competition and is quite close to the performance of the native C language. Performance optimization is quite an involved topic for any programming language. We cannot do complete justice to every possible aspect of performance optimization. We shall only review a few tools and guidelines that can help us write optimized code.

# 

Benchmarking is about comparing expected performance against a well-known target. The `<strong>BenchmarkTool.jl</strong>` package can help a developer measure time taken and memory allocated in executing a Julia code. Let us benchmark the performance of the table lookup-based scheme for computing the sine function that we saw earlier and see if there are really any significant gains. We shall make use of the tools provided by Julia `<strong>BenchmarkTools.jl</strong>` library in measuring the time periods and allocations.

`<strong>sin(x)</strong>` function assumes that the variable `<strong>x</strong>` is in radians. However, we will have a function `<strong>sindeg(x)</strong>` where `<strong>x</strong>` is in degrees. We shall also evaluate if `<strong>sin(x)</strong>` function available in Julia Base is the one we should use or approximate with a table lookup scheme we discussed.

`<strong>julia&gt; using BenchmarkTools;</strong>`

`<strong>julia&gt; deg2rad(x) = pi/180.0*x;</strong>`

`<strong>julia&gt; sindeg = sin ∘ deg2rad;</strong>`

`<strong>julia&gt; cosdeg = cos ∘ deg2rad;</strong>`

`<strong>julia&gt; @benchmark sindeg(52.0)</strong>`

`<strong>BenchmarkTools.Trial:</strong>`

`<strong>memory estimate:&nbsp;&nbsp;16 bytes</strong>`

`<strong>allocs estimate:&nbsp;&nbsp;1</strong>`

`<strong>--------------</strong>`

`<strong>minimum time:&nbsp;&nbsp;&nbsp;&nbsp; 94.110 ns (0.00% GC)</strong>`

`<strong>median time:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;95.795 ns (0.00% GC)</strong>`

`<strong>mean time:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;104.901 ns (1.20% GC)</strong>`

`<strong>maximum time:&nbsp;&nbsp;&nbsp;&nbsp; 19.238 μs (0.00% GC)</strong>`

`<strong>--------------</strong>`

`<strong>samples:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;10000</strong>`

`<strong>evals/sample:&nbsp;&nbsp;&nbsp;&nbsp; 951</strong>`

`<strong>@benchmark</strong>` shall run the code several times; aggregate the performance over several samples and report the statistics of the result. The minimum time is a better estimate as it is with the least system overheads or noise. `<strong>@btime</strong>` reports the results like `<strong>@time</strong>`, reporting the allocations and minimum time elapsed in a single function call while running the function over multiple sample runs. We shall be using `<strong>@btime</strong>` in most of our examples. 95ns is the timing we will like to achieve with our new implementation. Can we do better?

We create a memoization lookup with 6 intermediate values from 0 to 90 degrees, each at 15 degrees interval. For values within an interval range, we use the *sin(A + δ)* expression with approximated values for *sin δ* and *cos δ* as we have seen earlier.

`<strong>struct MemoLookup</strong>`

`<strong>n</strong>`

`<strong>lookup</strong>`

`<strong>function MemoLookup(n)</strong>`

`<strong>step = 90/n</strong>`

`<strong>δ = pi/180*step</strong>`

`<strong>lookup = [[sin(i*δ) for i=0:n] [cos(i*δ) for i=0:n]]</strong>`

`<strong>new(n, lookup)</strong>`

`<strong>end</strong>`

`<strong>end</strong>`

`<strong>step(m::MemoLookup) = 90/m.n</strong>`

`<strong>m = MemoLookup(6)</strong>`

`<strong>function sindegmemo(m::MemoLookup, x)</strong>`

`<strong>s, lookup = step(m), m.lookup</strong>`

`<strong>i = 1</strong>`

`<strong>while x &gt;= s</strong>`

`<strong>x -= s</strong>`

`<strong>i += 1</strong>`

`<strong>end</strong>`

`<strong>iszero(x) &amp;&amp; return lookup[i, 1]</strong>`

`<strong>x = deg2rad(x)</strong>`

`<strong>sinx, cosx = x, 1 - x*x/2</strong>`

`<strong>return lookup[i, 1]*cosx + lookup[i, 2]*sinx</strong>`

`<strong>end</strong>`

Now we will benchmark the function `<strong>sindegmemo</strong>`.

`<strong>julia&gt; @benchmark sindegmemo($m, 52)</strong>`

`<strong>BenchmarkTools.Trial:</strong>`

`<strong>memory estimate:&nbsp;&nbsp;208 bytes</strong>`

`<strong>allocs estimate:&nbsp;&nbsp;13</strong>`

`<strong>--------------</strong>`

`<strong>minimum time:&nbsp;&nbsp;&nbsp;&nbsp; 1.170 μs (0.00% GC)</strong>`

`<strong>median time:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;1.280 μs (0.00% GC)</strong>`

`<strong>mean time:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;1.438 μs (0.00% GC)</strong>`

`<strong>maximum time:&nbsp;&nbsp;&nbsp;&nbsp; 23.120 μs (0.00% GC)</strong>`

`<strong>--------------</strong>`

`<strong>samples:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;10000</strong>`

`<strong>evals/sample:&nbsp;&nbsp;&nbsp;&nbsp; 10</strong>`

The code is slower than what was computed earlier. There are 13 allocations and 208 bytes of additional memory needed for the computation. What can explain such allocations? Small yet frequent chunks of memory allocation can be a significant performance overhead.

# 

These are debugging tools that give insights into the code at various stages of code generation. These tools are named as `<strong>@code_XXX</strong>` where `<strong>xxx</strong>` stands for a specific stage. Julia’s code translation happens in stages. The code gets translated to an abstract structure tree, then to a LLVM code to a final native output. Different macros help us peek into various stages of this code generation process. Julia internally does not use them for actual code generation.

# 

We have seen some examples of type stability while discussing functions and their return values. We know that non-deterministic types can lead to inefficient code. Let us evaluate if the code provided in the preceding Benchmarking section has types that cannot be inferred deterministically.

`<strong>julia&gt; @code_warntype sindegmemo(m, 52)</strong>`

`<strong>Variables</strong>`

`<strong>#self#::Core.Compiler.Const(sindegmemo, false)</strong>`

`<strong>m::MemoLookup</strong>`

`<strong>x@_3::Float64</strong>`

`<strong>s::Any</strong>`

`<strong>lookup::Any</strong>`

`<strong>i::Int64</strong>`

`<strong>sinx::Any</strong>`

`<strong>cosx::Any</strong>`

`<strong>x@_9::Any</strong>`

`<strong>Body::Any</strong>`

`<strong>1 —&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(x@_9 = x@_3)</strong>`

`<strong>│&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Core.NewvarNode(:(sinx))</strong>`

`<strong>│&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Core.NewvarNode(:(cosx))</strong>`

`<strong>│&nbsp;&nbsp; %4&nbsp;&nbsp;= Main.step(m)::Any</strong>`

`<strong>│&nbsp;&nbsp; %5&nbsp;&nbsp;= Base.getproperty(m, :lookup)::Any</strong>`

`<strong>│&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; (s = %4)</strong>`

`<strong>│&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; (lookup = %5)</strong>`

`<strong>└──&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(i = 1)</strong>`

`<strong>2 — %9&nbsp;&nbsp;= (x@_9 &gt;= s)::Any</strong>`

`<strong>└──&nbsp;&nbsp;&nbsp;&nbsp; goto #4 if not %9</strong>`

`<strong>3 —&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; (x@_9 = x@_9 - s)</strong>`

`<strong>│&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; (i = i + 1)</strong>`

`<strong>└──&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; goto #2</strong>`

`<strong>4 — %14 = Main.iszero(x@_9)::Any</strong>`

`<strong>└──&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; goto #6 if not %14</strong>`

`<strong>5 — %16 = Base.getindex(lookup, i, 1)::Any</strong>`

`<strong>└──&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; return %16</strong>`

`<strong>6 —&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; (x@_9 = Main.deg2rad(x@_9))</strong>`

`<strong>│&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; (sinx = x@_9)</strong>`

`<strong>│&nbsp;&nbsp; %20 = (x@_9 * x@_9)::Any</strong>`

`<strong>│&nbsp;&nbsp; %21 = (%20 / 2)::Any</strong>`

`<strong>│&nbsp;&nbsp; %22 = (1 - %21)::Any</strong>`

`<strong>│&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; (cosx = %22)</strong>`

`<strong>│&nbsp;&nbsp; %24 = Base.getindex(lookup, i, 1)::Any</strong>`

`<strong>│&nbsp;&nbsp; %25 = (%24 * cosx)::Any</strong>`

`<strong>│&nbsp;&nbsp; %26 = Base.getindex(lookup, i, 2)::Any</strong>`

`<strong>│&nbsp;&nbsp; %27 = (%26 * sinx)::Any</strong>`

`<strong>│&nbsp;&nbsp; %28 = (%25 + %27)::Any</strong>`

`<strong>└──&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; return %28</strong>`

`<strong>@code_warntype</strong>` reports the Julia code as an AST. The AST is reported with type inference at each step of the AST. The non-deterministic types are highlighted with colors on a terminal or Jupyter console[7](#9ztdqvro.html#n4upl4fndil). There are many variables assigned to the type `<strong>Any</strong>`. This essentially means there will be an allocation for the location of memory and indirection to actual `<strong>Float64</strong>` value during any computation. We will add a type to the declaration for the parameter `<strong>x</strong>` and see how that affects the type inferences.

`<strong>julia&gt; function sindegmemo(m::MemoLookup, x::Float64)</strong>`

`<strong>s, lookup = step(m), m.lookup</strong>`

`<strong>i = 1</strong>`

`<strong>while x &gt;= s</strong>`

`<strong>x -= s</strong>`

`<strong>i += 1</strong>`

`<strong>end</strong>`

`<strong>iszero(x) &amp;&amp; return lookup[i, 1]</strong>`

`<strong>x = deg2rad(x)</strong>`

`<strong>sinx, cosx = x, 1 - x*x/2</strong>`

`<strong>return lookup[i, 1]*cosx + lookup[i, 2]*sinx</strong>`

`<strong>end</strong>`

`<strong>julia&gt; @code_warntype sindegmemo(m, 52)</strong>`

The change affects minimally to the type inferences. Only the variable `<strong>x</strong>` is interpreted properly to a `<strong>Float64</strong>`. However, the majority of the temporary variables are assigned to the type `<strong>Any</strong>`. `<strong>Any</strong>` being an ambiguous type, any operation over a type of `<strong>Any</strong>` is likely to result into an `<strong>Any</strong>`.

`<strong>Variables</strong>`

`<strong>#self#::Core.Compiler.Const(sindegmemo, false)</strong>`

`<strong>m::MemoLookup</strong>`

`<strong>x@_3::Float64</strong>`

`<strong>s::Any</strong>`

`<strong>lookup::Any</strong>`

`<strong>i::Int64</strong>`

`<strong>sinx::Any</strong>`

`<strong>cosx::Any</strong>`

`<strong>x@_9::Any</strong>`

`<strong>Body::Any</strong>`

`<strong>1 —&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; (x@_9 = x@_3)</strong>`

`<strong>│&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Core.NewvarNode(:(sinx))</strong>`

`<strong>│&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Core.NewvarNode(:(cosx))</strong>`

`<strong>│&nbsp;&nbsp; %4&nbsp;&nbsp;= Main.step(m)::Any</strong>`

`<strong>│&nbsp;&nbsp; %5&nbsp;&nbsp;= Base.getproperty(m, :lookup)::Any</strong>`

`<strong>│&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; (s = %4)</strong>`

`<strong>│&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; (lookup = %5)</strong>`

`<strong>└──&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; (i = 1)</strong>`

`<strong>2 — %9&nbsp;&nbsp;= (x@_9 &gt;= s)::Any</strong>`

`<strong>└──&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; goto #4 if not %9</strong>`

`<strong>3 —&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; (x@_9 = x@_9 - s)</strong>`

`<strong>│&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; (i = i + 1)</strong>`

`<strong>└──&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; goto #2</strong>`

`<strong>4 — %14 = Main.iszero(x@_9)::Any</strong>`

`<strong>└──&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; goto #6 if not %14</strong>`

`<strong>5 — %16 = Base.getindex(lookup, i, 1)::Any</strong>`

`<strong>└──&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; return %16</strong>`

`<strong>6 —&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; (x@_9 = Main.deg2rad(x@_9))</strong>`

`<strong>│&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; (sinx = x@_9)</strong>`

`<strong>│&nbsp;&nbsp; %20 = (x@_9 * x@_9)::Any</strong>`

`<strong>│&nbsp;&nbsp; %21 = (%20 / 2)::Any</strong>`

`<strong>│&nbsp;&nbsp; %22 = (1 - %21)::Any</strong>`

`<strong>│&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; (cosx = %22)</strong>`

`<strong>│&nbsp;&nbsp; %24 = Base.getindex(lookup, i, 1)::Any</strong>`

`<strong>│&nbsp;&nbsp; %25 = (%24 * cosx)::Any</strong>`

`<strong>│&nbsp;&nbsp; %26 = Base.getindex(lookup, i, 2)::Any</strong>`

`<strong>│&nbsp;&nbsp; %27 = (%26 * sinx)::Any</strong>`

`<strong>│&nbsp;&nbsp; %28 = (%25 + %27)::Any</strong>`

`<strong>└──&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; return %28</strong>`

We will introduce a new `<strong>MemoLookup</strong>` that has the types defined properly for the attributes like n and lookup.

`<strong>struct MemoLookup</strong>`

`<strong>n::Int</strong>`

`<strong>lookup::Matrix{Float64}</strong>`

`<strong>function MemoLookup (n)</strong>`

`<strong>step = 90/n</strong>`

`<strong>δ = pi/180*step</strong>`

`<strong>lookup = [[sin(i*δ) for i=0:n] [cos(i*δ) for i=0:n]]</strong>`

`<strong>new(n, lookup)</strong>`

`<strong>end</strong>`

`<strong>end</strong>`

`<strong>step(m::MemoLookup) = 90/m.n</strong>`

`<strong>m = MemoLookup(6)</strong>`

`<strong>julia&gt; @code_warntype sindegmemo(m, 52.0)</strong>`

`<strong>Variables</strong>`

`<strong>#self#::Core.Compiler.Const(sindegmemo, false)</strong>`

`<strong>m::MemoLookup2</strong>`

`<strong>x@_3::Float64</strong>`

`<strong>s::Float64</strong>`

`<strong>lookup::Array{Float64,2}</strong>`

`<strong>i::Int64</strong>`

`<strong>sinx::Float64</strong>`

`<strong>cosx::Float64</strong>`

`<strong>x@_9::Float64</strong>`

`<strong>Body::Float64</strong>`

`<strong>…</strong>`

`<strong>│&nbsp;&nbsp; %4&nbsp;&nbsp;= Main.step(m)::Float64</strong>`

`<strong>…</strong>`

`<strong>2 ┄ %9&nbsp;&nbsp;= (x@_9 &gt;= s)::Bool</strong>`

`<strong>└──&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; goto #4 if not %9</strong>`

`<strong>…</strong>`

`<strong>4 — %14 = Main.iszero(x@_9)::Bool</strong>`

`<strong>└──&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; goto #6 if not %14</strong>`

`<strong>5 — %16 = Base.getindex(lookup, i, 1)::Float64</strong>`

`<strong>└──&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; return %16</strong>`

`<strong>…</strong>`

`<strong>│&nbsp;&nbsp; %20 = (x@_9 * x@_9)::Float64</strong>`

`<strong>│&nbsp;&nbsp; %21 = (%20 / 2)::Float64</strong>`

`<strong>│&nbsp;&nbsp; %22 = (1 - %21)::Float64</strong>`

`<strong>…</strong>`

`<strong>│&nbsp;&nbsp; %24 = Base.getindex(lookup, i, 1)::Float64</strong>`

`<strong>│&nbsp;&nbsp; %25 = (%24 * cosx)::Float64</strong>`

`<strong>│&nbsp;&nbsp; %26 = Base.getindex(lookup, i, 2)::Float64</strong>`

`<strong>│&nbsp;&nbsp; %27 = (%26 * sinx)::Float64</strong>`

`<strong>│&nbsp;&nbsp; %28 = (%25 + %27)::Float64</strong>`

`<strong>└──&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; return %28</strong>`

There are no variables assigned a type `<strong>Any</strong>`. Let’s see if that improves the performance.

`<strong>julia&gt; @btime sindegmemo($m, 52.0)</strong>`

`<strong>19.257 ns (0 allocations: 0 bytes)</strong>`

`<strong>0.788218944092369</strong>`

There is significant improvement in performance: `<strong>1170ns</strong>` to `<strong>19ns</strong>`. But, if you remember the `<strong>sindeg(x)</strong>` function we wrote had `<strong>95ns</strong>` execution time. Is `<strong>sindeg(x)</strong>` properly constructed?

# 

One option will be to look at the `<strong>@code_warntype</strong>` dump for the function call.

`<strong>julia&gt; @code_warntype sindeg(52.0)</strong>`

`<strong>Variables</strong>`

`<strong>#self#::Core.Compiler.Const(Base.var"#62#63"{typeof(sin),typeof(deg2rad)}(sin, deg2rad), false)</strong>`

`<strong>x::Tuple{Float64}</strong>`

`<strong>Body::Float64</strong>`

`<strong>1 — %1 = Core.getfield(#self#, :f)::Core.Compiler.Const(sin, false)</strong>`

`<strong>│&nbsp;&nbsp; %2 = Core.getfield(#self#, :g)::Core.Compiler.Const(deg2rad, false)</strong>`

`<strong>│&nbsp;&nbsp; %3 = Core._apply_iterate(Base.iterate, %2, x)::Float64</strong>`

`<strong>│&nbsp;&nbsp; %4 = (%1)(%3)::Float64</strong>`

`<strong>└──&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;return %4</strong>`

While there is no problem in the code in terms of type inference (there are no `<strong>Any</strong>` types), `<strong>x</strong>` is assigned a `<strong>Tuple{Float64}</strong>`. This essentially means a new variable will be created and function input will be assigned to this newly created tuple[8](#9ztdqvro.html#n4upl4fndim). If we redefine the `<strong>sindeg</strong>` function as:

`<strong>julia&gt; sindeg(x) = sin(deg2rad(x))</strong>`

`<strong>julia&gt; @btime sindeg(x)</strong>`

`<strong>2.799 ns (0 allocations: 0 bytes)</strong>`

`<strong>0.49999999999999994</strong>`

This is very much equivalent to the performance of Julia function `<strong>sind(x)</strong>` that returns the sine of x when x is in degrees.

# 

Parametric data types improve performance as they are resolved during code compilation and not runtime. The challenge is in identifying such attributes. For example, in the type `<strong>MemoLookup</strong>` the table size attribute `<strong>n</strong>` is a constant and not too many such lookup tables need to be constructed. Hence, it is an ideal candidate for being a parameter for the type.

`<strong>struct MemoLookupP{N}</strong>`

`<strong>lookup::Matrix{Float64}</strong>`

`<strong>function MemoLookupP{N}() where N</strong>`

`<strong>δ = pi/2N</strong>`

`<strong>lookup = [[sin(i*δ) for i=0:N] [cos(i*δ) for i=0:N]]</strong>`

`<strong>new{N}(lookup)</strong>`

`<strong>end</strong>`

`<strong>end</strong>`

`<strong>step(m::MemoLookupP{N}) where N = 90.0/N</strong>`

`<strong>const m3 = MemoLookupP{6}()</strong>`

We define another `<strong>sindegmemo</strong>` function that takes `<strong>MemoLookupP</strong>` as an input.

`<strong>function sindegmemo(m::MemoLookupP, x::Float64)</strong>`

`<strong>s, lookup = step(m), m.lookup</strong>`

`<strong>i = 1</strong>`

`<strong>while x &gt;= s</strong>`

`<strong>x -= s</strong>`

`<strong>i += 1</strong>`

`<strong>end</strong>`

`<strong>x, sini = deg2rad(x), lookup[i, 1]</strong>`

`<strong>iszero(x) &amp;&amp; return sini</strong>`

`<strong>sinx, cosx, cosi = x, 1 - x*x/2, lookup[i, 2]</strong>`

`<strong>return sini*cosx + cosi*sinx</strong>`

`<strong>end</strong>`

`<strong>julia&gt; @btime sindegmemo(m3, 60.0)</strong>`

`<strong>13.012 ns (0 allocations: 0 bytes)</strong>`

`<strong>0.8660254037844386</strong>`

From 19ns to 13ns is an improvement but can we do better. Let’s review the LLVM bitcode generated.

# 

The bitcode generated from LLVM can be quite descriptive and may require good understanding of the code mnemonics. However, we will just identify some obvious issues not getting into a detailed analysis. The truncated dump may be something as follows:

``<strong>julia&gt; @code_llvm sindegmemo($m3, 60.0)<br><br>;&nbsp;&nbsp;@ In[38]:1 within `sindegmemo'<br>; Function Attrs: uwtable<br>define double @julia_sindegmemo_2316([1 x %jl_value_t*]* nocapture nonnull readonly dereferenceable(8), double) #0 {<br>top:<br>ib:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;; preds = %L9<br>;&nbsp;&nbsp;@ In[38]:8 within `sindegmemo'<br>;&nbsp;&nbsp;@ array.jl:810 within `getindex'<br>…<br><a id="page237"></a>oob:&nbsp;&nbsp;&nbsp;&nbsp; ; preds = %ib, %L9<br>&nbsp;&nbsp;%19 = alloca [2 x i64], align 8<br>&nbsp;&nbsp;%.sub = getelementptr inbounds [2 x i64], [2 x i64]* %19, i64 0, i64 0<br>…<br>&nbsp;&nbsp;ret double %37<br>}</strong>``

Whenever an array is accessed with `<strong>getindex</strong>` method, the bounds are checked. The `<strong>ib</strong>` label is executed when the arrays within limits and `<strong>oob</strong>` when the index is out of bounds. If we can be sure the index is within bounds the out of bounds section can be eliminated. You can use the macro `<strong>@inbounds</strong>` to ensure the bounds checking code is not generated.

`<strong>function sindegmemo(m::MemoLookupP, x::Float64)</strong>`

`<strong>s, lookup = step(m), m.lookup</strong>`

`<strong>i = 1</strong>`

`<strong>while x &gt;= s</strong>`

`<strong>x -= s</strong>`

`<strong>i += 1</strong>`

`<strong>end</strong>`

`<strong>x, sini = deg2rad(x), @inbounds lookup[i, 1]</strong>`

`<strong>iszero(x) &amp;&amp; return sini</strong>`

`<strong>sinx, cosx, cosi = x, 1 - x*x/2, @inbounds lookup[i, 2]</strong>`

`<strong>return sini*cosx + cosi*sinx</strong>`

`<strong>end</strong>`

`<strong>julia&gt; @btime sindegmemo($m3, 60.0)</strong>`

`<strong>2.699 ns (0 allocations: 0 bytes)</strong>`

`<strong>0.8660254037844386</strong>`

`<strong>julia&gt; @btime sindegmemo($m3, 22.0)</strong>`

`<strong>3.799 ns (0 allocations: 0 bytes)</strong>`

`<strong>0.3748975477461437</strong>`

We got very close to the performance of `<strong>sind(x)</strong>` but are not quite there[9](#9ztdqvro.html#n4upl4fndin). One obvious question, why `<strong>sindegmemo</strong>` performs better when the input is 60° than the input of 22°?

# 

In the examples, we analyzed so far, we knew a specific function has a performance bottleneck that we will like to get over. In many large applications, such knowledge is unlikely. For example, a particular word processor is slow to open a file and render the contents on the screen. There could be many factors. The file reading may be slow, some particular feature in the document is computationally complex or file size is too big and reading all the data and caching data in the memory can be a bottleneck. Profiling helps you identify such scenarios. At certain fixed intervals (say every milli-seconds), statistical profilers would look at the code execution stack and record the state of the stack like the line number and function where the execution was during the query. Once the run is complete they would correlate all such data and report the number of times a particular function was encountered along with the back trace of all the functions called to reach such function.

Julia has an in-built statistical profiler. Profiler is in the module called `<strong>Profile</strong>`. We shall use this tool to profile a function `<strong>profile_test</strong>`[10](#9ztdqvro.html#n4upl4fndio).

`<strong>using Profile</strong>`

`<strong>function profile_test(n)</strong>`

`<strong>for i = 1:n</strong>`

`<strong>A = randn(100,100,20)</strong>`

`<strong>m = maximum(A)</strong>`

`<strong>Am = mapslices(sum, A; dims=2)</strong>`

`<strong>B = A[:,:,5]</strong>`

`<strong>Bsort = mapslices(sort, B; dims=1)</strong>`

`<strong>b = rand(100)</strong>`

`<strong>C = B.*b</strong>`

`<strong>end</strong>`

`<strong>end</strong>`

`<strong>julia&gt; profile_test(1)</strong>`

The code is run once so that it is compiled and the time taken for such activities is not captured as part of the profiler sampling. Now we run the function over 100 iterations and profile the run.

`<strong>julia&gt; @profile profile_test</strong>`

The data are generated and cached with the profiler and can be printed with the `<strong>Profile.print()</strong>` call. A truncated view has given:

`<strong>julia&gt; Profile.print()</strong>`

`<strong>Overhead ╎ [+additional indent] Count File:Line; Function</strong>`

`<strong>=========================================================</strong>`

`<strong>╎410 @Base\task.jl:356; (::IJulia.var"#15#18")()</strong>`

`<strong>╎ 410 @IJulia\src\eventloop.jl:8; eventloop(::ZMQ.Socket)</strong>`

`<strong>╎&nbsp;&nbsp;410 @Base\essentials.jl:709; invokelatest</strong>`

`<strong>…</strong>`

`<strong>╎&nbsp;&nbsp;&nbsp;&nbsp;╎&nbsp;&nbsp;84&nbsp;&nbsp;In[29]:3; profile_test(::Int64)</strong>`

`<strong>╎&nbsp;&nbsp;&nbsp;&nbsp;╎&nbsp;&nbsp; 84&nbsp;&nbsp;…dom\src\normal.jl:210; randn</strong>`

`<strong>╎&nbsp;&nbsp;&nbsp;&nbsp;╎&nbsp;&nbsp;&nbsp;&nbsp;84&nbsp;&nbsp;…dom\src\normal.jl:204; randn</strong>`

`<strong>…</strong>`

`<strong>╎&nbsp;&nbsp;&nbsp;&nbsp;╎&nbsp;&nbsp;8&nbsp;&nbsp; In[29]:4; profile_test(::Int64)</strong>`

`<strong>╎&nbsp;&nbsp;&nbsp;&nbsp;╎&nbsp;&nbsp; 8&nbsp;&nbsp; @Base\reducedim.jl:722; maximum</strong>`

`<strong>╎&nbsp;&nbsp;&nbsp;&nbsp;╎&nbsp;&nbsp;&nbsp;&nbsp;8&nbsp;&nbsp; @Base\reducedim.jl:722; #maximum#631</strong>`

`<strong>…</strong>`

`<strong>╎&nbsp;&nbsp;&nbsp;&nbsp;╎&nbsp;&nbsp;264 In[29]:5; profile_test(::Int64)</strong>`

`<strong>╎&nbsp;&nbsp;&nbsp;&nbsp;╎&nbsp;&nbsp; 264 …\abstractarray.jl:2062; mapslices##kw</strong>`

`<strong>…</strong>`

`<strong>╎&nbsp;&nbsp;&nbsp;&nbsp;╎&nbsp;&nbsp;9&nbsp;&nbsp; In[29]:9; profile_test(::Int64)</strong>`

`<strong>╎&nbsp;&nbsp;&nbsp;&nbsp;╎&nbsp;&nbsp; 9&nbsp;&nbsp; @Base\broadcast.jl:837; materialize</strong>`

`<strong>╎&nbsp;&nbsp;&nbsp;&nbsp;╎&nbsp;&nbsp;&nbsp;&nbsp;9&nbsp;&nbsp; @Base\broadcast.jl:862; copy</strong>`

`<strong>…</strong>`

`<strong>Total snapshots: 413</strong>`

The highlighted portions are from the top-level function `<strong>profile_test</strong>`. The maximum time is spent on the line 5 as that has been sampled 264 times of a total of 413. You can get a better visual of the output using the package `<strong>ProfileView</strong>`. The same can be installed by using the command: `<strong>julia&gt;]add ProfileView</strong>`:

![](n4upl4fndqj.jpeg)

**Figure 11.2:** Visualization with ProfileView. The highlighted area represents the line no 5 of the function taking the maximum amount of time

We went through a few performance tuning processes. In the next section, we shall review a few guidelines for writing high-performance code.

# 

In , we looked at design patterns related to functional programming. In this section, we will review a few patterns that help improve the performance of the code.

# 

When a pure a function is called several times, it shall produce the same output. Rather than computing the result again and again if we can cache the value, it will reduce the computation overheads. This process is called `<strong>memoization</strong>`. One of the most common examples discussed in the context of memoization is the Fibonacci series[11](#9ztdqvro.html#n4upl4fndip). A Fibonacci series is best described recursively with the following code:

***fib(n) = n < 3 ? 1 : fib(n-1) + fib(n-2)***

The function is called recursively twice for every invocation. If we record the number of invocations by modifying the function a bit, you can see the number of function calls growing exponentially.

`<strong>function fib(n)</strong>`

`<strong>if n &lt; 3</strong>`

`<strong>return (result=1, calls=1)</strong>`

`<strong>else</strong>`

`<strong>r1, c1 = fib(n-2)</strong>`

`<strong>r2, c2 = fib(n-1)</strong>`

`<strong>return (result=r1+r2, calls=1+c1+c2)</strong>`

`<strong>end</strong>`

`<strong>end</strong>`

`<strong>julia&gt; for i = 1:10</strong>`

`<strong>r, c = fib(i)</strong>`

`<strong>println("n:", i, "\tresult: ", r, "\tcalls: ", c)</strong>`

`<strong>end</strong>`

`<strong>n:1 result: 1 calls: 1</strong>`

`<strong>n:2 result: 1 calls: 1</strong>`

`<strong>n:3 result: 2 calls: 3</strong>`

`<strong>n:4 result: 3 calls: 5</strong>`

`<strong>n:5 result: 5 calls: 9</strong>`

`<strong>n:6 result: 8 calls: 15</strong>`

`<strong>n:7 result: 13 calls: 25</strong>`

`<strong>n:8 result: 21 calls: 41</strong>`

`<strong>n:9 result: 34 calls: 67</strong>`

`<strong>n:10 result: 55 calls: 109</strong>`

`<strong>julia&gt; @btime fib(20)</strong>`

`<strong>112.899 μs (0 allocations: 0 bytes)</strong>`

`<strong>(result = 6765, calls = 13529)</strong>`

The function is quite expensive still, considering there are only addition operations involved. `<strong>fib(6) = fib(5) + fib(4)</strong>`, We have already seen `<strong>fib(4)</strong>` in the computation of `<strong>fib(5)</strong>`. If we cache `<strong>f(4)</strong>` as soon as we compute, we need not have to compute again while computing `<strong>f(5)</strong>` and `<strong>f(6)</strong>`. We can reuse the value from the previous computation. We employ the same concept in the following code:

`<strong>const mem = Dict()</strong>`

`<strong>function fib(n)</strong>`

`<strong>haskey(mem, n) &amp;&amp; return mem[n]</strong>`

`<strong>println("Calling fib: ", n)</strong>`

`<strong>res = n &lt; 3 ? 1 : fib(n-1) + fib(n-2)</strong>`

`<strong>mem[n] = res</strong>`

`<strong>return res</strong>`

`<strong>end</strong>`

`<strong>julia&gt; fib(5)</strong>`

`<strong>Calling fib: 5</strong>`

`<strong>Calling fib: 4</strong>`

`<strong>Calling fib: 3</strong>`

`<strong>Calling fib: 2</strong>`

`<strong>Calling fib: 1</strong>`

`<strong>julia&gt; @btime fib(20)</strong>`

`<strong>85.758 ns (0 allocations: 0 bytes)</strong>`

`<strong>6765</strong>`

`<strong>fib(5)</strong>` is called only 5 times and time taken for `<strong>fib(20)</strong>` is only 86ns; almost the time taken to read from the dictionary and add them. Can we generalize the concept to presentable form for any kind of memorization tasks?

`<strong>function memoize(f)</strong>`

`<strong>memo = Dict()</strong>`

`<strong>(args…; kwargs…) -&gt; begin</strong>`

`<strong>x = (args, kwargs)</strong>`

`<strong>haskey(memo, x) &amp;&amp; return memo[x]</strong>`

`<strong>v = f(args…; kwargs…)</strong>`

`<strong>memo[x] = v</strong>`

`<strong>return v</strong>`

`<strong>end</strong>`

`<strong>end</strong>`

The `<strong>memoize(f)</strong>` is a higher order function that can memoize a function with its parameters for subsequent value retrieval. The memo dictionary is accessed as a closure[12](#9ztdqvro.html#n4upl4fndiq) by the anonymous function returned by `<strong>memoize</strong>`. With a function like `<strong>memoize</strong>` you can define `<strong>fib(n)</strong>` method as shown:

`<strong>fib(n) = n &lt; 3 ? 1 : fib(n-1) + fib(n-2)</strong>`

`<strong>fib! = memoize(fib)</strong>`

However, `<strong>Memoize.jl</strong>` package[13](#9ztdqvro.html#n4upl4fndir) has a `<strong>@memoize</strong>` macro that can help specify if the function is memoization aware.

`<strong>julia&gt; Pkg.add("Memoize")</strong>`

`<strong>julia&gt; using Memoize</strong>`

`<strong>julia&gt; @memoize fib(n) = n &lt; 3 ? 1 : fib(n-1) + fib(n-2)</strong>`

# 

This is not really a design pattern. We want you to be aware of the challenges in using global variables. Julia global variables do not have an assigned type. They can be assigned to any type based on the data it is assigned to.

`<strong>GLOBAL_VAR = 3</strong>`

`<strong>function add_to_global(x)</strong>`

`<strong>x + GLOBAL_VAR</strong>`

`<strong>end</strong>`

`<strong>julia&gt; @btime add_to_global(10)</strong>`

`<strong>65.745 ns (0 allocations: 0 bytes)</strong>`

`<strong>13</strong>`

Now, let us pass the global variable to the basic addition operator.

`<strong>Julia&gt; @btime 10 + $GLOBAL_VAR</strong>`

`<strong>0.001 ns (0 allocations: 0 bytes)</strong>`

`<strong>13</strong>`

Just wrapping the global variable in the function is having significant overheads; but why? Let us consider a global constant instead of a variable.

`<strong>julia&gt; const GLOBAL_CONST = 20;</strong>`

`<strong>julia&gt; add_to_global_const(x) = x + GLOBAL_CONST</strong>`

`<strong>julia&gt; @btime add_to_global_const(3)</strong>`

`<strong>0.001 ns (0 allocations: 0 bytes)</strong>`

`<strong>23</strong>`

The value returned is fairly fast and much better than a global variable. Let us look at the LLVM bitcode.

`<strong>julia&gt; @code_llvm add_to_global_const(3)</strong>`

``<strong>;&nbsp;&nbsp;@ In[108]:1 within `add_to_global_const'</strong>``

`<strong>; Function Attrs: uwtable</strong>`

`<strong>define i64 @julia_add_to_global_const_4267(i64) #0 {</strong>`

`<strong>top:</strong>`

``<strong>; ┌ @ int.jl:86 within `+'</strong>``

`<strong>&nbsp;%1 = add i64 %0, 20</strong>`

`<strong>; └</strong>`

`<strong>ret i64 %1</strong>`

`<strong>}</strong>`

The constant 20 is directly replaced. So, there is no type ambiguity. The addition shall take place in a CPU register. There is no memory access. Global variables serve two purposes. They allocate a specific location of memory and a handle to the memory location. However, they are not type safe. However, `<strong>Ref{T}</strong>` allocate memory and are type safe. By declaring the variable as `<strong>const</strong>` can ensure the memory location is pinned as well.

`<strong>julia&gt; const GLOBAL_REF = Ref(10)</strong>`

`<strong>Base.RefValue{Int64}(10)</strong>`

`<strong>julia&gt; add_to_global_ref(x) = x + GLOBAL_REF[]</strong>`

`<strong>julia&gt; @btime add_to_global_ref(3)</strong>`

`<strong>2.499 ns (0 allocations: 0 bytes)</strong>`

`<strong>23</strong>`

There is definite improvement of performance over a global variable, yet it is not as fast as a `<strong>const</strong>` or a function argument. On reviewing the LLVM bitcode you will see, there are essentially two parts to the code.

1.  Load the value from a specific memory location to a variable or register or volatile memory location
2.  Add the value to another volatile memory location

`<strong>Julia&gt; @code_llvm add_to_global_ref(3)</strong>`

``<strong>;&nbsp;&nbsp;@ In[116]:1 within `add_to_global_ref'</strong>``

`<strong>; Function Attrs: uwtable</strong>`

`<strong>define i64 @julia_add_to_global_ref_4338(i64) #0 {</strong>`

`<strong>top:</strong>`

``<strong>; ┌ @ refvalue.jl:32 within `getindex'</strong>``

``<strong>; │┌ @ Base.jl:33 within `getproperty'</strong>``

`<strong>%1 = load i64, i64* inttoptr (i64 380471024 to i64*), align 16</strong>`

`<strong>; └└</strong>`

``<strong>; ┌ @ int.jl:86 within `+'</strong>``

`<strong>&nbsp;%2 = add i64 %1, %0</strong>`

`<strong>; └</strong>`

`<strong>ret i64 %2</strong>`

`<strong>}</strong>`

If you do not like to access the `<strong>Ref{T}</strong>` syntax with the square brackets ([]), you can use the accessor pattern as well.

`<strong>let _x = Ref(5)</strong>`

`<strong>global X() = _x[]</strong>`

`<strong>global X(y) = (_x[] = y)</strong>`

`<strong>end</strong>`

We will recommend readers to look at the LLVM bitcode for `<strong>add_to_global_var</strong>`. As there is no type inference for a global variable, the function will have to assume a type `<strong>Any</strong>` and resolve the type conflicts on every use.

# 

Julia system is designed for high-performance computations. We saw glimpses of such implementations in this chapter. However, performance tuning is a complex subject and the development of skills in this area needs sufficient exposure and practice. We thus recommend readers review performance-sensitive code and try improvising over them with regular practice. In the next chapter, we shall review the IDEs available for Julia’s development and how various debugging techniques can be used.

# 

1.  Choose a function of your choice and run `<strong>@code_warntype</strong>` over it. Try to identify the type stability issues and fix such that the type instabilities are removed.
2.  Consider the comprehension `<strong>f()=[x*x for x = 1:10000]</strong>`. Time the code with `<strong>btime</strong>` and compare with the following code:
    
    `<strong>function g()</strong>`
    
    `<strong>y = Vector{Int}(undef, 10000)</strong>`
    
    `<strong>for i in 1:10000</strong>`
    
    `<strong>y[i] = i*i</strong>`
    
    `<strong>end</strong>`
    
    `<strong>end</strong>`
    
    How will you explain the difference?
    
3.  Why is `<strong>@btime</strong>` of `<strong>BenchmarkTools.jl</strong>` preferred over `<strong>Base.@time</strong>`? How will you use `<strong>@btime</strong>` for functions with side-effects?
4.  What are some of the `<strong>@code_XXX</strong>` macros and why are they used in performance profiling?
5.  Julia performance profiling is suggested only when the code has been used several times with all relevant data types. It has been seen Julia is slow to start. What do you think are the reasons?

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

[1](#9ztdqvro.html#n4upl4fndis) Brian W. Kernighan and Rob Pike, The Practice of Programming, Chapter 7, Addison-Wesley, 1999

[2](#9ztdqvro.html#n4upl4fndit) Voyager 1 just left the solar system using less computing power than your iPhone, Washington Post, **[https://www.washingtonpost.com/news/the-switch/wp/2013/09/12/voyager-1-just-left-the-solar-system-using-less-computing-power-than-your-iphone/](https://www.washingtonpost.com/news/the-switch/wp/2013/09/12/voyager-1-just-left-the-solar-system-using-less-computing-power-than-your-iphone/)** September 13, 2013, last accessed January 12, 2021

[3](#9ztdqvro.html#n4upl4fndiu) Ideal Loop Processing, Microsoft MSDN Documentation, Visual Studio 2019, **[https://docs.microsoft.com/en-us/cpp/mfc/idle-loop-processing?view=msvc-160](https://docs.microsoft.com/en-us/cpp/mfc/idle-loop-processing?view=msvc-160)**, last accessed January 12, 2021

[4](#9ztdqvro.html#n4upl4fndiv) Evan Jones, The Unreasonable Effectiveness of Linear Search, Blog Post, September 10, 2018, **[https://www.evanjones.ca/linear-search.html](https://www.evanjones.ca/linear-search.html)** last accessed: January 14, 2021.

[5](#9ztdqvro.html#n4upl4fndiw) These are called micro-benchmarks as they are performance measured for specific tasks not a complete system.

[6](#9ztdqvro.html#n4upl4fndix) Julia Micro-Benchmarks, **[https://julialang.org/benchmarks/](https://julialang.org/benchmarks/)** last accessed: 1423^(th) January 2021

[7](#9ztdqvro.html#n4upl4fndiy) We have only bold faced the variables mapped to type `Any`. In the terminal output, you will be seeing variables with non-deterministic types highlighted in red or brown and deterministic types in green or cyan. `@code_typed` also reports almost similar information as `@code_warntype`. However, it does not highlight the type of warnings.

[8](#9ztdqvro.html#n4upl4fndiz) This code is from the 1.5.3 version of Julia. The relevant code is:  
`∘<strong>(f, g) = (x…)-&gt;f(g(x…))</strong>`  
A composition operator on two functions shall essentially, create an anonymous function and assign to the variable. `<strong>sindeg</strong>` is just a variable which is assigned an anonymous function of type: `<strong>Base.var"#62#63"{typeof(sin), typeof(deg2rad).</strong>`

[9](#9ztdqvro.html#n4upl4fndi0) The native Julia functions `<strong>sin</strong>` and `<strong>cos</strong>` are not utilizing the CPU instruction `<strong>FSIN</strong>`or `<strong>FSINCOS</strong>` as found in the Intel chipset. But, a 13-degree polynomial is computed using an optimized Horner’s method. The interested readers can review the code at the GitHub link: **[https://github.com/JuliaLang/julia/blob/cf9bcc7a49863ea47facbd93a2d920b0bf1e96ff/base/special/trig.jl#L69](https://github.com/JuliaLang/julia/blob/cf9bcc7a49863ea47facbd93a2d920b0bf1e96ff/base/special/trig.jl#L69)**. You can generate the bitcode for their native processors using the macro `<strong>@code_native</strong>` and verify.

[10](#9ztdqvro.html#n4upl4fndi1) The code is taken from the samples of ProfileView.jl, A package for better visualization of the Julia profiler output. **[https://github.com/timholy/ProfileView.jl](https://github.com/timholy/ProfileView.jl)**

[11](#9ztdqvro.html#n4upl4fndi2) Tom Kwong, Stefan Karpinski, Hands-On Design Patterns and Best Practices with Julia, Packt Publishing, 2020, Chapter 6

[12](#9ztdqvro.html#n4upl4fndi3) Closure (Computer Programming), Wikipedia **[https://en.wikipedia.org/wiki/Closure\_(computer\_programming)](https://en.wikipedia.org/wiki/Closure_\(computer_programming\))**

[13](#9ztdqvro.html#n4upl4fndi4) `Memoize.jl` **[https://github.com/JuliaCollections/Memoize.jl](https://github.com/JuliaCollections/Memoize.jl)**

Tom Kwong, Stefan Karpinski, Hands-On Design Patterns and Best Practices with Julia, Packt Publishing, 2020, Chapter 6

The code is taken from the samples of ProfileView.jl, A package for better visualization of the Julia profiler output. **[https://github.com/timholy/ProfileView.jl](https://github.com/timholy/ProfileView.jl)**

`Memoize.jl` **[https://github.com/JuliaCollections/Memoize.jl](https://github.com/JuliaCollections/Memoize.jl)**

Closure (Computer Programming), Wikipedia **[https://en.wikipedia.org/wiki/Closure\_(computer\_programming)](https://en.wikipedia.org/wiki/Closure_\(computer_programming\))**

*The first principle of optimization is don’t*1. The recommendation was given by *Kernighan* and *Pike*, the masters of Unix operating system, in their seminal book *The Practice of Programming*. Nothing much has changed over two decades. A correctly working program is far superior to an incorrect fast program. However, many workarounds are taken in ensuring a program behaves close to the performance that is acceptable. There is nothing like absolute performance or code optimized for all conditions. The code that is high performing in today’s standards may be much less in computational capability than a relatively simpler application in the future. Voyager, the first manmade object to leave the solar system, had much lesser computing power than a modern-day cell phone2. One does not have to really optimize every bit of code manually. The code compiled by many of the optimal code generators and compilers are far superior to manually optimized code in most cases. Modern languages like Julia utilize LLVM to handle the cross-platform optimal code generation and address many of the well-known optimization issues during compilation or code generation. One may ask if the hardware is cheap and easily accessible, why do we need to bother about optimized code? The answer lies in however cheaper hardware may get you will need to squeeze that extra bit from it.

*The first principle of optimization is don’t*1. The recommendation was given by *Kernighan* and *Pike*, the masters of Unix operating system, in their seminal book *The Practice of Programming*. Nothing much has changed over two decades. A correctly working program is far superior to an incorrect fast program. However, many workarounds are taken in ensuring a program behaves close to the performance that is acceptable. There is nothing like absolute performance or code optimized for all conditions. The code that is high performing in today’s standards may be much less in computational capability than a relatively simpler application in the future. Voyager, the first manmade object to leave the solar system, had much lesser computing power than a modern-day cell phone2. One does not have to really optimize every bit of code manually. The code compiled by many of the optimal code generators and compilers are far superior to manually optimized code in most cases. Modern languages like Julia utilize LLVM to handle the cross-platform optimal code generation and address many of the well-known optimization issues during compilation or code generation. One may ask if the hardware is cheap and easily accessible, why do we need to bother about optimized code? The answer lies in however cheaper hardware may get you will need to squeeze that extra bit from it.

Running several applications over a single processor on a single thread is not true simultaneous multitasking. The operating system preempts the tasks based on a schedule, letting the processor to execute one task at a time. The user gets a feeling that all the tasks are running simultaneously, while they are only executed for small intervals and switched over to the next. In **Graphical User Interfaces** (**GUI**)-based applications, the responsiveness of the user interface to user inputs is given higher importance over the execution of other background tasks to completion. With multitasked applications running long computationally intensive tasks on single-processor systems, the usual practice is to process UI events intermittently to keep the UI responsive. This is known as **idle loop processing**3 in the Windows systems. Here the optimal response time is given priority over raw execution speed. Hence, sheer execution speed of the code may not be the objective of all code optimization projects.

Computer scientists usually give maximum focus in perfecting this part of the problem. The gains that a well-chosen algorithm can provide to a problem are often unmatched by any amount of tweaking done around a poorly suited one. Whenever you have a code that is not performing right, it is best to take a look at the core design and understand if it has the right algorithm in place. Keeping performance focus in the design phase reduces significant rework costs. For example, *binary search has a complexity of O(log n) while the complexity of array search is linear time or O(n)*. Intuitively it seems that binary search will always perform over a linear search. But, with modern day processor cache and the efficiency of the memory management of arrays, it may be efficient to use linear search for smaller arrays4. While B-tree is the choice of database indexes for disk-based storage; binary trees may be the data structure of choice for in-memory databases. One needs to look at the right data structures considering the complete system performance and not just theoretical asymptotic time complexity or the worst-case performance.

Julia has an in-built statistical profiler. Profiler is in the module called `<strong>Profile</strong>`. We shall use this tool to profile a function `<strong>profile_test</strong>`10.

The Julia runtime needs to be loaded on the execution of a program for the first time and it will exit on completion of the execution. Second, Julia is a JIT-compiled language. Julia code executed sparingly may not have been compiled to native binaries before it is invoked. A part of the time may be spent in compiling the code to the native format when the code is invoked. To bring both the systems to a comparable state, Julia proponents would suggest the performance be measured in a steady-state condition. A steady state is reached when all the Julia code is run at least once and they are compiled to native binaries by the JIT compiler. While detractors of the language do not agree with the benchmark as they think the loading time has not been considered as a part of the process. Julia community publishes a set of micro-benchmarks5 for many competitive platforms taking few algorithmic tasks:

When a pure a function is called several times, it shall produce the same output. Rather than computing the result again and again if we can cache the value, it will reduce the computation overheads. This process is called `<strong>memoization</strong>`. One of the most common examples discussed in the context of memoization is the Fibonacci series11. A Fibonacci series is best described recursively with the following code:

`<strong>@code_warntype</strong>` reports the Julia code as an AST. The AST is reported with type inference at each step of the AST. The non-deterministic types are highlighted with colors on a terminal or Jupyter console7. There are many variables assigned to the type `<strong>Any</strong>`. This essentially means there will be an allocation for the location of memory and indirection to actual `<strong>Float64</strong>` value during any computation. We will add a type to the declaration for the parameter `<strong>x</strong>` and see how that affects the type inferences.

**Figure 11.1:** Julia vs Competiting Platforms6

The `<strong>memoize(f)</strong>` is a higher order function that can memoize a function with its parameters for subsequent value retrieval. The memo dictionary is accessed as a closure12 by the anonymous function returned by `<strong>memoize</strong>`. With a function like `<strong>memoize</strong>` you can define `<strong>fib(n)</strong>` method as shown:

While there is no problem in the code in terms of type inference (there are no `<strong>Any</strong>` types), `<strong>x</strong>` is assigned a `<strong>Tuple{Float64}</strong>`. This essentially means a new variable will be created and function input will be assigned to this newly created tuple8. If we redefine the `<strong>sindeg</strong>` function as:

We got very close to the performance of `<strong>sind(x)</strong>` but are not quite there9. One obvious question, why `<strong>sindegmemo</strong>` performs better when the input is 60° than the input of 22°?

However, `<strong>Memoize.jl</strong>` package13 has a `<strong>@memoize</strong>` macro that can help specify if the function is memoization aware.

Evan Jones, The Unreasonable Effectiveness of Linear Search, Blog Post, September 10, 2018, **[https://www.evanjones.ca/linear-search.html](https://www.evanjones.ca/linear-search.html)** last accessed: January 14, 2021.

Ideal Loop Processing, Microsoft MSDN Documentation, Visual Studio 2019, **[https://docs.microsoft.com/en-us/cpp/mfc/idle-loop-processing?view=msvc-160](https://docs.microsoft.com/en-us/cpp/mfc/idle-loop-processing?view=msvc-160)**, last accessed January 12, 2021

Voyager 1 just left the solar system using less computing power than your iPhone, Washington Post, **[https://www.washingtonpost.com/news/the-switch/wp/2013/09/12/voyager-1-just-left-the-solar-system-using-less-computing-power-than-your-iphone/](https://www.washingtonpost.com/news/the-switch/wp/2013/09/12/voyager-1-just-left-the-solar-system-using-less-computing-power-than-your-iphone/)** September 13, 2013, last accessed January 12, 2021

Brian W. Kernighan and Rob Pike, The Practice of Programming, Chapter 7, Addison-Wesley, 1999

The native Julia functions `<strong>sin</strong>` and `<strong>cos</strong>` are not utilizing the CPU instruction `<strong>FSIN</strong>`or `<strong>FSINCOS</strong>` as found in the Intel chipset. But, a 13-degree polynomial is computed using an optimized Horner’s method. The interested readers can review the code at the GitHub link: **[https://github.com/JuliaLang/julia/blob/cf9bcc7a49863ea47facbd93a2d920b0bf1e96ff/base/special/trig.jl#L69](https://github.com/JuliaLang/julia/blob/cf9bcc7a49863ea47facbd93a2d920b0bf1e96ff/base/special/trig.jl#L69)**. You can generate the bitcode for their native processors using the macro `<strong>@code_native</strong>` and verify.

This code is from the 1.5.3 version of Julia. The relevant code is:  
`∘<strong>(f, g) = (x…)-&gt;f(g(x…))</strong>`  
A composition operator on two functions shall essentially, create an anonymous function and assign to the variable. `<strong>sindeg</strong>` is just a variable which is assigned an anonymous function of type: `<strong>Base.var"#62#63"{typeof(sin), typeof(deg2rad).</strong>`

We have only bold faced the variables mapped to type `Any`. In the terminal output, you will be seeing variables with non-deterministic types highlighted in red or brown and deterministic types in green or cyan. `@code_typed` also reports almost similar information as `@code_warntype`. However, it does not highlight the type of warnings.

Julia Micro-Benchmarks, **[https://julialang.org/benchmarks/](https://julialang.org/benchmarks/)** last accessed: 1423^(th) January 2021

These are called micro-benchmarks as they are performance measured for specific tasks not a complete system.

# 

# 

# 

IDEs and GUI-based line debugging utilities are common tools for application development today. While functional programmers prefer short verifiable units of code that can be validated independently, debugging still is much sought-after tool for any programming environment. Julia has quite an elaborate GUI-based IDE with debugging environment.

# 

In this chapter, we will cover the following topics:

*   Background
*   Editor integration
*   IDE
*   Debugging
*   Code-Run-Fix

# 

In this chapter, the reader shall be able to understand, the capabilities of well-known editors in rendering Julia code. There are a few well-known **Integrated Development Environments** (**IDEs**) that provide support for development with Julia. Debugging of programs is a useful skill and IDEs help debug code line-by-line. We will look into some of techniques that help to debug as part of this chapter.

# 

REPL is a great utility when trying simple code segments for prototyping. However, production quality code development requires large volumes of code to be written, debugged, and verified. While an average engineer may be writing under 20 lines of code a day, the number of lines of code in maintenance is really large[1](#iftzdvy1.html#n4upl4fndk5). Unless you have informative visualization, it is not practical to be able to maintain such code. While most code is written as plaintext, source code editing requires certain aspects of the language to be understood by the editors.

1.  **Syntax highlighting**: Programmers use various indentation schemes while editing code; for example: tabs vs space, matching of delimiters like brackets, keywords like `<strong>function…end</strong>` or `<strong>try…end</strong>`. The highlighting is dynamic as well; while typing the relevant matching parenthesis is highlighted. Automatically inserting matched parenthesis is another area the editors help while typing. The highlighting can be with multiple colored texts, changing the type face to bold or italics. Some editors provide the flexibility to the users to define their own highlighting schemes.
2.  **Declaration or definition to usage matching**: When a function is being used, a programmer will like to see the definition of the function to understand how it works. In older editors, reference tags were generated as part of the compilation process with tools like `<strong>ctags</strong>` or `<strong>etags</strong>`. These tags were loaded into the editors for getting to reference locations of the functions. Some integrated development platforms like the visual studio would generate tags as part of code compilation to be able to track caller and callee graphs of the functions.
3.  **Documentation reference**: A developer will like to look at the documentation of a function before using it. While integrated document generation systems like literate programming[2](#iftzdvy1.html#n4upl4fndk6) have been in existence for several decades, help lookup of functions is particularly useful and popularized by Javadoc integration with IDEs. Visual Studio and many IDEs for Python language offer similar functionalities.
4.  **Code and data bundling**: Data used during the execution of the code like the user interface or string resources can be created using IDEs and embedded in the executables as a part of the compilation and linking process. Code and data are organized in specific directory structures and maintained in metadata called project or solution files. These metadata ensure the consistent organization of the code in the IDE.
5.  **Building of executables**: The integration of the build tools with IDEs provides a seamless build experience; for example, automation of build steps as the code is modified. The builds can cater to specific environment configurations like debug versus release executables. Invocation of specific environment start up scripts can be carried out as part of the runtime activities.
6.  **Test execution and debugging**: The code built can be run immediately with or without additional inputs to verify the code. Integrated test suites also offer complete validation of unit tests against the code modified. The ability to put breakpoints and debug each line of code execution while verifying the values of the variables are one of the most important functionalities of the IDEs.
7.  **Source control**: Many IDEs provide integration with source control. The code can be checked out from the remote repositories, modified, and checked back into the final remote repository. Some of the advanced IDEs even provided sharing of private workspaces between developers for collaborative application development ^(\[[3](#iftzdvy1.html#n4upl4fndk7),[4](#iftzdvy1.html#n4upl4fndk8)\]).
8.  **Deployment**: With cloud deployments being the standard for most production deployments, the final output needs to be integrated into an operations framework. For example, the final code needs to be packaged into deployable containers or virtual machine template so that they can be pushed onto the private or public cloud. This is part of a DevOps framework where development and operations are presented a unified view reducing costs and management overheads.

Julia is a relatively newer platform. The ecosystem for all the preceding components existed before Julia became popular as a language. Developers will like to see Julia seamlessly be used along with the tools they are most comfortable with. In the world of text editors in the UNIX environments, there is almost cult following for `<strong>vi</strong>` vs. `<strong>emacs</strong>`[5](#iftzdvy1.html#n4upl4fndk9). JuliaEditorSupport[6](#iftzdvy1.html#n4upl4fndla) organization under *GitHub* maintains integration with several of the well-known editors at differing levels of capabilities; some such editors being *Vim*, *Emacs*, *Sublime*, *Atom*, *Notepad++*, and *Eclipse*. Some of the integrations are active while many are deprecated due to lack of focus and usage. Julia IDEs are being developed for *Atom* under a project *Juno*[7](#iftzdvy1.html#n4upl4fndlb) and Microsoft **Visual Studio Code** (**VS Code**)[8](#iftzdvy1.html#n4upl4fndlc).

# 

With editor integrations, one can experience simple syntax highlighting, some navigation helpers, tagging of code to locate code blocks. The experience will not be IDE like. Although, some integrations are called plug-ins they are limited to simple scripts and regular expressions for syntax highlighting and tracking.

# 

`<strong>vi</strong>` has taken a significant mindshare in the UNIX community as one of the oldest multiline text editors. The extended version of `<strong>vi</strong>` called `<strong>vim</strong>` is rather the most popular flavor of the editor:

![](n4upl4fndq4.jpeg)

**Figure 12.1:** Syntax highlighting using julia-vim

The Julia plug-in for `<strong>vim</strong>`, called `<strong>julia-vim</strong>`, is a *GitHub* project[9](#iftzdvy1.html#n4upl4fndld) that can be installed in a `<strong>vim</strong>` set up for Mac OS X, UNIX, and Windows operating systems[10](#iftzdvy1.html#n4upl4fndle). The plug-in is a set of vim scripts that provide the following functionalities:

*   Syntax highlighting of Julia code, documentation, and links.
*   Integration with `<strong>ctags</strong>` for navigation.
*   Moving along code blocks, matching to code regular expressions or matched parenthesis, and so on.
*   Latex to Unicode substitution for specifying Julia variables and parameters as Unicode characters.
*   While some people have used terminal emulations with vim to use Julia REPL, it is not part of the plug-in per se[11](#iftzdvy1.html#n4upl4fndlf).
*   `<strong>vim</strong>` integration does not have any concept of a workspace or project to organize the Julia code as a package.

# 

It is one of the most popular editors in the UNIX platforms like `<strong>vi</strong>`. Unlike vi, where the focus is text editing, `<strong>Emacs</strong>` is developed more like a programmer's development environment. It has integrations with terminals, build systems, source control, email, internet browsers, and so on. Although originally started as a text-based system, it now integrates into most GUIs and runs equally well on Windows, UNIX, and Mac OS X operating systems. It also ships a LISP like scripting interface (Emacs Lisp) to develop customized solutions. Hence, you will see the integration with Julia is far elaborate and evolved. Emacs also has package management systems like `<strong>GNU elpa</strong>` and `<strong>melpa</strong>` to find and use various packages needed:

![](n4upl4fndq5.jpeg)

**Figure 12.2:** julia-emacs in action

 shows the `<strong>julia-emacs</strong>` screen with Julia as a major mode while Git integration shows up as a minor mode. The functions and constants show up as menu items that can aid quick navigation within a file. Emacs integration further allows the REPL to be loaded along with the `<strong>julia-emacs</strong>`, thus loading an environment for evaluating and debugging. Julia also integrates with a package called Emacs Speaks Statistics that supports other languages like R, S-plus, SAS and Stata, and so on. The package provides granular evaluation of a Julia code block, parts of an emacs code for rapid prototyping. This helps debug and test small chunks of code independently while still developing the code:

![](n4upl4fndq6.jpeg)

**Figure 12.3:** Julia sources and ESS eval buffer result side by side

While Julia integration with `<strong>emacs</strong>` is far deeper than `<strong>vim</strong>` in capabilities, some platforms like Windows may not provide a good terminal experience with the REPL.

# 

Just like `<strong>vi</strong>` and `<strong>emacs</strong>` are the most prevalent editors in the UNIX world, *Notepad++* has been a popular editor in the Windows operating systems with no direct port to the Unix or Mac OS X operating systems[12](#iftzdvy1.html#n4upl4fndlg). However, it is not to be confused with `<strong>notepad.exe</strong>`, shipping by default in the Windows Operating Systems with bare minimal text editing. *Notepad++* is a relatively advanced text editor, has complete plug-in capabilities to program and enhance editor rendering experiences. It also has the capability of customizing language syntax highlighting through **User Defined Languages** (**UDL**). The UDLs are an easier way to provide certain syntactic structures in an XML file and can be used to identify and render the files effectively:

![](n4upl4fndq7.jpeg)

**Figure 12.4:** Julia-NotepadPlusPlus UDL in action

UDL for Julia is available in the *GitHub* project `<strong>Julia-NotepadPlusPlus</strong>`[13](#iftzdvy1.html#n4upl4fndlh).

# 

`<strong>IDEs</strong>` are complete development platforms that help manage workspaces, projects and serve as editors, build, test, debug, and deployment tools. While there are many standard IDEs popular in the industry, Julia has the most elaborate integrations with *Atom* and *Microsoft Visual Studio Code* which we shall look into in the subsequent sections. Julia also has work-in-progress integration with *IntelliJ*[14](#iftzdvy1.html#n4upl4fndli) and an archived integration with Eclipse[15](#iftzdvy1.html#n4upl4fndlj).

# 

Atom is a HTML 5 rich client application using the Electron framework based on JavaScript, HTML, and CSS. It utilizes components of *NodeJS* and *Chromium* browsers for rendering. While Atom is one of the most used apps, there are almost a thousand apps published on the cross-platform framework, providing it a solid foundation:

![](n4upl4fndq8.jpeg)

**Figure 12.5:** Juno IDE with directory, code, REPL views

The Juno IDE which is the backbone of Julia integration with *Atom* is also the editor of choice for Julia PRO[16](#iftzdvy1.html#n4upl4fndlk), the commercial offering from Julia Computing. However, with Microsoft VS Code integrations some of the focus from this editor is slowly moving away[17](#iftzdvy1.html#n4upl4fndll):

![](n4upl4fndq9.jpeg)

**Figure 12.6:** The expanded Juno menu item showing functionalities

The Juno tab aggregates a large number of Julia integration functionalities like:

*   Launching Julia
*   Running portions of code and verifying the result
*   Formatting code
*   Debugging the complete code or a block of code

# 

Microsoft Visual Studio is a well-known front end for almost all of the software development for the Microsoft ecosystem. However, as Microsoft tried to establish itself as a dominant player in the cloud infrastructure market, it became necessary for Microsoft to introduce tools that are not bound to the Windows ecosystem. Microsoft introduced Visual Studio Code in 2015 to cater to such needs. Developed using an open-source code base using the Electron framework, VS Code is available on Windows, Linux, and Mac OS X platforms[18](#iftzdvy1.html#n4upl4fndlm). One can find the VS Code experience similar to Atom:

*   Integration with *Git* and *GitHub*
*   Various panes for Project Folders and Files, Runtime outputs, and results
*   Ability to Launch Julia to Run and Debug
*   Integration with Plot outputs from Julia, and so on:

![](n4upl4fndra.jpeg)

**Figure 12.7:** VS Code with Julia extension

You can open the file `<strong>plot.jl</strong>` from the sample code in VS Code with the Julia extension installed. If you run the file by right-clicking it, you shall be able to see the following screen with the plot displayed right next to the code:

![](n4upl4fndrb.jpeg)

**Figure 12.8:** Julia Plots displayed in the VS Code UI

As can be seen, both *Atom* and *VS Code* are useful and important developer tools. Right now, there is a greater thrust on the *VS Code* development. We shall suggest practitioners expose themselves to both the IDEs before deciding one over the other.

# 

An anecdote[19](#iftzdvy1.html#n4upl4fndln) suggests Grace Hopper’s team members discovered and removed a physical bug in a computer circuitry and were able to fix a non-functioning program. The science of finding fault in a computer program and fixing it is thus called `<strong>debugging</strong>`. Debugging can be a frustrating and challenging process particularly when the code is not written by the developer trying to fix it. At the same time, it is the most rewarding experience for new programmers to learn from other people’s code and also understand varieties of styles of programs out there in the wild. A programmer spends about 35–50% of productive time and 50–75% of the cost in software debugging[20](#iftzdvy1.html#n4upl4fndlo). While tools have reduced the time spent in debugging individual tasks, the overall time spent on such activities remains the same. While the study has emphasized on enhancing learning behavior, it has also been seen debugging requires effective knowledge of the tools.

# 

While in most cases we know the states a program will be transitioning over, it may not be possible to accurately predict over all the states. Prints or log messages are a good way to communicate your possible output at intermediate steps. Even `<strong>assert</strong>` macro is a good way of validating expected assumptions. While being a crude way to verify the correct behavior of these processes are still the most used debugging steps.

# 

Unit tests are another great way to keep the bugs in the code to the minimum. Julia has an elaborate unit test framework that we shall review in the next chapter. As a good practice, the unit test must ensure the following:

*   The test cases must include sufficient conditions along with the normal range of operation.
*   They should also consider all negative and boundary conditions.
*   Each test case must validate only one of the functionalities. Testing multiple functionalities creates unnecessary confusion in the code.
*   The previous step improves test efficacy if the functions are pure and have no side effects. In such cases, there are lesser internal states to manage, and remnants of previous results shall not affect the test cases.

# 

REPL is another great tool for debugging. However, for such tools to be effective one must practice writing small chunks of code into reusable functions. Pure functions shall make it even better. When a language has way too many features, it gets harder for the programmer to know all of the syntax and semantics of the language. The possibilities of making mistakes increase substantially. In such a case, testing small chunks of code independently in a REPL before actually using them is of significant value. Let us look at our earlier code on Fibonacci series.

`<strong>fib(n) = n &lt; 3 ? 1 : fib(n-1) + fib(n-2)</strong>`

Here are some test outcomes from the running the code in the REPL.

`<strong>julia&gt; fib(3)</strong>`

`<strong>2</strong>`

`<strong>julia&gt; fib(10)</strong>`

`<strong>55</strong>`

`<strong>julia&gt; fib(-1)</strong>`

`<strong>1</strong>`

`<strong>julia&gt; fib(0)</strong>`

`<strong>1</strong>`

The recursive function terminates as there is a termination condition for all values of `<strong>n &lt; 3</strong>`. The fundamental question remains if the Fibonacci sequence is valid for negative values of `<strong>n</strong>`. Having a small pure function and verifying it in the REPL makes it easier to ensure a properly running code is verified and introduced into the actual code. Running parts of code in the IDE is another way to achieve the same result.

While the preceding ones are some of the easier ways to test and use small chunks of code, they are unlike the line debugging used with tools like `<strong>gdb</strong>` for native binaries. Julia has a fully functional debugger for the command line[21](#iftzdvy1.html#n4upl4fndlp).

# 

Line debugging is best carried out with the IDEs as it is easier to set break points using the pointers; add watches on variables and see those values change as you step-in, step-out, or step-over of the code blocks or functions. You can run the code until a particular condition is met or a break point is hit. While line debugging is the most sought-after technique for most programmers, it may not be the most efficient option for an interpreted language like Julia.

*   Initializing the debugger environment can be very slow.
*   Debugging may require higher amount of memory.
*   Stepping over the code and verifying watch variables can be a slow process in itself.
*   Line debugging is the last option when one does not have enough understanding of the code or does not have any easier means to eliminate code that is already functioning properly.
*   Line debugging can be very effective when the erroneous code can be localized to a very small part and specifically validated:

![](n4upl4fndrc.jpeg)

**Figure 12.9:** Julia source code being debugged in VS Code

The readers can open the file `<strong>fibonacci.jl</strong>` in the IDE using VS Code or Atom and debug the code.

# 

However, adept a programmer is, she would like to try the idea in her mind, quickly experience the outcome, fix the changes, and move on with the next chunk of code. Julia's runtime is pre-loaded. As you load more data structures or modules and packages to the system, the older symbols and code blocks get loaded to the runtime. It may not be possible to modify the symbols already defined without affecting the overall working of the runtime elsewhere. For example, changing a function definition in the REPL is straightforward. But, adding or removing an attribute of a `<strong>struct</strong>` data type is not permitted. When a package is modified, it is not loaded on the subsequent usage of the command using `<strong>&lt;&lt;module&gt;&gt;</strong>`. To overcome these limitations, `<strong>Revise.jl</strong>`[22](#iftzdvy1.html#n4upl4fndlq) package may be used. This package can be autoloaded and can update symbols as part of code-run-fix cycles of development. We suggest the readers review the package documentation for a detailed understanding.

# 

We have come a long way in our journey along with Julia. We started with understanding the language, worked on a few sample examples; tried to use REPL or Jupyter to experience the language capabilities. In this chapter, we looked at a few of the tools for better editing and debugging experience with the code. In the next chapter, we shall try to gain the expertise in building Julia projects and organize them in a manner that is commonly expected.

# 

1.  Install the Julia extension or plug-in for a text editor of your choice. Observe various functionalities offered by the editor.
2.  Install Emacs. How can you integrate Julia mode with the Emacs speaks statistics? Do you see any problems or concerns?
3.  Install Juno and open a Julia package of your choice and try to debug it.
4.  Install Julia for VSCode and open a Julia package of your choice and try to debug it.
5.  What are some of the effective techniques to debugging? Do you feel line debugging is the only way forward?

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

[1](#iftzdvy1.html#n4upl4fndlr) Sage McEnery, How much computer code has been written?, 18^(th) July 2020, **[https://medium.com/modern-stack/how-much-computer-code-has-been-written-c8c03100f459](https://medium.com/modern-stack/how-much-computer-code-has-been-written-c8c03100f459)** last accessed: 23rd Jan 2021.

[2](#iftzdvy1.html#n4upl4fndls) D. E. Knuth, Literate Programming, The Computer Journal, September 1983

[3](#iftzdvy1.html#n4upl4fndlt) IBM Rational ClearCase, **[https://www.ibm.com/support/knowledgecenter/SSSH27\_9.1/com.ibm.rational.clearcase.help.ic.doc/topics/c\_product\_ovw.htm](https://www.ibm.com/support/knowledgecenter/SSSH27_9.1/com.ibm.rational.clearcase.help.ic.doc/topics/c_product_ovw.htm)**

[4](#iftzdvy1.html#n4upl4fndlu) Microsoft Visual Studio Teams Services, **[https://visualstudio.microsoft.com/vs/features/collaborate/](https://visualstudio.microsoft.com/vs/features/collaborate/)**

[5](#iftzdvy1.html#n4upl4fndlv) Editor War, **[https://en.wikipedia.org/wiki/Editor\_war](https://en.wikipedia.org/wiki/Editor_war)**

[6](#iftzdvy1.html#n4upl4fndlw) Julia Editor Support, **[https://github.com/JuliaEditorSupport](https://github.com/JuliaEditorSupport)**

[7](#iftzdvy1.html#n4upl4fndlx) The Juno Project, **[https://junolab.org/](https://junolab.org/)**

[8](#iftzdvy1.html#n4upl4fndly) Julia for VS Code **[https://www.julia-vscode.org/](https://www.julia-vscode.org/)**

[9](#iftzdvy1.html#n4upl4fndlz) `julia-vim`, **[https://github.com/JuliaEditorSupport/julia-vim](https://github.com/JuliaEditorSupport/julia-vim)**

[10](#iftzdvy1.html#n4upl4fndl0) Installation Guideline `julia-vim`, **[https://github.com/JuliaEditorSupport/julia-vim/blob/master/INSTALL.md](https://github.com/JuliaEditorSupport/julia-vim/blob/master/INSTALL.md)**

[11](#iftzdvy1.html#n4upl4fndl1) Julia-vim tutorial for newbies, Julia Discourse Post, **[https://discourse.julialang.org/t/julia-vim-tutorial-for-newbies/36636/6](https://discourse.julialang.org/t/julia-vim-tutorial-for-newbies/36636/6)**

[12](#iftzdvy1.html#n4upl4fndl2) Some attempts have been made to run `Notepad++` in Linux using Wine emulator. Editors like `Sublime Text` have Julia integrations as well.

[13](#iftzdvy1.html#n4upl4fndl3) `Julia-NotepadPlusPlus`, Git Hub Repository, **[https://github.com/JuliaEditorSupport/julia-NotepadPlusPlus](https://github.com/JuliaEditorSupport/julia-NotepadPlusPlus)**

[14](#iftzdvy1.html#n4upl4fndl4) `julia-intellij`, GitHub Project, **[https://github.com/JuliaEditorSupport/julia-intellij](https://github.com/JuliaEditorSupport/julia-intellij)**

[15](#iftzdvy1.html#n4upl4fndl5) juliaDT, GitHub Project, **[https://github.com/JuliaEditorSupport/JuliaDT](https://github.com/JuliaEditorSupport/JuliaDT)**

[16](#iftzdvy1.html#n4upl4fndl6) Julia PRO, **[https://juliacomputing.com/products/juliapro/](https://juliacomputing.com/products/juliapro/)**

[17](#iftzdvy1.html#n4upl4fndl7) Julia client for Atom is entering maintenance mode, **[https://atom.io/packages/julia-client](https://atom.io/packages/julia-client)** last accessed: 27th Jan 2021

[18](#iftzdvy1.html#n4upl4fndl8) Visual Studio Code, **[https://code.visualstudio.com/](https://code.visualstudio.com/)**

[19](#iftzdvy1.html#n4upl4fndl9) Anecdotes, Grace Hopper, Wikipedia, **[https://en.wikipedia.org/wiki/Grace\_Hopper](https://en.wikipedia.org/wiki/Grace_Hopper)**

[20](#iftzdvy1.html#n4upl4fndma) Devon H. O’Dell, The Debugging Mindset, acmqueue, Jan-Feb 2017

[21](#iftzdvy1.html#n4upl4fndmb) Tim Holy, Kristoffer Carlsson, Sebastian Pfitzner, Keno Fischer, A Julia interpreter and debugger, 19^(th) March 2019, The JuliaLang Blogs, **[https://julialang.org/blog/2019/03/debuggers/](https://julialang.org/blog/2019/03/debuggers/)** last accessed: 30^(th) Jan 2021

[22](#iftzdvy1.html#n4upl4fndmc) `Revise.jl`, Automatically update function definitions in a running Julia session, **[https://github.com/timholy/Revise.jl](https://github.com/timholy/Revise.jl)**

An anecdote19 suggests Grace Hopper’s team members discovered and removed a physical bug in a computer circuitry and were able to fix a non-functioning program. The science of finding fault in a computer program and fixing it is thus called `<strong>debugging</strong>`. Debugging can be a frustrating and challenging process particularly when the code is not written by the developer trying to fix it. At the same time, it is the most rewarding experience for new programmers to learn from other people’s code and also understand varieties of styles of programs out there in the wild. A programmer spends about 35–50% of productive time and 50–75% of the cost in software debugging20. While tools have reduced the time spent in debugging individual tasks, the overall time spent on such activities remains the same. While the study has emphasized on enhancing learning behavior, it has also been seen debugging requires effective knowledge of the tools.

The Julia plug-in for `<strong>vim</strong>`, called `<strong>julia-vim</strong>`, is a *GitHub* project9 that can be installed in a `<strong>vim</strong>` set up for Mac OS X, UNIX, and Windows operating systems10. The plug-in is a set of vim scripts that provide the following functionalities:

However, adept a programmer is, she would like to try the idea in her mind, quickly experience the outcome, fix the changes, and move on with the next chunk of code. Julia's runtime is pre-loaded. As you load more data structures or modules and packages to the system, the older symbols and code blocks get loaded to the runtime. It may not be possible to modify the symbols already defined without affecting the overall working of the runtime elsewhere. For example, changing a function definition in the REPL is straightforward. But, adding or removing an attribute of a `<strong>struct</strong>` data type is not permitted. When a package is modified, it is not loaded on the subsequent usage of the command using `<strong>&lt;&lt;module&gt;&gt;</strong>`. To overcome these limitations, `<strong>Revise.jl</strong>`22 package may be used. This package can be autoloaded and can update symbols as part of code-run-fix cycles of development. We suggest the readers review the package documentation for a detailed understanding.

^(\[3,4\]) 

While the preceding ones are some of the easier ways to test and use small chunks of code, they are unlike the line debugging used with tools like `<strong>gdb</strong>` for native binaries. Julia has a fully functional debugger for the command line21.

^(\[3,4\]) 

An anecdote19 suggests Grace Hopper’s team members discovered and removed a physical bug in a computer circuitry and were able to fix a non-functioning program. The science of finding fault in a computer program and fixing it is thus called `<strong>debugging</strong>`. Debugging can be a frustrating and challenging process particularly when the code is not written by the developer trying to fix it. At the same time, it is the most rewarding experience for new programmers to learn from other people’s code and also understand varieties of styles of programs out there in the wild. A programmer spends about 35–50% of productive time and 50–75% of the cost in software debugging20. While tools have reduced the time spent in debugging individual tasks, the overall time spent on such activities remains the same. While the study has emphasized on enhancing learning behavior, it has also been seen debugging requires effective knowledge of the tools.

Julia is a relatively newer platform. The ecosystem for all the preceding components existed before Julia became popular as a language. Developers will like to see Julia seamlessly be used along with the tools they are most comfortable with. In the world of text editors in the UNIX environments, there is almost cult following for `<strong>vi</strong>` vs. `<strong>emacs</strong>`5. JuliaEditorSupport6 organization under *GitHub* maintains integration with several of the well-known editors at differing levels of capabilities; some such editors being *Vim*, *Emacs*, *Sublime*, *Atom*, *Notepad++*, and *Eclipse*. Some of the integrations are active while many are deprecated due to lack of focus and usage. Julia IDEs are being developed for *Atom* under a project *Juno*7 and Microsoft **Visual Studio Code** (**VS Code**)8.

Julia is a relatively newer platform. The ecosystem for all the preceding components existed before Julia became popular as a language. Developers will like to see Julia seamlessly be used along with the tools they are most comfortable with. In the world of text editors in the UNIX environments, there is almost cult following for `<strong>vi</strong>` vs. `<strong>emacs</strong>`5. JuliaEditorSupport6 organization under *GitHub* maintains integration with several of the well-known editors at differing levels of capabilities; some such editors being *Vim*, *Emacs*, *Sublime*, *Atom*, *Notepad++*, and *Eclipse*. Some of the integrations are active while many are deprecated due to lack of focus and usage. Julia IDEs are being developed for *Atom* under a project *Juno*7 and Microsoft **Visual Studio Code** (**VS Code**)8.

Julia client for Atom is entering maintenance mode, **[https://atom.io/packages/julia-client](https://atom.io/packages/julia-client)** last accessed: 27th Jan 2021

Visual Studio Code, **[https://code.visualstudio.com/](https://code.visualstudio.com/)**

Anecdotes, Grace Hopper, Wikipedia, **[https://en.wikipedia.org/wiki/Grace\_Hopper](https://en.wikipedia.org/wiki/Grace_Hopper)**

`Julia-NotepadPlusPlus`, Git Hub Repository, **[https://github.com/JuliaEditorSupport/julia-NotepadPlusPlus](https://github.com/JuliaEditorSupport/julia-NotepadPlusPlus)**

`julia-intellij`, GitHub Project, **[https://github.com/JuliaEditorSupport/julia-intellij](https://github.com/JuliaEditorSupport/julia-intellij)**

juliaDT, GitHub Project, **[https://github.com/JuliaEditorSupport/JuliaDT](https://github.com/JuliaEditorSupport/JuliaDT)**

Julia PRO, **[https://juliacomputing.com/products/juliapro/](https://juliacomputing.com/products/juliapro/)**

Installation Guideline `julia-vim`, **[https://github.com/JuliaEditorSupport/julia-vim/blob/master/INSTALL.md](https://github.com/JuliaEditorSupport/julia-vim/blob/master/INSTALL.md)**

Julia-vim tutorial for newbies, Julia Discourse Post, **[https://discourse.julialang.org/t/julia-vim-tutorial-for-newbies/36636/6](https://discourse.julialang.org/t/julia-vim-tutorial-for-newbies/36636/6)**

Some attempts have been made to run `Notepad++` in Linux using Wine emulator. Editors like `Sublime Text` have Julia integrations as well.

Devon H. O’Dell, The Debugging Mindset, acmqueue, Jan-Feb 2017

Tim Holy, Kristoffer Carlsson, Sebastian Pfitzner, Keno Fischer, A Julia interpreter and debugger, 19^(th) March 2019, The JuliaLang Blogs, **[https://julialang.org/blog/2019/03/debuggers/](https://julialang.org/blog/2019/03/debuggers/)** last accessed: 30^(th) Jan 2021

`Revise.jl`, Automatically update function definitions in a running Julia session, **[https://github.com/timholy/Revise.jl](https://github.com/timholy/Revise.jl)**

REPL is a great utility when trying simple code segments for prototyping. However, production quality code development requires large volumes of code to be written, debugged, and verified. While an average engineer may be writing under 20 lines of code a day, the number of lines of code in maintenance is really large1. Unless you have informative visualization, it is not practical to be able to maintain such code. While most code is written as plaintext, source code editing requires certain aspects of the language to be understood by the editors.

*   **Documentation reference**: A developer will like to look at the documentation of a function before using it. While integrated document generation systems like literate programming2 have been in existence for several decades, help lookup of functions is particularly useful and popularized by Javadoc integration with IDEs. Visual Studio and many IDEs for Python language offer similar functionalities. 

Sage McEnery, How much computer code has been written?, 18^(th) July 2020, **[https://medium.com/modern-stack/how-much-computer-code-has-been-written-c8c03100f459](https://medium.com/modern-stack/how-much-computer-code-has-been-written-c8c03100f459)** last accessed: 23rd Jan 2021.

D. E. Knuth, Literate Programming, The Computer Journal, September 1983

IBM Rational ClearCase, **[https://www.ibm.com/support/knowledgecenter/SSSH27\_9.1/com.ibm.rational.clearcase.help.ic.doc/topics/c\_product\_ovw.htm](https://www.ibm.com/support/knowledgecenter/SSSH27_9.1/com.ibm.rational.clearcase.help.ic.doc/topics/c_product_ovw.htm)**

Microsoft Visual Studio Teams Services, **[https://visualstudio.microsoft.com/vs/features/collaborate/](https://visualstudio.microsoft.com/vs/features/collaborate/)**

Editor War, **[https://en.wikipedia.org/wiki/Editor\_war](https://en.wikipedia.org/wiki/Editor_war)**

Microsoft Visual Studio is a well-known front end for almost all of the software development for the Microsoft ecosystem. However, as Microsoft tried to establish itself as a dominant player in the cloud infrastructure market, it became necessary for Microsoft to introduce tools that are not bound to the Windows ecosystem. Microsoft introduced Visual Studio Code in 2015 to cater to such needs. Developed using an open-source code base using the Electron framework, VS Code is available on Windows, Linux, and Mac OS X platforms18. One can find the VS Code experience similar to Atom:

The Juno IDE which is the backbone of Julia integration with *Atom* is also the editor of choice for Julia PRO16, the commercial offering from Julia Computing. However, with Microsoft VS Code integrations some of the focus from this editor is slowly moving away17:

The Juno IDE which is the backbone of Julia integration with *Atom* is also the editor of choice for Julia PRO16, the commercial offering from Julia Computing. However, with Microsoft VS Code integrations some of the focus from this editor is slowly moving away17:

`<strong>IDEs</strong>` are complete development platforms that help manage workspaces, projects and serve as editors, build, test, debug, and deployment tools. While there are many standard IDEs popular in the industry, Julia has the most elaborate integrations with *Atom* and *Microsoft Visual Studio Code* which we shall look into in the subsequent sections. Julia also has work-in-progress integration with *IntelliJ*14 and an archived integration with Eclipse15.

Julia is a relatively newer platform. The ecosystem for all the preceding components existed before Julia became popular as a language. Developers will like to see Julia seamlessly be used along with the tools they are most comfortable with. In the world of text editors in the UNIX environments, there is almost cult following for `<strong>vi</strong>` vs. `<strong>emacs</strong>`5. JuliaEditorSupport6 organization under *GitHub* maintains integration with several of the well-known editors at differing levels of capabilities; some such editors being *Vim*, *Emacs*, *Sublime*, *Atom*, *Notepad++*, and *Eclipse*. Some of the integrations are active while many are deprecated due to lack of focus and usage. Julia IDEs are being developed for *Atom* under a project *Juno*7 and Microsoft **Visual Studio Code** (**VS Code**)8.

`<strong>IDEs</strong>` are complete development platforms that help manage workspaces, projects and serve as editors, build, test, debug, and deployment tools. While there are many standard IDEs popular in the industry, Julia has the most elaborate integrations with *Atom* and *Microsoft Visual Studio Code* which we shall look into in the subsequent sections. Julia also has work-in-progress integration with *IntelliJ*14 and an archived integration with Eclipse15.

Julia is a relatively newer platform. The ecosystem for all the preceding components existed before Julia became popular as a language. Developers will like to see Julia seamlessly be used along with the tools they are most comfortable with. In the world of text editors in the UNIX environments, there is almost cult following for `<strong>vi</strong>` vs. `<strong>emacs</strong>`5. JuliaEditorSupport6 organization under *GitHub* maintains integration with several of the well-known editors at differing levels of capabilities; some such editors being *Vim*, *Emacs*, *Sublime*, *Atom*, *Notepad++*, and *Eclipse*. Some of the integrations are active while many are deprecated due to lack of focus and usage. Julia IDEs are being developed for *Atom* under a project *Juno*7 and Microsoft **Visual Studio Code** (**VS Code**)8.

The Julia plug-in for `<strong>vim</strong>`, called `<strong>julia-vim</strong>`, is a *GitHub* project9 that can be installed in a `<strong>vim</strong>` set up for Mac OS X, UNIX, and Windows operating systems10. The plug-in is a set of vim scripts that provide the following functionalities:

UDL for Julia is available in the *GitHub* project `<strong>Julia-NotepadPlusPlus</strong>`13.

Just like `<strong>vi</strong>` and `<strong>emacs</strong>` are the most prevalent editors in the UNIX world, *Notepad++* has been a popular editor in the Windows operating systems with no direct port to the Unix or Mac OS X operating systems12. However, it is not to be confused with `<strong>notepad.exe</strong>`, shipping by default in the Windows Operating Systems with bare minimal text editing. *Notepad++* is a relatively advanced text editor, has complete plug-in capabilities to program and enhance editor rendering experiences. It also has the capability of customizing language syntax highlighting through **User Defined Languages** (**UDL**). The UDLs are an easier way to provide certain syntactic structures in an XML file and can be used to identify and render the files effectively:

*   While some people have used terminal emulations with vim to use Julia REPL, it is not part of the plug-in per se11. 

Julia Editor Support, **[https://github.com/JuliaEditorSupport](https://github.com/JuliaEditorSupport)**

The Juno Project, **[https://junolab.org/](https://junolab.org/)**

Julia for VS Code **[https://www.julia-vscode.org/](https://www.julia-vscode.org/)**

`julia-vim`, **[https://github.com/JuliaEditorSupport/julia-vim](https://github.com/JuliaEditorSupport/julia-vim)**

# 

# 

# 

Over the past several chapters you were wondering how to go about developing production-ready applications. The wait is almost over. This chapter shall provide the know how to build real-life applications; from solving toy problems to working on projects that you really would like to work on.

# 

In this chapter, we will cover the following topics:

*   Background
*   Projects, modules, and packages
*   Test automation
*   Documentation
*   Continuous integration
*   Binary dependencies
*   Environments
*   Package architecture

# 

In this chapter, the reader will be able to understand packaging the code for production use. You can use the binaries built with other languages in your package as well. Add unit testing and continuous integration frameworks to your packages and set up consistent environments for execution in different installations ensuring the correct version dependencies across packages are maintained.

# 

The best way to learn any programming language is to pick up a problem that has some real-life application. It will be ideal if you can develop the project with an open-source license and let others use it and derive value from it[1](#g395jpsk.html#n4upl4fndot). Julia also is part of many summer internship initiatives like Summer of Code and may help students get an income for their contributions. As you read through this chapter, it may help to think of a problem and design a solution for it. Design your code and packages as discussed in this chapter. While we try to introduce you to some tools and frameworks as examples, it will be overwhelming to provide elaborate details on every tool.

# 

You will be seeing the usage of terms module, package, and project in several of the discussions. While these are related, there are certain specific characteristics each of the terms have.

# 

We have already seen modules in . They represent a namespace in Julia. Modules can be:

*   Defined anywhere in the code. They need not have to be specified at the beginning of the file.
*   The filename does not have to match a module name.
*   One module can be defined inside another. Creating a hierarchical structure.

In the example we discussed in , we have seen all the above characteristics and also realized the need to export a symbol from a module to be used inside another module. However, there are ways to access symbols using the keyword `<strong>using</strong>`.

# 

Any code in Julia can make up a project. There is no specific definition of a project. They are mere collections of Julia or non-Julia files. However, no source code works in isolation; they depend on other well-known libraries for major parts of their functionalities. Those dependencies are captured as part of two metadata files: `<strong>Project.toml</strong>` and `<strong>Manifest.toml</strong>`. This set up is called an `<strong>environment</strong>`. The environment ensures the project is executed with a consistent set of dependent libraries. The constituents of these files we shall look into in some details later.

# 

We discussed about the standard library in . However, if you look into Julia as a language there is no specific definition of a library. Any code or binary written in any language that you can integrate with Julia can be considered as a library. Libraries can be Julia packages, native C/C++ shared objects, Java *.jar* files, or Python packages, etc. Each type of library shall require a different form of integration. For example, standard library is a Julia library that ships with the Julia installation. However, it is not always true for all Julia libraries. `<strong>FileIO</strong>` ships as an external Julia package that one needs to add to her project if she needs to utilize some of its functionalities.

# 

Packages provide a formal structure to a Julia project or library. Here are some characteristics of a package:

*   **Git Repositories**: The Julia packages can be Git repositories. Their deployment mechanism is based on Git library integration with Julia. Hence, once created, the packages can be pushed to GitHub by default.[2](#g395jpsk.html#n4upl4fndou) Packages can be deployed in local directories as well.
*   **Folder Structure**: The packages are organized in a well-defined folder structure: ![](n4upl4fndrp.jpeg)
    
    **Figure 13.1:** Folder structure of package PDFIO
    
    While the `<strong>src</strong>` and `<strong>test</strong>` folders are seen in almost all packages, the folders like `<strong>deps</strong>`, `<strong>docs</strong>` and `<strong>data</strong>`, and so on may be missing in some packages. Similarly, packages that are not public may not have a `<strong>LICENCE.md</strong>` file.
    
*   **Environment**: Packages have their inherent environment metadata files `<strong>Project.toml</strong>` and `<strong>Manifest.toml</strong>`. This ensures when they are deployed, they have a consistent library dependency maintained.
*   **Module**: Packages are wrapped inside the highest level module. That is the name of the package and it is defined in a file named `<strong>&lt;ModuleName&gt;.jl</strong>` inside the `<strong>src</strong>` folder. However, you can have sub-modules defined inside the highest level module as well.

# 

Remember the example of the N-queens problem[3](#g395jpsk.html#n4upl4fndov) we discussed in ? Suppose we will like to place queens on a board and show the visual result. How will we go about it?

1.  **UI Rendering API**: Browsers being the easiest to render we will go to JuliaHub[4](#g395jpsk.html#n4upl4fndow) and search for a few available options. All these are fairly good package options like: `<strong>Electron</strong>`, `<strong>Blink,</strong>` etc. We will suggest `<strong>WebIO</strong>` as that is an aggregator that can render on all the frontends of Blink, Jupyter, a custom window from a Julia REPL or Atom IDE.[5](#g395jpsk.html#n4upl4fndox)
2.  **Adding the package**: Now that you decided to use the WebIO, you can add it to the project by using the command `<strong>add WebIO</strong>`.
3.  **Add the relevant frontend**: If you decide to use Jupyter to render the UI, make sure you add the `<strong>IJulia</strong>` package. If you want to use the Electron-based Blink as a frontend, you will need to add Blink to your project: ![](n4upl4fndrq.jpeg)
    
    **Figure 13.2:** Sample rendering using WebIO and Blink
    

The starter code is given in the folder `<strong>Chapter-13/NQueens</strong>`. Two options are provided one with Jupyter notebook and the other with REPL. You can launch the application in REPL using the commands as follows:

`<strong>julia&gt; cd("Chapter-13/NQueens")</strong>`

`<strong>julia&gt;]</strong>`

`<strong>(@v1.6) pkg&gt; activate .</strong>`

`<strong>(@v1.5) pkg&gt; instantiate</strong>`

``<strong>Activating environment at `Chapter-13\NQueens\Project.toml`</strong>``

`<strong>julia&gt; include("NQueens.jl")</strong>`

For Jupyter notebooks, start `<strong>IJulia</strong>` and open the Jupyter notebook `<strong>Chapter-13/NQueens/NQueens.ipynb</strong>`. Run the notebook to view the rendering on the notebook.

If you open the `<strong>Project.toml</strong>` file, you will see the following:

`<strong>[deps]</strong>`

`<strong>Blink = "ad839575-38b3-5650-b840-f874b8c74a25"</strong>`

`<strong>IJulia = "7073ff75-c697-5162-941a-fcdaad2a7d2a"</strong>`

`<strong>WebIO = "0f1e0344-ec1d-5b48-a673-e5cf874b6c29"</strong>`

These are all the packages your application depends on. However, internally these packages also depend on other packages. If you open the `<strong>Manifest.toml</strong>`, you will be able to see all those packages with versions on which the project effectively depends on. Normally, the `<strong>Project.toml</strong>` is provided to set up the environment. When instantiate command is invoked, it analyzes the `<strong>Project.toml</strong>` and computes all the dependencies and creates a `<strong>Manifest.toml</strong>` if that does not exist. Subsequently, it installs all the needed packages if they are not available. Thus, ensuring the environment is set up to launch the application.

# 

We saw an example of a project where we had a few dependencies already defined and we wanted to replicate the environment in another machine and extend the code to add the user interface. In this example, we shall create a simple package and see how to develop it over its life cycle. For the best experience, we will suggest you use the REPL for executing this section.

# 

Two points are said to be coincident when the distance between them is less than a certain small value called the `<strong>point coincident tolerance</strong>`.[6](#g395jpsk.html#n4upl4fndoy) Given the above condition, how do we know 3 such points are collinear or form a straight line?

![](n4upl4fndrr.jpeg)

**Figure 13.3:** (a) Points AB are the same point if –ε < δ < ε. (b) 3 points ABC are collinear if either AB, BC, or AC are too close to each other. (c) But (b) is not sufficient as shown in B can be very close to the line AC

It is clear from  for ABC to be collinear the triangle area must be very small:

![](n4upl4fndrs.jpeg)

where δ is the height and L is the length of the longest side (BC in our example). If ![](n4upl4fndrt.jpeg)where ϵ is the point coincidence tolerance we know the points are collinear. The triangle area (can be computed using the determinant[7](#g395jpsk.html#n4upl4fndoz):

![](n4upl4fndru.jpeg)

# 

We will call the package `<strong>PointLib</strong>` and initialize it using the following steps:

1.  Change the directory to your work area where you want to create the `<strong>PointLib</strong>` package.
2.  Type the character (\]) on the Julia REPL prompt `<strong>julia&gt;</strong>`. The prompt shall change to `<strong>(@1.6)</strong>` `<strong>pkg&gt;</strong>`. This prompt is called the package mode.
3.  Use the command: `<strong>generate PointLib</strong>`.
4.  A new directory shall be created by the name PointLib with the following files:
    
    `<strong>shell&gt; tree /F<a id="ftn8a" href="#ftn8"><sup>8</sup></a></strong>`
    
    `<strong>Folder PATH listing</strong>`
    
    `<strong>Volume serial number is E285-F8B9</strong>`
    
    `<strong>C:.</strong>`
    
    `<strong>│&nbsp;&nbsp; Project.toml</strong>`
    
    `<strong>└───src</strong>`
    
    `<strong>PointLib.jl</strong>`
    
5.  The `<strong>Project.toml</strong>` will have the following metadata:
    
    `<strong>shell&gt; more Project.toml</strong>`
    
    `<strong>name = "PointLib"</strong>`
    
    `<strong>uuid = "7de1f589-fb91-4994-b265-ccfc43c44ada"</strong>`
    
    `<strong>authors = ["Sambit Kumar Dash &lt;sambitdash@gmail.com&gt;"]</strong>`
    
    `<strong>version = "0.1.0"</strong>`
    
6.  `<strong>src/PointLib.jl</strong>` is the entry point of the code for the package and will contain the following code. A default module matching the name of the package. A greet function as a sample code.
    
    `<strong>module PointLib</strong>`
    
    `<strong>greet() = print("Hello World!")</strong>`
    
    `<strong>end # module</strong>`
    
7.  Use `<strong>cd("PointLib")</strong>` and get inside the folder and use the command “`<strong>]activate</strong>` .”. The dot(.) following activate ensures the environment is activated in the current directory. That will change the prompt to `<strong>(PointLib) pkg&gt;</strong>` confirming the environment defined in the `<strong>PointLib/Project.toml</strong>` is being used.
8.  Add the `<strong>LinearAlgebra</strong>` library to the `<strong>PointLib</strong>` package. This can take some time depending on the registry update.
    
    `<strong>(PointLib) pkg&gt; add LinearAlgebra</strong>`
    
    ``<strong>&nbsp;Updating registry at `D:\Users\sambi\.julia\registries\General`</strong>``
    
    `<strong>Resolving package versions…</strong>`
    
    ``<strong>Updating `C:\Users\sambi\PointLib\Project.toml`</strong>``
    
    `<strong>[37e2e46d] + LinearAlgebra</strong>`
    
    ``<strong>Updating `C:\Users\sambi\PointLib\Manifest.toml`</strong>``
    
    `<strong>[8f399da3] + Libdl</strong>`
    
    `<strong>[37e2e46d] + LinearAlgebra</strong>`
    
    The `<strong>Project.toml</strong>` will have a dependency entry. And a new file `<strong>Manifest.toml</strong>` is created, that resolves the complete list of packages needed. For example, LinearAlgebra requires `<strong>Libdl</strong>` and that information is updated in the `<strong>Manifest.toml</strong>`.
    
    `<strong>shell&gt; more Project.toml</strong>`
    
    `<strong>name = "PointLib"</strong>`
    
    `<strong>uuid = "7de1f589-fb91-4994-b265-ccfc43c44ada"</strong>`
    
    `<strong>authors = ["Sambit Kumar Dash &lt;sambitdash@gmail.com&gt;"]</strong>`
    
    `<strong>version = "0.1.0"</strong>`
    
    `<strong>[deps]</strong>`
    
    `<strong>LinearAlgebra = "37e2e46d-f89d-539d-b4ee-838fcccc9c8e"</strong>`
    
    `<strong>shell&gt; more Manifest.toml</strong>`
    
    `<strong># This file is machine-generated - editing it directly is not advised</strong>`
    
    `<strong>[[Libdl]]</strong>`
    
    `<strong>uuid = "8f399da3-3557-5675-b5ff-fb832c97cbdb"</strong>`
    
    `<strong>[[LinearAlgebra]]</strong>`
    
    `<strong>deps = ["Libdl"]</strong>`
    
    `<strong>uuid = "37e2e46d-f89d-539d-b4ee-838fcccc9c8e"</strong>`
    

Thus we have a package to develop the functionalities we wanted and we can also add it to source control for better maintenance and sharing of our code. Git managed packages can be delivered through Julia package management.

# 

The following code should suffice for the code we will like to develop. While this is a starter code, we will leave it as an exercise for the readers to enhance the functionality with more use cases to add.

`<strong>module PointLib</strong>`

`<strong>greet() = print("Hello World!") # Created by generate command</strong>`

`<strong>using LinearAlgebra</strong>`

`<strong>export Point2D, iscollinear, ϵ</strong>`

`<strong>struct Point2D</strong>`

`<strong>x::Float64</strong>`

`<strong>y::Float64</strong>`

`<strong>end</strong>`

`<strong>function ϵ end</strong>`

`<strong>let _epsilon = 1e-5</strong>`

`<strong>global ϵ() = _epsilon</strong>`

`<strong>end</strong>`

`<strong>function length(pA::Point2D, pB::Point2D)</strong>`

`<strong>x1, y1, x2, y2 = pA.x, pA.y, pB.x, pB.y</strong>`

`<strong>dx, dy = x1 - x2, y1 - y2</strong>`

`<strong>return sqrt(dx*dx+dy*dy)</strong>`

`<strong>end</strong>`

`<strong>∆(pA::Point2D, pB::Point2D, pC::Point2D) =</strong>`

`<strong>0.5*det([pA.x pA.y 1; pB.x pB.y 1; pC.x pC.y 1])</strong>`

`<strong>L(pA::Point2D, pB::Point2D, pC::Point2D) =</strong>`

`<strong>max(length(pA, pB), length(pB, pC), length(pC, pA))</strong>`

`<strong>function iscollinear(pA::Point2D, pB::Point2D, pC::Point2D)</strong>`

`<strong>l = L(pA, pB, pC)</strong>`

`<strong># The longest length is too small if all the points</strong>`

`<strong># are coincident</strong>`

`<strong># This a special case to avoid divide by zero.</strong>`

`<strong>l &lt;= ϵ() &amp;&amp; return true</strong>`

`<strong>return 2∆(pA, pB, pC)/l &lt;= ϵ()</strong>`

`<strong>end</strong>`

`<strong>end # module</strong>`

Updated modules do not get updated once they are loaded. You will need to close the Julia session or use a package like `<strong>Revise.jl</strong>`[9](#g395jpsk.html#n4upl4fndo0) to be able to reload the new symbols inside a package.

# 

Once the program is developed, it is ideal to check-in to a project in a source control. We will suggest a git-based online repository like GitHub be used for this purpose. Please follow the following steps for the same:

1.  Login to GitHub at **[https://www.github.com](https://www.github.com)**
2.  Create a new repository with the name `<strong>PointLib.jl</strong>`. It’s customary to name Julia packages with an extension of `<strong>.jl</strong>`.
3.  You can use the GitHub Desktop to add your folder `<strong>PointLib</strong>` to the repository
    
    or
    
    follow the `<strong>git</strong>` commands below in the folder `<strong>PointLib</strong>`:
    
    `<strong>echo "# PointLib.jl" &gt;&gt; README.md</strong>`
    
    `<strong>git init</strong>`
    
    `<strong>git add .<a id="ftn10a" href="#ftn10"><sup>10</sup></a></strong>`
    
    `<strong>git commit -m "first commit"</strong>`
    
    `<strong># U is the GitHub username<br>git remote add origin https://github.com/U/PointLib.jl.git</strong>`
    
    `<strong>git push -u origin master</strong>`
    

Your final result may look something similar to the project `<strong>sambitdash/PointLib.jl</strong>`[11](#g395jpsk.html#n4upl4fndo1).

# 

No code is good enough unless it is thoroughly tested and the test cases are run frequently to detect regression on new code addition. Julia packages are expected to have unit test cases to address such needs. The test framework can be integrated with the following steps:

1.  Enter the folder `<strong>PointLib</strong>` with `<strong>cd("PointLib")</strong>`.
2.  Now edit the `<strong>Project.toml</strong>` to add the code in bold to add the Test package.
    
    `<strong>name = "PointLib"</strong>`
    
    `<strong>uuid = "7de1f589-fb91-4994-b265-ccfc43c44ada"</strong>`
    
    `<strong>authors = ["Sambit Kumar Dash &lt;sambitdash@gmail.com&gt;"]</strong>`
    
    `<strong>version = "0.1.0"</strong>`
    
    `<strong>[deps]</strong>`
    
    `<strong>LinearAlgebra = "37e2e46d-f89d-539d-b4ee-838fcccc9c8e"</strong>`
    
    `<strong>[extras]</strong>`
    
    `<strong>Test = "8dfed614-e22c-5e08-85e1-65c5234f0b40"</strong>`
    
    `<strong>[targets]</strong>`
    
    `<strong>test = ["Test"]</strong>`
    
3.  `<strong>test/runtests.jl</strong>` contains the test cases for the package. We add the following code to the file:
    
    `<strong>using Test<br>using PointLib</strong>`
    
    `<strong>@test iscollinear(Point2D(0, 0), Point2D(10, 0),<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Point2D(20, 2ϵ()))<br>@test !iscollinear(Point2D(0, 0), Point2D(10, 0),<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Point2D(20, 3ϵ()))<br>@test&nbsp;&nbsp;iscollinear(Point2D(10, 0), Point2D(10, 0),<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Point2D(20, 3ϵ()))</strong>`
    
4.  Now run the test using the command `<strong>]test</strong>` in the package mode.
    
    `<strong>(PointLib) pkg&gt; test</strong>`
    
    `<strong>Testing PointLib</strong>`
    
    ``<strong>Status `C:\Users\sambi\AppData\Local\Temp\jl_quSiap\Project.toml`</strong>``
    
    ``<strong>[7de1f589] PointLib v0.1.0 `C:\Users\sambi\PointLib`</strong>``
    
    `<strong>[37e2e46d] LinearAlgebra</strong>`
    
    `<strong>[8dfed614] Test</strong>`
    
    ``<strong>Status `C:\Users\sambi\AppData\Local\Temp\jl_quSiap\Manifest.toml`</strong>``
    
    ``<strong>[7de1f589] PointLib v0.1.0 `C:\Users\sambi\PointLib`</strong>``
    
    `<strong>[2a0f44e3] Base64</strong>`
    
    `<strong>[8ba89e20] Distributed</strong>`
    
    `<strong>[b77e0a4c] InteractiveUtils</strong>`
    
    `<strong>[8f399da3] Libdl</strong>`
    
    `<strong>[37e2e46d] LinearAlgebra</strong>`
    
    `<strong>[56ddb016] Logging</strong>`
    
    `<strong>[d6f4376e] Markdown</strong>`
    
    `<strong>[9a3f8284] Random</strong>`
    
    `<strong>[9e88b42a] Serialization</strong>`
    
    `<strong>[6462fe0b] Sockets</strong>`
    
    `<strong>[8dfed614] Test</strong>`
    
    `<strong>Testing PointLib tests passed</strong>`
    
5.  When a test fails you may see something like this as an error.
    
    `<strong>Test Failed at C:\Users\sambi\PointLib\test\runtests.jl:5</strong>`
    
    `<strong>Expression: iscollinear(Point2D(0, 0), Point2D(10, 0), Point2D(20, 3 * ϵ()))</strong>`
    
    `<strong>ERROR: LoadError: There was an error during testing</strong>`
    
    `<strong>in expression starting at C:\Users\sambi\PointLib\test\runtests.jl:5</strong>`
    
    `<strong>ERROR: Package PointLib errored during testing</strong>`
    

The `<strong>@test</strong>` expr validates if expr is true. However, there are other commands like `<strong>@test_throws</strong>` that validate a specific exception being raised. A set of tests can be grouped under a test set and aggregated reporting on number of tests passed can be reported. While we used simple test case creation and saw how to trigger them with commands from the REPL, we will need to make sure they are integrated as part of an integrated continuous integration framework. That way whenever there is any push into the GitHub repository there is a continuous integration framework triggered. It ensures the code is built and test is run and results are reported.

# 

Test adequacy is a cause of concern for most software programs and often one of the causes for discontent in engineering departments. Julia test can be invoked with the coverage data generation.

`<strong>(PointLib) pkg&gt; test --coverage</strong>`

`<strong>Testing PointLib</strong>`

``<strong>Status `C:\Users\sambi\AppData\Local\Temp\jl_0MhaZh\Project.toml`</strong>``

``<strong>[7de1f589] PointLib v0.1.0 `C:\Users\sambi\PointLib`</strong>``

`<strong>[37e2e46d] LinearAlgebra</strong>`

`<strong>[8dfed614] Test</strong>`

``<strong>Status `C:\Users\sambi\AppData\Local\Temp\jl_0MhaZh\Manifest.toml`</strong>``

``<strong>[7de1f589] PointLib v0.1.0 `C:\Users\sambi\PointLib`</strong>``

`<strong>[2a0f44e3] Base64</strong>`

`<strong>[8ba89e20] Distributed</strong>`

`<strong>[b77e0a4c] InteractiveUtils</strong>`

`<strong>[8f399da3] Libdl</strong>`

`<strong>[37e2e46d] LinearAlgebra</strong>`

`<strong>[56ddb016] Logging</strong>`

`<strong>[d6f4376e] Markdown</strong>`

`<strong>[9a3f8284] Random</strong>`

`<strong>[9e88b42a] Serialization</strong>`

`<strong>[6462fe0b] Sockets</strong>`

`<strong>[8dfed614] Test</strong>`

`<strong>Testing PointLib tests passed</strong>`

The data can be found for each file in the `<strong>src</strong>` directory. In this case, you will see a file `<strong>src/PointLib.jl.&lt;pid&gt;.cov</strong>`. The file has the complete text of the code with a number indicating the number of times the line was executed as part of the unit test execution. Some of the lines have hyphens indicating they have not been executed.

`<strong>- module PointLib</strong>`

`<strong>-</strong>`

`<strong>- using LinearAlgebra</strong>`

`<strong>-</strong>`

`<strong>- export Point2D, iscollinear, ϵ</strong>`

`<strong>-</strong>`

`<strong>- greet() = print("Hello World!")</strong>`

`<strong>-</strong>`

`<strong>- struct Point2D</strong>`

`<strong>9&nbsp;&nbsp;x::Float64</strong>`

`<strong>-&nbsp;&nbsp;y::Float64</strong>`

`<strong>- end</strong>`

`<strong>-</strong>`

`<strong>- let _epsilon = 1e-5</strong>`

`<strong>9&nbsp;&nbsp;global ϵ() = _epsilon</strong>`

`<strong>- end</strong>`

`<strong>-</strong>`

`<strong>- function length(pA::Point2D, pB::Point2D)</strong>`

`<strong>9&nbsp;&nbsp;x1, y1, x2, y2 = pA.x, pA.y, pB.x, pB.y</strong>`

`<strong>9&nbsp;&nbsp;dx, dy = x1 - x2, y1 - y2</strong>`

`<strong>9&nbsp;&nbsp;return sqrt(dx*dx+dy*dy)</strong>`

`<strong>- end</strong>`

`<strong>-</strong>`

`<strong>3 ∆(pA::Point2D, pB::Point2D, pC::Point2D) =</strong>`

`<strong>-&nbsp;&nbsp;0.5*det([pA.x pA.y 1; pB.x pB.y 1; pC.x pC.y 1])</strong>`

`<strong>-</strong>`

`<strong>3 L(pA::Point2D, pB::Point2D, pC::Point2D) =</strong>`

`<strong>-&nbsp;&nbsp;max(length(pA, pB), length(pB, pC), length(pC, pA))</strong>`

`<strong>-&nbsp;&nbsp;</strong>`

`<strong>- function iscollinear(pA::Point2D, pB::Point2D, pC::Point2D)</strong>`

`<strong>3&nbsp;&nbsp;&nbsp;&nbsp; l = L(pA, pB, pC)</strong>`

`<strong>-&nbsp;&nbsp;# The longest length is too small if all the points are coincident</strong>`

`<strong>-&nbsp;&nbsp;# This a special case to avoid divide by zero.</strong>`

`<strong>3&nbsp;&nbsp;l &lt;= ϵ() &amp;&amp; return true&nbsp;&nbsp;</strong>`

`<strong>3&nbsp;&nbsp;return 2∆(pA, pB, pC)/l &lt;= ϵ()</strong>`

`<strong>- end</strong>`

`<strong>-</strong>`

`<strong>- end # module</strong>`

The report has to be read carefully as a line with function declaration does not get executed and they are not supposed to be. However, the `<strong>greet()</strong>` function has not been executed; clearly showing insufficient test cases.  Visualization on coverage results can be shown using test coverage tools like `<strong>Codecov.io</strong>`, which we shall review in a later section.

# 

Documentation is not truly a function of a package management. However, for a package to be useful to an audience, documentation plays an important role. Hence, we discuss here how documentation can be developed and disseminated for a Julia package. Julia docstrings can be added before any function or type definition as a simple string or a triple quoted block of string. The docstrings can contain markdown syntax for documentation markups like headings, bold, italics or tables, and so on. Let us add a few such docstrings for all the public APIs of the `<strong>PointLib</strong>` package.

`<strong>"Sample module to show how packages are built"</strong>`

`<strong>module PointLib</strong>`

`<strong>…</strong>`

`<strong>"""</strong>`

`<strong>&nbsp;Point2D</strong>`

````<strong>```&nbsp;&nbsp;</strong>````

`<strong>&nbsp;x: Float64 x-cordinates</strong>`

`<strong>&nbsp;y: Float64 y-cordinates</strong>`

````<strong>```</strong>````

`<strong>"""</strong>`

`<strong>struct Point2D</strong>`

`<strong>…</strong>`

`<strong>"Returns the point coincident tolerance value"</strong>`

`<strong>function ϵ end</strong>`

`<strong>…</strong>`

You can test for docstrings by typing the function or type name in the help mode. The REPL switches to help mode as you type the character (?).

`<strong>julia&gt; using PointLib</strong>`

`<strong>help?&gt; Point2D</strong>`

`<strong>search: Point2D pointer PointLib pointer_from_objref codepoint unsafe_pointer_to_objref</strong>`

`<strong>Point2D</strong>`

`<strong>&nbsp;x: Float64 x-coordinates</strong>`

`<strong>&nbsp;y: Float64 y-coordinates</strong>`

`<strong>help?&gt; PointLib</strong>`

`<strong>search: PointLib</strong>`

`<strong>Sample module to show how packages are built</strong>`

While docstrings are useful in looking for help for specific methods and types, you also need elaborate documentation for the whole package. Those are achieved by a package called `<strong>Documenter.jl</strong>`[12](#g395jpsk.html#n4upl4fndo2).

# 

The documentation is created in the folder `<strong>docs</strong>` under the package by convention. In our example:

1.  We shall create a `<strong>PointLib/docs</strong>` folder.
2.  Enter into the folder and launch Julia.
3.  We need to instantiate the project by the command
    
    `<strong>]activate</strong>` . And that will change the package mode prompt to `<strong>(docs) pkg&gt;</strong>`.
    
4.  In the package mode, we need to use the following commands:
    
    `<strong>(docs) pkg&gt; add ..</strong>`
    
    `<strong>(docs) pkg&gt; add Documenter</strong>`
    
    The add `<strong>..</strong>` command shall add the `<strong>PointLib</strong>` package that is not registered in the Julia registry but needed for documentation cross-referencing.
    
5.  In the `<strong>docs</strong>` folder, we shall create a file `<strong>make.jl</strong>` with the following content:
    
    `<strong>if Base.HOME_PROJECT[] !== nothing</strong>`
    
    `<strong># JuliaLang/julia/pull/28625</strong>`
    
    `<strong>Base.HOME_PROJECT[] = abspath(Base.HOME_PROJECT[])</strong>`
    
    `<strong>end</strong>`
    
    `<strong>using Documenter, PointLib</strong>`
    
    `<strong>makedocs(</strong>`
    
    `<strong>format = Documenter.HTML(),</strong>`
    
    `<strong>modules = [PointLib],</strong>`
    
    `<strong>sitename = "PointLib",</strong>`
    
    `<strong>pages = [</strong>`
    
    `<strong>"README.md",</strong>`
    
    `<strong>"API Reference" =&gt; "index.md"</strong>`
    
    `<strong>]</strong>`
    
    `<strong>)</strong>`
    
    `<strong>deploydocs(</strong>`
    
    `<strong>repo&nbsp;&nbsp; = "github.com/sambitdash/PointLib.jl.git",</strong>`
    
    `<strong>)</strong>`
    
6.  The pages referred to in the `<strong>makedocs</strong>` method are looked up in the `<strong>PointLib/docs/src</strong>` directory. This directory must be created by the user. And, the following files should be placed in the `<strong>src</strong>` directory.
7.  The `<strong>README.md</strong>` file contains the standard README of the project.
8.  The `<strong>index.md</strong>` file contains the API References. The relevant docstrings are to be pulled out from the source code and are to be inserted in the reference locations. The index.md contains the code ````<strong>```@docs &lt;methods or types&gt;```</strong>```` where the docstrings are embedded by the build process.
    
    `<strong># Reference</strong>`
    
    `<strong>This page has references to all the exported types and functions.</strong>`
    
    `<strong>## Types</strong>`
    
    ````<strong>```@docs</strong>````
    
    `<strong>Point2D</strong>`
    
    ````<strong>```</strong>````
    
    `<strong>## Functions</strong>`
    
    ````<strong>```@docs</strong>````
    
    `<strong>ϵ</strong>`
    
    `<strong>iscollinear</strong>`
    
    ````<strong>```</strong>````
    
9.  Now, run `<strong>make.jl</strong>` in the docs directory. You will see the documentation in HTML mode in the build directory.
    
    `<strong>julia&gt; include("make.jl")</strong>`
    
    `<strong>[Info: SetupBuildDirectory: setting up build directory.</strong>`
    
    `<strong>[Info: Doctest: running doctests.</strong>`
    
    `<strong>[Info: ExpandTemplates: expanding markdown templates.</strong>`
    
    `<strong>[Info: CrossReferences: building cross-references.</strong>`
    
    `<strong>[Info: CheckDocument: running document checks.</strong>`
    
    `<strong>┌ Warning: 2 docstrings not included in the manual:</strong>`
    
    `<strong>│&nbsp;&nbsp;&nbsp;&nbsp; PointLib.PointLib</strong>`
    
    `<strong>│&nbsp;&nbsp;&nbsp;&nbsp; PointLib.greet :: Tuple{}</strong>`
    
    `<strong>│ These are docstrings in the checked modules (configured with the modules keyword)</strong>`
    
    `<strong>│ that are not included in @docs or @autodocs blocks.</strong>`
    
    `<strong>└ @ Documenter.DocChecks D:\Users\sambi\.julia\packages\Documenter\FuXcO\src\DocChecks.jl:69</strong>`
    
    `<strong>[Info: Populate: populating indices.</strong>`
    
    `<strong>[Info: RenderDocument: rendering document.</strong>`
    
    `<strong>[Info: HTMLWriter: rendering HTML pages.</strong>`
    
    `<strong>┌ Warning: Documenter could not auto-detect the building environment Skipping deployment.</strong>`
    
    `<strong>└ @ Documenter D:\Users\sambi\.julia\packages\Documenter\FuXcO\src\deployconfig.jl:75</strong>`
    
    At the end of the process, we shall see the *Reference API* page populated in the `<strong>build/index.html</strong>` page:
    
    ![](n4upl4fndrv.jpeg)
    
    **Figure 13.4:** Sample API Reference for PointLib
    
    The documentation can be deployed in GitHub pages using a continuous integration tool like GitHub Actions.
    
10.  However, before you proceed, make sure you have added all the source files to the source control. 
     1.  Add a .`<strong>gitignore</strong>` file to your package `<strong>PointLib</strong>` with `<strong>docs/build/*</strong>` in it. This folder is created as documenter output and need not be synced to the source control.
     2.  Run `<strong>git add .</strong>` so that all other source files are added to your repository.
     3.  Now commit your sources using `<strong>git commit</strong>` command or any other GUI tools you are comfortable with.
     4.  Push your changes to the GitHub repository to update it completely.

Now that all your sources are available in the source control, you will like to ensure continuous integration workflows are triggered so that automated testing is carried out along with the creation of the documentation. The documentation must be published on a predefined location as well.

# 

There are many continuous integration platforms available in the market. GitHub Actions are one the most popular frameworks used in the GitHub environments. We shall use GitHub Actions to automate the execution of test, coverage, and documentation creation tasks for the Julia projects.

1.  GitHub Actions reside in a folder called `<strong>.github/workflows</strong>` as yaml files. We shall create a file called `<strong>ci.yml</strong>`[13](#g395jpsk.html#n4upl4fndo3) and study various aspects of the integration framework.
2.  `<strong>Event</strong>`: The first part of the yaml file is an event when the action has to be triggered.
    
    `<strong>name: CI</strong>`
    
    `<strong>on:</strong>`
    
    `<strong>push:</strong>`
    
    `<strong>branches: [master]</strong>`
    
    `<strong>tags: ["*"]</strong>`
    
3.  **Jobs**: Next we specify the jobs that are to be run as part of the action trigger. The ids of the jobs can be any name like myjob. We use test and doc to use two categories of jobs we want to perform.
4.  **Test Jobs**: The test jobs essentially do a lot more than just running the unit tests. They help set up the environment, checkout the code, run the relevant unit tests and submit the coverage results to `<strong>codecov.io</strong>` for visualization.
5.  Setting up the operating environment:
    
    `<strong>jobs:</strong>`
    
    `<strong>test:</strong>`
    
    `<strong>name: Julia ${{matrix.version}} - ${{matrix.os}} - ${{matrix.arch}} - ${{github.event_name}}</strong>`
    
    `<strong>runs-on: ${{matrix.os}}</strong>`
    
    `<strong>strategy:</strong>`
    
    `<strong>fail-fast: false</strong>`
    
    `<strong>matrix:</strong>`
    
    `<strong>version:</strong>`
    
    `<strong>- '1.0'</strong>`
    
    `<strong>- '1' # automatically expands to the latest stable 1.x release of Julia</strong>`
    
    `<strong>- nightly</strong>`
    
    `<strong>os:</strong>`
    
    `<strong>- ubuntu-latest</strong>`
    
    `<strong>arch:</strong>`
    
    `<strong>- x64</strong>`
    
    `<strong>include:</strong>`
    
    `<strong># test macOS and Windows with latest Julia only</strong>`
    
    `<strong>- os: macOS-latest</strong>`
    
    `<strong>arch: x64</strong>`
    
    `<strong>version: 1</strong>`
    
    `<strong>- os: windows-latest</strong>`
    
    `<strong>&nbsp;arch: x64</strong>`
    
    `<strong>version: 1</strong>`
    
    You have the option of specifying the OS versions, Julia versions and you can also specify granular combinations of the Julia version with a specific OS. It may be ideal to pick up a sample `<strong>ci.yml</strong>` and modify it as appropriate than writing from scratch.
    
6.  `<strong>Steps</strong>`: The steps to be executed for a test job are given as follows:
    
    `<strong>steps:</strong>`
    
    `<strong>- uses: actions/checkout@v2</strong>`
    
    `<strong>- uses: julia-actions/setup-julia@v1</strong>`
    
    `<strong>with:</strong>`
    
    `<strong>version: ${{matrix.version}}</strong>`
    
    `<strong>arch: ${{matrix.arch}}</strong>`
    
    `<strong>- uses: actions/cache@v1</strong>`
    
    `<strong>env:</strong>`
    
    `<strong>cache-name: cache-artifacts</strong>`
    
    `<strong>with:</strong>`
    
    `<strong>path: ~/.julia/artifacts</strong>`
    
    `<strong>key: ${{runner.os}}-test-${{env.cache-name}}-${{hashFiles('**/Project.toml')}}</strong>`
    
    `<strong>restore-keys: |</strong>`
    
    `<strong>&nbsp;${{runner.os}}-test-${{env.cache-name}}-</strong>`
    
    `<strong>&nbsp;${{runner.os}}-test-</strong>`
    
    `<strong>&nbsp;${{runner.os}}-</strong>`
    
    `<strong>- uses: julia-actions/julia-buildpkg@v1</strong>`
    
    `<strong>- uses: julia-actions/julia-runtest@v1</strong>`
    
    `<strong>- uses: julia-actions/julia-processcoverage@v1</strong>`
    
    `<strong>- uses: codecov/codecov-action@v1</strong>`
    
    `<strong>with:</strong>`
    
    `<strong>file: lcov.info</strong>`
    
    The steps need not be defined in the steps section. Rather they are picked up from a few predefined scripts developed in the projects GitHub Actions[14](#g395jpsk.html#n4upl4fndo4) and Julia Actions[15](#g395jpsk.html#n4upl4fndo5). This makes the steps declarative.
    
7.  **Documentation Job**: Invokes the makedocs and creates the documentation as part of the doc build process which we have seen earlier.
    
    `<strong>docs:</strong>`
    
    `<strong>name: Documentation</strong>`
    
    `<strong>runs-on: ubuntu-latest</strong>`
    
    `<strong>steps:</strong>`
    
    `<strong>- uses: actions/checkout@v2</strong>`
    
    `<strong>- uses: julia-actions/setup-julia@v1</strong>`
    
    `<strong>with:</strong>`
    
    `<strong>version: '1'</strong>`
    
    `<strong>- run: |</strong>`
    
    `<strong>julia --project=docs -e '</strong>`
    
    `<strong>using Pkg</strong>`
    
    `<strong>Pkg.develop(PackageSpec(path=pwd()))</strong>`
    
    `<strong>Pkg.instantiate()'</strong>`
    
    `<strong>- run: julia --project=docs docs/make.jl</strong>`
    
    `<strong>&nbsp;&nbsp;env:</strong>`
    
    `<strong>GITHUB_TOKEN: ${{secrets.GITHUB_TOKEN}}</strong>`
    
    `<strong>DOCUMENTER_KEY: ${{secrets.DOCUMENTER_KEY}}</strong>`
    
8.  The docs need to show up as GitHub pages after deployment. You will need to create a key pair by using the code as follows[16](#g395jpsk.html#n4upl4fndo6):
    
    `<strong>julia&gt; using DocumenterTools</strong>`
    
    `<strong>julia&gt; DocumenterTools.genkeys()</strong>`
    
    `<strong>[Info: add the public key below to https://github.com/$USER/$REPO/settings/keys with read/write access:</strong>`
    
    `<strong>…</strong>`
    
    `<strong>[Info: add a secure environment variable named 'DOCUMENTER_KEY' to https://travis-ci.com/$USER/$REPO/settings (if you deploy using Travis CI) or https://github.com/$USER/$REPO/settings/secrets (if you deploy using GitHub Actions) with value:</strong>`
    
    `<strong>…</strong>`
    
    You will need to add the public key to the `<strong>keys</strong>` section. You can use DOCUMENTER as the title. Now add private key to the `<strong>secrets</strong>` section of the project settings in GitHub GUI with the name as `<strong>DOCUMENTER_KEY</strong>`.
    
    `<strong>gh-pages Branch:</strong>` GitHub pages are typically populated from a separate branch than the master branch. This is known as the gh-pages branch. The branch is created detached from the master. The commands can be run from the `<strong>PointLib</strong>` directory. Since the code is run to create a detached branch, make sure you have committed all the code changes you have made to the master branch before proceeding.
    
    Here are the commands to manually create a `<strong>gh-pages</strong>` branch[17](#g395jpsk.html#n4upl4fndo7).
    
    `<strong># create gh-pages branch</strong>`
    
    `<strong>git checkout --orphan gh-pages</strong>`
    
    `<strong>git rm -rf .</strong>`
    
    `<strong>touch README.md</strong>`
    
    `<strong>git add README.md</strong>`
    
    `<strong>git commit -m 'initial gh-pages commit'</strong>`
    
    `<strong>git push origin gh-pages</strong>`
    
9.  Configure gh-pages branch with GitHub Pages: In the `<strong>GitHub Pages</strong>` section of PointLib settings page, you can configure the `<strong>gh-pages</strong>` as the source for the webpage: ![](n4upl4fndrw.jpeg)
    
    **Figure 13.5:** GitHub pages configured with gh-pages branch
    
10.  With all the configurations in place, on next push into GitHub repository, the GitHub Actions will be triggered and the outcome of the run can be reported from the `<strong>Actions</strong>` tab of the project. ![](n4upl4fndrx.jpeg)
     
     **Figure 13.6:** Actions tab showing job status and details of each step
     
11.  The final documentation shall be accessible from the location: **https://<USER>.github.io/PointLib.jl/dev/**

# 

Earlier we have seen how coverage data is generated for the test cases. We can see visualizations with tools like `<strong>codecov.io</strong>` and would like to update them at the end of a successful test run.

1.  Go to the settings of `<strong>PointLib.jl</strong>` and mark it as a public package[18](#g395jpsk.html#n4upl4fndo8).
2.  Log-in to **[https://codecov.io](https://codecov.io)** using the GitHub credentials. Make sure your package `<strong>PointLib.jl</strong>` shows up as a listed package in your profile. You will have to set up the codecov for the package if it has not been configured already using the user interface.
3.  Wait for the continuous integration to be triggered and the process to be completed.
4.  If you login to **[https://codecov.io](https://codecov.io)**, you will see the coverage statistics of your code with colorful visualizations: ![](n4upl4fndry.jpeg)
    
    **Figure 13.7:** greet() is not covered while ϵ() is by the test cases. Reported from codecov.io
    

Thus, we generated a package code, created test cases, created relevant documentation. We updated the coverage data to a visualization tool on every test run and deployed the documentation to the `<strong>GitHub Pages</strong>` as part of continuous integrations. This ensures every change in the source code is reflected in proper test case run, ensuring test cases are added for the new functionalities introduced with the help of coverage tools and documentation is kept up-to-date.

# 

When a package is deployed, an optional pre-deployment build step is run to download data files external to the package, executing the build process or placing the built binaries in the right location, and so on. Some of the build steps can be fairly complex; we shall look at a few of the build steps carried out in the package PDFIO as an example[19](#g395jpsk.html#n4upl4fndo9).

*   `<strong>PDFIO</strong>` depends on binary libraries `<strong>zlib</strong>` and `<strong>libcrypto</strong>` from the OpenSSL library.
*   The libraries may be available in the operating system. The names of the libraries can vary based on the OS or distro. Julia provides `<strong>library_dependency</strong>` tools to resolve such issues.
*   The action taken can vary based on the OS. 
    *   `<strong>Windows</strong>`: Prebuilt binaries are downloaded from a specific URL.
    *   `<strong>Non-Windows</strong>`: The libraries are built from the sources and deployed at specific locations so that only PDFIO can utilize them.

The process can be quite complex, yet highly flexible in addressing all possible build and deployment needs[20](#g395jpsk.html#n4upl4fndpa).

However, if you look closely at the line 3 of the `<strong>build.jl</strong>` of `<strong>PDFIO</strong>`, for Julia 1.3 or higher the build step is completely ignored. This is possible as the Julia community now provides pre-built binaries for many well-known binary libraries and wraps them with a package name like: `<strong>&lt;libraryname&gt;_jll</strong>`.

`<strong>PDFIO</strong>` depends on:

*   OpenSLL\_jll
*   Zlib\_jll

These packages are built using a build template generation tool called *BinaryBuilder*.[21](#g395jpsk.html#n4upl4fndpb) If you require pre-built binaries you can be refer to the *JuliaBinaryWrappers*[22](#g395jpsk.html#n4upl4fndpc) organization and look for the repository you are interested in or submit an issue in project `<strong>JuliaPackaging/Yggdrasil</strong>`[23](#g395jpsk.html#n4upl4fndpd). You can also build binary using `<strong>BinaryBuilder</strong>` templates and contribute to the project.

# 

Using a native binary library in Julia requires compatible `<strong>Application Binary Interfaces</strong>` (`<strong>ABI</strong>`) across the Julia and the native library. The commonest binaries have C compatible interfaces that are to be accessed from Julia. Such functions can be called using a keyword `<strong>ccall()</strong>`[24](#g395jpsk.html#n4upl4fndpe).

`<strong>_zlibVersion() = ccall((:zlibVersion, libz), Ptr{Cstring}, ())</strong>`

The library `<strong>libz</strong>` has a method symbol of `<strong>zlibVersion</strong>` that has no input parameters but returns a pointer to a `<strong>Cstring</strong>`. `<strong>Cstring</strong>` is a representation of a C style string which is a byte array.

Alternatively, a function in C can invoke a Julia function as a callback using a macro `<strong>@cfunction</strong>`. Interested readers are suggested to review the manual on Calling C and Fortran Code.[25](#g395jpsk.html#n4upl4fndpf) The calling convention requires the type mappings be set up properly to be able to use objects allocated in Julia in C or vice versa.

`<strong>CXX.jl</strong>`[26](#g395jpsk.html#n4upl4fndpg) can be used to integrate C++ code with Julia. Similarly, `<strong>PyCall.jl</strong>`[27](#g395jpsk.html#n4upl4fndph) provides integration of Python libraries with Julia. `<strong>JavaCall.jl</strong>`[28](#g395jpsk.html#n4upl4fndpi) provides ways to invoke Java code from Julia.

# 

A project environment is controlled by the files `<strong>Project.toml</strong>` and `<strong>Manifest.toml</strong>`. The `<strong>Project.toml</strong>` has the package name, UUID, version, and direct dependencies. Each dependency may further depend on other packages. The dependent packages may have dependency on specific version of a package.

![](n4upl4fndrz.jpeg)

**Figure 13.8:** Package A depends on v1 of B. A depends on F which needs version 3 of B. Hence, v3 of B will be the eventual package that A will use

In the example above, packages are assumed to have perfect forward compatibility. Hence, any higher version of the package can provide all the functionalities of a lower version of the package. It may not be the case always. Sometimes, packages specify a range of versions of a package they are dependent on. In such cases, the most useful or compatible version of the package is to be decided. The `<strong>Project.toml</strong>` of `<strong>A.jl</strong>` will have dependency listing for `<strong>B.jl</strong>`, `<strong>C.jl,</strong>` and `<strong>F.jl</strong>`. However, the `<strong>Manifest.toml</strong>` will be computed after the resolution of specific versions and will have information on `<strong>B.jl v3</strong>`, `<strong>C.jl v1</strong>`, `<strong>D.jl v1</strong>`, `<strong>E.jl v1</strong>`, `<strong>F.jl v2</strong>`. Whenever you need to reproduce an environment, sharing `<strong>Project.toml</strong>` and `<strong>Manifest.toml</strong>` can help. However, in most source-controlled (Git) packages only `<strong>Project.toml</strong>` is checked-in as `<strong>Manifest.toml</strong>` is kept flexible to be updated based on the additional packages in the environment. While we realized that the packages have version information, we have so far not discussed how a package manager is aware of the location of the package. Such information is kept at a central registry.

# 

Packages are core units of delivering functionalities. Once you develop such a package it is natural to advertise it to the external world to be able to access it and use it. The best way to communicate information about your package is to make it available to everyone to use and deliver over a delivery ecosystem. GitHub is a very useful mechanism to achieve the same. Good quality documentation serves as a minimal advertising media. The second part is to make it available through the package registry of Julia. Julia package ecosystem has over 4000 packages. Such packages are mostly Git packages hosted in public Git repositories like GitHub or GitLab. The registered packages are analyzed and made search friendly and documentation is published over JuliaHub for easier access and cloud deployment. Every Julia installation has a local registry that syncs up with the Julia global registry on a periodic basis or on demand when a package update is requested:

![](n4upl4fndr0.jpeg)

**Figure 13.9:** Julia registry in action. The local registry has information about the packages not registered with the global registry. However, it is synced for all the registered packages

Let us assume in the example above, we are developing `<strong>A.jl</strong>` package in a local system. Hence, information regarding `<strong>A.jl</strong>` is currently available only in the local registry. It depends on package `<strong>F.jl</strong>` which is GitHub but not registered with the Julia registry. This is possible when you add a package with the GitHub URL and not the registered package name.

`<strong>(dir) pkg&gt;add https://github.com/user_name/F.jl</strong>`

However, information regarding B, C, D, and E packages are all available in the global cloud registry. The registry has the following information about a package:

1.  Version of the Package
2.  Location of the Package: This can be a Git address with version tags or file system path
3.  Dependency of the package on other packages: The information you normally find in a `<strong>Project.toml</strong>` file.

Location and dependency are stored per version of the package. For example, if you want to modify `<strong>C.jl</strong>` while using it in `<strong>A.jl</strong>`, you will need to make a development copy of the same. This is done using develop or `<strong>dev</strong>` command.

`<strong>(A) pkg&gt; dev C</strong>`

The GitHub repository of `<strong>C.jl</strong>` will be cloned locally into the `<strong>$JULIA_DEPOT_PATH/dev</strong>`. The package manager interacts with the local registry, updates it with the contents of the cloud registry as and when such information needs updating. It also ensures packages are consistent with the environmental requirements of a project. The `<strong>Manifest.toml</strong>` is also generated by the package manager after the dependencies are resolved for a project:

![](n4upl4fndr1.jpeg)

**Figure 13.10:** Julia depot folder structure

`<strong>JULIA_DEPOT_PATH</strong>` is a useful directory where all the packages and information related to them reside. They also have precompiled copies of packages and built binaries. It is by default configured as `<strong>$USER_HOME/.julia</strong>` folder. It must be noted that irrespective of number of project environments, only one depot exists in a Julia installation. The relevant versions of the packages are downloaded as needed by various environments and shared across them. Julia depot or any other files or package related datastructures should not be manipulated directly. Julia provides extensive command line interfaces and APIs to help with such needs.

# 

One can switch to pkg mode of the REPL using the character (\]). Once in pkg mode, you can use `<strong>add</strong>` to add packages to a project, `<strong>rm</strong>` to remove packages from projects. `<strong>update</strong>` command updates the registry and downloads the latest registry from the global server. Like packages, the registry is also a Git repository in Julia. Just like methods and types, help can be requested for a package command by pre-pending a question mark (?). `<strong>?add</strong>` will print the command line help on the REPL.

# 

Although, REPL commands are very helpful for interactive sessions, they may not be entirely helpful in case of scripts or including them in Julia programs. `<strong>Pkg</strong>` module becomes handy in such cases. The methods like `<strong>add()</strong>`, `<strong>rm(),</strong>` etc. provide similar functionalities as command line. Like arguments to the command line, parameters can be provided to the function calls.

Package management in Julia is quite elaborate. However, we have just touched the surface with an overview. The users should get used to packages and learn complex operations as they work with Julia. As many things with Julia package management are implemented using Git, a good knowledge of Git can be very helpful as well.

# 

In this chapter, we started with an understanding of modules, packages, and projects. We extended the 8-queens puzzle to include user interface and graphics. We also created a sample package, developed test cases, documentation and ensured the code coverage was adequate with respect to the test cases. Then we discussed a bit on how Julia package registration works. In short, we have talked about the initial level of details you need to develop production ready Julia applications. In the next chapter, we shall learn to deploy the applications in a cloud environment.

# 

1.  Pick up a real-life problem you will like to solve. Work on the design on how you will like to solve the problem. Do you have all the functionalities in Julia to address the problem? Do you know of any native libraries that solve such a problem? Create your project and start building your solution.
2.  Once you build your solution and bring it to a reasonable shape, register as a package for the Julia ecosystem. Do you really need to register a package for it to be used by others?
3.  Are there enough test cases in the `<strong>PointLib</strong>` package you have developed? How can you extend the test cases? Add a few relevant ones and make sure better use cases are added.
4.  `<strong>iscollinear</strong>` function in `<strong>PointLib</strong>` takes three points as arguments. Is there a way to extend it to N-points where N is greater than 3?
5.  Develop a project that shall utilize the PointLib you already have.

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

[1](#g395jpsk.html#n4upl4fndpj) The author developed a PDF reading library (PDFIO) as his first real-life Julia project. While the first project may have certain limitations and short comings, it gives a perfect opportunity to learn from mistakes and get feedback from community users and contributors.

Dash, Sambit Kumar, PDFIO: PDF Reader Library for native Julia, The Journal of Open Source, Nov. 2019, **[https://doi.org/10.21105%2Fjoss.01453](https://doi.org/10.21105%2Fjoss.01453)**

[2](#g395jpsk.html#n4upl4fndpk) Integration with other Git repositories like GitLab or any private repository also exists.

[3](#g395jpsk.html#n4upl4fndpl) The starter code can be found in the associated directory Chaper-13/NQueens.

[4](#g395jpsk.html#n4upl4fndpm) Packages, JuliaHub, **[https://juliahub.com/ui/Packages](https://juliahub.com/ui/Packages)**. There are some other locations from where Julia packages can be searched as well. **[https://julialang.org/packages/](https://julialang.org/packages/)**

[5](#g395jpsk.html#n4upl4fndpn) VS Code IDE is not supported. **[https://github.com/JuliaGizmos/WebIO.jl/issues/168](https://github.com/JuliaGizmos/WebIO.jl/issues/168)**

[6](#g395jpsk.html#n4upl4fndpo) Floating points are inherently inaccurate. You cannot exactly represent 0.1 in a finite binary system. It will be the infinite series: 0.000110011… This is similar to ⅓ represented as 0.333… in decimal floating-point system. Hence, most floating-point comparisons are carried out within a tolerance range and not for equality. You say a = b when –ε < a-b < ε where, a and b are floating-point numbers. The same is extended here to 2 dimensions in a CAD system.

[7](#g395jpsk.html#n4upl4fndpp) 1 ⁄ 2 *\[(x[A] - x[B]) (y[B] - y[C]) - (x[B] - x[C]) (y[A] - y[B])*\] algebraic expression is normally used. We are using the determinant expression just to add additional modules to the project.

trees command is only available in Windows. For Linux and Mac OS X one can use ls –lR .

[9](#g395jpsk.html#n4upl4fndpq) Revise.jl, GitHub Repository, **[https://github.com/timholy/Revise.jl](https://github.com/timholy/Revise.jl)**

`git add .` will add the whole directory and its contents to the Git repository. If you want to exclude some of the files, please selectively remove those from being synced.

[11](#g395jpsk.html#n4upl4fndpr) `sambitdash/PointLib.jl` is a sample copy of the project for reference. This is not a solution. Readers are expected to develop their own personal repositories and extend. **[https://github.com/sambitdash/PointLib.jl](https://github.com/sambitdash/PointLib.jl)**

[12](#g395jpsk.html#n4upl4fndps) Documenter.jl: A Documentation Generator for Julia, GitHub Repository, **[https://github.com/JuliaDocs/Documenter.jl](https://github.com/JuliaDocs/Documenter.jl)**

[13](#g395jpsk.html#n4upl4fndpt) Rather than writing a ci.yml from scratch, one can look at the one included in the `Example.jl` package at: **[https://github.com/JuliaLang/Example.jl](https://github.com/JuliaLang/Example.jl)**

[14](#g395jpsk.html#n4upl4fndpu) GitHub Actions Scripts, **[https://github.com/actions](https://github.com/actions)**

[15](#g395jpsk.html#n4upl4fndpv) Julia Actions, **[https://github.com/julia-actions](https://github.com/julia-actions)**

[16](#g395jpsk.html#n4upl4fndpw) You can add the package `DocumenterTools` to your package temporarily and remove the package from the package dependencies after generating the key pairs.

[17](#g395jpsk.html#n4upl4fndpx) **[https://gist.github.com/skratchdot/1ef433c666066389201a](https://gist.github.com/skratchdot/1ef433c666066389201a)**

[18](#g395jpsk.html#n4upl4fndpy) Codecov provides integration with GitHub public packages for free. Moreover, there is no need to configure any repository keys for public repositories.

[19](#g395jpsk.html#n4upl4fndpz) The build steps are described in the file `deps/build.jl` and can be invoked with the package mode command `build`. The file can be referred from the link: **[https://github.com/sambitdash/PDFIO.jl/blob/v0.1.12/deps/build.jl](https://github.com/sambitdash/PDFIO.jl/blob/v0.1.12/deps/build.jl)**

[20](#g395jpsk.html#n4upl4fndp0) Advanced users are requested to refer to the `BinDeps` package for more details. **[https://github.com/JuliaPackaging/BinDeps.jl](https://github.com/JuliaPackaging/BinDeps.jl)**

[21](#g395jpsk.html#n4upl4fndp1) BinaryBuilder, GitHub Repository, **[https://github.com/JuliaPackaging/BinaryBuilder.jl](https://github.com/JuliaPackaging/BinaryBuilder.jl)**

[22](#g395jpsk.html#n4upl4fndp2) JuliaBinaryWrappers, GitHub Organization, **[https://github.com/JuliaBinaryWrappers/](https://github.com/JuliaBinaryWrappers/)**

[23](#g395jpsk.html#n4upl4fndp3) Yggdrasil, GitHub Repository, **[https://github.com/JuliaPackaging/Yggdrasil/](https://github.com/JuliaPackaging/Yggdrasil/)**

[24](#g395jpsk.html#n4upl4fndp4) `Inflate.jl`, `PDFIO` GitHub Repository, **[https://github.com/sambitdash/PDFIO.jl/blob/v0.1.12/src/Inflate.jl](https://github.com/sambitdash/PDFIO.jl/blob/v0.1.12/src/Inflate.jl)**

[25](#g395jpsk.html#n4upl4fndp5) Calling C and Fortran Code, Julia Documentation Manuals, **[https://docs.julialang.org/en/v1/manual/calling-c-and-fortran-code/](https://docs.julialang.org/en/v1/manual/calling-c-and-fortran-code/)**

[26](#g395jpsk.html#n4upl4fndp6) `Cxx.jl`, GitHub Repository, **[https://github.com/JuliaInterop/Cxx.jl](https://github.com/JuliaInterop/Cxx.jl)**

[27](#g395jpsk.html#n4upl4fndp7) `PyCall.jl`, GitHub Repository, **[https://github.com/JuliaPy/PyCall.jl](https://github.com/JuliaPy/PyCall.jl)**

[28](#g395jpsk.html#n4upl4fndp8) `JavaCall.jl`, GitHub Repository, **[https://github.com/JuliaInterop/JavaCall.jl](https://github.com/JuliaInterop/JavaCall.jl)**

Revise.jl, GitHub Repository, **[https://github.com/timholy/Revise.jl](https://github.com/timholy/Revise.jl)**

1 ⁄ 2 *\[(x[A] - x[B]) (y[B] - y[C]) - (x[B] - x[C]) (y[A] - y[B])*\] algebraic expression is normally used. We are using the determinant expression just to add additional modules to the project.

The author developed a PDF reading library (PDFIO) as his first real-life Julia project. While the first project may have certain limitations and short comings, it gives a perfect opportunity to learn from mistakes and get feedback from community users and contributors.

Integration with other Git repositories like GitLab or any private repository also exists.

VS Code IDE is not supported. **[https://github.com/JuliaGizmos/WebIO.jl/issues/168](https://github.com/JuliaGizmos/WebIO.jl/issues/168)**

Floating points are inherently inaccurate. You cannot exactly represent 0.1 in a finite binary system. It will be the infinite series: 0.000110011… This is similar to ⅓ represented as 0.333… in decimal floating-point system. Hence, most floating-point comparisons are carried out within a tolerance range and not for equality. You say a = b when –ε < a-b < ε where, a and b are floating-point numbers. The same is extended here to 2 dimensions in a CAD system.

The starter code can be found in the associated directory Chaper-13/NQueens.

Packages, JuliaHub, **[https://juliahub.com/ui/Packages](https://juliahub.com/ui/Packages)**. There are some other locations from where Julia packages can be searched as well. **[https://julialang.org/packages/](https://julialang.org/packages/)**

Using a native binary library in Julia requires compatible `<strong>Application Binary Interfaces</strong>` (`<strong>ABI</strong>`) across the Julia and the native library. The commonest binaries have C compatible interfaces that are to be accessed from Julia. Such functions can be called using a keyword `<strong>ccall()</strong>`24.

While docstrings are useful in looking for help for specific methods and types, you also need elaborate documentation for the whole package. Those are achieved by a package called `<strong>Documenter.jl</strong>`12.

Remember the example of the N-queens problem3 we discussed in ? Suppose we will like to place queens on a board and show the visual result. How will we go about it?

*   GitHub Actions reside in a folder called `<strong>.github/workflows</strong>` as yaml files. We shall create a file called `<strong>ci.yml</strong>`13 and study various aspects of the integration framework. 

Alternatively, a function in C can invoke a Julia function as a callback using a macro `<strong>@cfunction</strong>`. Interested readers are suggested to review the manual on Calling C and Fortran Code.25 The calling convention requires the type mappings be set up properly to be able to use objects allocated in Julia in C or vice versa.

*   **UI Rendering API**: Browsers being the easiest to render we will go to JuliaHub4 and search for a few available options. All these are fairly good package options like: `<strong>Electron</strong>`, `<strong>Blink,</strong>` etc. We will suggest `<strong>WebIO</strong>` as that is an aggregator that can render on all the frontends of Blink, Jupyter, a custom window from a Julia REPL or Atom IDE.5 

These packages are built using a build template generation tool called *BinaryBuilder*.21 If you require pre-built binaries you can be refer to the *JuliaBinaryWrappers*22 organization and look for the repository you are interested in or submit an issue in project `<strong>JuliaPackaging/Yggdrasil</strong>`23. You can also build binary using `<strong>BinaryBuilder</strong>` templates and contribute to the project.

*   **UI Rendering API**: Browsers being the easiest to render we will go to JuliaHub4 and search for a few available options. All these are fairly good package options like: `<strong>Electron</strong>`, `<strong>Blink,</strong>` etc. We will suggest `<strong>WebIO</strong>` as that is an aggregator that can render on all the frontends of Blink, Jupyter, a custom window from a Julia REPL or Atom IDE.5 

Your final result may look something similar to the project `<strong>sambitdash/PointLib.jl</strong>`11.

These packages are built using a build template generation tool called *BinaryBuilder*.21 If you require pre-built binaries you can be refer to the *JuliaBinaryWrappers*22 organization and look for the repository you are interested in or submit an issue in project `<strong>JuliaPackaging/Yggdrasil</strong>`23. You can also build binary using `<strong>BinaryBuilder</strong>` templates and contribute to the project.

Two points are said to be coincident when the distance between them is less than a certain small value called the `<strong>point coincident tolerance</strong>`.6 Given the above condition, how do we know 3 such points are collinear or form a straight line?

The process can be quite complex, yet highly flexible in addressing all possible build and deployment needs20.

where δ is the height and L is the length of the longest side (BC in our example). If ![](n4upl4fndrt.jpeg)where ϵ is the point coincidence tolerance we know the points are collinear. The triangle area (can be computed using the determinant7:

Updated modules do not get updated once they are loaded. You will need to close the Julia session or use a package like `<strong>Revise.jl</strong>`9 to be able to reload the new symbols inside a package.

These packages are built using a build template generation tool called *BinaryBuilder*.21 If you require pre-built binaries you can be refer to the *JuliaBinaryWrappers*22 organization and look for the repository you are interested in or submit an issue in project `<strong>JuliaPackaging/Yggdrasil</strong>`23. You can also build binary using `<strong>BinaryBuilder</strong>` templates and contribute to the project.

*   Go to the settings of `<strong>PointLib.jl</strong>` and mark it as a public package18. 

When a package is deployed, an optional pre-deployment build step is run to download data files external to the package, executing the build process or placing the built binaries in the right location, and so on. Some of the build steps can be fairly complex; we shall look at a few of the build steps carried out in the package PDFIO as an example19.

The build steps are described in the file `deps/build.jl` and can be invoked with the package mode command `build`. The file can be referred from the link: **[https://github.com/sambitdash/PDFIO.jl/blob/v0.1.12/deps/build.jl](https://github.com/sambitdash/PDFIO.jl/blob/v0.1.12/deps/build.jl)**

Codecov provides integration with GitHub public packages for free. Moreover, there is no need to configure any repository keys for public repositories.

**[https://gist.github.com/skratchdot/1ef433c666066389201a](https://gist.github.com/skratchdot/1ef433c666066389201a)**

You can add the package `DocumenterTools` to your package temporarily and remove the package from the package dependencies after generating the key pairs.

Julia Actions, **[https://github.com/julia-actions](https://github.com/julia-actions)**

GitHub Actions Scripts, **[https://github.com/actions](https://github.com/actions)**

Rather than writing a ci.yml from scratch, one can look at the one included in the `Example.jl` package at: **[https://github.com/JuliaLang/Example.jl](https://github.com/JuliaLang/Example.jl)**

Documenter.jl: A Documentation Generator for Julia, GitHub Repository, **[https://github.com/JuliaDocs/Documenter.jl](https://github.com/JuliaDocs/Documenter.jl)**

`sambitdash/PointLib.jl` is a sample copy of the project for reference. This is not a solution. Readers are expected to develop their own personal repositories and extend. **[https://github.com/sambitdash/PointLib.jl](https://github.com/sambitdash/PointLib.jl)**

`<strong>CXX.jl</strong>`26 can be used to integrate C++ code with Julia. Similarly, `<strong>PyCall.jl</strong>`27 provides integration of Python libraries with Julia. `<strong>JavaCall.jl</strong>`28 provides ways to invoke Java code from Julia.

*   The docs need to show up as GitHub pages after deployment. You will need to create a key pair by using the code as follows16: 
    
    `<strong>julia&gt; using DocumenterTools</strong>`
    
    `<strong>julia&gt; DocumenterTools.genkeys()</strong>`
    
    `<strong>[Info: add the public key below to https://github.com/$USER/$REPO/settings/keys with read/write access:</strong>`
    
    `<strong>…</strong>`
    
    `<strong>[Info: add a secure environment variable named 'DOCUMENTER_KEY' to https://travis-ci.com/$USER/$REPO/settings (if you deploy using Travis CI) or https://github.com/$USER/$REPO/settings/secrets (if you deploy using GitHub Actions) with value:</strong>`
    
    `<strong>…</strong>`
    
    You will need to add the public key to the `<strong>keys</strong>` section. You can use DOCUMENTER as the title. Now add private key to the `<strong>secrets</strong>` section of the project settings in GitHub GUI with the name as `<strong>DOCUMENTER_KEY</strong>`.
    
    `<strong>gh-pages Branch:</strong>` GitHub pages are typically populated from a separate branch than the master branch. This is known as the gh-pages branch. The branch is created detached from the master. The commands can be run from the `<strong>PointLib</strong>` directory. Since the code is run to create a detached branch, make sure you have committed all the code changes you have made to the master branch before proceeding.
    
    Here are the commands to manually create a `<strong>gh-pages</strong>` branch17.
    
    `<strong># create gh-pages branch</strong>`
    
    `<strong>git checkout --orphan gh-pages</strong>`
    
    `<strong>git rm -rf .</strong>`
    
    `<strong>touch README.md</strong>`
    
    `<strong>git add README.md</strong>`
    
    `<strong>git commit -m 'initial gh-pages commit'</strong>`
    
    `<strong>git push origin gh-pages</strong>`
    

`JavaCall.jl`, GitHub Repository, **[https://github.com/JuliaInterop/JavaCall.jl](https://github.com/JuliaInterop/JavaCall.jl)**

`PyCall.jl`, GitHub Repository, **[https://github.com/JuliaPy/PyCall.jl](https://github.com/JuliaPy/PyCall.jl)**

`Cxx.jl`, GitHub Repository, **[https://github.com/JuliaInterop/Cxx.jl](https://github.com/JuliaInterop/Cxx.jl)**

Calling C and Fortran Code, Julia Documentation Manuals, **[https://docs.julialang.org/en/v1/manual/calling-c-and-fortran-code/](https://docs.julialang.org/en/v1/manual/calling-c-and-fortran-code/)**

`Inflate.jl`, `PDFIO` GitHub Repository, **[https://github.com/sambitdash/PDFIO.jl/blob/v0.1.12/src/Inflate.jl](https://github.com/sambitdash/PDFIO.jl/blob/v0.1.12/src/Inflate.jl)**

Yggdrasil, GitHub Repository, **[https://github.com/JuliaPackaging/Yggdrasil/](https://github.com/JuliaPackaging/Yggdrasil/)**

JuliaBinaryWrappers, GitHub Organization, **[https://github.com/JuliaBinaryWrappers/](https://github.com/JuliaBinaryWrappers/)**

BinaryBuilder, GitHub Repository, **[https://github.com/JuliaPackaging/BinaryBuilder.jl](https://github.com/JuliaPackaging/BinaryBuilder.jl)**

Advanced users are requested to refer to the `BinDeps` package for more details. **[https://github.com/JuliaPackaging/BinDeps.jl](https://github.com/JuliaPackaging/BinDeps.jl)**

Here are the commands to manually create a `<strong>gh-pages</strong>` branch17.

`<strong>CXX.jl</strong>`26 can be used to integrate C++ code with Julia. Similarly, `<strong>PyCall.jl</strong>`27 provides integration of Python libraries with Julia. `<strong>JavaCall.jl</strong>`28 provides ways to invoke Java code from Julia.

The steps need not be defined in the steps section. Rather they are picked up from a few predefined scripts developed in the projects GitHub Actions14 and Julia Actions15. This makes the steps declarative.

The best way to learn any programming language is to pick up a problem that has some real-life application. It will be ideal if you can develop the project with an open-source license and let others use it and derive value from it1. Julia also is part of many summer internship initiatives like Summer of Code and may help students get an income for their contributions. As you read through this chapter, it may help to think of a problem and design a solution for it. Design your code and packages as discussed in this chapter. While we try to introduce you to some tools and frameworks as examples, it will be overwhelming to provide elaborate details on every tool.

The steps need not be defined in the steps section. Rather they are picked up from a few predefined scripts developed in the projects GitHub Actions14 and Julia Actions15. This makes the steps declarative.

`<strong>CXX.jl</strong>`26 can be used to integrate C++ code with Julia. Similarly, `<strong>PyCall.jl</strong>`27 provides integration of Python libraries with Julia. `<strong>JavaCall.jl</strong>`28 provides ways to invoke Java code from Julia.

*   **Git Repositories**: The Julia packages can be Git repositories. Their deployment mechanism is based on Git library integration with Julia. Hence, once created, the packages can be pushed to GitHub by default.2 Packages can be deployed in local directories as well. 

# 

# 

We have understood the tools used to develop Julia applications. We shall now deploy our applications in the cloud environments. Julia is preferred for server-based computing and the cloud is a natural choice of deployment for such systems.

# 

In this chapter, we will learn the following topics:

*   Cloud environments
*   Deploying Julia
*   Kubernetes
*   Public cloud infrastructures

# 

You shall get a fair idea of deploying Julia applications as web services in Docker containers, and then also carry the containers over to a Kubernetes service for deployment and orchestration using Julia commands. You can also manage *AWS*, *Azure*, and *Google Cloud* services using Julia commands as an integrated platform. Thus, you can use Julia as a client interface for many of the cloud deployment activities.

# 

Julia is an environment designed for scientific computations. It is extensively used for server-based computing. Hence, many production Julia deployments are carried out in cloud environments. Cloud environments have their own unique challenges. Julia as a language does not restrict itself to any specific cloud platform. However, the levels of integration with cloud providers are continuously evolving and are of differing capabilities at any point of time. Julia computing provides a *JuliaHub* environment that integrates closely with the Julia Development environment. We have seen the integrations with VS Code IDE earlier. An elaborate tutorial[1](#7aua230v.html#n4upl4fndi5) is provided through which a workload can be deployed into the *JuliaHub* and run as a distributed application.

*JuliaHub* provides user interfaces to search and discover packages and also allows one to develop and register own packages. Packages can be structured and registered as applications, which essentially means adding the main method and specifying the environment, which then can be run multiple times or shared with other users of *JuliaHub*. *JuliaHub* also provides enterprise plans where one can have private registries and packages and also have tighter control of packages to match corporate policies. Distributed applications can be scaled on demand and on the push of a button from a single node to hundreds of nodes. *JuliaHub* can be a good option for someone using a Julia only environment. But for disparate applications, large infrastructures, or even for pure business reasons, one may prefer other well-known IaaS or PaaS solutions.

The *JuliaHub* interface is simple and needs a bare minimum set of resource configurations as shown in the following screenshot:

![](n4upl4fndql.jpeg)

**Figure 14.1:** JuliaHub provides a simple distributed environment with configurable amounts of CPUs and memory

Behind the scenes, *JuliaHub* manages log monitoring, scheduling, and distributed processing in a transparent manner. This reduces significant management and deployment overheads from complex systems. The readers are advised to refer to the documentation[2](#7aua230v.html#n4upl4fndi6) for an elaborate understanding of *JuliaHub*.

# 

If you look at the GitHub actions for any of the Julia packages, you will realize the following high-level steps are being followed in most of them:

1.  **Install Julia**: Based on the platform and operating system, the right binary needs to be downloaded and installed.
2.  **Set up Julia**: The installation needs to be configured in the paths so that it can be used by all users of interest.
3.  Checkout the packages to be tested.
4.  **Instantiate the package environment**: This may install all the dependent packages needed to run the application.
5.  Launch the environment and test the package.

While most of these can be achieved with custom scripts, it may not be desirable considering the repetitive nature of the work and the wide variety of deployment platforms on which these are to be carried out. Docker-based packages are considered the de-facto standards of deployment delivery. However, maintaining such images yourself can be hard. Custom package management reference implementation of Julia, `<strong>PkgServer</strong>`[3](#7aua230v.html#n4upl4fndi7) is a good package to understand the usage of Docker scripts to deploy complete server configurations. In the examples below, we shall look at much simpler examples and expose the `<strong>NQueens</strong>` problem as a service.

# 

Julia is a preferred environment for server-based computations. It will be ideal if Julia methods can be exposed as REST endpoints that can be accessed from a browser or a normal HTTP client. We will pick up the N-queens problem from  and try to deploy the computational elements as a server while we render the client locally as would be a typical deployment. `<strong>JuliaWebAPI</strong>`[4](#7aua230v.html#n4upl4fndi8) provides the perfect interface to expose APIs as a web interface.

`<strong>…</strong>`

`<strong>webqueens(N)=queens(parse(Int, N))</strong>`

`<strong>process(</strong>`

`<strong>JuliaWebAPI.create_responder([</strong>`

`<strong>(webqueens, true)</strong>`

`<strong>], "tcp://127.0.0.1:9999", true, ""), async=true</strong>`

`<strong>)</strong>`

`<strong>const apiclnt = APIInvoker("tcp://127.0.0.1:9999")</strong>`

`<strong>run_http(apiclnt, 8888)</strong>`

This is only the relevant piece of code[5](#7aua230v.html#n4upl4fndi9) for you to expose the `<strong>queens(N)</strong>` function from . Let us look into it in detail:

*   The server application listens to HTTP requests on the port 8888.
*   When it receives a valid REST request, it invokes with the `<strong>APIInvoker</strong>` with JMQ transport and JSON format.
*   The `<strong>APIResponder</strong>` running on port 9999 responds after launching the relevant function and converting the return values to a JSON format.

The client shall connect to the REST endpoint and get the positions of the queens and render it on the canvas. The relevant portions of the client code are shown as follows:

`<strong>using HTTP</strong>`

`<strong>using JSON</strong>`

`<strong>using Blink</strong>`

`<strong>using WebIO</strong>`

`<strong>try</strong>`

`<strong>N, W = 8, 30</strong>`

`<strong>resp = HTTP.get("http://172.17.0.2:8888/webqueens/$N")</strong>`

`<strong>json = JSON.parse(String(resp.body))</strong>`

`<strong>allqueens = json["data"]</strong>`

`<strong>w = Window()</strong>`

`<strong>…</strong>`

`<strong>### Code to update the canvas<a id="ftn6a" href="#ftn6"><sup>6</sup></a></strong>`

`<strong>catch e</strong>`

`<strong>return "Error occurred : $e"</strong>`

`<strong>end</strong>`

# 

Docker has become the de-facto standard for container management for both private as well as public cloud infrastructures. Julia already has registered Docker images with different base images on Docker Hub[7](#7aua230v.html#n4upl4fndja) and can be pulled using the following command:

`<strong>$docker pull julia</strong>`

Additional packages needed, can be updated in the configuration file called `<strong>Dockerfile</strong>`. We shall now deploy the server code into the Docker container. The sample DockerFile is shown here:

`<strong>FROM julia:latest</strong>`

`<strong>COPY Project.toml server.jl nqueens/</strong>`

`<strong>WORKDIR nqueens</strong>`

`<strong>RUN julia -e "using Pkg; pkg\"activate .\"; pkg\"instantiate\"; "</strong>`

`<strong>CMD julia server.jl</strong>`

Let us discuss the preceding lines of code:

1.  We take up the base Julia Docker container.
2.  Copy the `<strong>Project.toml</strong>` and `<strong>server.jl</strong>` to the work directory.
3.  We update the container using the Julia package management.
4.  Lastly, we set the command to be launched when the container is run.

You can build the Docker image using the command:

`<strong>$sudo docker build –t queens.</strong>`

The container can be launched using `<strong>docker run queens</strong>`. You can use the same client as earlier but make sure to change the IP address of the server to the IP address of the Docker container[8](#7aua230v.html#n4upl4fndjb). The `<strong>SimpleContainerGenerator</strong>`[9](#7aua230v.html#n4upl4fndjc) package helps to build the DockerFile configurations based on certain metadata.

# 

While Docker is the de-facto standard for container management, Kubernetes is the most commonly supported orchestration platform for cloud deployment. Cloud Native Computing Foundation certifies[10](#7aua230v.html#n4upl4fndjd) over 90 Kubernetes supported platforms for API compliance. Some of the notable offerings are as follows:

*   **Elastic Kubernetes Services** (**EKS**) by Amazon Web Services
*   **Azure Kubernetes Services** (**AKS**) by Microsoft Azure
*   **Google Kubernetes Engine** (**GKE**) by Google

So, Julia containers created using Docker can be orchestrated in almost all the well-known cloud platforms using Kubernetes. The Kuber[11](#7aua230v.html#n4upl4fndje) package provides Julia APIs to manage a Kubernetes orchestrated environment. A tutorial on orchestrating containers using Kuber on an Azure AKS[12](#7aua230v.html#n4upl4fndjf) is already available. The tutorial provides the methods to create new nodes, launch them and provides the steps to delete and clear the resources. The metrics for various Kubernetes nodes and pods can be queried from Julia as well. We shall try to deploy the container we created earlier into the **Azure Kubernetes Service** (**AKS**), using the following steps:

We will need to install the Azure **Command Line Interface** (**CLI**). This is available for Windows, Mac OS X, and Linux as well.

1.  Login into the Azure environment using the admin login and the following command:
    
    `<strong>$ az login</strong>`
    
2.  Create a Resource Group in Azure Portal by using the following command:
    
    `<strong>az group create --name HOJP --location centralindia</strong>`
    
    You could use the portal to do the same as well.
    
3.  Create a Kubernetes Cluster in the HOJP resource group, as follows:
    
    `<strong>$ az aks create --resource-group HOJP --name hojpcluster --node-count 1 --enable-addons monitoring --generate-ssh-keys</strong>`
    
    For this experimental cluster, we use only one node.
    
4.  We need to cache the credentials for the future use using the following command:
    
    `<strong>$&nbsp;&nbsp;az aks get-credentials --resource-group HOJP --name hojpcluster</strong>`
    
5.  Moreover, we need the AKS client for certain operations and must install it using the following command:
    
    `<strong>$ sudo az aks install-cli</strong>`
    
    You shall be able to use kubectl for many of the Kubernetes commands.
    
6.  `<strong>kubectl proxy</strong>` is useful for connecting to the Azure Kubernetes services through web services.
7.  You will need to install the Docker containers into the AKS. The images must reside in the AKS environment and must be registered in the Azure container registry so that they can be pulled into containers. You can do so by using the following command:
    
    `<strong>$ az acr create -n hojpreg -g HOJP --sku Standard</strong>`
    
8.  The registry may require authentication for pushing and pulling images from it. One way one can provide Azure admins access to the registry is by attaching the registry to the cluster. But this is not advisable for a real production Azure deployment.
    
    `<strong>$ az aks update -n hojpcluster -g HOJP --attach-acr hojpreg</strong>`
    
9.  Now you can create the Docker image and push it to the Azure container registry by using the commands as shown here:
    
    `<strong>$ docker build . -f Dockerfile -t hojpreg.azurecr.io/kubqueens</strong>`
    
    `<strong>$ docker push hojpreg.azurecr.io/kubqueens</strong>`
    
    This may take some time considering the network connection you have. The images can be a few hundred megabytes in size.
    

# 

Now that the images are registered in the AKS registry, we shall use the Kuber[13](#7aua230v.html#n4upl4fndjg) package and deploy the services, as follows:

1.  Start a context that connects with AKS using the proxy:
    
    `<strong>using Kuber</strong>`
    
    `<strong>ctx = Kuber.KuberContext()</strong>`
    
2.  A pod that is served by one or more containers is taken from the kubqueens image, as follows:
    
    `<strong>kubqueens_pod = kuber_obj(ctx, """{</strong>`
    
    `<strong>"kind": "Pod",</strong>`
    
    `<strong>"metadata":{</strong>`
    
    `<strong>"name": "kubqueens-pod",</strong>`
    
    `<strong>"namespace": "default",</strong>`
    
    `<strong>"labels": {</strong>`
    
    `<strong>"name": "kubqueens-pod"</strong>`
    
    `<strong>}</strong>`
    
    `<strong>},</strong>`
    
    `<strong>"spec": {</strong>`
    
    `<strong>"containers": [{</strong>`
    
    `<strong>"name": "kubqueens",</strong>`
    
    `<strong>"image": "hojpreg.azurecr.io/kubqueens",</strong>`
    
    `<strong>"ports": [{"containerPort": 8888}]</strong>`
    
    `<strong>}]</strong>`
    
    `<strong>}</strong>`
    
    `<strong>}""")</strong>`
    
3.  Create a load balancer service such that the containers can be exposed with a public URL.
    
    `<strong>kubqueens_service = kuber_obj(ctx, """{</strong>`
    
    `<strong>"kind": "Service",</strong>`
    
    `<strong>"metadata": {</strong>`
    
    `<strong>"name": "kubqueens-service",</strong>`
    
    `<strong>"namespace": "default",</strong>`
    
    `<strong>"labels": {"name": "kubqueens-service"}</strong>`
    
    `<strong>},</strong>`
    
    `<strong>"spec": {</strong>`
    
    `<strong>"type": "LoadBalancer",</strong>`
    
    `<strong>"ports": [{"port": 8888}],</strong>`
    
    `<strong>"selector": {"name": "kubqueens-pod"}</strong>`
    
    `<strong>}</strong>`
    
    `<strong>}""")</strong>`
    
4.  Both the objects must be attached to the context to make deploy them to the AKS cluster, as follows:
    
    `<strong>put!(ctx, kubqueens_pod);</strong>`
    
    `<strong>put!(ctx, kubqueens_service);</strong>`
    
5.  Now wait for the load balancer to come up:
    
    `<strong>while true</strong>`
    
    `<strong>println("waiting for loadbalancer to be configured…")</strong>`
    
    `<strong>status = get(ctx, :Service, "kubqueens-service").status</strong>`
    
    `<strong>if nothing !== status.loadBalancer.ingress &amp;&amp;<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;!isempty(status.loadBalancer.ingress)</strong>`
    
    `<strong>println(status.loadBalancer.ingress[1])</strong>`
    
    `<strong>break</strong>`
    
    `<strong>end</strong>`
    
    `<strong>sleep(5)</strong>`
    
    `<strong>end</strong>`
    
6.  We can access the AKS deployed service by accessing the REST end point with the public IP address, as follows:
    
    `<strong>C:\&gt;curl http://&lt;public_IP&gt;:8888/webqueens/8</strong>`
    
    `<strong>{"data":[4,2,7,3,6,8,5,1],"code":0}</strong>`
    
    You can also use the client code mentioned earlier to connect to the AKS and render the UI. The complete Kubernetes orchestrator code can be seen in C`<strong>hapter-14/kubernetes/kubserver.jl</strong>`. The services can be removed easily by calling the delete! Method, as follows:
    
    `<strong>delete!(ctx, kubqueens_service)</strong>`
    
    `<strong>delete!(ctx, kubqueens_pod)</strong>`
    

# 

Amazon Web Services, Microsoft Azure, and Google Cloud Platforms are almost the default public cloud infrastructures available today. Julia packages can connect to all of these platforms and provide service management APIs. In most cases, they are generated using the web services architectures of these platforms, and thus can be extended to adopt to the newer APIs as they are developed.

# 

While we can orchestrate workloads using the Kubernetes, native platforms provide granular controls and the ability to use across a larger stack of services. They are not confined to container-based workloads only. Julia provides an extensive coverage of managing AWS-based services using the package AWS[14](#7aua230v.html#n4upl4fndjh). AWS is by far the most comprehensive integration among all the public cloud infrastructures for Julia. A large part of this is due to the automated code generation using a *GitHub* action, which is executed every day at 6:00am UTC. It queries the *GitHub* repository `<strong>aws-sdk-js</strong>` repository[15](#7aua230v.html#n4upl4fndji) for the REST-based APIs. This action generates the wrapper functions for AWS services in Julia. The documentation is also pulled from the AWS documentation and presented as Juliadocs. This ensures the sources can accommodate all the changes to the AWS APIs and documentations. The APIs are generally designed as two categories:

*   Lower-level APIs
*   High-level APIs

Lower-level APIs query the AWS as URLs and commands like GET or POST. High-level APIs are function calls. Whenever Julia functions are generated for AWS functions, camel case names of functions are modified to lower case, and words are separated by an underscore (\_). For example, the `<strong>S3</strong>` function call `<strong>ListObjectsV2</strong>` shall become `<strong>list_objects_v2</strong>`.

# 

Just like AWS, the Azure[16](#7aua230v.html#n4upl4fndjj) package provides connectivity to Azure cloud infrastructure from a Julia client. The client has a very similar architecture as AWS. It uses Swagger Java Library to generate the Julia signatures for the REST APIs exposed by the Azure framework. Unlike AWS, Julia signatures for Azure APIs are generated intermittently and are not part of an automated GitHub Action. We suggest the reader to explore the APIs and use them for their Azure management needs.

# 

*GoogleCloud*[17](#7aua230v.html#n4upl4fndjk) provides connectivity to the `<strong>Google Clouds Platform</strong>` (`<strong>GCP</strong>`). It wraps the Google JSON APIs and provides a lightweight framework to invoke the GCP APIs. Just like AWS and Azure, this provides connectivity to the GCP using the web services connectivity frameworks.

# 

We looked at the JuliaHub, a simple yet ideal environment for Julia programs to utilize a parallel execution environment for native Julia applications. Subsequently, we created docker containers to deploy Julia services. Those docker containers can be deployed in a Kubernetes environment using a Julia client and orchestrated using the Kubernetes APIs. Lastly, we discussed about the Julia clients that connect to the native public cloud platforms like AWS, Azure, and GCP. Cloud environments are diverse and vast. They can be extremely complex. While we just scratched the surface here, we expect the reader to deep dive into the specific area he/she focuses in and use Julia to the fullest extent possible. With this we come to the end of the second module, in the subsequent module we shall review a few of the libraries used in data analysis, text analysis, and deep learning.

# 

1.  Launch the JuliaHub tutorial in distributed mode using multiple workloads. Estimate the time taken in computing the value of π.
2.  In the last chapter, we created an application to solve the point co-linearity problem. Now create a Docker container that can be deployed in another machine.
3.  Use the tutorial on Kuber to orchestrate workloads on Kubernetes platform of your choice.
4.  Use the Julia AWS to launch any AWS service and use it in your application.
5.  Are there any connectors for Azure and Google Cloud?

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

[1](#7aua230v.html#n4upl4fndjl) Running a JuliaHub job script from your local Julia IDE, **[https://docs.juliahub.com/run\_tutorials/basics/](https://docs.juliahub.com/run_tutorials/basics/)**

[2](#7aua230v.html#n4upl4fndjm) JuliaHub, **[https://docs.juliahub.com/](https://docs.juliahub.com/)**

[3](#7aua230v.html#n4upl4fndjn) PkgServer, **[https://github.com/JuliaPackaging/PkgServer.jl](https://github.com/JuliaPackaging/PkgServer.jl)**

[4](#7aua230v.html#n4upl4fndjo) JuliaWebAPI, Julia package for deploying APIs, **[https://github.com/JuliaWeb/JuliaWebAPI.jl](https://github.com/JuliaWeb/JuliaWebAPI.jl)**

[5](#7aua230v.html#n4upl4fndjp) The complete code is available at Chapter-14/server/server.jl

The complete code is available at Chapter-14/client/client.jl

[7](#7aua230v.html#n4upl4fndjq) Docker Hub, **[https://hub.docker.com/](https://hub.docker.com/)**

[8](#7aua230v.html#n4upl4fndjr) `<strong>docker network ls</strong>` and `<strong>docker network inspect</strong>` can be utilized to find the container IP address.

[9](#7aua230v.html#n4upl4fndjs) SimpleContainerGenerator, create container images for using Julia packages (especially useful in environments without Internet access), **[https://github.com/bcbi/SimpleContainerGenerator.jl](https://github.com/bcbi/SimpleContainerGenerator.jl)**

[10](#7aua230v.html#n4upl4fndjt) Software Conformance (Certified Kubernetes), Cloud Native Computing Foundation, **[https://www.cncf.io/certification/software-conformance/](https://www.cncf.io/certification/software-conformance/)**

[11](#7aua230v.html#n4upl4fndju) Kuber, Julia Kubernetes Client, **[https://github.com/JuliaComputing/Kuber.jl](https://github.com/JuliaComputing/Kuber.jl)**

[12](#7aua230v.html#n4upl4fndjv) Tanmay Mohapatra, Kubernetes in Julia with Kuber.jl, **[https://juliacomputing.com/blog/2018/12/kuber/](https://juliacomputing.com/blog/2018/12/kuber/)**

[13](#7aua230v.html#n4upl4fndjw) Kuber.jl, Julia Kubernetes Client, **[https://github.com/JuliaComputing/Kuber.jl](https://github.com/JuliaComputing/Kuber.jl)**

[14](#7aua230v.html#n4upl4fndjx) AWS, Julia interface to AWS, **[https://github.com/JuliaCloud/AWS.jl](https://github.com/JuliaCloud/AWS.jl)**

[15](#7aua230v.html#n4upl4fndjy) aws-sdk-js, AWS SDK for JavaScript in the browser and Node.js, **[https://github.com/aws/aws-sdk-js](https://github.com/aws/aws-sdk-js)**

[16](#7aua230v.html#n4upl4fndjz) Azure, Julia interface to Azure API, **[https://github.com/JuliaComputing/Azure.jl](https://github.com/JuliaComputing/Azure.jl)**

[17](#7aua230v.html#n4upl4fndj0) GoogleCloud, Google Cloud APIs for Julia, **[https://github.com/JuliaCloud/GoogleCloud.jl](https://github.com/JuliaCloud/GoogleCloud.jl)**

The container can be launched using `<strong>docker run queens</strong>`. You can use the same client as earlier but make sure to change the IP address of the server to the IP address of the Docker container8. The `<strong>SimpleContainerGenerator</strong>`9 package helps to build the DockerFile configurations based on certain metadata.

SimpleContainerGenerator, create container images for using Julia packages (especially useful in environments without Internet access), **[https://github.com/bcbi/SimpleContainerGenerator.jl](https://github.com/bcbi/SimpleContainerGenerator.jl)**

`<strong>docker network ls</strong>` and `<strong>docker network inspect</strong>` can be utilized to find the container IP address.

Docker has become the de-facto standard for container management for both private as well as public cloud infrastructures. Julia already has registered Docker images with different base images on Docker Hub7 and can be pulled using the following command:

PkgServer, **[https://github.com/JuliaPackaging/PkgServer.jl](https://github.com/JuliaPackaging/PkgServer.jl)**

JuliaHub, **[https://docs.juliahub.com/](https://docs.juliahub.com/)**

Running a JuliaHub job script from your local Julia IDE, **[https://docs.juliahub.com/run\_tutorials/basics/](https://docs.juliahub.com/run_tutorials/basics/)**

The container can be launched using `<strong>docker run queens</strong>`. You can use the same client as earlier but make sure to change the IP address of the server to the IP address of the Docker container8. The `<strong>SimpleContainerGenerator</strong>`9 package helps to build the DockerFile configurations based on certain metadata.

Docker Hub, **[https://hub.docker.com/](https://hub.docker.com/)**

The complete code is available at Chapter-14/server/server.jl

JuliaWebAPI, Julia package for deploying APIs, **[https://github.com/JuliaWeb/JuliaWebAPI.jl](https://github.com/JuliaWeb/JuliaWebAPI.jl)**

Julia is a preferred environment for server-based computations. It will be ideal if Julia methods can be exposed as REST endpoints that can be accessed from a browser or a normal HTTP client. We will pick up the N-queens problem from  and try to deploy the computational elements as a server while we render the client locally as would be a typical deployment. `<strong>JuliaWebAPI</strong>`4 provides the perfect interface to expose APIs as a web interface.

While we can orchestrate workloads using the Kubernetes, native platforms provide granular controls and the ability to use across a larger stack of services. They are not confined to container-based workloads only. Julia provides an extensive coverage of managing AWS-based services using the package AWS14. AWS is by far the most comprehensive integration among all the public cloud infrastructures for Julia. A large part of this is due to the automated code generation using a *GitHub* action, which is executed every day at 6:00am UTC. It queries the *GitHub* repository `<strong>aws-sdk-js</strong>` repository15 for the REST-based APIs. This action generates the wrapper functions for AWS services in Julia. The documentation is also pulled from the AWS documentation and presented as Juliadocs. This ensures the sources can accommodate all the changes to the AWS APIs and documentations. The APIs are generally designed as two categories:

While most of these can be achieved with custom scripts, it may not be desirable considering the repetitive nature of the work and the wide variety of deployment platforms on which these are to be carried out. Docker-based packages are considered the de-facto standards of deployment delivery. However, maintaining such images yourself can be hard. Custom package management reference implementation of Julia, `<strong>PkgServer</strong>`3 is a good package to understand the usage of Docker scripts to deploy complete server configurations. In the examples below, we shall look at much simpler examples and expose the `<strong>NQueens</strong>` problem as a service.

Now that the images are registered in the AKS registry, we shall use the Kuber13 package and deploy the services, as follows:

Just like AWS, the Azure16 package provides connectivity to Azure cloud infrastructure from a Julia client. The client has a very similar architecture as AWS. It uses Swagger Java Library to generate the Julia signatures for the REST APIs exposed by the Azure framework. Unlike AWS, Julia signatures for Azure APIs are generated intermittently and are not part of an automated GitHub Action. We suggest the reader to explore the APIs and use them for their Azure management needs.

This is only the relevant piece of code5 for you to expose the `<strong>queens(N)</strong>` function from . Let us look into it in detail:

While we can orchestrate workloads using the Kubernetes, native platforms provide granular controls and the ability to use across a larger stack of services. They are not confined to container-based workloads only. Julia provides an extensive coverage of managing AWS-based services using the package AWS14. AWS is by far the most comprehensive integration among all the public cloud infrastructures for Julia. A large part of this is due to the automated code generation using a *GitHub* action, which is executed every day at 6:00am UTC. It queries the *GitHub* repository `<strong>aws-sdk-js</strong>` repository15 for the REST-based APIs. This action generates the wrapper functions for AWS services in Julia. The documentation is also pulled from the AWS documentation and presented as Juliadocs. This ensures the sources can accommodate all the changes to the AWS APIs and documentations. The APIs are generally designed as two categories:

While Docker is the de-facto standard for container management, Kubernetes is the most commonly supported orchestration platform for cloud deployment. Cloud Native Computing Foundation certifies10 over 90 Kubernetes supported platforms for API compliance. Some of the notable offerings are as follows:

Software Conformance (Certified Kubernetes), Cloud Native Computing Foundation, **[https://www.cncf.io/certification/software-conformance/](https://www.cncf.io/certification/software-conformance/)**

Kuber.jl, Julia Kubernetes Client, **[https://github.com/JuliaComputing/Kuber.jl](https://github.com/JuliaComputing/Kuber.jl)**

AWS, Julia interface to AWS, **[https://github.com/JuliaCloud/AWS.jl](https://github.com/JuliaCloud/AWS.jl)**

Kuber, Julia Kubernetes Client, **[https://github.com/JuliaComputing/Kuber.jl](https://github.com/JuliaComputing/Kuber.jl)**

Tanmay Mohapatra, Kubernetes in Julia with Kuber.jl, **[https://juliacomputing.com/blog/2018/12/kuber/](https://juliacomputing.com/blog/2018/12/kuber/)**

GoogleCloud, Google Cloud APIs for Julia, **[https://github.com/JuliaCloud/GoogleCloud.jl](https://github.com/JuliaCloud/GoogleCloud.jl)**

aws-sdk-js, AWS SDK for JavaScript in the browser and Node.js, **[https://github.com/aws/aws-sdk-js](https://github.com/aws/aws-sdk-js)**

Azure, Julia interface to Azure API, **[https://github.com/JuliaComputing/Azure.jl](https://github.com/JuliaComputing/Azure.jl)**

So, Julia containers created using Docker can be orchestrated in almost all the well-known cloud platforms using Kubernetes. The Kuber11 package provides Julia APIs to manage a Kubernetes orchestrated environment. A tutorial on orchestrating containers using Kuber on an Azure AKS12 is already available. The tutorial provides the methods to create new nodes, launch them and provides the steps to delete and clear the resources. The metrics for various Kubernetes nodes and pods can be queried from Julia as well. We shall try to deploy the container we created earlier into the **Azure Kubernetes Service** (**AKS**), using the following steps:

Behind the scenes, *JuliaHub* manages log monitoring, scheduling, and distributed processing in a transparent manner. This reduces significant management and deployment overheads from complex systems. The readers are advised to refer to the documentation2 for an elaborate understanding of *JuliaHub*.

So, Julia containers created using Docker can be orchestrated in almost all the well-known cloud platforms using Kubernetes. The Kuber11 package provides Julia APIs to manage a Kubernetes orchestrated environment. A tutorial on orchestrating containers using Kuber on an Azure AKS12 is already available. The tutorial provides the methods to create new nodes, launch them and provides the steps to delete and clear the resources. The metrics for various Kubernetes nodes and pods can be queried from Julia as well. We shall try to deploy the container we created earlier into the **Azure Kubernetes Service** (**AKS**), using the following steps:

Julia is an environment designed for scientific computations. It is extensively used for server-based computing. Hence, many production Julia deployments are carried out in cloud environments. Cloud environments have their own unique challenges. Julia as a language does not restrict itself to any specific cloud platform. However, the levels of integration with cloud providers are continuously evolving and are of differing capabilities at any point of time. Julia computing provides a *JuliaHub* environment that integrates closely with the Julia Development environment. We have seen the integrations with VS Code IDE earlier. An elaborate tutorial1 is provided through which a workload can be deployed into the *JuliaHub* and run as a distributed application.

*GoogleCloud*17 provides connectivity to the `<strong>Google Clouds Platform</strong>` (`<strong>GCP</strong>`). It wraps the Google JSON APIs and provides a lightweight framework to invoke the GCP APIs. Just like AWS and Azure, this provides connectivity to the GCP using the web services connectivity frameworks.

# 

# 

# 

Julia is a system designed for scientific computing and people involved in data-centric applications. In this chapter, we shall study how the language can be used to obtain useful data needed from structured and unstructured sources. They also need to obtain the data and process it so that useful insights can be obtained from the data.

# 

In this chapter, we will cover the following topics:

*   Setting up the environment
*   FileIO
*   Text data
*   Delimited files
*   XML files
*   HTML files
*   PDF files
*   Microsoft Office Documents
*   Image data
*   Tabular data
*   Data visualization

# 

We will look at accessing various file types, access data of text and image types. We shall represent them in data frames for databases like collective computations. Then we shall review some plotting and visualization techniques. All these are part of the ever-growing number of packages being added to the Julia ecosystem.

# 

We realized Julia is a powerful programming language. We also saw the advantages and integrated experience in solving many programmers’ challenges. Now is the time to use Julia in accessing various data sources and gather useful insights into them. Such applications are supported by Julia community developers in their continuous interest in developing newer packages to solidify the Julia ecosystem of packages. While we shall just scratch the surface in identifying and using a few of them, there are many interesting ones either in the pipeline or are in active development. So readers are suggested to keep reviewing the packages on a periodic basis to understand the newer features added.

Launch the Julia REPL and execute the following commands:

`<strong>julia&gt; cd("&lt;sample_code&gt;\\Chapter-15")</strong>`

`<strong>(@v1.5) pkg&gt; activate .</strong>`

``<strong>Activating environment at `Chapter-15\Project.toml`</strong>``

`<strong>(Chapter-15) pkg&gt; instantiate</strong>`

If you are running for the first time, it may take a substantial amount of time. At the end, you will have all the relevant packages needed to run the sample codes used in this chapter. You can continue to run the samples in the REPL or launch a Jupyter notebook (preferred) to try the examples in this chapter.

# 

Julia has conceptually preferred a driver-like architecture in addressing a class of problems. In , we saw the `<strong>WebIO</strong>` framework where HTML5 could be rendered on various frontends utilizing a common set of functional APIs. `<strong>FileIO</strong>` is inherently a similar API framework. It helps load contents of a complete file or save it out using the framework methods `<strong>load</strong>` and `<strong>save</strong>`. Based on the underlying file type the relevant reader and writer shall be invoked and the file shall be loaded into the memory. The framework currently supports many file types. A few being: PBM, PGM, PPM, NRRD, AVI, JPG, PDF, TIFF, or a large number of image, sound, and video formats[1](#k22mj3kq.html#n4upl4fndnr). The following code shall display an image on a Jupyter notebook:

`<strong>using FileIO</strong>`

`<strong>using ImageShow</strong>`

`<strong>tiff = joinpath(pathof(FileIO), "..", "..", "test", "files", "magic2.tiff")</strong>`

`<strong>image = load(tiff)</strong>`

You did not need any complex understanding of the `<strong>ImageMagick</strong>` library. Since, `<strong>.tiff</strong>` file is registered in the `<strong>FileIO</strong>` registry[2](#k22mj3kq.html#n4upl4fndns) as a supported file type and is to be handled by the `<strong>ImageMagick</strong>` library, a simple `<strong>load</strong>` method could invoke the necessary module and function and deliver the needed image. Similarly, a call to `<strong>save</strong>` method with a filename can convert the file to a `<strong>.jpg</strong>` file.

`<strong>save("magic2.jpg", image)</strong>`

# 

Text data are by far the simplest form of data to access and manipulate only when there is a consistent representation. Normal text files are not very common as they do not have any formatting or stylizing information. Formatting of text data and interleaving them with image and tabular content makes access cumbersome and often inaccessible. Text data can be typically of two types. Structured text data like a delimited files, Excel, and XML or unstructured data like a word and PDF files.

# 

We already discussed these specific file types in , where we wrote a CSV file with headers. Subsequently, we read the file and extracted the data as an array.

# 

No discussion on structured data is complete without reference to XML. Both **Document Object Models** (**DOM**) trees and streams event-based parsers are available in Julia. The XML packages you can rely are: `<strong>libxml2</strong>` based `<strong>LightXML</strong>`[3](#k22mj3kq.html#n4upl4fndnt) and `<strong>EzXML</strong>`[4](#k22mj3kq.html#n4upl4fndnu) or `<strong>libexpat</strong>` based `<strong>LibExpat</strong>`[5](#k22mj3kq.html#n4upl4fndnv). `<strong>LightXML</strong>` is the simplest of the DOM APIs that reads the XML into a tree and provides interfaces to traverse it.

`<strong>using LightXML</strong>`

`<strong>xdoc = parse_file("books.xml")</strong>`

`<strong>xroot = root(xdoc)</strong>`

`<strong>println("Root Name: ", name(xroot))</strong>`

The above expression shall print `<strong>Root Name: bookstore</strong>`. Further querying one can access the complete DOM from the `<strong>xroot</strong>` object.

`<strong>julia&gt; for c in child_nodes(xroot)</strong>`

`<strong>println("Node type:", nodetype(c))</strong>`

`<strong>if is_elementnode(c)</strong>`

`<strong>e = XMLElement(c)</strong>`

`<strong>println("Element Name: ", name(e))</strong>`

`<strong>end</strong>`

`<strong>end</strong>`

`<strong>Node type:3</strong>`

`<strong>Node type:1</strong>`

`<strong>Element Name: book</strong>`

`<strong>Node type:3</strong>`

`<strong>Node type:1</strong>`

`<strong>Element Name: book</strong>`

`<strong>Node type:3</strong>`

One can use xpath to search the document or validate the DTD using the `<strong>EzXML</strong>` APIs.

`<strong>julia&gt; using EzXML;</strong>`

`<strong>julia&gt; doc = readxml("books.xml");</strong>`

`<strong>julia&gt; validate(doc);</strong>`

`<strong>julia&gt; for author in nodecontent.(findall("//author/text()", doc))</strong>`

`<strong>println(author)</strong>`

`<strong>end</strong>`

`<strong>Giada De Laurentiis</strong>`

`<strong>J K. Rowling</strong>`

You can also use the `<strong>LibExpat</strong>` library to load the document and search xpath from the document.

`<strong>julia&gt; using LibExpat</strong>`

`<strong>julia&gt; esm = xp_parse(read("books.xml", String));</strong>`

`<strong>julia&gt; authors = LibExpat.find(esm, "//author")</strong>`

`<strong>2-element Array{ETree,1}:</strong>`

`<strong>&lt;author&gt;Giada De Laurentiis&lt;/author&gt;</strong>`

`<strong>&lt;author&gt;J K. Rowling&lt;/author&gt;</strong>`

While HTML documents can be parsed like XML documents, there are HTML parsers available that heal the ill-formed documents and handle them gracefully.

# 

While it is generally understood that well-formed HTML documents can be read like XML documents, it is not always true as many HTML files are not well-formed. `<strong>Gumbo.jl</strong>`[6](#k22mj3kq.html#n4upl4fndnw) is a package built on top of the Google Gumbo library for HTML 5. We shall see some sample usage from this DOM-based parser. A simple HTML string shall be read as a full HTML document and all the missing tags shall be added by the library. The simplicity of the API makes it a very easy tool to be used to read large HTML documents like the ones during web scanning.

`<strong>julia&gt; doc = parsehtml("&lt;h1&gt; Hello, world! &lt;/h1&gt;")</strong>`

`<strong>HTML Document:</strong>`

`<strong>&lt;!DOCTYPE &gt;</strong>`

`<strong>HTMLElement{:HTML}:&lt;HTML&gt;</strong>`

`<strong>&lt;head&gt;&lt;/head&gt;</strong>`

`<strong>&lt;body&gt;<br></strong>`

`<strong>&lt;h1&gt;</strong>`

`<strong>Hello, world!</strong>`

`<strong>&lt;/h1&gt;</strong>`

`<strong>&lt;/body&gt;</strong>`

`<strong>&lt;/HTML&gt;</strong>`

Since, the elements are of `<strong>HTMLNode</strong>` type with `<strong>parent</strong>` and `<strong>children</strong>` attributes, you shall be able to traverse them using the `<strong>AbstractTrees</strong>`[7](#k22mj3kq.html#n4upl4fndnx) interface.

`<strong>julia&gt; for elem in PreOrderDFS(doc.root) println(hasmethod(tag, (typeof(elem),)) ? tag(elem) : elem) end</strong>`

`<strong>HTML</strong>`

`<strong>head</strong>`

`<strong>body</strong>`

`<strong>h1</strong>`

`<strong>Hello, world!</strong>`

The elements can be accessed through `<strong>getindex</strong>` interface as well.

`<strong>julia&gt; doc.root[2][1][1]</strong>`

``<strong>HTML Text: ` Hello, world! `</strong>``

This is not meant to be an XML representation of HTML. Hence, `<strong>CDATA</strong>` is not supported in this package.

# 

`<strong>PDFIO</strong>`[8](#k22mj3kq.html#n4upl4fndny) was developed keeping in mind the PDF specification. Although, currently developed as a reader API, the intent has been to extend it to writing PDF content as a writer as well. Hence, the PDF objects used in the API can map to the specification closely. Unlike the `<strong>FileIO</strong>` mechanism of loading the file, `<strong>PDFIO</strong>` utilizes object handles to store object references that can be accessed later to obtain file information as and when required. For many programmers, it may suffice to load all the text in a PDF file. The code chunk to achieve the same with `<strong>PDFIO</strong>` is given as follows:

`<strong>julia&gt; using PDFIO</strong>`

`<strong>julia&gt; """</strong>`

````<strong>```</strong>````

`<strong>&nbsp;&nbsp;getPDFText(src, out) -&gt; Dict</strong>`

````<strong>```</strong>````

`<strong>- src - Input PDF file path from where text is to be extracted</strong>`

`<strong>- out - Output TXT file path where the output will be written</strong>`

`<strong>return - A dictionary containing metadata of the document</strong>`

`<strong>"""</strong>`

`<strong>function getPDFText(src, out)</strong>`

`<strong>doc = pdDocOpen(src)</strong>`

`<strong>docinfo = pdDocGetInfo(doc)</strong>`

`<strong>open(out, "w") do io</strong>`

`<strong>npage = pdDocGetPageCount(doc)</strong>`

`<strong>for i=1:npage</strong>`

`<strong>&nbsp;page = pdDocGetPage(doc, i)</strong>`

`<strong>&nbsp;pdPageExtractText(io, page)</strong>`

`<strong>end</strong>`

`<strong>end</strong>`

`<strong>pdDocClose(doc)</strong>`

`<strong>return docinfo</strong>`

`<strong>end</strong>`

`<strong>julia&gt; getPDFText("sample-google-doc.pdf", "sample-google-doc.txt")</strong>`

`<strong>Dict{String,Union{CDDate, String, CosObject}} with 1 entry:</strong>`

`<strong>"Producer" =&gt; "Skia/PDF m79"</strong>`

The API can be used for password-protected PDF files as well. It also can be used for validating digital signatures in a PDF document.

# 

Microsoft office documents are common forms of documents available. Although the document format is an open standard[9](#k22mj3kq.html#n4upl4fndnz) called the **Office Open XML** (**OOXML**) originally supported by Microsoft, the voluminous specification creates significant challenges for document consumers to directly utilize them in their applications. Taro[10](#k22mj3kq.html#n4upl4fndn0) written over *Apache Tika*, *Apache POI* and *Apache FOP* provides a JavaCall-based integration with Julia. The same system also supports the reading and writing of PDF files. The interface is fairly straight forward with these functionalities:

*   Extraction of text from Word documents
*   Access to tabular data for Excel documents
*   Using XSL-FO to generate PDF reports

`<strong>julia&gt; docxfile=joinpath(pathof(Taro), "..", "..", "test", "WhyJulia.docx");</strong>`

`<strong>julia&gt; meta, text = Taro.extract(docxfile);</strong>`

`<strong>julia&gt; meta["meta:author"]</strong>`

`<strong>"Avik Sengupta"</strong>`

`<strong>julia&gt; text[1:54]</strong>`

`<strong>"Why we created Julia\n\nIn short, because we are greedy."</strong>`

Let us access an excel file from the test directory.

`<strong>julia&gt; xlsxfile=joinpath(pathof(Taro), "..", "..", "test", "df-test.xlsx");</strong>`

`<strong>julia&gt; df = DataFrame(Taro.readxl(xlsxfile, "Sheet1", "B2:F8"))</strong>`

`<strong>6×5 DataFrame</strong>`

`<strong>│ Row │ H1&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;│ H2&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;│ H3&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;│ H4&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;│ H5&nbsp;&nbsp;│</strong>`

`<strong>│&nbsp;&nbsp;&nbsp;&nbsp; │ Any&nbsp;&nbsp;&nbsp;&nbsp; │ Any&nbsp;&nbsp;&nbsp;&nbsp; │ Any&nbsp;&nbsp;&nbsp;&nbsp; │ Any&nbsp;&nbsp;&nbsp;&nbsp; │ Any │</strong>`

`<strong>├─────┼─────────┼─────────┼─────────┼─────────┼─────┤</strong>`

`<strong>│ 1&nbsp;&nbsp; │ a&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; │ 1.0&nbsp;&nbsp;&nbsp;&nbsp; │ 1.0&nbsp;&nbsp;&nbsp;&nbsp; │ 1.0&nbsp;&nbsp;&nbsp;&nbsp; │ a a │</strong>`

`<strong>│ 2&nbsp;&nbsp; │ b&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; │ 2.0&nbsp;&nbsp;&nbsp;&nbsp; │ 2.0&nbsp;&nbsp;&nbsp;&nbsp; │ 1.0&nbsp;&nbsp;&nbsp;&nbsp; │ b b │</strong>`

`<strong>│ 3&nbsp;&nbsp; │ c&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; │ missing │ 3.0&nbsp;&nbsp;&nbsp;&nbsp; │ 0.0&nbsp;&nbsp;&nbsp;&nbsp; │ c c │</strong>`

`<strong>│ 4&nbsp;&nbsp; │ d&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; │ 4.0&nbsp;&nbsp;&nbsp;&nbsp; │ missing │ missing │ d d │</strong>`

`<strong>│ 5&nbsp;&nbsp; │ e&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; │ 5.0&nbsp;&nbsp;&nbsp;&nbsp; │ 5.0&nbsp;&nbsp;&nbsp;&nbsp; │ 1.0&nbsp;&nbsp;&nbsp;&nbsp; │ e e │</strong>`

`<strong>│ 6&nbsp;&nbsp; │ missing │ 6.0&nbsp;&nbsp;&nbsp;&nbsp; │ 6.0&nbsp;&nbsp;&nbsp;&nbsp; │ 1.0&nbsp;&nbsp;&nbsp;&nbsp; │&nbsp;&nbsp;&nbsp;&nbsp; │</strong>`

We shall discuss about DataFrames[11](#k22mj3kq.html#n4upl4fndn1) in a later section. For our understanding, they help access tabular data with ease. Since MS Excel is used for tabular data, many packages have been developed for the same. One of them is `<strong>XLSX.jl</strong>`[12](#k22mj3kq.html#n4upl4fndn2). Written in pure Julia, this package does not require the overhead of configuring Java. `<strong>XLSX.jl</strong>` is written using the ECMA-376 standard. This also gives it the flexibility to access MS Excel files using the file structure like WorkSheet, Cell IDs, and so on.

`<strong>julia&gt; using XLSX</strong>`

`<strong>julia&gt; xlsx = XLSX.readxlsx("df-test.xlsx")</strong>`

`<strong>XLSXFile("df-test.xlsx") containing 1 Worksheet</strong>`

`<strong>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;sheetname size&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;range</strong>`

`<strong>-------------------------------------------------</strong>`

`<strong>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Sheet1 9x5&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; B2:F10</strong>`

`<strong>julia&gt; sheet = xlsx["Sheet1"]</strong>`

`<strong>9×5 XLSX.Worksheet: ["Sheet1"](B2:F10)</strong>`

The cells from the data can be accessed using Excel cell id ranges. The result shall be a Matrix.

`<strong>julia&gt; sheet["B2"]</strong>`

`<strong>"H1"</strong>`

`<strong>Julia&gt; sheet["C4:E9"]</strong>`

`<strong>6×3 Matrix{Any}:</strong>`

`<strong>&nbsp;2&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;2&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 1.0</strong>`

`<strong>missing&nbsp;&nbsp; 3&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 0.0</strong>`

`<strong>&nbsp;4&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;missing&nbsp;&nbsp; missing</strong>`

`<strong>&nbsp;5&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;5&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 1.0</strong>`

`<strong>&nbsp;6&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;6&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 1.0</strong>`

`<strong>&nbsp;7&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;7&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 1.0</strong>`

A `<strong>DataFrame</strong>` can be obtained using the `<strong>XLSX.jl</strong>` interface as shown as follows:

`<strong>julia&gt; DataFrame(XLSX.readtable("df-test.xlsx", "Sheet1")…)</strong>`

`<strong>8 rows × 5 columns</strong>`

`<strong>&nbsp;H1 H2 H3 H4 H5</strong>`

`<strong>&nbsp;Any Any Any Any Any</strong>`

`<strong>1 a 1 1 1.0 a a</strong>`

`<strong>2 b 2 2 1.0 b b</strong>`

`<strong>3 c&nbsp;&nbsp; missing 3 0.0 c c</strong>`

`<strong>4 d 4 missing missing d d</strong>`

`<strong>5 e 5 5 1.0 e e</strong>`

`<strong>6&nbsp;&nbsp;&nbsp;&nbsp;missing 6 6 1.0</strong>`

`<strong>7 g 7 7 1.0 g g</strong>`

`<strong>8 h 8 8 1.0 h h</strong>`

# 

Raster images are stored as arrays of numbers. These numbers are arranged as matrices. They can be represented as separated channels or interleaved channels as shown in :

![](n4upl4fndrl.jpeg)

**Figure 15.1:** An image as a matrix of numbers (a) H and W being the height and width of the image and C is the number of channels. For example, a RGBA image will have 4 channels. (b) The same image is in an interlaced mode where the pixel components are placed one after the other horizontally. So you get a 2-D matrix instead of a 3-D array

While it may seem the memory is aligned in a 2- or 3-dimensional arrangement, it is not really that way. It all means in the images all red components are together, followed by green intensity values, and so on. Image file formats do not necessarily store data in this fashion. They apply several transformations and compress the data and store it as a binary stream of numbers. However, almost all applications of images shall convert the data to one of the above arrangements before they consume or render the image. In section FileIO, we loaded a tiff file and the image object created is of type `<strong>Array{ColorTypes.Gray{FixedPointNumbers.Normed{UInt8,8}},2}</strong>`. If we keep the complex type aside, it is just an array of 2 dimensions. The third dimension of the component types is not relevant as the gray images have just one component. The type `<strong>ColorTypes.Gray{FixedPointNumbers.Normed{UInt8,8}}</strong>` itself is quite complex in itself. Traditionally, images components are normalized as a floating-point value from 0.0 to 1.0. As floating-point number needs larger storage space, it can be represented as a byte of data where 0 maps to 0.0 and 255 to 1.0; thus a fixed-point representation of a number. In a byte of data, even all 8 bits may not be consumed by one value. And only 4 bits may be used. Thus, one byte can be used to store two-pixel intensities. `<strong>ImageCore</strong>`[13](#k22mj3kq.html#n4upl4fndn3) package has many such image representations that readers are suggested to refer to for understanding various image formats. You can use the Julia Imaging Library[14](#k22mj3kq.html#n4upl4fndn4) for image processing as well. OpenCV library provides a tutorial[15](#k22mj3kq.html#n4upl4fndn5) to integrate with a Julia frontend as well.

# 

Tabular data are quite common in many data applications. Usage of RDBMS acts as an extensive source of tabular data. Further, we see languages like R and Python Pandas use tabular data as a foundation of their maintaining records. The tabular data source we have already seen with delimited files like CSV. We also loaded an excel file as a `<strong>DataFrame</strong>` using Taro earlier. Julia created an abstract interface called `<strong>Tables.jl</strong>`[16](#k22mj3kq.html#n4upl4fndn6) that can be used to access tabular data:

![](n4upl4fndrm.jpeg)

**Figure 15.2:** (a) Tabular data are like vectors of different types that can be accessed with row and column accessors (b) Vector of a composite type each attribute is stored side by side

`<strong>Tables.jl</strong>` interface provides an easier interface to access the columns and abstract the rows so that the data can be accessed easily.

`<strong>julia&gt; using Tables</strong>`

`<strong>julia&gt; rows = Tables.rows(df)</strong>`

`<strong>6×5 DataFrameRows</strong>`

`<strong>&nbsp;&nbsp;H1&nbsp;&nbsp;H2&nbsp;&nbsp;H3&nbsp;&nbsp;H4&nbsp;&nbsp;H5</strong>`

`<strong>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Any&nbsp;&nbsp;Any&nbsp;&nbsp;Any&nbsp;&nbsp;Any&nbsp;&nbsp;Any</strong>`

`<strong>1 a&nbsp;&nbsp;1.0&nbsp;&nbsp;1.0&nbsp;&nbsp;1.0&nbsp;&nbsp;a a</strong>`

`<strong>2 b&nbsp;&nbsp;2.0&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 2.0&nbsp;&nbsp;1.0&nbsp;&nbsp;b b</strong>`

`<strong>3 c&nbsp;&nbsp;missing 3.0&nbsp;&nbsp;0.0&nbsp;&nbsp;c c</strong>`

`<strong>4 d&nbsp;&nbsp;4.0&nbsp;&nbsp;missing missing d d</strong>`

`<strong>5 e&nbsp;&nbsp;5.0&nbsp;&nbsp;5.0&nbsp;&nbsp;1.0&nbsp;&nbsp;e e</strong>`

`<strong>6 missing 6.0&nbsp;&nbsp;6.0&nbsp;&nbsp;1.0</strong>`

A new type of `<strong>DataFrameRows</strong>` is created that essentially is a view of the original `<strong>DataFrame</strong>`. You can access the column names of the table. You can also index the tables using the column names.

`<strong>julia&gt; Tables.columnnames(df)</strong>`

`<strong>5-element Array{Symbol,1}:</strong>`

`<strong>:H1</strong>`

`<strong>:H2</strong>`

`<strong>:H3</strong>`

`<strong>:H4</strong>`

`<strong>:H5</strong>`

`<strong>julia&gt; cols = Tables.columns(df);</strong>`

`<strong>julia&gt; cols[:H1]</strong>`

`<strong>6-element Array{Any,1}:</strong>`

`<strong>"a"</strong>`

`<strong>"b"</strong>`

`<strong>"c"</strong>`

`<strong>"d"</strong>`

`<strong>"e"</strong>`

`<strong>missing</strong>`

Although Matrix is not a table, one can use `<strong>DataFrames</strong>` and convert them to tables.

`<strong>julia&gt; rows = Tables.rows(DataFrame([1 2 3; 4 5 6; 7 8 9]))</strong>`

`<strong>3×3 DataFrameRows</strong>`

`<strong>x1 x2 x3</strong>`

`<strong>&nbsp;Int64 Int64 Int64</strong>`

`<strong>1 1 2 3</strong>`

`<strong>2 4 5 6</strong>`

`<strong>3 7 8 9</strong>`

`<strong>Tables.schema</strong>` method can be used to find the schema information.

`<strong>julia&gt; Tables.schema(df)</strong>`

`<strong>Tables.Schema:</strong>`

`<strong>:H1&nbsp;&nbsp;Any</strong>`

`<strong>:H2&nbsp;&nbsp;Any</strong>`

`<strong>:H3&nbsp;&nbsp;Any</strong>`

`<strong>:H4&nbsp;&nbsp;Any</strong>`

`<strong>:H5&nbsp;&nbsp;Any</strong>`

Moreover, you can use `<strong>TableOperations</strong>` package for operations like `<strong>select</strong>`, `<strong>map</strong>`, and `<strong>filter</strong>` on tabular data. Julia also provides a high-performance database called `<strong>JuliaDB</strong>`[17](#k22mj3kq.html#n4upl4fndn7). The readers are suggested to understand its capabilities as part of an exercise.

# 

Visual feedback is the most appealing insight one can get on data. While there are dimensional limitations in representing data visually, plotting is by far one of the most common methods used for data visualization.

`<strong>julia&gt; using Plots</strong>`

`<strong>julia&gt; x = 1:10; y = rand(10); z = rand(10);<br>julia&gt; plot(x, [y, z])</strong>`

And, you will see something as below rendered on a new window in case of REPL or on the Jupyter screen:

![](n4upl4fndrn.jpeg)

**Figure 15.3:** Plot with multiple series of data

However, passing 3 parameters to the plot function (like `<strong>plot(x, y, z)</strong>`) one can draw a 3-D plot of the data:

![](n4upl4fndro.jpeg)

**Figure 15.4:** A 3-D plot

`<strong>Plots</strong>`[18](#k22mj3kq.html#n4upl4fndn8) is an abstract plotting aggregator library that utilizes other packages like `<strong>GR</strong>`, `<strong>pyplot</strong>`, `<strong>Plotly</strong>`, and so on to render plots. These are also known as `<strong>backends</strong>`. GR is one of the fastest libraries to use for plotting and is used as the default in most Julia installations, while `<strong>pyplot (matplotlib)</strong>` is the most feature-rich backend. Plots translate the functions to the relevant backend and show the results. Readers are suggested to read the Plots documentation and tutorials for better understanding and usage scenarios.

# 

We scratched the surface of various data representation and transformation tools available in Julia to give an overview for you to explore. Unfortunately, the list is elaborate and extensive. We will probably not be in a position to provide a detailed view on all these categories of tools available. We presume you will use the opportunity to delve deeper into the packages and work on solving some real-life use cases.

# 

1.  Suppose you would like to use `<strong>FileIO</strong>` interface to read and extract text content from a PDF file. How will you implement such a feature? You can use PDFIO for the extracting text content in your implementation.
2.  Use Taro and edit a Microsoft Excel file.
3.  Use `<strong>matplotlib</strong>` to render the example instead of `<strong>GR</strong>`.
4.  JuliaDB provides persistent datasets. Use JuliaDB in your application to persist data needed for your application.
5.  Set up the OpenCV binding for the Julia installation you have.
6.  Use `<strong>XLSX.jl</strong>` to read tabular data from a Microsoft Excel file and use the data in your application.

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

[1](#k22mj3kq.html#n4upl4fndn9) File types supported by ImageMagick, MeshIO, Netpbm, etc. **[https://github.com/JuliaIO/FileIO.jl/blob/master/docs/registry.md](https://github.com/JuliaIO/FileIO.jl/blob/master/docs/registry.md)**

[2](#k22mj3kq.html#n4upl4fndoa) File types are supported in FileIO registry currently. They can be dynamically updated through code as well. **[https://github.com/JuliaIO/FileIO.jl/blob/master/docs/registry.md](https://github.com/JuliaIO/FileIO.jl/blob/master/docs/registry.md)**

[3](#k22mj3kq.html#n4upl4fndob) LightXML, A light-weight Julia package for XML based on libxml2, **[https://github.com/JuliaIO/LightXML.jl](https://github.com/JuliaIO/LightXML.jl)**

[4](#k22mj3kq.html#n4upl4fndoc) EzXML, XML/HTML handling tools for primates, **[https://github.com/JuliaIO/EzXML.jl](https://github.com/JuliaIO/EzXML.jl)**

[5](#k22mj3kq.html#n4upl4fndod) LibExpat, Julia interface to the Expat XML parser library, **[https://github.com/JuliaIO/LibExpat.jl](https://github.com/JuliaIO/LibExpat.jl)**

[6](#k22mj3kq.html#n4upl4fndoe) Gumbo, Julia wrapper around Google's gumbo C library for parsing HTML, **[https://github.com/JuliaWeb/Gumbo.jl](https://github.com/JuliaWeb/Gumbo.jl)**

[7](#k22mj3kq.html#n4upl4fndof) AbstractTrees.jl, Abstract trees interface for tree-like datastructures, **[https://juliacollections.github.io/AbstractTrees.jl/stable/](https://juliacollections.github.io/AbstractTrees.jl/stable/)**

[8](#k22mj3kq.html#n4upl4fndog) PDFIO, PDF Reader Library for Native Julia, **[https://github.com/sambitdash/PDFIO.jl](https://github.com/sambitdash/PDFIO.jl)**

[9](#k22mj3kq.html#n4upl4fndoh) ECMA-376, Also published under ISO/IEC 29500, **[https://www.ecma-international.org/publications-and-standards/standards/ecma-376/](https://www.ecma-international.org/publications-and-standards/standards/ecma-376/)**

[10](#k22mj3kq.html#n4upl4fndoi) Taro.jl, Work with Excel, Word and PDF Files in Julia, **[https://aviks.github.io/Taro.jl/](https://aviks.github.io/Taro.jl/)**

[11](#k22mj3kq.html#n4upl4fndoj) `DataFrames.jl`, In-memory tabular data in Julia, **[https://github.com/JuliaData/DataFrames.jl](https://github.com/JuliaData/DataFrames.jl)**

[12](#k22mj3kq.html#n4upl4fndok) `XLSX.jl`, Excel file reader and writer for the Julia language, **[https://github.com/felipenoris/XLSX.jl](https://github.com/felipenoris/XLSX.jl)**

[13](#k22mj3kq.html#n4upl4fndol) ImageCore.jl, Julia types for representing images, **[https://github.com/JuliaImages/ImageCore.jl](https://github.com/JuliaImages/ImageCore.jl)**

[14](#k22mj3kq.html#n4upl4fndom) JuliaImaging, Image Processing and Machine Vision for Julia, **[https://juliaimages.org/stable/](https://juliaimages.org/stable/)**

[15](#k22mj3kq.html#n4upl4fndon) Introduction to Julia OpenCV Binding, **[https://docs.opencv.org/4.5.1/d8/da4/tutorial\_julia.html](https://docs.opencv.org/4.5.1/d8/da4/tutorial_julia.html)**

[16](#k22mj3kq.html#n4upl4fndoo) Tables, An interface for tables in Julia, **[https://github.com/JuliaData/Tables.jl](https://github.com/JuliaData/Tables.jl)**

[17](#k22mj3kq.html#n4upl4fndop) `JuliaDB`, Parallel Analytic Database in Pure Julia, **[https://juliadb.org/](https://juliadb.org/)**

[18](#k22mj3kq.html#n4upl4fndoq) Plots, Powerful convenience for Julia visualizations and data analysis, **[https://github.com/JuliaPlots/Plots.jl](https://github.com/JuliaPlots/Plots.jl)**

Gumbo, Julia wrapper around Google's gumbo C library for parsing HTML, **[https://github.com/JuliaWeb/Gumbo.jl](https://github.com/JuliaWeb/Gumbo.jl)**

LibExpat, Julia interface to the Expat XML parser library, **[https://github.com/JuliaIO/LibExpat.jl](https://github.com/JuliaIO/LibExpat.jl)**

PDFIO, PDF Reader Library for Native Julia, **[https://github.com/sambitdash/PDFIO.jl](https://github.com/sambitdash/PDFIO.jl)**

AbstractTrees.jl, Abstract trees interface for tree-like datastructures, **[https://juliacollections.github.io/AbstractTrees.jl/stable/](https://juliacollections.github.io/AbstractTrees.jl/stable/)**

File types are supported in FileIO registry currently. They can be dynamically updated through code as well. **[https://github.com/JuliaIO/FileIO.jl/blob/master/docs/registry.md](https://github.com/JuliaIO/FileIO.jl/blob/master/docs/registry.md)**

File types supported by ImageMagick, MeshIO, Netpbm, etc. **[https://github.com/JuliaIO/FileIO.jl/blob/master/docs/registry.md](https://github.com/JuliaIO/FileIO.jl/blob/master/docs/registry.md)**

EzXML, XML/HTML handling tools for primates, **[https://github.com/JuliaIO/EzXML.jl](https://github.com/JuliaIO/EzXML.jl)**

LightXML, A light-weight Julia package for XML based on libxml2, **[https://github.com/JuliaIO/LightXML.jl](https://github.com/JuliaIO/LightXML.jl)**

ECMA-376, Also published under ISO/IEC 29500, **[https://www.ecma-international.org/publications-and-standards/standards/ecma-376/](https://www.ecma-international.org/publications-and-standards/standards/ecma-376/)**

Microsoft office documents are common forms of documents available. Although the document format is an open standard9 called the **Office Open XML** (**OOXML**) originally supported by Microsoft, the voluminous specification creates significant challenges for document consumers to directly utilize them in their applications. Taro10 written over *Apache Tika*, *Apache POI* and *Apache FOP* provides a JavaCall-based integration with Julia. The same system also supports the reading and writing of PDF files. The interface is fairly straight forward with these functionalities:

We shall discuss about DataFrames11 in a later section. For our understanding, they help access tabular data with ease. Since MS Excel is used for tabular data, many packages have been developed for the same. One of them is `<strong>XLSX.jl</strong>`12. Written in pure Julia, this package does not require the overhead of configuring Java. `<strong>XLSX.jl</strong>` is written using the ECMA-376 standard. This also gives it the flexibility to access MS Excel files using the file structure like WorkSheet, Cell IDs, and so on.

Plots, Powerful convenience for Julia visualizations and data analysis, **[https://github.com/JuliaPlots/Plots.jl](https://github.com/JuliaPlots/Plots.jl)**

Introduction to Julia OpenCV Binding, **[https://docs.opencv.org/4.5.1/d8/da4/tutorial\_julia.html](https://docs.opencv.org/4.5.1/d8/da4/tutorial_julia.html)**

JuliaImaging, Image Processing and Machine Vision for Julia, **[https://juliaimages.org/stable/](https://juliaimages.org/stable/)**

`JuliaDB`, Parallel Analytic Database in Pure Julia, **[https://juliadb.org/](https://juliadb.org/)**

Tables, An interface for tables in Julia, **[https://github.com/JuliaData/Tables.jl](https://github.com/JuliaData/Tables.jl)**

`DataFrames.jl`, In-memory tabular data in Julia, **[https://github.com/JuliaData/DataFrames.jl](https://github.com/JuliaData/DataFrames.jl)**

Taro.jl, Work with Excel, Word and PDF Files in Julia, **[https://aviks.github.io/Taro.jl/](https://aviks.github.io/Taro.jl/)**

ImageCore.jl, Julia types for representing images, **[https://github.com/JuliaImages/ImageCore.jl](https://github.com/JuliaImages/ImageCore.jl)**

`XLSX.jl`, Excel file reader and writer for the Julia language, **[https://github.com/felipenoris/XLSX.jl](https://github.com/felipenoris/XLSX.jl)**

You did not need any complex understanding of the `<strong>ImageMagick</strong>` library. Since, `<strong>.tiff</strong>` file is registered in the `<strong>FileIO</strong>` registry2 as a supported file type and is to be handled by the `<strong>ImageMagick</strong>` library, a simple `<strong>load</strong>` method could invoke the necessary module and function and deliver the needed image. Similarly, a call to `<strong>save</strong>` method with a filename can convert the file to a `<strong>.jpg</strong>` file.

Julia has conceptually preferred a driver-like architecture in addressing a class of problems. In , we saw the `<strong>WebIO</strong>` framework where HTML5 could be rendered on various frontends utilizing a common set of functional APIs. `<strong>FileIO</strong>` is inherently a similar API framework. It helps load contents of a complete file or save it out using the framework methods `<strong>load</strong>` and `<strong>save</strong>`. Based on the underlying file type the relevant reader and writer shall be invoked and the file shall be loaded into the memory. The framework currently supports many file types. A few being: PBM, PGM, PPM, NRRD, AVI, JPG, PDF, TIFF, or a large number of image, sound, and video formats1. The following code shall display an image on a Jupyter notebook:

No discussion on structured data is complete without reference to XML. Both **Document Object Models** (**DOM**) trees and streams event-based parsers are available in Julia. The XML packages you can rely are: `<strong>libxml2</strong>` based `<strong>LightXML</strong>`3 and `<strong>EzXML</strong>`4 or `<strong>libexpat</strong>` based `<strong>LibExpat</strong>`5. `<strong>LightXML</strong>` is the simplest of the DOM APIs that reads the XML into a tree and provides interfaces to traverse it.

Tabular data are quite common in many data applications. Usage of RDBMS acts as an extensive source of tabular data. Further, we see languages like R and Python Pandas use tabular data as a foundation of their maintaining records. The tabular data source we have already seen with delimited files like CSV. We also loaded an excel file as a `<strong>DataFrame</strong>` using Taro earlier. Julia created an abstract interface called `<strong>Tables.jl</strong>`16 that can be used to access tabular data:

No discussion on structured data is complete without reference to XML. Both **Document Object Models** (**DOM**) trees and streams event-based parsers are available in Julia. The XML packages you can rely are: `<strong>libxml2</strong>` based `<strong>LightXML</strong>`3 and `<strong>EzXML</strong>`4 or `<strong>libexpat</strong>` based `<strong>LibExpat</strong>`5. `<strong>LightXML</strong>` is the simplest of the DOM APIs that reads the XML into a tree and provides interfaces to traverse it.

Moreover, you can use `<strong>TableOperations</strong>` package for operations like `<strong>select</strong>`, `<strong>map</strong>`, and `<strong>filter</strong>` on tabular data. Julia also provides a high-performance database called `<strong>JuliaDB</strong>`17. The readers are suggested to understand its capabilities as part of an exercise.

While it is generally understood that well-formed HTML documents can be read like XML documents, it is not always true as many HTML files are not well-formed. `<strong>Gumbo.jl</strong>`6 is a package built on top of the Google Gumbo library for HTML 5. We shall see some sample usage from this DOM-based parser. A simple HTML string shall be read as a full HTML document and all the missing tags shall be added by the library. The simplicity of the API makes it a very easy tool to be used to read large HTML documents like the ones during web scanning.

`<strong>Plots</strong>`18 is an abstract plotting aggregator library that utilizes other packages like `<strong>GR</strong>`, `<strong>pyplot</strong>`, `<strong>Plotly</strong>`, and so on to render plots. These are also known as `<strong>backends</strong>`. GR is one of the fastest libraries to use for plotting and is used as the default in most Julia installations, while `<strong>pyplot (matplotlib)</strong>` is the most feature-rich backend. Plots translate the functions to the relevant backend and show the results. Readers are suggested to read the Plots documentation and tutorials for better understanding and usage scenarios.

No discussion on structured data is complete without reference to XML. Both **Document Object Models** (**DOM**) trees and streams event-based parsers are available in Julia. The XML packages you can rely are: `<strong>libxml2</strong>` based `<strong>LightXML</strong>`3 and `<strong>EzXML</strong>`4 or `<strong>libexpat</strong>` based `<strong>LibExpat</strong>`5. `<strong>LightXML</strong>` is the simplest of the DOM APIs that reads the XML into a tree and provides interfaces to traverse it.

We shall discuss about DataFrames11 in a later section. For our understanding, they help access tabular data with ease. Since MS Excel is used for tabular data, many packages have been developed for the same. One of them is `<strong>XLSX.jl</strong>`12. Written in pure Julia, this package does not require the overhead of configuring Java. `<strong>XLSX.jl</strong>` is written using the ECMA-376 standard. This also gives it the flexibility to access MS Excel files using the file structure like WorkSheet, Cell IDs, and so on.

`<strong>PDFIO</strong>`8 was developed keeping in mind the PDF specification. Although, currently developed as a reader API, the intent has been to extend it to writing PDF content as a writer as well. Hence, the PDF objects used in the API can map to the specification closely. Unlike the `<strong>FileIO</strong>` mechanism of loading the file, `<strong>PDFIO</strong>` utilizes object handles to store object references that can be accessed later to obtain file information as and when required. For many programmers, it may suffice to load all the text in a PDF file. The code chunk to achieve the same with `<strong>PDFIO</strong>` is given as follows:

While it may seem the memory is aligned in a 2- or 3-dimensional arrangement, it is not really that way. It all means in the images all red components are together, followed by green intensity values, and so on. Image file formats do not necessarily store data in this fashion. They apply several transformations and compress the data and store it as a binary stream of numbers. However, almost all applications of images shall convert the data to one of the above arrangements before they consume or render the image. In section FileIO, we loaded a tiff file and the image object created is of type `<strong>Array{ColorTypes.Gray{FixedPointNumbers.Normed{UInt8,8}},2}</strong>`. If we keep the complex type aside, it is just an array of 2 dimensions. The third dimension of the component types is not relevant as the gray images have just one component. The type `<strong>ColorTypes.Gray{FixedPointNumbers.Normed{UInt8,8}}</strong>` itself is quite complex in itself. Traditionally, images components are normalized as a floating-point value from 0.0 to 1.0. As floating-point number needs larger storage space, it can be represented as a byte of data where 0 maps to 0.0 and 255 to 1.0; thus a fixed-point representation of a number. In a byte of data, even all 8 bits may not be consumed by one value. And only 4 bits may be used. Thus, one byte can be used to store two-pixel intensities. `<strong>ImageCore</strong>`13 package has many such image representations that readers are suggested to refer to for understanding various image formats. You can use the Julia Imaging Library14 for image processing as well. OpenCV library provides a tutorial15 to integrate with a Julia frontend as well.

Since, the elements are of `<strong>HTMLNode</strong>` type with `<strong>parent</strong>` and `<strong>children</strong>` attributes, you shall be able to traverse them using the `<strong>AbstractTrees</strong>`7 interface.

While it may seem the memory is aligned in a 2- or 3-dimensional arrangement, it is not really that way. It all means in the images all red components are together, followed by green intensity values, and so on. Image file formats do not necessarily store data in this fashion. They apply several transformations and compress the data and store it as a binary stream of numbers. However, almost all applications of images shall convert the data to one of the above arrangements before they consume or render the image. In section FileIO, we loaded a tiff file and the image object created is of type `<strong>Array{ColorTypes.Gray{FixedPointNumbers.Normed{UInt8,8}},2}</strong>`. If we keep the complex type aside, it is just an array of 2 dimensions. The third dimension of the component types is not relevant as the gray images have just one component. The type `<strong>ColorTypes.Gray{FixedPointNumbers.Normed{UInt8,8}}</strong>` itself is quite complex in itself. Traditionally, images components are normalized as a floating-point value from 0.0 to 1.0. As floating-point number needs larger storage space, it can be represented as a byte of data where 0 maps to 0.0 and 255 to 1.0; thus a fixed-point representation of a number. In a byte of data, even all 8 bits may not be consumed by one value. And only 4 bits may be used. Thus, one byte can be used to store two-pixel intensities. `<strong>ImageCore</strong>`13 package has many such image representations that readers are suggested to refer to for understanding various image formats. You can use the Julia Imaging Library14 for image processing as well. OpenCV library provides a tutorial15 to integrate with a Julia frontend as well.

While it may seem the memory is aligned in a 2- or 3-dimensional arrangement, it is not really that way. It all means in the images all red components are together, followed by green intensity values, and so on. Image file formats do not necessarily store data in this fashion. They apply several transformations and compress the data and store it as a binary stream of numbers. However, almost all applications of images shall convert the data to one of the above arrangements before they consume or render the image. In section FileIO, we loaded a tiff file and the image object created is of type `<strong>Array{ColorTypes.Gray{FixedPointNumbers.Normed{UInt8,8}},2}</strong>`. If we keep the complex type aside, it is just an array of 2 dimensions. The third dimension of the component types is not relevant as the gray images have just one component. The type `<strong>ColorTypes.Gray{FixedPointNumbers.Normed{UInt8,8}}</strong>` itself is quite complex in itself. Traditionally, images components are normalized as a floating-point value from 0.0 to 1.0. As floating-point number needs larger storage space, it can be represented as a byte of data where 0 maps to 0.0 and 255 to 1.0; thus a fixed-point representation of a number. In a byte of data, even all 8 bits may not be consumed by one value. And only 4 bits may be used. Thus, one byte can be used to store two-pixel intensities. `<strong>ImageCore</strong>`13 package has many such image representations that readers are suggested to refer to for understanding various image formats. You can use the Julia Imaging Library14 for image processing as well. OpenCV library provides a tutorial15 to integrate with a Julia frontend as well.

Microsoft office documents are common forms of documents available. Although the document format is an open standard9 called the **Office Open XML** (**OOXML**) originally supported by Microsoft, the voluminous specification creates significant challenges for document consumers to directly utilize them in their applications. Taro10 written over *Apache Tika*, *Apache POI* and *Apache FOP* provides a JavaCall-based integration with Julia. The same system also supports the reading and writing of PDF files. The interface is fairly straight forward with these functionalities:

# 

# 

# 

In the previous chapter, we learnt about techniques of acquiring data. We will try to make meaningful information extraction for `<strong>Natural Language Processing</strong>` (`<strong>NLP</strong>`) tasks. While NLP is an ever growing and actively researched field, this chapter will provide exposure to some tools available in Julia to meet your text analytics needs.

# 

In this chapter, we will cover the following topics:

*   Text processing pipeline
*   Preprocessing 
    *   Tokenization
    *   Word representations
    *   Embeddings
*   Semantic analysis
*   Classifiers
*   Extractive summarization 
    *   Evaluation metrics
*   Named entity recognition
*   ULMFiT

# 

The reader shall be able to appreciate various document corpus models, understanding of text tokenization, vector representations use of semantic analysis techniques, named entity recognition, some standard text classification models like `<strong>ULMFit</strong>`.

# 

Research in the text analysis space has been so rapid that many concepts that have been relevant a few years ago are getting continuously augmented with newer concepts and knowledge. Neural computing has made significant inroads into most text processing tasks. The traditional statistical approaches through relevant are being experimented alongside deep learning techniques. We shall discuss a few commonly used packages for text analytics and suggest the reader to explore and learn newer techniques as they proceed with expanding their horizons. The codes or texts described here are for the ease of learning and understanding and are trivial. They should not be considered for a production performance:

![](n4upl4fndqa.jpeg)

**Figure 16.1:** A typical text processing pipeline

Most text processing tasks can be considered as a simplified pipeline of activities as shown in . However, it is an over simplification from your real-life use cases and there may be certain tasks that are overlapping. We describe the pipeline components as follows:

*   **Acquisition**: The text acquisition we discuss here is of non-structured texts obtained from web captures, reading files of various formats like MS Word or PDF from disks, social media feeds, and so on. While we discussed a part of the tasks in the previous chapter, the challenge remains in creating the level of granularity in a document. For example, a document can be as short as a Twitter feed or as large as a complete book. This distinction needs to be understood from the problem you are trying to solve.
*   **Tokenization**: Text chunks need to be tokenized into building blocks such that meaningful interpretations can be carried out. For example, a document can be of multiple paragraphs, each paragraph may contain sentences and sentences can be composed of words. And, the word arrangement in certain fashion will lead to a meaningful document. Not just words, even certain sub-words may have meanings; say *unforgettable* as a word has a meaningful association with *forget*. Although the reader has never seen the word, he will analyze the word in sub-words like *un-forget-able* and will be able to derive a meaningful association.
*   **Representation**: Finally, everything in computers needs to be represented as a collection of numbers or symbols for any subsequent analysis. The tokens created through tokenization are needed to be represented as an array of numbers that take into consideration the context of the tokens and their interrelations. They should have certain inherent properties of the language they represent. While initially started as word matrices or one-hot vectors, they are represented as dense vectors of larger dimensions (300 can be typical) or even language models of the extremely large number of parameters as in the case of GPT-2.
*   **Models**: These are not language models of the previous section but the actual task at hand we will like to solve. Given that we have a reasonable language model representation of say vectors of words, we will like to use them to find the sentiments a particular sentence may represent. The models will take the word vectors as input and complete a classification task if the problem is of sentiment analysis. This classification task can be a logistic regression or a neural network or a conditional random field, and so on. Similarly, one building a text summarization task may utilize a text generation neural model.

If you look closely, the first three tasks are unsupervised or semi-supervised to understand the language better. Why so? For example, while training the word vectors a probability of a word is estimated given the surrounding words. In some tasks, random words are deleted from the sentences so that the language model guesses those words correctly. Moreover, the training is carried out over a large corpus of text consisting of trillions of words through web captures or Wikipedia content and so on. and no labeling is carried out on the words. Hence, the information about the words and their association with other words are captured as part of a mathematical vector representation. Since, training the representation can be time consuming and resource hungry, it may be carried out by a research team utilizing large resources in the cloud dedicated for months of training.

Let us look at the sentence: Can you pass me the can? The homonym can here stand for two different meanings. Hence, the mere existence of a word in a sentence is not enough details unless the surrounding context is captured as well. This gets worse with homophones. Since, many a times the text and voice-related techniques in NLP are similar, the representation of tokens to an intermediate form definitely add significant benefits. The classic sentence: Tell me a tale about a tail will generate substantially different signatures for similar sounding phonetic tokens. More and more research is focused on picking up representations off a language model and utilizing that as input into the task models.

Julia package ecosystem provides solutions for all the four pipeline tasks[1](#61911y84.html#n4upl4fndgh). One package that cuts across the pipeline is `<strong>TextAnalysis</strong>`[2](#61911y84.html#n4upl4fndgi). We shall discuss about it in some detail. There are other packages we will touch upon as well. However, one may use a modeling tool like the `<strong>Flux</strong>` package to actually develop the task-specific models. We shall discuss Flux in some detail in the next chapter.

# 

We can loosely call the first three steps in the pipeline as preprocessing. `<strong>TextAnalysis</strong>` package and few associated packages maintained by JuliaText GitHub organization provide such functionalities. Documents in Julia can be of various kinds. `<strong>TextAnalysis</strong>` provides the following document types:

*   **StringDocument**: The document is considered as a Julia String.
*   **FileDocument**: The document resides as a file on the file system of the operating system.
*   **NGramDocument**: Document is considered as a bag or set of words or word pairs or triplets depending on N. The order and context of the words are not maintained.
*   **TokenDocument:** The document is stored as a sequence of tokens. Tokens can be words but can be derivatives of words as well.

Every document type has a specific purpose. For example, `<strong>NGramDocuments</strong>` cannot be used for operations where word sequences are important. By definition, sequence labeling requires the data are presented in a proper language sequence. However, N-grams are quite useful in SPAM classification where the existence of words in the document is enough to differentiate HAM (good document) from SPAM. Documents may be worked upon as a group; also called corpus.

Typically, a corpus will have similar properties across the documents; thus one can apply a common transformation on the corpus. `<strong>TextAnalysis</strong>` has a type `<strong>Corpus</strong>` that captures this concept effectively. `<strong>CorpusLoader</strong>`[3](#61911y84.html#n4upl4fndgj) package can download standard text corpus and lazy loading it as and when needed.

# 

Tokenization is subdividing the document into useful chunks of text. A document can be tokenized at a level of paragraph, sentence, word or even character level. `<strong>MultiresolutionIterator</strong>`[4](#61911y84.html#n4upl4fndgk) package provides an iterator framework to access this level of tokenization. However, there is a `<strong>WordTokenizer</strong>`[5](#61911y84.html#n4upl4fndgl) package that provides various ways to tokenize words and sentences. Every tokenization scheme has certain limitations and needs to be used judiciously.

`<strong>using WordTokenizers<br>s1 = """This is a multi-line text. And the sentence splitter<br>may not do a great job on this. But if no line ending<br>is provided it works like a charm. Even keeps Dr. Smith intact."""<br><br>split_sentences(s1)</strong>`

`<strong>7-element Array{SubString{String},1}:<br>&nbsp;"This is a multi-line text."<br>&nbsp;"And the sentence splitter"<br>&nbsp;"may not do a great job on this."<br>&nbsp;"But if no line ending"<br>&nbsp;"is provided it works like a charm."<br>&nbsp;"Even keeps Dr. Smith"<br>&nbsp;"intact."</strong>`

The same sentences without line separators:

`<strong>s2 = "This is a multi-line text. And the sentence splitter "*</strong>`

`<strong>"is provided it works like a charm. Even keeps Dr. Smith "*</strong>`

`<strong>"intact."</strong>`

`<strong>split_sentences(s2)</strong>`

`<strong>3-element Array{SubString{String},1}:</strong>`

`<strong>"This is a multi-line text."</strong>`

`<strong>"And the sentence splitter is provided it works like a charm."</strong>`

`<strong>"Even keeps Dr. Smith intact."</strong>`

Similar is with word tokenization as well. The poorman’s word tokenizer behaves somewhat imperfectly.

`<strong>s3 = "I won't be able to attend the meeting. This isn't possible."</strong>`

`<strong>set_tokenizer(poormans_tokenize);</strong>`

`<strong>println("Poorman: \t", tokenize(s3))</strong>`

`<strong>set_tokenizer(nltk_word_tokenize);</strong>`

`<strong>println("NLTK: \t", tokenize(s3))</strong>`

`<strong>Poorman:&nbsp;&nbsp;SubString{String}["I", "wont", "be", "able", "to", "attend", "the", "meeting", "This", "isnt", "possible"]</strong>`

`<strong>NLTK:&nbsp;&nbsp;["I", "wo", "n't", "be", "able", "to", "attend", "the", "meeting.", "This", "is", "n't", "possible", "."]</strong>`

# 

While we discussed tokenization, not all words are alike. Let’s compare the sentences: *Educate to add value to a person vs. Education is valued for a person*. Both sentences have similar meanings but tokenized words education versus educated are distinct. So is *value* and *valued*. They may be truncated to something that may not have a relevant meaning but can be represented for comparison purposes. These truncated representations are called `<strong>word stems</strong>`. The words *is*, *to*, *a*, and *for* are there in most sentences and do not add significant context to the communication. They are known as `<strong>stop words</strong>`. Similarly, capitalization may be eliminated to improve comparisons.

`<strong>doc1 = StringDocument("Educate to add value to a person")</strong>`

`<strong>prepare!(doc1, strip_case | strip_stopwords | stem_words)</strong>`

`<strong>println(doc1.text)</strong>`

`<strong>doc2 = StringDocument("Education is valued for a person")</strong>`

`<strong>prepare!(doc2, strip_case | strip_stopwords | stem_words)</strong>`

`<strong>println(doc2.text)</strong>`

`<strong>---</strong>`

`<strong>educ add valu person</strong>`

`<strong>educ valu person</strong>`

Now, both sentences become easier to compare. Let us look at a similarity measure called `<strong>cos_similarity</strong>`. Before we do so we use a corpus to simplify the strings.

`<strong>using LinearAlgebra</strong>`

`<strong>doc1 = StringDocument("Educate to add value to a person")</strong>`

`<strong>doc2 = StringDocument("Education is valued for a person")</strong>`

`<strong>doc3 = StringDocument("Education is valuable asset for a human")</strong>`

`<strong>c = Corpus([doc1, doc2, doc3])</strong>`

`<strong>prepare!(c, strip_case | strip_stopwords | stem_words)</strong>`

`<strong>update_lexicon!(c)</strong>`

This produces the output: `<strong>("educ add valu person", "educ valu person", "educ valuabl asset human")</strong>`

Now, we can compute the document term matrix and transform it to obtain the `<strong>tf-idf</strong>` or term frequency over inverse document frequency. `<strong>tf-idf</strong>` is particularly useful as it finds out the frequency of a term but penalizes the most commonly used words across all the documents; thus a useful characteristic for a document. If you use the cosine similarity matrix[6](#61911y84.html#n4upl4fndgm), you will find the `<strong>doc1</strong>` and `<strong>doc2</strong>` are more similar to each other than `<strong>doc3. educ</strong>` as a stem is ignored as it is there in all the documents.

`<strong>tfm =&nbsp;&nbsp;tf_idf(dtm(c))</strong>`

`<strong>cs = Matrix(tfm*tfm')</strong>`

`<strong>d = sqrt.(diag(cs))</strong>`

`<strong>cs ./ (d*d')</strong>`

`<strong>3×3 Array{Float64,2}:</strong>`

`<strong>1.0&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 0.462709&nbsp;&nbsp;0.0</strong>`

`<strong>0.462709&nbsp;&nbsp;1.0&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 0.0</strong>`

`<strong>0.0&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 0.0&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 1.0</strong>`

# 

While `<strong>tf-idf</strong>` is a useful representation, so is one-hot vector, they have certain limitations. They are sparse and consider the count of the words in the documents. They do not take the local context of the words into consideration. For example, the word *Apple* can mean the fruit or the technology company. Hence, the surrounding words are crucial in identifying the relevant context of the homonyms.

Text embeddings provide dense fixed-sized word to vector conversions that take words and their association or relations to other words into consideration. Thus they have better context information than classical NLP techniques. In some sense have become the de-facto representative language models today. The `<strong>Embeddings</strong>`[7](#61911y84.html#n4upl4fndgn) package provides the commonly used embeddings in various languages. We shall use the simplest and the oldest `<strong>Word2Vec</strong>` embeddings in the examples below.

`<strong>using Embeddings</strong>`

`<strong>const et = load_embeddings(Word2Vec)</strong>`

`<strong>const w2idx = Dict((w =&gt; i for (i, w) in enumerate(et.vocab)))</strong>`

`<strong>embedding(w) = et.embeddings[:, w2idx[w]]</strong>`

`<strong>res = embedding("king") - embedding("man") + embedding("woman")</strong>`

`<strong>cosdist = vec(sum(res .* et.embeddings, dims=1))</strong>`

`<strong>ids = partialsortperm(cosdist, 1:5, rev=true)</strong>`

`<strong>[(et.vocab[ii], cosdist[ii]) for ii in ids]</strong>`

`<strong>5-element Array{Tuple{String,Float32},1}:</strong>`

`<strong>("king", 0.8990531)</strong>`

`<strong>("queen", 0.80069506)</strong>`

`<strong>("monarch", 0.69625)</strong>`

`<strong>("princess", 0.6639391)</strong>`

`<strong>("prince", 0.6048718)</strong>`

Although, normal presumption shall be that the outcome should be closest to `<strong>queen</strong>`, it may not be so. The cosine similarity is effective but not foolproof. Hence, it is best to consider a few closest words to the expected results. Cosine similarity is only effective to the extent of unsupervised training carried out by the general-purpose large corpus training conducted by techniques like, `<strong>Word2Vec</strong>`, `<strong>GloVe</strong>`, or `<strong>Transformers</strong>`, and so on. They can be further fine-tuned for task-specific training using supervised learning for other tasks.

# 

The semantic analysis methods supported in `<strong>TextAnalysis</strong>` package are **Latent Semantic Analysis** (**LSA**) and **Latent Dirichlet Allocation** (**LDA**). Both techniques are dimension reduction techniques, particularly useful in finding topics in a corpus. The essential assumptions in both these models are words that distinctively establish topics in a document are just a handful numbers.

Similarly, there are only handful of topics that exist in a document collection. LSA computation in Julia utilizes Single Valued Decomposition (SVD) to correlate topics with words and in LDA Gibb’s sampling is carried out to simulate the predicted outcome. Readers are suggested to look at some of the authoritative texts on both these topics to get a formal understanding of techniques used in LSA and LDA.

`<strong>using LinearAlgebra</strong>`

`<strong>doc1 = StringDocument("Educate to add value to a person")</strong>`

`<strong>doc2 = StringDocument("Education is valued for a person")</strong>`

`<strong>doc3 = StringDocument("Education is valuable asset for a human")</strong>`

`<strong>c = Corpus([doc1, doc2, doc3])</strong>`

`<strong>prepare!(c, strip_case | strip_stopwords | stem_words)</strong>`

`<strong>update_lexicon!(c)</strong>`

`<strong>println((c[1].text, c[2].text, c[3].text))</strong>`

`<strong>lsa(c)</strong>`

Intuitively, one can see the third document is roughly different from the other two. Moreover, `<strong>educ</strong>` being a common stem across all the documents does not contribute to belongingness to any specific topic classifications. The `<strong>SVD</strong>` outputs shall validate the similar findings in the results as shown.

`<strong>("educ add valu person", "educ valu person", "educ valuabl asset human")</strong>`

`<strong>SVD{Float64,Float64,Array{Float64,2}}</strong>`

`<strong>U factor:</strong>`

`<strong>3×3 Array{Float64,2}:</strong>`

`<strong>0.0&nbsp;&nbsp;-0.931471&nbsp;&nbsp;-0.363815</strong>`

`<strong>0.0&nbsp;&nbsp;-0.363815&nbsp;&nbsp; 0.931471</strong>`

`<strong>1.0&nbsp;&nbsp; 0.0&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;0.0</strong>`

`<strong>singular values:</strong>`

`<strong>3-element Array{Float64,1}:</strong>`

`<strong>0.47571307544817304</strong>`

`<strong>0.3266291290597002</strong>`

`<strong>0.16072253690428198</strong>`

`<strong>Vt factor:</strong>`

`<strong>3×7 Array{Float64,2}:</strong>`

`<strong>-3.63e-17&nbsp;&nbsp;0.57735&nbsp;&nbsp;0.0&nbsp;&nbsp;0.57735&nbsp;&nbsp; 4.92e-17&nbsp;&nbsp; 4.92e-17&nbsp;&nbsp;0.57735</strong>`

`<strong>-0.783248&nbsp;&nbsp;0.0&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;0.0&nbsp;&nbsp;0.0&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;-0.439615&nbsp;&nbsp;-0.439615&nbsp;&nbsp;0.0</strong>`

`<strong>-0.62171&nbsp;&nbsp; 0.0&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;0.0&nbsp;&nbsp;0.0&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 0.55384&nbsp;&nbsp;&nbsp;&nbsp;0.55384&nbsp;&nbsp; 0.0</strong>`

`<strong># add&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; asset&nbsp;&nbsp;&nbsp;&nbsp;educ human&nbsp;&nbsp;&nbsp;&nbsp; person&nbsp;&nbsp;&nbsp;&nbsp; valu&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;valuabl</strong>`

The same finding shall be re-established in the LDA findings as well.

`<strong>m = DocumentTermMatrix(c)</strong>`

`<strong>lda(m, 2, 2000, 0.1, 0.1)</strong>`

`<strong>(</strong>`

`<strong>[2, 1]&nbsp;&nbsp;=&nbsp;&nbsp;0.142857</strong>`

`<strong>[1, 2]&nbsp;&nbsp;=&nbsp;&nbsp;0.25</strong>`

`<strong>[1, 3]&nbsp;&nbsp;=&nbsp;&nbsp;0.25</strong>`

`<strong>[2, 3]&nbsp;&nbsp;=&nbsp;&nbsp;0.285714</strong>`

`<strong>[1, 4]&nbsp;&nbsp;=&nbsp;&nbsp;0.25</strong>`

`<strong>[2, 5]&nbsp;&nbsp;=&nbsp;&nbsp;0.285714</strong>`

`<strong>[2, 6]&nbsp;&nbsp;=&nbsp;&nbsp;0.285714</strong>`

`<strong>[1, 7]&nbsp;&nbsp;=&nbsp;&nbsp;0.25, [0.0 0.0 1.0; 1.0 1.0 0.0])</strong>`

When we create 2 topics for the LDA, the third document is classified distinctively from the other two.

# 

`<strong>TextAnalysis</strong>` package has an implementation of Naïve Bayes Classifier. Naïve Bayes assumes the classification depends on the words independently. Hence, it is only relevant for bag of words or tokens models and not useful for seq2seq tasks. Here is an example with sentences we used earlier.

`<strong>using TextAnalysis</strong>`

`<strong>m = NaiveBayesClassifier([:g1, :g2])</strong>`

`<strong>fit!(m, "Education is valued for a person", :g1)</strong>`

`<strong>fit!(m, "Education is valuable asset for a human", :g2)</strong>`

`<strong>predict(m, "Education is valued for a man")</strong>`

`<strong>Dict{Symbol,Float64} with 2 entries:</strong>`

`<strong>:g2 =&gt; 0.278623</strong>`

`<strong>:g1 =&gt; 0.721377</strong>`

The sentence `<strong>Education is valued for a man</strong>` belongs to `<strong>:g1</strong>` than `<strong>:g2</strong>`.

# 

Although not entirely a preprocessing step, summarization in Julia is based on the `<strong>TextRank</strong>`[8](#61911y84.html#n4upl4fndgo) algorithm that is a modification from the `<strong>PageRank</strong>` algorithm. The sentences that have the most number of varied words are ranked higher or leaders from which other sentences are linked. The linked sentences are followed from the leader with certain probability. This exercise is carried out as a simulation for several depths. The sentences that were followed the maximum number of times are ranked higher and are put in as part of the summary. The summarization of the first paragraph of Text Processing Pipeline may look as follows:

`<strong>s = "Research in the text analysis space has been so rapid…</strong>`

`<strong>real life use cases and there may be certain tasks that are overlapping."</strong>`

`<strong>summary = *(summarize(StringDocument(s), ns=4)…)</strong>`

`<strong>"Neural computing has made significant inroads into most text processing tasks. The traditional statistical approaches though relevant are being experimented alongside deep learning techniques. The codes or texts described here are for the ease of learning and understanding and should not be considered for a production performance. However, it is an over simplification from your real-life use cases and there may be certain tasks that are overlapping."</strong>`

Since, the sentences are picked up from the paragraphs they are not generative.

# 

`<strong>Recall Oriented Understudy for Gisting Evaluation</strong>` (`<strong>ROUGE</strong>`) can be used to test the quality of metrics against a human-created reference summary.

`<strong>ref = ["Text analysis research has been rapid. ",</strong>`

`<strong>&nbsp;"Neural computing is being used alongwith statistical techniques. ",</strong>`

`<strong>&nbsp;"Deep learning is gaining popularity as well. ",</strong>`

`<strong>&nbsp;"Code and text provides here are for ease of learning and should not be used for production performance."]</strong>`

`<strong>julia&gt; rouge_n(ref, summary, 2, avg=true)</strong>`

`<strong>0.3645833333333333</strong>`

`<strong>julia&gt; rouge_n(ref, summary, 1, avg=true)</strong>`

`<strong>0.956140350877193</strong>`

While 2-gram scores are not as overlapping as far as singles words go there are many overlaps.

# 

`<strong>TextModels</strong>`[9](#61911y84.html#n4upl4fndgp) package abstracts out a few of the modeling tasks and provides predefined models for the same. One such model is `<strong>Named Entity Recognition</strong>` (`<strong>NER</strong>`) tagging. The class of problem is also known called as `<strong>end-to-end sequence labeling</strong>`[10](#61911y84.html#n4upl4fndgq). `<strong>Part of Speech</strong>` (`<strong>POS</strong>`) tagging is another similar problem. While we shall quickly run through a sample code the detailed model has been discussed in the paper. Since, names are quite common in sentences it is crucial to be identified in a NLU task to be able to carry out subsequent actions like in chatbots; for example, greeting a person or finding the destination for booking a ticket for her air travel, etc.

`<strong>using TextModels</strong>`

`<strong>ner = NERTagger()<br>s1 = "Kumar is from Bangalore and works for Julia Computing."<br>println(ner(s1))<br>s2 = "Julia language is easy to learn."<br>println(ner(s2))</strong>`

`<strong>["PER", "O", "O", "LOC", "O", "O", "O", "ORG", "ORG", "O"]<br>["PER", "O", "O", "O", "O", "O", "O"]</strong>`

While the first sentence is able to identify the person, locations and organization easily, Julia in the second sentence is mapped as person. There will be some form of misidentifications in the NER tagging though generally it matches reasonably in most cases. Secondly, the NER API only supports 5 classes of entities: Person(PER), Location(LOC), Organization(ORG), Miscellaneous(MISC), and Others(O). Thirdly, this model also captures sub-word information through CNN embedding (refer to the paper for a detailed explanation).

# 

**Universal Language Model Fine Tuning** (**ULMFiT**)[11](#61911y84.html#n4upl4fndgr) for Text Classification is a model used for text classification tasks originally. However, the same learnt weights could be repurposed for other downstream text tasks. `<strong>TextModels</strong>` package has an implementation for the same that can be used for some of the advanced text processing tasks. The model usage has four steps:

*   Data loading and preprocessing
*   Language model pre-training
*   Fine tuning the language model
*   Fine tuning the classifier for the downstream tasks

One can add special purpose dropouts as layers to the model as well. We will suggest the readers to look into the `<strong>TextModels</strong>` documentation for a detailed understanding and usage of the ULMFiT model.

# 

Text analytics is a vast field to explore and requires the right tools for the best results. The focus in most Julia packages is to address a focused problem at hand than investing in large language model development. While it is not hard to do so, utilizing transfer learning and fine tuning the embeddings for solving a domain problem is more attractive for many practitioners. As we skimmed through a few techniques in developing awareness in the field, the details are left to the readers to continuously develop and gain expertise.

# 

1.  What is the difference between stemming vs. lemmatization? Are there any benefits of using one over the other? Why is lemmatization harder to implement than stemming?
2.  TF-IDF is used as a language representation from a long time. Why is it not used for large scale language models? Do you see any applications of the TF-IDF still? What are some of its advantages?
3.  There are many well-known embeddings available to be used for NLP tasks. Word2vec and GLOVE are quite popular embeddings. However, they have certain limitations. What are some of those?
4.  NER tagging tokenizes the words in certain fashion. Is it possible to modify the tokenizer to something else? Can you find a use case where you will like to utilize a different tokenization scheme?
5.  Use ULMFit for one of your real-life use cases. What are some of the challenges you are facing in doing so?

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

[1](#61911y84.html#n4upl4fndgs) The readers are suggested to watch the video: Ayush Kaushal, Natural Language Processing in Julia, JuliaCon 2020, **[https://www.youtube.com/watch?v=hHCi8ojazqk](https://www.youtube.com/watch?v=hHCi8ojazqk)**

[2](#61911y84.html#n4upl4fndgt) TextAnalysis, Julia package for text analysis, **[https://github.com/JuliaText/TextAnalysis.jl](https://github.com/JuliaText/TextAnalysis.jl)**

[3](#61911y84.html#n4upl4fndgu) CorpusLoader, A variety of loaders for various NLP corpora, **[https://github.com/JuliaText/CorpusLoaders.jl](https://github.com/JuliaText/CorpusLoaders.jl)**

[4](#61911y84.html#n4upl4fndgv) MultiResolutionsIterators, Tools for working with Iterators of Iterators of …, **[https://github.com/oxinabox/MultiResolutionIterators.jl](https://github.com/oxinabox/MultiResolutionIterators.jl)**

[5](#61911y84.html#n4upl4fndgw) WordTokenizers, High-performance tokenizers for natural language processing and other related tasks, **[https://github.com/JuliaText/WordTokenizers.jl](https://github.com/JuliaText/WordTokenizers.jl)**

[6](#61911y84.html#n4upl4fndgx) `cos_similarity` method is already available in the master branch of the `TextAnalysis` package but we used the v0.7.2 version of the release for this book.

[7](#61911y84.html#n4upl4fndgy) Embeddings, Functions and data dependencies for loading various word embeddings, **[https://github.com/JuliaText/Embeddings.jl](https://github.com/JuliaText/Embeddings.jl)**

[8](#61911y84.html#n4upl4fndgz) Rada Mihalcea and Paul Tarau, 2004: TextRank: Bringing Order into Texts, Department of Computer Science University of North Texas, **[https://web.eecs.umich.edu/~mihalcea/papers/mihalcea.emnlp04.pdf](https://web.eecs.umich.edu/~mihalcea/papers/mihalcea.emnlp04.pdf)**

[9](#61911y84.html#n4upl4fndg0) TextModels, Neural Network-based models for Natural Language Processing, **[https://github.com/JuliaText/TextModels.jl](https://github.com/JuliaText/TextModels.jl)**

[10](#61911y84.html#n4upl4fndg1) Xuezhe Ma and Eduard Hovy, End-to-end Sequence Labeling via Bi-directional LSTM-CNNs-CRF, 2016, Proceedings of the 54th Annual Meeting of the Association for Computational Linguistics (Volume 1: Long Papers), **[http://dx.doi.org/10.18653/v1/P16-1101](http://dx.doi.org/10.18653/v1/P16-1101)**

[11](#61911y84.html#n4upl4fndg2) Jeremy Howard and Sebastian Ruder, Universal Language Model Fine-tuning for Text Classification, ACL 2018, **[https://www.aclweb.org/anthology/P18-1031.pdf](https://www.aclweb.org/anthology/P18-1031.pdf)**

`<strong>TextModels</strong>`9 package abstracts out a few of the modeling tasks and provides predefined models for the same. One such model is `<strong>Named Entity Recognition</strong>` (`<strong>NER</strong>`) tagging. The class of problem is also known called as `<strong>end-to-end sequence labeling</strong>`10. `<strong>Part of Speech</strong>` (`<strong>POS</strong>`) tagging is another similar problem. While we shall quickly run through a sample code the detailed model has been discussed in the paper. Since, names are quite common in sentences it is crucial to be identified in a NLU task to be able to carry out subsequent actions like in chatbots; for example, greeting a person or finding the destination for booking a ticket for her air travel, etc.

**Universal Language Model Fine Tuning** (**ULMFiT**)11 for Text Classification is a model used for text classification tasks originally. However, the same learnt weights could be repurposed for other downstream text tasks. `<strong>TextModels</strong>` package has an implementation for the same that can be used for some of the advanced text processing tasks. The model usage has four steps:

Tokenization is subdividing the document into useful chunks of text. A document can be tokenized at a level of paragraph, sentence, word or even character level. `<strong>MultiresolutionIterator</strong>`4 package provides an iterator framework to access this level of tokenization. However, there is a `<strong>WordTokenizer</strong>`5 package that provides various ways to tokenize words and sentences. Every tokenization scheme has certain limitations and needs to be used judiciously.

Typically, a corpus will have similar properties across the documents; thus one can apply a common transformation on the corpus. `<strong>TextAnalysis</strong>` has a type `<strong>Corpus</strong>` that captures this concept effectively. `<strong>CorpusLoader</strong>`3 package can download standard text corpus and lazy loading it as and when needed.

Now, we can compute the document term matrix and transform it to obtain the `<strong>tf-idf</strong>` or term frequency over inverse document frequency. `<strong>tf-idf</strong>` is particularly useful as it finds out the frequency of a term but penalizes the most commonly used words across all the documents; thus a useful characteristic for a document. If you use the cosine similarity matrix6, you will find the `<strong>doc1</strong>` and `<strong>doc2</strong>` are more similar to each other than `<strong>doc3. educ</strong>` as a stem is ignored as it is there in all the documents.

Tokenization is subdividing the document into useful chunks of text. A document can be tokenized at a level of paragraph, sentence, word or even character level. `<strong>MultiresolutionIterator</strong>`4 package provides an iterator framework to access this level of tokenization. However, there is a `<strong>WordTokenizer</strong>`5 package that provides various ways to tokenize words and sentences. Every tokenization scheme has certain limitations and needs to be used judiciously.

Xuezhe Ma and Eduard Hovy, End-to-end Sequence Labeling via Bi-directional LSTM-CNNs-CRF, 2016, Proceedings of the 54th Annual Meeting of the Association for Computational Linguistics (Volume 1: Long Papers), **[http://dx.doi.org/10.18653/v1/P16-1101](http://dx.doi.org/10.18653/v1/P16-1101)**

Jeremy Howard and Sebastian Ruder, Universal Language Model Fine-tuning for Text Classification, ACL 2018, **[https://www.aclweb.org/anthology/P18-1031.pdf](https://www.aclweb.org/anthology/P18-1031.pdf)**

Julia package ecosystem provides solutions for all the four pipeline tasks1. One package that cuts across the pipeline is `<strong>TextAnalysis</strong>`2. We shall discuss about it in some detail. There are other packages we will touch upon as well. However, one may use a modeling tool like the `<strong>Flux</strong>` package to actually develop the task-specific models. We shall discuss Flux in some detail in the next chapter.

Julia package ecosystem provides solutions for all the four pipeline tasks1. One package that cuts across the pipeline is `<strong>TextAnalysis</strong>`2. We shall discuss about it in some detail. There are other packages we will touch upon as well. However, one may use a modeling tool like the `<strong>Flux</strong>` package to actually develop the task-specific models. We shall discuss Flux in some detail in the next chapter.

Although not entirely a preprocessing step, summarization in Julia is based on the `<strong>TextRank</strong>`8 algorithm that is a modification from the `<strong>PageRank</strong>` algorithm. The sentences that have the most number of varied words are ranked higher or leaders from which other sentences are linked. The linked sentences are followed from the leader with certain probability. This exercise is carried out as a simulation for several depths. The sentences that were followed the maximum number of times are ranked higher and are put in as part of the summary. The summarization of the first paragraph of Text Processing Pipeline may look as follows:

Text embeddings provide dense fixed-sized word to vector conversions that take words and their association or relations to other words into consideration. Thus they have better context information than classical NLP techniques. In some sense have become the de-facto representative language models today. The `<strong>Embeddings</strong>`7 package provides the commonly used embeddings in various languages. We shall use the simplest and the oldest `<strong>Word2Vec</strong>` embeddings in the examples below.

TextModels, Neural Network-based models for Natural Language Processing, **[https://github.com/JuliaText/TextModels.jl](https://github.com/JuliaText/TextModels.jl)**

Rada Mihalcea and Paul Tarau, 2004: TextRank: Bringing Order into Texts, Department of Computer Science University of North Texas, **[https://web.eecs.umich.edu/~mihalcea/papers/mihalcea.emnlp04.pdf](https://web.eecs.umich.edu/~mihalcea/papers/mihalcea.emnlp04.pdf)**

Embeddings, Functions and data dependencies for loading various word embeddings, **[https://github.com/JuliaText/Embeddings.jl](https://github.com/JuliaText/Embeddings.jl)**

`cos_similarity` method is already available in the master branch of the `TextAnalysis` package but we used the v0.7.2 version of the release for this book.

WordTokenizers, High-performance tokenizers for natural language processing and other related tasks, **[https://github.com/JuliaText/WordTokenizers.jl](https://github.com/JuliaText/WordTokenizers.jl)**

MultiResolutionsIterators, Tools for working with Iterators of Iterators of …, **[https://github.com/oxinabox/MultiResolutionIterators.jl](https://github.com/oxinabox/MultiResolutionIterators.jl)**

CorpusLoader, A variety of loaders for various NLP corpora, **[https://github.com/JuliaText/CorpusLoaders.jl](https://github.com/JuliaText/CorpusLoaders.jl)**

TextAnalysis, Julia package for text analysis, **[https://github.com/JuliaText/TextAnalysis.jl](https://github.com/JuliaText/TextAnalysis.jl)**

The readers are suggested to watch the video: Ayush Kaushal, Natural Language Processing in Julia, JuliaCon 2020, **[https://www.youtube.com/watch?v=hHCi8ojazqk](https://www.youtube.com/watch?v=hHCi8ojazqk)**

`<strong>TextModels</strong>`9 package abstracts out a few of the modeling tasks and provides predefined models for the same. One such model is `<strong>Named Entity Recognition</strong>` (`<strong>NER</strong>`) tagging. The class of problem is also known called as `<strong>end-to-end sequence labeling</strong>`10. `<strong>Part of Speech</strong>` (`<strong>POS</strong>`) tagging is another similar problem. While we shall quickly run through a sample code the detailed model has been discussed in the paper. Since, names are quite common in sentences it is crucial to be identified in a NLU task to be able to carry out subsequent actions like in chatbots; for example, greeting a person or finding the destination for booking a ticket for her air travel, etc.

# 

# 

# 

In the previous chapter, we learnt about packages for NLP tasks. We used neural computation under the hood for some of the tasks. In this chapter, we shall model Flux using neural networks primitives. We assume you have a fundamental understanding of deep learning and exploring how to model using Julia. This chapter is not meant to be an introduction to deep learning.

# 

*   Deep learning
*   What is Flux?
*   Model Zoo
*   Types of Neural Network 
    *   Fully connected
    *   CNN
    *   RNN

# 

In this chapter, the reader shall be able to understand fully connected, **convolutional neural networks** (**CNN**) and **recurrent neural networks** (**RNN**) through examples. The examples are picked up from the Model Zoo samples of the Flux package. This will help the user to understand the modeling framework and help them build complex models or understand models built with Flux.

# 

Digital agents help us accomplish a task better or faster; a chatbot assistant for example. The process of learning improves the efficiency of such an agent. When an agent learns, over time it either performs faster or more accurately the same task. `<strong>Artificial Neural Networks</strong>` (`<strong>ANN</strong>`) are such learning techniques that have been used to solve many classification problems.

Given a set of inputs, we will like to know which set of it belongs to. The MNIST dataset of handwritten black and white images is a good example to look at:

![](n4upl4fndqt.jpeg)

**Figure 17.1:** Sample images[1](#hcbia8m5.html#n4upl4fndj7) from the MNIST dataset[2](#hcbia8m5.html#n4upl4fndj8). Images are classified as digits they represent. The dataset contains 60,000 images of training and 10,000 images for testing. The images are black and white are of in size. The handwriting data is obtained from almost 500 distinct writers

The example here is a case of supervised learning where the input and output classes are provided. The system shall be trained using an ANN. It shall predict values from the dataset and they shall be compared with :

![](n4upl4fndqu.jpeg)

**Figure 17.2:** The input image of digit 2 enters into the neural network as a vector of binary values. It’s multiplied with a weight of wij for each connection. All values are added as the values enter the intermediate layer. An ANN can have multiple intermediate layers before they pass onto the output layer. Output layers have the same number of nodes as there are classes of output expected. 10 in this case. A non-linear activation function is applied to convert the values closer to binary values of 0 or 1

 can be explained mathematically by the following equations. A non-linear activation function (σ)[3](#hcbia8m5.html#n4upl4fndj9) may be applied at each layer.

![](n4upl4fndqv.jpeg)

As can be seen above, the neural network is mostly a weighted sum of values. We are interested in finding the best values of the weights that fit the inputs X to the output Y. The activation function introduces the needed non-linearity to the system. In the output layer, the activation function (`<strong>softmax</strong>`), pushes smaller values closer to zero and larger values closer to 1. `<strong>softmax</strong>`, `<strong>sigmoid</strong>`, and `<strong>tanh</strong>` are commonly used as the activation functions in classification tasks.

The system operates to find the best values of that shall minimize the losses. Back-propagation using gradient descent is used as the most common technique to update the weights[4](#hcbia8m5.html#n4upl4fndka). We shall not be detailing the neural network concepts here but expect the readers to refer to the more authoritative text in the interest of elaborate mathematical treatment needed on this topic. However, our focus in this chapter will be to introduce the reader to the `<strong>Flux</strong>`[5](#hcbia8m5.html#n4upl4fndkb) package that provides elaborate modeling primitives for deep learning or other machine learning applications.

# 

Flux is a platform designed to model machine learning problems. The modeling capabilities can be thought of as similar to *Tensorflow*[6](#hcbia8m5.html#n4upl4fndkc) or *PyTorch*. Flux utilizes many of the standard Julia capabilities like macros, `<strong>Automated Differentiation</strong>` (`<strong>AD</strong>`) with `<strong>Zygote</strong>`, GPU based computation with the package `<strong>CUDA</strong>`. It also utilizes `<strong>DataLoader</strong>` to lazy load and batch process data needed for computation. While Flux may seem like a simple package, it has many interesting usage of macros and may be used as a good sample code to understand advanced Julia programming.

We shall try to solve a linear regression problem using Flux. Let Us look at the following set of the equations. We have taken a linear equation, added a bit of Gaussian noise to simulate our dataset. This is a very common technique used in data sciences to simulate artificial data for addressing some simple tasks or showcase a concept that depends on real-world data.

`<strong>x = 5*rand(100)</strong>`

`<strong>y = 3*x .+ 4 .+ randn(100);</strong>`

![](n4upl4fndqw.jpeg)

**Figure 17.3:** Plot of the x and y. y1 represents the scatter plot of the raw data. y2 is the line plot of the equation y3 is the line plot of the linear regression line:

The coefficients of the regression equations are computed using the formula:

![](n4upl4fndqx.jpeg)

The code looks as below with the resultant output.

`<strong>using Statistics</strong>`

`<strong>xy = x.*y</strong>`

`<strong>xm = mean(x)</strong>`

`<strong>ym = mean(y)</strong>`

`<strong>xym = mean(xy)</strong>`

`<strong>x2 = x.^2</strong>`

`<strong>x2m = mean(x2)</strong>`

`<strong>ac = (xym - xm*ym)/(x2m - xm*xm)</strong>`

`<strong>bc = ym - ac*xm</strong>`

`<strong>ac, bc</strong>`

`<strong>(3.040366776530602, 3.7358219564957356)</strong>`

In `<strong>Flux,</strong>` we can model a similar regression equation and estimate for `<strong>a</strong>` and `<strong>b</strong>` using the gradient descent method. Initially, we shall define the parameters `<strong>a</strong>` and `<strong>b</strong>` and compute the model using the parameters.

`<strong>using Flux</strong>`

`<strong>a, b = rand(1), rand(1)</strong>`

`<strong>ps = params([a, b])</strong>`

`<strong>model(x) = a.*x .+ b</strong>`

We shall define a loss function and minimize it by computing the appropriate values for parameters `<strong>a</strong>` and `<strong>b</strong>`.

`<strong>function loss(x, y)</strong>`

`<strong>yp = model(x)</strong>`

`<strong>sum((y .- yp).^2)</strong>`

`<strong>end</strong>`

The loss is the sum squares of errors; we use a gradient descent optimizer and update the parameters.

`<strong>data = zip(x, y)</strong>`

`<strong>opt = Descent(0.02)</strong>`

`<strong>for d in data</strong>`

`<strong>gs = Flux.gradient(ps) do</strong>`

`<strong>loss(d…)</strong>`

`<strong>end</strong>`

`<strong>Flux.Optimise.update!(opt, ps, gs)</strong>`

`<strong>@info ps</strong>`

`<strong>end</strong>`

The model, loss function, the optimizer, and data acquisition techniques may vary from problem to problem:

![](n4upl4fndqy.jpeg)

**Figure 17.4:** Plot of the x and y. y1 represents the scatter plot of the raw data. y2 is the scatter plot of the output from the Flux model. y3 is the line plot of the linear regression line:

The model output is a close approximation for the linear regression equation. The model may not find the exact optimal value as the stochastic gradient descent is only a search technique along the gradient of the loss function in the parameter space. Better convergence strategies may be needed to ensure the search reaches the optimal value. The same is shown from one of the runs of the optimization in the following image. The plot details are skipped from the explanation here. However, the complete code is available in the Jupyter notebook `<strong>Chapter-17/Chapter-17 Deep Learning.ipynb</strong>`.

![](n4upl4fndqz.jpeg)

**Figure 17.5:** The stochastic gradient descent search is along the gradient to the surface created by the loss function with reference to the parameters a and b. The best result thus obtained is still far from the absolute optimum computed from analytical means

# 

Machine learning is time consuming and laborious process. Developing good quality models, relevant datasets, and parameter tuning to showcase results can be quite substantial even for advanced data scientists. Hence, it is important to have a collection of good quality samples that can be used as references for developing other models. Model Zoo[7](#hcbia8m5.html#n4upl4fndkd) for `<strong>Flux</strong>` started on the same premise. There are samples for a representative class of problems that data scientists can look at to design their own models. Note that the problems are representational and for learning purposes only. They may not be the most performance optimal code. `<strong>Flux</strong>` provides a general purpose modeling framework. For specific image classification problems, one may look at packages like `<strong>Metalhead</strong>`[8](#hcbia8m5.html#n4upl4fndke).

# 

In Deep Learning, we discussed about ANNs. However, ANNs are of various kinds. The types are broadly based on how the computation units or nodes interact with each other or the topology of the nodes. We shall discuss three classes of neural networks with examples adapted from model zoo.

*   Fully connected (Dense) networks
*   Convolutional networks (CNN)
*   Recurrent networks (RNN)

# 

We address the MNIST handwritten digit classification problem as shown in . We use a fully connected layer of ANN similar to , with the following details:

*   Input layer with nodes
*   An intermediate layer with 32 nodes with ReLU activation
*   Output layer with 10 nodes with softmax activation

A downside of using fully connected layers is the number of parameters. Since the nodes are fully connected, the total number of parameters shall be: 784 × 32 + 32 × 10 = 25, 408 parameters. We suggest you to look into the complete code from the accompanying Jupyter notebook.

The images are flattened into vectors. They are loaded into a data loader that samples the data in batches of 1024.

`<strong>function getdata(args)</strong>`

`<strong>…</strong>`

`<strong>xtrain, ytrain = MLDatasets.MNIST.traindata(Float32)</strong>`

`<strong># Flatten images to vector</strong>`

`<strong>xtrain = Flux.flatten(xtrain)<br>&nbsp;&nbsp;&nbsp;&nbsp;# One-hot-encode the labels</strong>`

`<strong>ytrain = onehotbatch(ytrain, 0:9)</strong>`

`<strong># Batching</strong>`

`<strong>train_data = DataLoader(xtrain, ytrain, batchsize=args.batchsize, shuffle=true)</strong>`

`<strong>…</strong>`

`<strong>return train_data, test_data</strong>`

`<strong>end</strong>`

This can be easily designed with the layers of primitives.

`<strong>function build_model(; imgsize=(28,28,1), nclasses=10)</strong>`

`<strong>return Chain(Dense(prod(imgsize), 32, relu),</strong>`

`<strong>&nbsp;&nbsp;Dense(32, nclasses))</strong>`

`<strong>end</strong>`

As the part of training the following code shall be executed:

`<strong>function train(; kws…)</strong>`

`<strong># Initializing Model parameters</strong>`

`<strong>args = Args(; kws…)</strong>`

`<strong># Load Data</strong>`

`<strong>train_data,test_data = getdata(args)</strong>`

`<strong># Construct model</strong>`

`<strong>m = build_model()</strong>`

`<strong>train_data = args.device.(train_data)</strong>`

`<strong>test_data = args.device.(test_data)</strong>`

`<strong>m = args.device(m)</strong>`

`<strong>loss(x,y) = logitcrossentropy(m(x), y)</strong>`

`<strong>## Training</strong>`

`<strong>evalcb = () -&gt; @show(loss_all(train_data, m))</strong>`

`<strong>opt = ADAM(args.η)</strong>`

`<strong>@epochs args.epochs Flux.train!(loss, params(m), train_data, opt, cb = evalcb)</strong>`

`<strong>@show accuracy(train_data, m)</strong>`

`<strong>@show accuracy(test_data, m)</strong>`

`<strong>end</strong>`

The highlighted portion is the actual training code in `<strong>Flux</strong>`. The data are loaded in batches into the model. The gradients are updated using `<strong>ADAM</strong>` as the optimizer after every batch of computation. You will need to set a learning rate with the optimizer as well. Intermittently progress shall be reported using the `<strong>evalcb</strong>` callback. The `<strong>train!</strong>` function takes only one callback as input and invokes it after each batch. The training shall be executed `<strong>args.epochs</strong>` times. This means the whole training data shall be used to train the model 10 times. `<strong>logitcrossentropy</strong>` is used as a loss function. At the end of the run, the 91.77% accuracy of classification could be achieved with 10 epochs. On MNIST dataset state of the art accuracy achieved is almost 99.9%. While we are not keen on trying state of art accuracy, we will look at the CNNs, which are commonly used networks for image processing.

# 

CNNs are fundamentally driven from the concept of classic convolution and feature engineering of image processing. Image processing engineers would design convolution kernels and apply them over an image to extract features from the images. For example, edge extraction using Sobel filters. Neural networks could be used as a means to compute the filter parameters[9](#hcbia8m5.html#n4upl4fndkf) in an automated fashion; thus became the foundation of the CNN models:

![](n4upl4fndq0.jpeg)

**Figure 17.6:** A kernel will truncate the image by one pixel on both sides. You can use padding so that such reduction is not affected. The kernel is actually 3 dimensional and that introduces additional channels to the output image. If an image of 3 channels when convolved with a kernel of 3×3×8 shall need 3×3×3×8 parameters. These parameters are the same and are applied at every location of the pixel. The parameter sharing reduces the overall parameters used in a CNN

While CNNs reuse the parameters, the kernels are applied at multiple resolutions. For example, the maxpool operation takes a grid of 2×2 pixels of the image and replaces the 4 pixels with the highest pixel value. A maxpool operation reduces the width and height of an image by half due to this sub-sampling.

The `<strong>getdata</strong>` function is very similar to what we saw earlier save we take much smaller batch of images (128 in CNN) and we introduce an extra dimension so that images are 28×28×1 in size. The model is designed as layers of primitives.

`<strong>function build_model(args; imgsize = (28,28,1), nclasses = 10)</strong>`

`<strong>return Chain(</strong>`

`<strong># Input image 28x28x1 image</strong>`

`<strong>Conv((3, 3), imgsize[3]=&gt;4, relu),</strong>`

`<strong>#Output: 26x26x4 Params: 3x3x1x4=36</strong>`

`<strong>BatchNorm(4),</strong>`

`<strong>Conv((3, 3), 4=&gt;4, relu),</strong>`

`<strong>#Output: 24x24x4 Params: 3x3x4x4=144</strong>`

`<strong>BatchNorm(4),</strong>`

`<strong>MaxPool((2,2)), #Output: 12x12x4</strong>`

`<strong>Dropout(0.1),</strong>`

`<strong>Conv((3, 3), 4=&gt;8, relu),</strong>`

`<strong>#Output: 10x10x8 Params: 3x3x4x8=288</strong>`

`<strong>BatchNorm(8),</strong>`

`<strong>Conv((3, 3), 8=&gt;8, relu),</strong>`

`<strong>#Output: 8x8x8 Params: 3x3x8x8=576</strong>`

`<strong>BatchNorm(8),</strong>`

`<strong>MaxPool((2,2)), #Output: 4x4x8</strong>`

`<strong>Dropout(0.1),</strong>`

`<strong>Conv((3, 3), 8=&gt;32, pad=(1, 1), relu),</strong>`

`<strong>#Output: 4x4x32 Params: 3x3x8x32=2304</strong>`

`<strong>BatchNorm(32),</strong>`

`<strong>Conv((3, 3), 32=&gt;nclasses, relu),</strong>`

`<strong>#Output: 2x2x10 Params: 3x3x32x10=2880</strong>`

`<strong>BatchNorm(10),</strong>`

`<strong>AdaptiveMeanPool((1, 1)), #Output: 1x1x10</strong>`

`<strong>flatten #Output: 10</strong>`

`<strong>)</strong>`

`<strong>end</strong>`

It is layers of convolution, batch normalization, maxpooling, and dropouts. `<strong>Flux</strong>` provides simple layers like primitives to model DNN layers very similar to frameworks like *Keras*. The model itself behaves like a callable. Hence, you can call like `<strong>model(x)</strong>` to obtain the predicted values.

The training code is similar to the previous one with additions of stopping execution after 99% test accuracy is achieved. The model is saved for the run that provides maximum test accuracy. The saved model is loaded to print the test results.

`<strong>function train(; kws…)</strong>`

`<strong>…</strong>`

`<strong>best_acc = 0.0</strong>`

`<strong>last_improvement = 0</strong>`

`<strong>for epoch_idx in 1:args.epochs</strong>`

`<strong>Flux.train!(loss, params(model), train_set, opt)</strong>`

`<strong>acc = accuracy(test_set, model)</strong>`

`<strong>if acc &gt;= best_acc</strong>`

`<strong>BSON.@save joinpath(args.savepath, "mnist_conv.bson")</strong>`

`<strong>&nbsp;&nbsp; model=cpu(model) epoch_idx acc</strong>`

`<strong>best_acc = acc</strong>`

`<strong>last_improvement = epoch_idx</strong>`

`<strong>end</strong>`

`<strong>acc &gt;= 0.99 &amp;&amp; break</strong>`

`<strong>if epoch_idx - last_improvement &gt;= 5 &amp;&amp; opt.eta &gt; 1e-6</strong>`

`<strong>opt.eta /= 10.0</strong>`

`<strong>last_improvement = epoch_idx</strong>`

`<strong>end</strong>`

`<strong>end</strong>`

`<strong>end</strong>`

The learning rate is dynamic and updated when the model accuracy does not improve over 5 epochs. If you run this model for about 10 iterations, you shall be able to achieve an accuracy of 99% for the test data, a significant improvement over the fully connected model. The CNN code executes better on GPUs or TPUs. If you are using a CPU-based system, you may find the examples executing slower than you would expect.

# 

RNNs[10](#hcbia8m5.html#n4upl4fndkg) are used to solve problems of sequences. For example, text and voice involve a sequence of words or characters or voice phonemes. They have a meaningful context due to the order in which the tokens appear. Similarly, the output can also be sequenced themselves. For example, guessing the next word given a sequence of words like a fill in the blanks exercise.

![](n4upl4fndq1.jpeg)

**Figure 17.7:** RNN with states updated with every input of the sequence. Unrolling the node in the time scale is shown in the image above

Forward pass of the RNN may have equations as shown:

*s[t] = tanh(Ux[t] + Ws[t-1])*

*o[t] = softmax (Vs[t])*

While solving RNN parameters, the network is unrolled in the timescale as shown. Since sequences can be of arbitrary sizes, either they are considered as a sequence of a large size where null inputs are provided to fill up a finite large sequence or an end-of-sequence marker is used to end the sequence. Typically, the back propagation is carried out for the unrolled network. The state parameters are stored in a vector of width H. U, W, and V vectors are independent of the time. While they get updated as part of back-propagation steps, the updated values shall be used for the subsequent forward pass.

In the problem, we are trying to solve, we take a sequence of characters in 5 languages and input them into a recurrent network. We will like to infer the language the character sequence represents. Since we are using character sequence and we ignore all accented and case sensitive characters, we have a vocabulary size of 39. The number of output categories are 5 (`<strong>:en</strong>`, `<strong>:fr</strong>`, `<strong>:it</strong>`, `<strong>:da</strong>` and `<strong>:es</strong>`). Thus the matrices shall have the following dimensions:

*   U - 5 × 39
*   W - 5 × 5
*   V - 5 × 5-V is ignored in the `<strong>Flux RNNCell</strong>`

RNN while a useful tool may not be the best option for large sequences. As the sequence gets longer the gradients may vanish and back-propagation may not be able to update the weights effectively. So slowly the earlier inputs from the sequence are forgotten by the network. Networks like `<strong>Long Short Term Memory</strong>` (`<strong>LSTM</strong>`)[11](#hcbia8m5.html#n4upl4fndkh) and `<strong>Gated Recurrent Units</strong>` (`<strong>GRU</strong>`) provide additional gates to ignore inputs, outputs, or previous state values selectively. We use an LSTM to model our language identifier. The model may look like the following. The complete code can be obtained from the associated Jupyter notebook.

`<strong>function build_model(args)</strong>`

`<strong>return LSTM(args.alphabet_len, args.langs_len)</strong>`

`<strong>end</strong>`

`<strong>function model(x, scanner)</strong>`

`<strong>return scanner.(x.data)[end]</strong>`

`<strong>end</strong>`

The `<strong>build_model</strong>` creates a scanner that scans the character sequence and produces a sequence of output. However, we are only interested in the last value of the sequence and use it for the loss computation. Training for about 5 epochs the best test accuracy obtained was 0.78. While it is reasonable for such a simple model, the state of art is almost 99.8% on USENET groups for 8 languages[12](#hcbia8m5.html#n4upl4fndki). Moreover, just like other primitives, RNN, LSTM or GRU can be stacked in layers to form complex deep networks. They can also be stacked with CNNs and Dense networks as well. Transformers[13](#hcbia8m5.html#n4upl4fndkj) are useful sequence modeling primitives, extensively used for language modeling. BERT and GPT are some of the well-known transformer-based architectures.

# 

`<strong>ANNs</strong>` are being used widely in the industry today. The applications are currently seen in all the domains possible. We did a quick review of the examples provided as a part of the model zoo. While the examples provide some insights into the modeling capability of Flux, you will need to explore further details in understanding deep learning theories and trying to solve real-life problems using Flux to be able to be effective at building models with it.

# 

1.  In the example for fully connected network, softmax is not used as the activation function on the final layer. However, the same has been accommodated by some alternate means. Can you identify it?
2.  What is batch normalization? Why is it used in CNNs?
3.  We saw CNNs being used with 2-D kernels and on images. Can CNNs be used on text? What kind of changes you will have to introduce to use them for text?
4.  Compute the parameters needed for the LSTM based language identification problem. Is the increase in the number of parameters justified?
5.  Review the survey paper of language identification models and implement one of the models that can provide 99% or more accuracy on the test set using Flux.

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

[1](#hcbia8m5.html#n4upl4fndkk) Seung-Hwan Lim, Steven Robert Young, and Robert Patton, An analysis of image storage systems for scalable training of deep neural networks, The Seventh workshop on Big Data Benchmarks, Performance Optimization, and Emerging Hardware (in conjunction with ASPLOS'16), 2016.

[2](#hcbia8m5.html#n4upl4fndkl) Lecun et al., THE MNIST DATABASE of handwritten digits, **[http://yann.lecun.com/exdb/mnist/index.html](http://yann.lecun.com/exdb/mnist/index.html)**

[3](#hcbia8m5.html#n4upl4fndkm) The choice of non-linear function is problem dependent. In CNNs, Rectilinear Unit, *LU(x) = x if x > 0 else 0*, is commonly used as activation function.

[4](#hcbia8m5.html#n4upl4fndkn) Goodfellow et al., The Deep Learning Book, page 200, **[https://www.deeplearningbook.org/contents/mlp.html#pf25](https://www.deeplearningbook.org/contents/mlp.html#pf25)**

[5](#hcbia8m5.html#n4upl4fndko) Flux, The Elegant Machine Learning Stack, **[https://fluxml.ai/](https://fluxml.ai/)**

[6](#hcbia8m5.html#n4upl4fndkp) TensorFlow, A Julia wrapper for TensorFlow, The package is under a minimal maintenance mode with no new feature being added and is bound to an older version of `libtensorflow` **[https://github.com/malmaud/TensorFlow.jl](https://github.com/malmaud/TensorFlow.jl)**

[7](#hcbia8m5.html#n4upl4fndkq) model-zoo, Do not feed the models, **[https://github.com/FluxML/model-zoo](https://github.com/FluxML/model-zoo)**

[8](#hcbia8m5.html#n4upl4fndkr) `Metalhead.jl`, Computer vision models for Flux, **[https://github.com/FluxML/Metalhead.jl](https://github.com/FluxML/Metalhead.jl)**

[9](#hcbia8m5.html#n4upl4fndks) Dan Ciresan, Ueli Meier, Jurgen Schmidhuber, Multi-column Deep Neural Networks for Image Classification, Technical Report No. IDSIA-04-12

[10](#hcbia8m5.html#n4upl4fndkt) For a detailed understanding of the RNN concepts you can refer to the blog post at: **[http://www.wildml.com/2015/09/recurrent-neural-networks-tutorial-part-1-introduction-to-rnns/](http://www.wildml.com/2015/09/recurrent-neural-networks-tutorial-part-1-introduction-to-rnns/)** by Denny Britz, September 2015

[11](#hcbia8m5.html#n4upl4fndku) Christpher Olah, Understanding LSTM Networks, August 2015. **[http://colah.github.io/posts/2015-08-Understanding-LSTMs/](http://colah.github.io/posts/2015-08-Understanding-LSTMs/)**

[12](#hcbia8m5.html#n4upl4fndkv) Tommi Jauhiainen et al, Automatic language identification in texts: a survey, JAIR, May 2019, **[https://doi.org/10.1613/jair.1.11675](https://doi.org/10.1613/jair.1.11675)**

[13](#hcbia8m5.html#n4upl4fndkw) Transformers, Julia Implementation of Transformer models, **[https://github.com/chengchingwen/Transformers.jl/](https://github.com/chengchingwen/Transformers.jl/)**

Seung-Hwan Lim, Steven Robert Young, and Robert Patton, An analysis of image storage systems for scalable training of deep neural networks, The Seventh workshop on Big Data Benchmarks, Performance Optimization, and Emerging Hardware (in conjunction with ASPLOS'16), 2016.

Lecun et al., THE MNIST DATABASE of handwritten digits, **[http://yann.lecun.com/exdb/mnist/index.html](http://yann.lecun.com/exdb/mnist/index.html)**

The choice of non-linear function is problem dependent. In CNNs, Rectilinear Unit, *LU(x) = x if x > 0 else 0*, is commonly used as activation function.

Goodfellow et al., The Deep Learning Book, page 200, **[https://www.deeplearningbook.org/contents/mlp.html#pf25](https://www.deeplearningbook.org/contents/mlp.html#pf25)**

Flux, The Elegant Machine Learning Stack, **[https://fluxml.ai/](https://fluxml.ai/)**

TensorFlow, A Julia wrapper for TensorFlow, The package is under a minimal maintenance mode with no new feature being added and is bound to an older version of `libtensorflow` **[https://github.com/malmaud/TensorFlow.jl](https://github.com/malmaud/TensorFlow.jl)**

model-zoo, Do not feed the models, **[https://github.com/FluxML/model-zoo](https://github.com/FluxML/model-zoo)**

`Metalhead.jl`, Computer vision models for Flux, **[https://github.com/FluxML/Metalhead.jl](https://github.com/FluxML/Metalhead.jl)**

Dan Ciresan, Ueli Meier, Jurgen Schmidhuber, Multi-column Deep Neural Networks for Image Classification, Technical Report No. IDSIA-04-12

The `<strong>build_model</strong>` creates a scanner that scans the character sequence and produces a sequence of output. However, we are only interested in the last value of the sequence and use it for the loss computation. Training for about 5 epochs the best test accuracy obtained was 0.78. While it is reasonable for such a simple model, the state of art is almost 99.8% on USENET groups for 8 languages12. Moreover, just like other primitives, RNN, LSTM or GRU can be stacked in layers to form complex deep networks. They can also be stacked with CNNs and Dense networks as well. Transformers13 are useful sequence modeling primitives, extensively used for language modeling. BERT and GPT are some of the well-known transformer-based architectures.

The `<strong>build_model</strong>` creates a scanner that scans the character sequence and produces a sequence of output. However, we are only interested in the last value of the sequence and use it for the loss computation. Training for about 5 epochs the best test accuracy obtained was 0.78. While it is reasonable for such a simple model, the state of art is almost 99.8% on USENET groups for 8 languages12. Moreover, just like other primitives, RNN, LSTM or GRU can be stacked in layers to form complex deep networks. They can also be stacked with CNNs and Dense networks as well. Transformers13 are useful sequence modeling primitives, extensively used for language modeling. BERT and GPT are some of the well-known transformer-based architectures.

RNNs10 are used to solve problems of sequences. For example, text and voice involve a sequence of words or characters or voice phonemes. They have a meaningful context due to the order in which the tokens appear. Similarly, the output can also be sequenced themselves. For example, guessing the next word given a sequence of words like a fill in the blanks exercise.

RNN while a useful tool may not be the best option for large sequences. As the sequence gets longer the gradients may vanish and back-propagation may not be able to update the weights effectively. So slowly the earlier inputs from the sequence are forgotten by the network. Networks like `<strong>Long Short Term Memory</strong>` (`<strong>LSTM</strong>`)11 and `<strong>Gated Recurrent Units</strong>` (`<strong>GRU</strong>`) provide additional gates to ignore inputs, outputs, or previous state values selectively. We use an LSTM to model our language identifier. The model may look like the following. The complete code can be obtained from the associated Jupyter notebook.

The system operates to find the best values of that shall minimize the losses. Back-propagation using gradient descent is used as the most common technique to update the weights4. We shall not be detailing the neural network concepts here but expect the readers to refer to the more authoritative text in the interest of elaborate mathematical treatment needed on this topic. However, our focus in this chapter will be to introduce the reader to the `<strong>Flux</strong>`5 package that provides elaborate modeling primitives for deep learning or other machine learning applications.

 can be explained mathematically by the following equations. A non-linear activation function (σ)3 may be applied at each layer.

Flux is a platform designed to model machine learning problems. The modeling capabilities can be thought of as similar to *Tensorflow*6 or *PyTorch*. Flux utilizes many of the standard Julia capabilities like macros, `<strong>Automated Differentiation</strong>` (`<strong>AD</strong>`) with `<strong>Zygote</strong>`, GPU based computation with the package `<strong>CUDA</strong>`. It also utilizes `<strong>DataLoader</strong>` to lazy load and batch process data needed for computation. While Flux may seem like a simple package, it has many interesting usage of macros and may be used as a good sample code to understand advanced Julia programming.

The system operates to find the best values of that shall minimize the losses. Back-propagation using gradient descent is used as the most common technique to update the weights4. We shall not be detailing the neural network concepts here but expect the readers to refer to the more authoritative text in the interest of elaborate mathematical treatment needed on this topic. However, our focus in this chapter will be to introduce the reader to the `<strong>Flux</strong>`5 package that provides elaborate modeling primitives for deep learning or other machine learning applications.

Machine learning is time consuming and laborious process. Developing good quality models, relevant datasets, and parameter tuning to showcase results can be quite substantial even for advanced data scientists. Hence, it is important to have a collection of good quality samples that can be used as references for developing other models. Model Zoo7 for `<strong>Flux</strong>` started on the same premise. There are samples for a representative class of problems that data scientists can look at to design their own models. Note that the problems are representational and for learning purposes only. They may not be the most performance optimal code. `<strong>Flux</strong>` provides a general purpose modeling framework. For specific image classification problems, one may look at packages like `<strong>Metalhead</strong>`8.

Machine learning is time consuming and laborious process. Developing good quality models, relevant datasets, and parameter tuning to showcase results can be quite substantial even for advanced data scientists. Hence, it is important to have a collection of good quality samples that can be used as references for developing other models. Model Zoo7 for `<strong>Flux</strong>` started on the same premise. There are samples for a representative class of problems that data scientists can look at to design their own models. Note that the problems are representational and for learning purposes only. They may not be the most performance optimal code. `<strong>Flux</strong>` provides a general purpose modeling framework. For specific image classification problems, one may look at packages like `<strong>Metalhead</strong>`8.

CNNs are fundamentally driven from the concept of classic convolution and feature engineering of image processing. Image processing engineers would design convolution kernels and apply them over an image to extract features from the images. For example, edge extraction using Sobel filters. Neural networks could be used as a means to compute the filter parameters9 in an automated fashion; thus became the foundation of the CNN models:

Christpher Olah, Understanding LSTM Networks, August 2015. **[http://colah.github.io/posts/2015-08-Understanding-LSTMs/](http://colah.github.io/posts/2015-08-Understanding-LSTMs/)**

For a detailed understanding of the RNN concepts you can refer to the blog post at: **[http://www.wildml.com/2015/09/recurrent-neural-networks-tutorial-part-1-introduction-to-rnns/](http://www.wildml.com/2015/09/recurrent-neural-networks-tutorial-part-1-introduction-to-rnns/)** by Denny Britz, September 2015

Transformers, Julia Implementation of Transformer models, **[https://github.com/chengchingwen/Transformers.jl/](https://github.com/chengchingwen/Transformers.jl/)**

Tommi Jauhiainen et al, Automatic language identification in texts: a survey, JAIR, May 2019, **[https://doi.org/10.1613/jair.1.11675](https://doi.org/10.1613/jair.1.11675)**

**Figure 17.1:** Sample images1 from the MNIST dataset2. Images are classified as digits they represent. The dataset contains 60,000 images of training and 10,000 images for testing. The images are black and white are of in size. The handwriting data is obtained from almost 500 distinct writers

**Figure 17.1:** Sample images1 from the MNIST dataset2. Images are classified as digits they represent. The dataset contains 60,000 images of training and 10,000 images for testing. The images are black and white are of in size. The handwriting data is obtained from almost 500 distinct writers

# 

Symbols

8-queens problem

about

functions [55](#0pdg2cas.html#n4upl4fndax)

operators

A

abstract array types , [122](#0pdg2cas.html#n4upl4fnday)

AbstractChar

AbstractString , [145](#0pdg2cas.html#n4upl4fndaz)

Abstract Syntax Trees (AST) [149](#0pdg2cas.html#n4upl4fnda0), [150](#0pdg2cas.html#n4upl4fnda1)

abstract type [28](#0pdg2cas.html#n4upl4fnda2)

accessor method [218](#0pdg2cas.html#n4upl4fnda3)

Amazon Web Services [304](#0pdg2cas.html#n4upl4fnda4), [305](#0pdg2cas.html#n4upl4fnda5)

American National Standard Institute (ANSI) [129](#0pdg2cas.html#n4upl4fnda6)

American Standard Code for Information Interchange (ASCII) [129](#0pdg2cas.html#n4upl4fnda6)

anonymous function [57](#0pdg2cas.html#n4upl4fnda7)

Any type , [33](#0pdg2cas.html#n4upl4fnda8)

area method [71](#0pdg2cas.html#n4upl4fnda9)

array [85](#0pdg2cas.html#n4upl4fndba)

array inner product

Artificial Neural Networks (ANN)

aspect\_ratio method [71](#0pdg2cas.html#n4upl4fnda9)

assignment

associative collection

about [92](#0pdg2cas.html#n4upl4fndbb)

dict object [92](#0pdg2cas.html#n4upl4fndbb), [93](#0pdg2cas.html#n4upl4fndbc)

set object

asynchronous programming

about [174](#0pdg2cas.html#n4upl4fndbd), [175](#0pdg2cas.html#n4upl4fndbe)

channel , [178](#0pdg2cas.html#n4upl4fndbf)

lock [178](#0pdg2cas.html#n4upl4fndbf)

task [176](#0pdg2cas.html#n4upl4fndbg)

Atom , [256](#0pdg2cas.html#n4upl4fndbh)

Automated Differentiation (AD) [340](#0pdg2cas.html#n4upl4fndbi)

Azure Kubernetes Services (AKS)

about [301](#0pdg2cas.html#n4upl4fndbj)

orchestrating, from Julia [302](#0pdg2cas.html#n4upl4fndbk)\-[304](#0pdg2cas.html#n4upl4fnda4)

B

backends [321](#0pdg2cas.html#n4upl4fndbl)

benchmarking [226](#0pdg2cas.html#n4upl4fndbm)\-[229](#0pdg2cas.html#n4upl4fndbn)

Binary Coded Decimal Interchange Code (EBCDIC) [129](#0pdg2cas.html#n4upl4fnda6)

binary dependencies

about [289](#0pdg2cas.html#n4upl4fndbo)

native binaries, using [290](#0pdg2cas.html#n4upl4fndbp)

bit type

Bool [27](#0pdg2cas.html#n4upl4fndbq)

broadcast

about , [117](#0pdg2cas.html#n4upl4fndbr)

performance [118](#0pdg2cas.html#n4upl4fndbs)

versus map [118](#0pdg2cas.html#n4upl4fndbs)

C

C encoding

character array [143](#0pdg2cas.html#n4upl4fndbt)

character (Char)

characters , [129](#0pdg2cas.html#n4upl4fnda6)

cloud environment [296](#0pdg2cas.html#n4upl4fndbu),

code generation tools

about [229](#0pdg2cas.html#n4upl4fndbn)

allocations [234](#0pdg2cas.html#n4upl4fndbv), [235](#0pdg2cas.html#n4upl4fndbw)

code, removing [236](#0pdg2cas.html#n4upl4fndbx),

parametric data types [235](#0pdg2cas.html#n4upl4fndbw), [236](#0pdg2cas.html#n4upl4fndbx)

type stability [229](#0pdg2cas.html#n4upl4fndbn), [231](#0pdg2cas.html#n4upl4fndby), [233](#0pdg2cas.html#n4upl4fndbz), [234](#0pdg2cas.html#n4upl4fndbv)

code-run-fix , [262](#0pdg2cas.html#n4upl4fndb0)

Command Line Interface (CLI) [301](#0pdg2cas.html#n4upl4fndbj)

Comma separated values (CSV) [186](#0pdg2cas.html#n4upl4fndb1)

compound statements

about [40](#0pdg2cas.html#n4upl4fndb2)

begin end [40](#0pdg2cas.html#n4upl4fndb2)

comprehensions [101](#0pdg2cas.html#n4upl4fndb3), [102](#0pdg2cas.html#n4upl4fndb4)

compressed sparse column (CSC) [124](#0pdg2cas.html#n4upl4fndb5)

conditional statements

about [40](#0pdg2cas.html#n4upl4fndb2)

if else [40](#0pdg2cas.html#n4upl4fndb2), [41](#0pdg2cas.html#n4upl4fndb6)

switch case [41](#0pdg2cas.html#n4upl4fndb6)\-

unstructured branching , [44](#0pdg2cas.html#n4upl4fndb7)

constants , [190](#0pdg2cas.html#n4upl4fndb8), [191](#0pdg2cas.html#n4upl4fndb9)

constructors

about , , [70](#0pdg2cas.html#n4upl4fndca), [87](#0pdg2cas.html#n4upl4fndcb), [88](#0pdg2cas.html#n4upl4fndcc)

return value [70](#0pdg2cas.html#n4upl4fndca)

container [106](#0pdg2cas.html#n4upl4fndcd), [107](#0pdg2cas.html#n4upl4fndce)

continuous integration

about [283](#0pdg2cas.html#n4upl4fndcf)\-[287](#0pdg2cas.html#n4upl4fndcg)

code coverage, visualizing [288](#0pdg2cas.html#n4upl4fndch)

convolutional network (CNN) [346](#0pdg2cas.html#n4upl4fndci)\-[349](#0pdg2cas.html#n4upl4fndcj)

custom string literals [158](#0pdg2cas.html#n4upl4fndck), [159](#0pdg2cas.html#n4upl4fndcl)

custom strings

about

AbstractChar

AbstractString , [145](#0pdg2cas.html#n4upl4fndaz)

D

data environment

setting up [308](#0pdg2cas.html#n4upl4fndcm)

data types

about [68](#0pdg2cas.html#n4upl4fndcn)

multiple dispatch

data visualization [319](#0pdg2cas.html#n4upl4fndco)\-[321](#0pdg2cas.html#n4upl4fndbl)

debugging

about [258](#0pdg2cas.html#n4upl4fndcp)

assert

line debugging, in IDE [260](#0pdg2cas.html#n4upl4fndcq),

log

print

REPL tool, using , [260](#0pdg2cas.html#n4upl4fndcq)

unit tests

decreasing ranges , [85](#0pdg2cas.html#n4upl4fndba)

deep learning -[340](#0pdg2cas.html#n4upl4fndbi)

default streams

about

binary I/O [184](#0pdg2cas.html#n4upl4fndcr)

file I/O [184](#0pdg2cas.html#n4upl4fndcr)\-[186](#0pdg2cas.html#n4upl4fndb1)

text I/O , [183](#0pdg2cas.html#n4upl4fndcs)

Defined Languages (UDL) [254](#0pdg2cas.html#n4upl4fndct)

delegation , [218](#0pdg2cas.html#n4upl4fnda3)

dict object

about [92](#0pdg2cas.html#n4upl4fndbb), [93](#0pdg2cas.html#n4upl4fndbc)

get method [93](#0pdg2cas.html#n4upl4fndbc), [94](#0pdg2cas.html#n4upl4fndcu)

hashing [94](#0pdg2cas.html#n4upl4fndcu)

setindex method [94](#0pdg2cas.html#n4upl4fndcu)

dimension [107](#0pdg2cas.html#n4upl4fndce), [108](#0pdg2cas.html#n4upl4fndcv)

distributed computing [175](#0pdg2cas.html#n4upl4fndbe), [181](#0pdg2cas.html#n4upl4fndcw)

documentation

about [278](#0pdg2cas.html#n4upl4fndcx), [279](#0pdg2cas.html#n4upl4fndcy)

configuring [279](#0pdg2cas.html#n4upl4fndcy)\-[283](#0pdg2cas.html#n4upl4fndcf)

Document Object Models (DOM) [309](#0pdg2cas.html#n4upl4fndcz)

E

editor integration

about [250](#0pdg2cas.html#n4upl4fndc0)

emacs [251](#0pdg2cas.html#n4upl4fndc1)\-[253](#0pdg2cas.html#n4upl4fndc2)

Notepad++ [253](#0pdg2cas.html#n4upl4fndc2), [254](#0pdg2cas.html#n4upl4fndct)

vim (vi) [250](#0pdg2cas.html#n4upl4fndc0)

efficiency [125](#0pdg2cas.html#n4upl4fndc3)

Elastic Kubernetes Services (EKS) [301](#0pdg2cas.html#n4upl4fndbj)

emacs [251](#0pdg2cas.html#n4upl4fndc1)\-[253](#0pdg2cas.html#n4upl4fndc2)

encoding

about [129](#0pdg2cas.html#n4upl4fnda6), [141](#0pdg2cas.html#n4upl4fndc4), [142](#0pdg2cas.html#n4upl4fndc5)

function [142](#0pdg2cas.html#n4upl4fndc5), [143](#0pdg2cas.html#n4upl4fndbt)

end-to-end sequence labeling

exception handling

about

exception information , [51](#0pdg2cas.html#n4upl4fndc6)

finally

rethrow [49](#0pdg2cas.html#n4upl4fndc7),

throw [49](#0pdg2cas.html#n4upl4fndc7),

try catch [49](#0pdg2cas.html#n4upl4fndc7)

extractive summarization

about [333](#0pdg2cas.html#n4upl4fndc8)

evaluation metrics

F

FileIO [308](#0pdg2cas.html#n4upl4fndcm), [309](#0pdg2cas.html#n4upl4fndcz)

Filesystem [172](#0pdg2cas.html#n4upl4fndc9)\-[174](#0pdg2cas.html#n4upl4fndbd)

floating point numbers [27](#0pdg2cas.html#n4upl4fndbq)

Flux [340](#0pdg2cas.html#n4upl4fndbi)\-[343](#0pdg2cas.html#n4upl4fndda)

font and glyphs [132](#0pdg2cas.html#n4upl4fnddb)

for loop [96](#0pdg2cas.html#n4upl4fnddc), [97](#0pdg2cas.html#n4upl4fnddd)

for statement

about [44](#0pdg2cas.html#n4upl4fndb7), [45](#0pdg2cas.html#n4upl4fndde)

continue and break [45](#0pdg2cas.html#n4upl4fndde)

do while

for in

multiple range objects , [47](#0pdg2cas.html#n4upl4fnddf)

while [47](#0pdg2cas.html#n4upl4fnddf)

fully connected network

function

about [55](#0pdg2cas.html#n4upl4fndax), [156](#0pdg2cas.html#n4upl4fnddg)

collect

constructors [87](#0pdg2cas.html#n4upl4fndcb), [88](#0pdg2cas.html#n4upl4fndcc)

fill and similar

hcat [91](#0pdg2cas.html#n4upl4fnddh), [92](#0pdg2cas.html#n4upl4fndbb)

hvcat [91](#0pdg2cas.html#n4upl4fnddh), [92](#0pdg2cas.html#n4upl4fndbb)

reshape , [91](#0pdg2cas.html#n4upl4fnddh)

true and false

vcat [91](#0pdg2cas.html#n4upl4fnddh), [92](#0pdg2cas.html#n4upl4fndbb)

zeros and ones

functional programming principles

about [207](#0pdg2cas.html#n4upl4fnddi)

declarative programming

functions, with no side effects

higher-order functions

immutability , [211](#0pdg2cas.html#n4upl4fnddj)

function do [97](#0pdg2cas.html#n4upl4fnddd), [98](#0pdg2cas.html#n4upl4fnddk)

G

Gated Recurrent Units (GRU) [350](#0pdg2cas.html#n4upl4fnddl)

generated functions [159](#0pdg2cas.html#n4upl4fndcl), [160](#0pdg2cas.html#n4upl4fnddm)

generators [101](#0pdg2cas.html#n4upl4fndb3), [102](#0pdg2cas.html#n4upl4fndb4)

GitHub

registration [273](#0pdg2cas.html#n4upl4fnddn)

Git Repositories [265](#0pdg2cas.html#n4upl4fnddo)

Google Clouds Platform (GCP) [305](#0pdg2cas.html#n4upl4fnda5)

Google Kubernetes Engine (GKE) [301](#0pdg2cas.html#n4upl4fndbj)

Graphical User Interfaces (GUI) [222](#0pdg2cas.html#n4upl4fnddp)

H

high-performance code

global variables [243](#0pdg2cas.html#n4upl4fnddq)\-[245](#0pdg2cas.html#n4upl4fnddr)

guidelines [240](#0pdg2cas.html#n4upl4fndds)

memoization [240](#0pdg2cas.html#n4upl4fndds)\-[243](#0pdg2cas.html#n4upl4fnddq)

I

idle loop processing [223](#0pdg2cas.html#n4upl4fnddt)

image data , [317](#0pdg2cas.html#n4upl4fnddu)

Imperative Programming [207](#0pdg2cas.html#n4upl4fnddi)

indexing ,

index types

assignment

Boolean index [112](#0pdg2cas.html#n4upl4fnddv)

Cartesian index [111](#0pdg2cas.html#n4upl4fnddw), [112](#0pdg2cas.html#n4upl4fnddv)

interface , [114](#0pdg2cas.html#n4upl4fnddx)

linear index [111](#0pdg2cas.html#n4upl4fnddw)

ranges , [110](#0pdg2cas.html#n4upl4fnddy)

scalars

special indices

vectors [110](#0pdg2cas.html#n4upl4fnddy), [111](#0pdg2cas.html#n4upl4fnddw)

inline evaluation [152](#0pdg2cas.html#n4upl4fnddz)

Input and Output (I/O)

about

default streams

delimited files [186](#0pdg2cas.html#n4upl4fndb1)

memory and I/O [189](#0pdg2cas.html#n4upl4fndd0), [190](#0pdg2cas.html#n4upl4fndb8)

network communication -[189](#0pdg2cas.html#n4upl4fndd0)

input arguments

about [57](#0pdg2cas.html#n4upl4fnda7)

default values [59](#0pdg2cas.html#n4upl4fndd1)

fixed arguments length [57](#0pdg2cas.html#n4upl4fnda7), [58](#0pdg2cas.html#n4upl4fndd2)

slurping

splatting

variable number of arguments [58](#0pdg2cas.html#n4upl4fndd2), [59](#0pdg2cas.html#n4upl4fndd1)

integral type [27](#0pdg2cas.html#n4upl4fndbq)

integrated development environment (IDE)

about , [254](#0pdg2cas.html#n4upl4fndct)

Atom , [256](#0pdg2cas.html#n4upl4fndbh)

Visual Studio Code (VS Code) , [258](#0pdg2cas.html#n4upl4fndcp)

Interactive Julia (IJulia) [16](#0pdg2cas.html#n4upl4fndd3)

interface

about , [114](#0pdg2cas.html#n4upl4fnddx), [211](#0pdg2cas.html#n4upl4fnddj), [212](#0pdg2cas.html#n4upl4fndd4)

holy traits [214](#0pdg2cas.html#n4upl4fndd5)\-[216](#0pdg2cas.html#n4upl4fndd6)

super type [212](#0pdg2cas.html#n4upl4fndd4)\-[214](#0pdg2cas.html#n4upl4fndd5)

interned strings [150](#0pdg2cas.html#n4upl4fnda1), [151](#0pdg2cas.html#n4upl4fndd7)

interpolation [152](#0pdg2cas.html#n4upl4fnddz), [154](#0pdg2cas.html#n4upl4fndd8)\-[156](#0pdg2cas.html#n4upl4fnddg)

ISO-8859

iterate methods [99](#0pdg2cas.html#n4upl4fndd9)

iteration

about [96](#0pdg2cas.html#n4upl4fnddc)

for loop [96](#0pdg2cas.html#n4upl4fnddc), [97](#0pdg2cas.html#n4upl4fnddd)

function do [97](#0pdg2cas.html#n4upl4fnddd), [98](#0pdg2cas.html#n4upl4fnddk)

iteration framework

about [98](#0pdg2cas.html#n4upl4fnddk), [99](#0pdg2cas.html#n4upl4fndd9)

example [100](#0pdg2cas.html#n4upl4fndea), [101](#0pdg2cas.html#n4upl4fndb3)

iterative statements

about [44](#0pdg2cas.html#n4upl4fndb7)

for statement [44](#0pdg2cas.html#n4upl4fndb7), [45](#0pdg2cas.html#n4upl4fndde)

J

Julia

Azure Kubernetes Services (AKS), orchestrating [302](#0pdg2cas.html#n4upl4fndbk)\-[304](#0pdg2cas.html#n4upl4fnda4)

deploying , [298](#0pdg2cas.html#n4upl4fndeb)

Docker container [299](#0pdg2cas.html#n4upl4fndec), [300](#0pdg2cas.html#n4upl4fnded)

REST-based web services [298](#0pdg2cas.html#n4upl4fndeb), [299](#0pdg2cas.html#n4upl4fndec)

Julia built-in types

about [26](#0pdg2cas.html#n4upl4fndee)

character (Char)

nothing [26](#0pdg2cas.html#n4upl4fndee)

numeric type [27](#0pdg2cas.html#n4upl4fndbq)

string

Julia concepts

about

active community [6](#0pdg2cas.html#n4upl4fndef)

advantage

design for researcher [3](#0pdg2cas.html#n4upl4fndeg), [4](#0pdg2cas.html#n4upl4fndeh)

development toolset [4](#0pdg2cas.html#n4upl4fndeh)

enterprise-friendly architecture [6](#0pdg2cas.html#n4upl4fndef)

flexible licensing

integration, with platforms [3](#0pdg2cas.html#n4upl4fndeg)

metaprogramming [4](#0pdg2cas.html#n4upl4fndeh)

modern programming language , [3](#0pdg2cas.html#n4upl4fndeg)

open source

package ecosystem

performance

server platform

Julia language

about

arrays [9](#0pdg2cas.html#n4upl4fndei)

collections [9](#0pdg2cas.html#n4upl4fndei)

conditions

control flow

data types

functions and methods , [9](#0pdg2cas.html#n4upl4fndei)

installer binaries, downloading

installer binaries, for Linux

installer binaries, for Windows , [15](#0pdg2cas.html#n4upl4fndej)

iterations

metaprogramming [10](#0pdg2cas.html#n4upl4fndek)

modules -[169](#0pdg2cas.html#n4upl4fndel)

overview

runtime environment, elaborating

setting up

standard libraries [10](#0pdg2cas.html#n4upl4fndek)

standard modules [169](#0pdg2cas.html#n4upl4fndel), [170](#0pdg2cas.html#n4upl4fndem)

strings [9](#0pdg2cas.html#n4upl4fndei)

version

Julia language, development environment

about [10](#0pdg2cas.html#n4upl4fndek)

debugging

deployment

IDE

package management

performance management

programming guidelines [10](#0pdg2cas.html#n4upl4fndek)

Julia language, packages

about

data transformation

deep learning

text analytics

Julia performance

about [222](#0pdg2cas.html#n4upl4fnddp)

algorithm [224](#0pdg2cas.html#n4upl4fnden), [225](#0pdg2cas.html#n4upl4fndeo)

cloud computing resources [224](#0pdg2cas.html#n4upl4fnden)

optimization [225](#0pdg2cas.html#n4upl4fndeo)

optimizing [222](#0pdg2cas.html#n4upl4fnddp)\-[224](#0pdg2cas.html#n4upl4fnden)

runtime, comparing [225](#0pdg2cas.html#n4upl4fndeo), [226](#0pdg2cas.html#n4upl4fndbm)

Julia programs [18](#0pdg2cas.html#n4upl4fndep)

Julia type

about

constants

literals

tuples [25](#0pdg2cas.html#n4upl4fndeq)

variables , [23](#0pdg2cas.html#n4upl4fnder)

Jupyter

about [16](#0pdg2cas.html#n4upl4fndd3)

configuring [17](#0pdg2cas.html#n4upl4fndes)

Just-in-Time (JIT) compilation ,

K

Kubernetes [300](#0pdg2cas.html#n4upl4fnded)\-[302](#0pdg2cas.html#n4upl4fndbk)

L

Latent Dirichlet Allocation (LDA)

Latent Semantic Analysis (LSA)

linear algebra [125](#0pdg2cas.html#n4upl4fndc3), [126](#0pdg2cas.html#n4upl4fndet)

linear index [111](#0pdg2cas.html#n4upl4fnddw)

literals

Long Short Term Memory (LSTM) [350](#0pdg2cas.html#n4upl4fnddl)

long-term support (LTS) [6](#0pdg2cas.html#n4upl4fndef)

l-valued expressions

M

macros

about [156](#0pdg2cas.html#n4upl4fnddg), [160](#0pdg2cas.html#n4upl4fnddm)

assert [162](#0pdg2cas.html#n4upl4fndeu)

calling convention , [158](#0pdg2cas.html#n4upl4fndck)

eval [161](#0pdg2cas.html#n4upl4fndev)

source locations [160](#0pdg2cas.html#n4upl4fnddm), [161](#0pdg2cas.html#n4upl4fndev)

time [163](#0pdg2cas.html#n4upl4fndew)

maintainability guidelines

about -[204](#0pdg2cas.html#n4upl4fndex)

coding style [204](#0pdg2cas.html#n4upl4fndex)\-[207](#0pdg2cas.html#n4upl4fnddi)

map

versus broadcast [118](#0pdg2cas.html#n4upl4fndbs)

mapreduce [120](#0pdg2cas.html#n4upl4fndey)

members

memoization [240](#0pdg2cas.html#n4upl4fndds)

memory layout

metaprogramming , [149](#0pdg2cas.html#n4upl4fnda0)

Microsoft Azure [305](#0pdg2cas.html#n4upl4fnda5)

Microsoft office documents [313](#0pdg2cas.html#n4upl4fndez)\-[315](#0pdg2cas.html#n4upl4fnde0)

model zoo

module

about

usage

multiline expression [152](#0pdg2cas.html#n4upl4fnddz)\-[154](#0pdg2cas.html#n4upl4fndd8)

multithreading [175](#0pdg2cas.html#n4upl4fndbe), [178](#0pdg2cas.html#n4upl4fndbf)\-[180](#0pdg2cas.html#n4upl4fnde1)

mutable struct

N

Naïve Bayes Classifier [332](#0pdg2cas.html#n4upl4fnde2)

Named Entity Recognition (NER) , [335](#0pdg2cas.html#n4upl4fnde3)

nested quotes [154](#0pdg2cas.html#n4upl4fndd8)\-[156](#0pdg2cas.html#n4upl4fnddg)

network

neural network, types

about

convolutional network (CNN) [346](#0pdg2cas.html#n4upl4fndci)\-[349](#0pdg2cas.html#n4upl4fndcj)

fully connected network -[346](#0pdg2cas.html#n4upl4fndci)

recurrent neural network (RNN) [349](#0pdg2cas.html#n4upl4fndcj)\-[351](#0pdg2cas.html#n4upl4fnde4)

notable modules

about [191](#0pdg2cas.html#n4upl4fndb9)

dates [191](#0pdg2cas.html#n4upl4fndb9)\-[193](#0pdg2cas.html#n4upl4fnde5)

logging -[196](#0pdg2cas.html#n4upl4fnde6)

random number [196](#0pdg2cas.html#n4upl4fnde6), [197](#0pdg2cas.html#n4upl4fnde7)

statistics [196](#0pdg2cas.html#n4upl4fnde6)

Notepad++ [253](#0pdg2cas.html#n4upl4fndc2), [254](#0pdg2cas.html#n4upl4fndct)

N-queens , [268](#0pdg2cas.html#n4upl4fnde8)

NTuple [79](#0pdg2cas.html#n4upl4fnde9)

numeric type

about [27](#0pdg2cas.html#n4upl4fndbq)

abstract type [28](#0pdg2cas.html#n4upl4fnda2)

bit type

Bool [27](#0pdg2cas.html#n4upl4fndbq)

floating point numbers [27](#0pdg2cas.html#n4upl4fndbq)

integral type [27](#0pdg2cas.html#n4upl4fndbq)

primitive type

rational and complex type

O

Office Open XML (OOXML) [313](#0pdg2cas.html#n4upl4fndez)

open source

about [219](#0pdg2cas.html#n4upl4fndfa)

contributing, to Julia [220](#0pdg2cas.html#n4upl4fndfb)

operation types

about [34](#0pdg2cas.html#n4upl4fndfc)

isa

supertype

typeof

optional methods [99](#0pdg2cas.html#n4upl4fndd9), [100](#0pdg2cas.html#n4upl4fndea)

P

package

about [265](#0pdg2cas.html#n4upl4fnddo)

creating [268](#0pdg2cas.html#n4upl4fnde8)

functionality, developing [272](#0pdg2cas.html#n4upl4fndfd), [273](#0pdg2cas.html#n4upl4fnddn)

initializing -[272](#0pdg2cas.html#n4upl4fndfd)

problem statement

usage

package architecture

about -[293](#0pdg2cas.html#n4upl4fndfe)

package module

REPL command [293](#0pdg2cas.html#n4upl4fndfe)

package, characteristics

environment [266](#0pdg2cas.html#n4upl4fndff)

folder structure [266](#0pdg2cas.html#n4upl4fndff)

Git Repositories [265](#0pdg2cas.html#n4upl4fnddo)

module [266](#0pdg2cas.html#n4upl4fndff)

paging effect

parallel programming

about , [174](#0pdg2cas.html#n4upl4fndbd)

asynchronous programming [175](#0pdg2cas.html#n4upl4fndbe)

distributed computing [181](#0pdg2cas.html#n4upl4fndcw)

multithreading [178](#0pdg2cas.html#n4upl4fndbf)\-[180](#0pdg2cas.html#n4upl4fnde1)

parametric data type

about [33](#0pdg2cas.html#n4upl4fnda8), [34](#0pdg2cas.html#n4upl4fndfc), [71](#0pdg2cas.html#n4upl4fnda9)

dispatch interface [71](#0pdg2cas.html#n4upl4fnda9), [72](#0pdg2cas.html#n4upl4fndfg)

Part of Speech (POS)

patterns

about [211](#0pdg2cas.html#n4upl4fnddj)

accessor method [218](#0pdg2cas.html#n4upl4fnda3)

delegation , [218](#0pdg2cas.html#n4upl4fnda3)

interface [211](#0pdg2cas.html#n4upl4fnddj)

point coincident tolerance

polymorphic method

about [68](#0pdg2cas.html#n4upl4fndcn)

constructors , [70](#0pdg2cas.html#n4upl4fndca)

data types [68](#0pdg2cas.html#n4upl4fndcn)

parametric data type [71](#0pdg2cas.html#n4upl4fnda9)

predefined data structures

primitive type

printing data types

about , [37](#0pdg2cas.html#n4upl4fndfh)

print [37](#0pdg2cas.html#n4upl4fndfh)

show [37](#0pdg2cas.html#n4upl4fndfh)

string [37](#0pdg2cas.html#n4upl4fndfh)

profiling -[240](#0pdg2cas.html#n4upl4fndds)

project

about [265](#0pdg2cas.html#n4upl4fnddo)

usage

project environment [290](#0pdg2cas.html#n4upl4fndbp),

public cloud infrastructures

about [304](#0pdg2cas.html#n4upl4fnda4)

Amazon Web Services [304](#0pdg2cas.html#n4upl4fnda4)

Google Clouds Platform (GCP) [305](#0pdg2cas.html#n4upl4fnda5)

pull requests (PR) [220](#0pdg2cas.html#n4upl4fndfb)

R

ranges

about [83](#0pdg2cas.html#n4upl4fndfi), , [110](#0pdg2cas.html#n4upl4fnddy)

decreasing ranges , [85](#0pdg2cas.html#n4upl4fndba)

StepRange

UnitRange

rational and complex type

Read-Eval-Print Loop (REPL) [15](#0pdg2cas.html#n4upl4fndej), [16](#0pdg2cas.html#n4upl4fndd3)

Recall Oriented Understudy for Gisting Evaluation (ROUGE)

recurrent neural network (RNN) [349](#0pdg2cas.html#n4upl4fndcj)\-[351](#0pdg2cas.html#n4upl4fnde4)

recursion

about -[64](#0pdg2cas.html#n4upl4fndfj)

code, computing [65](#0pdg2cas.html#n4upl4fndfk)\-[67](#0pdg2cas.html#n4upl4fndfl)

reduction operations

about

associativity , [120](#0pdg2cas.html#n4upl4fndey)

mapreduce [120](#0pdg2cas.html#n4upl4fndey)

slices [120](#0pdg2cas.html#n4upl4fndey)

return value

about

multiple values

type safety

S

scalars

semantic analysis , [332](#0pdg2cas.html#n4upl4fnde2)

set object

about

union and intersection [96](#0pdg2cas.html#n4upl4fnddc)

short form

single dispatch interface

singleton [83](#0pdg2cas.html#n4upl4fndfi)

slicing [114](#0pdg2cas.html#n4upl4fnddx), [115](#0pdg2cas.html#n4upl4fndfm)

slurping

sparse array

about

efficiency [125](#0pdg2cas.html#n4upl4fndc3)

sparse matrix storage [124](#0pdg2cas.html#n4upl4fndb5), [125](#0pdg2cas.html#n4upl4fndc3)

sparse vector storage

sparse matrix storage [124](#0pdg2cas.html#n4upl4fndb5), [125](#0pdg2cas.html#n4upl4fndc3)

sparse vector storage

special indices

stack traces [51](#0pdg2cas.html#n4upl4fndc6)

standard library (stdlib) [186](#0pdg2cas.html#n4upl4fndb1)

StepRange

string , , [132](#0pdg2cas.html#n4upl4fnddb), [133](#0pdg2cas.html#n4upl4fndfn)

string method

about [133](#0pdg2cas.html#n4upl4fndfn)

case conversion [138](#0pdg2cas.html#n4upl4fndfo)

comparison [133](#0pdg2cas.html#n4upl4fndfn), [134](#0pdg2cas.html#n4upl4fndfp)

iteration [134](#0pdg2cas.html#n4upl4fndfp), [135](#0pdg2cas.html#n4upl4fndfq)

pattern matching

regular expression , [141](#0pdg2cas.html#n4upl4fndc4)

split and concatenate [136](#0pdg2cas.html#n4upl4fndfr)\-[138](#0pdg2cas.html#n4upl4fndfo)

struct

symbol [150](#0pdg2cas.html#n4upl4fnda1), [151](#0pdg2cas.html#n4upl4fndd7)

system shell

accessing [171](#0pdg2cas.html#n4upl4fndfs), [172](#0pdg2cas.html#n4upl4fndc9)

T

tabular data [317](#0pdg2cas.html#n4upl4fnddu)\-[319](#0pdg2cas.html#n4upl4fndco)

Tail Call Optimization (TCO) [67](#0pdg2cas.html#n4upl4fndfl)

test automation

about [274](#0pdg2cas.html#n4upl4fndft)\-[276](#0pdg2cas.html#n4upl4fndfu)

coverage [276](#0pdg2cas.html#n4upl4fndfu)\-[278](#0pdg2cas.html#n4upl4fndcx)

TextAnalysis

embeddings [329](#0pdg2cas.html#n4upl4fndfv), [330](#0pdg2cas.html#n4upl4fndfw)

preprocessing [326](#0pdg2cas.html#n4upl4fndfx)

tokenization [327](#0pdg2cas.html#n4upl4fndfy), [328](#0pdg2cas.html#n4upl4fndfz)

word representation [328](#0pdg2cas.html#n4upl4fndfz), [329](#0pdg2cas.html#n4upl4fndfv)

TextAnalysis, document types

FileDocument [326](#0pdg2cas.html#n4upl4fndfx)

NGramDocument [326](#0pdg2cas.html#n4upl4fndfx)

StringDocument [326](#0pdg2cas.html#n4upl4fndfx)

TokenDocument [326](#0pdg2cas.html#n4upl4fndfx)

text data

about [309](#0pdg2cas.html#n4upl4fndcz)

delimited files [309](#0pdg2cas.html#n4upl4fndcz)

HTML files [311](#0pdg2cas.html#n4upl4fndf0), [312](#0pdg2cas.html#n4upl4fndf1)

Microsoft office documents [313](#0pdg2cas.html#n4upl4fndez)\-[315](#0pdg2cas.html#n4upl4fnde0)

PDF files [312](#0pdg2cas.html#n4upl4fndf1), [313](#0pdg2cas.html#n4upl4fndez)

XML files [309](#0pdg2cas.html#n4upl4fndcz)\-[311](#0pdg2cas.html#n4upl4fndf0)

text processing pipeline

about [324](#0pdg2cas.html#n4upl4fndf2), [325](#0pdg2cas.html#n4upl4fndf3), [326](#0pdg2cas.html#n4upl4fndfx)

acquisition [324](#0pdg2cas.html#n4upl4fndf2)

models [325](#0pdg2cas.html#n4upl4fndf3)

representation [325](#0pdg2cas.html#n4upl4fndf3)

tokenization [325](#0pdg2cas.html#n4upl4fndf3)

Tuple

about , [79](#0pdg2cas.html#n4upl4fnde9)

as collection [79](#0pdg2cas.html#n4upl4fnde9)

integers type parameter [80](#0pdg2cas.html#n4upl4fndf4), [81](#0pdg2cas.html#n4upl4fndf5)

integer type parameter

NTuple [79](#0pdg2cas.html#n4upl4fnde9)

value parameter , [83](#0pdg2cas.html#n4upl4fndfi)

tuples [25](#0pdg2cas.html#n4upl4fndeq)

type interaction

about [72](#0pdg2cas.html#n4upl4fndfg), [73](#0pdg2cas.html#n4upl4fndf6)

conversion [73](#0pdg2cas.html#n4upl4fndf6), [74](#0pdg2cas.html#n4upl4fndf7)

promotion [74](#0pdg2cas.html#n4upl4fndf7), [75](#0pdg2cas.html#n4upl4fndf8)

U

Unicode

about

in Julia [132](#0pdg2cas.html#n4upl4fnddb)

Unicode transformation [131](#0pdg2cas.html#n4upl4fndf9), [132](#0pdg2cas.html#n4upl4fnddb)

UnitRange

Universal Coded Character Set (UCS)

Universal Language Model Fine Tuning (ULMFiT) [335](#0pdg2cas.html#n4upl4fnde3)

user-defined types

about

members

mutable struct

struct

V

variables

about , [23](#0pdg2cas.html#n4upl4fnder)

definition, versus initialization [23](#0pdg2cas.html#n4upl4fnder)

vectors [110](#0pdg2cas.html#n4upl4fnddy), [111](#0pdg2cas.html#n4upl4fnddw)

vim (vi) [250](#0pdg2cas.html#n4upl4fndc0)

Visual Studio Code (VS Code) [250](#0pdg2cas.html#n4upl4fndc0), , [258](#0pdg2cas.html#n4upl4fndcp)

W

walkdir() method [173](#0pdg2cas.html#n4upl4fndga)

word stems [328](#0pdg2cas.html#n4upl4fndfz)

`<strong>Tables.schema</strong>` method can be used to find the schema information.

The cells from the data can be accessed using Excel cell id ranges. The result shall be a Matrix.

While it may seem the memory is aligned in a 2- or 3-dimensional arrangement, it is not really that way. It all means in the images all red components are together, followed by green intensity values, and so on. Image file formats do not necessarily store data in this fashion. They apply several transformations and compress the data and store it as a binary stream of numbers. However, almost all applications of images shall convert the data to one of the above arrangements before they consume or render the image. In section FileIO, we loaded a tiff file and the image object created is of type `<strong>Array{ColorTypes.Gray{FixedPointNumbers.Normed{UInt8,8}},2}</strong>`. If we keep the complex type aside, it is just an array of 2 dimensions. The third dimension of the component types is not relevant as the gray images have just one component. The type `<strong>ColorTypes.Gray{FixedPointNumbers.Normed{UInt8,8}}</strong>` itself is quite complex in itself. Traditionally, images components are normalized as a floating-point value from 0.0 to 1.0. As floating-point number needs larger storage space, it can be represented as a byte of data where 0 maps to 0.0 and 255 to 1.0; thus a fixed-point representation of a number. In a byte of data, even all 8 bits may not be consumed by one value. And only 4 bits may be used. Thus, one byte can be used to store two-pixel intensities. `<strong>ImageCore</strong>` package has many such image representations that readers are suggested to refer to for understanding various image formats. You can use the Julia Imaging Library for image processing as well. OpenCV library provides a tutorial to integrate with a Julia frontend as well.

In the preceding examples, comprehensions are used to create a single dimension and multi-dimensional array. Following is an example where an index may depend on another.

`<strong>IteratorSize(IterType)</strong>` is a helper method that says if the iterator has a length or a shape. Based on which size or/and length methods must be defined for the collection iterator.

So we add a `<strong>length</strong>` method to achieve the same.

The starter code is given in the folder `<strong>Chapter-13/NQueens</strong>`. Two options are provided one with Jupyter notebook and the other with REPL. You can launch the application in REPL using the commands as follows:

In the example we discussed in , we have seen all the above characteristics and also realized the need to export a symbol from a module to be used inside another module. However, there are ways to access symbols using the keyword `<strong>using</strong>`.

*   **Folder Structure**: The packages are organized in a well-defined folder structure: ![](n4upl4fndrp.jpeg)
    
    **Figure 13.1:** Folder structure of package PDFIO
    
    While the `<strong>src</strong>` and `<strong>test</strong>` folders are seen in almost all packages, the folders like `<strong>deps</strong>`, `<strong>docs</strong>` and `<strong>data</strong>`, and so on may be missing in some packages. Similarly, packages that are not public may not have a `<strong>LICENCE.md</strong>` file.
    

`<strong>Plots</strong>` is an abstract plotting aggregator library that utilizes other packages like `<strong>GR</strong>`, `<strong>pyplot</strong>`, `<strong>Plotly</strong>`, and so on to render plots. These are also known as `<strong>backends</strong>`. GR is one of the fastest libraries to use for plotting and is used as the default in most Julia installations, while `<strong>pyplot (matplotlib)</strong>` is the most feature-rich backend. Plots translate the functions to the relevant backend and show the results. Readers are suggested to read the Plots documentation and tutorials for better understanding and usage scenarios.

````<strong>```</strong>````

`<strong>Expression: iscollinear(Point2D(0, 0), Point2D(10, 0), Point2D(20, 3 * ϵ()))</strong>`

`<strong>3 L(pA::Point2D, pB::Point2D, pC::Point2D) =</strong>`

`<strong>deps = ["Libdl"]</strong>`

`<strong>git add .<a id="ftn10a" href="#ftn10"><sup>10</sup></a></strong>`

`<strong>L(pA::Point2D, pB::Point2D, pC::Point2D) =</strong>`

The recursive function terminates as there is a termination condition for all values of `<strong>n &lt; 3</strong>`. The fundamental question remains if the Fibonacci sequence is valid for negative values of `<strong>n</strong>`. Having a small pure function and verifying it in the REPL makes it easier to ensure a properly running code is verified and introduced into the actual code. Running parts of code in the IDE is another way to achieve the same result.

However, adept a programmer is, she would like to try the idea in her mind, quickly experience the outcome, fix the changes, and move on with the next chunk of code. Julia's runtime is pre-loaded. As you load more data structures or modules and packages to the system, the older symbols and code blocks get loaded to the runtime. It may not be possible to modify the symbols already defined without affecting the overall working of the runtime elsewhere. For example, changing a function definition in the REPL is straightforward. But, adding or removing an attribute of a `<strong>struct</strong>` data type is not permitted. When a package is modified, it is not loaded on the subsequent usage of the command using `<strong>&lt;&lt;module&gt;&gt;</strong>`. To overcome these limitations, `<strong>Revise.jl</strong>` package may be used. This package can be autoloaded and can update symbols as part of code-run-fix cycles of development. We suggest the readers review the package documentation for a detailed understanding.

The Julia plug-in for `<strong>vim</strong>`, called `<strong>julia-vim</strong>`, is a *GitHub* project that can be installed in a `<strong>vim</strong>` set up for Mac OS X, UNIX, and Windows operating systems. The plug-in is a set of vim scripts that provide the following functionalities:

Julia is a relatively newer platform. The ecosystem for all the preceding components existed before Julia became popular as a language. Developers will like to see Julia seamlessly be used along with the tools they are most comfortable with. In the world of text editors in the UNIX environments, there is almost cult following for `<strong>vi</strong>` vs. `<strong>emacs</strong>`. JuliaEditorSupport organization under *GitHub* maintains integration with several of the well-known editors at differing levels of capabilities; some such editors being *Vim*, *Emacs*, *Sublime*, *Atom*, *Notepad++*, and *Eclipse*. Some of the integrations are active while many are deprecated due to lack of focus and usage. Julia IDEs are being developed for *Atom* under a project *Juno* and Microsoft **Visual Studio Code** (**VS Code**).

 shows the `<strong>julia-emacs</strong>` screen with Julia as a major mode while Git integration shows up as a minor mode. The functions and constants show up as menu items that can aid quick navigation within a file. Emacs integration further allows the REPL to be loaded along with the `<strong>julia-emacs</strong>`, thus loading an environment for evaluating and debugging. Julia also integrates with a package called Emacs Speaks Statistics that supports other languages like R, S-plus, SAS and Stata, and so on. The package provides granular evaluation of a Julia code block, parts of an emacs code for rapid prototyping. This helps debug and test small chunks of code independently while still developing the code:

*   Now wait for the load balancer to come up: 
    
    `<strong>while true</strong>`
    
    `<strong>println("waiting for loadbalancer to be configured…")</strong>`
    
    `<strong>status = get(ctx, :Service, "kubqueens-service").status</strong>`
    
    `<strong>if nothing !== status.loadBalancer.ingress &amp;&amp;<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;!isempty(status.loadBalancer.ingress)</strong>`
    
    `<strong>println(status.loadBalancer.ingress[1])</strong>`
    
    `<strong>break</strong>`
    
    `<strong>end</strong>`
    
    `<strong>sleep(5)</strong>`
    
    `<strong>end</strong>`
    

While we can orchestrate workloads using the Kubernetes, native platforms provide granular controls and the ability to use across a larger stack of services. They are not confined to container-based workloads only. Julia provides an extensive coverage of managing AWS-based services using the package AWS. AWS is by far the most comprehensive integration among all the public cloud infrastructures for Julia. A large part of this is due to the automated code generation using a *GitHub* action, which is executed every day at 6:00am UTC. It queries the *GitHub* repository `<strong>aws-sdk-js</strong>` repository for the REST-based APIs. This action generates the wrapper functions for AWS services in Julia. The documentation is also pulled from the AWS documentation and presented as Juliadocs. This ensures the sources can accommodate all the changes to the AWS APIs and documentations. The APIs are generally designed as two categories:

Just like `<strong>vi</strong>` and `<strong>emacs</strong>` are the most prevalent editors in the UNIX world, *Notepad++* has been a popular editor in the Windows operating systems with no direct port to the Unix or Mac OS X operating systems. However, it is not to be confused with `<strong>notepad.exe</strong>`, shipping by default in the Windows Operating Systems with bare minimal text editing. *Notepad++* is a relatively advanced text editor, has complete plug-in capabilities to program and enhance editor rendering experiences. It also has the capability of customizing language syntax highlighting through **User Defined Languages** (**UDL**). The UDLs are an easier way to provide certain syntactic structures in an XML file and can be used to identify and render the files effectively:

The Juno IDE which is the backbone of Julia integration with *Atom* is also the editor of choice for Julia PRO, the commercial offering from Julia Computing. However, with Microsoft VS Code integrations some of the focus from this editor is slowly moving away:

You can open the file `<strong>plot.jl</strong>` from the sample code in VS Code with the Julia extension installed. If you run the file by right-clicking it, you shall be able to see the following screen with the plot displayed right next to the code:

`<strong>using TextAnalysis</strong>`

`<strong>singular values:</strong>`

While `<strong>tf-idf</strong>` is a useful representation, so is one-hot vector, they have certain limitations. They are sparse and consider the count of the words in the documents. They do not take the local context of the words into consideration. For example, the word *Apple* can mean the fruit or the technology company. Hence, the surrounding words are crucial in identifying the relevant context of the homonyms.

`<strong>$docker pull julia</strong>`

*   **Elastic Kubernetes Services** (**EKS**) by Amazon Web Services *   `<strong>kubectl proxy</strong>` is useful for connecting to the Azure Kubernetes services through web services. 

Now, both sentences become easier to compare. Let us look at a similarity measure called `<strong>cos_similarity</strong>`. Before we do so we use a corpus to simplify the strings.

Similar is with word tokenization as well. The poorman’s word tokenizer behaves somewhat imperfectly.

Typically, a corpus will have similar properties across the documents; thus one can apply a common transformation on the corpus. `<strong>TextAnalysis</strong>` has a type `<strong>Corpus</strong>` that captures this concept effectively. `<strong>CorpusLoader</strong>` package can download standard text corpus and lazy loading it as and when needed.

Let us look at the sentence: Can you pass me the can? The homonym can here stand for two different meanings. Hence, the mere existence of a word in a sentence is not enough details unless the surrounding context is captured as well. This gets worse with homophones. Since, many a times the text and voice-related techniques in NLP are similar, the representation of tokens to an intermediate form definitely add significant benefits. The classic sentence: Tell me a tale about a tail will generate substantially different signatures for similar sounding phonetic tokens. More and more research is focused on picking up representations off a language model and utilizing that as input into the task models.

*   **Acquisition**: The text acquisition we discuss here is of non-structured texts obtained from web captures, reading files of various formats like MS Word or PDF from disks, social media feeds, and so on. While we discussed a part of the tasks in the previous chapter, the challenge remains in creating the level of granularity in a document. For example, a document can be as short as a Twitter feed or as large as a complete book. This distinction needs to be understood from the problem you are trying to solve. *   Evaluation metrics *   Microsoft Office Documents 

Julia has conceptually preferred a driver-like architecture in addressing a class of problems. In , we saw the `<strong>WebIO</strong>` framework where HTML5 could be rendered on various frontends utilizing a common set of functional APIs. `<strong>FileIO</strong>` is inherently a similar API framework. It helps load contents of a complete file or save it out using the framework methods `<strong>load</strong>` and `<strong>save</strong>`. Based on the underlying file type the relevant reader and writer shall be invoked and the file shall be loaded into the memory. The framework currently supports many file types. A few being: PBM, PGM, PPM, NRRD, AVI, JPG, PDF, TIFF, or a large number of image, sound, and video formats. The following code shall display an image on a Jupyter notebook:

`<strong>julia&gt; for author in nodecontent.(findall("//author/text()", doc))</strong>`

Since, the elements are of `<strong>HTMLNode</strong>` type with `<strong>parent</strong>` and `<strong>children</strong>` attributes, you shall be able to traverse them using the `<strong>AbstractTrees</strong>` interface.

`<strong>&nbsp;&nbsp;getPDFText(src, out) -&gt; Dict</strong>`

However, `<strong>Memoize.jl</strong>` package has a `<strong>@memoize</strong>` macro that can help specify if the function is memoization aware.

The highlighted portions are from the top-level function `<strong>profile_test</strong>`. The maximum time is spent on the line 5 as that has been sampled 264 times of a total of 413. You can get a better visual of the output using the package `<strong>ProfileView</strong>`. The same can be installed by using the command: `<strong>julia&gt;]add ProfileView</strong>`:

`<strong>define i64 @julia_add_to_global_ref_4338(i64) #0 {</strong>`

Forward pass of the RNN may have equations as shown:

The `<strong>build_model</strong>` creates a scanner that scans the character sequence and produces a sequence of output. However, we are only interested in the last value of the sequence and use it for the loss computation. Training for about 5 epochs the best test accuracy obtained was 0.78. While it is reasonable for such a simple model, the state of art is almost 99.8% on USENET groups for 8 languages. Moreover, just like other primitives, RNN, LSTM or GRU can be stacked in layers to form complex deep networks. They can also be stacked with CNNs and Dense networks as well. Transformers are useful sequence modeling primitives, extensively used for language modeling. BERT and GPT are some of the well-known transformer-based architectures.

Julia is developed as a collection of open-source projects. We will insist on the usage of the term collection of open-source projects as most of the packages used are distributed as open source but may have different licensing than the Julia language. The Julia language is developed under the MIT License, which provides significant flexibility in terms of using and extending the sources. The same also makes it easy for anyone to include complete Julia or its derivatives as a part of the other applications they are developing. Most packages developed in Julia also follow similar licensing schemes. Make sure you review the licensing flexibilities for the packages before you use them in your commercially licensed products.

Julia is designed for researchers who would like to see their contribution made to the production code than having to be rewritten and redesigned for performance and maintainability. The functional programming paradigm ensures any program can be easily extended using compositions than rigidly adhering to pure object-oriented hierarchies. Data encapsulation is a directive. and language constructs do not rigidly block access to underlying attributes of an object.. Multiple dispatch interfaces provide easy polymorphic designs like an object-oriented system. Like most functional programming languages, recursion programming is encouraged where needed while iterative programming is fully supported. Lack of native support for tail-call optimization can be considered a minor bottleneck. It has support for Unicode variables and native set theoretic expressions that help researchers write complete mathematical expressions in Julia. Many researchers in the community develop applications with LaTeX document management systems to be able to present their research in exportable for publications formats. Moreover, some of the works in the Julia community are published in various research publications. Interactive modes like IJulia and Jupyter provide easy prototyping alongside console-based **REPL**.

In the world of programming, where COBOL and FORTRAN programs written about half a century ago are still in existence, a decade is definitely a short period of time. Let us look at some of the competing languages such as Python (1990), R (1993), S (1976), SPSS (1968), and MATLAB (the late 1970s). None of these languages were developed with the need for a production-ready data science application development platform. Python started as a general-purpose scripting language; providing easy programming interfaces to develop quick solutions even for non-regular programmers, while R, S, SPSSS, and MATLAB provided excellent prototyping infrastructures for researchers. The first appearance in 2012 gave Julia a new kid in the block image. As you read along, you will realize Julia is really a smart brat. Maintaining backward compatibility with old systems may not be always practical. Python 3.x had many features that were incompatible with Python 2.x; putting programmers into the same level of difficulty to migrate and rewriting in a new language. Julia is modern and built with newer programming paradigms keeping researchers and data scientists in mind; yet, it integrates effortlessly with native platforms.

`<strong>julia&gt; i, l = firstindex(s), lastindex(s);</strong>`

`<strong>julia&gt; s[begin], s[begin+2], s[end-1], s[end]<br>('J', 'l', 'i', 'a')</strong>`

`<strong>split()</strong>` example uses comma (,) as a delimiter and limits the number of split parts to 2. Very similar to `<strong>split</strong>` that splits the string from the left, `<strong>rsplit</strong>` splits the string from the right.

The basic module contains matrix operations like, transpose (`<strong>tr</strong>`), inverse (`<strong>inv</strong>`), dot product (`<strong>dot</strong>`), and so on. There are further methods like single-valued decomposition (`<strong>svd</strong>`), lower and upper triangular decomposition, etc. An eigen module that provides eigen value computation of various matrix types. We will not delve deeper into these concepts here. However, we suggest the readers to look into the language documentation. We will look into some of the methods in later chapters selectively as we need them.

Just like the sparse vector examples, `<strong>SparseMatrixCSC</strong>` has similar functions to create, access, and manipulate the matrices. We will leave the details of using these data structures to the reader and suggest an understanding of the language documentation for the same in the interest of space and complexities they can add.

The similar example is now shown with a named capture. The captured data can be collected by indexing the `<strong>RegexMatch</strong>` with the captured group name.

`<strong>julia&gt; isascii("∀ x ∃ y"), isascii("abcd ef")</strong>`

`<strong>julia&gt; s = "\u2200 x \u2203 y"<br>"∀ x ∃ y"</strong>`

`<strong>AbstractString</strong>` interface is far more elaborate and makes certain assumptions on the internal composition of the string object as well. For example, these interfaces define assumptions on how many minimum bytes you will need to define a character in the string. If you use the `<strong>LegacyStrings</strong>` you will realize `<strong>ASCIIString</strong>` utilizes a `<strong>codeunit</strong>` of a `<strong>UInt8</strong>` while `<strong>UTF16String</strong>` utilizes a `<strong>codeunit</strong>` of `<strong>UInt16</strong>`. But both have a same size of internal data length in the code units.

The highlighted portion is the actual training code in `<strong>Flux</strong>`. The data are loaded in batches into the model. The gradients are updated using `<strong>ADAM</strong>` as the optimizer after every batch of computation. You will need to set a learning rate with the optimizer as well. Intermittently progress shall be reported using the `<strong>evalcb</strong>` callback. The `<strong>train!</strong>` function takes only one callback as input and invokes it after each batch. The training shall be executed `<strong>args.epochs</strong>` times. This means the whole training data shall be used to train the model 10 times. `<strong>logitcrossentropy</strong>` is used as a loss function. At the end of the run, the 91.77% accuracy of classification could be achieved with 10 epochs. On MNIST dataset state of the art accuracy achieved is almost 99.9%. While we are not keen on trying state of art accuracy, we will look at the CNNs, which are commonly used networks for image processing.

The learning rate is dynamic and updated when the model accuracy does not improve over 5 epochs. If you run this model for about 10 iterations, you shall be able to achieve an accuracy of 99% for the test data, a significant improvement over the fully connected model. The CNN code executes better on GPUs or TPUs. If you are using a CPU-based system, you may find the examples executing slower than you would expect.

`<strong>["PER", "O", "O", "LOC", "O", "O", "O", "ORG", "ORG", "O"]<br>["PER", "O", "O", "O", "O", "O", "O"]</strong>`

As can be seen above, the neural network is mostly a weighted sum of values. We are interested in finding the best values of the weights that fit the inputs X to the output Y. The activation function introduces the needed non-linearity to the system. In the output layer, the activation function (`<strong>softmax</strong>`), pushes smaller values closer to zero and larger values closer to 1. `<strong>softmax</strong>`, `<strong>sigmoid</strong>`, and `<strong>tanh</strong>` are commonly used as the activation functions in classification tasks.

The model, loss function, the optimizer, and data acquisition techniques may vary from problem to problem:

\[' ', 'T', 'a', 'c', 'd', 'e', 'h', 'i', 'l', 'n', 's', 't', 'v'\] characters make the sentence *This is a valid sentence.*

The preceding representation is called as **UTF-8**. What about encodings beyond 21-bits? So far Unicode specification does not utilize more than 21-bits of information but the scheme can accommodate up to 36-bits of information covering the whole UCS-4 range. Similar to UTF-8, UTF-16 has been introduced as well that considers character codes to be extended to 2-bytes of characters at a time. There is also UTF-32 transformation scheme as well.

As adoptions of computers became prevalent, it got clearer that computing cannot be kept confined to a specific region any longer. Second, data interchange also required the data be able to be presented in any computational system available. Third, the memory that was needed to represent text could be increased beyond one byte as both storage and RAM available in a computer had got cheaper. A single-byte restriction on characters was not needed. A group of computer scientists and linguists from various organizations and academics came together under an organization Unicode Consortium and introduced a **Universal Coded Character Set** (**UCS**). The first set of characters introduced in 1991 had about 7000 characters represented by a 2-byte character representation called UCS-2. However, very soon the characters started to grow as more languages were added to the specification. And, it was decided to take up 4 bytes for each character in a representation called UCS-4. In reality, the Unicode specification defines 16 planes of codes each of 65536 (216) size, where only few values are actually used. Technically, only 20 bits of the 32-bits are really used for practical purposes. However, many computer systems went on to implement wide character in the operating systems, Windows developed a native 16-bit operating system with Windows NT and discontinued the older Windows 95 code base. The code needed to be compiled for 8-bit and 16-bit versions separately by using macros in the late 90s and early parts of the millennia.

`<strong>julia&gt; s1 = "abc"</strong>`

Strings are immutable. Once created, they cannot be modified. Here is another way to define strings where the formatting and new line characters are preserved. No additional quoting is required for special characters.

`<strong>[:, :, 1] =</strong>`

`<strong>julia&gt; length(a)<br>4<br>julia&gt; isempty(a)<br>false<br>julia&gt; empty!(a)<br>Any[]<br>julia&gt; isempty(a)<br>true</strong>`

*   Abstract array types 

`<strong>julia&gt; a[:, [2], [1], [1]]<br>4×1×1×1 Array{Int64,4}:<br>[:, :, 1, 1] =<br>&nbsp;5<br>&nbsp;6<br>&nbsp;7<br>&nbsp;8<br>julia&gt; a[[1 2; 3 4], [2], [1], [1]]<br>2×2×1×1×1 Array{Int64,5}:<br>[:, :, 1, 1, 1] =<br>&nbsp;5&nbsp;&nbsp;6<br>&nbsp;7&nbsp;&nbsp;8</strong>`

As can be seen, range objects can be of any of the integral range types like `<strong>UnitRange</strong>`, `<strong>StepRange</strong>`, and so on. Multiple range indices can be used as index expressions as well. This leads to multidimensional arrays with elements picked up from locations that are specified in the ranges.

`<strong>julia&gt; A = reshape(collect(1:6), 3, 2)<br>3×2 Matrix{Int64}:<br>&nbsp;1&nbsp;&nbsp;4<br>&nbsp;2&nbsp;&nbsp;5<br>&nbsp;3&nbsp;&nbsp;6<br>julia&gt; ci = CartesianIndices(A)<br>3×2CartesianIndices{2,Tuple{Base.OneTo{Int64},Base.OneTo{Int64}}}:<br>&nbsp;CartesianIndex(1, 1)&nbsp;&nbsp;CartesianIndex(1, 2)<br>&nbsp;CartesianIndex(2, 1)&nbsp;&nbsp;CartesianIndex(2, 2)<br>&nbsp;CartesianIndex(3, 1)&nbsp;&nbsp;CartesianIndex(3, 2)</strong>`

There is only one entry for ": " and that is repeated 4 times to be consistent with mapping with other collections being broadcast.

While most of the examples are fairly straight forward, we will like to bring to your attention `<strong>a[1, :]</strong>` and `<strong>a[1, 2:3]</strong>`. Both these should have been row matrices. However, Julia would return a single dimension vector.

`<strong>getindex(X, i)</strong>` returns the value of the element at location `<strong>i</strong>` when `<strong>X[i]</strong>` is accessed. In a multidimensional array, the same is extended to using expression `<strong>getindex(X, I_1, I_2, …, I_n)</strong>` when `<strong>X[I_1, I_2, …, I_n]</strong>` is accessed.

What if the array `<strong>a</strong>` and `<strong>b</strong>` are of different sizes? Can they interact at an elements level? Keeping `<strong>a</strong>` as the preceding one, let us make `<strong>b</strong>` row and column vector and observe the results.

`<strong>Base.size(m::MyIdentity)=(m.l, m.l)</strong>`

A 5-element vector is created as the maximum value of the index was 5 in the `<strong>I</strong>` vector. Members of vector `<strong>R</strong>` can be accessed like a normal vector.

`<strong>julia&gt; foldl(=&gt;, [1, 2, 3, 4])<br>((1 =&gt; 2) =&gt; 3) =&gt; 4<br>julia&gt; foldr(=&gt;, [1, 2, 3, 4])<br>1 =&gt; (2 =&gt; (3 =&gt; 4))<br>julia&gt; reduce(=&gt;, [1, 2, 3, 4])<br>((1 =&gt; 2) =&gt; 3) =&gt; 4</strong>`

You shall get a fair idea of deploying Julia applications as web services in Docker containers, and then also carry the containers over to a Kubernetes service for deployment and orchestration using Julia commands. You can also manage *AWS*, *Azure*, and *Google Cloud* services using Julia commands as an integrated platform. Thus, you can use Julia as a client interface for many of the cloud deployment activities.

*   **Instantiate the package environment**: This may install all the dependent packages needed to run the application. 

This is only the relevant piece of code for you to expose the `<strong>queens(N)</strong>` function from . Let us look into it in detail:

`<strong># create gh-pages branch</strong>`

Thus, we generated a package code, created test cases, created relevant documentation. We updated the coverage data to a visualization tool on every test run and deployed the documentation to the `<strong>GitHub Pages</strong>` as part of continuous integrations. This ensures every change in the source code is reflected in proper test case run, ensuring test cases are added for the new functionalities introduced with the help of coverage tools and documentation is kept up-to-date.

*   The final documentation shall be accessible from the location: **https://<USER>.github.io/PointLib.jl/dev/** *   Run `<strong>git add .</strong>` so that all other source files are added to your repository. 

Location and dependency are stored per version of the package. For example, if you want to modify `<strong>C.jl</strong>` while using it in `<strong>A.jl</strong>`, you will need to make a development copy of the same. This is done using develop or `<strong>dev</strong>` command.

These packages are built using a build template generation tool called *BinaryBuilder*. If you require pre-built binaries you can be refer to the *JuliaBinaryWrappers* organization and look for the repository you are interested in or submit an issue in project `<strong>JuliaPackaging/Yggdrasil</strong>`. You can also build binary using `<strong>BinaryBuilder</strong>` templates and contribute to the project.

The constructors can take any `<strong>Real</strong>` number as a parameter and they ensure no non-positive value is permitted as part of the arguments. Suppose we were to create two additional constructors to construct squares.

`<strong>julia&gt; a = collect(1:16)<br>16-element Vector{Int64}:<br>&nbsp;1<br>&nbsp;2<br>&nbsp;3<br>&nbsp;…<br>&nbsp;16<br>julia&gt; b = reshape(a, (4, 4))<br>4×4 Matrix{Int64}:<br>&nbsp;1&nbsp;&nbsp;5&nbsp;&nbsp; 9&nbsp;&nbsp;13<br>&nbsp;2&nbsp;&nbsp;6&nbsp;&nbsp;10&nbsp;&nbsp;14<br>&nbsp;3&nbsp;&nbsp;7&nbsp;&nbsp;11&nbsp;&nbsp;15<br>&nbsp;4&nbsp;&nbsp;8&nbsp;&nbsp;12&nbsp;&nbsp;16<br>julia&gt; c = reshape(b, (2, 8))<br>2×8 Matrix{Int64}:<br>&nbsp;1&nbsp;&nbsp;3&nbsp;&nbsp;5&nbsp;&nbsp;7&nbsp;&nbsp; 9&nbsp;&nbsp;11&nbsp;&nbsp;13&nbsp;&nbsp;15<br>&nbsp;2&nbsp;&nbsp;4&nbsp;&nbsp;6&nbsp;&nbsp;8&nbsp;&nbsp;10&nbsp;&nbsp;12&nbsp;&nbsp;14&nbsp;&nbsp;16</strong>`

`<strong>julia&gt; vcat([1 2; 3 4], [5 6; 7 8], [9 10; 11 12])<br>6×2 Matrix{Int64}:<br>&nbsp;&nbsp;1&nbsp;&nbsp; 2<br>&nbsp;&nbsp;3&nbsp;&nbsp; 4<br>&nbsp;&nbsp;5&nbsp;&nbsp; 6<br>&nbsp;&nbsp;7&nbsp;&nbsp; 8<br>&nbsp;&nbsp;9&nbsp;&nbsp;10<br>&nbsp;11&nbsp;&nbsp;12</strong>`

What value do the exception objects add with such an elaborate architecture? They affect execution speed as every time there is a stack unwinding, there is a need to verify the exception objects. One of the major advantages they provide is the ability to track the stack where the exception occurred. Thus, one can get a trace of the error propagation. Second, the formation of an exception object provides the ability to provide enough information regarding the error.

`<strong>julia&gt; d = Dict("a"=&gt;1, "c"=&gt;2, "b"=&gt;3)<br>Dict{String,Int64} with 3 entries:<br>&nbsp;&nbsp;"c" =&gt; 2<br>&nbsp;&nbsp;"b" =&gt; 3<br>&nbsp;&nbsp;"a" =&gt; 1<br>julia&gt; d["b"]<br>3<br>julia&gt; d["a"] = 5<br>5<br>julia&gt; println(d)<br>Dict("c" =&gt; 2,"b" =&gt; 3,"a" =&gt; 5)</strong>`

*   Browse to the path where you will like to install Julia: ![](n4upl4fndqb.jpeg)
    
    **Figure 1.1:** Julia Windows Installer
    
    The default path is: `<strong>%LOCALAPPDATA%\Programs\Julia x.y.z</strong>`
    

At the end of the command, a new browser window will open up with Jupyter as shown in the following screenshot:

The two attributes of the type `<strong>num</strong>` and `<strong>den</strong>` are of the type `<strong>T</strong>` where `<strong>T</strong>` is a subtype of Integer. `<strong>Rational</strong>` is a subtype of Real. Here are some observations on the parametric data types.

`<strong>a.member</strong>` which was of type `<strong>Int64</strong>`, now is of `<strong>String</strong>` type. Julia presumes such unspecified types as `<strong>Any</strong>`. Scenarios where it is not possible to be deterministic about type, Julia would presume the type as `<strong>Any</strong>`. Use of `<strong>Any</strong>` is not desirable from a performance perspective. Every time an object of type `<strong>Any</strong>` is accessed, it is another redirection to access the actual object. Size of the object Any will not be available ahead in time. It will be a pointer pointing to another location in the memory where the actual object resides:

Let us try few experiments at the REPL prompt.

Strings are used for the textual presentation of information; when no other structure can represent the data effectively data can be presented as strings. Julia strings follow the Unicode specification and are encoded using the UTF-8 encoding. However, transformations can be carried out into other encodings with ease. Strings can also be considered as collections of characters. In this chapter, we will look at methods applicable to strings and their applications. Non-standard strings can be developed for custom applications while they continue to support the String framework. Regular expressions are another important concept that is utilized extensively for text pattern matching. Julia utilizes the PCRE engine for regular expressions. Lastly, we shall see how formatted outputs can be created for objects for output to terminals or file systems.

`<strong>Nothing</strong>` does not mark the output by default. When a semicolon is used as the end of a statement the behavior is similar to adding a `<strong>nothing</strong>` at the end of semicolon. Hence no output gets printed.

`<strong>function collect_function(f::Function, v)<br>&nbsp;&nbsp;&nbsp;&nbsp;a = similar(v)<br>&nbsp;&nbsp;&nbsp;&nbsp;for i=1:length(v)<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;a[i] = f(v[i])<br>&nbsp;&nbsp;&nbsp;&nbsp;end<br>&nbsp;&nbsp;&nbsp;&nbsp;return a<br>end<br>julia&gt; collect_function(x-&gt;x^3, 1:4)<br>4-element Vector{Int64}:<br>&nbsp;&nbsp;1<br>&nbsp;&nbsp;8<br>&nbsp;27<br>&nbsp;64</strong>`

`<strong>julia&gt; v = collect(3:2:10)<br>4-element Vector{Int64}:<br>&nbsp;3<br>&nbsp;5<br>&nbsp;7<br>&nbsp;9<br>julia&gt; for i=v<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; println(i)<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; end<br>3<br>5<br>7<br>9</strong>`

`<strong>julia&gt; function minrect(r1::RectangleP, r2::RectangleP)<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; w = r1.w &lt; r2.w ? r1.w : r2.w<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; h = r1.h &lt; r2.h ? r1.h : r2.h<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; return RectangleP(w, h)<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; end<br>minrect (generic function with 1 method)<br>julia&gt; minrect(RectangleP(1, 2), RectangleP(2.0, 0.5))<br>RectangleP{Float64}(1.0, 0.5)<br>julia&gt; minrect(RectangleP(1, 2), RectangleP(3.0, 4.0))<br>RectangleP{Int64}(1, 2)</strong>`

`<strong>get!(dict, key, value)</strong>` method is similar to the `<strong>get(dict, key, defval)</strong>` method but will insert the key with value where the key is not available in the dict. In the preceding example:

Non-existence of convert method from `<strong>String</strong>` to `<strong>Int</strong>` is making the constructor fail.

`<strong>julia&gt; 1f0+2<br>3.0f0<br>julia&gt; 1f0+2.0<br>3.0</strong>`

`<strong>union!</strong>` works like union but updates the first argument. Just like `<strong>union</strong>`, `<strong>symdiff</strong>` and `<strong>setdiff</strong>` methods are defined for symmetric difference and set difference as well. `<strong>issubset</strong>` method provides the subset relationship of one set with another.

While `<strong>area</strong>` function returned values as `<strong>Rational{Int}</strong>` and `<strong>Int</strong>` depending on the parametric type of Rectangle the same seems to have been ignored in the function `<strong>aspect_ratio</strong>`. The operator (/) is explicitly a floating-point division operator. The rational or division operator in Julia is (//). Let us introduce two additional methods for `<strong>aspect_ratio</strong>` specifically for the integer and rational types.

The constructor must return a well-initialized object. In Julia, the objects are expected to be initialized properly at the end of a call to the constructor. While there are cases where compound objects may not be initialized due to performance reasons they are more of exceptions than the rule. The constructor must return an object of the type it is trying to construct.

Instead of `<strong>for…=</strong>`, `<strong>for…in</strong>` can be used as well. This representation of for loop is similar to the previous only the syntax that looks more conducive to a collection. Let us look at the usage of this against a dictionary object.

`<strong>julia&gt; length(a)<br>10<br>julia&gt; for i=1:length(a)<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; println(a[i])<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; end<br>1.0<br>2.0<br>3.0<br>4.0<br>5.0<br>6.0<br>7.0<br>8.0<br>9.0<br>10.0</strong>`

In this chapter, the reader shall be able to understand compound statements. We will discuss branching and control flows like `<strong>if…else</strong>`, loops like `<strong>while</strong>` and `<strong>for</strong>` and exception handling. Control flows are core to programming logic and help build complex applications.

The preceding example, we could define a `<strong>Point2D</strong>` and `<strong>Point3D</strong>` as an alias on `<strong>Point{N}</strong>`. We defined two `<strong>dist</strong>` functions for both the types and ensured the dispatch is available based on the integer value of 2 or 3. `<strong>Point{2}</strong>` and `<strong>Point{3}</strong>` are two distinct types. With the `<strong>NTuple</strong>` as a collection type, let us try to have a `<strong>dist</strong>` method that works well for `<strong>Point{N}</strong>`.

`<strong>if &lt;Boolean condition&gt;<br>&nbsp;&nbsp;&nbsp;&nbsp;#do something<br>else<br>&nbsp;&nbsp;&nbsp;&nbsp;#do the something else<br>end</strong>`

`<strong>julia&gt; begin<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; s = 0<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; n = 10<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; @label loop<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; s = s + n<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; n = n - 1<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; if n &gt; 0<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; @goto loop<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; end<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; s<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; end<br>55</strong>`

`<strong>julia&gt; s = 0;<br>julia&gt; for i = 1:2:10<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; println(i)<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; s = s + i<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; end<br>1<br>3<br>5<br>7<br>9<br>julia&gt; s<br>25</strong>`

The `<strong>for</strong>` loop here is a single loop and will get terminated on a `<strong>break</strong>` statement. The `<strong>break</strong>` does not just terminate the inner loop as in the case of a nested `<strong>for</strong>` loop.

When an exceptional condition occurs in a program, it may not be possible for the function executing to return a valid value or bring the program to a recoverable state. Some programs may report an errors and terminate execution. However, it may be desirable to recover from such conditions and bring the program to a recoverable state while reporting the abnormal condition. Second, the recovered state must be in the call stack across multiple depths of function calls. Hence, it is possible exceptions can lead to a control flow move to another function in the call stack and not just the callers address space.

`<strong>for col=1:100000<br>&nbsp;&nbsp;&nbsp;&nbsp;for row=1:1000<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;do_something(m[row, col])<br>&nbsp;&nbsp;&nbsp;&nbsp;end<br>end</strong>`

Now let us look at the following scenario of an array of non-bits type:

`<strong>function f(::MyVal{1})<br>&nbsp;&nbsp;&nbsp;&nbsp;println(“Called from 1”)<br>end</strong>`

Ranges are used for iterations, indices, and initializing collections. They can have more complex parameters and also can have floating points for the initial value, steps, and final values. We will review the involved range objects in a later chapter. Here is just an example of a range with floating-point values.

`<strong>struct PolyLine &lt;: OpenShape</strong>`

`<strong>struct Rectangle</strong>`

`<strong>w()</strong>` and `<strong>w!()</strong>` are kept as the getter and setter methods; while `<strong>_w</strong>` being the attribute starting with an underscore (`<strong>_</strong>`) is kind of a directive that such attribute should not be accessed directly.

`<strong>area(x::T) where {T&lt;:Shape} = area(HasAreaTrait(T), x)</strong>`

Lastly, we have to make sure the area function utilizes the trait properly.

We discussed a few aspects of functional programming. Those interested in a concise conceptual understanding of functional programming with multiple programming languages can refer to *Functional Thinking*. It is natural for the readers to wonder if they should follow an imperative style or functional style. Julia is rather a flexible language in that respect. Although at many places you will find declarative programs, recursive functions, comprehensions, or similar features, Julia is not prescriptive about any specific style of programming. The language provides equally useful constructs to program in an imperative style. Sometimes immutability may lead to increased intermediate variable allocations, affecting the performance of the code. In such conditions, it may be ideal to use functions with side effects.

What happens when you specify `<strong>mymax(x)</strong>`? Naturally, it must give an error as there is no function that takes only one argument as input.

Errors are reported stating the function is only defined to consider 4 arguments or input parameters. However, the function can take any type as a data input. This is possible as the parameter type is `<strong>Any</strong>`, considering no parameter types are specified in the function definition.

`<strong>julia&gt; attacks(x1, y1, x2, y2) = begin<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; if x1 == x2<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; return true<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; elseif y1 == y2<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; return true<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; elseif x1 - y1 == x2 - y2<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; return true<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; elseif x1 + y1 == x2 + y2<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; return true<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; else<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; return false<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; end<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;end<br>attacks (generic function with 1 method)</strong>`

Before we design the complete solution to the problem, we must have a program unit that takes inputs of two queen locations and report if the queens are attacking each other.

*   **Do not overload** `<strong>Base</strong>` **methods for well-defined data types**: The following code will make the idea clear. 
    
    `<strong>module MyModule</strong>`
    
    `<strong>Base.:(*)(x::Symbol, y::Symbol) =</strong>`
    
    `<strong>Symbol(string(x)*string(y))</strong>`
    
    `<strong>end</strong>`
    
    `<strong>julia&gt; :a*:b</strong>`
    
    `<strong>:ab</strong>`
    
    The preceding code is not confined to `<strong>MyModule</strong>` only. It can be accessed from anywhere after the `<strong>MyModule</strong>` is loaded. That can be risky as inadvertently one may change the behavior of a type that you have not defined. Unlike classical object-oriented languages, Julia is relatively flexible in terms of data hiding, private and public distinction. Hence, these kinds of guidelines are necessary for better system design.
    

The short form is to be used for single-line mathematical constructs and the longer form for multiple lines in the function body.

You can type in and run; the results are shown in the same browser window.

Although Julia is a functional programming language, it also has complete iterative programming support. Some programmers have used Julia macros and generative programming to emulate TCO-like behavior.

There is no further computation after the recursive function call. The aggregation is to be carried out through the accumulator. There is no need to construct a stack frame on every function call.

`<strong>julia&gt; queens(8)<br>()<br>(1,)<br>(1, 3)<br>(1, 3, 5)<br>(1, 3, 5, 2)<br>(1, 3, 5, 2, 4)<br>(1, 3, 5, 2, 8)<br>(1, 3, 5, 7)<br>…<br>(1, 5, 7, 2)<br>(1, 5, 7, 2, 4)<br>(1, 5, 7, 2, 4, 8)<br>(1, 5, 7, 2, 6)<br>(1, 5, 7, 2, 6, 3)<br>(1, 5, 7, 2, 6, 8)<br>(1, 5, 8)<br>(1, 5, 8, 2)<br>(1, 5, 8, 2, 4)<br>(1, 5, 8, 2, 4, 7)<br>(1, 5, 8, 2, 4, 7, 3)<br>(1, 5, 8, 2, 7)<br>(1, 5, 8, 2, 7, 3)<br>(1, 5, 8, 2, 7, 3, 6)<br>(1, 5, 8, 6)<br>(1, 5, 8, 6, 3)<br>(1, 5, 8, 6, 3, 7)<br>(1, 5, 8, 6, 3, 7, 2)<br>(1, 5, 8, 6, 3, 7, 2, 4)<br>Final Positions: (4, 2, 7, 3, 6, 8, 5, 1)</strong>`

To observe the behavior of the varargs as a part of recursion one can add a `<strong>println</strong>` statement to the beginning of the function call.

Tasks are not functions. They can be switched easily as there is no need to recreate a stack frames as is needed to be carried out for functions. How the scheduler decides on the task to pick up is dependent on the architecture of the Julia runtime. For example, a scheduler with the availability of multiple thread execution may be able to pick up multiple tasks for execution. Similarly, the condition is another system-dependent entity. For example, the condition can be a file being locked, a device being busy or a channel being full or empty.

*   **Multithreading**: Julia by default runs as a single-threaded application. However, it can be made to run with a number of threads where the operating system supports it. Julia provides APIs where applications can take advantage from such threads available to them. 

`<strong>for dir in dirs</strong>`

`<strong>julia&gt; old_dir = pwd()</strong>`

`<strong>Directory of C:\Users\juser</strong>`

**Note: Julia has support for functionalities that require interaction with an operating system. We will review a few of these in this chapter. The treatment cannot be exhaustive in the book. The reader is suggested to refer to the Julia documentation for a detailed understanding.**

As can be seen, `<strong>Main</strong>`, `<strong>Core</strong>`, and `<strong>Base</strong>` were reported to have been available. `<strong>InteractiveUtils</strong>` is loaded due to the REPL. When launching the Julia environment with IJulia the same may not be loaded. Modules `<strong>m1</strong>` and `<strong>m2</strong>` that are defined previously are loaded as well. Let’s define a few variables.

One could also use, `<strong>Main.m2</strong>` instead of `<strong>.m2</strong>` that is the relative position of the module `<strong>m2</strong>`, while `<strong>Main.m2</strong>` is the fully qualified module name. `<strong>Main</strong>` is the highest level of the Julia execution environment. When a call is being made from a REPL or IJulia environment, the module namespace where all the interactions occur is the `<strong>Main</strong>` module. We will look at some of the predefined modules in the next section. You can import a non-exported function like `<strong>m1.g()</strong>` by using command specifically a requesting for the access. However, it will not succeed as there is already `<strong>g()</strong>` available from `<strong>m2.g()</strong>`.

`<strong>julia&gt; write("hello.txt", "Hello World");</strong>`

In the preceding example, while print tries to display the numeric value of the `<strong>UInt8</strong>`, the write method does a text output to the terminal.

Expected one character and as soon as we got one, the read command is completed. The method returned the data into a `<strong>Char</strong>` constant. The same for a `<strong>String</strong>` can lead to a never-ending condition.

The distributed architecture in Julia has all the similar models discussed in the earlier chapters related to asynchronous programming as well as multithreading programming. However, there are certain additional complexities that are due to the distributed architecture.

`<strong>Step: 1</strong>`

*   **Giving back**: As an organization, you may have used open-source technologies. Contributing back directly by active contribution is an alternative to monetary payout. 

`<strong>Removing value: 4</strong>`

If data types are nouns of communication, then functions play the role of a verb. Functions provide a mechanism to make small chunks of code that can meaningfully accomplish a task; the task can be repetitive or can represent a logically separable concept. Functions can take multiple inputs and return one or more output values as a tuple. The multiple dispatch architecture of Julia enables different functions are invoked based on the data type of input parameters. This enables a polymorphic behavior of the functions and can be called as **methods**. The polymorphic behavior with parametric data types can enable the implementation of reusable algorithms. Julia does not support automatic promotion across data types but provides enablers for programmers to define their own type conversion and promotion rules. We will take a look at recursion which is considered as a fundamental method of control flow in many algorithmic tasks, hence given emphasis in functional languages. Lastly, we will look at anonymous functions which are similar to the concept of lambda in languages like *Lisp*. Anonymous functions are used as predicates or callbacks in many functional language applications.

`<strong>template &lt;typename T&gt;</strong>`

`<strong>mean time:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;1.438 μs (0.00% GC)</strong>`

The Julia runtime needs to be loaded on the execution of a program for the first time and it will exit on completion of the execution. Second, Julia is a JIT-compiled language. Julia code executed sparingly may not have been compiled to native binaries before it is invoked. A part of the time may be spent in compiling the code to the native format when the code is invoked. To bring both the systems to a comparable state, Julia proponents would suggest the performance be measured in a steady-state condition. A steady state is reached when all the Julia code is run at least once and they are compiled to native binaries by the JIT compiler. While detractors of the language do not agree with the benchmark as they think the loading time has not been considered as a part of the process. Julia community publishes a set of micro-benchmarks for many competitive platforms taking few algorithmic tasks:

`<strong>0.97246&nbsp;&nbsp;&nbsp;&nbsp;0.245371<br><br>&nbsp;1.00337&nbsp;&nbsp; -0.0176268</strong>`

Computer scientists usually give maximum focus in perfecting this part of the problem. The gains that a well-chosen algorithm can provide to a problem are often unmatched by any amount of tweaking done around a poorly suited one. Whenever you have a code that is not performing right, it is best to take a look at the core design and understand if it has the right algorithm in place. Keeping performance focus in the design phase reduces significant rework costs. For example, *binary search has a complexity of O(log n) while the complexity of array search is linear time or O(n)*. Intuitively it seems that binary search will always perform over a linear search. But, with modern day processor cache and the efficiency of the memory management of arrays, it may be efficient to use linear search for smaller arrays. While B-tree is the choice of database indexes for disk-based storage; binary trees may be the data structure of choice for in-memory databases. One needs to look at the right data structures considering the complete system performance and not just theoretical asymptotic time complexity or the worst-case performance.

In this chapter, the reader shall be able to code for better performance. We shall look at the benchmark tools and understand how to profile the code. Julia code generation is a staged process and we can look at the generated code at various stages of generation as a means to understand the optimizations carried out. In the end, we will review some of the patterns and styles that help the user in writing high-performance code.

Running several applications over a single processor on a single thread is not true simultaneous multitasking. The operating system preempts the tasks based on a schedule, letting the processor to execute one task at a time. The user gets a feeling that all the tasks are running simultaneously, while they are only executed for small intervals and switched over to the next. In **Graphical User Interfaces** (**GUI**)-based applications, the responsiveness of the user interface to user inputs is given higher importance over the execution of other background tasks to completion. With multitasked applications running long computationally intensive tasks on single-processor systems, the usual practice is to process UI events intermittently to keep the UI responsive. This is known as **idle loop processing** in the Windows systems. Here the optimal response time is given priority over raw execution speed. Hence, sheer execution speed of the code may not be the objective of all code optimization projects.

Assignment expression introduces a new assigned variable `<strong>z</strong>` to the program state. Thus, manipulations of expressions and evaluations can modify the program states. When operating on them one has to be careful on the scope of variables.

Let us modify the assignment in the line # 2 from `<strong>x = 1</strong>` to `<strong>z = 1</strong>`.

Here are some of the examples:

We took a valid string that can be a Julia expression. We parsed it with a Julia parser and the output is returned in an interned string format. The interned string format is of type `<strong>Expr</strong>`. The dump method provides the AST of the expression. The following can be discerned from the AST:

When a symbol is defined using a colon, some alphabets may need disambiguation like the == operator in this case. You can use the colon character (:) to define an expression or interned string than use the `<strong>Expr</strong>` constructor or `<strong>Meta.parse</strong>` a string as we did in the previous section.

`<strong>@code_warntype</strong>` reports the Julia code as an AST. The AST is reported with type inference at each step of the AST. The non-deterministic types are highlighted with colors on a terminal or Jupyter console. There are many variables assigned to the type `<strong>Any</strong>`. This essentially means there will be an allocation for the location of memory and indirection to actual `<strong>Float64</strong>` value during any computation. We will add a type to the declaration for the parameter `<strong>x</strong>` and see how that affects the type inferences.

When `<strong>$$e</strong>` is used instead of `<strong>$e</strong>`, `<strong>eval(eval(:e))</strong>` is computed and thus the computed value 3 is placed between `<strong>quote…end</strong>`.

`<strong>julia&gt; macro sayhello(x::Int)</strong>`

One can invoke a regular expression match expression as shown.

`<strong>Body::Float64</strong>`

We define another `<strong>sindegmemo</strong>` function that takes `<strong>MemoLookupP</strong>` as an input.

We will introduce a new `<strong>MemoLookup</strong>` that has the types defined properly for the attributes like n and lookup.

`<strong>4 — %14 = Main.iszero(x@_9)::Bool</strong>`

`<strong>Stacktrace:</strong>`

`<strong>return :(x^2)</strong>`

`<strong>println(__module__)</strong>`

The `<strong>eval(quote…end)</strong>` is a commonly used expression in many Julia applications. The same is represented as the macro `<strong>@eval</strong>` and the expression looks as follows:

Random numbers are used extensively in data sciences to initialize data. They are also useful as sample creation for various probability distributions. A cryptographically secured random number is also a requirement for encryption and decryption algorithms. Here are some examples:

Since the local logger has overridden the current logger inside the `<strong>with_logger</strong>` block, the current logger is different from the global logger. However, outside the `<strong>with_logger</strong>` block the `<strong>current_logger()</strong>` is the same as the `<strong>global_logger()</strong>`. `<strong>SimpleLogger</strong>` provides a very simple interface to override the logging stream and the message levels to be shown in the logger. Log events can also have modules, message identifiers, files, line numbers, maximum times a log message should be shown and exceptions that are to be shown as part of logs.

`<strong>julia&gt; p = Month(3) + Day(10) + Hour(15)</strong>`

`<strong>4</strong>`

`<strong>Step 2</strong>`: Memory mapping the file and read value and ensure the correct data is populated.

*   The server spawns another parallel task so that client and server can communicate over it while the main server task keeps listening on the port 3000 indefinitely waiting for the next client to communicate. 

As we delve further into types, we will review the literals in further details in the context of specific types. In general, variables are initialized as `<strong>var = &lt;literals&gt;</strong>`.

As can be seen, a variable name cannot begin as a number. A variable can contain a Unicode character. There are limitations to the name of a variable and the author will like to suggest reviewing the Julia documentation for a detailed understanding of variable nomenclature. Keywords in Julia cannot be used as variables. Julia has very few keywords. Some of them are: `<strong>baremodule</strong>`, `<strong>begin</strong>`, `<strong>break</strong>`, `<strong>catch</strong>`, `<strong>const</strong>`, `<strong>continue</strong>`, `<strong>do</strong>`, `<strong>else</strong>`, `<strong>elseif</strong>`, `<strong>end</strong>`, `<strong>export</strong>`, `<strong>false</strong>`, `<strong>finally</strong>`, `<strong>for</strong>`, `<strong>function</strong>`, `<strong>global</strong>`, `<strong>if</strong>`, `<strong>import</strong>`, `<strong>let</strong>`, `<strong>local</strong>`, `<strong>macro</strong>`, `<strong>module</strong>`, `<strong>quote</strong>`, `<strong>return</strong>`, `<strong>struct</strong>`, `<strong>true</strong>`, `<strong>try</strong>`, `<strong>using</strong>`, `<strong>while</strong>`. Julia also has multiword keywords (mutable struct, abstract type, and so on) and infix operator (in, isa, and so on) keywords. The author will suggest a detailed review of the keywords in the language documentation for an elaborate understanding.

`<strong>julia&gt; typeof(1.0), typeof(1e0), typeof(1.e4) (Float64, Float64, Float64)</strong>`

Here, if `<strong>i</strong>` becomes less than 5 then a gets assigned to a value of 5. Otherwise, it remains as a nothing. Nothing and nothing also are used extensively in function arguments and return types.

`<strong>1</strong>`