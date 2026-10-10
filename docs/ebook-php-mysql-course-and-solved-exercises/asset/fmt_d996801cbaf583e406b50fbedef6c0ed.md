
Some chapters are accompanied by practical exercises to put your knowledge into practice, and to help you check your understanding, a suggested correction for each exercise is provided at the end of the book.

We're confident that this book will provide you with the tools you need to become a competent and accomplished PHP developer. Whether you're a beginner looking to learn new skills, or an experienced professional looking to deepen your knowledge, "PHP & MySQL: Master dynamic web development" is your ideal companion on your learning journey.

Happy reading and learning!

The editorial team

You can count on our support!

If you have any questions about any aspect of this book, or if you need any help, please send us an e-mail at `contact@skilldeve.com` and mention the title of the book in the subject line.

Share your opinion

We look forward to hearing from you! After exploring the pages of "Mastering HTML and CSS: from beginner to expert", we encourage you to share your opinion. To do so, simply click on the following link to access Amazon's review page dedicated to this book. Your feedback is valuable, not only to us, but to the entire technology community. Your feedback will help us keep the quality of our content at an optimum level. We look forward to reading your thoughts and hearing how this book has enriched your knowledge of HTML and CSS.

![Image](images/image.png)

# Introduction and development environment

In this introductory chapter, we will delve into the fascinating world of web development with `PHP` and `MySQL`. We will start with an exploration of how websites work, examining the differences between static and dynamic sites, as well as the programming languages associated with each type. Then, we will focus on the development environment for coding in `PHP`, including setting up a local `Apache` server and `MySQL` for creating and testing web applications on our own machine.

## How does a website work?

When it comes to how a website works, it's common to distinguish between two main types: static and dynamic.

Before going into detail, it's important to clarify the two essential components: the client, which corresponds to the user's computer, and the server, which hosts the website.

The fundamental question is: How do these two players communicate with each other?

To answer this question, we need to examine the communication process specific to each type of website.

In the case of a static website, communication takes place in two simple steps:

*   The client sends a request to the server to display a web page;
*   The server responds by sending the requested web page back to the client.

In concrete terms, in this scenario, the server stores web pages as static files and sends them to clients without any further modification or processing.

![Image](images/image-1.png)

For a dynamic site, on the other hand, the process is slightly more complex, with an intermediate step:

*   The client sends a request to the server to display a web page;
*   Instead of simply returning an existing page, the server dynamically generates the page according to the client's specific request;
*   The server then sends the freshly generated page to the client.

In this case, the server performs real-time processing and calculations to create a personalized page for each client request.

In conclusion, the fundamental difference between static and dynamic sites lies in the way web pages are generated and delivered to users, with significant implications in terms of data processing and content personalization.

![Image](images/image-2.png)

## Programming languages for every type of website

Websites fall into two broad categories: static and dynamic. Each type of site uses specific programming languages for its development.

### Static websites

Static websites are mainly built using markup languages such as `HTML` (HyperText Markup Language) and `CSS` (Cascading Style Sheets). `HTML` is used to structure the content of a Web page, defining elements such as headings, paragraphs, images, etc. `CSS` is used to style and format these elements, controlling their visual appearance.

### Dynamic Websites

Dynamic websites require interaction with a database, and use server-side programming languages to generate personalized content based on user requests. Common programming languages used for dynamic web development include `PHP` (Hypertext Preprocessor), `Python`, `ASP .NET`, `Java`, `JavaScript` and `Ruby`, and many others. `PHP` is one of the most popular languages for server-side web development, due to its simplicity, flexibility and compatibility with many database management systems, notably `MySQL`. `Python` and `Ruby` are also widely used for their dynamic web development capabilities and expressive syntax.

Understanding the programming languages suitable for each type of website is essential for choosing the most appropriate technology for a specific project, and for developing robust, functional websites.

## Development environment

There are two main approaches to website development:

### Local development

This method involves working on one's own computer, using a specific development environment to create and test the website. Once development is complete, the site is then transferred to a remote hosting server to make it accessible over the Internet. This approach is often preferred, as it offers an isolated working environment and does not require a permanent Internet connection. In this book, we explore in detail how to set up this development environment.

### Remote development

With this approach, website development takes place directly on the remote server hosting the site under development. This method is suitable for experienced developers working on complex projects requiring real-time collaboration with other team members. It also enables the site to be tested on different browsers and operating systems before going into production.

In short, the choice between local and remote development depends on the specific needs of the project, the experience of the developer and the resources available. All the examples presented in this book are tested locally before being deployed on a remote server.

To develop a dynamic website, several elements are required on our machine:

*   **Apache server**: This is the Web server responsible for managing the site. However, by default, `Apache` can only handle static websites, i.e. `HTML` pages. To enable it to handle `PHP` as well, a plugin must be added. By combining `Apache` with `PHP`, our computer will be able to read web pages written in `PHP`.
*   **Database management system (DBMS)**: Since dynamic websites require interaction with databases, a database management tool is essential. `MySQL` is one of the most commonly used DBMS for this purpose.

![Image](images/image-3.png)

Fortunately, there are software programs that make it much easier to install these items on your computer. Depending on the operating system you're using, you can choose from the following options:

*   For Windows: `WAMP Server` [`http://www.wampserver.com/`](http://www.wampserver.com/)
*   For Mac: `MAMP` [`https://www.mamp.info/en/downloads/`](https://www.mamp.info/en/downloads/)
*   For Linux: `XAMPP` [`https://www.apachefriends.org/fr/download.html`](https://www.apachefriends.org/fr/download.html)

`XAMPP` is available in three different versions: one for Windows, one for Mac and one for Linux. Although it is more complete than the other options (`WAMP` and `LAMP`), it is not necessary to use all its features. In this book, we'll be installing `XAMPP` for its versatility. However, you are free to choose between `XAMPP`, `MAMP` or `WAMP`, as the basic operation is the same for all three.

## Downloading and installing XAMPP on Mac OS

Here are the steps to download and install `XAMPP` on macOS:

1.  Visit the official Apache Friends website: [`https://www.apachefriends.org/fr/download.html`](https://www.apachefriends.org/fr/download.html)
