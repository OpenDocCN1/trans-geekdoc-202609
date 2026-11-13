# 3.3 Domain Knowledge

It is natural to wonder what knowledge it takes to code up the body of a function. A little bit of reflection tells you that this step demands an appropriate grasp of the domain of the program. Indeed, there are two forms of such *domain knowledge*:

+   1. Knowledge from external domains, such as mathematics, music, biology, civil engineering, art, and so on. Because programmers cannot know all of the application domains of computing, they must be prepared to understand the language of a variety of application areas so that they can discuss problems with domain experts. Mathematics is at the intersection of many, but not all, domains. Hence, programmers must often pick up new languages as they work through problems with domain experts.

+   2. Knowledge about the library functions in the chosen programming language. When your task is to translate a mathematical formula involving the tangent function, you need to know or guess that your chosen language comes with a function such as BSL’s tan. When your task involves graphics, you will benefit from understanding the possibilities of the 2htdp/image library.

Since you can never predict the area you will be working in, or which programming language you will have to use, it is imperative that you have a solid understanding of the full possibilities of whatever computer languages are around and suitable. Otherwise some domain expert with half-baked programming knowledge will take over your job.

You can recognize problems that demand domain knowledge from the data definitions that you work out. As long as the data definitions use classes that exist in the chosen programming language, the definition of the function body (and program) mostly relies on expertise in the domain. Later, when we introduce complex forms of data, the design of functions demands computer science knowledge.