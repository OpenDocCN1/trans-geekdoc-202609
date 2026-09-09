 ![img](d2d_images/cover.jpg) 

 ![image](d2d_images/image069.png)

 © 2024 Jiho Seok.   All rights reserved. 

 No part of this publication may be reproduced, stored in a retrieval system, or transmitted in any form or by any means, electronic, mechanical, photocopying, recording, or otherwise, without the written permission of the author. 

 This book is provided for informational purposes only and, while every attempt has been made to ensure its accuracy, the contents are the author's opinions and views.   The author or publisher shall not be liable for any loss of profit or any other damages, including but not limited to special, incidental, consequential, or other damages. 

 All trademarks, service marks, product names or named features are assumed to be the property of their respective owners, and are used only for reference.   There is no implied endorsement if we use any of these terms. 

  This page intentionally left blank    . 

 ![image](d2d_images/image226.png)

[ Preface ](#c002.xhtml#_Toc170065675)

[ Introduction to Node.js ](#c003.xhtml#_Toc170065677)

[ 1.1.   What is Node.js? ](#c003.xhtml#_Toc170065678)

[ 1.2.   History and Evolution of Node.js ](#c003.xhtml#_Toc170065679)

[ 1.3.   Node.js Architecture ](#c003.xhtml#_Toc170065680)

[ 1.4.   Installing Node.js ](#c003.xhtml#_Toc170065681)

[ 1.5.   Setting Up the Development Environment ](#c003.xhtml#_Toc170065682)

[ 1.6.   Creating a Basic Web Server ](#c003.xhtml#_Toc170065683)

[ 2.   Core Concepts ](#c004.xhtml#_Toc170065684)

[ 2.1.   The Event Loop ](#c004.xhtml#_Toc170065685)

[ 2.2.   Understanding Non-blocking I/O ](#c004.xhtml#_Toc170065686)

[ 2.3.   Asynchronous Programming in Node.js ](#c004.xhtml#_Toc170065687)

[ Example: Building a Simple Weather Application ](#c004.xhtml#_Toc170065688)

[ Important Note ](#c004.xhtml#_Toc170065689)

[ 2.4.   Node.js Modules and NPM ](#c004.xhtml#_Toc170065690)

[ 2.5.   Using the REPL (Read-Eval-Print Loop) ](#c004.xhtml#_Toc170065691)

[ Table of REPL Commands ](#c004.xhtml#_Toc170065692)

[ 3.   File System and Streams ](#c005.xhtml#_Toc170065693)

[ 3.1.   Reading and Writing Files ](#c005.xhtml#_Toc170065694)

[ 3.2.   Working with Directories ](#c005.xhtml#_Toc170065695)

[ 3.3.   Streams and Buffers ](#c005.xhtml#_Toc170065696)

[ 3.4.   Handling File Uploads ](#c005.xhtml#_Toc170065697)

[ Link the CSS File to Your HTML Page ](#c005.xhtml#_Toc170065698)

[ Multiple File Uploads ](#c005.xhtml#_Toc170065699)

[ Complete Example ](#c005.xhtml#_Toc170065700)

[ Explanation of the Code ](#c005.xhtml#_Toc170065701)

[ 3.5.   Practical Examples with File System Operations ](#c005.xhtml#_Toc170065702)

[ 4.   HTTP and Web Servers ](#c006.xhtml#_Toc170065703)

[ Understanding HTTP Status Codes ](#c006.xhtml#_Toc170065704)

[ Detailed Explanation of HTTP Status Codes ](#c006.xhtml#_Toc170065705)

[ Understanding HTTP Methods ](#c006.xhtml#_Toc170065706)

[ Detailed Explanation of HTTP Methods ](#c006.xhtml#_Toc170065707)

[ 4.1.   Creating a Simple Web Server ](#c006.xhtml#_Toc170065708)

[ 4.-Introduction to Postman ](#c006.xhtml#_Toc170065709)

[ How to Use Postman ](#c006.xhtml#_Toc170065710)

[ 4.2.   Handling Requests and Responses ](#c006.xhtml#_Toc170065711)

[ Handling Different HTTP Methods ](#c006.xhtml#_Toc170065712)

[ Handling GET Requests ](#c006.xhtml#_Toc170065713)

[ Handling POST Requests ](#c006.xhtml#_Toc170065714)

[ Handling PUT Requests ](#c006.xhtml#_Toc170065715)

[ Handling DELETE Requests ](#c006.xhtml#_Toc170065716)

[ Handling Other HTTP Methods (PATCH, OPTIONS, HEAD) ](#c006.xhtml#_Toc170065717)

[ Parsing and Managing Data ](#c006.xhtml#_Toc170065718)

[ Error Handling ](#c006.xhtml#_Toc170065719)

[ 4.3.   Routing ](#c006.xhtml#_Toc170065720)

[ 4.4.   Serving Static Files ](#c006.xhtml#_Toc170065721)

[ 4.5.   Using Middleware ](#c006.xhtml#_Toc170065722)

[ Introduction to Middleware ](#c006.xhtml#_Toc170065723)

[ Types of Middleware ](#c006.xhtml#_Toc170065724)

[ Third-Party Middleware ](#c006.xhtml#_Toc170065725)

[ Body-Parser ](#c006.xhtml#_Toc170065726)

[ Helmet ](#c006.xhtml#_Toc170065727)

[ Practical Example: Secure REST API with Helmet ](#c006.xhtml#_Toc170065728)

[ Creating Custom Middleware ](#c006.xhtml#_Toc170065729)

[ Step 2: Create the HTML Page ](#c006.xhtml#_Toc170065730)

[ Step 3: Implement Custom Middleware ](#c006.xhtml#_Toc170065731)

[ Step 4: Set Up Routes ](#c006.xhtml#_Toc170065732)

[ Step 5: Set Up the Main Application ](#c006.xhtml#_Toc170065733)

[ 4.6.   Building a Simple Blog Server ](#c006.xhtml#_Toc170065734)

[ Project Structure ](#c006.xhtml#_Toc170065735)

[ Step 2: Create the HTML Page ](#c006.xhtml#_Toc170065736)

[ Step 3: Implement Custom Middleware ](#c006.xhtml#_Toc170065737)

[ Step 4: Set Up Routes ](#c006.xhtml#_Toc170065738)

[ Step 5: Set Up the Main Application ](#c006.xhtml#_Toc170065739)

[ 5.   Networking and Security ](#c007.xhtml#_Toc170065740)

[ 5.1.   Working with TCP and UDP Servers ](#c007.xhtml#_Toc170065741)

[ 5.2.   Handling Secure Communications with HTTPS ](#c007.xhtml#_Toc170065742)

[ 5.3.   Implementing Authentication and Authorization ](#c007.xhtml#_Toc170065743)

[ 5.4.   Secure Coding Practices in Node.js ](#c007.xhtml#_Toc170065744)

[ 5.5.   Practical Examples: Building a Chat Application ](#c007.xhtml#_Toc170065745)

[ Step 1: Setting Up the Project ](#c007.xhtml#_Toc170065746)

[ Step 2: Setting Up the User Model and Sample Data ](#c007.xhtml#_Toc170065747)

[ Step 3: Implementing Authentication Routes ](#c007.xhtml#_Toc170065748)

[ Step 4: Setting Up WebSocket for Real-Time Communication ](#c007.xhtml#_Toc170065749)

[ Step 5: Creating Middleware for Authentication ](#c007.xhtml#_Toc170065750)

[ Step 6: Integrating Everything in the Main Application File ](#c007.xhtml#_Toc170065751)

[ Step 7: Creating a Simple Client ](#c007.xhtml#_Toc170065752)

[ 6.   Databases ](#c008.xhtml#_Toc170065753)

[ 6.1.   Introduction to Databases with Node.js ](#c008.xhtml#_Toc170065754)

[ 6.2.   Working with SQL Databases (MySQL) ](#c008.xhtml#_Toc170065755)

[ PostgreSQL ](#c008.xhtml#_Toc170065756)

[ MongoDB ](#c008.xhtml#_Toc170065757)

[ Redis ](#c008.xhtml#_Toc170065758)

[ 6.4.   Using ORMs (Sequelize) ](#c008.xhtml#_Toc170065759)

[ Using ORMs (Mongoose) ](#c008.xhtml#_Toc170065760)

[ 6.5.   Database Connection Pooling ](#c008.xhtml#_Toc170065761)

[ 6.6.   Practical Examples: Building a RESTful API with Database Integration ](#c008.xhtml#_Toc170065762)

[ 7.   Advanced JavaScript and Node.js Patterns ](#c009.xhtml#_Toc170065763)

[ 7.1.   Promises and Async/Await ](#c009.xhtml#_Toc170065764)

[ 7.2.   Error Handling Strategies ](#c009.xhtml#_Toc170065765)

[ 7.3.   Event Emitters ](#c009.xhtml#_Toc170065766)

[ 7.4.   Streams and Pipe Chaining ](#c009.xhtml#_Toc170065767)

[ 7.5.   Module Design Patterns ](#c009.xhtml#_Toc170065768)

[ 7.6.   Practical Examples: Creating a Custom Event Emitter ](#c009.xhtml#_Toc170065769)

[ Sources ](#c009.xhtml#_Toc170065770)

 
|  ![image](d2d_images/chapter_title_corner_decoration_left.png)  ||  ||  ![image](d2d_images/chapter_title_corner_decoration_right.png)  |
| --- | --- | --- |

 ![image](d2d_images/chapter_title_above.png) 

#  ​   Preface 

 ![image](d2d_images/chapter_title_below.png) 

   W    elcome to     The Complete Node.js Guide    .   This book is crafted to guide you through the intricacies of Node.js, whether you're just starting your journey or looking to deepen your expertise.   Node.js has revolutionized the world of server-side programming with its efficient, non-blocking I/O model, enabling the creation of high-performance applications that scale In this comprehensive guide, we will explore the foundational concepts of Node.js and progressively delve into more advanced topics.   The aim is to provide a clear and thorough understanding of Node.js, empowering you to build robust, efficient, and scalable applications. 

  Chapter 1    serves as your introduction to Node.js, covering its origins, architecture, and fundamental concepts.   You'll learn about the history and evolution of Node.js, gaining insight into how it became the powerful platform it is today.   We'll guide you through installing Node.js and setting up your development environment, culminating in writing your first Node.js program. 

  Chapter 2    dives into the core concepts that make Node.js unique.   You'll explore the event loop, understand non-blocking I/O, and master asynchronous programming using promises and async/await.   This chapter also covers Node.js modules and npm, the package manager that has become a cornerstone of Node.js development. 

  Chapter 3    focuses on file system operations and streams.   You'll learn how to read and write files, work with directories, and leverage streams and buffers for efficient data processing.   Practical examples will help solidify your understanding of these essential operations. 

  Chapter 4    introduces you to HTTP and web server concepts.   You'll start by creating a simple web server and progressively handle more complex scenarios such as request and response management, routing, serving static files, and using middleware.   The chapter includes practical examples, such as building a simple blog server, to illustrate these concepts in action. 

  Chapter 5    covers networking and security.   You'll explore working with TCP and UDP servers, handling secure communications with HTTPS, and implementing authentication and authorization.   This chapter also emphasizes secure coding practices to ensure your applications are robust and secure.   A practical example of building a chat application will demonstrate these concepts. 

  Chapter 6    dives into databases, both SQL and NoSQL.   You'll learn how to work with MySQL, PostgreSQL, MongoDB, and Redis, and understand the benefits and use cases of each.   This chapter also covers using ORMs like Sequelize and Mongoose for database interactions and explains database connection pooling.   Practical examples, such as building a RESTful API with database integration, will help you apply these concepts. 

  Chapter 7    explores advanced JavaScript and Node.js patterns.   You'll master promises and async/await, develop robust error-handling strategies, and understand event emitters.   The chapter also covers streams and pipe chaining, module design patterns, and provides practical examples, such as creating a custom event emitter. 

 Node.js continues to evolve, and staying updated with the latest versions is crucial for leveraging its full potential.   Throughout this book, we use the latest software versions available at the time of writing, ensuring you are equipped with up-to-date knowledge and practices. 

 This book is designed to be a practical, hands-on guide that complements your learning journey.   Each chapter builds upon the previous ones, with clear explanations, code examples, and best practices.   Whether you are a beginner eager to learn or an experienced developer looking to refine your skills, this book aims to be a valuable resource in your Node.js development toolkit. 

 Thank you for choosing this book.   I hope it inspires you to create amazing applications and helps you become a proficient Node.js developer. 

#  ​   ![image](d2d_images/image194.png)

 
|  ![image](d2d_images/chapter_title_corner_decoration_left.png)  ||  ||  ![image](d2d_images/chapter_title_corner_decoration_right.png)  |
| --- | --- | --- |

 ![image](d2d_images/chapter_title_above.png) 

#  Introduction to Node.js 

 ![image](d2d_images/chapter_title_below.png) 

##  ​   1.1.   What is Node.js? 

   N    ode.js is an open    -source, cross-platform runtime environment that allows developers to execute JavaScript code outside of a web browser.   Traditionally, JavaScript was confined to the browser, primarily used to enhance the interactivity of web pages.   However, with the advent of Node.js, developers can now leverage JavaScript for server-side scripting   ​   ^( \[1\] )   , enabling the development of dynamic and scalable web applications with a single programming language across both the client and server sides. 

 ![image](d2d_images/image049.png)

####  Key Features of Node.js 

    E    VENT-DRIVEN AND NON    -Blocking I/O    : Node.js operates on a single-threaded event loop   ​   ^( \[2\] )   , utilizing non-blocking I/O calls.   This means that operations such as reading from or writing to a file, interacting with databases, or making network requests are handled asynchronously.   This architecture allows Node.js to handle many concurrent connections with high throughput and efficiency, making it ideal for real-time applications where performance and scalability are crucial. 

  Single Programming Language    : One of the significant advantages of Node.js is that it enables developers to use JavaScript for both server-side and client-side development.   This unification of the development stack simplifies the workflow, enhances productivity, and promotes code reuse between the server and client. 

  NPM (Node Package Manager)    : Node.js comes with npm, the largest ecosystem of open-source libraries and packages.   With npm, developers can easily share, discover, and integrate third-party modules, significantly accelerating the development process.   The npm   ​   ^( \[3\] )   registry hosts millions of packages that address a wide range of functionalities, from database drivers and web frameworks to utility libraries and testing tools. 

  Fast and Scalable    : Node.js's non-blocking nature and efficient handling of asynchronous operations contribute to its speed and scalability.   It can manage a large number of concurrent connections with minimal overhead, making it a preferred choice for high-traffic applications, such as streaming services, online gaming platforms, and collaborative tools. 

  Microservices and Real-Time Applications    : Node.js excels in building microservices architectures   ​   ^( \[4\] )   , where an application is divided into small, loosely coupled services that can be developed, deployed, and scaled independently.   Additionally, its support for WebSockets   ​   ^( \[5\] )   and real-time communication libraries like Socket.IO enables developers to create real-time applications such as chat apps, live updates, and collaborative tools with ease. 

####  Practical Applications of Node.js 

   N    ODE.JS IS WIDELY USED    across various domains and industries due to its versatility and performance.   Here are some practical applications where Node.js shines: 

  Web Servers    : Node.js is commonly used to build web servers that can handle multiple client requests simultaneously.   Frameworks like Express.js   ​   ^( \[6\] )   make it easy to develop robust web applications with routing, middleware, and templating capabilities. 

  API Development    : With Node.js, developers can create RESTful APIs   ​   ^( \[7\] )   to serve as the backbone of web and mobile applications.   Its asynchronous nature ensures fast response times, even under heavy loads. 

  Real-Time Applications    : Node.js is an excellent choice for developing real-time applications such as chat applications, online gaming, live streaming, and collaborative tools.   Its event-driven   ​   ^( \[8\] )   architecture and support for WebSockets enable real-time communication and updates. 

  Microservices    : Node.js's lightweight nature and modularity make it suitable for microservices architecture.   Developers can build, deploy, and scale individual services independently, resulting in more maintainable and scalable applications. 

  Command-Line Tools    : Many command-line tools and utilities are built using Node.js due to its ease of scripting and access to the file system.   Popular tools like npm itself are examples of Node.js applications. 

####  A Glimpse into Node.js in Action 

   I    MAGINE YOU'RE WORKING    on a real-time chat application.   With Node.js, you can efficiently manage numerous simultaneous connections, handle message broadcasting, and ensure low latency communication.   By using libraries like Socket.IO, you can implement features like user presence, typing indicators, and instant messaging with minimal effort.   The event-driven model of Node.js ensures that your server remains responsive, even when handling thousands of concurrent users. 

 Another example is building a scalable e-commerce platform.   Node.js allows you to create a RESTful API for managing products, user accounts, and orders.   You can integrate various third-party services, such as payment gateways and shipping providers, using npm packages.   The non-blocking I/O   ​   ^( \[9\] )   operations ensure that your server can handle a high volume of transactions without becoming a bottleneck, providing a seamless shopping experience for your users Node.js has revolutionized web development by extending JavaScript's reach beyond the browser and into the server environment.   Its event-driven, non-blocking architecture, combined with the extensive npm ecosystem, makes it a powerful tool for building modern, high-performance web applications.   As you embark on your journey to master Node.js, you'll discover its immense potential and versatility, empowering you to create innovative solutions that meet the demands of today's digital world. 

##  ​   1.2.   History and Evolution of Node.js 

   T    HE HISTORY OF NODE    .js is a fascinating journey of innovation and evolution, reflecting the changing landscape of web development and server-side programming.   Understanding this history not only provides context for Node.js's current capabilities but also highlights the significant milestones that have shaped its development. 

####  The Birth of Node.js 

    2009    : INCEPTION     Node.js was created in 2009 by Ryan Dahl.   Dahl was motivated by the limitations of existing server-side technologies, particularly the inability to handle many concurrent connections efficiently.   At a presentation in 2009, he famously demonstrated how existing web servers, including Apache, struggled with concurrent connections due to their synchronous nature. 

  Key Insight:    Dahl's key insight was the potential of a single-threaded, event-driven architecture that could handle I/O operations asynchronously.   This led to the development of Node.js, which used the V8 JavaScript engine from Google Chrome to execute JavaScript code on the server side. 

  First Release:    The initial version of Node.js was released in May 2009.   It introduced a new programming paradigm for server-side development, leveraging JavaScript's non-blocking, event-driven model. 

 ![image](d2d_images/image125.png)

####  Early Years and Rapid Adoption 

    2010    : NPM INTRODUCTION     In January 2010, Isaac Schlueter introduced npm (Node Package Manager), which revolutionized how Node.js developers managed and shared code.   npm provided a centralized repository of reusable modules, significantly accelerating development and fostering a vibrant community. 

  2011: Joyent Sponsorship    Joyent, a cloud computing company, began sponsoring Node.js in 2011.   This sponsorship provided the resources needed for more structured development and contributed to the growing adoption of Node.js in the industry. 

 Key Versions: 

  v0.2.0 (July 2010)    : Improved stability and added new features like TLS (Transport Layer Security) support. 

  v0.4.0 (February 2011)    : Introduced the Windows port, making Node.js accessible to a broader audience. 

####  Expansion and Maturity 

    2012    -2014: BROADENING    Horizons    During this period, Node.js continued to evolve, adding features and improving performance.   The community around Node.js grew rapidly, with major companies beginning to adopt it for production use. 

 Key Versions: 

  v0.6.0 (October 2011)    : Included significant performance improvements and enhancements to the core modules. 

  v0.8.0 (June 2012)    : Introduced the cluster module, allowing Node.js to take advantage of multi-core systems. 

  v0.10.0 (March 2013)    : Brought enhancements to streams and better error handling mechanisms. 

  2014: io.js Fork    In late 2014, a group of developers forked Node.js to create io.js.   This was a community-driven effort aimed at accelerating development and incorporating the latest versions of the V8 engine.   The fork was motivated by dissatisfaction with the slow pace of Node.js development under Joyent's stewardship. 

####  Reconciliation and Formation of the Node.js Foundation 

    2015    : RECONCILIATION AND    Node.js Foundation    In 2015, the Node.js and io.js communities reconciled, leading to the creation of the Node.js Foundation under the Linux Foundation.   This move aimed to provide a neutral governance structure and ensure the continued growth and stability of Node.js. 

 Key Versions: 

  v4.0.0 (September 2015)    : This version marked the unification of Node.js and io.js.   It brought numerous improvements and aligned the project with the latest V8 engine features. 

  v6.0.0 (April 2016)    : Focused on performance improvements and added new ES6 features. 

  v8.0.0 (May 2017)    : Introduced async/await, making asynchronous programming in Node.js more intuitive and manageable. 

####  Node.js Today 

    2018    -2020: CONTINUED GROWTH    and New Features    Node.js has continued to evolve, adding new features and improvements with each release.   The community and ecosystem have grown exponentially, with npm hosting millions of packages. 

 Key Versions: 

  v10.0.0 (April 2018)    : Introduced performance improvements and new features like the    fs.promises    API. 

  v12.0.0 (April 2019)    : Brought enhancements to the performance of the Node.js runtime, improved diagnostics, and introduced native modules. 

  v14.0.0 (April 2020)    : Included improved diagnostics, internationalization support, and the addition of the    Diagnostic Report    feature. 

  2021-2022: Emphasis on Security and Performance    Node.js has continued to place a strong emphasis on security, performance, and developer experience.   New features and improvements have made it even more powerful and versatile. 

 Key Versions: 

  v16.0.0 (April 2021)    : Added Apple Silicon support, improved internationalization, and enhanced timers. 

  v18.0.0 (April 2022)    : Introduced new APIs and improved performance, especially for high-performance server applications. 

 2023: Latest Release 

  v20.14.0 (As of June 2023)    : The latest stable release at the time of writing.   This version continues to build on the improvements of previous versions, focusing on performance optimizations, security enhancements, and new features that keep Node.js at the forefront of server-side development 

####  Milestones and Community Contributions 

    E    COSYSTEM GROWTH:     The Node.js ecosystem, powered by npm, has become one of the largest and most active open-source communities in the world.   The vast array of modules available on npm enables developers to quickly find solutions to common problems and integrate a wide range of functionalities into their applications. 

  Corporate Adoption:    Major companies such as Netflix, LinkedIn, Uber, and Walmart have adopted Node.js for their backend services.   Its ability to handle high concurrency with minimal overhead makes it an ideal choice for real-time applications, microservices, and APIs. 

  Community and Governance:    The Node.js Foundation has fostered a strong community and established a clear governance model, ensuring that the project remains open, transparent, and inclusive.   Regular releases and a focus on backwards compatibility have helped maintain a stable and reliable platform for developers worldwide. 

####  Future Directions 

   T    HE FUTURE OF NODE    .js looks promising, with ongoing efforts to enhance its performance, security, and developer experience.   Key areas of focus include: 

  Improved Diagnostics    : Enhancing the debugging and profiling tools to help developers identify and resolve issues more efficiently. 

  Security Enhancements    : Continuing to strengthen the security model and provide tools for secure coding practices. 

  Performance Optimizations    : Further optimizing the runtime to handle even more demanding workloads. 

  Ecosystem Integration    : Ensuring seamless integration with modern development tools and frameworks. 

##  ​   1.3.   Node.js Architecture 

   U    NDERSTANDING THE ARCHITECTURE    of Node.js is essential to appreciate its performance and scalability advantages.   Node.js is designed to build scalable network applications, and its architecture plays a crucial role in achieving this goal.   The architecture of Node.js can be broadly categorized into the following key components: 

1.    Single-Threaded Event Loop    : 
2.    Non-Blocking I/O    : 
3.    V8 JavaScript Engine    : 
4.    Libuv    : 
5.    C++ Bindings    : 

####  Single-Threaded Event Loop 

   A    T THE HEART OF NODE    .js is the single-threaded event loop.   Unlike traditional web servers that create a new thread for each client request, Node.js uses a single thread to handle all incoming requests.   This single-threaded nature might seem like a limitation at first, but it is, in fact, one of Node.js's strengths.   The event loop operates on an asynchronous, non-blocking paradigm, allowing Node.js to handle many concurrent connections efficiently without the overhead of managing multiple threads. 

 The event loop works as follows: 

  Incoming Requests    : When a request arrives, Node.js places it in an event queue. 

  Event Loop Processing    : The event loop continuously checks the event queue for new requests.   It processes each request by executing the corresponding callback functions. 

  I/O Operations    : If a request involves I/O operations, such as reading from a file or making a network request, Node.js offloads these tasks to the system kernel or worker threads provided by the libuv library.   The event loop does not wait for these operations to complete.   Instead, it continues processing other requests in the queue. 

  Callbacks    : Once the I/O operations are completed, the callbacks associated with these operations are added to the event queue.   The event loop picks them up and executes them, ensuring that the application remains responsive and efficient. 

 This non-blocking, event-driven model allows Node.js to handle a high number of concurrent connections with low latency, making it ideal for real-time applications like chat servers, online gaming, and live streaming. 

 ![image](d2d_images/image024.png)

####  Non-Blocking I/O 

   N    ODE.JS'S NON-BLOCKING    I/O operations are integral to its architecture.   In traditional server environments, I/O operations, such as reading a file or querying a database, block the execution of the program until the operation completes.   This blocking behavior can lead to inefficiencies and scalability issues, especially when handling multiple simultaneous requests. 

 Node.js, on the other hand, uses non-blocking I/O operations.   When an I/O operation is initiated, Node.js does not wait for it to complete.   Instead, it registers a callback function and moves on to handle other tasks.   Once the I/O operation finishes, the callback function is executed, allowing the application to process the result of the operation.   This approach ensures that the application remains responsive and can handle many concurrent connections without being bogged down by slow I/O operations. 

####  V8 JavaScript Engine 

   T    HE V8 JAVASCRIPT ENGINE    , developed by Google, is a crucial component of Node.js.   V8 compiles JavaScript code directly into machine code, allowing for fast and efficient execution.   Originally designed for the Google Chrome browser, V8 has been adapted for server-side use in Node.js. 

 V8's performance optimizations, such as just-in-time (JIT) compilation, garbage collection, and efficient memory management, contribute to Node.js's speed and scalability.   By leveraging V8, Node.js can execute JavaScript code at near-native speeds, making it a powerful platform for building high-performance applications. 

####  Libuv 

   L    IBUV IS A MULTI-PLATFORM    support library that provides Node.js with its asynchronous I/O capabilities.   It is responsible for abstracting the underlying operating system mechanisms, allowing Node.js to perform non-blocking I/O operations across different platforms, including Windows, macOS, and various Unix-like systems. 

 Libuv provides the following core functionalities: 

  Event Loop    : The event loop mechanism that drives the execution of callback functions in Node.js. 

  Thread Pool    : A pool of worker threads that handle file system operations, DNS lookups, and other tasks that would otherwise block the event loop. 

  Asynchronous I/O    : Non-blocking file system and network operations. 

  Timers    : Mechanisms for scheduling and executing callback functions after a specified delay. 

 By offloading blocking operations to worker threads and utilizing asynchronous I/O, libuv ensures that the Node.js event loop remains free to handle incoming requests, maintaining high throughput and responsiveness. 

####  C++ Bindings 

   N    ODE.JS'S ARCHITECTURE    also includes C++ bindings that allow it to interface with lower-level system functionalities and native libraries.   These bindings enable Node.js to execute performance-critical operations and leverage existing C/C++ libraries, extending its capabilities beyond pure JavaScript. 

 Node.js modules, such as the    fs    module for file system operations and the    net    module for networking, are implemented using C++ bindings.   This approach ensures that these modules can perform efficiently and interact seamlessly with the underlying operating system. 

####  Practical Example: How the Architecture Works Together 

   T    O ILLUSTRATE HOW THESE    components work together, let's consider a practical example of a simple web server built with Node.js: 

 const http =    require    ('http'); 

 const server = http.    createServer    ((req, res) => { 

 if (req.method === 'GET' && req.url === '/') { 

 res.    writeHead    (200, { 'Content-Type': 'text/plain' }); 

 res.    end    ('Hello, World!\\n'); 

 } else { 

 res.    writeHead    (404, { 'Content-Type': 'text/plain' }); 

 res.    end    ('Not Found\\n'); 

 } 

 }); 

 server.    listen    (3000, () => { 

 console.log('Server running at http://localhost:3000/'); 

 }); 

 –––––––– 

 ![image](d2d_images/scene_break.png) 

   I    N THIS EXAMPLE:  

1.    Single-Threaded Event Loop    : The    createServer    function sets up an HTTP server that listens for incoming requests.   Each request is added to the event queue, and the event loop processes these requests one by one. 
2.    Non-Blocking I/O    : When a request is received, the server processes it without blocking the event loop.   If any I/O operations were involved (e.g., reading a file), they would be handled asynchronously, allowing the server to remain responsive. 
3.    V8 Engine    : The JavaScript code is executed by the V8 engine, ensuring fast performance. 
4.    Libuv    : Any low-level asynchronous operations (e.g., handling network connections) are managed by libuv, which abstracts the platform-specific details. 
5.    C++ Bindings    : The    http    module internally uses C++ bindings to efficiently handle network requests and responses. 

 ![image](d2d_images/image032.png)

 Node.js's architecture, characterized by its single-threaded event loop, non-blocking I/O, V8 engine, libuv library, and C++ bindings, enables it to build high-performance, scalable network applications.   By understanding these components, developers can leverage Node.js to create efficient and responsive applications that meet the demands of modern web development. 

##  ​   1.4.   Installing Node.js 

   G    ETTING STARTED WITH    Node.js involves setting up the runtime environment on your system.   Node.js can be installed on various operating systems, including Windows, macOS, and Linux.   This section will guide you through the installation process for each of these platforms, ensuring that you have a smooth and successful setup. 

####  Installing Node.js on Windows 

1.    Download the Installer    :  
    *    Visit the official Node.js website at  [ nodejs.org ](https://nodejs.org)  . 

 ![image](d2d_images/image033.png)

   Y    OU WILL SEE TWO VERSIONS    available for download: the LTS (Long Term Support) version and the Current version.   For most users, it is recommended to download the LTS version as it is more stable and suitable for production use. 

 Click on the appropriate installer for Windows to download the    .msi    file. 

1.    Run the Installer    : 

 Once the download is complete, open the    .msi    file to run the installer. 

 ![image](d2d_images/image016.png)

*    Follow the prompts in the Node.js Setup Wizard.   The default settings are sufficient for most users. 

 ![image](d2d_images/image019.png)

 ![image](d2d_images/image228.png)

 Make sure to check the box that says "Automatically install the necessary tools" to install additional tools required for native modules, such as Python and the Visual Studio Build Tools. 

 ![image](d2d_images/image085.png)

 ![image](d2d_images/image036.png)

1.    Verify the Installation    : 

 After the installation is complete, open a command prompt (you can search for    cmd    in the Start menu). 

 Type    node -v    and press Enter.   This command will display the installed version of Node.js. 

 ![image](d2d_images/image068.png)

 Type    npm -v    and press Enter to check the installed version of npm (Node Package Manager). 

 ![image](d2d_images/image053.png)

1.    Update npm (Optional)    : 

 Although Node.js comes with npm pre-installed, it is a good practice to update npm to the latest version. 

 In the command prompt, type    npm install -g npm    and press Enter. 

####  Installing Node.js on macOS 

1.    Using the Installer    : 

 Visit the official Node.js website at  [ nodejs.org ](https://nodejs.org)  . 

 Download the macOS installer (    .pkg    file) for the LTS version. 

 Open the downloaded    .pkg    file and follow the prompts to install Node.js. 

1.    Using Homebrew    : 

 Alternatively, you can use Homebrew, a popular package manager for macOS, to install Node.js. 

 If you don't have Homebrew installed, open the Terminal and run the following command to install it: 

   /B    IN/BASH -C "$(CURL    -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)" 

 Once Homebrew is installed, you can install Node.js by running: 

 brew install node 

 ![image](d2d_images/image145.png)

     Verify the Installation    : 

 Open the Terminal and type    node -v    to check the installed version of Node.js. 

 Type    npm -v    to verify the installed version of npm. 

     Update npm (Optional)    : 

 To update npm to the latest version, run the following command in the Terminal: 

 npm install -g npm 

####  Installing Node.js on Linux 

   F    OR LINUX USERS, THE    installation process may vary slightly depending on the distribution you are using.   Here are the steps for some common distributions: 

1.    Debian and Ubuntu    : 

 Open the Terminal and run the following commands to install Node.js from the official NodeSource repository: 

 curl -fsSL https://deb.nodesource.com/setup\_lts.x | sudo -E bash - 

 sudo apt-get install -y nodejs 

 –––––––– 

 ![image](d2d_images/scene_break.png) 

   T    HIS SCRIPT WILL ADD    the NodeSource repository and install Node.js along with npm. 

     CentOS and Fedora    : 

 For CentOS, run the following commands to add the NodeSource repository and install Node.js: 

 curl -fsSL https://rpm.nodesource.com/setup\_lts.x | sudo bash - 

 sudo yum install -y nodejs 

 For Fedora, you can use the same commands as CentOS, but use    dnf    instead of    yum    : 

 curl -fsSL https://rpm.nodesource.com/setup\_lts.x | sudo bash - 

 sudo dnf install -y nodejs 

  Arch Linux    : 

 Open the Terminal and run the following command to install Node.js using the package manager: 

 sudo pacman -S nodejs npm 

  Verify the Installation    : 

 After installation, verify the Node.js and npm versions by running the following commands in the Terminal: 

 node -v 

 npm -v 

  Update npm (Optional)    : 

 To update npm to the latest version, run: 

 npm install -g npm 

##  ​   1.5.   Setting Up the Development Environment 

   V    ISUAL STUDIO CODE    (VS Code) is one of the most popular code editors among developers due to its lightweight nature, extensive customization options, and robust features.   Setting up your Node.js development environment in VS Code will enhance your productivity and make coding a pleasant experience.   Here’s how to get started: 

####  Step 1: Installing Visual Studio Code 

    D    OWNLOAD VS CODE     : 

 Go to the  [ official Visual Studio Code website ](https://code.visualstudio.com/)  . 

 Download the appropriate installer for your operating system (Windows, macOS, or Linux). 

  Install VS Code    : 

 Follow the installation instructions specific to your operating system to install VS Code. 

####  Step 2: Setting Up Your Node.js Project 

  Create a Project Directory    : 

 Open VS Code. 

 Use the built-in terminal in VS Code (you can open it by pressing \`Ctrl+\`\`) to create a new directory for your project: 

   M    KDIR MY-NODE-PROJECT  

 ![image](d2d_images/image122.png)

 cd my-node-project 

 ![image](d2d_images/image221.png)

 ![image](d2d_images/image037.png)

  Initialize a Node.js Project    : 

 Initialize your project by creating a    package.json    file: 

 npm init 

 Follow the prompts to enter your project details.   You can accept the default values by pressing Enter. 

 ![image](d2d_images/image230.png)

 ![image](d2d_images/image009.png)

####  Step 4: Installing Extensions in VS Code 

   T    O ENHANCE YOUR NODE    .js development experience, install the following essential extensions: 

  ESLint    : 

 ESLint helps identify and fix code quality issues. 

 To install, search for "ESLint" in the Extensions view and click Install. 

 ![image](d2d_images/image018.png)

  Prettier - Code Formatter    : 

 Prettier formats your code consistently. 

 To install, search for "Prettier" in the Extensions view and click Install. 

 ![image](d2d_images/image042.png)

  Nodemon    : 

 Nodemon automatically restarts your Node.js application when file changes are detected. 

 Although Nodemon is not an extension, you can install it globally via npm: 

 npm install -g nodemon 

 ![image](d2d_images/image136.png)

####  Step 5: Configuring Your Project 

 ![image](d2d_images/image133.png)   Creating Essential Files    : 

*    Create an index.js file in your project directory.   This will be the entry point for your Node.js application: 

   C    ONSOLE.     log    ('Hello, World!'); 

  Setting Up ESLint    : 

 Initialize ESLint in your project: 

 npx eslint—init 

 ![image](d2d_images/image121.png)

 Follow the prompts to set up your ESLint configuration.   This will create an    .eslintrc    file in your project directory. 

 ![image](d2d_images/image074.png)

  Updating     package.json    : 

 Add a start script to your    package.json    to use Nodemon for running your application: 

 "scripts": { 

 "test": "echo \\"Error: no test specified\\" && exit 1", 

 "start": "nodemon index.js" 

 }, 

 ![image](d2d_images/image128.png)

####  Step 6: Running Your Node.js Application 

  Using VS Code Terminal    : 

 Open the terminal in VS Code (\`Ctrl+\`\`). 

 Run your application using the start script: 

   N    PM START  

 Nodemon will start your application and automatically restart it whenever you make changes to the code. 

 ![image](d2d_images/image174.png)

 ![image](d2d_images/image011.png)

 By setting up your development environment in Visual Studio Code, you create a powerful and efficient workspace tailored for Node.js development.   With the right extensions, configurations, and tools, VS Code can significantly streamline your workflow, making coding more enjoyable and productive. 

##  ​   1.6.   Creating a Basic Web Server 

   C    REATING A BASIC WEB    server using Node.js is an excellent way to understand how the platform works and to see its simplicity and power in action.   Let’s go through the steps to set up your first Node.js web server, explaining every detail to ensure beginners can follow along easily. 

####  ![image](d2d_images/image091.png)  Step 1: Setting Up Your Project 

   I    N THE EXPLORER PANEL    on the left, click the "New File" button or right-click on your project folder and select "New File." 

 Name the file    server.js    .   This will be the file where we write our server code. 

####  Step 2: Writing the Server Code 

  Write the Code    : 

 Open    server.js    and type the following code: 

   C    ONST HTTP =     require    ('http'); 

 const hostname = '127.0.0.1'; 

 const port = 3000; 

 const server = http.    createServer    ((req, res) => { 

 res.statusCode = 200; 

 res.    setHeader    ('Content-Type', 'text/plain'); 

 res.    end    ('Hello, World!\\n'); 

 }); 

 server.    listen    (port, hostname, () => { 

 console.    log    (\`Server running at http://${hostname}:${port}/\`); 

 }); 

 Let's break down this code to understand what each part does. 

     Understanding the Code    : 

  Importing the     http     Module    : 

 const http =    require    ('http'); 

 This line imports the built-in    http    module in Node.js.   Modules are reusable pieces of code that can be included in your application.   The    http    module provides the functionality to create an HTTP server, which can handle HTTP requests and responses. 

  Defining the Hostname and Port    : 

 const hostname = '127.0.0.1'; 

 const port = 3000; 

 These lines define the hostname and port number where the server will listen for incoming requests.    127.0.0.1    is the localhost address, meaning the server will only be accessible from your computer.   The port number    3000    is arbitrary and can be any available port, but    3000    is commonly used for development servers. 

     Creating the Server    : 

 const server = http.    createServer    ((req, res) => { 

 res.statusCode = 200; 

 res.    setHeader    ('Content-Type', 'text/plain'); 

 res.    end    ('Hello, World!\\n'); 

 }); 

   This line creates an HTTP server.   The    createServer    function takes a callback function that is executed each time a request is received.   The callback function has two parameters:    req    (the request object) and    res    (the response object). 

  req    represents the incoming request, containing information like the request URL, method, headers, etc. 

  res    represents the outgoing response, which we use to send data back to the client. 

 Inside the callback function: 

  res.statusCode = 200;    sets the HTTP status code to    200    , indicating a successful response. 

  res.setHeader('Content-Type', 'text/plain');    sets the    Content-Type    header to    text/plain    , indicating that the response content is plain text. 

  res.end('Hello, World!\\n');    sends the response body    Hello, World!    and ends the response.   The    \\n    adds a newline character at the end. 

     Starting the Server    : 

 server.    listen    (port, hostname, () => { 

 console.    log    (\`Server running at http://${hostname}:${port}/\`); 

 }); 

 This line starts the server and makes it listen on the specified hostname and port.   The callback function provided to the    listen    method is executed once the server starts successfully.   It logs a message to the console indicating that the server is running and providing the URL to access it. 

####  Step 3: Running the Server 

  Open the Integrated Terminal    : 

 Open the integrated terminal in VS Code by pressing \`Ctrl+\`\` or by selecting "Terminal" > "New Terminal" from the top menu. 

  Run the Server    : 

 In the terminal, ensure you are in your project directory and run the following command: 

   N    ODE SERVER.JS  

 ![image](d2d_images/image216.png)

 You will see the message    Server running at http://127.0.0.1:3000/    in the terminal.   This means your server is up and running. 

  Access the Server    : 

 Open your web browser and navigate to  [ http://127.0.0.1:3000/ ](http://127.0.0.1:3000/)  . 

 Or simply click on the link inside the terminal. 

 You should see the message    Hello, World!    displayed in your browser.   This is the response sent by your Node.js server. 

 ![image](d2d_images/image191.png)

####  Experimenting with Routes 

   T    O MAKE YOUR SERVER    more interactive, you can extend it to handle different routes (URLs).   Here’s how you can do it: 

  Update the Code    : 

 Modify the    server.js    file as follows: 

 const http =    require    ('http'); 

 const hostname = '127.0.0.1'; 

 const port = 3000; 

 const server = http.    createServer    ((req, res) => { 

 res.statusCode = 200; 

 res.    setHeader    ('Content-Type', 'text/plain'); 

 if (req.url === '/') { 

 res.    end    ('Welcome to the Home Page!\\n'); 

 } else if (req.url === '/about') { 

 res.    end    ('This is the About Page.\\n'); 

 } else { 

 res.statusCode = 404; 

 res.    end    ('Page Not Found\\n'); 

 } 

 }); 

 server.    listen    (port, hostname, () => { 

 console.    log    (\`Server running at http://${hostname}:${port}/\`); 

 }); 

 This updated code introduces routing by checking the    req.url    property to determine the requested URL path. 

 If the requested URL is    /    , the server responds with    Welcome to the Home Page!    . 

 If the requested URL is    /about    , the server responds with    This is the About Page.    . 

 For any other URL, the server responds with a    404    status code and the message    Page Not Found    . 

  Restart the Server    : 

  If the server is already running, stop it by pressing     Ctrl+C     in the terminal.  

 Run the server again with the following command: 

 node server.js 

         Open your web browser and navigate to     http://127.0.0.1:3000/     .   You should see the message     Welcome to the Home Page!     .    ![image](d2d_images/image058.png)

   Navigate to    http://127.0.0.1:3000/about    .   You should see the message    This is the About Page.    . 

 ![image](d2d_images/image197.png)

   Navigate to any other URL, such as    http://127.0.0.1:3000/contact    .   You should see the message    Page Not Found    . 

 ![image](d2d_images/image079.png)

 This example demonstrates how to handle different routes in a Node.js server.   By checking the    req.url    property, you can create custom responses for various endpoints. 

 ![image](d2d_images/image163.png)

 You've now written and executed your first Node.js programs!   Starting with a simple "Hello, World!"   script, you progressed to creating a basic web server and handling different routes.   This foundational knowledge is crucial as you move forward in your Node.js journey.   Understanding how to create and manage servers, handle HTTP requests, and respond to different routes will serve as the building blocks for more complex applications. 

 In the upcoming chapters, we'll dive deeper into the core concepts of Node.js, explore its powerful features, and build more sophisticated applications.   For now, take a moment to appreciate the simplicity and power of Node.js, and get ready for the exciting journey ahead! 

 
|  ![image](d2d_images/chapter_title_corner_decoration_left.png)  ||  ||  ![image](d2d_images/chapter_title_corner_decoration_right.png)  |
| --- | --- | --- |

 ![image](d2d_images/chapter_title_above.png) 

#  ​   ![image](d2d_images/image172.png)  2.   Core Concepts 

 ![image](d2d_images/chapter_title_below.png) 

##  ​   2.1.   The Event Loop 

   T    he event loop is one    of the most fundamental and fascinating concepts in Node.js, enabling its non-blocking, asynchronous nature.   To fully appreciate its power and elegance, let's dive deep into the event loop, breaking down its mechanics, phases, and the principles that make it essential for building high-performance applications. 

####  The Concept of the Event Loop 

   A    T ITS CORE, THE EVENT    loop is an infinite loop that waits for tasks, executes them, and then sleeps until it receives more tasks.   It's like a diligent worker who constantly checks for new jobs to do, completes them, and then immediately looks for the next task.   This continuous cycle allows Node.js to handle numerous tasks efficiently without creating multiple threads. 

 ![image](d2d_images/image004.png)

 Figure 1: Event Loop Architecture 

####  Understanding Synchronous and Asynchronous Execution 

   T    O UNDERSTAND THE EVENT    loop, it's crucial to grasp the difference between synchronous and asynchronous execution.   Synchronous execution means tasks are performed one after the other, and each task must wait for the previous one to complete.   Imagine standing in line at a coffee shop where the barista prepares one order at a time; if someone orders a complicated drink, everyone else has to wait. 

 In contrast, asynchronous execution allows tasks to start and continue without waiting for others to finish.   It's like having multiple baristas at a coffee shop, each handling different orders independently, ensuring faster service for everyone.   Node.js achieves this asynchronous behavior through the event loop, which handles tasks efficiently without blocking the main execution thread. 

####  The Mechanics of the Event Loop 

   T    HE EVENT LOOP CONTINUOUSLY    cycles through a series of phases, each responsible for different types of operations.   Let's break down these phases: 

 ![image](d2d_images/image195.png)

 Figure 2: Phases of the Event Loop 

 ›    Timers Phase    : 

 Executes callbacks scheduled by    setTimeout    and    setInterval    . 

 If you set a timer to trigger after a certain period, the callback associated with that timer will be executed in this phase. 

 ›    I/O Callbacks Phase    : 

 Executes callbacks for completed I/O operations, such as reading from a file or a network request. 

 This phase handles the majority of the asynchronous I/O operations, ensuring that the application remains responsive. 

 ›    Idle, Prepare Phase    : 

 Internal operations of Node.js, preparing the system for the upcoming phases. 

 Not commonly interacted with by developers but crucial for the event loop's functioning. 

 ›    Poll Phase    : 

 Retrieves new I/O events and executes their callbacks. 

 The poll phase is where the event loop spends most of its time, waiting for new events and processing them as they come in. 

 ›    Check Phase    : 

 Executes callbacks scheduled by    setImmediate    . 

 This phase allows developers to run functions immediately after the poll phase, ensuring they are executed as soon as possible. 

 ›    Close Callbacks Phase    : 

 Executes callbacks for closed connections, such as when a TCP socket is closed. 

 Ensures proper cleanup and resource management for closed resources. 

 ![image](d2d_images/image187.png)

####  A Practical Example 

   T    O ILLUSTRATE THE EVENT    loop in action, consider the following example: 

 const fs =    require    ('fs'); 

 // Simulate an I/O operation 

 fs.    readFile    ('C:\\\\Users\\\\Name\\\\Desktop\\\\file.txt', 'utf8', (err, data) => { 

 if (err) throw err; 

 console.    log    (data); 

 }); 

 console.    log    ('Reading file...'); 

 In this example,    fs.readFile    initiates an asynchronous file read operation.   Here's how the event loop processes this: 

 ![image](d2d_images/image099.png)  ![image](d2d_images/image048.png)

  Task Initiation    : 

 The    fs.readFile    function is called to read the contents of 'file.txt'. 

 Node.js offloads this I/O operation to the system's file system handlers and moves to the next task. 

  Immediate Execution    : 

 The    console.log('Reading file...')    statement is executed immediately, printing 'Reading file...'   to the console. 

  Event Loop in Action    : 

 The event loop continues to check for new tasks.   Since the file read operation is offloaded, the event loop is free to process other events. 

 Once the file read operation completes, the associated callback function (    (err, data) => { if (err) throw err; console.log(data); }    ) is added to the event queue. 

  Callback Execution    : 

 The event loop picks up the callback from the event queue and executes it, printing the contents of 'file.txt' to the console. 

 This example demonstrates how Node.js handles I/O operations asynchronously, ensuring the main thread is not blocked and remains available to process other tasks. 

####  The Power of Non-Blocking I/O 

   N    ON-BLOCKING I/O IS    a cornerstone of Node.js's architecture.   In traditional blocking I/O models, tasks like reading a file or querying a database block the entire process until the operation completes.   This approach can severely limit the performance and scalability of applications, especially under heavy loads. 

 Node.js's non-blocking I/O model ensures that these operations are handled in the background, allowing the event loop to continue processing other tasks.   This is particularly beneficial for real-time applications, such as chat servers or online gaming, where responsiveness and low latency are critical. 

 ![image](d2d_images/image209.png)

####  Real-World Applications 

   T    HE EVENT LOOP'S EFFICIENCY    makes Node.js an ideal choice for a wide range of real-world applications: 

 ›    Real-Time Chat Applications    : 

 Chat applications require handling many simultaneous connections with minimal latency.   The event loop's ability to manage numerous tasks concurrently ensures that messages are delivered quickly and efficiently. 

 ›    Online Gaming    : 

 Online games need to process multiple player actions in real-time.   The non-blocking nature of the event loop allows the game server to handle numerous events, such as player movements and interactions, without delay. 

 ›    Collaborative Tools    : 

 Tools like collaborative text editors or project management apps benefit from the event loop's capability to manage real-time updates and notifications, ensuring that all users see changes instantly. 

 ›    Microservices Architecture    : 

 Node.js's event loop is well-suited for microservices, where each service handles specific tasks independently.   The event loop's ability to efficiently manage I/O-bound operations ensures that each microservice can perform optimally. 

 The event loop is the beating heart of Node.js, enabling its asynchronous, non-blocking capabilities.   By continuously cycling through various phases and efficiently managing tasks, the event loop ensures that Node.js applications remain responsive and scalable.   Understanding the event loop empowers developers to write efficient code that takes full advantage of Node.js's strengths, making it an essential concept for anyone working with this powerful platform.   Whether you're building a real-time chat application, an online game, or a collaborative tool, the event loop is the key to unlocking the full potential of Node.js. 

##  ​   2.2.   Understanding Non-blocking I/O 

   N    ON-BLOCKING I/O IS    a cornerstone of Node.js's design, allowing it to handle multiple operations concurrently without waiting for one to complete before starting another.   This approach is crucial for building high-performance, scalable applications, especially those requiring real-time interactions.   Let’s dive into the concept of non-blocking I/O, understand how it works, and explore its significance in the Node.js ecosystem. 

####  The Concept of I/O Operations 

   I    NPUT/OUTPUT (I/O)    operations refer to any operation that involves transferring data to or from a system's peripherals, such as reading from a file, writing to a database, or making network requests.   In traditional, blocking I/O models, these operations can cause significant delays because the program must wait for each operation to complete before moving on to the next task.   This waiting can lead to inefficiencies and a poor user experience, especially under high load conditions. 

####  Blocking vs.   Non-blocking I/O 

    B    LOCKING I/O:     In a blocking I/O model, each I/O operation must complete before the next one begins.   This can be visualized as a queue where each task waits for the previous one to finish: 

 const fs =    require    ('fs'); 

 // Blocking I/O 

 const data = fs.    readFileSync    ('file.txt', 'utf8'); 

 console.    log    (data); 

 console.    log    ('File read complete'); 

 In this example,    fs.readFileSync    is a synchronous, blocking call.   The program halts execution at this line until the file read operation completes.   Only then does it proceed to print the file contents and the 'File read complete' message. 

 ![image](d2d_images/image142.png)

  Non-blocking I/O:    In a non-blocking I/O model, tasks are initiated and allowed to proceed without waiting for them to complete.   The program continues to execute subsequent tasks, and the results of the I/O operations are handled as they become available: 

 const fs =    require    ('fs'); 

 // Non-blocking I/O 

 fs.    readFile    ('file.txt', 'utf8', (err, data) => { 

 if (err) throw err; 

 console.    log    (data); 

 }); 

 console.    log    ('File read initiated'); 

 In this example,    fs.readFile    initiates an asynchronous, non-blocking file read operation.   The program immediately proceeds to the next line, printing 'File read initiated'.   Once the file read operation completes, the callback function is executed, printing the file contents. 

 ![image](d2d_images/image075.png)

####  How Non-blocking I/O Works in Node.js 

   N    ODE.JS USES AN EVENT    -driven, non-blocking I/O model to achieve high concurrency.   Here’s how it works: 

 Event Loop: 

 Node.js runs on a single-threaded event loop that continuously checks for and processes tasks from an event queue. 

 When an asynchronous I/O operation is initiated, the event loop offloads the task to the system's I/O handlers and continues to process other tasks. 

 Callback Functions: 

 For each non-blocking I/O operation, a callback function is provided.   This function is executed once the I/O operation completes, ensuring that the application can handle the results of the operation without blocking the main thread. 

 Event Queue: 

 Completed I/O operations and their callbacks are placed back into the event queue.   The event loop processes these callbacks as they become available, executing them to handle the results of the I/O operations. 

####  Benefits of Non-blocking I/O 

1.   High Performance: 

   N    ON-BLOCKING I/O ALLOWS    Node.js to handle many simultaneous connections efficiently.   By not waiting for I/O operations to complete, the event loop can process other tasks, making the application highly responsive and performant. 

1.   Scalability: 

 Non-blocking I/O is crucial for building scalable applications.   Node.js can manage thousands of concurrent connections with minimal overhead, making it ideal for real-time applications such as chat servers, online gaming, and collaborative tools. 

 ![image](d2d_images/image193.png)

####  Practical Example of Non-blocking I/O 

   C    ONSIDER A WEB SERVER    handling multiple client requests: 

 const http =    require    ('http'); 

 const fs =    require    ('fs'); 

 const server = http.    createServer    ((req, res) => { 

 fs.    readFile    ('index.html', (err, data) => { 

 if (err) { 

 res.    writeHead    (500); 

 res.    end    ('Error loading file'); 

 } else { 

 res.    writeHead    (200, { 'Content-Type': 'text/html' }); 

 res.    end    (data); 

 } 

 }); 

 }); 

 server.    listen    (3000, () => { 

 console.    log    ('Server running at http://localhost:3000/'); 

 }); 

 –––––––– 

 ![image](d2d_images/scene_break.png) 

 ![image](d2d_images/image045.png)

   I    N THIS EXAMPLE:  

 When a request is received, the server initiates a non-blocking file read operation using    fs.readFile    . 

 While the file is being read, the event loop can continue processing other incoming requests. 

 Once the file read operation completes, the callback function is executed, and the file contents are sent as the response. 

 ![image](d2d_images/image206.png)

 ![image](d2d_images/image132.png)

 This non-blocking approach ensures that the server remains responsive and can handle multiple requests concurrently without waiting for each file read operation to complete. 

####  Real-world Applications of Non-blocking I/O 

 ›    Real-time Applications:  

   A    PPLICATIONS LIKE CHAT    servers and online games benefit greatly from non-blocking I/O.   These applications require low latency and high throughput, which Node.js's non-blocking model provides. 

 ›    API Servers:  

 Node.js is widely used for building RESTful APIs.   Non-blocking I/O ensures that API servers can handle numerous requests simultaneously, providing fast and efficient responses. 

 ›    Data Streaming:  

 Non-blocking I/O is ideal for applications that involve data streaming, such as video streaming services.   Node.js can stream data efficiently without buffering the entire content, reducing latency and memory usage. 

 ›    Microservices:  

 In a microservices architecture, services often need to communicate with each other over the network.   Non-blocking I/O allows Node.js to handle these communications efficiently, ensuring that services remain responsive and scalable. 

 ![image](d2d_images/image029.png)

 Non-blocking I/O is a powerful feature that sets Node.js apart from traditional server-side technologies.   By allowing I/O operations to be handled asynchronously, Node.js can achieve high performance, scalability, and resource efficiency.   Understanding and leveraging non-blocking I/O is essential for building robust, real-time applications that can handle the demands of modern web development.   Whether you're developing a chat server, an API, or a data streaming service, the non-blocking I/O model of Node.js provides the foundation for creating highly responsive and scalable applications. 

##  ​   2.3.   Asynchronous Programming in Node.js 

   A    SYNCHRONOUS PROGRAMMING    is at the heart of Node.js, allowing it to handle multiple operations concurrently without waiting for one to complete before starting another.   This approach is crucial for building high-performance, scalable applications, especially those requiring real-time interactions.   Let's dive into the concept of asynchronous programming, understand how it works in Node.js, and explore its significance in the Node.js ecosystem. 

####  The Importance of Asynchronous Programming 

   I    N TRADITIONAL SYNCHRONOUS    programming, operations are executed sequentially, and each operation must wait for the previous one to complete before moving on to the next.   This can lead to inefficiencies and a poor user experience, especially when dealing with I/O-bound tasks like reading files, querying databases, or making network requests.   Asynchronous programming, on the other hand, allows multiple operations to proceed simultaneously, significantly improving the efficiency and responsiveness of applications. 

 ![image](d2d_images/image155.png)

####  Callbacks 

   T    HE SIMPLEST AND MOST    traditional way to handle asynchronous operations in Node.js is through callbacks.   A callback is a function passed as an argument to another function, which is then executed once an asynchronous operation completes. 

 Example: 

 const fs =    require    ('fs'); 

 fs.    readFile    ('file.txt', 'utf8', (err, data) => { 

 if (err) { 

 console.    error    (err); 

 return; 

 } 

 console.    log    (data); 

 }); 

 console.    log    ('File read initiated'); 

 In this example,    fs.readFile    is an asynchronous function that reads the contents of a file.   The second argument is a callback function that is executed once the file read operation completes.   While the file is being read, the program continues to execute the next line, printing 'File read initiated'. 

 ![image](d2d_images/image008.png)

####  Promises 

   W    HILE CALLBACKS ARE    simple and effective, they can lead to "callback hell" or "pyramid of doom" when dealing with multiple nested asynchronous operations.   Promises provide a cleaner and more manageable way to handle asynchronous code.   A promise represents the eventual completion (or failure) of an asynchronous operation and allows chaining of multiple operations. 

 Example: 

 const fs =    require    ('fs').promises; 

 fs.    readFile    ('file.txt', 'utf8') 

 .    then    (data => { 

 console.    log    (data); 

 }) 

 .    catch    (err => { 

 console.    error    (err); 

 }); 

 console.    log    ('File read initiated'); 

 In this example,    fs.readFile    returns a promise.   The    then    method is used to handle the successful completion of the file read operation, and the    catch    method is used to handle any errors.   This approach makes the code more readable and easier to maintain. 

####  Async/Await 

   A    SYNC/AWAIT, INTRODUCED    in ECMAScript 2017 (ES8), provides a syntactic sugar over promises, making asynchronous code look and behave more like synchronous code.   This helps in writing cleaner and more readable asynchronous code. 

 Example: 

 const fs =    require    ('fs').promises; 

 async function    readFile    () { 

 try { 

 const data = await fs.    readFile    ('file.txt', 'utf8'); 

 console.    log    (data); 

 } catch (err) { 

 console.    error    (err); 

 } 

 } 

  readFile    (); 

 console.    log    ('File read initiated'); 

 In this example, the    async    keyword is used to define an asynchronous function, and the    await    keyword is used to wait for the promise returned by    fs.readFile    to resolve.   This allows us to write asynchronous code that appears synchronous, improving readability and maintainability. 

####  Handling Multiple Asynchronous Operations 

   A    SYNCHRONOUS PROGRAMMING    in Node.js often involves handling multiple operations concurrently.   Here are a few techniques to manage this: 

1.    Promise.all:   
    *    Promise.all allows you to wait for multiple promises to complete.   It takes an array of promises and returns a single promise that resolves when all the promises in the array have resolved. 

 Example: 

 const fs =    require    ('fs').promises; 

 async function    readFiles    () { 

 try { 

 const \[file1, file2\] = await Promise.    all    (\[ 

 fs.    readFile    ('file1.txt', 'utf8'), 

 fs.    readFile    ('file2.txt', 'utf8') 

 \]); 

 console.    log    (file1); 

 console.    log    (file2); 

 } catch (err) { 

 console.    error    (err); 

 } 

 } 

  readFiles    (); 

 console.    log    ('File read initiated'); 

 Promise.race: 

  Promise.race    returns a promise that resolves or rejects as soon as one of the promises in the array resolves or rejects. 

 Example: 

 const fetch =    require    ('node-fetch'); 

 const promise1 =    fetch    ('https://api.example.com/data1'); 

 const promise2 =    fetch    ('https://api.example.com/data2'); 

 Promise.    race    (\[promise1, promise2\]) 

 .    then    (response => response.    json    ()) 

 .    then    (data => console.    log    (data)) 

 .    catch    (err => console.    error    (err)); 

 console.    log    ('Fetch initiated'); 

 Parallel Execution: 

 Node.js allows the execution of multiple asynchronous operations in parallel, improving the efficiency and performance of the application. 

 Example: 

 const fs =    require    ('fs').promises; 

 async function    readFilesInParallel    () { 

 try { 

 const file1Promise = fs.    readFile    ('file1.txt', 'utf8'); 

 const file2Promise = fs.    readFile    ('file2.txt', 'utf8'); 

 const file1 = await file1Promise; 

 const file2 = await file2Promise; 

 console.    log    (file1); 

 console.    log    (file2); 

 } catch (err) { 

 console.    error    (err); 

 } 

 } 

  readFilesInParallel    (); 

 console.    log    ('File read initiated'); 

 ![image](d2d_images/image050.png)

####  Error Handling in Asynchronous Code 

   H    ANDLING ERRORS IN    asynchronous code is crucial for building robust applications.   Both promises and async/await provide mechanisms for catching errors. 

 Using Promises: 

 Use the    catch    method to handle errors. 

 Example: 

 fs.    readFile    ('file.txt', 'utf8') 

 .    then    (data => { 

 console.    log    (data); 

 }) 

 .    catch    (err => { 

 console.    error    (err); 

 }); 

 Using Async/Await: 

 Use    try...catch    blocks to handle errors in async functions. 

 Example: 

 async function    readFile    () { 

 try { 

 const data = await fs.    readFile    ('file.txt', 'utf8'); 

 console.    log    (data); 

 } catch (err) { 

 console.    error    (err); 

 } 

 } 

####  Real-world Applications of Asynchronous Programming 

   W    EB SERVERS:  

 Node.js's non-blocking, asynchronous nature makes it ideal for building web servers that handle numerous simultaneous connections efficiently. 

 APIs: 

 Asynchronous programming is crucial for API servers that need to handle multiple requests and interact with databases or other services without blocking the main thread. 

 Real-time Applications: 

 Applications like chat servers and online games benefit from asynchronous programming, ensuring low latency and high responsiveness. 

 Microservices: 

 In a microservices architecture, services often communicate with each other asynchronously, allowing for better scalability and fault tolerance. 

 ![image](d2d_images/image148.png)

###  Example: Building a Simple Weather Application 

   L    ET'S CREATE A SIMPLE    weather application to demonstrate asynchronous programming, the event loop, and non-blocking I/O in Node.js.   This application will fetch weather data from an external API and display it to the user. 

####  Step-by-Step Guide 

 Set Up Your Project 

   F    IRST, CREATE A NEW    directory for your project and navigate into it: 

 mkdir weather-app 

 cd weather-app 

 Initialize a new Node.js project: 

 npm init -y 

 Install the    axios    library to make HTTP requests: 

 npm install axios 

 Create Your Application 

 Create a file named    app.js    in the project directory and open it in your code editor. 

 Write the Code 

 const axios =    require    ('axios'); 

 // Function to fetch weather data 

 async function    fetchWeather    (city) { 

 try { 

 const apiKey = 'your\_api\_key\_here'; // Replace with your OpenWeatherMap API key 

 const url = \`http://api.openweathermap.org/data/2.5/weather?q=${city}&appid=${apiKey}&units=metric\`; 

 const response = await axios.    get    (url); 

 const weatherData = response.data; 

 console.    log    (\`Weather in ${city}:\`); 

 console.    log    (\`Temperature: ${weatherData.main.temp}°C\`); 

 console.    log    (\`Description: ${weatherData.weather\[0\].description}\`); 

 } catch (error) { 

 console.    error    ('Error fetching weather data:', error.message); 

 } 

 } 

 // Get the city name from command line arguments 

 const city = process.argv\[2\]; 

 if (!city) { 

 console.    error    ('Please provide a city name.'); 

 process.    exit    (1); 

 } 

 // Fetch and display the weather data 

  fetchWeather    (city); 

 console.    log    ('Fetching weather data...'); 

 Understanding the Code 

  axios Library    : We use the    axios    library to make HTTP requests to the OpenWeatherMap API.   Axios is a promise-based HTTP client that works in both the browser and Node.js. 

  Asynchronous Function (     fetchWeather     )    : The    fetchWeather    function is defined as an    async    function, allowing us to use the    await    keyword to wait for the promise returned by    axios.get    to resolve. 

  Error Handling    : A    try...catch    block is used to handle any errors that may occur during the HTTP request. 

  Command Line Arguments    : We get the city name from the command line arguments (    process.argv\[2\]    ).   If no city name is provided, the program exits with an error message. 

  Non-blocking I/O    : The    fetchWeather    function is called, and immediately after, the message 'Fetching weather data...'   is printed.   The program does not wait for the HTTP request to complete before printing this message, demonstrating non-blocking I/O. 

###  Important Note 

   T    O RUN THE APPLICATION    , you need an API key from OpenWeatherMap.   Sign up at  [ OpenWeatherMap ](https://openweathermap.org/)  and get your API key.   Replace    'your\_api\_key\_here'    in the code with your actual API key. 

 Now, here's a little heads-up: OpenWeatherMap is kind of like your favorite gourmet coffee shop.   While you get the free samples (the free tier), if you start loving it too much and keep coming back for more (exceeding the free tier), you'll need to pay for each additional "cup of weather data".   If you think it's worth it, go ahead and treat yourself to premium weather forecasts!   Just keep an eye on those charges, so your next weather update doesn’t come with a surprise bill. 

 When everything works, the output is typically something like this: 

 run the application from the command line: 

 node app.js London 

 You should see output similar to this: 

 Fetching weather data... 

 Weather in London: 

 Temperature: 15°C 

 Description: clear sky 

 So, if you're ready to pay for a premium weather experience, go ahead and enjoy detailed forecasts right from your terminal! 

 ![image](d2d_images/image168.png)

##  ​   2.4.   Node.js Modules and NPM 

   N    ODE.JS MODULES AND    the Node Package Manager (NPM) are integral parts of the Node.js ecosystem.   They allow developers to structure their applications in a modular fashion and manage dependencies efficiently.   Understanding how to use modules and NPM is essential for any Node.js developer. 

####  Node.js Modules 

   M    ODULES IN NODE.JS    help in organizing code into smaller, reusable pieces.   This modular approach makes the codebase more maintainable and easier to understand.   Node.js supports three types of modules: built-in modules, user-defined modules, and third-party modules. 

#####  Built-in Modules 

   N    ODE.JS COMES WITH    a set of built-in modules that provide various functionalities, such as file system operations, HTTP servers, and utilities.   These modules are part of the Node.js runtime and do not require any installation. 

 Example: Using the    fs    module 

 const fs =    require    ('fs'); 

 fs.    readFile    ('example.txt', 'utf8', (err, data) => { 

 if (err) throw err; 

 console.    log    (data); 

 }); 

 In this example, the    fs    (file system) module is used to read the contents of a file.   The    readFile    method is asynchronous and takes a callback function that handles the result once the file read operation completes. 

#####  User-defined Modules 

   U    SER-DEFINED MODULES    are custom modules created by developers to encapsulate specific functionality.   These modules can be exported and imported in other parts of the application. 

 Example: Creating and using a user-defined module 

1.    Create a file named     math.js  

 // math.js 

 function    add    (a, b) { 

 return a + b; 

 } 

 function    subtract    (a, b) { 

 return a - b; 

 } 

 module.exports = { 

  add    , 

 subtract 

 }; 

 Import and use the    math.js    module 

 // app.js 

 const math =    require    ('./math'); 

 const sum = math.    add    (5, 3); 

 const difference = math.    subtract    (5, 3); 

 console.    log    (\`Sum: ${sum}\`); // Sum: 8 

 console.    log    (\`Difference: ${difference}\`); // Difference: 2 

 ![image](d2d_images/image158.png)

 ![image](d2d_images/image054.png)  In this example,    math.js    defines two functions,    add    and    subtract    , and exports them using    module.exports    .   These functions are then imported in    app.js    using    require('./math')    and used to perform arithmetic operations. 

#####  Third-party Modules 

   T    HIRD-PARTY MODULES    are modules created by the community and shared through NPM.   They provide a wide range of functionalities, from utility libraries to full-fledged frameworks. 

  Example: Using a third-party module    To use a third-party module, you need to install it using NPM and then require it in your application. 

 npm install lodash 

 const \_ =    require    ('lodash'); 

 const array = \[1, 2, 3, 4, 5\]; 

 const reversedArray = \_.reverse(array.    slice    ()); 

 console.    log    (reversedArray); // \[5, 4, 3, 2, 1\] 

 In this example, we use the    lodash    library, a popular utility library, to reverse an array.   We first install    lodash    using NPM and then import it in our application using    require    . 

 ![image](d2d_images/image116.png)

####  Node Package Manager (NPM) 

   N    PM IS A POWERFUL TOOL    that comes bundled with Node.js.   It allows developers to manage project dependencies, install third-party modules, and share their own modules with the community.   NPM makes it easy to incorporate external libraries and tools into your Node.js projects. 

 ![image](d2d_images/image104.png)

#####  Key NPM Commands 

    I    NITIALIZING A PROJECT     To start a new Node.js project and create a    package.json    file, which holds metadata about your project and its dependencies, you use: 

 npm init 

 This command will prompt you to enter information about your project, or you can use    npm init -y    to generate a    package.json    file with default values. 

  Installing a Package    To install a package and add it to your project's dependencies, you use: 

 npm install <package-name>—save 

 The    —save    flag ensures that the package is listed under the dependencies section of your    package.json    . 

  Installing a Package Globally    Some packages are used as command-line tools and are often installed globally so they can be used from any directory: 

 npm install -g <package-name> 

  Listing Installed Packages    To see all the packages installed in your project, you use: 

 npm list 

  Updating a Package    To update a specific package to the latest version, you use: 

 npm update <package-name> 

#####  Managing Dependencies with    package.json  

   T    HE     package.json    file is a critical component of a Node.js project.   It keeps track of all the dependencies and scripts associated with the project. 

 Example: A simple    package.json    file 

 { 

 "name": "weather-app", 

 "version": "1.0.0", 

 "description": "A simple weather application", 

 "main": "app.js", 

 "scripts": { 

 "start": "node app.js" 

 }, 

 "dependencies": { 

 "axios": "^0.21.1" 

 }, 

 "author": "Your Name", 

 "license": "ISC" 

 } 

 –––––––– 

 ![image](d2d_images/scene_break.png) 

   I    N THIS EXAMPLE, THE     package.json    file includes basic information about the project, a start script to run the application, and a dependency (    axios    ).   The    dependencies    section lists the packages required by the project and their versions. 

 
|  Command  ||  Description  |
| --- | --- |
|  npm init  ||  Initializes a new Node.js project and creates a    package.json    file with metadata and dependencies.  |
|  npm init -y  ||  Initializes a new Node.js project with default values, skipping the interactive prompts.  |
|  npm install <package>  ||  Installs a package and adds it to the    dependencies    section of    package.json    .  |
|  npm install <package>—save  ||  (Deprecated) Same as    npm install <package>    .  |
|  npm install <package>—save-dev  ||  Installs a package and adds it to the    devDependencies    section of    package.json    .  |
|  npm install <package> -g  ||  Installs a package globally, making it available from the command line anywhere on your system.  |
|  npm install  ||  Installs all dependencies listed in    package.json    .  |
|  npm uninstall <package>  ||  Uninstalls a package and removes it from the    dependencies    section of    package.json    .  |
|  npm update <package>  ||  Updates a package to the latest version that matches the version range specified in    package.json    .  |
|  npm outdated  ||  Lists packages that are outdated compared to the latest versions available.  |
|  npm list  ||  Lists all installed packages in the current project along with their dependencies.  |
|  npm list -g  ||  Lists all globally installed packages.  |
|  npm run <script>  ||  Runs a script defined in the    scripts    section of    package.json    .  |
|  npm test  ||  Runs the    test    script defined in    package.json    .  |
|  npm start  ||  Runs the    start    script defined in    package.json    .  |
|  npm stop  ||  Runs the    stop    script defined in    package.json    .  |
|  npm init <initializer>  ||  Initializes a new project using an initializer (e.g.,    npm init react-app    ).  |
|  npm version <newversion>  ||  Bumps the version in    package.json    to a new version (e.g.,    npm version 1.0.1    ).  |
|  npm publish  ||  Publishes a package to the NPM registry.  |
|  npm unpublish <package>  ||  Removes a published package from the NPM registry (can be used with    —force    for unpublishing).  |
|  npm cache clean—force  ||  Clears the NPM cache.  |
|  npm config set <key> <value>  ||  Sets a configuration key to a specified value.  |
|  npm config get <key>  ||  Retrieves the value of a configuration key.  |
|  npm help  ||  Displays help information about NPM.  |
|  npm search <term>  ||  Searches for packages matching the search term in the NPM registry.  |
|  npm audit  ||  Performs a security audit of the project's dependencies.  |
|  npm audit fix  ||  Automatically fixes vulnerabilities found in the project's dependencies.  |
|  npm ci  ||  Installs dependencies from a clean slate using    package-lock.json    , for continuous integration.  |
|  npm rebuild  ||  Rebuilds native addons that were installed with    npm install    .  |
|  npm dedupe  ||  Deduplicates dependencies in the project.  |
|  npm link  ||  Symlinks a package folder during development.  |
|  npm unlink  ||  Removes symlink created by    npm link    .  |
|  npm doctor  ||  Runs a set of checks to ensure your NPM installation is in good shape.  |
|  npm exec <command>  ||  Runs a command from a local or global package.  |

 Table.1 NPM Commands 

 ![image](d2d_images/image025.png)

 Understanding Node.js modules and NPM is essential for any Node.js developer.   Modules help you organize your code into reusable pieces, whether they are built-in, user-defined, or third-party.   NPM simplifies dependency management, allowing you to incorporate a vast ecosystem of packages into your projects effortlessly.   By mastering modules and NPM, you can write cleaner, more maintainable code and leverage the power of the Node.js community to build robust and scalable applications. 

##  ​   2.5.   Using the REPL (Read-Eval-Print Loop) 

   T    HE REPL (READ-EVAL    -Print Loop) is an interactive shell that comes with Node.js.   It allows you to execute JavaScript code line by line and see the results immediately.   This tool is incredibly useful for testing, debugging, and experimenting with JavaScript and Node.js code. 

 ![image](d2d_images/image108.png)

####  What is REPL? 

   T    HE REPL STANDS FOR    : 

  Read    : It reads the user’s input, parses it into JavaScript data structures, and stores it in memory. 

  Eval    : It evaluates the parsed data structure. 

  Print    : It prints the result of the evaluation. 

  Loop    : It loops, waiting for new user input. 

 ![image](d2d_images/image165.png)

   F    IGURE 3: REPL  

 The REPL provides a quick and easy way to try out JavaScript and Node.js code without having to create a new file and run it through the Node.js runtime. 

####  Starting the REPL 

   T    O START THE NODE.JS    REPL, simply open your terminal or command prompt and type: 

 node 

 ![image](d2d_images/image217.png)

 You will see a prompt (    >    ) indicating that the REPL is ready to accept commands. 

####  Basic Usage 

   E    XAMPLE 1: SIMPLE ARITHMETIC  

 > 1 + 2 

 3 

 > 5 \* 10 

 50 

 The REPL reads the input    1 + 2    , evaluates it, prints the result    3    , and then waits for the next input. 

 Example 2: Variable Declaration 

 > let x = 10; 

 undefined 

 > x \* 2 

 20 

 You can declare variables and use them in subsequent commands.   The REPL stores the state of the session, allowing you to interact with previously declared variables. 

####  Using Node.js APIs in the REPL 

   Y    OU CAN ALSO USE NODE    .js built-in modules directly in the REPL. 

 Example: Using the    fs    Module 

 > const fs =    require    ('fs'); 

 undefined 

 > fs.    readFileSync    ('example.txt', 'utf8'); 

 'This is the content of the file.' 

 In this example, the    fs    module is required, and its    readFileSync    method is used to read the contents of a file synchronously. 

####  Multi-line Input 

   T    HE REPL SUPPORTS MULTI    -line input, allowing you to enter more complex code structures such as loops and functions. 

 Example: Defining a Function 

 > function    add    (a, b) { 

 ...   return a + b; 

 ...   } 

 undefined 

 >    add    (5, 10); 

 15 

 The REPL waits for you to finish the function definition before evaluating it.   You can press Enter twice to indicate that you have finished entering the multi-line input. 

####  Special Commands 

   T    ABLE OF REPL COMMANDS  

 
|  Command  ||  Explanation  |
| --- | --- |
|  .help  ||  Displays a list of all the special REPL commands and their descriptions.  |
|  .break  ||  When you get stuck in a multi-line expression, use this to get out of the current context.  |
|  .clear  ||  Alias for    .break    .   It clears the current context in the REPL.  |
|  .exit  ||  Exits the REPL.   You can also use Ctrl+C twice to achieve the same result.  |
|  .save <filename>  ||  Saves the current REPL session to a file.  |
|  .load <filename>  ||  Loads a file into the current REPL session.  |
|  .editor  ||  Enters into a multi-line input mode where you can write multiple lines of code.   Press Ctrl+D to finish and evaluate the code.  |
|  .scope  ||  Displays the current scope's context, including local variables.  |
|  .history  ||  Shows the REPL history of commands executed.  |
|  .set var value  ||  Sets a variable in the REPL context.  |
|  .inspect var  ||  Inspects and prints the details of a variable.  |

####  .help 

    D    ESCRIPTION     : Lists all the special REPL commands available and provides a brief description of each. 

  Usage    : 

 > .help 

 .break  Sometimes you get stuck, this gets you out 

 .clear  Alias for .break 

 .exit  Exit the REPL 

 .help  Print this help message 

 .load  Load JS from a file into the REPL session 

 .save  Save all evaluated commands in this REPL session to a file 

 .editor  Enter editor mode 

 .scope  Show current scope 

 .history  Show REPL history 

 .set  Set a variable in the REPL context 

 .inspect  Inspect a variable in detail 

####   .    break 

    D    ESCRIPTION     : Use this command if you get stuck in the middle of writing a multi-line expression.   It will exit the current expression and return to the REPL prompt. 

  Usage    : 

 > { 

 ...   const x = 10; 

 ...   .break 

 > 

####   .    clear 

    D    ESCRIPTION     : Clears the current REPL context.   It is an alias for    .break    . 

  Usage    : 

 > const x = 10; 

 > .clear 

 > 

####  .exit 

    D    ESCRIPTION     : Exits the REPL.   You can also use    Ctrl+C    twice to exit. 

  Usage    : 

 > .exit 

####  .save <filename> 

    D    ESCRIPTION     : Saves the current REPL session to a file.   This can be useful for saving your work and reviewing it later. 

  Usage    : 

 > .save session.js 

####  .load <filename> 

    D    ESCRIPTION     : Loads and executes a file in the current REPL session.   This allows you to bring in predefined scripts or functions. 

  Usage    : 

 > .load script.js 

####   .    editor 

    D    ESCRIPTION     : Enters into a multi-line input mode where you can write multiple lines of code.   To finish and evaluate the code, press    Ctrl+D    . 

  Usage    : 

 > .editor 

 // Entering editor mode (Ctrl+D to finish, Ctrl+C to cancel) 

 const x = 10; 

 const y = 20; 

 console.log(x + y); 

 Ctrl+D 

 30 

 > 

####  .scope 

    D    ESCRIPTION     : Displays the current scope's context, including local variables and their values.   Useful for debugging and inspecting the current state. 

  Usage    : 

 > const x = 10; 

 > .scope 

 Local { 

 x: 10 

 } 

 > 

####   .    history 

    D    ESCRIPTION     : Shows the REPL history of commands executed.   It helps to review and reuse previous commands. 

  Usage    : 

 > .history 

 1: const x = 10; 

 2: console.log(x); 

 3: .history 

####  .set var value 

    D    ESCRIPTION     : Sets a variable in the REPL context.   This can be useful for dynamically adjusting values during a session. 

  Usage    : 

 > .set y 50 

 > console.log(y); 

 50 

####  .inspect var 

    D    ESCRIPTION     : Inspects and prints the details of a variable.   This is useful for debugging complex objects or variables. 

  Usage    : 

 > const obj = { a: 1, b: 2 }; 

 > .inspect obj 

 { 

 a: 1, 

 b: 2 

 } 

####  Accessing REPL History 

   T    HE REPL KEEPS A HISTORY    of commands you’ve entered.   You can navigate through your history using the up and down arrow keys, making it easy to re-run previous commands or make slight modifications. 

####  Underscore Variable 

   T    HE REPL AUTOMATICALLY    assigns the result of the last evaluated expression to the underscore (    \_    ) variable, allowing you to use it in subsequent commands. 

 Example: Using the Underscore Variable 

 > 5 + 10 

 15 

 > \_ \* 2 

 30 

 In this example, the result of    5 + 10    is    15    , which is then stored in    \_    .   The next command multiplies this result by    2    , yielding    30    . 

 ![image](d2d_images/image082.png)

 The Node.js REPL is a powerful tool for experimenting with JavaScript and Node.js code in an interactive manner.   It allows you to quickly test snippets, debug code, and explore Node.js APIs without the overhead of creating and running separate files.   By understanding and leveraging the features of the REPL, you can significantly enhance your development workflow and productivity. 

 
|  ![image](d2d_images/chapter_title_corner_decoration_left.png)  ||  ||  ![image](d2d_images/chapter_title_corner_decoration_right.png)  |
| --- | --- | --- |

 ![image](d2d_images/chapter_title_above.png) 

#  ​   ![image](d2d_images/image129.png)  3.   File System and Streams 

 ![image](d2d_images/chapter_title_below.png) 

##  ​   3.1.   Reading and Writing Files 

   H    andling files is a    fundamental aspect of many applications.   Whether you're reading configuration files, writing logs, or processing data, understanding how to read and write files efficiently in Node.js is crucial.   Node.js provides the    fs    module, which offers both synchronous and asynchronous methods for interacting with the file system.   Let's explore these concepts in depth. 

 ![image](d2d_images/image225.png)

####  Introduction to the    fs    Module 

   T    HE     fs    (File System) module in Node.js allows you to interact with the file system on your computer.   You can use it to read, write, update, delete, and manage files and directories.   The    fs    module can be imported using: 

 const fs =    require    ('fs'); 

####  Reading Files 

   R    EADING FILES CAN BE    done in two ways: synchronously and asynchronously. 

#####  Synchronous Reading 

   I    N SYNCHRONOUS READING    , the execution of the program pauses until the file reading operation is completed.   This can be straightforward for small files or simple scripts but can block the event loop for larger files or more complex applications. 

 Example: Synchronous Reading 

 const fs =    require    ('fs'); 

 try { 

 const data = fs.    readFileSync    ('example.txt', 'utf8'); 

 console.    log    (data); 

 } catch (err) { 

 console.    error    ('Error reading file:', err); 

 } 

 ![image](d2d_images/image160.png)

 ![image](d2d_images/image013.png)

 In this example: 

  fs.readFileSync('example.txt', 'utf8')    reads the contents of    example.txt    synchronously. 

 The    utf8    argument specifies the encoding. 

 If an error occurs, it is caught and logged to the console. 

#####  Asynchronous Reading 

   A    SYNCHRONOUS READING    allows other operations to continue while the file is being read, making it more suitable for larger files and high-performance applications. 

 Example: Asynchronous Reading 

 const fs =    require    ('fs'); 

 fs.    readFile    ('example.txt', 'utf8', (err, data) => { 

 if (err) { 

 return console.    error    ('Error reading file:', err); 

 } 

 console.    log    (data); 

 }); 

 console.    log    ('Reading file...'); 

 In this example: 

  fs.readFile('example.txt', 'utf8', callback)    reads the file asynchronously. 

 The callback function handles the file data or any errors. 

 The message 'Reading file...'   is logged immediately, demonstrating non-blocking behavior. 

####  Writing Files 

   W    RITING TO FILES CAN    also be done synchronously or asynchronously. 

#####  Synchronous Writing 

   E    XAMPLE: SYNCHRONOUS    Writing 

 const fs =    require    ('fs'); 

 const data = 'If somethings important enough, you should try.   Even if - the probable outcome is failure.Elon Musk'; 

 try { 

 fs.    writeFileSync    ('C:\\\\Users\\\\MOAML\\\\Desktop\\\\file.txt', data); 

 console.    log    ('File written successfully'); 

 } catch (err) { 

 console.    error    ('Error writing file:', err); 

 } 

 ![image](d2d_images/image202.png)

 ![image](d2d_images/image056.png)

 Unimportant note..   I use vs code  to open text files 

 In this example: 

*    fs.writeFileSync('example.txt', data)    writes the string    data    to    example.txt    synchronously.  
*    If an error occurs, it is caught and logged to the console. 

#####  Asynchronous Writing 

   E    XAMPLE: ASYNCHRONOUS    Writing 

 const fs =    require    ('fs'); 

 const data = 'Hello, world!'; 

 fs.    writeFile    ('example.txt', data, (err) => { 

 if (err) { 

 return console.    error    ('Error writing file:', err); 

 } 

 console.    log    ('File written successfully'); 

 }); 

 console.    log    ('Writing file...'); 

 In this example: 

  fs.writeFile('example.txt', data, callback)    writes the string    data    to    example.txt    asynchronously. 

 The callback function handles any errors. 

 The message 'Writing file...'   is logged immediately, demonstrating non-blocking behavior. 

####  Appending to Files 

   S    OMETIMES, YOU MAY    need to add data to an existing file rather than overwriting it.   The    fs.appendFile    and    fs.appendFileSync    methods are used for this purpose. 

 Example: Asynchronous Appending 

 const fs =    require    ('fs'); 

 const data = 'Appending some text...🥴 \\n'; 

 fs.    appendFile    (' C:\\\\Users\\\\NAME\\\\Desktop\\\\file.txt ', data, (err) => { 

 if (err) { 

 return console.    error    ('Error appending to file:', err); 

 } 

 console.    log    ('File appended successfully'); 

 }); 

 console.    log    ('Appending to file...'); 

 ![image](d2d_images/image188.png)

 ![image](d2d_images/image101.png)

 In this example: 

  fs.appendFile('example.txt', data, callback)    appends the string    data    to    example.txt    asynchronously. 

 The callback function handles any errors. 

 The message 'Appending to file...'   is logged immediately, demonstrating non-blocking behavior. 

####  Deleting Files 

   T    O DELETE FILES, YOU    can use the    fs.unlink    and    fs.unlinkSync    methods. 

 Example: Asynchronous Deleting 

 const fs =    require    ('fs'); 

 fs.    unlink    (C:\\\\Users\\\\NAME\\\\Desktop\\\\file.txt', (err) => { 

 if (err) { 

 return console.    error    ('Error deleting file:', err); 

 } 

 console.    log    ('File deleted successfully'); 

 }); 

 console.    log    ('Deleting file...'); 

 ![image](d2d_images/image118.png)

 ![image](d2d_images/image084.png)

 In this example: 

  fs.unlink('example.txt', callback)    deletes    example.txt    asynchronously. 

 The callback function handles any errors. 

 The message 'Deleting file...'   is logged immediately, demonstrating non-blocking behavior. 

####  Watching Files for Changes 

   N    ODE.JS CAN WATCH FOR    changes in a file or directory, which is useful for implementing features like live reloads in development environments. 

 Example: Watching a File 

 const fs =    require    ('fs'); 

 fs.    watch    ('example.txt', (eventType, filename) => { 

 if (filename) { 

 console.    log    (\`File ${filename} has been modified\`); 

 } 

 }); 

 console.    log    ('Watching file...'); 

 In this example: 

  fs.watch('example.txt', callback)    watches    example.txt    for changes. 

 The callback function logs a message whenever the file is modified. 

 The message 'Watching file...'   is logged immediately. 

 ![image](d2d_images/image087.png)

 ![image](d2d_images/image227.png)

 Reading and writing files in Node.js is made simple and efficient by the    fs    module.   Whether you choose synchronous or asynchronous methods depends on the specific needs of your application.   Synchronous methods are straightforward but can block the event loop, while asynchronous methods are non-blocking and better suited for performance-critical applications.   By understanding and leveraging these capabilities, you can handle file operations effectively in your Node.js projects. 

##  ​   3.2.   Working with Directories 

   D    IRECTORIES ARE ESSENTIAL    for organizing files within a file system.   Node.js provides a robust set of methods through the    fs    module to create, read, update, and delete directories.   Understanding how to work with directories is crucial for managing your application's file structure efficiently. 

####  Creating Directories 

   T    O CREATE DIRECTORIES    , Node.js offers both synchronous and asynchronous methods. 

#####  Synchronous Directory Creation 

   E    XAMPLE: SYNCHRONOUS    Directory Creation 

 const fs =    require    ('fs'); 

 try { 

 if (!fs.    existsSync    ('new-directory')) { 

 fs.    mkdirSync    ('new-directory'); 

 console.    log    ('Directory created successfully'); 

 } else { 

 console.    log    ('Directory already exists'); 

 } 

 } catch (err) { 

 console.    error    ('Error creating directory:', err); 

 } 

 In this example: 

  fs.existsSync('new-directory')    checks if the directory already exists. 

  fs.mkdirSync('new-directory')    creates the directory if it doesn't exist. 

 Errors are caught and logged to the console. 

#####  Asynchronous Directory Creation 

   E    XAMPLE: ASYNCHRONOUS    Directory Creation 

 const fs =    require    ('fs'); 

 fs.    mkdir    ('new-directory', (err) => { 

 if (err) { 

 return console.    error    ('Error creating directory:', err); 

 } 

 console.    log    ('Directory created successfully'); 

 }); 

 console.    log    ('Creating directory...'); 

 ![image](d2d_images/image010.png)

 In this example: 

  fs.mkdir('new-directory', callback)    creates the directory asynchronously. 

 The callback function handles any errors. 

 The message 'Creating directory...'   is logged immediately, demonstrating non-blocking behavior. 

 ![image](d2d_images/image139.png)

####  Reading Directories 

   R    EADING THE CONTENTS    of a directory can be done synchronously or asynchronously to list files and subdirectories. 

#####  Synchronous Directory Reading 

   E    XAMPLE: SYNCHRONOUS    Directory Reading 

 const fs =    require    ('fs'); 

 try { 

 const files = fs.    readdirSync    ('.'); 

 console.    log    ('Files in directory:'); 

 files.    forEach    (file => { 

 console.    log    (file); 

 }); 

 } catch (err) { 

 console.    error    ('Error reading directory:', err); 

 } 

 In this example: 

*    fs.readdirSync('.')    reads the contents of the current directory synchronously.  
*    The contents are logged to the console. 

#####  Asynchronous Directory Reading 

   E    XAMPLE: ASYNCHRONOUS    Directory Reading 

 const fs =    require    ('fs'); 

 fs.    readdir    ('.', (err, files) => { 

 if (err) { 

 return console.    error    ('Error reading directory:', err); 

 } 

 console.    log    ('Files in directory:'); 

 files.    forEach    (file => { 

 console.    log    (file); 

 }); 

 }); 

 console.    log    ('Reading directory...'); 

 In this example: 

*    fs.readdir('.', callback)    reads the contents of the current directory asynchronously.  
*    The callback function handles the file list and any errors. 
*    The message 'Reading directory...'   is logged immediately, demonstrating non-blocking behavior. 

 ![image](d2d_images/image035.png)

####  Deleting Directories 

   T    O DELETE DIRECTORIES    , you can use both synchronous and asynchronous methods. 

#####  Synchronous Directory Deletion 

   E    XAMPLE: SYNCHRONOUS    Directory Deletion 

 const fs =    require    ('fs'); 

 try { 

 if (fs.    existsSync    ('new-directory')) { 

 fs.    rmdirSync    ('new-directory'); 

 console.    log    ('Directory deleted successfully'); 

 } else { 

 console.    log    ('Directory does not exist'); 

 } 

 } catch (err) { 

 console.    error    ('Error deleting directory:', err); 

 } 

 In this example: 

*    fs.existsSync('new-directory')    checks if the directory exists.  
*    fs.rmdirSync('new-directory')    deletes the directory if it exists.  
*    Errors are caught and logged to the console. 

 ![image](d2d_images/image038.png)

#####  Asynchronous Directory Deletion 

   E    XAMPLE: ASYNCHRONOUS    Directory Deletion 

 const fs =    require    ('fs'); 

 fs.    rmdir    ('new-directory', (err) => { 

 if (err) { 

 return console.    error    ('Error deleting directory:', err); 

 } 

 console.    log    ('Directory deleted successfully'); 

 }); 

 console.    log    ('Deleting directory...'); 

 In this example: 

*    fs.rmdir('new-directory', callback)    deletes the directory asynchronously.  
*    The callback function handles any errors. 
*    The message 'Deleting directory...'   is logged immediately, demonstrating non-blocking behavior. 

####  Renaming Directories 

   N    ODE.JS ALLOWS YOU    to rename directories using the    fs.rename    and    fs.renameSync    methods. 

#####  Synchronous Directory Renaming 

   E    XAMPLE: SYNCHRONOUS    Directory Renaming 

 const fs =    require    ('fs'); 

 try { 

 fs.    renameSync    ('old-directory', 'new-directory'); 

 console.    log    ('Directory renamed successfully'); 

 } catch (err) { 

 console.    error    ('Error renaming directory:', err); 

 } 

 In this example: 

*    fs.renameSync('old-directory', 'new-directory')    renames the directory synchronously.  
*    Errors are caught and logged to the console. 

#####  Asynchronous Directory Renaming 

   E    XAMPLE: ASYNCHRONOUS    Directory Renaming 

 const fs =    require    ('fs'); 

 fs.    rename    ('old-directory', 'new-directory', (err) => { 

 if (err) { 

 return console.    error    ('Error renaming directory:', err); 

 } 

 console.    log    ('Directory renamed successfully'); 

 }); 

 console.    log    ('Renaming directory...'); 

 In this example: 

*    fs.rename('old-directory', 'new-directory', callback)    renames the directory asynchronously.  
*    The callback function handles any errors. 
*    The message 'Renaming directory...'   is logged immediately, demonstrating non-blocking behavior. 

####  Watching Directories 

   N    ODE.JS CAN MONITOR    changes in a directory, such as file additions, deletions, or modifications. 

 Example: Watching a Directory 

 const fs =    require    ('fs'); 

 fs.    watch    ('new-directory', (eventType, filename) => { 

 if (filename) { 

 console.    log    (\`Event: ${eventType} on file: ${filename}\`); 

 } else { 

 console.    log    (\`Event: ${eventType}\`); 

 } 

 }); 

 console.    log    ('Watching directory...'); 

 In this example: 

*    fs.watch('new-directory', callback)    watches    new-directory    for changes.  
*    The callback function logs the type of event and the affected file. 
*    The message 'Watching directory...'   is logged immediately. 

 ![image](d2d_images/image130.png)

 Working with directories in Node.js is made straightforward by the    fs    module.   You can create, read, rename, delete, and monitor directories using both synchronous and asynchronous methods.   While synchronous methods are simple and easy to use, asynchronous methods are preferred for performance-critical applications as they do not block the event loop.   Understanding these operations allows you to manage your application's file structure effectively, ensuring smooth and efficient handling of directories. 

##  ​   3.3.   Streams and Buffers 

   S    TREAMS AND BUFFERS    are fundamental to handling I/O operations efficiently in Node.js.   They enable reading and writing data in a continuous flow, making it possible to work with large datasets or files without loading everything into memory at once.   Let's dive deep into these concepts to understand their roles and how to use them effectively. 

 ![image](d2d_images/image180.png)

####  Understanding Streams 

   S    TREAMS ARE OBJECTS    in Node.js that allow you to read data from a source or write data to a destination in a sequential manner.   They provide a way to handle data in chunks, which is crucial for performance and memory management. 

#####  Types of Streams 

1.    Readable Streams    : Used to read data from a source. 
2.    Writable Streams    : Used to write data to a destination. 
3.    Duplex Streams    : Can both read and write data. 
4.    Transform Streams    : Duplex streams that can modify or transform the data as it is read or written. 

#####  Readable Streams 

   R    EADABLE STREAMS ALLOW    you to read data from a source, such as a file or an HTTP response. 

 Example: Reading a File with Readable Streams 

 const fs =    require    ('fs'); 

 const readStream = fs.    createReadStream    ('example.txt', 'utf8'); 

 readStream.    on    ('data', (chunk) => { 

 console.    log    ('Reading chunk:', chunk); 

 }); 

 readStream.    on    ('end', () => { 

 console.    log    ('File reading completed'); 

 }); 

 readStream.    on    ('error', (err) => { 

 console.    error    ('Error reading file:', err); 

 }); 

 ![image](d2d_images/image078.png)

 In this example: 

*    fs.createReadStream('example.txt', 'utf8')    creates a readable stream for    example.txt    .  
*     The    data    event is emitted each time a chunk of data is read.  
*     The    end    event is emitted when the entire file has been read.  
*     The    error    event is emitted if an error occurs while reading the file.  

#####  Writable Streams 

   W    RITABLE STREAMS ALLOW    you to write data to a destination, such as a file or a network socket. 

 Example: Writing to a File with Writable Streams 

 const fs =    require    ('fs'); 

 const writeStream = fs.    createWriteStream    ('example.txt'); 

 writeStream.    write    ('Hello, ', 'utf8'); 

 writeStream.    write    ('world!', 'utf8'); 

 writeStream.    end    (); 

 writeStream.    on    ('finish', () => { 

 console.    log    ('File writing completed'); 

 }); 

 writeStream.    on    ('error', (err) => { 

 console.    error    ('Error writing to file:', err); 

 }); 

 In this example: 

*    fs.createWriteStream('example.txt')    creates a writable stream for    example.txt    .  
*     The    write    method writes data to the stream.  
*     The    end    method indicates that no more data will be written.  
*     The    finish    event is emitted when all data has been written.  
*     The    error    event is emitted if an error occurs while writing to the file.  

#####  Duplex Streams 

   D    UPLEX STREAMS CAN    perform both read and write operations, making them useful for network communications and similar tasks. 

 Example: Using a Duplex Stream 

 const net =    require    ('net'); 

 const server = net.    createServer    ((socket) => { 

 socket.    write    ('Welcome to the server!\\n'); 

 socket.    on    ('data', (data) => { 

 console.    log    ('Received:', data.    toString    ()); 

 socket.    write    ('You said: ' + data); 

 }); 

 socket.    on    ('end', () => { 

 console.    log    ('Client disconnected'); 

 }); 

 socket.    on    ('error', (err) => { 

 console.    error    ('Error:', err); 

 }); 

 }); 

 server.    listen    (3000, () => { 

 console.    log    ('Server listening on port 3000'); 

 }); 

 In this example: 

 ›    net.createServer    creates a TCP server that uses duplex streams. 

 ›  The    socket    object represents a duplex stream that can read data from the client and write data back to the client. 

#####  Transform Streams 

   T    RANSFORM STREAMS ARE    duplex streams that can modify or transform the data as it is read or written.   They are particularly useful for tasks like data compression and encryption. 

 Example: Transform Stream with zlib 

 const fs =    require    ('fs'); 

 const zlib =    require    ('zlib'); 

 const readStream = fs.    createReadStream    ('example.txt', 'utf8'); 

 const writeStream = fs.    createWriteStream    ('example.txt.gz'); 

 const gzip = zlib.    createGzip    (); 

 readStream.    pipe    (gzip).    pipe    (writeStream); 

 writeStream.    on    ('finish', () => { 

 console.    log    ('File compression completed'); 

 }); 

 In this example: 

*    zlib.createGzip    creates a transform stream that compresses data.  
*     The    pipe    method is used to chain the readable stream, transform stream, and writable stream together.  
*     Data read from    example.txt    is compressed and written to    example.txt.gz    .  

####  Understanding Buffers 

   B    UFFERS ARE TEMPORARY    storage areas for binary data.   In Node.js, buffers are used to handle raw binary data, making them essential for working with streams and other I/O operations. 

#####  Creating Buffers 

   B    UFFERS CAN BE CREATED    from various sources, such as arrays, strings, or existing buffer data. 

 Example: Creating a Buffer from a String 

 const buffer = Buffer.    from    ('Hello, world!', 'utf8'); 

 console.    log    (buffer); 

 console.    log    (buffer.    toString    ('utf8')); 

 In this example: 

*    Buffer.from('Hello, world!', 'utf8')    creates a buffer from the string 'Hello, world!'   using UTF-8 encoding.  
*     The buffer is then converted back to a string using    buffer.toString('utf8')    .  

#####  Writing to Buffers 

   B    UFFERS PROVIDE METHODS    for writing binary data. 

 Example: Writing to a Buffer 

 const buffer = Buffer.    alloc    (16); 

 buffer.    write    ('Hello, world!', 'utf8'); 

 console.    log    (buffer); 

 console.    log    (buffer.    toString    ('utf8')); 

 In this example: 

*    Buffer.alloc(16)    creates a buffer of 16 bytes.  
*     The    write    method writes the string 'Hello, world!'   to the buffer using UTF-8 encoding.  
*     The buffer is then converted back to a string using    buffer.toString('utf8')    .  

#####  Buffer Operations 

   B    UFFERS SUPPORT VARIOUS    operations for manipulating binary data, such as slicing and concatenating. 

 Example: Buffer Slicing 

 const buffer = Buffer.    from    ('Hello, world!', 'utf8'); 

 const slice = buffer.    slice    (0, 5); 

 console.    log    (slice.    toString    ('utf8')); // Output: Hello 

 In this example: 

*    buffer.slice(0, 5)    creates a new buffer that references a portion of the original buffer.  
*    The slice contains the first 5 bytes of the original buffer, which is then converted to a string. 

 Example: Buffer Concatenation 

 const buffer1 = Buffer.    from    ('Hello, ', 'utf8'); 

 const buffer2 = Buffer.    from    ('world!', 'utf8'); 

 const combined = Buffer.    concat    (\[buffer1, buffer2\]); 

 console.    log    (combined.    toString    ('utf8')); // Output: Hello, world! 

 In this example: 

*    Buffer.concat(\[buffer1, buffer2\])    concatenates    buffer1    and    buffer2    into a single buffer.  
*    The combined buffer is then converted to a string. 

####  Practical Applications of Streams and Buffers 

   S    TREAMS AND BUFFERS    are used in various real-world applications, such as: 

1.    File Processing    :  
    *    Reading and writing large files without loading them entirely into memory. 
    *    Example: Processing log files or media files. 
2.    Network Communication    :  
    *    Handling data transfer over networks efficiently. 
    *    Example: Building HTTP servers, TCP servers, or WebSocket servers. 
3.    Data Transformation    :  
    *    Modifying data as it is read or written, such as compression or encryption. 
    *    Example: Compressing files using gzip or encrypting data streams. 
4.    Real-time Data Processing    :  
    *    Handling real-time data streams, such as video streaming or real-time analytics. 
    *    Example: Processing video streams for live broadcasting. 

 –––––––– 

 ![image](d2d_images/scene_break.png) 

 ![image](d2d_images/image115.png)

   S    TREAMS AND BUFFERS    are powerful tools in Node.js for handling I/O operations efficiently.   Streams allow you to process data in chunks, making them ideal for working with large datasets or files.   Buffers enable you to manipulate binary data directly, providing the foundation for working with streams.   By mastering these concepts, you can build robust applications that handle data efficiently and perform well under load.   Whether you are processing files, communicating over networks, or transforming data in real-time, streams and buffers are essential components of your Node.js toolkit. 

##  ​   3.4.   Handling File Uploads 

   H    ANDLING FILE UPLOADS    is a common requirement in web applications.   Node.js provides various tools and libraries to simplify this process.   One of the most popular libraries for handling file uploads in Node.js is    multer    .   This section will guide you through setting up file uploads using    multer    and provide practical examples to illustrate the process. 

####  Setting Up    multer  

    M    ULTER     is a middleware for handling    multipart/form-data    , which is primarily used for uploading files.   It is easy to set up and works seamlessly with Express, a popular web application framework for Node.js. 

 Installation 

 First, you need to install    multer    and    express    : 

 npm install express multer 

####  Basic File Upload Example 

   H    ERE’S A BASIC EXAMPLE    of setting up a file upload server using Express and    multer    . 

 Step 1: Import Required Modules 

 const express =    require    ('express'); 

 const multer =    require    ('multer'); 

 const path =    require    ('path'); 

 Step 2: Configure Storage for Uploaded Files 

  multer    allows you to configure storage options, such as the destination directory and file naming. 

 const storage =    multer    .    diskStorage    ({ 

  destination    : function (req, file,    cb    ) { 

  cb    (null, 'uploads/'); // Directory to save the uploaded files 

 }, 

  filename    : function (req, file,    cb    ) { 

  cb    (null, file.fieldname + '-' + Date.    now    () + path.    extname    (file.originalname)); // Filename format 

 } 

 }); 

 const upload =    multer    ({ storage: storage }); 

 Step 3: Set Up the Express Application 

 const app =    express    (); 

 const PORT = 3000; 

 app.    use    (express.    static    ('public')); // Serve static files from the "public" directory 

 Step 4: Create an Upload Endpoint 

 app.    post    ('/upload', upload.    single    ('file'), (req, res) => { 

 try { 

 res.    send    ('File uploaded successfully'); 

 } catch (error) { 

 res.    status    (400).    send    ('Error uploading file'); 

 } 

 }); 

 Step 5: Start the Server 

 app.    listen    (PORT, () => { 

 console.    log    (\`Server is running on port ${PORT}\`); 

 }); 

 –––––––– 

 ![image](d2d_images/scene_break.png) 

   S    TEP 6: CREATE AN HTML    Form for File Upload 

 Create an    index.html    file in the    public    directory with the following content: 

 <!DOCTYPE html> 

 <html lang="en"> 

 <head> 

 <meta charset="UTF-8"> 

 <meta name="viewport" content="width=device-width, initial-scale=1.0"> 

 <title>File Upload</title> 

 </head> 

 <body> 

 <h1>Upload a File</h1> 

 <form action="/upload" method="POST" enctype="multipart/form-data"> 

 <input type="file" name="file" required> 

 <button type="submit">Upload</button> 

 </form> 

 </body> 

 </html> 

 Complete Example 

 Here’s the complete code for the server: 

 const    express    =    require    ('express'); 

 const    multer    =    require    ('multer'); 

 const path =    require    ('path'); 

 const app =    express    (); 

 const PORT = 3000; 

 const storage =    multer    .    diskStorage    ({ 

  destination    : function (req, file,    cb    ) { 

  cb    (null, 'uploads/'); 

 }, 

  filename    : function (req, file,    cb    ) { 

  cb    (null, file.fieldname + '-' + Date.    now    () + path.    extname    (file.originalname)); 

 } 

 }); 

 const upload =    multer    ({ storage: storage }); 

 app.    use    (    express    .    static    ('public')); 

 app.    post    ('/upload', upload.    single    ('file'), (req, res) => { 

 try { 

 res.    send    ('File uploaded successfully'); 

 } catch (error) { 

 res.    status    (400).    send    ('Error uploading file'); 

 } 

 }); 

 app.    listen    (PORT, () => { 

 console.    log    (\`Server is running on port ${PORT}\`); 

 }); 

 ![image](d2d_images/image094.png)

 –––––––– 

 ![image](d2d_images/scene_break.png) 

   Y    OU WILL NOTICE THIS    directory appearing in the editor 

 ![image](d2d_images/image077.png)

  Maybe some css effects if you want (    Not necessary    )  

 Create a file named    styles.css    in the    public    directory: 

 /\* styles.css \*/ 

 body { 

 font-family: Arial, sans-serif; 

 background-color: #f4f4f4; 

 margin: 0; 

 padding: 0; 

 display: flex; 

 justify-content: center; 

 align-items: center; 

 height: 100vh; 

 } 

 h1 { 

 color: #333; 

 text-align: center; 

 } 

 form { 

 background: #fff; 

 padding: 20px; 

 border-radius: 8px; 

 box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1); 

 width: 300px; 

 text-align: center; 

 } 

 input\[type="file"\] { 

 margin: 10px 0; 

 padding: 10px; 

 border: 1px solid #ccc; 

 border-radius: 4px; 

 width: 100%; 

 box-sizing: border-box; 

 } 

 button { 

 background-color: #007BFF; 

 color: white; 

 padding: 10px; 

 border: none; 

 border-radius: 4px; 

 cursor: pointer; 

 width: 100%; 

 font-size: 16px; 

 } 

 button:hover { 

 background-color: #0056b3; 

 } 

 –––––––– 

 ![image](d2d_images/scene_break.png) 

###  Link the CSS File to Your HTML Page 

   U    PDATE YOUR     index.html    file to include a link to the    styles.css    file: 

 <!DOCTYPE html> 

 <html lang="en"> 

 <head> 

 <meta charset="UTF-8"> 

 <meta name="viewport" content="width=device-width, initial-scale=1.0"> 

 <title>File Upload</title> 

 <link rel="stylesheet" href="/styles.css"> 

 </head> 

 <body> 

 <h1>Upload a File</h1> 

 <form action="/upload" method="POST" enctype="multipart/form-data"> 

 <input type="file" name="file" required> 

 <button type="submit">Upload</button> 

 </form> 

 </body> 

 </html> 

 –––––––– 

 ![image](d2d_images/scene_break.png) 

 ![image](d2d_images/image170.png)

 ![image](d2d_images/image166.png)

 ![image](d2d_images/image031.png)

   N    OW YOU WILL NOTICE    that the images have been uploaded to the uploads directory 

 –––––––– 

 ![image](d2d_images/scene_break.png) 

###  Multiple File Uploads 

   S    TEP 1: IMPORT REQUIRED    Modules 

 const    express    =    require    ('express'); 

 const    multer    =    require    ('multer'); 

 const path =    require    ('path'); 

 const fs =    require    ('fs'); 

 Step 2: Configure Storage for Uploaded Files 

  multer    allows you to configure storage options, such as the destination directory and file naming. 

 const storage =    multer    .    diskStorage    ({ 

  destination    : function (req, file,    cb    ) { 

  cb    (null, 'uploads/'); // Directory to save the uploaded files 

 }, 

  filename    : function (req, file,    cb    ) { 

  cb    (null, file.fieldname + '-' + Date.    now    () + path.    extname    (file.originalname)); // Filename format 

 } 

 }); 

 const upload =    multer    ({ storage: storage }); 

 Step 3: Set Up the Express Application 

 const app =    express    (); 

 const PORT = 3000; 

 // Ensure the uploads directory exists 

 if (!fs.    existsSync    ('uploads')) { 

 fs.    mkdirSync    ('uploads'); 

 } 

 app.    use    (    express    .    static    ('public')); // Serve static files from the "public" directory 

 –––––––– 

 ![image](d2d_images/scene_break.png) 

   S    TEP 4: CREATE AN ENDPOINT    for Multiple File Uploads 

 app.    use    (    express    .    static    ('public')); // Serve static files from the "public" directory 

 app.    post    ('/upload-multiple', upload.    array    ('files', 10), (req, res) => { 

 try { 

 res.    send    ('Files uploaded successfully'); 

 } catch (error) { 

 res.    status    (400).    send    ('Error uploading files'); 

 } 

 }); 

 Step 5: Start the Server 

 app.    listen    (PORT, () => { 

 console.    log    (\`Server is running on port ${PORT}\`); 

 }); 

 Step 6: Create an HTML Form for Multiple File Uploads 

 Also create an    index.html    file in the    public    directory with the following content: 

 <!DOCTYPE html> 

 <html lang="en"> 

 <head> 

 <meta charset="UTF-8"> 

 <meta name="viewport" content="width=device-width, initial-scale=1.0"> 

 <title>File Upload</title> 

 <link rel="stylesheet" href="/styles.css"> 

 </head> 

 <body> 

 <h1>Upload Multiple Files</h1> 

 <form action="/upload-multiple" method="POST" enctype="multipart/form-data"> 

 <input type="file" name="files" multiple required> 

 <button type="submit">Upload</button> 

 </form> 

 </body> 

 </html> 

 –––––––– 

 ![image](d2d_images/scene_break.png) 

###  Complete Example 

   H    ERE’S THE COMPLETE    code for the server: 

 const    express    =    require    ('express'); 

 const    multer    =    require    ('multer'); 

 const path =    require    ('path'); 

 const fs =    require    ('fs'); 

 const app =    express    (); 

 const PORT = 3000; 

 // Ensure the uploads directory exists 

 if (!fs.    existsSync    ('uploads')) { 

 fs.    mkdirSync    ('uploads'); 

 } 

 const storage =    multer    .    diskStorage    ({ 

  destination    : function (req, file,    cb    ) { 

  cb    (null, 'uploads/'); 

 }, 

  filename    : function (req, file,    cb    ) { 

  cb    (null, file.fieldname + '-' + Date.    now    () + path.    extname    (file.originalname)); 

 } 

 }); 

 const upload =    multer    ({ storage: storage }); 

 app.    use    (    express    .    static    ('public')); 

 // Serve the HTML form for file uploads 

 app.    get    ('/', (req, res) => { 

 res.    sendFile    (path.    join    (\_\_dirname, 'public', 'index.html')); 

 }); 

 // Endpoint to handle multiple file uploads 

 app.    post    ('/upload-multiple', upload.    array    ('files', 10), (req, res) => { 

 try { 

 res.    send    ('Files uploaded successfully'); 

 } catch (error) { 

 res.    status    (400).    send    ('Error uploading files'); 

 } 

 }); 

 // Start the server 

 app.    listen    (PORT, () => { 

 console.    log    (\`Server is running on port ${PORT}\`); 

 }); 

 ![image](d2d_images/image151.png)

###  Explanation of the Code 

*     Express Setup     : We set up an Express application to handle HTTP requests.  
*     multer     Configuration     : We configure    multer    to store uploaded files in the    uploads    directory with a unique filename.  
*     Static Files     : We serve static files from the    public    directory, where we place our HTML form.  
*     Upload Endpoint     : We create an endpoint    /upload-multiple    that handles multiple file uploads.   The    upload.array('files', 10)    middleware processes the file uploads, allowing up to 10 files to be uploaded at a time.   The uploaded files are available in    req.files    .  

 –––––––– 

 ![image](d2d_images/scene_break.png) 

 ![image](d2d_images/image020.png)

   V    ALIDATING FILE UPLOADS  

 You can add file validation to ensure that only certain types of files are uploaded. 

 Example: File Validation 

 const    fileFilter    = (req, file, cb) => { 

 // Accept images only 

 if (!file.originalname.    match    (/\\.(jpg|jpeg|png|gif)$/)) { 

 return    cb    (new Error('Only image files are allowed!'), false); 

 } 

  cb    (null, true); 

 }; 

 const upload =    multer    ({ 

 storage: storage, 

  fileFilter    :    fileFilter  

 }); 

 ![image](d2d_images/image088.png)

 ![image](d2d_images/image146.png)

##  ​   3.5.   Practical Examples with File System Operations 

   F    ILE SYSTEM OPERATIONS    are essential for various tasks such as reading, writing, and managing files and directories.   This section provides practical examples to demonstrate how to perform these operations using Node.js. 

####  Example 1: Reading and Writing Files 

    O    BJECTIVE     : Read the contents of a file and write them to a new file. 

  Code    : 

 const fs =    require    ('fs'); 

 // Reading the contents of 'input.txt' and writing them to 'output.txt' 

 fs.    readFile    ('input.txt', 'utf8', (err, data) => { 

 if (err) { 

 console.    error    ('Error reading file:', err); 

 return; 

 } 

 fs.    writeFile    ('output.txt', data, (err) => { 

 if (err) { 

 console.    error    ('Error writing file:', err); 

 return; 

 } 

 console.    log    ('File has been written successfully'); 

 }); 

 }); 

 console.    log    ('Reading and writing files...'); 

  Explanation    : 

*    fs.readFile('input.txt', 'utf8', callback)    : Reads the contents of    input.txt    asynchronously.  
*    fs.writeFile('output.txt', data, callback)    : Writes the data read from    input.txt    to    output.txt    asynchronously.  
*    The program logs 'Reading and writing files...'   immediately, demonstrating non-blocking behavior. 

####  Example 2: Creating and Deleting Directories 

    O    BJECTIVE     : Create a new directory and then delete it. 

  Code    : 

 const fs =    require    ('fs'); 

 // Creating a new directory 'newDir' 

 fs.    mkdir    ('newDir', (err) => { 

 if (err) { 

 console.    error    ('Error creating directory:', err); 

 return; 

 } 

 console.    log    ('Directory created successfully'); 

 // Deleting the directory 'newDir' 

 fs.    rmdir    ('newDir', (err) => { 

 if (err) { 

 console.    error    ('Error deleting directory:', err); 

 return; 

 } 

 console.    log    ('Directory deleted successfully'); 

 }); 

 }); 

 console.    log    ('Creating and deleting directory...'); 

  Explanation    : 

*    fs.mkdir('newDir', callback)    : Creates a new directory named    newDir    .  
*    fs.rmdir('newDir', callback)    : Deletes the directory named    newDir    .  
*    The program logs 'Creating and deleting directory...'   immediately, demonstrating non-blocking behavior. 

####  Example 3: Copying Files 

    O    BJECTIVE     : Copy a file from one location to another. 

  Code    : 

 const fs =    require    ('fs'); 

 // Source and destination paths 

 const source = 'source.txt'; 

 const destination = 'destination.txt'; 

 // Copying the contents of 'source.txt' to 'destination.txt' 

 fs.    copyFile    (source, destination, (err) => { 

 if (err) { 

 console.    error    ('Error copying file:', err); 

 return; 

 } 

 console.    log    ('File copied successfully'); 

 }); 

 console.    log    ('Copying file...'); 

  Explanation    : 

*    fs.copyFile(source, destination, callback)    : Copies the contents of    source.txt    to    destination.txt    .  
*    The program logs 'Copying file...'   immediately, demonstrating non-blocking behavior. 

####  Example 4: Listing Files in a Directory 

    O    BJECTIVE     : List all files and directories within a specified directory. 

  Code    : 

 const fs =    require    ('fs'); 

 // Listing the contents of the current directory 

 fs.    readdir    ('.', (err, files) => { 

 if (err) { 

 console.    error    ('Error reading directory:', err); 

 return; 

 } 

 console.    log    ('Files in directory:'); 

 files.    forEach    (file => { 

 console.    log    (file); 

 }); 

 }); 

 console.    log    ('Listing files in directory...'); 

  Explanation    : 

*    fs.readdir('.', callback)    : Reads the contents of the current directory (denoted by    .    ).  
*    The program logs 'Listing files in directory...'   immediately, demonstrating non-blocking behavior. 

####  Example 5: Watching for File Changes 

    O    BJECTIVE     : Monitor a file for changes and log when it is modified. 

  Code    : 

 const fs =    require    ('fs'); 

 // Watching 'watchedFile.txt' for changes 

 fs.    watch    ('watchedFile.txt', (eventType, filename) => { 

 if (filename) { 

 console.    log    (\`${filename} file Changed\`); 

 } 

 }); 

 console.    log    ('Watching file for changes...'); 

  Explanation    : 

*    fs.watch('watchedFile.txt', callback)    : Watches    watchedFile.txt    for any changes (e.g., modifications, deletions).  
*    The program logs 'Watching file for changes...'   immediately, demonstrating non-blocking behavior. 

####  Example 6: Appending Data to a File 

    O    BJECTIVE     : Append data to an existing file. 

  Code    : 

 const fs =    require    ('fs'); 

 // Data to append 

 const data = '\\nAppended text.'; 

 // Appending data to 'fileToAppend.txt' 

 fs.    appendFile    ('fileToAppend.txt', data, (err) => { 

 if (err) { 

 console.    error    ('Error appending to file:', err); 

 return; 

 } 

 console.    log    ('Data appended successfully'); 

 }); 

 console.    log    ('Appending data to file...'); 

  Explanation    : 

*    fs.appendFile('fileToAppend.txt', data, callback)    : Appends    data    to    fileToAppend.txt    .  
*    The program logs 'Appending data to file...'   immediately, demonstrating non-blocking behavior. 

 These practical examples demonstrate how to perform various file system operations using Node.js, such as reading and writing files, creating and deleting directories, copying files, listing directory contents, watching for file changes, and appending data to files.   By understanding and utilizing these operations, you can efficiently manage files and directories within your Node.js applications, ensuring robust and flexible file handling capabilities. 

 
|  ![image](d2d_images/chapter_title_corner_decoration_left.png)  ||  ||  ![image](d2d_images/chapter_title_corner_decoration_right.png)  |
| --- | --- | --- |

 ![image](d2d_images/chapter_title_above.png) 

#  ​   ![image](d2d_images/image167.png)  4.   HTTP and Web Servers 

 ![image](d2d_images/chapter_title_below.png) 

##  ​   Understanding HTTP Status Codes 

   H    TTP status codes are    standardized responses issued by a server in response to a client's request made to the server.   These status codes are grouped into five classes: 

1.    1xx (Informational)    : The request was received, continuing process. 
2.    2xx (Successful)    : The request was successfully received, understood, and accepted. 
3.    3xx (Redirection)    : Further action needs to be taken in order to complete the request. 
4.    4xx (Client Error)    : The request contains bad syntax or cannot be fulfilled. 
5.    5xx (Server Error)    : The server failed to fulfill a valid request. 

####  Common HTTP Status Codes 

####  404 Not Found 

    D    EFINITION     : The 404 status code means that the server cannot find the requested resource.   This status code is commonly returned when the URL requested by the client does not correspond to any resource on the server.   It indicates a client-side error where the user is trying to access a page that does not exist. 

  Typical Causes    : 

*    Typing an incorrect URL. 
*    Clicking on a broken or dead link. 
*    The resource has been moved or deleted. 

  Handling    : On encountering a 404 error, the server should ideally respond with a custom 404 error page that informs the user that the requested resource could not be found and provide navigation options to help them find the desired content. 

####  500 Internal Server Error 

    D    EFINITION     : The 500 status code indicates that the server encountered an unexpected condition that prevented it from fulfilling the request.   This is a generic error message, given when no more specific message is suitable.   It signals a server-side error. 

  Typical Causes    : 

*    Server misconfiguration. 
*    Script errors in server-side code. 
*    Resource exhaustion (e.g., out of memory). 
*    Issues with third-party services or APIs the server is trying to access. 

  Handling    : When a 500 error occurs, the server should log the error details for further investigation and return a generic error message to the user to avoid exposing sensitive information.   Additionally, it is good practice to show a custom error page that informs the user of the issue and, if possible, provides a way to report the problem. 

###  Detailed Explanation of HTTP Status Codes 

####  1xx Informational 

*     100 Continue     : The server has received the request headers, and the client should proceed to send the request body.  
*     101 Switching Protocols     : The requester has asked the server to switch protocols, and the server is acknowledging that it will do so.  

####  2xx Successful 

*     200 OK     : The request has succeeded.   The meaning of the success depends on the HTTP method (GET, POST, PUT, DELETE).  
*     201 Created     : The request has been fulfilled, resulting in the creation of a new resource.  
*     204 No Content     : The server successfully processed the request, but is not returning any content.  

####  3xx Redirection 

*     301 Moved Permanently     : The URL of the requested resource has been changed permanently.   The new URL is given in the response.  
*     302 Found     : The URL of the requested resource has been changed temporarily.  
*     304 Not Modified     : Indicates that the resource has not been modified since the last request.  

####  4xx Client Error 

*     400 Bad Request     : The server cannot process the request due to a client error (e.g., malformed request syntax).  
*     401 Unauthorized     : The request requires user authentication.  
*     403 Forbidden     : The server understood the request, but refuses to authorize it.  
*     404 Not Found     : The server cannot find the requested resource.  
*     408 Request Timeout     : The server timed out waiting for the request.  

####  5xx Server Error 

*     500 Internal Server Error     : The server encountered an unexpected condition that prevented it from fulfilling the request.  
*     501 Not Implemented     : The server does not support the functionality required to fulfill the request.  
*     502 Bad Gateway     : The server, while acting as a gateway or proxy, received an invalid response from the upstream server.  
*     503 Service Unavailable     : The server is not ready to handle the request, often due to temporary overload or maintenance.  
*     504 Gateway Timeout     : The server, while acting as a gateway or proxy, did not receive a timely response from the upstream server.  

 
|  Status Code  ||  Meaning  ||  Description  |
| --- | --- | --- |
|  1xx Informational  ||  ||  |
|  100  ||  Continue  ||  The server has received the request headers, and the client should proceed to send the request body.  |
|  101  ||  Switching Protocols  ||  The requester has asked the server to switch protocols, and the server is acknowledging that it will do so.  |
|  2xx Successful  ||  ||  |
|  200  ||  OK  ||  The request has succeeded.  |
|  201  ||  Created  ||  The request has been fulfilled, resulting in the creation of a new resource.  |
|  204  ||  No Content  ||  The server successfully processed the request, and is not returning any content.  |
|  3xx Redirection  ||  ||  |
|  301  ||  Moved Permanently  ||  The URL of the requested resource has been changed permanently.  |
|  302  ||  Found  ||  The URL of the requested resource has been changed temporarily.  |
|  304  ||  Not Modified  ||  Indicates that the resource has not been modified since the last request.  |
|  4xx Client Error  ||  ||  |
|  400  ||  Bad Request  ||  The server cannot process the request due to a client error (e.g., malformed request syntax).  |
|  401  ||  Unauthorized  ||  The request requires user authentication.  |
|  403  ||  Forbidden  ||  The server understood the request, but refuses to authorize it.  |
|  404  ||  Not Found  ||  The server cannot find the requested resource.  |
|  408  ||  Request Timeout  ||  The server timed out waiting for the request.  |
|  5xx Server Error  ||  ||  |
|  500  ||  Internal Server Error  ||  The server encountered an unexpected condition that prevented it from fulfilling the request.  |
|  501  ||  Not Implemented  ||  The server does not support the functionality required to fulfill the request.  |
|  502  ||  Bad Gateway  ||  The server, while acting as a gateway or proxy, received an invalid response from the upstream server.  |
|  503  ||  Service Unavailable  ||  The server is not ready to handle the request, often due to temporary overload or maintenance.  |
|  504  ||  Gateway Timeout  ||  The server, while acting as a gateway or proxy, did not receive a timely response from the upstream server.  |

   T    ABLE.2 OF COMMON HTTP    Status Codes 

##  ​   Understanding HTTP Methods 

   H    TTP METHODS, ALSO    known as verbs, are a fundamental part of the HTTP protocol used for web communication.   These methods define the action to be performed on the resources identified by a URL.   The most commonly used HTTP methods are GET, POST, PUT, and DELETE, but there are others like PATCH, OPTIONS, and HEAD, each serving a specific purpose. 

###  Detailed Explanation of HTTP Methods 

####  GET Method 

    D    EFINITION     : The GET method is used to request data from a specified resource.   Requests using GET should only retrieve data and have no other effect on the data. 

  Characteristics    : 

*     Idempotent     : Multiple identical GET requests should have the same effect as a single request.  
*     Safe     : Does not alter the state of the server.  
*     Cachable     : Responses to GET requests can be cached for better performance.  

  Usage    : 

*    Fetching web pages. 
*    Retrieving data from a server. 

  Example    : 

 GET /users HTTP/1.1 

 Host: example.com 

 In this example, a GET request is made to the    /users    endpoint to retrieve a list of users. 

####  POST Method 

    D    EFINITION     : The POST method is used to send data to the server to create or update a resource.   The data is included in the body of the request. 

  Characteristics    : 

*     Non-idempotent     : Multiple identical POST requests can have different effects.  
*     Not Safe     : Alters the state of the server.  
*     Not Cachable     : Responses to POST requests are typically not cached.  

  Usage    : 

*    Submitting form data. 
*    Uploading files. 
*    Creating a new resource on the server. 

  Example    : 

 POST /users HTTP/1.1 

 Host: example.com 

 Content-Type: application/json 

 { 

 "name": "John Doe", 

 "email": "john.doe@example.com" 

 } 

  Explanation    : In this example, a POST request is made to the    /users    endpoint with JSON data in the body to create a new user. 

####  PUT Method 

    D    EFINITION     : The PUT method is used to update a current resource with new data.   If the resource does not exist, PUT can create it. 

  Characteristics    : 

*     Idempotent     : Multiple identical PUT requests should have the same effect as a single request.  
*     Not Safe     : Alters the state of the server.  
*     Not Cachable     : Responses to PUT requests are typically not cached.  

  Usage    : 

*    Updating existing resources. 
*    Creating resources at a specified URL. 

  Example    : 

 PUT /users/1 HTTP/1.1 

 Host: example.com 

 Content-Type: application/json 

 { 

 "name": "John Doe", 

 "email": "john.doe@example.com" 

 } 

  Explanation    : In this example, a PUT request is made to the    /users/1    endpoint to update the user with ID 1. 

####  DELETE Method 

    D    EFINITION     : The DELETE method is used to delete a specified resource. 

  Characteristics    : 

*     Idempotent     : Multiple identical DELETE requests should have the same effect as a single request.  
*     Not Safe     : Alters the state of the server.  
*     Not Cachable     : Responses to DELETE requests are typically not cached.  

  Usage    : 

*    Removing resources from the server. 

  Example    : 

 DELETE /users/1 HTTP/1.1 

 Host: example.com 

  Explanation    : In this example, a DELETE request is made to the    /users/1    endpoint to delete the user with ID 1. 

####  PATCH Method 

    D    EFINITION     : The PATCH method is used to apply partial modifications to a resource. 

  Characteristics    : 

*     Not Idempotent     : Multiple identical PATCH requests can have different effects.  
*     Not Safe     : Alters the state of the server.  
*     Not Cachable     : Responses to PATCH requests are typically not cached.  

  Usage    : 

*    Partially updating resources. 

  Example    : 

 PATCH /users/1 HTTP/1.1 

 Host: example.com 

 Content-Type: application/json 

 { 

 "email": "john.newemail@example.com" 

 } 

 In this example, a PATCH request is made to the    /users/1    endpoint to update only the email of the user with ID 1. 

####  OPTIONS Method 

    D    EFINITION     : The OPTIONS method is used to describe the communication options for the target resource. 

  Characteristics    : 

*     Idempotent     : Multiple identical OPTIONS requests should have the same effect as a single request.  
*     Safe     : Does not alter the state of the server.  
*     Not Cachable     : Responses to OPTIONS requests are typically not cached.  

  Usage    : 

*    Checking what HTTP methods are supported by a server. 

  Example    : 

 OPTIONS /users HTTP/1.1 

 Host: example.com 

 In this example, an OPTIONS request is made to the    /users    endpoint to determine the methods supported by the server for this resource. 

####  HEAD Method 

    D    EFINITION     : The HEAD method is identical to GET except that the server MUST NOT return a message body in the response.   It is useful for retrieving meta-information written in response headers, without having to transport the entire content. 

  Characteristics    : 

*     Idempotent     : Multiple identical HEAD requests should have the same effect as a single request.  
*     Safe     : Does not alter the state of the server.  
*     Cachable     : Responses to HEAD requests can be cached.  

  Usage    : 

*    Checking if a resource exists. 
*    Fetching meta-information about a resource. 

 HEAD /users HTTP/1.1 

 Host: example.com 

 In this example, a HEAD request is made to the    /users    endpoint to retrieve headers without the response body. 

 
|  HTTP Method  ||  Idempotent  ||  Safe  ||  Cacheable  ||  Description  |
| --- | --- | --- | --- | --- |
|  GET  ||  Yes  ||  Yes  ||  Yes  ||  Retrieve data from a specified resource.  |
|  POST  ||  No  ||  No  ||  No  ||  Send data to the server to create/update a resource.  |
|  PUT  ||  Yes  ||  No  ||  No  ||  Update a resource or create it if it does not exist.  |
|  DELETE  ||  Yes  ||  No  ||  No  ||  Delete a specified resource.  |
|  PATCH  ||  No  ||  No  ||  No  ||  Apply partial modifications to a resource.  |
|  OPTIONS  ||  Yes  ||  Yes  ||  No  ||  Describe the communication options for the resource.  |
|  HEAD  ||  Yes  ||  Yes  ||  Yes  ||  Retrieve headers for a resource without the body.  |

 Table.3 of HTTP Methods 

 ![image](d2d_images/image198.png)

##  ​   4.1.   Creating a Simple Web Server 

   C    REATING A SIMPLE WEB    server in Node.js is an essential step in understanding how server-side applications work.   Node.js's built-in    http    module provides all the necessary functionality to set up a basic web server.   This section will guide you through the process of creating a simple web server, explaining each part in detail. 

 Step 1: Import the HTTP Module 

 First, you need to import the    http    module.   This module provides the    createServer    method that will be used to create the web server. 

 const http =    require    ('http'); 

 Step 2: Create the Server 

 Use the    createServer    method to create the server.   This method takes a callback function that will be executed every time the server receives a request.   The callback function has two parameters:    req    (the request object) and    res    (the response object). 

 const server = http.    createServer    ((req, res) => { 

 res.statusCode = 200; // Set the response status code to 200 (OK) 

 res.    setHeader    ('Content-Type', 'text/plain'); // Set the response header 

 res.    end    ('Hello, World!\\n'); // Send the response body 

 }); 

 Step 3: Listen on a Port 

 Tell the server to listen on a specific port.   Commonly used ports for development are 3000, 8080, and 5000. 

 const PORT = 3000; 

 server.    listen    (PORT, () => { 

 console.    log    (\`Server running at http://localhost:${PORT}/\`); 

 }); 

 Complete Example 

 const http =    require    ('http'); 

 const server = http.    createServer    ((req, res) => { 

 res.statusCode = 200; 

 res.    setHeader    ('Content-Type', 'text/plain'); 

 res.    end    ('Hello, World!\\n'); 

 }); 

 const PORT = 3000; 

 server.    listen    (PORT, () => { 

 console.    log    (\`Server running at http://localhost:${PORT}/\`); 

 }); 

 –––––––– 

 ![image](d2d_images/scene_break.png) 

           Importing the HTTP Module    : The    http    module is part of Node.js's core modules, which means you don't need to install anything extra to use it. 

     Creating the Server    : The    http.createServer    method creates a new server instance.   The callback function handles incoming requests and sends responses. 

     Setting the Status Code and Headers    :    res.statusCode    sets the HTTP status code of the response.    res.setHeader    sets the HTTP headers.   In this case, we're setting the    Content-Type    header to    text/plain    . 

     Sending the Response    :    res.end    ends the response process.   The argument passed to    res.end    is sent as the response body. 

     Listening on a Port    :    server.listen    makes the server start listening for incoming requests on the specified port.   The callback function logs a message when the server starts successfully. 

 Open your web browser and navigate to    http://localhost:3000    .   You should see "Hello, World!"   displayed on the page. 

 –––––––– 

 ![image](d2d_images/scene_break.png) 

 ![image](d2d_images/image070.png)

####  Expanding the Basic Server 

   O    NCE YOU HAVE A BASIC    server running, you can expand its functionality to handle more complex tasks. 

 Handling Different URLs 

 You can modify the server to respond differently based on the requested URL. 

 const http =    require    ('http'); 

 const server = http.    createServer    ((req, res) => { 

 res.statusCode = 200; 

 res.    setHeader    ('Content-Type', 'text/plain'); 

 if (req.url === '/') { 

 res.    end    ('Hello, World!\\n'); 

 } else if (req.url === '/about') { 

 res.    end    ('About Us\\n'); 

 } else { 

 res.statusCode = 404; 

 res.    end    ('Not Found\\n'); 

 } 

 }); 

 const PORT = 3000; 

 server.    listen    (PORT, () => { 

 console.    log    (\`Server running at http://localhost:${PORT}/\`); 

 }); 

 Serving HTML Content 

 You can serve HTML content instead of plain text by setting the    Content-Type    to    text/html    . 

 const http =    require    ('http'); 

 const server = http.    createServer    ((req, res) => { 

 res.statusCode = 200; 

 res.    setHeader    ('Content-Type', 'text/html'); 

 res.    end    ('<h1>Hello, World!</h1>\\n'); 

 }); 

 const PORT = 3000; 

 server.    listen    (PORT, () => { 

 console.    log    (\`Server running at http://localhost:${PORT}/\`); 

 }); 

 Creating a simple web server in Node.js is a foundational skill for web development 

 ![image](d2d_images/image178.png)

##  ​   4.-Introduction to Postman 

   P    OSTMAN IS A POWERFUL    and user-friendly tool designed to simplify the process of developing, testing, and documenting APIs.   It allows developers to send HTTP requests, inspect responses, and automate API testing.   With Postman, you can interact with your web server without writing additional code, making it an essential tool for web development and API testing. 

 ![image](d2d_images/image093.png)

####  What is Postman? 

   P    OSTMAN IS A COLLABORATION    platform for API development.   It provides a comprehensive set of tools to help you design, debug, test, and document APIs.   It supports various HTTP methods (GET, POST, PUT, DELETE, etc.), and allows you to add headers, parameters, and request bodies with ease.   Postman’s intuitive interface and robust feature set make it a popular choice among developers for API testing and development. 

 ![image](d2d_images/image157.png)

####  Key Features of Postman 

1.    HTTP Requests    : Send HTTP requests with various methods (GET, POST, PUT, DELETE, etc.). 
2.    Headers and Parameters    : Add custom headers and query parameters to your requests. 
3.    Request Body    : Send different types of request bodies (raw, JSON, form-data, etc.). 
4.    Response Inspection    : View detailed responses including status codes, headers, and body. 
5.    Environment Variables    : Use variables to manage different environments (development, staging, production). 
6.    Automation    : Write tests and automate API workflows with Postman’s scripting capabilities. 
7.    Collections    : Group related requests into collections for better organization and reusability. 

###  How to Use Postman 

####  Installing Postman 

1.    Download    : Visit the Postman download page and download the appropriate version for your operating system. 
2.    Install    : Follow the installation instructions for your platform to install Postman. 

####  Creating a New Request 

1.    Open Postman    : Launch the Postman application. 
2.    Create a New Request    : 

   C    LICK ON THE     +    button or    New    button in the top left corner to create a new request. 

 Select    HTTP Request    . 

 ![image](d2d_images/image219.png)

1.    Set the Request Method    : 

 Use the dropdown menu to select the HTTP method (GET, POST, PUT, DELETE, etc.). 

 ![image](d2d_images/image171.png)

1.    Enter the URL    : 

 Enter the URL of the API endpoint you want to test (e.g.,    http://localhost:3000    ). 

####  Adding Headers and Parameters 

1.    Headers    :  
    *     Click on the    Headers    tab below the URL bar.  
    *     Add key-value pairs for the headers you want to include (e.g.,    Content-Type: application/json    ).  
2.    Query Parameters    :  
    *     Click on the    Params    tab below the URL bar.  
    *     Add key-value pairs for the query parameters you want to include (e.g.,    name=John&age=30    ).  

####  Adding a Request Body 

1.    Select the Body Tab    :  
    *    Click on the Body tab below the URL bar. 
2.    Choose the Body Type    :  
    *    Select the appropriate body type (raw, form-data, x-www-form-urlencoded, etc.). 
3.    Enter the Request Body    :  
    *     For    raw    body type, select the data format (e.g., JSON) and enter the request body.  
    *    Example JSON body: 

 { 

 "name": "John", 

 "age": 30 

 } 

####  Sending the Request 

1.    Click Send    :  
    *    Click the Send button to send the request to the server. 
2.    Inspect the Response    :  
    *    The response from the server will be displayed in the lower section of Postman. 
    *    You can view the response status, headers, and body. 

####  Using Postman Collections 

1.    Create a Collection    :  
    *     Click on the    Collections    tab on the left sidebar.  
    *     Click the    New Collection    button and give your collection a name.  
2.    Add Requests to Collection    :  
    *    Save individual requests to the collection for better organization. 
    *     Click    Save    on the request and select the collection to save it to.  

####  Automating Tests 

1.    Write Tests    :  
    *     Click on the    Tests    tab below the URL bar.  
    *    Write JavaScript code to create tests that validate the response. 
    *    Example test: 

 ![image](d2d_images/image214.png)

   P    M.TEST("STATUS CODE    is 200", function () { 

 pm.response.to.have.status(200); 

 }); 

 For a thorough and engaging tutorial on using Postman, I highly recommend watching the video clip by Hitesh Choudhary on YouTube, where he explains Postman in an excellent way. 

 ![image](d2d_images/image089.png)

 What is Postman and why everyone use it ?   ​   ^( \[10\] ) 

##  ​   4.2.   Handling Requests and Responses 

###  Handling Different HTTP Methods 

   H    TTP METHODS DEFINE    the type of operation that is being requested by the client.   Each method has a specific purpose and usage.   Understanding how to handle different HTTP methods in Node.js is crucial for building robust and RESTful APIs.   Here we will explain how to handle GET, POST, PUT, DELETE, and other HTTP methods (PATCH, OPTIONS, HEAD) in depth, with examples using Postman for testing. 

 ![image](d2d_images/image067.png)

 ![image](d2d_images/image153.png)

###  Handling GET Requests 

    G    ET     requests are used to retrieve data from the server.   They are idempotent, meaning multiple identical GET requests should have the same effect as a single request.   GET requests do not change the state of the server. 

  Example    : 

 const http =    require    ('http'); 

 const url =    require    ('url'); 

 const server = http.    createServer    ((req, res) => { 

 if (req.method === 'GET') { 

 const parsedUrl = url.    parse    (req.url, true); 

 const query = parsedUrl.query; 

 res.statusCode = 200; 

 res.    setHeader    ('Content-Type', 'application/json'); 

 res.    end    (JSON.    stringify    (query)); 

 } else { 

 res.statusCode = 405; 

 res.    end    ('Method Not Allowed'); 

 } 

 }); 

 const PORT = 3000; 

 server.    listen    (PORT, () => { 

 console.    log    (\`Server running at http://localhost:${PORT}/\`); 

 }); 

 –––––––– 

 ![image](d2d_images/scene_break.png) 

    T    ESTING     : 

1.   Open Postman and create a new GET request. 
2.   Set the URL to  [ http://localhost:3000?name=John&age=30 ](http://localhost:3000?name=John&age=30)  . 

 ![image](d2d_images/image134.png)

1.   Click    Send    . 
2.   You will see the response with the query parameters: 

 ![image](d2d_images/image109.png)

###  Handling POST Requests 

    P    OST     requests are used to send data to the server to create or update a resource.   The data is included in the request body. 

  Example    : 

 const http =    require    ('http'); 

 const server = http.    createServer    ((req, res) => { 

 if (req.method === 'POST') { 

 let body = ''; 

 req.    on    ('data', chunk => { 

 body += chunk.    toString    (); 

 }); 

 req.    on    ('end', () => { 

 res.statusCode = 200; 

 res.    setHeader    ('Content-Type', 'application/json'); 

 res.    end    (\`Received data: ${body}\`); 

 }); 

 } else { 

 res.statusCode = 405; 

 res.    end    ('Method Not Allowed'); 

 } 

 }); 

 const PORT = 3000; 

 server.    listen    (PORT, () => { 

 console.    log    (\`Server running at http://localhost:${PORT}/\`); 

 }); 

  Testing    : 

1.   Open Postman and create a new    POST    request. 

 ![image](d2d_images/image083.png)

1.   Set the URL to    http://localhost:3000    . 
2.   Go to the    Body    tab, select    raw    and    JSON    , and enter: 

 ![image](d2d_images/image154.png)

 ![image](d2d_images/image179.png)

   Click    Send    . 

   You should see the response with the received data: 

 ![image](d2d_images/image081.png)

###  Handling PUT Requests 

    P    UT     requests are used to update a resource on the server.   They can also be used to create a resource if it does not exist.   PUT requests typically include data in the request body. 

  Example Code    : 

 const http =    require    ('http'); 

 const server = http.    createServer    ((req, res) => { 

 if (req.method === 'PUT') { 

 let body = ''; 

 req.    on    ('data', chunk => { 

 body += chunk.    toString    (); 

 }); 

 req.    on    ('end', () => { 

 res.statusCode = 200; 

 res.    setHeader    ('Content-Type', 'application/json'); 

 res.    end    (\`Updated data: ${body}\`); 

 }); 

 } else { 

 res.statusCode = 405; 

 res.    end    ('Method Not Allowed'); 

 } 

 }); 

 const PORT = 3000; 

 server.    listen    (PORT, () => { 

 console.    log    (\`Server running at http://localhost:${PORT}/\`); 

 }); 

  Testing    : 

1.   Open Postman and create a new    PUT    request. 
2.   Set the URL to    http://localhost:3000    . 
3.   Go to the    Body    tab, select    raw    and    JSON    , and enter: 

 { 

 "name": "John", 

 "age": 31 

 } 

   Click    Send    . 

   You will see the response with the updated data: 

 ![image](d2d_images/image208.png)

###  Handling DELETE Requests 

    D    ELETE     requests are used to delete a resource on the server. 

  Example    : 

 const http =    require    ('http'); 

 const server = http.    createServer    ((req, res) => { 

 if (req.method === 'DELETE') { 

 const urlParts = req.url.    split    ('/'); 

 const id = urlParts\[urlParts.length - 1\]; 

 res.statusCode = 200; 

 res.    setHeader    ('Content-Type', 'text/plain'); 

 res.    end    (\`Resource with ID ${id} deleted\`); 

 } else { 

 res.statusCode = 405; 

 res.    end    ('Method Not Allowed'); 

 } 

 }); 

 const PORT = 3000; 

 server.    listen    (PORT, () => { 

 console.    log    (\`Server running at http://localhost:${PORT}/\`); 

 }); 

  Testing    : 

1.   Open Postman and create a new    DELETE    request. 
2.   Set the URL to  [ http://localhost:3000/resource/123 ](http://localhost:3000/resource/123)  . 

 ![image](d2d_images/image043.png)

1.   Click    Send    . 
2.   You should see the response indicating the resource was deleted: 

 Resource with ID 123 deleted 

###  Handling Other HTTP Methods (PATCH, OPTIONS, HEAD) 

    P    ATCH     : Used to apply partial modifications to a resource. 

  Example    : 

 const http =    require    ('http'); 

 const server = http.    createServer    ((req, res) => { 

 if (req.method === 'PATCH') { 

 let body = ''; 

 req.    on    ('data', chunk => { 

 body += chunk.    toString    (); 

 }); 

 req.    on    ('end', () => { 

 res.statusCode = 200; 

 res.    setHeader    ('Content-Type', 'application/json'); 

 res.    end    (\`Patched data: ${body}\`); 

 }); 

 } else { 

 res.statusCode = 405; 

 res.    end    ('Method Not Allowed'); 

 } 

 }); 

 const PORT = 3000; 

 server.    listen    (PORT, () => { 

 console.    log    (\`Server running at http://localhost:${PORT}/\`); 

 }); 

  Testing    : 

1.   Open Postman and create a new PATCH request. 
2.   Set the URL to    http://localhost:3000    . 
3.   Go to the    Body    tab, select    raw    and    JSON    , and enter: 

 { 

 "name": "John", 

 "age": 32 

 } 

   Click    Send    . 

   You will see the response with the patched data: 

 { 

 "Patched data: {\\"name\\":\\"John\\",\\"age\\":32}" 

 } 

 ![image](d2d_images/image127.png)

  OPTIONS    : Used to describe the communication options for the target resource. 

  Example    : 

 const http =    require    ('http'); 

 const server = http.    createServer    ((req, res) => { 

 if (req.method === 'OPTIONS') { 

 res.statusCode = 200; 

 res.    setHeader    ('Allow', 'GET, POST, PUT, DELETE, PATCH, OPTIONS'); 

 res.    end    (); 

 } else { 

 res.statusCode = 405; 

 res.    end    ('Method Not Allowed'); 

 } 

 }); 

 const PORT = 3000; 

 server.    listen    (PORT, () => { 

 console.    log    (\`Server running at http://localhost:${PORT}/\`); 

 }); 

  Testing    : 

1.   Open Postman and create a new OPTIONS request. 
2.   Set the URL to    http://localhost:3000    . 
3.   Click    Send    . 
4.   You should see the response with the allowed methods: 

 Allow: GET, POST, PUT, DELETE, PATCH, OPTIONS 

 ![image](d2d_images/image212.png)

 ![image](d2d_images/image140.png)

###  Parsing and Managing Data 

   P    ARSING AND MANAGING    data are essential tasks when handling HTTP requests in Node.js.   Different types of data can be sent in HTTP requests, such as JSON data, URL-encoded data, and multipart form data (commonly used for file uploads).   This section will explain how to parse and manage these different types of data. 

####  Parsing JSON Data 

   J    SON (JAVASCRIPT OBJECT    Notation) is a lightweight data-interchange format that is easy to read and write for humans and machines.   JSON is commonly used for sending structured data in HTTP requests. 

  Example with Core HTTP Module    : 

 const http =    require    ('http'); 

 const server = http.    createServer    ((req, res) => { 

 if (req.method === 'POST' && req.headers\['content-type'\] === 'application/json') { 

 let body = ''; 

 req.    on    ('data', chunk => { 

 body += chunk.    toString    (); 

 }); 

 req.    on    ('end', () => { 

 try { 

 const parsedData = JSON.    parse    (body); 

 res.statusCode = 200; 

 res.    setHeader    ('Content-Type', 'application/json'); 

 res.    end    (JSON.    stringify    ({ received: parsedData })); 

 } catch (err) { 

 res.statusCode = 400; 

 res.    end    ('Invalid JSON'); 

 } 

 }); 

 } else { 

 res.statusCode = 405; 

 res.    end    ('Method Not Allowed'); 

 } 

 }); 

 const PORT = 3000; 

 server.    listen    (PORT, () => { 

 console.    log    (\`Server running at http://localhost:${PORT}/\`); 

 }); 

  Explanation    : 

*     This code snippet sets up an HTTP server that listens for POST requests with a    Content-Type    of    application/json    .  
*    The server reads the request body, parses it as JSON, and responds with the parsed data. 
*     If the JSON is invalid, it returns a    400 Bad Request    status.  

  Testing with Postman    : 

1.   Create a new POST request. 
2.   Set the URL to    http://localhost:3000    . 
3.   Set the    Content-Type    header to    application/json    . 
4.   In the Body tab, select    raw    and    JSON    , then enter: 

 { 

 "name": "John", 

 "age": 30 

 } 

 Click    Send    . 

####  Parsing URL-encoded Data 

   U    RL-ENCODED DATA IS    often used in form submissions.   It encodes key-value pairs in a URL format, where each key-value pair is separated by    &    and keys/values are separated by    =    . 

 ![image](d2d_images/image203.png)

  Example with Core HTTP Module    : 

 const http =    require    ('http'); 

 const querystring =    require    ('querystring'); 

 const server = http.    createServer    ((req, res) => { 

 if (req.method === 'POST' && req.headers\['content-type'\] === 'application/x-www-form-urlencoded') { 

 let body = ''; 

 req.    on    ('data', chunk => { 

 body += chunk.    toString    (); 

 }); 

 req.    on    ('end', () => { 

 const parsedData = querystring.    parse    (body); 

 res.statusCode = 200; 

 res.    setHeader    ('Content-Type', 'application/json'); 

 res.    end    (JSON.    stringify    ({ received: parsedData })); 

 }); 

 } else { 

 res.statusCode = 405; 

 res.    end    ('Method Not Allowed'); 

 } 

 }); 

 const PORT = 3000; 

 server.    listen    (PORT, () => { 

 console.    log    (\`Server running at http://localhost:${PORT}/\`); 

 }); 

 –––––––– 

 ![image](d2d_images/scene_break.png) 

    E    XPLANATION     : 

*     This code snippet sets up an HTTP server that listens for POST requests with a    Content-Type    of    application/x-www-form-urlencoded    .  
*     The server reads the request body, parses it using    querystring.parse    , and responds with the parsed data.  

  Testing with Postman    : 

1.   Create a new POST request. 
2.   Set the URL to    http://localhost:3000    . 
3.   Set the    Content-Type    header to    application/x-www-form-urlencoded    . 
4.   In the Body tab, select    x-www-form-urlencoded    , then add key-value pairs like    name=John    and    age=30    . 
5.   Click    Send    . 

 ![image](d2d_images/image015.png)

 ![image](d2d_images/image201.png)

####  Handling Multipart Form Data (File Uploads) 

   M    ULTIPART FORM DATA    is used for file uploads and can contain both text and binary data.   To handle multipart form data, you typically use a middleware library like    multer    with Express. 

  Example with Express and Multer    : 

  Install Express and Multer    : 

 npm install express multer 

  Set Up the Server    : 

 const    express    =    require    ('express'); 

 const    multer    =    require    ('multer'); 

 const path =    require    ('path'); 

 const app =    express    (); 

 const upload =    multer    ({ dest: 'uploads/' }); 

 app.    post    ('/upload', upload.    single    ('file'), (req, res) => { 

 res.statusCode = 200; 

 res.    setHeader    ('Content-Type', 'application/json'); 

 res.    end    (JSON.    stringify    ({ file: req.file })); 

 }); 

 const PORT = 3000; 

 app.    listen    (PORT, () => { 

 console.    log    (\`Server running at http://localhost:${PORT}/\`); 

 }); 

  Explanation    : 

*    This code snippet sets up an Express server with Multer middleware to handle file uploads. 
*     The    upload.single('file')    middleware processes single file uploads with the form field name    file    .  
*    The server responds with information about the uploaded file. 

  Testing with Postman    : 

1.   Create a new POST request. 
2.   Set the URL to    http://localhost:3000/upload    . 
3.   In the Body tab, select    form-data    . 

 ![image](d2d_images/image000.png)

1.   Add a key    file    and set the type to    File    . 

 ![image](d2d_images/image030.png)

1.   Choose a file to upload. 

 ![image](d2d_images/image034.png)

1.   Click    Send    . 

 ![image](d2d_images/image061.png)

 ![image](d2d_images/image185.png)

 ![image](d2d_images/image017.png)

 ![image](d2d_images/image023.png)

 ![image](d2d_images/image096.png)

###  Error Handling 

   P    ROPER ERROR HANDLING    is essential for creating a robust and user-friendly application.   In web development, it's important to manage different types of errors gracefully and provide meaningful feedback to users.   This section covers handling common HTTP errors like 404 Not Found and 500 Internal Server Errors, creating custom error pages, and logging errors for debugging purposes. 

####  Handling 404 Not Found 

   A    404 ERROR OCCURS    when the requested resource is not found on the server.   It's important to catch this error and provide a user-friendly message instead of a generic browser error page. 

  Example with Express    : 

 const    express    =    require    ('express'); 

 const app =    express    (); 

 // Define your routes here 

 // Catch 404 and forward to error handler 

 app.    use    ((req, res,    next    ) => { 

 res.    status    (404).    send    ('404 Not Found'); 

 }); 

 const PORT = 3000; 

 app.    listen    (PORT, () => { 

 console.    log    (\`Server running at http://localhost:${PORT}/\`); 

 }); 

  Explanation    : 

*    After defining your routes, use a middleware function to catch all unmatched routes. 
*    Set the status code to 404 and send a user-friendly message. 

 ![image](d2d_images/image119.png)

 ![image](d2d_images/image169.png)

####  Handling 500 Internal Server Errors 

   A    500 ERROR INDICATES    that something went wrong on the server side.   It's important to log these errors and provide a generic message to the user to avoid exposing sensitive information. 

  Example with Express    : 

 const    express    =    require    ('express'); 

 const app =    express    (); 

 // Simulate an error 

 app.    get    ('/error', (req, res,    next    ) => { 

 const err = new Error('Something went wrong!'); 

 err.status = 500; 

  next    (err); 

 }); 

 // Error handling middleware 

 app.    use    ((err, req, res, next) => { 

 console.    error    (err.stack); 

 res.    status    (err.status || 500).    send    ('500 Internal Server Error'); 

 }); 

 const PORT = 3000; 

 app.    listen    (PORT, () => { 

 console.    log    (\`Server running at http://localhost:${PORT}/\`); 

 }); 

 –––––––– 

 ![image](d2d_images/scene_break.png) 

 ![image](d2d_images/image105.png)

 ![image](d2d_images/image114.png)

    E    XPLANATION     : 

*    Define an endpoint that simulates an error. 
*    Use an error handling middleware function to catch all errors, log the stack trace, and send a generic message. 

 ![image](d2d_images/image211.png)

####  Custom Error Pages 

   C    USTOM ERROR PAGES    improve user experience by providing more context and a better-looking page when errors occur. 

  Example with Express    : 

1.    Create Custom Error Pages (e.g.,     public/404.html     and     public/500.html     )    : 

 404.html 

 <!—public/404.html—> 

 <!DOCTYPE html> 

 <html lang="en"> 

 <head> 

 <meta charset="UTF-8"> 

 <title>404 Not Found</title> 

 </head> 

 <body> 

 <h1>404 Not Found</h1> 

 <p>The page you are looking for might have been removed, had its name changed, or is temporarily unavailable.</p> 

 </body> 

 </html> 

 –––––––– 

 ![image](d2d_images/scene_break.png) 

   500    .HTML  

 <!—public/500.html—> 

 <!DOCTYPE html> 

 <html lang="en"> 

 <head> 

 <meta charset="UTF-8"> 

 <title>500 Internal Server Error</title> 

 </head> 

 <body> 

 <h1>500 Internal Server Error</h1> 

 <p>Something went wrong on our end.   Please try again later.</p> 

 </body> 

 </html> 

 –––––––– 

 ![image](d2d_images/scene_break.png) 

    S    ERVE CUSTOM ERROR    Pages in Express    : 

 const    express    =    require    ('express'); 

 const path =    require    ('path'); 

 const app =    express    (); 

 // Serve static files from the "public" directory 

 app.    use    (    express    .    static    (path.    join    (\_\_dirname, 'public'))); 

 // Define your routes here 

 // Catch 404 and forward to error handler 

 app.    use    ((req, res,    next    ) => { 

 res.    status    (404).    sendFile    (path.    join    (\_\_dirname, 'public', '404.html')); 

 }); 

 // Error handling middleware 

 app.    use    ((err, req, res, next) => { 

 console.    error    (err.stack); 

 res.    status    (err.status || 500).    sendFile    (path.    join    (\_\_dirname, 'public', '500.html')); 

 }); 

 const PORT = 3000; 

 app.    listen    (PORT, () => { 

 console.    log    (\`Server running at http://localhost:${PORT}/\`); 

 }); 

 –––––––– 

 ![image](d2d_images/scene_break.png) 

       SERVE STATIC FILES    from the    public    directory where your custom error pages are stored. 

   Use    res.sendFile    to send the custom error pages for 404 and 500 errors. 

 ![image](d2d_images/image055.png)

 ![image](d2d_images/image192.png)

 ![image](d2d_images/image057.png)

####  Logging Errors 

   L    OGGING ERRORS IS CRUCIAL    for debugging and maintaining your application.   You can use simple logging with    console.error    or more advanced logging libraries like    winston    . 

  Example with Express and Winston    : 

1.    Install Winston    : 

 npm install winston 

  Set Up Winston Logging    : 

 const    express    =    require    ('express'); 

 const winston =    require    ('winston'); 

 const app =    express    (); 

 const logger = winston.    createLogger    ({ 

 level: 'error', 

 format: winston.    format    .    combine    ( 

 winston.    format    .    timestamp    (), 

 winston.    format    .    printf    (({ timestamp, level, message }) => { 

 return \`${timestamp} \[${level}\]: ${message}\`; 

 }) 

 ), 

 transports: \[ 

 new winston.transports.Console(), 

 new winston.transports.File({ filename: 'error.log' }) 

 \] 

 }); 

 // Simulate an error 

 app.    get    ('/error', (req, res,    next    ) => { 

 const err = new Error('Something went wrong!'); 

 err.status = 500; 

  next    (err); 

 }); 

 // Error handling middleware 

 app.    use    ((err, req, res, next) => { 

 logger.    error    (err.stack); 

 res.    status    (err.status || 500).    send    ('500 Internal Server Error'); 

 }); 

 const PORT = 3000; 

 app.    listen    (PORT, () => { 

 console.    log    (\`Server running at http://localhost:${PORT}/\`); 

 }); 

 –––––––– 

 ![image](d2d_images/scene_break.png) 

 ![image](d2d_images/image072.png)  ![image](d2d_images/image213.png)

       CREATE A WINSTON    logger with console and file transports. 

   Use the logger in the error handling middleware to log error details. 

 ![image](d2d_images/image137.png)

 ![image](d2d_images/image001.png)

 –––––––– 

 ![image](d2d_images/scene_break.png) 

##  ​   4.3.   Routing 

   R    OUTING IS THE PROCESS    of determining how an application responds to a client request to a particular endpoint, which is a URI (or path) and a specific HTTP method (GET, POST, etc.).   In Node.js, routing can be implemented using the built-in    http    module or, more commonly, using the    express    framework which provides a more intuitive and powerful routing mechanism. 

####  Basic Routing with HTTP Module 

   T    HE     http    module provides the basic functionalities to set up routing.   However, this method can become cumbersome for larger applications. 

 ![image](d2d_images/image041.png)

  Example using HTTP Module    : 

 const http =    require    ('http'); 

 const url =    require    ('url'); 

 const server = http.    createServer    ((req, res) => { 

 const parsedUrl = url.    parse    (req.url, true); 

 const pathname = parsedUrl.pathname; 

 if (req.method === 'GET' && pathname === '/') { 

 res.statusCode = 200; 

 res.    setHeader    ('Content-Type', 'text/plain'); 

 res.    end    ('Home Page'); 

 } else if (req.method === 'GET' && pathname === '/about') { 

 res.statusCode = 200; 

 res.    setHeader    ('Content-Type', 'text/plain'); 

 res.    end    ('About Page'); 

 } else { 

 res.statusCode = 404; 

 res.    setHeader    ('Content-Type', 'text/plain'); 

 res.    end    ('404 Not Found'); 

 } 

 }); 

 const PORT = 3000; 

 server.    listen    (PORT, () => { 

 console.    log    (\`Server running at http://localhost:${PORT}/\`); 

 }); 

  Explanation    : 

*     The    url    module is used to parse the URL and extract the pathname.  
*    Different responses are sent based on the request method and pathname. 

####  Advanced Routing with Express 

   E    XPRESS IS A WEB APPLICATION    framework for Node.js that simplifies routing and provides a wide range of features for building web and mobile applications. 

  Installing Express    : 

 npm install express 

  Basic Routing with Express    : 

 const    express    =    require    ('express'); 

 const app =    express    (); 

 app.    get    ('/', (req, res) => { 

 res.    send    ('Home Page'); 

 }); 

 app.    get    ('/about', (req, res) => { 

 res.    send    ('About Page'); 

 }); 

 app.    get    ('/users/:id', (req, res) => { 

 const userId = req.params.id; 

 res.    send    (\`User ID: ${userId}\`); 

 }); 

 app.    use    ((req, res,    next    ) => { 

 res.    status    (404).    send    ('404 Not Found'); 

 }); 

 const PORT = 3000; 

 app.    listen    (PORT, () => { 

 console.    log    (\`Server running at http://localhost:${PORT}/\`); 

 }); 

 –––––––– 

 ![image](d2d_images/scene_break.png) 

 ![image](d2d_images/image215.png)

    E    XPLANATION     : 

*    app.get('/')    : Defines a route for GET requests to the root URL.  
*    app.get('/about')    : Defines a route for GET requests to the    /about    URL.  
*    app.get('/users/:id')    : Defines a route for GET requests to    /users/:id    , where    :id    is a route parameter.  
*    app.use((req, res, next) => {...})    : Middleware to handle 404 errors for any unmatched routes.  

####  Using Path Parameters 

   P    ATH PARAMETERS ARE    used to capture values specified at certain positions in the URL. 

  Example with Path Parameters    : 

 app.    get    ('/users/:id/books/:bookId', (req, res) => { 

 const userId = req.params.id; 

 const bookId = req.params.bookId; 

 res.    send    (\`User ID: ${userId}, Book ID: ${bookId}\`); 

 }); 

 –––––––– 

 ![image](d2d_images/scene_break.png) 

    E    XPLANATION     : 

*    :id    and    :bookId    are placeholders for path parameters.  
*    req.params    is used to access these parameters.  

####  Using Query Parameters 

   Q    UERY PARAMETERS ARE    used to pass additional data to the server as key-value pairs in the URL. 

  Example with Query Parameters    : 

 app.    get    ('/search', (req, res) => { 

 const query = req.query.q; 

 res.    send    (\`Search Query: ${query}\`); 

 }); 

  Explanation    : 

*     Query parameters are accessed using    req.query    .  
*     In this example,    req.query.q    retrieves the value of the    q    query parameter.  

####  Handling Different HTTP Methods 

   E    XPRESS MAKES IT EASY    to handle different HTTP methods for the same route. 

  Example    : 

 app.    route    ('/resource') 

 .    get    ((req, res) => { 

 res.    send    ('GET request to /resource'); 

 }) 

 .    post    ((req, res) => { 

 res.    send    ('POST request to /resource'); 

 }) 

 .    put    ((req, res) => { 

 res.    send    ('PUT request to /resource'); 

 }) 

 .    delete    ((req, res) => { 

 res.    send    ('DELETE request to /resource'); 

 }); 

  Explanation    : 

*    app.route('/resource')    : Chaining route handlers for the same route.  
*    Different handlers are defined for GET, POST, PUT, and DELETE requests. 

####  Using Middleware for Routing 

   M    IDDLEWARE FUNCTIONS    are functions that have access to the request object (    req    ), the response object (    res    ), and the next middleware function in the application’s request-response cycle. 

  Example    : 

 app.    use    ((req, res, next) => { 

 console.    log    (\`Request Method: ${req.method}, Request URL: ${req.url}\`); 

  next    (); 

 }); 

 app.    get    ('/', (req, res) => { 

 res.    send    ('Home Page'); 

 }); 

 app.    get    ('/about', (req, res) => { 

 res.    send    ('About Page'); 

 }); 

   Middleware logs the request method and URL for every request. 

     next()    passes control to the next middleware function. 

 ![image](d2d_images/image064.png)

 Routing is a fundamental part of building web applications in Node.js.   Whether using the core    http    module for simple applications or leveraging the powerful features of Express for more complex routing, understanding how to define and manage routes is essential.   Express simplifies routing with its intuitive syntax and additional features, making it a popular choice for Node.js developers. 

##  ​   4.4.   Serving Static Files 

   S    ERVING STATIC FILES    (such as HTML, CSS, JavaScript, images, etc.) is a common requirement for web applications.   Static files are files that do not change on the server and are delivered to the client as-is.   In Node.js, serving static files can be done using the built-in    http    module, but it is more commonly done using the    express    framework, which simplifies the process significantly. 

####  Serving Static Files with HTTP Module 

   W    HILE IT IS POSSIBLE    to serve static files using the core    http    module, it requires more manual setup and handling. 

  Example using HTTP Module    : 

 const http =    require    ('http'); 

 const fs =    require    ('fs'); 

 const path =    require    ('path'); 

 const server = http.    createServer    ((req, res) => { 

 // Construct the file path 

 let filePath = path.    join    (\_\_dirname, 'public', req.url === '/' ?   'index.html' : req.url); 

 // Get the file extension 

 let extname = path.    extname    (filePath); 

 // Set default content type 

 let contentType = 'text/html'; 

 // Determine the content type based on the file extension 

 switch (extname) { 

 case '.js': 

 contentType = 'text/javascript'; 

 break; 

 case '.css': 

 contentType = 'text/css'; 

 break; 

 case '.json': 

 contentType = 'application/json'; 

 break; 

 case '.png': 

 contentType = 'image/png'; 

 break; 

 case '.jpg': 

 contentType = 'image/jpg'; 

 break; 

 } 

 // Read the file and serve it 

 fs.    readFile    (filePath, (err, content) => { 

 if (err) { 

 if (err.code == 'ENOENT') { 

 // File not found 

 fs.    readFile    (path.    join    (\_\_dirname, 'public', '404.html'), (err, content) => { 

 res.    writeHead    (404, { 'Content-Type': 'text/html' }); 

 res.    end    (content, 'utf8'); 

 }); 

 } else { 

 // Some server error 

 res.    writeHead    (500); 

 res.    end    (\`Server Error: ${err.code}\`); 

 } 

 } else { 

 // Serve the file 

 res.    writeHead    (200, { 'Content-Type': contentType }); 

 res.    end    (content, 'utf8'); 

 } 

 }); 

 }); 

 const PORT = 3000; 

 server.    listen    (PORT, () => { 

 console.    log    (\`Server running at http://localhost:${PORT}/\`); 

 }); 

  Explanation    : 

*     This code sets up a basic HTTP server that serves files from a    public    directory.  
*    It determines the content type based on the file extension and serves the file with the correct content type. 
*    If a file is not found, it serves a custom 404 error page. 

 ![image](d2d_images/image102.png)

####  Serving Static Files with Express 

   U    SING EXPRESS, SERVING    static files becomes much simpler with the help of the    express.static    middleware. 

  Example with Express    : 

 project-directory/ 

 ├── public/ 

 │  ├── index.html 

 │  ├── style.css 

 │  └── script.js 

 └── server.js 

   The    express.static    middleware is used to serve static files from the    public    directory. 

   When you access    http://localhost:3000    , Express will look for    index.html    in the    public    directory and serve it. 

####  Customizing the Static Middleware 

   Y    OU CAN CUSTOMIZE THE    behavior of the    express.static    middleware with options such as setting cache control headers, specifying a fallback, and more. 

  Example with Custom Options    : 

 const    express    =    require    ('express'); 

 const path =    require    ('path'); 

 const app =    express    (); 

 const options = { 

 dotfiles: 'ignore', // Options are 'allow', 'deny', 'ignore' 

 etag: false, 

 extensions: \['htm', 'html'\], 

 index: 'index.html', 

 maxAge: '1d', // Cache control 

 redirect: false, 

  setHeaders    : function (res, path, stat) { 

 res.    set    ('x-timestamp', Date.    now    ()); 

 } 

 }; 

 // Serve static files from the "public" directory with custom options 

 app.    use    (    express    .    static    (path.    join    (\_\_dirname, 'public'), options)); 

 const PORT = 3000; 

 app.    listen    (PORT, () => { 

 console.    log    (\`Server running at http://localhost:${PORT}/\`); 

 }); 

  Explanation    : 

  ›  dotfiles    : Controls the handling of dotfiles.   Options are 'allow', 'deny', 'ignore'. 

  ›  etag    : Disables ETag headers. 

  ›  extensions    : Sets default file extension fallback. 

  ›  index    : Specifies the default file to serve. 

  ›  maxAge    : Sets the Cache-Control max-age directive in milliseconds or a string in a format accepted by the ms module. 

  ›  redirect    : Disables redirect for directories without a trailing slash. 

  ›  setHeaders    : Allows you to set custom headers. 

 ![image](d2d_images/image190.png)

 ![image](d2d_images/image006.png)

##  ​   4.5.   Using Middleware 

###  Introduction to Middleware 

   M    IDDLEWARE IS ONE OF    the core concepts of Express.js, a web application framework for Node.js.   Middleware functions are functions that have access to the request object (    req    ), the response object (    res    ), and the next middleware function in the application’s request-response cycle.   Middleware can perform a variety of tasks such as executing code, making changes to the request and response objects, ending the request-response cycle, and calling the next middleware function in the stack. 

 Middleware functions are the heart and soul of Express applications.   They provide a robust mechanism for handling HTTP requests and responses, enabling developers to build complex and feature-rich web applications.   Understanding how middleware works and how to use it effectively is crucial for any developer working with Express. 

 ![image](d2d_images/image184.png)

####  What is Middleware? 

   M    IDDLEWARE IS ESSENTIALLY    a series of functions that are executed in sequence for each request that comes into the server.   Each middleware function can perform operations on the request and response objects, and either pass control to the next middleware function using the    next()    function or end the request-response cycle by sending a response to the client. 

#####  Key Characteristics of Middleware 

1.    Chain of Functions    : Middleware functions form a chain of operations where each function performs a specific task and then passes control to the next function in the sequence. 
2.    Access to Request and Response Objects    : Middleware functions have access to the request (    req    ) and response (    res    ) objects, allowing them to read from and modify these objects as needed. 
3.    Control Flow    : Middleware functions can control the flow of the request-response cycle.   By calling    next()    , they pass control to the next middleware function.   If they do not call    next()    , the request-response cycle ends. 
4.    Order Matters    : The order in which middleware functions are defined is important.   They are executed in the order they are added to the application. 

###  Types of Middleware 

   M    IDDLEWARE IN EXPRESS    .js can be broadly categorized into three types: built-in middleware, third-party middleware, and custom middleware.   Each type serves different purposes and provides various functionalities that help streamline the development process and enhance the capabilities of your web applications. 

####  Built-in Middleware 

   E    XPRESS.JS COMES WITH    a set of built-in middleware functions that provide basic but essential functionalities.   These middleware functions are integrated into Express and do not require any additional installation.   The most commonly used built-in middleware functions include: 

  express.static    : 

*     Purpose     : Serves static files such as HTML, CSS, JavaScript, images, and other assets.  
*     Usage     : This middleware is essential for delivering static content to the client directly from the server.  

  express.json    : 

*     Purpose     : Parses incoming requests with JSON payloads and is based on    body-parser    .  
*     Usage     : This middleware is useful for APIs that expect JSON data in the request body.  

  express.urlencoded    : 

*     Purpose     : Parses incoming requests with URL-encoded payloads.   This is typically used for HTML form submissions.  
*     Usage    : This middleware is useful for handling form submissions where the data is encoded in the URL. 

####  Third-Party Middleware 

   T    HIRD-PARTY MIDDLEWARE    is developed and maintained by the community.   These middleware functions provide additional functionalities that are not included in the built-in middleware of Express.   They can be installed via npm and are widely used in Express applications.   Some popular third-party middleware include: 

  morgan    : 

*     Purpose     : HTTP request logger middleware for Node.js.   It logs requests in a predefined format and is useful for debugging and monitoring HTTP requests.  
*     Usage    : Helps track and log HTTP requests made to the server. 

 npm install morgan 

  body-parser    : 

*     Purpose     : Parses incoming request bodies in a middleware before your handlers, available under the    req.body    property.  
*     Usage     : Useful for parsing JSON, URL-encoded, and raw data in the request body.  

 npm install body-parser 

  cors    : 

*     Purpose     : Provides a Connect/Express middleware that can be used to enable Cross-Origin Resource Sharing (CORS) with various options.  
*     Usage     : Allows or restricts resources on a web server to be requested from another domain.  

 npm install cors 

  helmet    : 

*     Purpose     : Helps secure Express apps by setting various HTTP headers.  
*     Usage    : Provides protection against well-known web vulnerabilities by setting HTTP headers appropriately. 

 npm install helmet 

 ![image](d2d_images/image051.png)

####  Custom Middleware 

   C    USTOM MIDDLEWARE FUNCTIONS    are those you create yourself to meet specific requirements of your application.   These middleware functions can perform tasks like logging, authentication, error handling, and more. 

  Example of Custom Middleware    : 

1.    Logging Middleware    : 

 const    express    =    require    ('express'); 

 const app =    express    (); 

 // Custom logging middleware 

 app.    use    ((req, res,    next    ) => { 

 console.    log    (\`Request Method: ${req.method}, Request URL: ${req.url}\`); 

  next    (); // Pass control to the next middleware function 

 }); 

 app.    get    ('/', (req, res) => { 

 res.    send    ('Hello, World!'); 

 }); 

 const PORT = 3000; 

 app.    listen    (PORT, () => { 

 console.    log    (\`Server running at http://localhost:${PORT}/\`); 

 }); 

 –––––––– 

 ![image](d2d_images/scene_break.png) 

 ![image](d2d_images/image007.png)

    A    UTHENTICATION MIDDLEWARE     : 

 const    express    =    require    ('express'); 

 const app =    express    (); 

 // Custom authentication middleware 

 const    authenticate    = (req, res, next) => { 

 const auth = req.headers.authorization; 

 if (auth && auth === 'mysecrettoken') { 

  next    (); // User is authenticated, proceed to the next middleware 

 } else { 

 res.    status    (401).    send    ('Unauthorized'); 

 } 

 }; 

 app.    use    (    authenticate    ); 

 app.    get    ('/', (req, res) => { 

 res.    send    ('Authenticated!'); 

 }); 

 const PORT = 3000; 

 app.    listen    (PORT, () => { 

 console.    log    (\`Server running at http://localhost:${PORT}/\`); 

 }); 

 –––––––– 

 ![image](d2d_images/scene_break.png) 

 ![image](d2d_images/image071.png)

    E    RROR HANDLING MIDDLEWARE     : 

 const    express    =    require    ('express'); 

 const app =    express    (); 

 // Define the route that throws an error 

 app.    get    ('/', (req, res) => { 

 throw new Error('Simulated error'); // This will be caught by the error handler 

 }); 

 // Custom error-handling middleware 

 app.    use    ((err, req, res, next) => { 

 console.    error    (err.stack); 

 res.    status    (500).    send    ('Something broke 😑 !'); 

 }); 

 const PORT = 3000; 

 app.    listen    (PORT, () => { 

 console.    log    (\`Server running at http://localhost:${PORT}/\`); 

 }); 

 ![image](d2d_images/image123.png)

     Logging Middleware    : Logs the request method and URL for every incoming request. 

     Authentication Middleware    : Checks if the request contains a specific authorization token and either allows the request to proceed or responds with a 401 Unauthorized status. 

     Error Handling Middleware    : Catches errors thrown by other middleware functions or route handlers and sends a 500 Internal Server Error response. 

 ![image](d2d_images/image103.png)

###  Third-Party Middleware 

####  Morgan 

####  What is Morgan? 

   M    ORGAN IS A POPULAR    HTTP request logger middleware for Node.js.   It simplifies the process of logging requests made to your server, which is crucial for debugging and monitoring your applications.   By providing detailed logs of each request, Morgan helps developers understand how their applications are being used and identify potential issues. 

 Morgan can be configured to log various details about each request, such as the method, URL, response status, response time, and more.   It supports multiple predefined formats, and you can also create custom formats to suit your needs. 

####  Why Use Morgan? 

*     Debugging     : Helps in identifying issues by providing detailed logs of each request.  
*     Monitoring     : Tracks the performance and usage of your application.  
*     Audit Trails     : Maintains a record of all requests for security and compliance purposes.  
*     Customizable     : Allows you to define custom logging formats based on your requirements.  

####  Installing Morgan 

   T    O USE MORGAN IN YOUR    Node.js application, you first need to install it using npm: 

 npm install morgan 

####  Basic Usage of Morgan 

   H    ERE’S A BASIC EXAMPLE    of how to use Morgan in an Express application: 

  First Set Up an Express Application    : 

 const    express    =    require    ('express'); 

 const    morgan    =    require    ('morgan'); 

 const app =    express    (); 

 // Use Morgan for logging requests 

 app.    use    (    morgan    ('combined')); 

 // Define a simple route 

 app.    get    ('/', (req, res) => { 

 res.    send    ('Hello, World!'); 

 }); 

 const PORT = 3000; 

 app.    listen    (PORT, () => { 

 console.    log    (\`Server running at http://localhost:${PORT}/\`); 

 }); 

*     Import Express and Morgan     : We require both the    express    and    morgan    modules.  
*     Use Morgan Middleware     : The    app.use(morgan('combined'))    line integrates Morgan into our application.   The    'combined'    format provides a comprehensive logging format that includes the remote IP, request method, URL, HTTP version, response status, response time, and more.  
*     Define a Route     : We define a simple route that responds with "Hello, World!"   when accessed.  

  Running the Application    : 

 node server.js 

 Open your browser or use a tool like Postman to navigate to http://localhost:3000. 

  Viewing the Logs    : 

*    After making a request to the server, you will see detailed logs in your console similar to this: 

 ![image](d2d_images/image002.png)

####  Customizing Morgan 

   M    ORGAN SUPPORTS SEVERAL    predefined formats, such as 'combined', 'common', 'dev', 'short', and 'tiny'.   You can also create custom formats to log specific details that are important to you. 

  Example of a Custom Format    : 

1.    Define a Custom Format    : 

 const    express    =    require    ('express'); 

 const    morgan    =    require    ('morgan'); 

 const app =    express    (); 

 // Define a custom format 

  morgan    .    format    ('myFormat', ':method :url :status :res\[content-length\] - :response-time ms'); 

 // Use the custom format 

 app.    use    (    morgan    ('myFormat')); 

 app.    get    ('/', (req, res) => { 

 res.    send    ('Hello, Custom Logger!'); 

 }); 

 const PORT = 3000; 

 app.    listen    (PORT, () => { 

 console.    log    (\`Server running at http://localhost:${PORT}/\`); 

 }); 

 –––––––– 

 ![image](d2d_images/scene_break.png) 

 ![image](d2d_images/image026.png)

           Custom Format Definition    : The    morgan.format('myFormat', ':method :url :status :res\[content-length\] - :response-time ms')    line defines a custom logging format named 'myFormat'.   This format logs the HTTP method, URL, response status, content length, and response time. 

     Using the Custom Format    : We use the custom format by passing 'myFormat' to the    morgan    middleware. 

  Viewing the Custom Logs    : 

*    After making a request to the server, you will see logs in your console formatted according to your custom format: 

 ![image](d2d_images/image014.png)

 ![image](d2d_images/image060.png)

###  Body-Parser 

####  What is Body-Parser? 

   B    ODY-PARSER IS A MIDDLEWARE    for Express.js that allows you to parse incoming request bodies in a middleware before your handlers, making the body contents available under the    req.body    property.   This is particularly useful for handling form submissions, JSON payloads, and other types of data sent in the body of HTTP requests. 

 Body-Parser simplifies the process of extracting data sent by the client, whether it's in JSON format, URL-encoded form data, or other formats.   This makes it an essential tool for developing APIs and handling various types of request data in web applications. 

####  Why Use Body-Parser? 

*     Simplifies Data Handling     : Extracts and parses data from the request body, making it easily accessible.  
*     Supports Multiple Formats     : Can parse JSON, URL-encoded data, and raw data.  
*     Integration with Express     : Seamlessly integrates with Express.js to handle request bodies.  
*     Security     : Helps in validating and sanitizing incoming data to prevent common security vulnerabilities like SQL injection and XSS.  

####  Installing Body-Parser 

   T    O USE BODY-PARSER    in your Node.js application, you first need to install it using npm: 

 npm install body-parser 

####  Basic Usage of Body-Parser 

   H    ERE’S A BASIC EXAMPLE    of how to use Body-Parser in an Express application to handle JSON and URL-encoded data: 

1.    Set Up an Express Application    : 

 const    express    =    require    ('express'); 

 const bodyParser =    require    ('body-parser'); 

 const app =    express    (); 

 // Use Body-Parser middleware to parse JSON and URL-encoded data 

 app.    use    (bodyParser.    json    ()); 

 app.    use    (bodyParser.    urlencoded    ({ extended: true })); 

 // Define a simple POST route to handle form data 

 app.    post    ('/submit', (req, res) => { 

 const { name, email } = req.body; 

 res.    send    (\`Received name: ${name}, email: ${email}\`); 

 }); 

 const PORT = 3000; 

 app.    listen    (PORT, () => { 

 console.    log    (\`Server running at http://localhost:${PORT}/\`); 

 }); 

 Start the server by running: 

 node server.js 

  Testing with Postman    : 

*    Create a new POST request. 
*     Set the URL to    http://localhost:3000/submit    .  
*     In the Body tab, select    raw    and    JSON    , then enter:  

 { 

 "name": "John Doe", 

 "email": "john.doe@example.com" 

 } 

 Click    Send    . 

 ![image](d2d_images/image047.png)

 –––––––– 

 ![image](d2d_images/scene_break.png) 

####  Handling Different Data Formats with Body-Parser 

   B    ODY-PARSER CAN BE    configured to handle various types of data formats.   Below are examples of how to configure Body-Parser for JSON, URL-encoded, and raw data. 

  1.   JSON Data    : 

 app.    use    (bodyParser.    json    ()); 

 Example 

 { 

 "name": "John Doe", 

 "email": "john.doe@example.com" 

 } 

  2.   URL-encoded Data    : 

 app.use(bodyParser.urlencoded({ extended: true })); 

  Example    : 

 name=John+Doe&email=john.doe%40example.com 

  Raw Data    : 

 app.use(bodyParser.raw()); 

  Example    : 

 This is raw data 

  4.   Text Data    : 

 app.use(bodyParser.text()); 

  Example    : 

 This is plain text data 

####  Customizing Body-Parser 

   B    ODY-PARSER PROVIDES    options to customize its behavior.   For instance, you can limit the size of the request body to prevent abuse, or you can configure the extended option for URL-encoded data. 

  Example with Custom Options    : 

 const    express    =    require    ('express'); 

 const bodyParser =    require    ('body-parser'); 

 const app =    express    (); 

 // Use Body-Parser with custom options 

 app.    use    (bodyParser.    json    ({ limit: '10mb' })); 

 app.    use    (bodyParser.    urlencoded    ({ extended: false, limit: '10mb' })); 

 app.    post    ('/submit', (req, res) => { 

 const { name, email } = req.body; 

 res.    send    (\`Received name: ${name}, email: ${email}\`); 

 }); 

 const PORT = 3000; 

 app.    listen    (PORT, () => { 

 console.    log    (\`Server running at http://localhost:${PORT}/\`); 

 }); 

     Limit Option    : The    limit    option restricts the maximum size of the request body to 10MB. 

     Extended Option    : The    extended    option determines whether to use the querystring library (when    false    ) or the qs library (when    true    ) for parsing URL-encoded data. 

 ![image](d2d_images/image003.png)

###  Helmet 

####  What is Helmet? 

   H    ELMET IS A SECURITY    -focused middleware for Express.js that helps secure your application by setting various HTTP headers.   It aims to protect your app from some well-known web vulnerabilities by configuring appropriate HTTP headers.   These vulnerabilities include cross-site scripting (XSS), clickjacking, and other common attacks that can be mitigated by setting the correct headers. 

####  Why Use Helmet? 

*     Security     : Provides a straightforward way to secure your application by setting HTTP headers.  
*     Simplicity     : Easy to implement and configure.  
*     Comprehensive     : Covers various aspects of security by enabling multiple security-related headers.  
*     Customization     : Allows you to configure each header individually to suit your specific security needs.  

####  Installing Helmet 

   T    O USE HELMET IN YOUR    Node.js application, you first need to install it using npm: 

 npm install helmet 

####  Basic Usage of Helmet 

   H    ERE’S A BASIC EXAMPLE    of how to use Helmet in an Express application: 

1.    Set Up an Express Application    : 

 const    express    =    require    ('express'); 

 const helmet =    require    ('helmet'); 

 const app =    express    (); 

 // Use Helmet to secure the app by setting various HTTP headers 

 app.    use    (    helmet    ()); 

 // Define a simple route 

 app.    get    ('/', (req, res) => { 

 res.    send    ('Hello, secure world!'); 

 }); 

 const PORT = 3000; 

 app.    listen    (PORT, () => { 

 console.    log    (\`Server running at http://localhost:${PORT}/\`); 

 }); 

     Import Express and Helmet    : We require both the    express    and    helmet    modules. 

     Use Helmet Middleware    : The    app.use(helmet())    line integrates Helmet into our application, automatically setting various HTTP headers for enhanced security. 

     Define a Route    : We define a simple route that responds with "Hello, secure world!"   when accessed. 

   Open your browser or use a tool like Postman to navigate to    http://localhost:3000    . 

   Check the response headers to see the security headers added by Helmet. 

 ![image](d2d_images/image220.png)

 ![image](d2d_images/image112.png)

####  Headers Set by Helmet 

   H    ELMET SETS A VARIETY    of HTTP headers to help secure your application.   Some of the key headers include: 

*     Content-Security-Policy (CSP)     : Helps prevent XSS attacks by controlling the sources from which content can be loaded.  
*     X-DNS-Prefetch-Control     : Controls DNS prefetching, which can improve privacy.  
*     Expect-CT     : Helps detect and prevent the use of misissued SSL certificates.  
*     Strict-Transport-Security (HSTS)     : Enforces secure (HTTP over SSL/TLS) connections to the server.  
*     X-Frame-Options     : Protects against clickjacking by controlling whether the site can be framed.  
*     X-Content-Type-Options     : Prevents browsers from interpreting files as a different MIME type, reducing the risk of drive-by downloads.  
*     X-Permitted-Cross-Domain-Policies     : Controls the Adobe Flash and Acrobat cross-domain policies.  
*     Referrer-Policy     : Controls the amount of referrer information sent with requests.  
*     Feature-Policy     : Allows control over which browser features can be used.  

####  Customizing Helmet 

   W    HILE THE DEFAULT CONFIGURATION    of Helmet provides a good level of security, you might want to customize it to suit your specific needs.   You can enable or disable specific headers and configure their values. 

  Example of Custom Configuration    : 

 const    express    =    require    ('express'); 

 const helmet =    require    ('helmet'); 

 const app =    express    (); 

 // Custom Helmet configuration 

 app.    use    (    helmet    ({ 

 contentSecurityPolicy: { 

 directives: { 

 defaultSrc: \["'self'"\], 

 scriptSrc: \["'self'", "'trusted-scripts.com'"\], 

 objectSrc: \["'none'"\], 

 upgradeInsecureRequests: \[\], 

 }, 

 }, 

 referrerPolicy: { policy: 'no-referrer' }, 

 featurePolicy: { 

 features: { 

 fullscreen: \["'self'"\], 

 vibrate: \["'none'"\], 

 } 

 } 

 })); 

 app.    get    ('/', (req, res) => { 

 res.    send    ('Hello, secure world!'); 

 }); 

 const PORT = 3000; 

 app.    listen    (PORT, () => { 

 console.    log    (\`Server running at http://localhost:${PORT}/\`); 

 }); 

     Content-Security-Policy    : Configures the content security policy to allow scripts only from the same origin and from    trusted-scripts.com    , and disallows the use of objects. 

     Referrer-Policy    : Sets the referrer policy to    no-referrer    , meaning no referrer information will be sent. 

     Feature-Policy    : Restricts the use of certain browser features to specific sources. 

###  Practical Example: Secure REST API with Helmet 

   H    ERE’S A PRACTICAL    example of using Helmet to secure a REST API: 

1.    Set Up an Express Application    : 

 const    express    =    require    ('express'); 

 const helmet =    require    ('helmet'); 

 const app =    express    (); 

 // Use Helmet to secure the app by setting various HTTP headers 

 app.    use    (    helmet    ()); 

 // Parse JSON request bodies 

 app.    use    (    express    .    json    ()); 

 // Define a simple API endpoint 

 app.    get    ('/api/data', (req, res) => { 

 res.    json    ({ message: 'Secure data' }); 

 }); 

 const PORT = 3000; 

 app.    listen    (PORT, () => { 

 console.    log    (\`Server running at http://localhost:${PORT}/\`); 

 }); 

 –––––––– 

 ![image](d2d_images/scene_break.png) 

           Helmet Middleware    : Secures the application by setting various HTTP headers. 

     JSON Parsing Middleware    : Parses JSON request bodies using    express.json()    . 

     API Endpoint    : Defines a simple GET endpoint that returns a JSON response. 

  Testing the API    : 

*     Open your browser or use a tool like Postman to navigate to    http://localhost:3000/api/data    .  
*    Check the response headers to see the security headers added by Helmet. 

 ![image](d2d_images/image161.png)

 ![image](d2d_images/image156.png)

###  Creating Custom Middleware 

   I    N THIS COMPREHENSIVE    guide, we will build an Express.js application from scratch that demonstrates the use of custom middleware.   This example will include an HTML page for ease of understanding and will cover various middleware functionalities such as logging, authentication, error handling, rate limiting, and input validation. 

 We'll use the following project structure: 

 ![image](d2d_images/image063.png)  custom-middleware-app/ 

 ├── node\_modules/ 

 ├── public/ 

 │  └── index.html 

 ├── middlewares/ 

 │  ├── logger.js 

 │  ├── auth.js 

 │  ├── rateLimiter.js 

 │  ├── validateInput.js 

 │  └── errorHandler.js 

 ├── routes/ 

 │  └── api.js 

 ├── app.js 

 └── package.json 

 First, set up the project and install the necessary dependencies. 

 mkdir custom-middleware-app 

 cd custom-middleware-app 

 npm init -y 

 npm install express body-parser morgan 

###  Step 2: Create the HTML Page 

   C    REATE AN     index.html    file inside the    public    directory. 

  public/index.html    : 

 <!DOCTYPE html> 

 <html lang="en"> 

 <head> 

 <meta charset="UTF-8"> 

 <meta name="viewport" content="width=device-width, initial-scale=1.0"> 

 <title>Custom Middleware Example</title> 

 </head> 

 <body> 

 <h1>Welcome to the Custom Middleware Example</h1> 

 <p>This page demonstrates the use of custom middleware in an Express.js application.</p> 

 </body> 

 </html> 

 –––––––– 

 ![image](d2d_images/scene_break.png) 

###  Step 3: Implement Custom Middleware 

   C    REATE CUSTOM MIDDLEWARE    for logging requests, handling authentication, error handling, rate limiting, and input validation. 

  middlewares/logger.js    : 

 module.exports = (req, res, next) => { 

 console.    log    (\`${req.method} ${req.url} - ${new Date().    toISOString    ()}\`); 

  next    (); 

 }; 

  middlewares/auth.js    : 

 module.exports = (req, res, next) => { 

 const authHeader = req.headers.authorization; 

 if (authHeader && authHeader === 'Bearer mysecrettoken') { 

  next    (); 

 } else { 

 res.    status    (401).    json    ({ message: 'Unauthorized' }); 

 } 

 }; 

  middlewares/errorHandler.js    : 

 module.exports = (err, req, res, next) => { 

 console.    error    (err.stack); 

 res.    status    (500).    json    ({ message: 'Something went wrong!'   }); 

 }; 

  middlewares/rateLimiter.js    : 

 const rateLimit = {}; 

 module.exports = (req, res, next) => { 

 const userIp = req.ip; 

 const currentTime = Date.    now    (); 

 const timeWindow = 60000; // 1 minute 

 const requestLimit = 10; 

 if (!rateLimit\[userIp\]) { 

 rateLimit\[userIp\] = \[\]; 

 } 

 // Filter requests within the time window 

 rateLimit\[userIp\] = rateLimit\[userIp\].    filter    (timestamp => currentTime - timestamp < timeWindow); 

 if (rateLimit\[userIp\].length >= requestLimit) { 

 res.    status    (429).    json    ({ message: 'Too many requests, please try again later.'   }); 

 } else { 

 rateLimit\[userIp\].push(currentTime); 

  next    (); 

 } 

 }; 

  middlewares/validateInput.js    : 

 module.exports = (req, res, next) => { 

 const { title, description } = req.body; 

 if (!title || typeof title !== 'string' || title.    trim    () === '') { 

 return res.    status    (400).    json    ({ message: 'Invalid title' }); 

 } 

 if (!description || typeof description !== 'string' || description.    trim    () === '') { 

 return res.    status    (400).    json    ({ message: 'Invalid description' }); 

 } 

  next    (); 

 }; 

 –––––––– 

 ![image](d2d_images/scene_break.png) 

###  Step 4: Set Up Routes 

   C    REATE AN API ROUTE    to demonstrate the use of custom middleware. 

  routes/api.js    : 

 const    express    =    require    ('express'); 

 const router =    express    .    Router    (); 

 const authMiddleware =    require    ('../middlewares/auth'); 

 const rateLimiterMiddleware =    require    ('../middlewares/rateLimiter'); 

 const validateInputMiddleware =    require    ('../middlewares/validateInput'); 

 // Protected route with rate limiting 

 router.    get    ('/protected', authMiddleware, rateLimiterMiddleware, (req, res) => { 

 res.    json    ({ message: 'This is a protected route' }); 

 }); 

 // POST /api/resource - Create a new resource with input validation 

 router.    post    ('/resource', validateInputMiddleware, (req, res) => { 

 const { title, description } = req.body; 

 res.    status    (201).    json    ({ message: 'Resource created', data: { title, description } }); 

 }); 

 module.exports = router; 

###  Step 5: Set Up the Main Application 

   C    REATE THE MAIN APPLICATION    file to use the custom middleware and serve the static HTML page. 

  app.js    : 

 const    express    =    require    ('express'); 

 const path =    require    ('path'); 

 const bodyParser =    require    ('body-parser'); 

 const    morgan    =    require    ('morgan'); 

 const loggerMiddleware =    require    ('./middlewares/logger'); 

 const errorHandlerMiddleware =    require    ('./middlewares/errorHandler'); 

 const apiRoutes =    require    ('./routes/api'); 

 const app =    express    (); 

 // Use Morgan for logging requests 

 app.    use    (    morgan    ('combined')); 

 // Use custom logger middleware 

 app.    use    (loggerMiddleware); 

 // Use Body-Parser middleware to parse JSON data 

 app.    use    (bodyParser.    json    ()); 

 // Serve static files from the public directory 

 app.    use    (    express    .    static    (path.    join    (\_\_dirname, 'public'))); 

 // API Routes 

 app.    use    ('/api', apiRoutes); 

 // Use custom error handling middleware 

 app.    use    (errorHandlerMiddleware); 

 const PORT = 3000; 

 app.    listen    (PORT, () => { 

 console.    log    (\`Server running at http://localhost:${PORT}/\`); 

 }); 

 –––––––– 

 ![image](d2d_images/scene_break.png) 

   S    TEP 6: TESTING THE    Application 

 node app.js 

  Access the application    : 

*     Open your browser and navigate to    http://localhost:3000    to see the static HTML page.  
*     Use Postman to test the API endpoints:   
    *     GET    http://localhost:3000/api/protected (with header Authorization: Bearer token): Should return a protected message or rate limit message if requests exceed the limit. 
    *     POST    http://localhost:3000/api/resource (with JSON body {"title": "My Title", "description": "My Description"}): Should create a resource if the input is valid, otherwise return an error message. 

 ![image](d2d_images/image107.png)

 –––––––– 

 ![image](d2d_images/scene_break.png) 

##  ​   4.6.   Building a Simple Blog Server 

   I    N THIS EXAMPLE, WE    will build a simple blog server using Express.js.   This server will include functionalities for creating, reading, updating, and deleting blog posts.   We will also implement middleware for logging requests, handling authentication, input validation, and error handling. 

###  Project Structure 

   H    ERE IS THE PROJECT    structure for the blog server: 

 blog-server/ 

 ├── node\_modules/ 

 ├── public/ 

 │  └── index.html 

 ├── middlewares/ 

 │  ├── logger.js 

 │  ├── auth.js 

 │  ├── validatePost.js 

 │  └── errorHandler.js 

 ├── routes/ 

 │  └── blog.js 

 ├── app.js 

 └── package.json 

 Step 1: Initialize the Project 

 mkdir blog-server 

 cd blog-server 

 npm init -y 

 npm install express body-parser morgan 

###  Step 2: Create the HTML Page 

   C    REATE AN     index.html    file inside the    public    directory. 

  public/index.html    : 

 <!DOCTYPE html> 

 <html lang="en"> 

 <head> 

 <meta charset="UTF-8"> 

 <meta name="viewport" content="width=device-width, initial-scale=1.0"> 

 <title>Simple Blog Server</title> 

 </head> 

 <body> 

 <h1>Welcome to the Simple Blog Server</h1> 

 <p>This page demonstrates a simple blog server built with Express.js.</p> 

 </body> 

 </html> 

###  Step 3: Implement Custom Middleware 

   C    REATE CUSTOM MIDDLEWARE    for logging requests, handling authentication, input validation, and error handling. 

  middlewares/logger.js    : 

 module.exports = (req, res, next) => { 

 console.    log    (\`${req.method} ${req.url} - ${new Date().    toISOString    ()}\`); 

  next    (); 

 }; 

  middlewares/auth.js    : 

 module.exports = (req, res, next) => { 

 const authHeader = req.headers.authorization; 

 if (authHeader && authHeader === 'Bearer mysecrettoken') { 

  next    (); 

 } else { 

 res.    status    (401).    json    ({ message: 'Unauthorized' }); 

 } 

 }; 

  middlewares/errorHandler.js    : 

 module.exports = (err, req, res, next) => { 

 console.    error    (err.stack); 

 res.    status    (500).    json    ({ message: 'Something went wrong!'   }); 

 }; 

  middlewares/validatePost.js    : 

 module.exports = (req, res, next) => { 

 const { title, content } = req.body; 

 if (!title || typeof title !== 'string' || title.    trim    () === '') { 

 return res.    status    (400).    json    ({ message: 'Invalid title' }); 

 } 

 if (!content || typeof content !== 'string' || content.    trim    () === '') { 

 return res.    status    (400).    json    ({ message: 'Invalid content' }); 

 } 

  next    (); 

 }; 

###  Step 4: Set Up Routes 

   C    REATE ROUTES TO HANDLE    blog post CRUD operations. 

  routes/blog.js    : 

 const    express    =    require    ('express'); 

 const router =    express    .    Router    (); 

 const authMiddleware =    require    ('../middlewares/auth'); 

 const validatePostMiddleware =    require    ('../middlewares/validatePost'); 

 // Mock database 

 let posts = \[\]; 

 // GET /api/posts - Get all posts 

 router.    get    ('/posts', (req, res) => { 

 res.    json    (posts); 

 }); 

 // GET /api/posts/:id - Get a single post by ID 

 router.    get    ('/posts/:id', (req, res) => { 

 const post = posts.    find    (p => p.id ===    parseInt    (req.params.id)); 

 if (!post) { 

 return res.    status    (404).    json    ({ message: 'Post not found' }); 

 } 

 res.    json    (post); 

 }); 

 // POST /api/posts - Create a new post 

 router.    post    ('/posts', authMiddleware, validatePostMiddleware, (req, res) => { 

 const { title, content } = req.body; 

 const newPost = { id: posts.length + 1, title, content }; 

 posts.    push    (newPost); 

 res.    status    (201).    json    (newPost); 

 }); 

 // PUT /api/posts/:id - Update a post by ID 

 router.    put    ('/posts/:id', authMiddleware, validatePostMiddleware, (req, res) => { 

 const post = posts.    find    (p => p.id ===    parseInt    (req.params.id)); 

 if (!post) { 

 return res.    status    (404).    json    ({ message: 'Post not found' }); 

 } 

 const { title, content } = req.body; 

 post.title = title; 

 post.content = content; 

 res.    json    (post); 

 }); 

 // DELETE /api/posts/:id - Delete a post by ID 

 router.    delete    ('/posts/:id', authMiddleware, (req, res) => { 

 posts = posts.    filter    (p => p.id !==    parseInt    (req.params.id)); 

 res.    json    ({ message: 'Post deleted' }); 

 }); 

 module.exports = router; 

 –––––––– 

 ![image](d2d_images/scene_break.png) 

###  Step 5: Set Up the Main Application 

   C    REATE THE MAIN APPLICATION    file to use the custom middleware and serve the static HTML page. 

  app.js    : 

 const    express    =    require    ('express'); 

 const path =    require    ('path'); 

 const bodyParser =    require    ('body-parser'); 

 const    morgan    =    require    ('morgan'); 

 const loggerMiddleware =    require    ('./middlewares/logger'); 

 const errorHandlerMiddleware =    require    ('./middlewares/errorHandler'); 

 const blogRoutes =    require    ('./routes/blog'); 

 const app =    express    (); 

 // Use Morgan for logging requests 

 app.    use    (    morgan    ('combined')); 

 // Use custom logger middleware 

 app.    use    (loggerMiddleware); 

 // Use Body-Parser middleware to parse JSON data 

 app.    use    (bodyParser.    json    ()); 

 // Serve static files from the public directory 

 app.    use    (    express    .    static    (path.    join    (\_\_dirname, 'public'))); 

 // Blog Routes 

 app.    use    ('/api', blogRoutes); 

 // Use custom error handling middleware 

 app.    use    (errorHandlerMiddleware); 

 const PORT = process.env.PORT || 3000; 

 app.    listen    (PORT, () => { 

 console.    log    (\`Server running at http://localhost:${PORT}/\`); 

 }); 

 –––––––– 

 ![image](d2d_images/scene_break.png) 

       OPEN YOUR BROWSER    and navigate to    http://localhost:3000    to see the static HTML page. 

   Use a tool like Postman to test the API endpoints: 

*     GET    http://localhost:3000/api/posts    : Should return all posts.  
*     POST    http://localhost:3000/api/posts    (with header    Authorization: Bearer token    and JSON body    {"title": "My First Post", "content": "This is the content of my first post"}    ): Should create a new post.  
*     GET    http://localhost:3000/api/posts/1    : Should return the post with ID 1.  
*     PUT    http://localhost:3000/api/posts/1    (with header    Authorization: Bearer mysecrettoken    and JSON body    {"title": "Updated Title", "content": "Updated content"}    ): Should update the post with ID 1.  
*     DELETE    http://localhost:3000/api/posts/1    (with header    Authorization: Bearer mysecrettoken    ): Should delete the post with ID 1.  

 ![image](d2d_images/image012.png)

 
|  ![image](d2d_images/chapter_title_corner_decoration_left.png)  ||  ||  ![image](d2d_images/chapter_title_corner_decoration_right.png)  |
| --- | --- | --- |

 ![image](d2d_images/chapter_title_above.png) 

#  ​   ![image](d2d_images/image173.png)  5.   Networking and Security 

 ![image](d2d_images/chapter_title_below.png) 

    D    ownload OpenSSL     : 

*    Visit the OpenSSL for Windows website. 
*    Download the appropriate version (typically the "Win64 OpenSSL v1.1.x" for 64-bit systems). 

 brew install openssl 

##  ​   5.1.   Working with TCP and UDP Servers 

   T    CP (TRANSMISSION CONTROL    Protocol) and UDP (User Datagram Protocol) are two fundamental protocols that form the backbone of internet communication.   Understanding these protocols is essential for developing networked applications.   This section will delve into the details of TCP and UDP, their differences, use cases, and how to implement servers using Node.js. 

####  TCP (Transmission Control Protocol) 

   T    CP IS A CONNECTION    -oriented protocol that ensures reliable and ordered delivery of data between applications.   Here’s a breakdown of its key characteristics: 

1.    Reliability    : TCP ensures that all data sent from the sender reaches the receiver without errors.   If any data is lost or corrupted during transmission, TCP will detect this and retransmit the affected data. 
2.    Connection-Oriented    : Before any data transfer occurs, TCP establishes a connection between the sender and receiver through a process known as the TCP handshake.   This three-step process (SYN, SYN-ACK, ACK) ensures both parties are ready for communication. 
3.    Ordered Data Transfer    : TCP guarantees that data packets are delivered in the order they were sent.   If packets arrive out of order, TCP reorders them before passing them to the application layer. 
4.    Flow Control    : TCP uses flow control mechanisms to prevent the sender from overwhelming the receiver with too much data at once.   This is achieved through the use of a sliding window protocol. 
5.    Congestion Control    : TCP dynamically adjusts the rate of data transmission based on network congestion.   This helps in optimizing the use of network resources and preventing network collapse due to excessive load. 

 ![image](d2d_images/image098.png)

#####  Implementing a TCP Server in Node.js 

   H    ERE’S HOW TO CREATE    a simple TCP server in Node.js: 

  Import the Net Module    : The    net    module in Node.js provides an asynchronous network API for creating TCP servers. 

 const net =    require    ('net'); 

 C 

  reate the Server    : Use the    net.createServer()    method to create a new TCP server. 

 const server = net.    createServer    ((socket) => { 

 console.    log    ('Client connected'); 

 socket.    on    ('data', (data) => { 

 console.    log    ('Data received: ' + data); 

 }); 

 socket.    on    ('end', () => { 

 console.    log    ('Client disconnected'); 

 }); 

 socket.    write    ('Welcome to the TCP server!\\n'); 

 }); 

 server.    listen    (3000, () => { 

 console.    log    ('Server is listening on port 3000'); 

 }); 

  Run the Server    : Save the file and run the server using    node filename.js    .   You can use a TCP client like    telnet    to connect to the server and send data. 

####  UDP (User Datagram Protocol) 

   U    DP IS A CONNECTIONLESS    protocol that emphasizes speed over reliability.   It is often used in applications where real-time performance is critical and some data loss is acceptable, such as video streaming or online gaming. 

1.    Speed    : UDP is faster than TCP because it does not establish a connection before sending data.   This reduces latency, making it suitable for time-sensitive applications. 
2.    Connectionless    : Unlike TCP, UDP does not establish a connection before data transfer.   Each data packet, called a datagram, is sent independently. 
3.    Unreliable    : UDP does not guarantee the delivery of data packets.   If a packet is lost or arrives out of order, UDP does not attempt to retransmit or reorder it. 
4.    No Flow or Congestion Control    : UDP does not have built-in mechanisms for flow or congestion control, making it simpler but less robust than TCP. 

#####  Implementing a UDP Server in Node.js 

   H    ERE’S HOW TO CREATE    a simple UDP server in Node.js: 

1.    Import the Dgram Module    : The    dgram    module in Node.js provides an API for UDP datagram sockets. 

 const dgram =    require    ('dgram'); 

  Create the Server    : Use the    dgram.createSocket()    method to create a new UDP server. 

 const server = dgram.    createSocket    ('udp4'); 

 server.    on    ('message', (msg, rinfo) => { 

 console.    log    (\`Server received: ${msg} from ${rinfo.address}:${rinfo.port}\`); 

 }); 

 server.    on    ('listening', () => { 

 const address = server.    address    (); 

 console.    log    (\`Server listening on ${address.address}:${address.port}\`); 

 }); 

 server.    bind    (4000); // The server will listen on port 4000 

  Run the Server    : Save the file and run the server using    node filename.js    .   You can use a UDP client tool to send datagrams to the server. 

####  Differences Between TCP and UDP 

   U    NDERSTANDING THE DIFFERENCES    between TCP and UDP is crucial for choosing the right protocol for your application: 

1.    Reliability    : TCP is reliable and ensures data integrity, while UDP is unreliable and does not guarantee delivery. 
2.    Connection    : TCP is connection-oriented, requiring a handshake before communication.   UDP is connectionless and sends data without establishing a connection. 
3.    Speed    : TCP is slower due to its reliability features.   UDP is faster but sacrifices reliability. 
4.    Use Cases    : TCP is used for applications where reliability is critical, such as web servers, email, and file transfers.   UDP is used for applications requiring low latency, such as video streaming, online gaming, and VoIP (Voice over IP). 

 ![image](d2d_images/image189.png)

####  Use Cases for TCP and UDP 

  ❖     TCP Use Cases    : 

  ❖     Web Servers    : HTTP/HTTPS protocols rely on TCP for reliable data transfer. 

  ❖     Email Services    : SMTP, IMAP, and POP3 protocols use TCP to ensure email delivery. 

  ❖     File Transfers    : Protocols like FTP and SFTP use TCP to guarantee complete file transmission. 

  ❖     UDP Use Cases    : 

  ❖     Live Streaming    : Applications like Twitch and YouTube Live use UDP to minimize latency. 

  ❖     Online Gaming    : Games like Fortnite and Call of Duty use UDP for real-time multiplayer experiences. 

  ❖     VoIP    : Services like Skype and Zoom use UDP to ensure smooth voice and video calls. 

 ![image](d2d_images/image181.png)

##  ​   5.2.   Handling Secure Communications with HTTPS 

   I    N TODAY'S DIGITAL    landscape, ensuring secure communication over the internet is paramount.   HTTPS (HyperText Transfer Protocol Secure) is the secure version of HTTP, providing encryption and authentication to safeguard data transmitted between a client and a server.   This section will explore the principles of HTTPS, how it works, and how to implement it in Node.js. 

####  Understanding HTTPS 

   H    TTPS USES SSL (SECURE    Sockets Layer) or its successor, TLS (Transport Layer Security), to encrypt the data exchanged between a client and a server.   This encryption ensures that even if the data is intercepted, it cannot be read without the encryption keys. 

1.    Encryption    : HTTPS encrypts data using symmetric encryption for the data exchange and asymmetric encryption for key exchange.   This ensures that sensitive information, such as login credentials, personal data, and payment details, remains confidential. 
2.    Authentication    : HTTPS verifies the identity of the server using digital certificates issued by trusted Certificate Authorities (CAs).   This prevents man-in-the-middle attacks where an attacker could impersonate the server. 
3.    Data Integrity    : HTTPS ensures that the data sent and received is not tampered with during transmission.   Any modification to the data would be detected, ensuring the integrity of the communication. 

 ![image](d2d_images/image097.png)

####  How HTTPS Works 

1.    SSL/TLS Handshake    : When a client connects to an HTTPS server, an SSL/TLS handshake occurs.   This process involves the client and server agreeing on encryption algorithms and exchanging encryption keys. 
2.    Certificate Verification    : During the handshake, the server presents its SSL/TLS certificate.   The client verifies this certificate against a list of trusted CAs.   If the certificate is valid, the client proceeds with the connection. 
3.    Session Encryption    : Once the handshake is complete, a secure session is established.   All data exchanged during this session is encrypted using the agreed-upon encryption methods. 
4.    Data Exchange    : Encrypted data is transmitted between the client and server.   Both parties can decrypt the data using the session keys established during the handshake. 

####  Implementing HTTPS in Node.js 

   T    O SET UP AN HTTPS    server in Node.js, you need an SSL/TLS certificate and the corresponding private key.   You can obtain these from a trusted CA or generate self-signed certificates for development purposes. 

#####  Steps to Implement HTTPS in Node.js 

1.    Install the     https     Module    : Node.js provides a built-in    https    module for creating HTTPS servers. 

   C    ONST HTTPS =     require    ('https'); 

 const fs =    require    ('fs'); 

 const    express    =    require    ('express'); 

 const app =    express    (); 

 // Load SSL/TLS certificates 

 const options = { 

 key: fs.    readFileSync    ('path/to/private-key.pem'), 

 cert: fs.    readFileSync    ('path/to/certificate.pem') 

 }; 

 // Create an HTTPS server 

 const server = https.    createServer    (options, app); 

 // Sample route 

 app.    get    ('/', (req, res) => { 

 res.    send    ('Hello, secure world!'); 

 }); 

 // Start the server 

 server.    listen    (3000, () => { 

 console.    log    ('HTTPS server running on port 3000'); 

 }); 

  Generate SSL/TLS Certificates    : For development purposes, you can generate self-signed certificates using OpenSSL: 

 openssl req -nodes -new -x509 -keyout private-key.pem -out certificate.pem 

  Use Middleware for Secure Headers    : Enhance security by using middleware like    helmet    to set secure HTTP headers. 

 const helmet =    require    ('helmet'); 

 app.    use    (    helmet    ()); 

  Redirect HTTP to HTTPS    : Ensure all traffic is encrypted by redirecting HTTP requests to HTTPS.   Use middleware to handle this redirection. 

 app.    use    ((req, res, next) => { 

 if (req.secure) { 

  next    (); 

 } else { 

 res.    redirect    (\`https://${req.headers.host}${req.url}\`); 

 } 

 }); 

  Force HTTPS in Production    : Configure your web server (like Nginx or Apache) or cloud provider to enforce HTTPS connections and redirect HTTP traffic to HTTPS. 

 ![image](d2d_images/image175.png)

 ![image](d2d_images/image176.png)

##  ​   5.3.   Implementing Authentication and Authorization 

   I    N WEB APPLICATIONS    , ensuring that users are who they claim to be (authentication) and controlling their access to resources (authorization) are critical for security.   Authentication verifies the identity of a user, while authorization determines what resources the user is allowed to access.   Implementing robust authentication and authorization mechanisms is essential for protecting sensitive data and maintaining the integrity of your application. 

####  Authentication 

   A    UTHENTICATION IS THE    process of verifying the identity of a user.   Common methods include: 

1.    Password-Based Authentication    : Users provide a username and password, which are checked against stored credentials. 
2.    Token-Based Authentication    : Users receive a token (e.g., JWT) after logging in, which they include in subsequent requests to prove their identity. 
3.    OAuth    : Users authenticate through a third-party provider (e.g., Google, Facebook) and receive a token to access the application. 

#####  Implementing JWT Authentication in Node.js 

   J    SON WEB TOKENS (JWT    ) are a popular method for implementing authentication.   They provide a secure way to transmit information between parties and are stateless, meaning the server doesn't need to store session data. 

 ![image](d2d_images/image144.png)

  Install Required Packages    : 

 npm install jsonwebtoken bcryptjs body-parser 

  Create User Model and Sample Data    : 

  models/user.js    : 

 const users = \[ 

 { 

 id: 1, 

 username: 'user1', 

 password: '$2a$10$CwTycUXWue0Thq9StjUM0uJ8BRg.GtOvBtt/RCK3GGbS1j3M4eCqa' // hashed password 'password1' 

 } 

 \]; 

 module.exports = users; 

  Set Up Authentication Routes    : 

  routes/auth.js    : 

 const express =    require    ('express'); 

 const jwt =    require    ('jsonwebtoken'); 

 const bcrypt =    require    ('bcryptjs'); 

 const users =    require    ('../models/user'); 

 const router = express.    Router    (); 

 const SECRET\_KEY = 'your\_secret\_key'; 

 // Login Route 

 router.    post    ('/login', (req, res) => { 

 const { username, password } = req.body; 

 const user = users.    find    (u => u.username === username); 

 if (!user) { 

 return res.    status    (401).    json    ({ message: 'Invalid credentials' }); 

 } 

 const isValidPassword = bcrypt.    compareSync    (password, user.password); 

 if (!isValidPassword) { 

 return res.    status    (401).    json    ({ message: 'Invalid credentials' }); 

 } 

 const token = jwt.    sign    ({ id: user.id }, SECRET\_KEY, { expiresIn: '1h' }); 

 res.    json    ({ token }); 

 }); 

 // Protected Route 

 router.    get    ('/protected', (req, res) => { 

 const token = req.headers.authorization.    split    (' ')\[1\]; 

 if (!token) { 

 return res.    status    (401).    json    ({ message: 'No token provided' }); 

 } 

 try { 

 const decoded = jwt.    verify    (token, SECRET\_KEY); 

 res.    json    ({ message: 'Access granted', userId: decoded.id }); 

 } catch (error) { 

 res.    status    (401).    json    ({ message: 'Invalid token' }); 

 } 

 }); 

 module.exports = router; 

  Integrate Authentication Routes into Your Application    : 

  app.js    : 

 const    express    =    require    ('express'); 

 const bodyParser =    require    ('body-parser'); 

 const authRoutes =    require    ('./routes/auth'); 

 const app =    express    (); 

 app.    use    (bodyParser.    json    ()); 

 app.    use    ('/auth', authRoutes); 

 const PORT = process.env.PORT || 3000; 

 app.    listen    (PORT, () => { 

 console.    log    (\`Server running on port ${PORT}\`); 

 }); 

####  Authorization 

   A    UTHORIZATION CONTROLS    what actions a user can perform and what resources they can access.   It’s often implemented through role-based access control (RBAC) or attribute-based access control (ABAC). 

1.    Role-Based Access Control (RBAC)    : Users are assigned roles, and roles have permissions.   For example, an "admin" role might have access to all resources, while a "user" role has limited access. 
2.    Attribute-Based Access Control (ABAC)    : Access is granted based on attributes of the user, resource, and environment.   This allows for more fine-grained control compared to RBAC. 

#####  Implementing Role-Based Authorization 

1.    Extend User Model with Roles    : 

   M    ODELS/USER.JS  

 const users = \[ 

 { 

 id: 1, 

 username: 'user1', 

 password: '$2a$10$CwTycUXWue0Thq9StjUM0uJ8BRg.GtOvBtt/RCK3GGbS1j3M4eCqa', // hashed password 'password1' 

 role: 'user' 

 }, 

 { 

 id: 2, 

 username: 'admin', 

 password: '$2a$10$7sHhBft6A8IzTmKfv92BVuBPXk8lUNW.s2hlcX0DxE.MhAp.kTF7i', // hashed password 'admin123' 

 role: 'admin' 

 } 

 \]; 

 module.exports = users; 

  Create Middleware for Role-Based Authorization    : 

  middlewares/authorize.js    : 

 const jwt =    require    ('jsonwebtoken'); 

 const users =    require    ('../models/user'); 

 const SECRET\_KEY = 'your\_secret\_key'; 

 function    authorize    (roles = \[\]) { 

 // roles param can be a single role string (e.g., 'admin') or an array of roles (e.g., \['admin', 'user'\]) 

 if (typeof roles === 'string') { 

 roles = \[roles\]; 

 } 

 return (req, res, next) => { 

 const token = req.headers.authorization.    split    (' ')\[1\]; 

 if (!token) { 

 return res.    status    (401).    json    ({ message: 'No token provided' }); 

 } 

 try { 

 const decoded = jwt.    verify    (token, SECRET\_KEY); 

 const user = users.    find    (u => u.id === decoded.id); 

 if (!user || (roles.length && !roles.    includes    (user.role))) { 

 return res.    status    (403).    json    ({ message: 'Forbidden' }); 

 } 

 req.user = user; 

  next    (); 

 } catch (error) { 

 res.    status    (401).    json    ({ message: 'Invalid token' }); 

 } 

 }; 

 } 

  module    .    exports    =    authorize    ; 

  Protect Routes with Role-Based Middleware    : 

  routes/protected.js    : 

 const    express    =    require    ('express'); 

 const    authorize    =    require    ('../middlewares/authorize'); 

 const router =    express    .    Router    (); 

 // Admin-only route 

 router.    get    ('/admin',    authorize    ('admin'), (req, res) => { 

 res.    json    ({ message: 'Welcome, admin!'   }); 

 }); 

 // User and Admin route 

 router.    get    ('/user',    authorize    (\['user', 'admin'\]), (req, res) => { 

 res.    json    ({ message: \`Welcome, ${req.user.role}!\` }); 

 }); 

 module.exports = router; 

  Integrate Protected Routes into Your Application    : 

  app.js    : 

 const    express    =    require    ('express'); 

 const bodyParser =    require    ('body-parser'); 

 const authRoutes =    require    ('./routes/auth'); 

 const protectedRoutes =    require    ('./routes/protected'); 

 const app =    express    (); 

 app.    use    (bodyParser.    json    ()); 

 app.    use    ('/auth', authRoutes); 

 app.    use    ('/protected', protectedRoutes); 

 const PORT = process.env.PORT || 3000; 

 app.    listen    (PORT, () => { 

 console.    log    (\`Server running on port ${PORT}\`); 

 }); 

 ![image](d2d_images/image021.png)

 ![image](d2d_images/image200.png)

##  ​   5.4.   Secure Coding Practices in Node.js 

   S    ECURE CODING PRACTICES    are essential for building resilient and robust applications that can withstand malicious attacks.   Node.js, with its asynchronous nature and extensive ecosystem, offers both opportunities and challenges in terms of security.   This section will cover best practices for writing secure Node.js code, ensuring that your applications remain safe from common vulnerabilities and threats. 

 ![image](d2d_images/image005.png)

####  Input Validation and Sanitization 

1.    Validate All Inputs    : Always validate inputs from all sources, including user inputs, API requests, and data from other services.   Use validation libraries like    Joi    or    validator    to ensure data conforms to expected formats. 

   C    ONST JOI =     require    ('joi'); 

 const schema = Joi.    object    ({ 

 username: Joi.    string    ().    alphanum    ().    min    (3).    max    (30).    required    (), 

 password: Joi.    string    ().    pattern    (new RegExp('^\[a-zA-Z0-9\]{3,30}$')).    required    () 

 }); 

 const { error, value } = schema.    validate    ({ username: 'user1', password: 'password1' }); 

 if (error) { 

 console.    error    ('Validation error:', error.details); 

 } else { 

 console.    log    ('Validated data:', value); 

 } 

  Sanitize Inputs    : Remove or escape potentially dangerous characters from inputs to prevent injection attacks.   Use libraries like    sanitize-html    for sanitizing HTML inputs. 

 const sanitizeHtml =    require    ('sanitize-html'); 

 const sanitized =    sanitizeHtml    ('<script>alert("xss");</script>', { 

 allowedTags: \[\], 

 allowedAttributes: {} 

 }); 

 console.    log    ('Sanitized input:', sanitized); // Output: '' 

 –––––––– 

 ![image](d2d_images/scene_break.png) 

####  Avoiding SQL Injection 

    U    SE PARAMETERIZED QUERIES     : When interacting with databases, use parameterized queries or prepared statements to prevent SQL injection attacks.   Libraries like    pg    for PostgreSQL or    mysql2    for MySQL support parameterized queries. 

 const { Client } =    require    ('pg'); 

 const client = new Client(); 

 const userId = 1; // example user input 

 const query = 'SELECT \* FROM users WHERE id = $1'; 

 client.    query    (query, \[userId\], (err, res) => { 

 if (err) { 

 console.    error    ('Query error:', err.stack); 

 } else { 

 console.    log    ('Query result:', res.rows); 

 } 

 }); 

####  Protecting Against Cross-Site Scripting (XSS) 

1.    Escape Output    : When rendering user-generated content in HTML, escape special characters to prevent XSS attacks.   Use templating engines like Pug or Handlebars, which automatically escape output. 

   //-    PUG EXAMPLE  

 p= userInput // Automatically escapes userInput 

 const Handlebars =    require    ('handlebars'); 

 const template = Handlebars.    compile    ('<p>{{userInput}}</p>'); 

 const result =    template    ({ userInput: '<script>alert("xss");</script>' }); 

 console.    log    ('Escaped output:', result); // Output: <p>&lt;script&gt;alert("xss");&lt;/script&gt;</p> 

 –––––––– 

 ![image](d2d_images/scene_break.png) 

####  Using Security Headers 

1.    Set Security Headers    : Use middleware like    helmet    to set security-related HTTP headers, enhancing the security of your application by preventing common attacks. 

   C    ONST HELMET =     require    ('helmet'); 

 const    express    =    require    ('express'); 

 const app =    express    (); 

 app.    use    (    helmet    ()); 

 app.    get    ('/', (req, res) => { 

 res.    send    ('Hello, secure world!'); 

 }); 

 const PORT = process.env.PORT || 3000; 

 app.    listen    (PORT, () => { 

 console.    log    (\`Server running on port ${PORT}\`); 

 }); 

####  Preventing Cross-Site Request Forgery (CSRF) 

1.    Use CSRF Protection    : Implement CSRF protection to prevent unauthorized actions being performed on behalf of authenticated users.   Use middleware like    csurf    to add CSRF tokens to forms and validate them on the server. 

   C    ONST CSURF =     require    ('csurf'); 

 const cookieParser =    require    ('cookie-parser'); 

 const    express    =    require    ('express'); 

 const app =    express    (); 

 app.    use    (    cookieParser    ()); 

 app.    use    (    csurf    ({ cookie: true })); 

 app.    get    ('/form', (req, res) => { 

 res.    send    (\`<form action="/process" method="POST"> 

 <input type="hidden" name="\_csrf" value="${req.    csrfToken    ()}"> 

 <button type="submit">Submit</button> 

 </form>\`); 

 }); 

 app.    post    ('/process', (req, res) => { 

 res.    send    ('Form processed'); 

 }); 

 const PORT = process.env.PORT || 3000; 

 app.    listen    (PORT, () => { 

 console.    log    (\`Server running on port ${PORT}\`); 

 }); 

####  Secure Authentication and Authorization 

    U    SE STRONG PASSWORD    Hashing    : Always hash passwords before storing them in your database.   Use libraries like    bcrypt    to apply strong, adaptive hashing algorithms. 

 const bcrypt =    require    ('bcryptjs'); 

 const password = 'mySecurePassword'; 

 const saltRounds = 10; 

 bcrypt.    hash    (password, saltRounds, (err, hash) => { 

 if (err) { 

 console.    error    ('Hashing error:', err); 

 } else { 

 console.    log    ('Hashed password:', hash); 

 } 

 }); 

  Implement Role-Based Access Control (RBAC)    : Define roles and permissions for different types of users, and check these roles before allowing access to sensitive resources. 

 const    express    =    require    ('express'); 

 const app =    express    (); 

 const roles = { 

 admin: \['read', 'write', 'delete'\], 

 user: \['read'\] 

 }; 

 function    checkPermission    (role, permission) { 

 return roles\[role\] && roles\[role\].    includes    (permission); 

 } 

 app.    get    ('/secure-data', (req, res) => { 

 const userRole = req.headers.role; // Assume role is sent in headers for simplicity 

 if (    checkPermission    (userRole, 'read')) { 

 res.    send    ('Secure data accessed'); 

 } else { 

 res.    status    (403).    send    ('Forbidden'); 

 } 

 }); 

 const PORT = process.env.PORT || 3000; 

 app.    listen    (PORT, () => { 

 console.    log    (\`Server running on port ${PORT}\`); 

 }); 

####  Ensuring Data Integrity and Privacy 

    E    NCRYPT SENSITIVE DATA     : Encrypt sensitive data both in transit and at rest to protect it from unauthorized access.   Use HTTPS for data in transit and encryption libraries for data at rest. 

 const crypto =    require    ('crypto'); 

 const algorithm = 'aes-256-cbc'; 

 const key = crypto.    randomBytes    (32); 

 const iv = crypto.    randomBytes    (16); 

 function    encrypt    (text) { 

 let cipher = crypto.    createCipheriv    (algorithm, Buffer.    from    (key), iv); 

 let encrypted = cipher.    update    (text); 

 encrypted = Buffer.    concat    (\[encrypted, cipher.    final    ()\]); 

 return { iv: iv.    toString    ('hex'), encryptedData: encrypted.    toString    ('hex') }; 

 } 

 function    decrypt    (text) { 

 let iv = Buffer.    from    (text.iv, 'hex'); 

 let encryptedText = Buffer.    from    (text.encryptedData, 'hex'); 

 let decipher = crypto.    createDecipheriv    (algorithm, Buffer.    from    (key), iv); 

 let decrypted = decipher.    update    (encryptedText); 

 decrypted = Buffer.    concat    (\[decrypted, decipher.    final    ()\]); 

 return decrypted.    toString    (); 

 } 

 const data = 'Sensitive information'; 

 const encryptedData =    encrypt    (data); 

 console.    log    ('Encrypted data:', encryptedData); 

 const decryptedData =    decrypt    (encryptedData); 

 console.    log    ('Decrypted data:', decryptedData); 

####  Regular Security Audits and Updates 

    K    EEP DEPENDENCIES UP    to Date    : Regularly update your Node.js dependencies to ensure you have the latest security patches.   Use tools like    npm audit    to identify and fix vulnerabilities. 

 npm audit 

  Conduct Security Audits    : Perform regular security audits to identify and address potential vulnerabilities in your application.   Use automated tools and manual reviews to ensure comprehensive coverage. 

 ![image](d2d_images/image223.png)

 ![image](d2d_images/image135.png)

##  ​   5.5.   Practical Examples: Building a Chat Application 

   B    UILDING A CHAT APPLICATION    is an excellent way to understand various networking and security concepts in Node.js.   This practical example will cover setting up a basic chat application using WebSocket for real-time communication, implementing authentication, and ensuring secure communication.   By the end of this example, you will have a fully functional chat application that you can expand and customize. 

 chat-app/ 

 ├── certs/ 

 │  ├── private-key.pem 

 │  └── certificate.pem 

 ├── middlewares/ 

 │  ├── auth.js 

 ├── models/ 

 │  ├── user.js 

 ├── public/ 

 │  ├── index.html 

 │  ├── styles.css 

 ├── routes/ 

 │  ├── auth.js 

 │  ├── chat.js 

 ├── app.js 

 ├── package.json 

####  Step-by-Step Guide to Building a Chat Application 

###  Step 1: Setting Up the Project 

    C    REATE A NEW DIRECTORY    for your project    and initialize it with npm: 

 mkdir chat-app 

 cd chat-app 

 npm init -y 

  Install the required dependencies    : 

 npm install express ws jsonwebtoken bcryptjs body-parser 

  Create the necessary project files and directories    : 

 touch app.js 

 mkdir models routes middlewares 

 touch models/user.js routes/auth.js routes/chat.js middlewares/auth.js 

###  Step 2: Setting Up the User Model and Sample Data 

    M    ODELS/USER.JS     : 

 const bcrypt =    require    ('bcryptjs'); 

 const users = \[ 

 { 

 id: 1, 

 username: 'user1', 

 password: bcrypt.    hashSync    ('password1', 10) // hashed password 

 }, 

 { 

 id: 2, 

 username: 'user2', 

 password: bcrypt.    hashSync    ('password2', 10) // hashed password 

 } 

 \]; 

 module.exports = users; 

###  Step 3: Implementing Authentication Routes 

    R    OUTES/AUTH.JS     : 

 const    express    =    require    ('express'); 

 const jwt =    require    ('jsonwebtoken'); 

 const bcrypt =    require    ('bcryptjs'); 

 const users =    require    ('../models/user'); 

 const router =    express    .    Router    (); 

 const SECRET\_KEY = 'your\_secret\_key'; 

 // Login Route 

 router.    post    ('/login', (req, res) => { 

 const { username, password } = req.body; 

 const user = users.    find    (u => u.username === username); 

 if (!user) { 

 return res.    status    (401).    json    ({ message: 'Invalid credentials' }); 

 } 

 const isValidPassword = bcrypt.    compareSync    (password, user.password); 

 if (!isValidPassword) { 

 return res.    status    (401).    json    ({ message: 'Invalid credentials' }); 

 } 

 const token = jwt.    sign    ({ id: user.id }, SECRET\_KEY, { expiresIn: '1h' }); 

 res.    json    ({ token }); 

 }); 

 module.exports = router; 

###  Step 4: Setting Up WebSocket for Real-Time Communication 

    R    OUTES/CHAT.JS     : 

 const WebSocket =    require    ('ws'); 

 const jwt =    require    ('jsonwebtoken'); 

 const users =    require    ('../models/user'); 

 const SECRET\_KEY = 'your\_secret\_key'; 

 const    chatHandler    = (server) => { 

 const wss = new WebSocket.Server({ server }); 

 wss.    on    ('connection', (ws, req) => { 

 const token = req.url.    split    ('token=')\[1\]; 

 if (!token) { 

 ws.    close    (); 

 } 

 try { 

 const decoded = jwt.    verify    (token, SECRET\_KEY); 

 const user = users.    find    (u => u.id === decoded.id); 

 if (!user) { 

 ws.    close    (); 

 } 

 ws.    on    ('message', (message) => { 

 const msg = JSON.    parse    (message); 

 const broadcastMessage = { 

 user: user.username, 

 message: msg.message, 

 timestamp: new Date().    toISOString    () 

 }; 

 wss.clients.    forEach    (client => { 

 if (client.readyState === WebSocket.OPEN) { 

 client.    send    (JSON.    stringify    (broadcastMessage)); 

 } 

 }); 

 }); 

 } catch (error) { 

 ws.    close    (); 

 } 

 }); 

 }; 

 module.    exports    =    chatHandler    ; 

###  Step 5: Creating Middleware for Authentication 

    M    IDDLEWARES/AUTH.JS     : 

 const jwt =    require    ('jsonwebtoken'); 

 const users =    require    ('../models/user'); 

 const SECRET\_KEY = 'your\_secret\_key'; 

 const    authMiddleware    = (req, res, next) => { 

 const token = req.headers.authorization.    split    (' ')\[1\]; 

 if (!token) { 

 return res.    status    (401).    json    ({ message: 'No token provided' }); 

 } 

 try { 

 const decoded = jwt.    verify    (token, SECRET\_KEY); 

 const user = users.    find    (u => u.id === decoded.id); 

 if (!user) { 

 return res.    status    (403).    json    ({ message: 'Forbidden' }); 

 } 

 req.user = user; 

  next    (); 

 } catch (error) { 

 res.    status    (401).    json    ({ message: 'Invalid token' }); 

 } 

 }; 

 module.    exports    =    authMiddleware    ; 

###  Step 6: Integrating Everything in the Main Application File 

    A    PP.JS     : 

 const    express    =    require    ('express'); 

 const bodyParser =    require    ('body-parser'); 

 const http =    require    ('http'); 

 const authRoutes =    require    ('./routes/auth'); 

 const chatHandler =    require    ('./routes/chat'); 

 const authMiddleware =    require    ('./middlewares/auth'); 

 const app =    express    (); 

 app.    use    (bodyParser.    json    ()); 

 // Authentication Routes 

 app.    use    ('/auth', authRoutes); 

 // Protected Route Example 

 app.    get    ('/protected', authMiddleware, (req, res) => { 

 res.    json    ({ message: 'Access granted', user: req.user.username }); 

 }); 

 const server = http.    createServer    (app); 

 // WebSocket Chat Handler 

  chatHandler    (server); 

 const PORT = process.env.PORT || 3000; 

 server.    listen    (PORT, () => { 

 console.    log    (\`Server running on port ${PORT}\`); 

 }); 

###  Step 7: Creating a Simple Client 

   C    REATE A BASIC HTML    file to test the chat application. 

  public/index.html    : 

 <!DOCTYPE html> 

 <html lang="en"> 

 <head> 

 <meta charset="UTF-8"> 

 <title>Chat Application</title> 

 <script> 

 let ws; 

 function    login    () { 

 const username = document.    getElementById    ('username').value; 

 const password = document.    getElementById    ('password').value; 

  fetch    ('/auth/login', { 

 method: 'POST', 

 headers: { 'Content-Type': 'application/json' }, 

 body: JSON.    stringify    ({ username, password }) 

 }).    then    (response => response.    json    ()) 

 .    then    (data => { 

 if (data.token) { 

 ws = new    WebSocket    (\`ws://localhost:3000?token=${data.token}\`); 

 ws.    onmessage    = (event) => { 

 const msg = JSON.    parse    (event.data); 

 const chat = document.    getElementById    ('chat'); 

 chat.innerHTML += \`<p><strong>${msg.user}:</strong> ${msg.message} <em>${msg.timestamp}</em></p>\`; 

 }; 

 } else { 

  alert    ('Login failed'); 

 } 

 }); 

 } 

 function    sendMessage    () { 

 const message = document.    getElementById    ('message').value; 

 ws.    send    (JSON.    stringify    ({ message })); 

 document.    getElementById    ('message').value = ''; 

 } 

 </script> 

 </head> 

 <body> 

 <div> 

 <h1>Login</h1> 

 <input type="text" id="username" placeholder="Username"> 

 <input type="password" id="password" placeholder="Password"> 

 <button onclick="    login    ()">Login</button> 

 </div> 

 <div> 

 <h1>Chat</h1> 

 <div id="chat"></div> 

 <input type="text" id="message" placeholder="Type a message"> 

 <button onclick="    sendMessage    ()">Send</button> 

 </div> 

 </body> 

 </html> 

     Open the chat client    : 

*    Open your browser and navigate to http://localhost:3000 to access the chat client. 

     Test the application    : 

*     Log in using one of the sample users (    user1/password1    or    user2/password2    ).  
*    Start sending messages and see them appear in real-time. 

 ![image](d2d_images/image039.png)

 
|  ![image](d2d_images/chapter_title_corner_decoration_left.png)  ||  ||  ![image](d2d_images/chapter_title_corner_decoration_right.png)  |
| --- | --- | --- |

 ![image](d2d_images/chapter_title_above.png) 

#  ​   ![image](d2d_images/image150.png)  6.   Databases 

 ![image](d2d_images/chapter_title_below.png) 

##  ​   6.1.   Introduction to Databases with Node.js 

   D    atabases are a     fundamental component    of modern web applications, enabling the storage, retrieval, and management of vast amounts of data.   In the context of Node.js, databases are crucial for maintaining user information, managing application data, and ensuring data persistence across sessions.   There are two primary types of databases used in Node.js applications: SQL and NoSQL databases.   Each type has its own strengths and use cases, which will be explored in this section. 

 ![image](d2d_images/image207.png)

  SQL    databases, also known as relational databases, store data in tables with predefined schemas.   These tables are structured in rows and columns, where each row represents a record and each column represents a data attribute.   SQL databases use Structured Query Language (SQL) for defining, manipulating, and querying data.   Examples of SQL databases include MySQL, PostgreSQL, SQLite, and Microsoft SQL Server.   One of the main advantages of SQL databases is their ability to handle complex queries and transactions.   They enforce data integrity through constraints and relationships between tables, which is essential for applications requiring robust data consistency. 

  NoSQL    databases, on the other hand, are designed to handle a wide variety of data models, including document, key-value, column-family, and graph formats.   These databases are known for their flexibility, scalability, and performance.   Examples of NoSQL databases include MongoDB, Redis, Cassandra, and Couchbase.   Unlike SQL databases, NoSQL databases do not require a fixed schema, allowing for dynamic changes in the data structure.   This flexibility makes them ideal for applications with large volumes of unstructured or semi-structured data, such as social media platforms, real-time analytics, and content management systems , In Node.js, interacting with databases can be done through various modules and libraries tailored for each type of database.   For SQL databases, popular modules include    mysql    for MySQL and    pg    for PostgreSQL.   These modules provide methods to establish connections, execute queries, and manage transactions.   For NoSQL databases, commonly used modules include    mongodb    for MongoDB and    redis    for Redis.   These modules facilitate operations such as inserting, updating, and retrieving data, as well as managing indexes and collections. 

 Scientific principles underpin the design and operation of databases, ensuring they can efficiently store and retrieve data while maintaining integrity and performance.   One such principle is    ACID    compliance, which stands for Atomicity, Consistency, Isolation, and Durability.   ACID properties are essential for ensuring reliable transaction processing in SQL databases.   Atomicity guarantees that all operations within a transaction are completed successfully or none at all.   Consistency ensures that a transaction brings the database from one valid state to another.   Isolation prevents concurrent transactions from interfering with each other, and Durability ensures that once a transaction is committed, it remains persistent even in the event of a system failure. 

 ![image](d2d_images/image199.png)

 NoSQL databases, while often prioritizing scalability and performance, may adopt different consistency models, such as eventual consistency.   Eventual consistency is a consistency model used in distributed systems where updates to a database will propagate and eventually all nodes will converge to the same value.   This model is particularly useful for systems that require high availability and partition tolerance, as described by the CAP theorem.   The CAP theorem states that a distributed data store can only achieve two out of three guarantees: Consistency, Availability, and Partition tolerance.   NoSQL databases often trade off strict consistency for better availability and partition tolerance, making them suitable for applications with high read and write loads. 

 ![image](d2d_images/image138.png)

##  ​   6.2.   Working with SQL Databases (MySQL) 

   S    QL DATABASES ARE A    cornerstone of data management in many web applications, and MySQL is one of the most popular SQL database management systems.   Known for its reliability, performance, and ease of use, MySQL is used by organizations of all sizes, from small startups to large enterprises.   This section will explore how to work with MySQL in a Node.js environment, including setting up the database, establishing connections, performing CRUD operations, and understanding advanced features like transactions and indexing. 

####  Setting Up MySQL 

   B    EFORE WORKING WITH    MySQL in Node.js, you need to install and configure MySQL on your system.   You can download MySQL from the official website and follow the installation instructions for your operating system.   Once installed, you can start the MySQL server and use the MySQL command-line client or a graphical tool like MySQL Workbench to manage your databases. 

 ![image](d2d_images/image159.png)

####  Installing MySQL Module for Node.js 

   T    O INTERACT WITH MYSQL    from a Node.js application, you need to install the    mysql    module.   This module provides methods to connect to a MySQL database, execute queries, and manage connections. 

 npm install mysql 

####  Establishing a Connection 

   E    STABLISHING A CONNECTION    to a MySQL database involves creating a connection object with the necessary configuration details such as host, user, password, and database name.   Here's an example of how to establish a connection: 

 const mysql =    require    ('mysql'); 

 const connection = mysql.    createConnection    ({ 

 host: 'localhost', 

 user: 'root', 

 password: 'password', 

 database: 'my\_database' 

 }); 

 connection.    connect    ((err) => { 

 if (err) { 

 console.    error    ('Error connecting to MySQL:', err); 

 return; 

 } 

 console.    log    ('Connected to MySQL'); 

 }); 

####  Performing CRUD Operations 

   C    RUD OPERATIONS (CREATE    , Read, Update, Delete) are the fundamental operations for interacting with a database.   Let's look at how to perform these operations using the    mysql    module in Node.js. 

 Creating (Inserting) Data: 

 To insert data into a table, you can use the    INSERT INTO    SQL statement.   Here’s an example of inserting a new user into a    users    table: 

 const user = { username: 'johndoe', password: 'securepassword' }; 

 const query = 'INSERT INTO users SET ?'; 

 connection.    query    (query, user, (err, results) => { 

 if (err) throw err; 

 console.    log    ('User added with ID:', results.insertId); 

 }); 

 Reading (Selecting) Data: 

 To retrieve data from a table, you can use the    SELECT    SQL statement.   Here’s an example of selecting all users from the    users    table: 

 const query = 'SELECT \* FROM users'; 

 connection.    query    (query, (err, results) => { 

 if (err) throw err; 

 console.    log    ('User data:', results); 

 }); 

 Updating Data: 

 To update existing data in a table, you can use the    UPDATE    SQL statement.   Here’s an example of updating a user’s password: 

 const userId = 1; 

 const newPassword = 'newsecurepassword'; 

 const query = 'UPDATE users SET password = ?   WHERE id = ?'; 

 connection.    query    (query, \[newPassword, userId\], (err, results) => { 

 if (err) throw err; 

 console.    log    ('Changed rows:', results.changedRows); 

 }); 

 –––––––– 

 ![image](d2d_images/scene_break.png) 

   D    ELETING DATA:  

 To delete data from a table, you can use the    DELETE    SQL statement.   Here’s an example of deleting a user from the    users    table: 

 const userId = 1; 

 const query = 'DELETE FROM users WHERE id = ?'; 

 connection.    query    (query, userId, (err, results) => { 

 if (err) throw err; 

 console.    log    ('Deleted rows:', results.affectedRows); 

 }); 

####  Advanced Features: Transactions and Indexing 

   T    RANSACTIONS:  

 Transactions are a sequence of one or more SQL operations executed as a single unit.   They ensure data integrity and consistency, especially in cases where multiple operations depend on each other.   Transactions follow the ACID properties: Atomicity, Consistency, Isolation, and Durability. 

 To perform transactions in MySQL with Node.js, you can use the    BEGIN    ,    COMMIT    , and    ROLLBACK    SQL statements.   Here’s an example of a transaction: 

 connection.    beginTransaction    ((err) => { 

 if (err) throw err; 

 const query1 = 'INSERT INTO accounts SET ?'; 

 const account1 = { user\_id: 1, balance: 100 }; 

 connection.    query    (query1, account1, (err, results) => { 

 if (err) { 

 return connection.    rollback    (() => { 

 throw err; 

 }); 

 } 

 const query2 = 'INSERT INTO accounts SET ?'; 

 const account2 = { user\_id: 2, balance: 200 }; 

 connection.    query    (query2, account2, (err, results) => { 

 if (err) { 

 return connection.    rollback    (() => { 

 throw err; 

 }); 

 } 

 connection.    commit    ((err) => { 

 if (err) { 

 return connection.    rollback    (() => { 

 throw err; 

 }); 

 } 

 console.    log    ('Transaction Complete.'); 

 }); 

 }); 

 }); 

 }); 

 Indexing: 

 Indexes improve the speed of data retrieval operations on a database table.   They are particularly useful for columns that are frequently used in search conditions (    WHERE    clauses) or join conditions. 

 Creating an index on a column involves using the    CREATE INDEX    SQL statement.   Here’s an example of creating an index on the    username    column in the    users    table: 

 const query = 'CREATE INDEX idx\_username ON users(username)'; 

 connection.    query    (query, (err, results) => { 

 if (err) throw err; 

 console.    log    ('Index created:', results); 

 }); 

 ![image](d2d_images/image076.png)

 ![image](d2d_images/image090.png)

##  ​   PostgreSQL 

   P    OSTGRESQL, OFTEN REFERRED    to as Postgres, is a powerful, open-source object-relational database system.   Known for its robustness, scalability, and compliance with SQL standards, PostgreSQL is a popular choice for many developers and organizations.   This section will explore how to work with PostgreSQL in a Node.js environment, including setting up the database, establishing connections, performing CRUD operations, and understanding advanced features like transactions and indexing. 

####  Setting Up PostgreSQL 

   B    EFORE WORKING WITH    PostgreSQL in Node.js, you need to install and configure PostgreSQL on your system.   You can download PostgreSQL from the official website and follow the installation instructions for your operating system.   Once installed, you can start the PostgreSQL server and use the    psql    command-line tool or a graphical tool like pgAdmin to manage your databases. 

 ![image](d2d_images/image120.png)

####  Installing PostgreSQL Module for Node.js 

   T    O INTERACT WITH POSTGRESQL    from a Node.js application, you need to install the    pg    module.   This module provides methods to connect to a PostgreSQL database, execute queries, and manage connections. 

 npm install pg 

####  Establishing a Connection 

   E    STABLISHING A CONNECTION    to a PostgreSQL database involves creating a client object with the necessary configuration details such as host, user, password, and database name.   Here’s an example of how to establish a connection: 

 const { Client } =    require    ('pg'); 

 const client = new Client({ 

 host: 'localhost', 

 user: 'your\_username', 

 password: 'your\_password', 

 database: 'your\_database', 

 port: 5432, // Default port for PostgreSQL 

 }); 

 client.    connect    ((err) => { 

 if (err) { 

 console.    error    ('Error connecting to PostgreSQL:', err); 

 return; 

 } 

 console.    log    ('Connected to PostgreSQL'); 

 }); 

####  Performing CRUD Operations 

   C    RUD OPERATIONS (CREATE    , Read, Update, Delete) are fundamental operations for interacting with a database.   Let's look at how to perform these operations using the    pg    module in Node.js. 

 Creating (Inserting) Data: 

 To insert data into a table, you can use the    INSERT INTO    SQL statement.   Here’s an example of inserting a new user into a    users    table: 

 const user = { username: 'johndoe', password: 'securepassword' }; 

 const query = 'INSERT INTO users (username, password) VALUES ($1, $2) RETURNING id'; 

 client.    query    (query, \[user.username, user.password\], (err, res) => { 

 if (err) { 

 console.    error    ('Error inserting data:', err); 

 return; 

 } 

 console.    log    ('User added with ID:', res.rows\[0\].id); 

 }); 

 Reading (Selecting) Data: 

 To retrieve data from a table, you can use the    SELECT    SQL statement.   Here’s an example of selecting all users from the    users    table: 

 const query = 'SELECT \* FROM users'; 

 client.    query    (query, (err, res) => { 

 if (err) { 

 console.    error    ('Error reading data:', err); 

 return; 

 } 

 console.    log    ('User data:', res.rows); 

 }); 

 Updating Data: 

 To update existing data in a table, you can use the    UPDATE    SQL statement.   Here’s an example of updating a user’s password: 

 const userId = 1; 

 const newPassword = 'newsecurepassword'; 

 const query = 'UPDATE users SET password = $1 WHERE id = $2'; 

 client.    query    (query, \[newPassword, userId\], (err, res) => { 

 if (err) { 

 console.    error    ('Error updating data:', err); 

 return; 

 } 

 console.    log    ('Rows affected:', res.rowCount); 

 }); 

 Deleting Data: 

 To delete data from a table, you can use the    DELETE    SQL statement.   Here’s an example of deleting a user from the    users    table: 

 const userId = 1; 

 const query = 'DELETE FROM users WHERE id = $1'; 

 client.    query    (query, \[userId\], (err, res) => { 

 if (err) { 

 console.    error    ('Error deleting data:', err); 

 return; 

 } 

 console.    log    ('Rows deleted:', res.rowCount); 

 }); 

 –––––––– 

 ![image](d2d_images/scene_break.png) 

 ![image](d2d_images/image066.png)

####  Advanced Features: Transactions and Indexing 

   T    RANSACTIONS:  

 Transactions are a sequence of one or more SQL operations executed as a single unit.   They ensure data integrity and consistency, especially in cases where multiple operations depend on each other.   Transactions follow the ACID properties: Atomicity, Consistency, Isolation, and Durability. 

 To perform transactions in PostgreSQL with Node.js, you can use the    BEGIN    ,    COMMIT    , and    ROLLBACK    SQL statements.   Here’s an example of a transaction: 

 client.    query    ('BEGIN', (err) => { 

 if (err) { 

 console.error('Error starting transaction:', err); 

 return; 

 } 

 const query1 = 'INSERT INTO accounts (user\_id, balance) VALUES ($1, $2)'; 

 const account1 = \[1, 100\]; 

 client.    query    (query1, account1, (err, res) => { 

 if (err) { 

 return client.    query    ('ROLLBACK', (rollbackErr) => { 

 if (rollbackErr) { 

 console.    error    ('Error rolling back transaction:', rollbackErr); 

 } 

 console.    error    ('Error during transaction:', err); 

 }); 

 } 

 const query2 = 'INSERT INTO accounts (user\_id, balance) VALUES ($1, $2)'; 

 const account2 = \[2, 200\]; 

 client.    query    (query2, account2, (err, res) => { 

 if (err) { 

 return client.    query    ('ROLLBACK', (rollbackErr) => { 

 if (rollbackErr) { 

 console.    error    ('Error rolling back transaction:', rollbackErr); 

 } 

 console.    error    ('Error during transaction:', err); 

 }); 

 } 

 client.    query    ('COMMIT', (err) => { 

 if (err) { 

 console.    error    ('Error committing transaction:', err); 

 } else { 

 console.    log    ('Transaction complete.'); 

 } 

 }); 

 }); 

 }); 

 }); 

 Indexing: 

 Indexes improve the speed of data retrieval operations on a database table.   They are particularly useful for columns that are frequently used in search conditions (    WHERE    clauses) or join conditions. 

 Creating an index on a column involves using the    CREATE INDEX    SQL statement.   Here’s an example of creating an index on the    username    column in the    users    table: 

 const query = 'CREATE INDEX idx\_username ON users(username)'; 

 client.    query    (query, (err, res) => { 

 if (err) { 

 console.    error    ('Error creating index:', err); 

 return; 

 } 

 console.    log    ('Index created:', res); 

 }); 

 ![image](d2d_images/image117.png)

##  ​   MongoDB 

   M    ONGODB IS ONE OF THE    most popular NoSQL databases, known for its flexibility, scalability, and ease of use.   It stores data in JSON-like documents, which makes it a natural fit for applications that require a dynamic schema.   This section will explore how to work with MongoDB in a Node.js environment, including setting up the database, establishing connections, performing CRUD operations, and understanding advanced features like indexing and aggregation. 

 ![image](d2d_images/image224.png)

####  Setting Up MongoDB 

   B    EFORE WORKING WITH    MongoDB in Node.js, you need to install and configure MongoDB on your system.   You can download MongoDB from the official website and follow the installation instructions for your operating system.   Once installed, you can start the MongoDB server using the command line. 

  Starting MongoDB    : 

 mongod—dbpath /path/to/your/data 

####  Installing MongoDB Module for Node.js 

   T    O INTERACT WITH MONGODB    from a Node.js application, you need to install the    mongodb    module.   This module provides methods to connect to a MongoDB database, execute queries, and manage connections. 

 npm install mongodb 

####  Establishing a Connection 

   E    STABLISHING A CONNECTION    to a MongoDB database involves creating a client object with the necessary configuration details such as the connection URL and database name.   Here’s an example of how to establish a connection: 

 const { MongoClient } =    require    ('mongodb'); 

 const uri = 'mongodb://localhost:27017'; 

 const client = new MongoClient(uri, { useNewUrlParser: true, useUnifiedTopology: true }); 

 async function    run    () { 

 try { 

 await client.    connect    (); 

 console.    log    ('Connected to MongoDB'); 

 } catch (err) { 

 console.    error    ('Error connecting to MongoDB:', err); 

 } 

 } 

  run    (); 

 –––––––– 

 ![image](d2d_images/scene_break.png) 

####  Performing CRUD Operations 

   C    RUD OPERATIONS (CREATE    , Read, Update, Delete) are fundamental operations for interacting with a database.   Let's look at how to perform these operations using the    mongodb    module in Node.js. 

 Creating (Inserting) Data: 

 To insert data into a collection, you can use the    insertOne    or    insertMany    methods.   Here’s an example of inserting a new document into a    users    collection: 

 async function    createUser    () { 

 const database = client.    db    ('my\_database'); 

 const users = database.    collection    ('users'); 

 const user = { username: 'johndoe', password: 'securepassword' }; 

 const result = await users.    insertOne    (user); 

 console.    log    ('User added with ID:', result.insertedId); 

 } 

  createUser    (); 

 Reading (Finding) Data: 

 To retrieve data from a collection, you can use the    find    method.   Here’s an example of finding all documents in the    users    collection: 

 async function    getUsers    () { 

 const database = client.    db    ('my\_database'); 

 const users = database.    collection    ('users'); 

 const cursor = users.    find    ({}); 

 const allValues = await cursor.    toArray    (); 

 console.    log    ('User data:', allValues); 

 } 

  getUsers    (); 

 Updating Data: 

 To update existing data in a collection, you can use the    updateOne    or    updateMany    methods.   Here’s an example of updating a user’s password: 

 async function    updateUser    () { 

 const database = client.    db    ('my\_database'); 

 const users = database.    collection    ('users'); 

 const query = { username: 'johndoe' }; 

 const update = { $set: { password: 'newsecurepassword' } }; 

 const result = await users.    updateOne    (query, update); 

 console.    log    ('Matched documents:', result.matchedCount); 

 console.    log    ('Modified documents:', result.modifiedCount); 

 } 

  updateUser    (); 

 –––––––– 

 ![image](d2d_images/scene_break.png) 

   D    ELETING DATA:  

 To delete data from a collection, you can use the    deleteOne    or    deleteMany    methods.   Here’s an example of deleting a user from the    users    collection: 

 async function    deleteUser    () { 

 const database = client.    db    ('my\_database'); 

 const users = database.    collection    ('users'); 

 const query = { username: 'johndoe' }; 

 const result = await users.    deleteOne    (query); 

 console.    log    ('Deleted documents:', result.deletedCount); 

 } 

  deleteUser    (); 

####  Advanced Features: Indexing and Aggregation 

   I    NDEXING:  

 Indexes improve the speed of data retrieval operations on a collection.   They are particularly useful for fields that are frequently used in search conditions (    find    queries).   Creating an index on a field involves using the    createIndex    method.   Here’s an example of creating an index on the    username    field in the    users    collection: 

 async function    createIndex    () { 

 const database = client.    db    ('my\_database'); 

 const users = database.    collection    ('users'); 

 const result = await users.    createIndex    ({ username: 1 }); 

 console.    log    ('Index created:', result); 

 } 

  createIndex    (); 

 Aggregation: 

 Aggregation operations process data records and return computed results.   They are used to perform complex data transformations and calculations.   The    aggregate    method in MongoDB allows you to perform operations like grouping, sorting, and averaging.   Here’s an example of using the    aggregate    method to group users by their username and count the number of users: 

 async function    aggregateUsers    () { 

 const database = client.    db    ('my\_database'); 

 const users = database.    collection    ('users'); 

 const pipeline = \[ 

 { $group: { \_id: '$username', count: { $sum: 1 } } }, 

 { $sort: { count: -1 } } 

 \]; 

 const cursor = users.    aggregate    (pipeline); 

 const results = await cursor.    toArray    (); 

 console.    log    ('Aggregation results:', results); 

 } 

  aggregateUsers    (); 

 –––––––– 

 ![image](d2d_images/scene_break.png) 

 ![image](d2d_images/image143.png)

 ![image](d2d_images/image205.png)

##  ​   Redis 

   R    EDIS (REMOTE DICTIONARY    Server) is an open-source, in-memory data structure store that can be used as a database, cache, and message broker.   It supports various data structures such as strings, hashes, lists, sets, and sorted sets.   Redis is known for its high performance and flexibility, making it a popular choice for real-time applications, caching, and session management.   This section will explore how to work with Redis in a Node.js environment, including setting up the database, establishing connections, performing basic operations, and understanding advanced features like pub/sub and persistence. 

####  Setting Up Redis 

   B    EFORE WORKING WITH    Redis in Node.js, you need to install and configure Redis on your system.   You can download Redis from the official website and follow the installation instructions for your operating system.   Once installed, you can start the Redis server using the command line. 

 ![image](d2d_images/image113.png)

  Starting Redis    : 

 redis-server 

####  Installing Redis Module for Node.js 

   T    O INTERACT WITH REDIS    from a Node.js application, you need to install the    redis    module.   This module provides methods to connect to a Redis server, execute commands, and manage connections. 

 npm install redis 

####  Establishing a Connection 

   E    STABLISHING A CONNECTION    to a Redis server involves creating a client object with the necessary configuration details such as the host and port.   Here’s an example of how to establish a connection: 

 const redis =    require    ('redis'); 

 const client = redis.    createClient    ({ 

 host: 'localhost', 

 port: 6379 

 }); 

 client.    on    ('connect', () => { 

 console.    log    ('Connected to Redis'); 

 }); 

 client.    on    ('error', (err) => { 

 console.    error    ('Error connecting to Redis:', err); 

 }); 

 –––––––– 

 ![image](d2d_images/scene_break.png) 

####  Performing Basic Operations 

   R    EDIS SUPPORTS A WIDE    range of commands for various data structures.   Let's look at how to perform some basic operations using the    redis    module in Node.js. 

 Setting and Getting Values: 

 To set and get values in Redis, you can use the    set    and    get    commands.   Here’s an example of setting and getting a value: 

 // Set a value 

 client.    set    ('key', 'value', redis.print); 

 // Get a value 

 client.    get    ('key', (err, reply) => { 

 if (err) throw err; 

 console.    log    ('Value:', reply); 

 }); 

 –––––––– 

 ![image](d2d_images/scene_break.png) 

   W    ORKING WITH HASHES    : 

 Hashes in Redis are used to store sets of key-value pairs.   Here’s an example of setting and getting fields in a hash: 

 // Set fields in a hash 

 client.    hset    ('user:1000', 'username', 'johndoe', 'password', 'securepassword', redis.print); 

 // Get all fields in a hash 

 client.    hgetall    ('user:1000', (err, reply) => { 

 if (err) throw err; 

 console.    log    ('User:', reply); 

 }); 

 –––––––– 

 ![image](d2d_images/scene_break.png) 

   W    ORKING WITH LISTS    : 

 Lists in Redis are ordered collections of strings.   Here’s an example of pushing values to a list and retrieving them: 

 // Push values to a list 

 client.    rpush    ('tasks', 'task1', 'task2', 'task3', redis.print); 

 // Get all values from a list 

 client.    lrange    ('tasks', 0, -1, (err, reply) => { 

 if (err) throw err; 

 console.    log    ('Tasks:', reply); 

 }); 

 Working with Sets: 

 Sets in Redis are unordered collections of unique strings.   Here’s an example of adding values to a set and retrieving them: 

 // Add values to a set 

 client.    sadd    ('tags', 'nodejs', 'redis', 'database', redis.print); 

 // Get all values from a set 

 client.    smembers    ('tags', (err, reply) => { 

 if (err) throw err; 

 console.    log    ('Tags:', reply); 

 }); 

 –––––––– 

 ![image](d2d_images/scene_break.png) 

   P    UB/SUB:  

 Publish/Subscribe (Pub/Sub) messaging is a pattern where messages are published to channels and subscribers receive those messages.   Here’s an example of using Pub/Sub in Redis: 

 const subscriber = redis.    createClient    (); 

 const publisher = redis.    createClient    (); 

 // Subscribe to a channel 

 subscriber.    subscribe    ('notifications'); 

 // Listen for messages on the channel 

 subscriber.    on    ('message', (channel, message) => { 

 console.    log    (\`Received message from ${channel}: ${message}\`); 

 }); 

 // Publish a message to the channel 

 publisher.    publish    ('notifications', 'Hello, Redis!'); 

 ![image](d2d_images/image162.png)

 Persistence: 

 Redis provides different persistence options to ensure data durability.   The two main options are RDB (Redis Database Backup) and AOF (Append-Only File). 

*     RDB     : Creates point-in-time snapshots of the dataset at specified intervals.  
*     AOF     : Logs every write operation received by the server, which can be replayed to reconstruct the dataset.  

 To configure persistence, you need to update the Redis configuration file (    redis.conf    ). 

 ![image](d2d_images/image062.png)

##  ​   6.4.   Using ORMs (Sequelize) 

   O    BJECT-RELATIONAL MAPPING    (ORM) is a programming technique used to convert data between incompatible type systems in object-oriented programming languages.   Sequelize is a popular ORM for Node.js that provides a powerful and flexible interface for interacting with SQL databases like MySQL, PostgreSQL, SQLite, and Microsoft SQL Server.   This section will explore how to use Sequelize in a Node.js environment, including setting up the ORM, defining models, performing CRUD operations, and leveraging advanced features like associations and migrations. 

####  Setting Up Sequelize 

   B    EFORE USING SEQUELIZE    , you need to install it along with the database driver for your specific SQL database.   For this example, we will use PostgreSQL. 

 npm install sequelize pg pg-hstore 

 To establish a connection to your database, you need to create a Sequelize instance with the necessary configuration details such as database name, username, password, host, and dialect. 

 const { Sequelize } =    require    ('sequelize'); 

 const sequelize = new Sequelize('database', 'username', 'password', { 

 host: 'localhost', 

 dialect: 'postgres', // Change this to 'mysql' for MySQL, 'sqlite' for SQLite, etc. 

 logging: false, // Disable logging; default: console.log 

 }); 

 (async () => { 

 try { 

 await sequelize.    authenticate    (); 

 console.    log    ('Connection to the database has been established successfully.'); 

 } catch (error) { 

 console.    error    ('Unable to connect to the database:', error); 

 } 

 })(); 

####  Defining Models 

   M    ODELS IN SEQUELIZE    represent tables in your database.   You define a model by extending the    Model    class and defining its attributes.   Here’s an example of defining a    User    model: 

 const { DataTypes, Model } =    require    ('sequelize'); 

 class User extends Model {} 

 User.    init    ( 

 { 

 username: { 

 type: DataTypes.STRING, 

 allowNull: false, 

 }, 

 password: { 

 type: DataTypes.STRING, 

 allowNull: false, 

 }, 

 }, 

 { 

 sequelize, // Pass the Sequelize instance 

 modelName: 'User', // Name of the model 

 tableName: 'users', // Optional: Table name in the database 

 timestamps: true, // Automatically adds createdAt and updatedAt fields 

 } 

 ); 

 (async () => { 

 await sequelize.    sync    (); // Sync all defined models to the database 

 })(); 

####  Performing CRUD Operations 

   S    EQUELIZE PROVIDES    a simple and consistent API for performing CRUD operations.   Here’s how to create, read, update, and delete records using Sequelize. 

 Creating (Inserting) Data: 

 To create a new record in the database, use the    create    method: 

 (async () => { 

 const user = await User.    create    ({ username: 'johndoe', password: 'securepassword' }); 

 console.    log    ('User created:', user.    toJSON    ()); 

 })(); 

 Reading (Selecting) Data: 

 To retrieve data from the database, use the    findAll    or    findOne    methods: 

 (async () => { 

 const users = await User.    findAll    (); 

 console.    log    ('All users:', users.    map    (user => user.    toJSON    ())); 

 const user = await User.    findOne    ({ where: { username: 'johndoe' } }); 

 console.    log    ('Single user:', user.    toJSON    ()); 

 })(); 

 Updating Data: 

 To update an existing record, use the    update    method: 

 (async () => { 

 const \[updated\] = await User.    update    ({ password: 'newsecurepassword' }, { 

 where: { username: 'johndoe' } 

 }); 

 console.    log    ('Number of users updated:', updated); 

 })(); 

 Deleting Data: 

 To delete a record, use the    destroy    method: 

 (async () => { 

 const deleted = await User.    destroy    ({ 

 where: { username: 'johndoe' } 

 }); 

 console.    log    ('Number of users deleted:', deleted); 

 })(); 

 Associations: 

 Sequelize supports various types of associations between models, such as    hasOne    ,    belongsTo    ,    hasMany    , and    belongsToMany    .   Here’s an example of defining associations between    User    and    Post    models: 

 class Post extends Model {} 

 Post.    init    ( 

 { 

 title: { 

 type: DataTypes.STRING, 

 allowNull: false, 

 }, 

 content: { 

 type: DataTypes.TEXT, 

 allowNull: false, 

 }, 

 }, 

 { 

 sequelize, 

 modelName: 'Post', 

 tableName: 'posts', 

 timestamps: true, 

 } 

 ); 

 User.    hasMany    (Post, { foreignKey: 'userId' }); 

 Post.    belongsTo    (User, { foreignKey: 'userId' }); 

 (async () => { 

 await sequelize.    sync    ({ force: true }); // Recreate tables 

 })(); 

 Migrations: 

 Migrations allow you to version-control your database schema changes.   Sequelize provides a CLI tool to manage migrations.   First, install the Sequelize CLI: 

 npm install—save-dev sequelize-cli 

 Create a configuration file    sequelize.config.js    : 

 module.exports = { 

 development: { 

 username: 'username', 

 password: 'password', 

 database: 'database', 

 host: '127.0.0.1', 

 dialect: 'postgres', 

 }, 

 }; 

 Initialize Sequelize CLI: 

 npx sequelize-cli init 

 This will create the necessary folders:    config    ,    migrations    ,    models    , and    seeders    . 

 Create a migration file: 

 npx sequelize-cli migration:generate—name create-users-table 

 Edit the generated migration file to define the schema changes: 

 'use strict'; 

 module.exports = { 

  up    : async (queryInterface, Sequelize) => { 

 await queryInterface.    createTable    ('users', { 

 id: { 

 allowNull: false, 

 autoIncrement: true, 

 primaryKey: true, 

 type: Sequelize.INTEGER, 

 }, 

 username: { 

 type: Sequelize.STRING, 

 }, 

 password: { 

 type: Sequelize.STRING, 

 }, 

 createdAt: { 

 allowNull: false, 

 type: Sequelize.DATE, 

 }, 

 updatedAt: { 

 allowNull: false, 

 type: Sequelize.DATE, 

 }, 

 }); 

 }, 

  down    : async (queryInterface, Sequelize) => { 

 await queryInterface.    dropTable    ('users'); 

 }, 

 }; 

 Run the migration: 

 npx sequelize-cli db:migrate 

 ![image](d2d_images/image177.png)

 ![image](d2d_images/image218.png)

##  ​   Using ORMs (Mongoose) 

   M    ONGOOSE IS A POPULAR    Object Data Modeling (ODM) library for MongoDB and Node.js.   It provides a straightforward and schema-based solution to model your application data, offering built-in type casting, validation, query building, and business logic hooks.   This section will explore how to use Mongoose in a Node.js environment, including setting up the ODM, defining schemas, performing CRUD operations, and leveraging advanced features like middleware and virtuals. 

####  Setting Up Mongoose 

   B    EFORE USING MONGOOSE    , you need to install it along with the MongoDB Node.js driver. 

 npm install mongoose 

 To establish a connection to your MongoDB database, you need to create a connection using Mongoose.   Here’s an example of how to establish a connection: 

 const mongoose =    require    ('mongoose'); 

 const uri = 'mongodb://localhost:27017/my\_database'; 

 mongoose.    connect    (uri, { 

 useNewUrlParser: true, 

 useUnifiedTopology: true 

 }); 

 const db = mongoose.connection; 

 db.    on    ('error', console.    error    .    bind    (console, 'connection error:')); 

 db.    once    ('open', () => { 

 console.    log    ('Connected to MongoDB'); 

 }); 

 –––––––– 

 ![image](d2d_images/scene_break.png) 

####  Defining Schemas and Models 

   S    CHEMAS IN MONGOOSE    define the structure of the documents within a collection.   Once a schema is defined, you can create a model based on that schema.   Here’s an example of defining a    User    schema and model: 

 const { Schema, model } = mongoose; 

 const userSchema = new Schema({ 

 username: { 

 type: String, 

 required: true, 

 unique: true 

 }, 

 password: { 

 type: String, 

 required: true 

 }, 

 email: { 

 type: String, 

 required: true, 

 unique: true 

 }, 

 createdAt: { 

 type: Date, 

  default    : Date.    now  

 } 

 }); 

 const User =    model    ('User', userSchema); 

 –––––––– 

 ![image](d2d_images/scene_break.png) 

####  Performing CRUD Operations 

   M    ONGOOSE PROVIDES A    simple and consistent API for performing CRUD operations.   Here’s how to create, read, update, and delete records using Mongoose. 

 Creating (Inserting) Data: 

 To create a new record in the database, use the    save    method: 

 const newUser = new User({ 

 username: 'johndoe', 

 password: 'securepassword', 

 email: 'johndoe@example.com' 

 }); 

 newUser.    save    ((err) => { 

 if (err) return console.    error    (err); 

 console.    log    ('User created:', newUser); 

 }); 

 Reading (Finding) Data: 

 To retrieve data from the database, use the    find    method: 

 User.    find    ({}, (err, users) => { 

 if (err) return console.    error    (err); 

 console.    log    ('All users:', users); 

 }); 

 User.    findOne    ({ username: 'johndoe' }, (err, user) => { 

 if (err) return console.    error    (err); 

 console.    log    ('Single user:', user); 

 }); 

 Updating Data: 

 To update an existing record, use the    updateOne    or    findByIdAndUpdate    methods: 

 User.    updateOne    ({ username: 'johndoe' }, { password: 'newsecurepassword' }, (err, res) => { 

 if (err) return console.    error    (err); 

 console.    log    ('User updated:', res); 

 }); 

 User.    findByIdAndUpdate    ('user\_id', { email: 'newemail@example.com' }, (err, user) => { 

 if (err) return console.    error    (err); 

 console.    log    ('Updated user:', user); 

 }); 

 Deleting Data: 

 To delete a record, use the    deleteOne    or    findByIdAndDelete    methods: 

 User.    deleteOne    ({ username: 'johndoe' }, (err) => { 

 if (err) return console.    error    (err); 

 console.    log    ('User deleted'); 

 }); 

 User.    findByIdAndDelete    ('user\_id', (err) => { 

 if (err) return console.    error    (err); 

 console.    log    ('User deleted'); 

 }); 

####  Advanced Features: Middleware and Virtuals 

   M    IDDLEWARE:  

 Middleware in Mongoose is similar to middleware in Express.   It allows you to define pre- and post-hooks for various model methods.   Here’s an example of a pre-save middleware that hashes a user’s password before saving it: 

 const bcrypt =    require    ('bcrypt'); 

 userSchema.    pre    ('save', function(next) { 

 const user = this; 

 if (!user.    isModified    ('password')) return    next    (); 

 bcrypt.    hash    (user.password, 10, (err, hash) => { 

 if (err) return    next    (err); 

 user.password = hash; 

  next    (); 

 }); 

 }); 

 Virtuals: 

 Virtuals are document properties that you can get and set but that do not get persisted to MongoDB.   They are typically used for computed properties.   Here’s an example of adding a virtual property for the user’s full name: 

 userSchema.    virtual    ('fullName').    get    (function() { 

 return \`${this.firstName} ${this.lastName}\`; 

 }); 

 const User =    model    ('User', userSchema); 

 const user = new User({ 

 firstName: 'John', 

 lastName: 'Doe' 

 }); 

 console.    log    (user.fullName); // Output: John Doe 

 –––––––– 

 ![image](d2d_images/scene_break.png) 

 ![image](d2d_images/image152.png)

 ![image](d2d_images/image040.png)

##  ​   6.5.   Database Connection Pooling 

   D    ATABASE CONNECTION    pooling is a technique used to maintain a cache of database connections so that they can be reused, improving the performance and scalability of applications.   By reusing existing connections rather than creating new ones for each database request, connection pooling reduces the overhead associated with establishing database connections.   This section will explore how to implement database connection pooling in Node.js using popular libraries for MySQL, PostgreSQL, and MongoDB. 

 ![image](d2d_images/image073.png)

####  Why Use Connection Pooling? 

1.    Performance    : Establishing a new database connection can be time-consuming and resource-intensive.   Connection pooling allows for faster query execution by reusing existing connections. 
2.    Resource Management    : Databases have a limit on the number of concurrent connections they can handle.   Connection pooling helps manage these connections efficiently. 
3.    Scalability    : Connection pooling enables applications to handle more simultaneous database requests by efficiently managing a pool of reusable connections. 

####  Implementing Connection Pooling in MySQL 

   T    O IMPLEMENT CONNECTION    pooling in MySQL, you can use the    mysql    or    mysql2    module.   Here’s how to do it with the    mysql2    module: 

  Install the mysql2 Module    : 

 npm install mysql2 

  Create a Connection Pool    : 

 const mysql =    require    ('mysql2'); 

 const pool = mysql.    createPool    ({ 

 host: 'localhost', 

 user: 'root', 

 password: 'password', 

 database: 'my\_database', 

 waitForConnections: true, 

 connectionLimit: 10, 

 queueLimit: 0 

 }); 

 // Use the pool to perform queries 

 pool.    query    ('SELECT \* FROM users', (err, results) => { 

 if (err) throw err; 

 console.    log    (results); 

 }); 

 // Close the pool 

 pool.    end    ((err) => { 

 if (err) throw err; 

 console.    log    ('Pool closed'); 

 }); 

####  Implementing Connection Pooling in PostgreSQL 

   T    O IMPLEMENT CONNECTION    pooling in PostgreSQL, you can use the    pg    module.   Here’s how to do it: 

  Install the pg Module    : 

 npm install pg 

  Create a Connection Pool    : 

 const { Pool } =    require    ('pg'); 

 const pool = new Pool({ 

 user: 'your\_username', 

 host: 'localhost', 

 database: 'your\_database', 

 password: 'your\_password', 

 port: 5432, 

 max: 10, // Maximum number of connections 

 idleTimeoutMillis: 30000, // Close idle clients after 30 seconds 

 connectionTimeoutMillis: 2000, // Return an error after 2 seconds if connection could not be established 

 }); 

 // Use the pool to perform queries 

 pool.    query    ('SELECT \* FROM users', (err, res) => { 

 if (err) throw err; 

 console.    log    (res.rows); 

 }); 

 // Close the pool 

 pool.    end    ((err) => { 

 if (err) throw err; 

 console.    log    ('Pool closed'); 

 }); 

 –––––––– 

 ![image](d2d_images/scene_break.png) 

####  Implementing Connection Pooling in MongoDB 

   T    O IMPLEMENT CONNECTION    pooling in MongoDB, you can use the    mongodb    module.   Here’s how to do it: 

  Install the mongodb Module    : 

 npm install mongodb 

  Create a Connection Pool    : 

 const { MongoClient } =    require    ('mongodb'); 

 const uri = 'mongodb://localhost:27017'; 

 const client = new MongoClient(uri, { 

 useNewUrlParser: true, 

 useUnifiedTopology: true, 

 poolSize: 10, // Maximum number of connections in the pool 

 }); 

 async function    run    () { 

 try { 

 await client.    connect    (); 

 console.    log    ('Connected to MongoDB'); 

 const database = client.    db    ('my\_database'); 

 const users = database.    collection    ('users'); 

 // Use the connection pool to perform queries 

 const results = await users.    find    ({}).    toArray    (); 

 console.    log    (results); 

 } catch (err) { 

 console.    error    ('Error connecting to MongoDB:', err); 

 } finally { 

 // Close the pool 

 await client.    close    (); 

 console.    log    ('Pool closed'); 

 } 

 } 

  run    (); 

 ![image](d2d_images/image100.png)

 ![image](d2d_images/image095.png)

##  ​   6.6.   Practical Examples: Building a RESTful API with Database Integration 

   B    UILDING A RESTFUL    API with database integration is a common task in modern web development.   In this section, we will create a simple RESTful API using Node.js, Express, and Sequelize for database integration with PostgreSQL.   This API will handle basic CRUD operations for a    User    model. 

####  Setting Up the Project 

    I    NITIALIZE THE PROJECT     : 

 Create a new directory for your project and initialize it with    npm    : 

 mkdir restful-api 

 cd restful-api 

 npm init -y 

  nstall Dependencies    : 

 Install the required dependencies: 

 npm install express sequelize pg pg-hstore body-parser 

  Project Structure    : 

 Create the following directory structure: 

 restful-api/ 

 ├── config/ 

 │  └── database.js 

 ├── models/ 

 │  └── user.js 

 ├── routes/ 

 │  └── users.js 

 ├── app.js 

 └── package.json 

####  Configuring the Database 

    D    ATABASE CONFIGURATION     : 

 Create a    config/database.js    file to configure the Sequelize instance: 

 const { Sequelize } =    require    ('sequelize'); 

 const sequelize = new Sequelize('my\_database', 'your\_username', 'your\_password', { 

 host: 'localhost', 

 dialect: 'postgres', 

 logging: false, 

 }); 

 module.exports = sequelize; 

  Defining the User Model    : 

 Create a    models/user.js    file to define the    User    model: 

 const { DataTypes } =    require    ('sequelize'); 

 const sequelize =    require    ('../config/database'); 

 const User = sequelize.    define    ('User', { 

 username: { 

 type: DataTypes.STRING, 

 allowNull: false, 

 unique: true, 

 }, 

 password: { 

 type: DataTypes.STRING, 

 allowNull: false, 

 }, 

 email: { 

 type: DataTypes.STRING, 

 allowNull: false, 

 unique: true, 

 }, 

 }); 

 module.exports = User; 

####  Setting Up Express and Routes 

    C    REATING THE EXPRESS    App    : 

 Create an    app.js    file to set up the Express application: 

 const    express    =    require    ('express'); 

 const bodyParser =    require    ('body-parser'); 

 const sequelize =    require    ('./config/database'); 

 const User =    require    ('./models/user'); 

 const userRoutes =    require    ('./routes/users'); 

 const app =    express    (); 

 // Middleware 

 app.    use    (bodyParser.    json    ()); 

 // Routes 

 app.    use    ('/api/users', userRoutes); 

 // Sync database and start server 

 sequelize.    sync    () 

 .    then    (() => { 

 app.    listen    (3000, () => { 

 console.    log    ('Server is running on port 3000'); 

 }); 

 }) 

 .    catch    (err => { 

 console.    error    ('Unable to connect to the database:', err); 

 }); 

  Creating the Routes    : 

 Create a    routes/users.js    file to define the routes for user operations: 

 const express =    require    ('express'); 

 const User =    require    ('../models/user'); 

 const router = express.    Router    (); 

 // Get all users 

 router.    get    ('/', async (req, res) => { 

 try { 

 const users = await User.    findAll    (); 

 res.    json    (users); 

 } catch (err) { 

 res.    status    (500).    json    ({ error: err.message }); 

 } 

 }); 

 // Get a user by ID 

 router.    get    ('/:id', async (req, res) => { 

 try { 

 const user = await User.    findByPk    (req.params.id); 

 if (user) { 

 res.    json    (user); 

 } else { 

 res.    status    (404).    json    ({ error: 'User not found' }); 

 } 

 } catch (err) { 

 res.    status    (500).    json    ({ error: err.message }); 

 } 

 }); 

 // Create a new user 

 router.    post    ('/', async (req, res) => { 

 try { 

 const user = await User.    create    (req.body); 

 res.    status    (201).    json    (user); 

 } catch (err) { 

 res.    status    (400).    json    ({ error: err.message }); 

 } 

 }); 

 // Update a user 

 router.    put    ('/:id', async (req, res) => { 

 try { 

 const user = await User.    findByPk    (req.params.id); 

 if (user) { 

 await user.    update    (req.body); 

 res.    json    (user); 

 } else { 

 res.    status    (404).    json    ({ error: 'User not found' }); 

 } 

 } catch (err) { 

 res.    status    (400).    json    ({ error: err.message }); 

 } 

 }); 

 // Delete a user 

 router.    delete    ('/:id', async (req, res) => { 

 try { 

 const user = await User.    findByPk    (req.params.id); 

 if (user) { 

 await user.    destroy    (); 

 res.    status    (204).    json    (); 

 } else { 

 res.    status    (404).    json    ({ error: 'User not found' }); 

 } 

 } catch (err) { 

 res.    status    (500).    json    ({ error: err.message }); 

 } 

 }); 

 module.exports = router; 

 ![image](d2d_images/image141.png)

####  Running the API 

   T    O RUN THE API, EXECUTE    the following command: 

 node app.js 

 Your RESTful API is now running on    http://localhost:3000    .   You can use tools like Postman or cURL to test the endpoints. 

####  Testing the Endpoints 

1.    Get all users    : 

   G    ET   [ http://localhost:3000/api/users ](http://localhost:3000/api/users)

  Get a user by ID    : 

 GET  [ http://localhost:3000/api/users/1 ](http://localhost:3000/api/users/1)

  Create a new user    : 

 POST  [ http://localhost:3000/api/users ](http://localhost:3000/api/users)

 Content-Type: application/json 

 { 

 "username": "johndoe", 

 "password": "securepassword", 

 "email": "johndoe@example.com" 

 } 

  Update a user    : 

 PUT  [ http://localhost:3000/api/users/1 ](http://localhost:3000/api/users/1)

 Content-Type: application/json 

 { 

 "email": "newemail@example.com" 

 } 

  Delete a user    : 

 DELETE  [ http://localhost:3000/api/users/1 ](http://localhost:3000/api/users/1)

 ![image](d2d_images/image044.png)

 ![image](d2d_images/image111.png)

 
|  ![image](d2d_images/chapter_title_corner_decoration_left.png)  ||  ||  ![image](d2d_images/chapter_title_corner_decoration_right.png)  |
| --- | --- | --- |

 ![image](d2d_images/chapter_title_above.png) 

#  ​   ![image](d2d_images/image147.png)  7.   Advanced JavaScript and Node.js Patterns 

 ![image](d2d_images/chapter_title_below.png) 

##  ​   7.1.   Promises and Async/Await 

   A    s you delve deeper    into advanced JavaScript, understanding promises is crucial.   Promises represent one of the core concepts for handling asynchronous operations.   They provide a more robust and cleaner way to manage tasks that take time to complete, such as fetching data from an API, reading files, or interacting with databases. 

 A promise is an object that represents the eventual completion (or failure) of an asynchronous operation and its resulting value.   When you create a promise, it can be in one of three states: 

*     Pending     : The initial state, neither fulfilled nor rejected.  
*     Fulfilled     : The operation completed successfully.  
*     Rejected     : The operation failed.  

 Creating and Using a Promise: 

 Let's start by creating a simple promise.   Imagine you want to simulate a task that might succeed or fail based on some condition. 

 const myPromise = new Promise((    resolve    ,    reject    ) => { 

 let condition = true; // Simulate an asynchronous operation 

 if (condition) { 

  resolve    ("Operation successful!"); 

 } else { 

  reject    ("Operation failed!"); 

 } 

 }); 

 // Handling the promise 

 myPromise 

 .    then    (result => { 

 console.    log    (result); 

 }) 

 .    catch    (error => { 

 console.    error    (error); 

 }); 

 –––––––– 

 ![image](d2d_images/scene_break.png) 

 ![image](d2d_images/image022.png)

   I    N THIS EXAMPLE, WE    create a new promise that takes a function with two parameters:    resolve    and    reject    .   These are functions that JavaScript provides to handle the outcome of the promise.   If the condition is met, we call    resolve    with a success message; otherwise, we call    reject    with an error message. 

 The    .then()    method is used to define what happens when the promise is fulfilled, while    .catch()    handles any errors if the promise is rejected. 

 ![image](d2d_images/image196.png)

####  Advanced Promise Usage 

   A    S YOU ADVANCE, YOU    will often need to handle multiple asynchronous operations.   This is where promises really shine, allowing you to chain operations and manage them efficiently. 

 Chaining Promises: 

 const fetchData = new Promise((    resolve    ,    reject    ) => { 

  setTimeout    (() =>    resolve    ("Data fetched"), 1000); 

 }); 

 const    processData    = data => { 

 return new Promise((    resolve    ,    reject    ) => { 

  setTimeout    (() =>    resolve    (\`${data} and processed\`), 1000); 

 }); 

 }; 

 fetchData 

 .    then    (data => { 

 console.    log    (data); // Output: Data fetched 

 return    processData    (data); 

 }) 

 .    then    (processedData => { 

 console.    log    (processedData); // Output: Data fetched and processed 

 }) 

 .    catch    (error => { 

 console.    error    (error); 

 }); 

 –––––––– 

 ![image](d2d_images/scene_break.png) 

 ![image](d2d_images/image126.png)

   H    ERE, WE CHAIN TWO    promises:    fetchData    and    processData    .   The second promise starts only after the first one fulfills, ensuring a sequential execution of asynchronous tasks. 

 Promise.all for Concurrent Execution: 

 Sometimes, you need to run multiple promises concurrently and wait for all of them to complete.    Promise.all    is perfect for this scenario. 

 const promise1 = new Promise((    resolve    ,    reject    ) =>    setTimeout    (    resolve    , 1000, 'First')); 

 const promise2 = new Promise((    resolve    ,    reject    ) =>    setTimeout    (    resolve    , 2000, 'Second')); 

 const promise3 = new Promise((    resolve    ,    reject    ) =>    setTimeout    (    resolve    , 3000, 'Third')); 

 Promise.    all    (\[promise1, promise2, promise3\]) 

 .    then    (results => { 

 console.    log    (results); // Output: \['First', 'Second', 'Third'\] 

 }) 

 .    catch    (error => { 

 console.    error    (error); 

 }); 

 –––––––– 

 ![image](d2d_images/scene_break.png) 

 ![image](d2d_images/image106.png)

    P    ROMISE.ALL     takes an array of promises and returns a single promise that resolves when all the promises in the array have resolved.   It rejects if any of the promises reject. 

####  Introduction to Async/Await 

   A    SYNC/AWAIT IS SYNTACTIC    sugar built on top of promises, introduced in ES2017 (ES8).   It makes asynchronous code look and behave more like synchronous code, improving readability and maintainability. 

 Creating an Async Function: 

 An    async    function returns a promise.   Inside this function, you can use the    await    keyword to wait for a promise to resolve or reject. 

 async function    fetchData    () { 

 try { 

 let response = await    fetch    ('https://api.example.com/data'); 

 let data = await response.    json    (); 

 console.    log    (data); 

 } catch (error) { 

 console.    error    ('Error fetching data:', error); 

 } 

 } 

  fetchData    (); 

 In this example, the    fetchData    function is declared with the    async    keyword.   Inside,    await    pauses the execution until the promise from    fetch    resolves.   If the promise rejects, the error is caught in the    catch    block. 

 Handling Multiple Async Operations: 

 Just like with    Promise.all    , you can handle multiple async operations concurrently using    await    inside an    async    function. 

 async function    fetchMultipleData    () { 

 try { 

 let \[response1, response2\] = await Promise.    all    (\[ 

  fetch    ('https://api.example.com/data1'), 

  fetch    ('https://api.example.com/data2') 

 \]); 

 let data1 = await response1.    json    (); 

 let data2 = await response2.    json    (); 

 console.    log    ('Data 1:', data1); 

 console.    log    ('Data 2:', data2); 

 } catch (error) { 

 console.    error    ('Error fetching data:', error); 

 } 

 } 

  fetchMultipleData    (); 

 In this example,    Promise.all    is used to fetch two data sources concurrently.   The results are then processed using    await    for cleaner and more readable code. 

####  Error Handling with Async/Await 

   H    ANDLING ERRORS IN    async/await is straightforward and resembles traditional    try/catch    in synchronous code. 

 async function    fetchDataWithErrorHandling    () { 

 try { 

 let response = await    fetch    ('https://api.example.com/data'); 

 if (!response.ok) { 

 throw new Error('Network response was not ok'); 

 } 

 let data = await response.    json    (); 

 console.    log    (data); 

 } catch (error) { 

 console.    error    ('Error fetching data:', error); 

 } 

 } 

  fetchDataWithErrorHandling    (); 

 In this function,    try/catch    blocks are used to handle any errors that occur during the fetch operation, making it easier to debug and maintain the code. 

 ![image](d2d_images/image182.png)

 ![image](d2d_images/image110.png)

##  ​   7.2.   Error Handling Strategies 

   A    S YOU ADVANCE IN YOUR    JavaScript and Node.js journey, mastering error handling is crucial.   Proper error handling ensures your applications are robust, reliable, and user-friendly.   It prevents your application from crashing unexpectedly and helps you identify and fix issues efficiently. 

####  Types of Errors 

1.    Synchronous Errors    : These occur during the execution of the code.   They are usually easy to catch and handle. 
2.    Asynchronous Errors    : These occur during asynchronous operations like network requests, file system operations, or timers.   Handling these requires different strategies. 

####  Basic Error Handling in JavaScript 

   T    RY/CATCH BLOCKS  

 The    try/catch    block is the most common way to handle synchronous errors in JavaScript. 

 try { 

 // Code that might throw an error 

 let result =    riskyOperation    (); 

 console.    log    (result); 

 } catch (error) { 

 console.    error    ('Error occurred:', error); 

 } 

 In this example, if    riskyOperation()    throws an error, the    catch    block will handle it, preventing the application from crashing. 

 ![image](d2d_images/image222.png)

####  Handling Errors in Promises 

   P    ROMISES PROVIDE A    cleaner way to handle asynchronous operations, but they come with their own error-handling mechanisms. 

 Using .catch() 

 When working with promises, errors can be caught using the    .catch()    method. 

 const myPromise = new Promise((    resolve    ,    reject    ) => { 

 let condition = false; 

 if (condition) { 

  resolve    ("Success!"); 

 } else { 

  reject    ("Error: Condition was false"); 

 } 

 }); 

 myPromise 

 .    then    (result => { 

 console.    log    (result); 

 }) 

 .    catch    (error => { 

 console.    error    (error); 

 }); 

 In this example, if the promise is rejected, the error message is caught and logged by the    .catch()    method. 

 Handling Multiple Promises 

 When dealing with multiple promises,    Promise.all    can be used.   If any promise is rejected, the entire operation is considered rejected. 

 const promise1 = new Promise((    resolve    ,    reject    ) =>    setTimeout    (    resolve    , 1000, 'First')); 

 const promise2 = new Promise((    resolve    ,    reject    ) =>    setTimeout    (    reject    , 2000, 'Second failed')); 

 const promise3 = new Promise((    resolve    ,    reject    ) =>    setTimeout    (    resolve    , 3000, 'Third')); 

 Promise.    all    (\[promise1, promise2, promise3\]) 

 .    then    (results => { 

 console.    log    (results); 

 }) 

 .    catch    (error => { 

 console.    error    ('One of the promises failed:', error); 

 }); 

 Here,    promise2    is rejected, so the    .catch()    block will handle the error, and the operation will not log the results of the other promises. 

####  Handling Errors with Async/Await 

   A    SYNC/AWAIT, INTRODUCED    in ES2017, simplifies working with promises and provides a synchronous-like way to handle asynchronous code.   It also integrates well with    try/catch    for error handling. 

 Using Try/Catch with Async/Await 

 async function    fetchData    () { 

 try { 

 let response = await    fetch    ('https://api.example.com/data'); 

 let data = await response.    json    (); 

 console.    log    (data); 

 } catch (error) { 

 console.    error    ('Error fetching data:', error); 

 } 

 } 

  fetchData    (); 

 In this example, any errors occurring during the fetch operation or while parsing the JSON response are caught and handled in the    catch    block. 

 Handling Multiple Async Operations 

 Using    Promise.all    with    async/await    allows you to handle multiple asynchronous operations concurrently and catch errors effectively. 

 async function    fetchMultipleData    () { 

 try { 

 let \[response1, response2\] = await Promise.    all    (\[ 

  fetch    ('https://api.example.com/data1'), 

  fetch    ('https://api.example.com/data2') 

 \]); 

 let data1 = await response1.    json    (); 

 let data2 = await response2.    json    (); 

 console.    log    ('Data 1:', data1); 

 console.    log    ('Data 2:', data2); 

 } catch (error) { 

 console.    error    ('Error fetching data:', error); 

 } 

 } 

  fetchMultipleData    (); 

####  Centralized Error Handling in Node.js 

   F    OR LARGER APPLICATIONS    , having a centralized error-handling mechanism can simplify error management and improve code maintainability. 

 Error Handling Middleware 

 In an Express application, you can create an error-handling middleware function. 

 const    express    =    require    ('express'); 

 const app =    express    (); 

 // Error handling middleware 

 app.    use    ((err, req, res, next) => { 

 console.    error    (err.stack); 

 res.    status    (500).    send    ('Something broke!'); 

 }); 

 // Simulate an error 

 app.    get    ('/', (req, res) => { 

 throw new Error('Simulated error'); 

 }); 

 const PORT = 3000; 

 app.    listen    (PORT, () => { 

 console.    log    (\`Server running on port ${PORT}\`); 

 }); 

 In this example, any error thrown in the route handlers will be passed to the error-handling middleware, which logs the error and sends a response to the client. 

 ![image](d2d_images/image027.png)

####  Creating Custom Error Classes 

   C    REATING CUSTOM ERROR    classes can provide more context and control over error handling. 

 class CustomError extends Error { 

  constructor    (message, statusCode) { 

  super    (message); 

 this.statusCode = statusCode; 

 } 

 } 

 function    riskyOperation    () { 

 throw new CustomError('Operation failed!', 400); 

 } 

 try { 

  riskyOperation    (); 

 } catch (error) { 

 if (error instanceof CustomError) { 

 console.    error    (\`Custom error occurred: ${error.message} (Status Code: ${error.statusCode})\`); 

 } else { 

 console.    error    ('An unexpected error occurred:', error); 

 } 

 } 

 In this example, the    CustomError    class extends the built-in    Error    class, adding a    statusCode    property.   This allows for more granular error handling based on the type of error. 

 ![image](d2d_images/image086.png)

##  ​   7.3.   Event Emitters 

   A    S YOU CONTINUE TO    dive deeper into Node.js, one of the core concepts you will encounter is the event-driven architecture.   This approach is a fundamental part of how Node.js handles asynchronous operations and scales efficiently.   At the heart of this architecture is the EventEmitter class.   Understanding how to use event emitters effectively can greatly enhance your ability to build responsive, scalable applications. 

####  What Are Event Emitters? 

   E    VENT EMITTERS ARE    objects that can emit named events and register listeners for those events.   When an event is emitted, all the listeners registered for that event are called synchronously.   This mechanism is central to many parts of Node.js, from the core modules to custom modules that you create. 

 Imagine you're at a concert.   The band on stage (the emitter) plays music (emits an event), and the audience (listeners) reacts by clapping, singing along, or dancing.   This analogy illustrates the basic principle of event emitters: the band plays, and the audience responds. 

####  Creating and Using Event Emitters 

   L    ET'S START WITH A    simple example to see how event emitters work.   We'll use the EventEmitter class from the events module to create an emitter and attach some listeners to it. 

 Basic Example: 

 const EventEmitter =    require    ('events'); 

 class MyEmitter extends EventEmitter {} 

 const myEmitter = new MyEmitter(); 

 // Register a listener for the 'greet' event 

 myEmitter.    on    ('greet', () => { 

 console.    log    ('Hello!   The greet event was emitted.'); 

 }); 

 // Emit the 'greet' event 

 myEmitter.    emit    ('greet'); 

 ![image](d2d_images/image164.png)

 In this example, we first import the EventEmitter class and create a new class that extends EventEmitter.   We then create an instance of this class, register a listener for the 'greet' event using the    on    method, and finally, emit the 'greet' event using the    emit    method.   When the event is emitted, the registered listener is called, and we see the message in the console. 

 ![image](d2d_images/image080.png)

####  Handling Multiple Events 

   A    N EMITTER CAN HAVE    multiple events and listeners.   Each listener can be specific to an event, making it a powerful tool for managing complex behaviors. 

 Example: 

 const EventEmitter =    require    ('events'); 

 class MyEmitter extends EventEmitter {} 

 const myEmitter = new MyEmitter(); 

 // Register multiple listeners for different events 

 myEmitter.    on    ('start', () => { 

 console.    log    ('Starting...'); 

 }); 

 myEmitter.    on    ('progress', (percent) => { 

 console.    log    (\`Progress: ${percent}%\`); 

 }); 

 myEmitter.    on    ('finish', () => { 

 console.    log    ('Finished!'); 

 }); 

 // Emit events 

 myEmitter.    emit    ('start'); 

 myEmitter.    emit    ('progress', 50); 

 myEmitter.    emit    ('progress', 75); 

 myEmitter.    emit    ('finish'); 

 –––––––– 

 ![image](d2d_images/scene_break.png) 

 ![image](d2d_images/image092.png)

   I    N THIS EXAMPLE, WE    have three events: 'start', 'progress', and 'finish'.   Each event has its own listener.   When we emit these events, the corresponding listeners are invoked with any provided arguments, allowing us to handle different parts of a process. 

####  Removing Listeners 

   S    OMETIMES, YOU MAY    need to remove listeners to prevent memory leaks or to stop listening to certain events under specific conditions.   You can use the    removeListener    or    removeAllListeners    methods for this purpose. 

 const EventEmitter =    require    ('events'); 

 class MyEmitter extends EventEmitter {} 

 const myEmitter = new MyEmitter(); 

 function    onGreet    () { 

 console.    log    ('Hello!   The greet event was emitted.'); 

 } 

 // Register the listener 

 myEmitter.    on    ('greet',    onGreet    ); 

 // Emit the 'greet' event 

 myEmitter.    emit    ('greet'); // Output: Hello!   The greet event was emitted. 

 // Remove the listener 

 myEmitter.    removeListener    ('greet',    onGreet    ); 

 // Emit the 'greet' event again 

 myEmitter.    emit    ('greet'); // No output 

 –––––––– 

 ![image](d2d_images/scene_break.png) 

   H    ERE, WE REGISTER A    listener for the 'greet' event, emit the event to see the listener in action, and then remove the listener using    removeListener    .   When we emit the event again, the listener is no longer called. 

####  Listening to an Event Only Once 

   T    HERE ARE SCENARIOS    where you might want to listen to an event only once.   For this, you can use the    once    method, which ensures that the listener is called only the first time the event is emitted. 

 const EventEmitter =    require    ('events'); 

 class MyEmitter extends EventEmitter {} 

 const myEmitter = new MyEmitter(); 

 // Register a listener that is called only once 

 myEmitter.    once    ('specialEvent', () => { 

 console.    log    ('This will be logged only once.'); 

 }); 

 // Emit the 'specialEvent' twice 

 myEmitter.    emit    ('specialEvent'); // Output: This will be logged only once. 

 myEmitter.    emit    ('specialEvent'); // No output 

 In this example, the listener for 'specialEvent' is registered with    once    .   When the event is emitted the first time, the listener is called.   However, subsequent emissions of the event do not trigger the listener. 

####  Error Handling with Event Emitters 

   H    ANDLING ERRORS IS    a crucial part of building robust applications.   Event emitters have a special 'error' event that you can use to handle errors gracefully. 

 Example: 

 const EventEmitter =    require    ('events'); 

 class MyEmitter extends EventEmitter {} 

 const myEmitter = new MyEmitter(); 

 // Register an error listener 

 myEmitter.    on    ('error', (err) => { 

 console.    error    ('An error occurred:', err.message); 

 }); 

 // Emit an error event 

 myEmitter.    emit    ('error', new Error('Something went wrong!')); 

 In this example, we register a listener for the 'error' event.   When an error is emitted, the listener logs the error message.   If you emit an 'error' event without a listener, Node.js will throw an exception and terminate the process, highlighting the importance of always handling errors. 

 ![image](d2d_images/image131.png)

####  Practical Use Case: Creating a Custom Event Emitter 

   T    O SEE EVENT EMITTERS    in a more practical context, let’s create a custom event emitter for a simple chat application.   This will involve emitting events for user actions like joining, sending messages, and leaving the chat. 

 const EventEmitter =    require    ('events'); 

 class Chat extends EventEmitter { 

  join    (username) { 

 this.    emit    ('join', username); 

 } 

  sendMessage    (username, message) { 

 this.    emit    ('message', username, message); 

 } 

  leave    (username) { 

 this.    emit    ('leave', username); 

 } 

 } 

 const chat = new Chat(); 

 // Register listeners 

 chat.    on    ('join', (username) => { 

 console.    log    (\`${username} joined the chat.\`); 

 }); 

 chat.    on    ('message', (username, message) => { 

 console.    log    (\`${username}: ${message}\`); 

 }); 

 chat.    on    ('leave', (username) => { 

 console.    log    (\`${username} left the chat.\`); 

 }); 

 // Simulate user actions 

 chat.    join    ('Alice'); 

 chat.    sendMessage    ('Alice', 'Hello, everyone!'); 

 chat.    leave    ('Alice'); 

 In this example, we define a    Chat    class that extends EventEmitter.   We then create methods for common chat actions (    join    ,    sendMessage    ,    leave    ) that emit corresponding events.   We also register listeners for these events to handle user actions and log messages. 

 ![image](d2d_images/image204.png)

##  ​   7.4.   Streams and Pipe Chaining 

   S    TREAMS ARE ONE OF    the most powerful features in Node.js, enabling efficient data processing by reading or writing data in chunks, rather than loading it all into memory at once.   This makes streams ideal for handling large files, real-time data, and other scenarios where efficiency and performance are crucial.   Understanding streams and how to use pipe chaining can significantly enhance your ability to build high-performance Node.js applications. 

 ![image](d2d_images/image052.png)

####  What Are Streams? 

   S    TREAMS ARE OBJECTS    that let you read data from a source or write data to a destination in a continuous manner.   In Node.js, there are four types of streams: 

1.    Readable Streams    : Used for reading data sequentially.   Examples include    fs.createReadStream    for file reading and HTTP requests. 
2.    Writable Streams    : Used for writing data sequentially.   Examples include    fs.createWriteStream    for file writing and HTTP responses. 
3.    Duplex Streams    : Both readable and writable, used for bidirectional communication.   Examples include TCP sockets. 
4.    Transform Streams    : A type of duplex stream that can modify or transform the data as it is read and written.   Examples include zlib streams for compression. 

####  Understanding the Basics 

   C    REATING A READABLE    Stream: 

 const fs =    require    ('fs'); 

 // Create a readable stream 

 const readableStream = fs.    createReadStream    ('example.txt', { 

 encoding: 'utf8', 

 highWaterMark: 16 \* 1024 // 16 KB chunk size 

 }); 

 // Handle stream events 

 readableStream.    on    ('data', (chunk) => { 

 console.    log    ('Received chunk:', chunk); 

 }); 

 readableStream.    on    ('end', () => { 

 console.    log    ('No more data.'); 

 }); 

 readableStream.    on    ('error', (err) => { 

 console.    error    ('Error:', err); 

 }); 

 –––––––– 

 ![image](d2d_images/scene_break.png) 

   I    N THIS EXAMPLE, WE    create a readable stream from a file named    example.txt    .   The    data    event is emitted whenever a chunk of data is available to be read.   The    end    event signifies that the stream has no more data to read, and the    error    event handles any errors that occur during reading. 

 Creating a Writable Stream: 

 const fs =    require    ('fs'); 

 // Create a writable stream 

 const writableStream = fs.    createWriteStream    ('output.txt'); 

 // Write data to the stream 

 writableStream.    write    ('Hello, world!\\n'); 

 writableStream.    write    ('Writing more data...\\n'); 

 // End the writable stream 

 writableStream.    end    ('This is the end.\\n'); 

 // Handle stream events 

 writableStream.    on    ('finish', () => { 

 console.    log    ('All writes are now complete.'); 

 }); 

 writableStream.    on    ('error', (err) => { 

 console.    error    ('Error:', err); 

 }); 

 Here, we create a writable stream to a file named    output.txt    .   We write multiple pieces of data to the stream and call the    end    method to indicate that no more data will be written.   The    finish    event is emitted when all data has been flushed to the underlying system, and the    error    event handles any errors that occur during writing. 

####  Pipe Chaining 

   O    NE OF THE MOST POWERFUL    features of Node.js streams is the ability to pipe data from one stream to another.   This is especially useful for tasks like file compression, where you can read data from a file, compress it, and write it to another file, all in a single chain of operations. 

 Example: 

 const fs =    require    ('fs'); 

 const zlib =    require    ('zlib'); 

 // Create a readable stream from the input file 

 const readableStream = fs.    createReadStream    ('input.txt'); 

 // Create a writable stream to the output file 

 const writableStream = fs.    createWriteStream    ('input.txt.gz'); 

 // Create a transform stream for compression 

 const gzip = zlib.    createGzip    (); 

 // Pipe the streams together 

 readableStream 

 .    pipe    (gzip)          // Compress the data 

 .    pipe    (writableStream) // Write the compressed data to the output file 

 .    on    ('finish', () => { 

 console.    log    ('File successfully compressed.'); 

 }) 

 .    on    ('error', (err) => { 

 console.    error    ('Error:', err); 

 }); 

 In this example, we use    fs.createReadStream    to read data from    input.txt    ,    zlib.createGzip    to compress the data, and    fs.createWriteStream    to write the compressed data to    input.txt.gz    .   The    pipe    method connects these streams together, allowing data to flow from the readable stream through the transform stream and into the writable stream seamlessly. 

####  Transform Streams 

   T    RANSFORM STREAMS ARE    a special type of duplex stream where the output is computed based on the input.   They are particularly useful for operations like compression, encryption, or modifying data as it is being read or written. 

 Example: 

 const { Transform } =    require    ('stream'); 

 class UppercaseTransform extends Transform { 

  \_transform    (chunk, encoding, callback) { 

 this.    push    (chunk.    toString    ().    toUpperCase    ()); 

  callback    (); 

 } 

 } 

 const uppercase = new UppercaseTransform(); 

 // Using the custom transform stream 

 process.stdin 

 .    pipe    (uppercase) 

 .    pipe    (process.stdout); 

 In this example, we create a custom transform stream    UppercaseTransform    that converts all input data to uppercase.   By piping    process.stdin    to    uppercase    and then to    process.stdout    , we can transform any input typed into the terminal to uppercase before it is printed out. 

####  Error Handling in Streams 

   H    ANDLING ERRORS IN    streams is crucial to ensure your application can recover gracefully from unexpected issues. 

 Example: 

 const fs =    require    ('fs'); 

 const readableStream = fs.    createReadStream    ('nonexistent.txt'); 

 readableStream.    on    ('error', (err) => { 

 console.    error    ('Error:', err); 

 }); 

 // Providing a fallback or alternate action 

 readableStream.    on    ('error', (err) => { 

 if (err.code === 'ENOENT') { 

 console.    log    ('File not found.   Creating a new file...'); 

 fs.    writeFileSync    ('nonexistent.txt', 'This is a new file.'); 

 } else { 

 console.    error    ('Error:', err); 

 } 

 }); 

 In this example, we handle an error event for a non-existent file.   If the file is not found (    ENOENT    error code), we create a new file as a fallback. 

 ![image](d2d_images/image046.png)

 ![image](d2d_images/image183.png)

##  ​   7.5.   Module Design Patterns 

   A    S YOU DELVE DEEPER    into advanced Node.js programming, understanding module design patterns is essential.   These patterns help you organize your code, improve maintainability, and enhance scalability.   Modules in Node.js are individual files or packages that encapsulate specific functionality and can be reused across different parts of your application.   This section explores some common module design patterns and how to apply them effectively in your Node.js projects. 

####  1.   Revealing Module Pattern 

   T    HE REVEALING MODULE    Pattern is one of the most common design patterns in JavaScript.   It aims to encapsulate private members while exposing only the necessary parts of the module. 

 Example: 

 // mathModule.js 

 const mathModule = (() => { 

 let \_privateCounter = 0; 

 function    \_privateMethod    () { 

 console.    log    ('Private method'); 

 } 

 function    add    (a, b) { 

 \_privateCounter++; 

 return a + b; 

 } 

 function    subtract    (a, b) { 

 \_privateCounter++; 

 return a - b; 

 } 

 return { 

  add    , 

 subtract 

 }; 

 })(); 

 module.exports = mathModule; 

 // main.js 

 const math =    require    ('./mathModule'); 

 console.    log    (math.    add    (5, 3)); // Output: 8 

 console.    log    (math.    subtract    (5, 3)); // Output: 2 

 In this example,    \_privateCounter    and    \_privateMethod    are private and not accessible outside    mathModule    .   Only the    add    and    subtract    methods are revealed and can be used by other modules. 

 ![image](d2d_images/image028.png)

####  2.   Singleton Pattern 

   T    HE SINGLETON PATTERN    ensures that a class has only one instance and provides a global point of access to it.   This is useful for managing global states, like configurations or logging. 

 Example: 

 // logger.js 

 class Logger { 

  constructor    () { 

 if (Logger.instance) { 

 return Logger.instance; 

 } 

 this.logs = \[\]; 

 Logger.instance = this; 

 } 

  log    (message) { 

 this.logs.    push    (message); 

 console.    log    (\`LOG: ${message}\`); 

 } 

  printLogCount    () { 

 console.    log    (\`${this.logs.length} Logs\`); 

 } 

 } 

 module.exports = new Logger(); 

 // main.js 

 const logger =    require    ('./logger'); 

 logger.    log    ('First log'); // Output: LOG: First log 

 logger.    printLogCount    (); // Output: 1 Logs 

 const logger2 =    require    ('./logger'); 

 logger2.    log    ('Second log'); // Output: LOG: Second log 

 logger2.    printLogCount    (); // Output: 2 Logs 

 In this example, the    Logger    class ensures that only one instance is created.   Even when you require    logger    in multiple files, it points to the same instance, maintaining a single state. 

####  3.   Factory Pattern 

   T    HE FACTORY PATTERN    is used to create objects without exposing the instantiation logic to the client.   It provides a way to encapsulate the creation of complex objects and makes the code more modular and easier to maintain. 

 Example: 

 // shapeFactory.js 

 class Circle { 

  constructor    (radius) { 

 this.radius = radius; 

 } 

  draw    () { 

 console.log(\`Drawing a circle with radius ${this.radius}\`); 

 } 

 } 

 class Square { 

  constructor    (side) { 

 this.side = side; 

 } 

  draw    () { 

 console.    log    (\`Drawing a square with side ${this.side}\`); 

 } 

 } 

 class ShapeFactory { 

 static    createShape    (type, size) { 

 if (type === 'circle') { 

 return new Circle(size); 

 } else if (type === 'square') { 

 return new Square(size); 

 } 

 return null; 

 } 

 } 

 module.exports = ShapeFactory; 

 // main.js 

 const ShapeFactory =    require    ('./shapeFactory'); 

 const myCircle = ShapeFactory.    createShape    ('circle', 5); 

 myCircle.    draw    (); // Output: Drawing a circle with radius 5 

 const mySquare = ShapeFactory.    createShape    ('square', 4); 

 mySquare.    draw    (); // Output: Drawing a square with side 4 

 In this example,    ShapeFactory    abstracts the creation logic for different shapes, making the code cleaner and more manageable. 

####  4.   Middleware Pattern 

   T    HE MIDDLEWARE PATTERN    is widely used in web frameworks like Express.js.   It allows you to define a pipeline of processing steps that requests pass through.   Each middleware function can modify the request, response, or pass control to the next middleware. 

 // middleware.js 

 function    logger    (req, res, next) { 

 console.log(\`${req.method} ${req.url}\`); 

  next    (); 

 } 

 function    errorHandler    (err, req, res, next) { 

 console.error(err.stack); 

 res.    status    (500).    send    ('Something broke!'); 

 } 

 module.exports = { 

  logger    , 

 errorHandler 

 }; 

 // server.js 

 const    express    =    require    ('express'); 

 const { logger, errorHandler } =    require    ('./middleware'); 

 const app =    express    (); 

 app.    use    (logger); 

 app.    get    ('/', (req, res) => { 

 res.    send    ('Hello World'); 

 }); 

 app.    get    ('/error', (req, res) => { 

 throw new Error('Oops!'); 

 }); 

 app.    use    (errorHandler); 

 app.    listen    (3000, () => { 

 console.    log    ('Server running on port 3000'); 

 }); 

 In this example, the    logger    middleware logs each request, and the    errorHandler    middleware handles any errors that occur in the application. 

####  5.   Proxy Pattern 

   T    HE PROXY PATTERN PROVIDES    a surrogate or placeholder for another object to control access to it.   This is useful for implementing lazy initialization, access control, logging, and more. 

 Example: 

 // networkRequest.js 

 class NetworkRequest { 

  fetch    (url) { 

 console.log(\`Fetching data from ${url}\`); 

 return \`Data from ${url}\`; 

 } 

 } 

 class NetworkRequestProxy { 

  constructor    () { 

 this.cache = {}; 

 this.networkRequest = new NetworkRequest(); 

 } 

  fetch    (url) { 

 if (!this.cache\[url\]) { 

 this.cache\[url\] = this.networkRequest.    fetch    (url); 

 } 

 return this.cache\[url\]; 

 } 

 } 

 module.exports = NetworkRequestProxy; 

 // main.js 

 const NetworkRequestProxy =    require    ('./networkRequest'); 

 const proxy = new NetworkRequestProxy(); 

 console.    log    (proxy.    fetch    ('https://api.example.com/data1')); // Fetching data from https://api.example.com/data1 

 console.    log    (proxy.    fetch    ('https://api.example.com/data1')); // Cached data 

 console.    log    (proxy.    fetch    ('https://api.example.com/data2')); // Fetching data from https://api.example.com/data2 

 In this example,    NetworkRequestProxy    caches the results of network requests, avoiding redundant network calls and improving performance. 

 ![image](d2d_images/image210.png)

 –––––––– 

 ![image](d2d_images/scene_break.png) 

 ![image](d2d_images/image059.png)

##  ​   7.6.   Practical Examples: Creating a Custom Event Emitter 

   I    N THIS SECTION, WE'LL    put into practice the concepts learned about event emitters by creating a custom event emitter for a simple chat application.   This practical example will help you understand how to use event emitters effectively to handle real-time events in your Node.js applications. 

####  Step 1: Setting Up the Project 

   F    IRST, LET'S SET UP    our project directory and create the necessary files. 

 mkdir chat-app 

 cd chat-app 

 npm init -y 

 npm install events 

 Next, create the following directory structure: 

 chat-app/ 

 ├── index.js 

 └── chat.js 

####  Step 2: Creating the Chat Module 

   W    E'LL CREATE A     Chat    class that extends the    EventEmitter    class from the    events    module.   This class will emit events for user actions like joining, sending messages, and leaving the chat. 

 chat.js: 

 const EventEmitter =    require    ('events'); 

 class Chat extends EventEmitter { 

  join    (username) { 

 this.    emit    ('join', username); 

 } 

  sendMessage    (username, message) { 

 this.    emit    ('message', username, message); 

 } 

  leave    (username) { 

 this.    emit    ('leave', username); 

 } 

 } 

 module.exports = Chat; 

 In this module, the    Chat    class has three methods: 

1.    join(username)    : Emits a 'join' event when a user joins the chat. 
2.    sendMessage(username, message)    : Emits a 'message' event when a user sends a message. 
3.    leave(username)    : Emits a 'leave' event when a user leaves the chat. 

####  Step 3: Using the Chat Module 

   N    OW, WE'LL USE THE     Chat    module in our main application file.   We'll create an instance of the    Chat    class, register listeners for the events, and simulate some user actions. 

 index.js: 

 const Chat =    require    ('./chat'); 

 const chat = new Chat(); 

 // Register listeners 

 chat.    on    ('join', (username) => { 

 console.    log    (\`${username} joined the chat.\`); 

 }); 

 chat.    on    ('message', (username, message) => { 

 console.    log    (\`${username}: ${message}\`); 

 }); 

 chat.    on    ('leave', (username) => { 

 console.    log    (\`${username} left the chat.\`); 

 }); 

 // Simulate user actions 

 chat.    join    ('Alice'); 

 chat.    sendMessage    ('Alice', 'Hello, everyone!'); 

 chat.    leave    ('Alice'); 

 chat.    join    ('Bob'); 

 chat.    sendMessage    ('Bob', 'Hey Alice, where did you go?'); 

 chat.    leave    ('Bob'); 

 In this file, we: 

1.   Import the    Chat    module. 
2.   Create an instance of the    Chat    class. 
3.   Register listeners for the 'join', 'message', and 'leave' events. 
4.   Simulate user actions by calling the    join    ,    sendMessage    , and    leave    methods on the    Chat    instance. 

 When you run this script, you will see the following output: 

 ![image](d2d_images/image186.png)

 ![image](d2d_images/image124.png)

####  Step 4: Enhancing the Chat Module 

   L    ET'S ENHANCE OUR CHAT    application by adding a few more features: 

*     Logging     : Log all events to a file.  
*     Broadcasting     : Broadcast messages to all connected users.  

 Enhanced chat.js: 

 const EventEmitter =    require    ('events'); 

 const fs =    require    ('fs'); 

 class Chat extends EventEmitter { 

  constructor    () { 

  super    (); 

 this.users = \[\]; 

 this.logStream = fs.    createWriteStream    ('chat.log', { flags: 'a' }); 

 } 

  join    (username) { 

 this.users.    push    (username); 

 this.    emit    ('join', username); 

 this.    logEvent    ('join', username); 

 } 

  sendMessage    (username, message) { 

 this.    emit    ('message', username, message); 

 this.    logEvent    ('message', username, message); 

 this.    broadcast    (username, message); 

 } 

  leave    (username) { 

 this.users = this.users.    filter    (user => user !== username); 

 this.    emit    ('leave', username); 

 this.    logEvent    ('leave', username); 

 } 

  logEvent    (event, username, message = '') { 

 const logMessage = \`\[${new Date().    toISOString    ()}\] ${event.    toUpperCase    ()}: ${username} ${message}\\n\`; 

 this.logStream.    write    (logMessage); 

 } 

  broadcast    (username, message) { 

 this.users.    forEach    (user => { 

 if (user !== username) { 

 this.    emit    ('broadcast', user, message); 

 } 

 }); 

 } 

 } 

 module.exports = Chat; 

 In this enhanced version: 

1.    Logging    : We added a    logStream    to log all events to a file named    chat.log    .   The    logEvent    method logs events with timestamps. 
2.    Broadcasting    : The    broadcast    method emits a 'broadcast' event to all users except the sender. 

 Enhanced index.js: 

 const Chat =    require    ('./chat'); 

 const chat = new Chat(); 

 // Register listeners 

 chat.    on    ('join', (username) => { 

 console.    log    (\`${username} joined the chat.\`); 

 }); 

 chat.    on    ('message', (username, message) => { 

 console.    log    (\`${username}: ${message}\`); 

 }); 

 chat.    on    ('leave', (username) => { 

 console.    log    (\`${username} left the chat.\`); 

 }); 

 chat.    on    ('broadcast', (user, message) => { 

 console.    log    (\`Broadcast to ${user}: ${message}\`); 

 }); 

 // Simulate user actions 

 chat.    join    ('Alice'); 

 chat.    sendMessage    ('Alice', 'Hello, everyone!'); 

 chat.    leave    ('Alice'); 

 chat.    join    ('Bob'); 

 chat.    sendMessage    ('Bob', 'Hey Alice, where did you go?'); 

 chat.    leave    ('Bob'); 

 –––––––– 

 ![image](d2d_images/scene_break.png) 

 ![image](d2d_images/image149.png)

   I    N THIS ENHANCED     index.js    , we also register a listener for the 'broadcast' event.   Now, when a user sends a message, it is broadcasted to all other users, and the events are logged to    chat.log    . 

 ![image](d2d_images/image065.png)

 ![image](d2d_images/image229.png)

##  Sources 

   T    HIS BOOK HAS BEEN    crafted with the support of various books, websites, and articles to provide comprehensive and accurate information on Node.js.   Here are 15 key sources that were invaluable in the creation of this book: 

 Books: 

 "Node.js Design Patterns" by Mario Casciaro and Luciano Mammino 

 "Learning Node.js Development" by Andrew Mead 

 "Node.js 8 the Right Way" by Jim R.   Wilson 

 "Pro Node.js for Developers" by Colin J.   Ihrig 

 "Mastering Node.js" by Sandro Pasquali 

 Websites: 

  Node.js Official Documentation    - https://nodejs.org/en/docs/ 

  Mozilla Developer Network (MDN) Web Docs    -  [ https://developer.mozilla.org/ ](https://developer.mozilla.org/)

  npm Documentation    -  [ https://docs.npmjs.com/ ](https://docs.npmjs.com/)

  W3Schools Node.js Tutorial    - https://www.w3schools.com/nodejs/ 

  GeeksforGeeks Node.js Tutorial    - https://www.geeksforgeeks.org/nodejs/ 

 Articles: 

  "Understanding the Node.js Event Loop" by Samer Buna    - freeCodeCamp 

  "A Guide to JavaScript Promises" by Jake Archibald    - HTML5 Rocks 

  "Introduction to Asynchronous Programming in Node.js" by Tim Oxley    - Node.js Blog 

  "Using Buffers in Node.js" by Mosh Hamedani    -  [ Code with Mosh ](https://codewithmosh.com/)

  "Node.js Best Practices" by Yoni Goldberg    -  [ GitHub ](https://github.com/goldbergyoni/nodebestpractices)

 These sources have been instrumental in providing the depth and breadth of knowledge necessary to cover the topics in this book comprehensively.   They offer a wealth of information for anyone looking to deepen their understanding of Node.js and related technologies. 

 As we come to the end of " The Complete Node.js Guide," I hope this journey has equipped you with a deep and comprehensive understanding of Node.js.   From the foundational concepts to advanced techniques, you now have the knowledge and skills to build robust, efficient, and scalable applications. 

 Throughout this book, we've explored the intricacies of Node.js, delving into its architecture, core concepts, file system operations, HTTP servers, networking, security, database integration, and advanced JavaScript patterns.   Each chapter has been crafted to provide you with practical insights and hands-on experience, ensuring you are well-prepared to tackle real-world development challenges. 

 Your feedback is invaluable and helps us improve our content to better serve the developer community.   If you found this book helpful, insightful, or inspiring, please consider leaving a review on Amazon.   Your rating and comments not only support the author but also guide other readers in their journey to mastering Node.js. 

 Thank you for choosing this book.   I wish you continued success in your development career and hope you will create amazing applications that make a difference.   Happy coding!❤ 

* * *

[^( \[1\] )](#c003.xhtml#_ftnref1)  Server-side scripting involves running scripts on a web server, which generate dynamic web pages based on user input or other data. 

[^( \[2\] )](#c003.xhtml#_ftnref2)  A single-threaded event loop handles multiple operations by executing them asynchronously, one at a time, using a single thread. 

[^( \[3\] )](#c003.xhtml#_ftnref3)  npm is the default package manager for Node.js, providing access to a vast repository of open-source libraries and tools.   For more details, visit  [ npmjs.com ](https://www.npmjs.com)  . 

[^( \[4\] )](#c003.xhtml#_ftnref4)  Microservices architecture involves structuring an application as a collection of loosely coupled, independently deployable services. 

[^( \[5\] )](#c003.xhtml#_ftnref5)  WebSockets provide a full-duplex communication channel over a single, long-lived connection, allowing for real-time data exchange between a client and a server. 

[^( \[6\] )](#c003.xhtml#_ftnref6)  Express.js is a web application framework for Node.js, designed for building web applications and APIs.   More information can be found at  [ expressjs.com ](https://expressjs.com)  . 

[^( \[7\] )](#c003.xhtml#_ftnref7)  RESTful APIs (Representational State Transfer) are web services that follow the principles of REST, providing a way to interact with web-based services via HTTP requests. 

[^( \[8\] )](#c003.xhtml#_ftnref8)  An event-driven architecture is a programming paradigm where the flow of the program is determined by events such as user actions, sensor outputs, or messages from other programs. 

[^( \[9\] )](#c003.xhtml#_ftnref9)  Non-blocking I/O allows other processing to continue before the transmission finishes, improving the performance of applications. 

[^( \[10\] )](#c006.xhtml#_ftnref10)  https://www.youtube.com/watch?v=A36VQFdIAkI