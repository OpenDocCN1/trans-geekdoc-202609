# Core PHP Programming

Before you design a system, it is important to understand what it's supposed to do. Too often this comes in the form of a verbal request such as, "We need a home page with a guest book and a visitor counter," which is never defined. This usually leads to the building of a prototype that is 25 percent of what the client wants. Changes are made to the prototype, and the site is now 50 percent of what the client wants. During the time the changes were made, the client has moved the target.

The solution to this problem is to have a set of goals and stick with it. This should start with a statement of the goals. In my experience the most important question left is about motivation. When a client asks for a large animated to appear on their index page, often the motivation is a desire to seem familiar with leading-edge technology. Instead of blindly fulfilling the client's request, it is better to look for the best solution for "Why?". Design can say more about the client's attention to details.

Once you have enough times, you should have a list of several goals for the project. These goals should suggest a set of requirements. If one of the system's goals is to generate business, one requirement might raise visitor awareness of items in the catalog. This could be implemented as banners strategically placed within the site. Don't tie yourself down with design issues. The earliest stage of development should concentrate solely on the goals of the system.

From a solid base of goals, you can begin to describe the system. This usually takes the form of a requirements specification, a formal description of the expected behavior. The goals will collect a collection of functional requirements and constraints on design. As I've said, among other things, the site should raise customer awareness. Another requirement could be that the site provide some service to attract visitors. An example is a calculator. It is a good idea to explore possible solutions, but it's still important to keep design out of this.

The requirements specification is formal and structured, but it should be understandable by non-experts in the technology. The description of the system's behavior serves partially as a contract between the client and developer. Clear statements will eliminate misunderstandings that have high cost later in development. When possible, state requirements in measurable terms. Constraining page size is an objective and easily measurable, but sometimes it's all you need.

Table 2-1 lists things which a requirements should aspire. It should only specify external behavior. Every requirement should be expressed as an answer to a "What?" question. This should specify constraints. These are best expressed as quantities: How many hits per day? Maximum page size? Maximum page depth? The requirements

While you should use natural language, don't write a long narrative. Number sections of the document and use diagrams where necessary. It should be a document that helps a future programmer learn about the system. Don't be surprised if programmer is six months later.

The requirements should pay attention to the entire life of the system. If the system needs to be able to recover from a catastrophic failure within an hour, write it into the specification. And the follow-up to this idea is that you should describe how the system deals with adversity—not just disaster, but also illegal input. Some systems ignore user input that is not understood. How many times have you seen a "404 Document Not Found" error? It's nice when a page includes a link to the index page of site.

Keeping these guidelines in mind, refer to Table 2-2, which outlines the structure of a requirements specification. The overview should be a page or less that reviews the goals of the site. If the goals were detailed in another document, make that document available. It is important to preserve the thought that went into the project at each phase. The requirements build on the goals, and in turn the design will build on the requirements. By being able to refer to the original goals of the system will be helpful to the designer and even the implementer.

| Table 2-1. Properties of Requirements Specifications |
| :--- |
| Only specifies external behavior |
| Specifies constraints on the implementation |
| Allows easy modification |
| Serves as a reference tool for system maintainers |
| Records forethought about the life cycle of the system |
| Characterizes acceptable responses to undesired events |

| Table 2-2. Requirements Specification Document Structure |
| :--- |
| Overview of System Goals |
| Operating and Development Environments |
| External Interfaces and Data Flow |
| Functional Requirements |
| Performance Requirements |
| Exception Handling |
| Implementation Priorities |
| Foreseeable Modifications |
| Design Suggestions |

The operating and development environments are sometimes overlooked in specifications. This includes both the browser and the Web server. If you are developing an intranet application, you may be fortunate enough to optimize for a particular browser version. I've found that while a large company may impose a standard browser for the organization for which you've developed an application, no standard may apply to the users in another organization a thousand miles away. My wish for you is that you never build a system for Netscape Navigator version 3.01, only to be asked to make the system for Microsoft Explorer version 3.02.

The Web server is perhaps more under your control and certainly less finicky about differences in code. If you are using PHP, most likely you will be using Apache. It's a good idea to use identical versions of both Apache and PHP for your development and live environments.

For the most part, your list of external interfaces will include the Internet connection between the browser and the Web server, the local file system, and possibly a database connection. I find it helpful to create a diagram that shows the relationship between data elements, the simplest of which might be a box labeled Browser connected to a box labeled Server. The line would have arrows at each end to show that information travels in both directions. This diagram is a description of the context, not a design of the structure. Whether you using a database may be obvious, which database may not. If the system will be storing data somehow, just show data flowing into a box that could be database or flat file. The goal is to describe how data moves around the system.

The functional requirements will certainly be the largest part of the document. If you have drawn a data flow diagram, you may have a very good idea of how the system breaks up into modules. The more you can partition the functionality into distinct pieces, the easier it will be to group the functional requirements. I've written many requirements for Web applications that are essentially data warehouses. My approach has been to dedicate a section to each of the major data entities. A project management application might have a collection of project descriptions, a collection of users, and a collection of comments. Each of these would have a section in the functional requirements that lists first all the information they store and then the ways the information can be manipulated.
