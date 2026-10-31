
### [Chapter 6](#c06.xhtml)
gives a step-by-step understanding of the assembly code generated from basic C/C++ program.

### [Chapter 7](#c07.xhtml)
provides a step-by-step understanding of the assembly code generated from `printf()` function in C/C++ program.

### [Chapter 8](#c08.xhtml)
gives a step-by-step understanding of the assembly code generated from pointers in C/C++ program.

### [Chapter 9](#c09.xhtml)
provides a step-by-step understanding of the assembly code generated from decision control structure in C/C++ program.

### [Chapter 10](#c10.xhtml)
gives a step-by-step understanding of the assembly code generated from loop control structure in C/C++ program.

# PART 3: Real World Examples and Solutions

In this part, understanding of whatever learned in the previous chapters is explained with real world exercises with solutions and also reversing of Windows well-known application is demonstrated.

### [Chapter 11](#c11.xhtml)
covers RE exercise of an array code along with the solution used in the RE process.

### [Chapter 12](#c12.xhtml)
covers RE exercise of a structure code along with the solution used in the RE process.

### [Chapter 13](#c13.xhtml)
explains RE exercise of a Scanf program along with the solution used in the RE process.

### [Chapter 14](#c14.xhtml)
explains RE exercise of a `strcpy` program along with the solution used in the RE process.

### [Chapter 15](#c15.xhtml)
covers RE exercise of a simple interest code along with the solution used in the RE process.

### [Chapter 16](#c16.xhtml)
explains RE exercise of breaking Wannacry ransomware with Ghidra.

### [Chapter 17](#c17.xhtml)
covers RE exercise using Cutter tool.

### [Chapter 18](#c18.xhtml)
demonstrates the process of RE of Windows Calculator in a step-by-step manner.

This book is to educate the learners on the topic of Reverse Engineering on x86 platform. This will be a good book for beginners and computer graduates in the area of RE. Professionals who want to switch their career to RE can also use this book. Other readers can be from schools, universities or those who are passionate to get into the area of cyber security.

# Downloading the code
bundle and coloured images:
Please follow the link to download the
***Code Bundle*** and the ***Coloured Images*** of the book:
[https://rebrand.ly/b2fe9c](https://rebrand.ly/b2fe9c)

# Errata
We take immense pride in our work at BPB Publications and follow best practices to ensure the accuracy of our content to provide with an indulging reading experience to our subscribers. Our readers are our mirrors, and we use their inputs to reflect and improve upon human errors, if any, that may have occurred during the publishing processes involved. To let us maintain the quality and help us reach out to any readers who might be having difficulties due to any unforeseen errors, please write to us at :
[errata@bpbonline.com](mailto:errata@bpbonline.com)
Your support, suggestions and feedbacks are highly appreciated by the BPB Publications’ Family.
Did you know that BPB offers eBook versions of every book published, with PDF and ePub files available? You can upgrade to the eBook version at [www.bpbonline.com](http://www.bpbonline.com) and as a print book customer, you are entitled to a discount on the eBook copy. Get in touch with us at [business@bpbonline.com](mailto:business@bpbonline.com) for more details.
At [www.bpbonline.com](http://www.bpbonline.com), you can also read a collection of free technical articles, sign up for a range of free newsletters, and receive exclusive discounts and offers on BPB books and eBooks.

# BPB is searching for authors like you
If you're interested in becoming an author for BPB, please visit [www.bpbonline.com](http://www.bpbonline.com/) and apply today. We have worked with thousands of developers and tech professionals, just like you, to help them share their insight with the global tech community. You can make a general application, apply for a specific hot topic that we are recruiting an author for, or submit your own idea.
The code bundle for the book is also hosted on GitHub at [https://github.com/bpbpublications/Implementing-Reverse-Engineering](https://github.com/bpbpublications/Implementing-Reverse-Engineering). In case there's an update to the code, it will be updated on the existing GitHub repository.
We also have other code bundles from our rich catalog of books and videos available at [https://github.com/bpbpublications](https://github.com/bpbpublications). Check them out!

# PIRACY
If you come across any illegal copies of our works in any form on the internet, we would be grateful if you would provide us with the location address or website name. Please contact us at [business@bpbonline.com](mailto:business@bpbonline.com) with a link to the material.

# If you are interested in becoming an author
If there is a topic that you have expertise in, and you are interested in either writing or contributing to a book, please visit [www.bpbonline.com.](http://www.bpbonline.com/)

# REVIEWS
Please leave a review. Once you have read and used this book, why not leave a review on the site that you purchased it from? Potential readers can then see and use your unbiased opinion to make purchase decisions, we at BPB can understand what you think about our products, and our authors can see your feedback on their book. Thank you!
For more information about BPB, please visit [www.bpbonline.com.](http://www.bpbonline.com/)

# [CHAPTER 1](#toc.xhtml#c01)

## [Impact of Reverse Engineering](#toc.xhtml#c01)
Before we start on the implementation of reverse engineering, it will be interesting to understand what reverse engineering really is, how it came into existence, and how it is beneficial in the modern era. Reverse engineering, as the name suggests, is a combination of two words: Reverse and Engineering. Engineering is the science of designing and building something beneficial for the human race. Engineering has provided us with both advantages and disadvantages. Engineering equipped us with the knowledge and means to build essential things for the human race, including roads, buildings, bridges, cars, airplanes, software, and more. However, gradually, we also started using engineering to produce weapons of mass destruction like missiles, malware, and other deadly products harmful for humans and nature itself. When anything is engineered, it goes through many phases of design, development, and testing. With reverse engineering, things have really changed.
The concept behind reverse engineering is to break something to understand its internal architecture to build a copy or for the purpose of improvement or modification. In this chapter, we will talk about some real-life examples to understand the importance of reverse engineering and how it is changing the way the software industry works.

## [Structure](#toc.xhtml#s1a)
In this chapter, we will cover the following topics:
* Introduction to Reverse Engineering
* Importance of Reverse Engineering
* The Role of Reverse Engineering

## [Objective](#toc.xhtml#s2a)
After studying this chapter, you should be able to understand the importance of reverse engineering and its impact on the software industry. We will also talk about the opportunities associated with reverse engineering and how malware writers are using it to exploit the software systems of big companies.

## [Introduction to Reverse Engineering](#toc.xhtml#s3a)
