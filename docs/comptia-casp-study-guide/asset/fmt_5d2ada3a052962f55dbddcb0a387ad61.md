
# Security by Design, Default, and Deployment

Security by design means that security measures are built in and that security code reviews must be carried out to uncover potential security problems during the early stages of the development process. The longer the delay in this process, the greater the cost to fix the problem.

Security by default means that security is set to a secure or restrictive setting by default. As an example, OpenBSD is installed at the most secure setting; that is, security by default. See `www.openbsd.org/security.html` for more information.

Security by deployment means that security is added in when the product or application is deployed. Research has shown that every bug removed during a review saves nine hours in testing, debugging, and fixing of the code. As a result, it is much cheaper to add in early on than later. Reviews make the application more robust and more resistant to malicious attackers. A security code review helps new programmers identify common security problems and best practices.

## Secure Functionality

Another issue is secure functionality. Users constantly ask for software that has greater functionality. Macros are an example of this. A macro is just a set of instructions designed to make some tasks easier. This same functionality is used, however, by the macro virus. The macro virus takes advantage of the power offered by word processors, spreadsheets, or other applications. This exploitation is inherent in the product, and all users are susceptible to it unless they choose to disable all macros and do without the functionality. Feature requests drive software development and hinder security because complexity is the enemy of security.

## Application Security Framework

An application security framework is a great framework for system development that can make the development process easier to manage for the security manager. It is designed to build in security controls as needed. There are many different models and approaches. Some have more steps than others, yet the overall goal is the same: to control the process and add security to build defense in depth.

One industry-accepted approach is a standardized System Development Life Cycle (SDLC) process. NIST defines SDLC in NIST SP 800-34 as “The scope of activities associated with a system, encompassing the system's initiation, development and acquisition, implementation, operation and maintenance, and ultimately its disposal that instigates another system initiation.”

### Development Use Cases and Programming Languages

Some development use cases and programming languages used are as follows:

*   **Front-end web development:** `JavaScript`
*   **Back-end web development:** `JavaScript`, `Java`, `Python`, `PHP`, `Ruby`
*   **Mobile development:** `Swift`, `Java`, `C#`
*   **Game development:** `C++`, `C#`
*   **Desktop applications:** `Java`, `C++`, `Python`
*   **Systems programming:** `C`, `Rust`

## Storage Design Patterns

To become more efficient, reduce complexity, and increase performance working with large forms of information, using plans and design patterns for repeatability becomes a way to simplify big data applications. Storage design patterns have various components including data sources as well as ingestion, storage, and access layers.

The ingestion layer takes information directly from the source itself and with that comes a great deal of noise, as well as important data. Filtering the noise from the important data can be difficult when you have multiple sources, data compression, and validation. After the separation, architects have to decide which pattern to use. Some of these patterns include the following:

*   **Multidestination:** Great for multiple data streams
*   **Protocol converter:** Best for data coming in from different types of systems
*   **Real-time streaming:** Used for continuous processing of unstructured data

The data storage layer is important to convert any data into a format that can be readily analyzed. Once the data has been normalized, then data access patterns focus on two primary ways to consume the data, through a developer API or an end-to-end user API. There are many ways to structure data at each layer and use those to efficiently pattern the way data will be consumed in an enterprise.

## Container APIs

You may not need an entire virtual system to complete a specific task; a container can be used. Containers allow for the isolation of applications running on a server. Containers offer a lower-cost alternative to using virtualization to run isolated applications on a single host. When a container is used, the OS kernel provides process isolation and performs resource management. When exchanging information between the container and other resources, one of the best ways to do that is through an application programming interface (API). A container API allows for building complex functionality between containers, systems, and other services.

## Secure Coding Standards

A standard library for a programming language is the library that is made available in every implementation of that language. Depending on the constructs made available by the host language, a standard library may include items such as subroutines, macro definitions, global variables, and templates.

The C++ Standard Library can be divided into the following categories:

*   A standard template library
*   Inputs and outputs
*   Standard C headers

The C++ Standard Library provides several generic containers, functions to use and manipulate these containers, function objects, generic strings and streams (including interactive and file I/O), support for some language features, and functions for everyday tasks. The problem is that some C standard library functions can be used inappropriately or in ways that may cause security problems when programmers don't follow industry-accepted approaches to developing robust, secure applications.

**Code quality** is the term relating to the utility and longevity of a particular piece of code. Code that will be useful for a specific, short-lived function is deemed “low code quality.” A code module that will be useful for several years to come, possibly appropriate for multiple applications, possesses “high code quality.”

## API Management

Application programming interfaces (APIs) are the connection between a consumer and a provider. This could be a client and server or an application and operating system. An API defines how the client should ask for information from the server and how the server will respond. This definition means that programs written in any language can implement an API and make requests.

APIs are useful for building interfaces, but they can also be a point of vulnerability if they are not properly secured and managed. API security relies on authentication, authorization, proper data scoping to ensure that too much data isn't exposed, and appropriate monitoring and logging to remain secure.

There are four major types of APIs that need to be managed:

*   **Open or Public API:** Publicly available to developers, focuses on external users accessing a service or data
*   **Internal or Private API:** Hidden from external users and used only by internal systems
*   **Partner API:** Shared with business partners with a specific workflow to get access
*   **Composite API:** Built with API tooling, allowing access to multiple endpoints in one call

Managing APIs is the process and procedure of creating, publishing, documenting, and validating all the APIs used within an organization to ensure security. Benefits of implementing API management also include the ability to change quickly and automation.

## Middleware
