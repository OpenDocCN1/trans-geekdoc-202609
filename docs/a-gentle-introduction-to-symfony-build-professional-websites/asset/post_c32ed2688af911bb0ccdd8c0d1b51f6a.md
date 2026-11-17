
## Database Connections .................................................................... 371

## Extending the Model........................................................................ 373

## Adding New Methods ........................................................................ 373

## Overriding Existing Methods ........................................................... 374

## Using Model Behaviors..................................................................... 374

## Extended Schema Syntax ................................................................... 375

## Attributes...................................................................................... 375

## Column Details................................................................................ 377

## Foreign Keys................................................................................... 378

## Indexes ........................................................................................ 379

## Empty Columns ................................................................................ 379

## I18n Tables...................................................................................... 380

## Behaviors ...................................................................................... 380

## Beyond the schema.yml: The schema.xml............................................. 381

## Don't Create the Model Twice ........................................................... 382

## Building a SQL Database Structure Based on an Existing Schema ........ 382

## Generating a YAML Data Model from an Existing Database ................... 382

## Summary......................................................................................... 383

## Appendix B: GNU Free Documentation License ................................ 385

## 0. PREAMBLE .................................................................................... 385

## 1. APPLICABILITY AND DEFINITIONS ................................................... 385

## 2. VERBATIM COPYING ....................................................................... 387

## 3. COPYING IN QUANTITY ................................................................... 387

## 4. MODIFICATIONS ............................................................................. 387

## 5. COMBINING DOCUMENTS ................................................................ 389

## 6. COLLECTIONS OF DOCUMENTS ........................................................ 389

## 7. AGGREGATION WITH INDEPENDENT WORKS ..................................... 389

## 8. TRANSLATION ................................................................................. 390

## 9. TERMINATION ................................................................................. 390

## 10. FUTURE REVISIONS OF THIS LICENSE ............................................. 390

## Chapter 1
Introducing Symfony

What can symfony do for you? What's required to use it? This chapter answers these questions.

### Symfony in Brief

A framework streamlines application development by automating many of the patterns employed for a given purpose. A framework also adds structure to the code, prompting the developer to write better, more readable, and more maintainable code. Ultimately, a framework makes programming easier, since it packages complex operations into simple statements.

Symfony is a complete framework designed to optimize the development of web applications by way of several key features. For starters, it separates a web application’s business rules, server logic, and presentation views. It contains numerous tools and classes aimed at shortening the development time of a complex web application. Additionally, it automates common tasks so that the developer can focus entirely on the specifics of an application. The end result of these advantages means there is no need to reinvent the wheel every time a new web application is built!

Symfony is written entirely in PHP. It has been thoroughly tested in various real-world projects, and is actually in use for high-demand e-business websites. It is compatible with most of the available databases engines, including MySQL, PostgreSQL, Oracle, and Microsoft SQL Server. It runs on *nix and Windows platforms. Let's begin with a closer look at its features.

### Symfony Features

Symfony was built in order to fulfill the following requirements:

- Easy to install and configure on most platforms (and guaranteed to work on standard *nix and Windows platforms)
- Database engine-independent
- Simple to use, in most cases, but still flexible enough to adapt to complex cases
- Based on the premise of convention over configuration—the developer needs to configure only the unconventional
- Compliant with most web best practices and design patterns
- 1. http://sf-to.org/answers
- 2. http://sf-to.org/delicious
- 3. http://sf-to.org/dailymotion
- Enterprise-ready—adaptable to existing information technology (IT) policies and architectures, and stable enough for long-term projects
- Very readable code, with phpDocumentor comments, for easy maintenance
- Easy to extend, allowing for integration with other vendor libraries

### Automated Web Project Features

Most of the common features of web projects are automated within symfony, as follows:

- The built-in internationalization layer allows for both data and interface translation, as well as content localization.
- The presentation uses templates and layouts that can be built by HTML designers without any knowledge of the framework. Helpers reduce the amount of presentation code to write by encapsulating large portions of code in simple function calls.
- Forms support automated validation and repopulation, and this ensures a good quality of data in the database and a better user experience.
- Output escaping protects applications from attacks via corrupted data.
- The cache management features reduce bandwidth usage and server load.
- Authentication and credential features facilitate the creation of restricted sections and user security management.
- Routing and smart URLs make the page address part of the interface and search-engine friendly.
- Built-in e-mail and API management features allow web applications to go beyond the classic browser interactions.
- Lists are more user-friendly thanks to automated pagination, sorting, and filtering.
- Factories, plug-ins, and events provide a high level of extensibility.

### Development Environment and Tools

To fulfill the requirements of enterprises having their own coding guidelines and project management rules, symfony can be entirely customized. It provides, by default, several development environments and is bundled with multiple tools that automate common software-engineering tasks:

- The code-generation tools are great for prototyping and one-click back-end administration.
- The built-in unit and functional testing framework provides the perfect tools to allow test-driven development.
- The debug panel accelerates debugging by displaying all the information the developer needs on the page he’s working on.
- The command-line interface automates application deployment between two servers.
- Live configuration changes are possible and effective.
- The logging features give administrators full details about an application’s activities.

### Who Made Symfony and Why?

The first version of symfony was released in October 2005 by project founder Fabien Potencier, coauthor of this book. Fabien is the CEO of Sensio (http://www.sensio.com/), a French web agency well known for its innovative views on web development.

Back in 2003, Fabien spent some time inquiring about the existing open source development tools for web applications in PHP. He found that none fulfilled the previously described requirements. When PHP 5 was released, he decided that the available tools had reached a

- 4. http://www.sensio.com/
