
[Chapter 4](#c04.xhtml) is where you want to go if you want to use a desktop setup, while [Chapter 6](#c06.xhtml) is helpful when you want to use a mobile device. Your preexisting setup may not work with the book’s examples because you might have different versions of the various products. It’s essential that you use the correct product versions to ensure success. Even if you choose to go with your own setup, consider reviewing [Chapter 5](#c05.xhtml) unless you’re an expert Python coder already.

If you’re already an expert with Python and know how machine learning works, you could always skip to [Chapter 7](#c07.xhtml). Starting at [Chapter 7](#c07.xhtml) will help you get into the examples quickly so that you spend less time with basics and more time with intermediate machine learning tasks. You can always go back and review the previous materials as needed.

# Part 1: Introducing How Machines Learn

IN THIS PART …

Discovering how AI really works and what it can do for you

Considering what the term `big data` means

Understanding the role of statistics in machine learning

Defining where machine learning will take society in the future

# Chapter 1: Getting the Real Story about AI

IN THIS CHAPTER

![Bullet](images/check.png)**`Seeing the dream; getting beyond the hype of artificial intelligence (AI)`**

![Bullet](images/check.png)**`Comparing AI to machine learning`**

![Bullet](images/check.png)**`Understanding the engineering portion of AI and machine learning`**

![Bullet](images/check.png)**`Delineating where engineering ends and art begins`**

`Artificial Intelligence (AI)`, the appearance of intelligence in machines, is a huge topic today, and it’s getting bigger all the time thanks to the success of new technologies (see some current examples at [`https://thinkml.ai/top-5-ai-achievements-of-2019/`](https://thinkml.ai/top-5-ai-achievements-of-2019/)). However, most people are looking for everyday applications, such as talking to their smartphone. Talking to your smartphone is both fun and helpful to find out things like the location of the best sushi restaurant in town or to discover how to get to the concert hall. As you talk to your smartphone, it learns more about the way you talk and makes fewer mistakes in understanding your requests. The capability of your smartphone to learn and interpret your particular way of speaking is an example of an AI, and part of the technology used to make it happen is `machine learning`, the use of various techniques to allow algorithms to work better based on experience.

You likely make limited use of machine learning and AI all over the place today without really thinking about it. For example, the capability to speak to devices and have them actually do what you intend is an example of machine learning at work. Likewise, recommender systems, such as those found on Amazon, help you make purchases based on criteria such as previous product purchases or products that complement a current choice. The use of both AI and machine learning will only increase with time.

In this chapter, you delve into AI and discover what it means from several perspectives, including how it affects you as a consumer and as a scientist or engineer. You also discover that AI doesn’t equal machine learning, even though the media often confuse the two. Machine learning is definitely different from AI, even though the two are related.

## Moving beyond the Hype

As any technology becomes bigger, so does the hype, and AI certainly has a lot of hype surrounding it. For one thing, some people have decided to engage in fear mongering rather than science. Killer robots, such as those found in the film `The Terminator`, really aren’t going to be the next big thing. Your first real experience with an android AI is more likely to be in the form a health care assistant ([`https://www.robotics.org/blog-article.cfm/The-Future-of-Elder-Care-is-Service-Robots/262`](https://www.robotics.org/blog-article.cfm/The-Future-of-Elder-Care-is-Service-Robots/262)) or possibly as a coworker ([`https://www.computerworld.com/article/2990849/meet-the-virtual-woman-who-may-take-your-job.html`](https://www.computerworld.com/article/2990849/meet-the-virtual-woman-who-may-take-your-job.html)). The reality is that you interact with AI and machine learning in far more mundane ways already. Part of the reason you need to read this chapter is to get past the hype and discover what AI can do for you today.

![Remember](images/remember.png)You may also have heard machine learning and AI used interchangeably. AI includes machine learning, but machine learning doesn’t fully define AI. This chapter helps you understand the relationship between machine learning and AI so that you can better understand how this book helps you move into a technology that used to appear only within the confines of science fiction novels.

Machine learning and AI both have strong engineering components. That is, you can quantify both technologies precisely based on `theory` (substantiated and tested explanations) rather than simply `hypothesis` (a suggested explanation for a phenomenon). In addition, both have strong science components, through which people test concepts and create new ideas of how expressing the thought process might be possible. Finally, machine learning also has an artistic component, and this is where a talented scientist can excel. In some cases, AI and machine learning both seemingly defy logic, and only the true artist can make them work as expected.

## Dreaming of Electric Sheep

`Androids` (a specialized kind of robot that looks and acts like a human, such as Data in `Star Trek: The Next Generation`) and some types of `humanoid robots` (a kind of robot that has human characteristics but is easily distinguished from a human, such as C-3PO in `Star Wars`) have become the poster children for AI (see the dancing robots at [`https://www.youtube.com/watch?v=lTckiTBaWkw`](https://www.youtube.com/watch?v=lTckiTBaWkw)). They present computers in a form that people can `anthropomorphize` (give human characteristics to, even though they aren’t human). In fact, it’s entirely possible that one day you won’t be able to distinguish between human and artificial life with ease. Science fiction authors, such as Philip K. Dick, have long predicted such an occurrence, and it seems all too possible today. The story “Do Androids Dream of Electric Sheep?” discusses the whole concept of more real than real. The idea appears as part of the plot in the movie `Blade Runner` ([`https://www.warnerbros.com/movies/blade-runner`](https://www.warnerbros.com/movies/blade-runner)). However, some uses of robots today are just plain fun, as in the Robot Restaurant show at [`https://www.youtube.com/watch?v=l1vvTtz8hpg`](https://www.youtube.com/watch?v=l1vvTtz8hpg). The sections that follow help you understand how close technology currently gets to the ideals presented by science fiction authors and the movies.
