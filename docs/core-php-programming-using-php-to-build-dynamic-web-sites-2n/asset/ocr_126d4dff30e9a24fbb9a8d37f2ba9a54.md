# Core PHP Programming

requirements specification should allow you to change it later. While you should use natural language, don't write a long narrative. Number sections of the document and use diagrams where necessary. It should be a document that helps a future programmer learn about the system. Don't be surprised if programmer is you six months later.

The requirements should pay attention to the entire life of the system. If the system needs to be able to recover from a catastrophic failure within an hour, write it into the specification. And the follow-up to this idea is that you should describe how the system deals with adversity—not just disaster, but also illegal user input. Some systems ignore user input that is not understood. How many times have you seen a "404 Document Not Found" error? It's nice when a page includes a link to the index page of site.

Keeping these guidelines in mind, refer to Table 21-2, which outlines the structure of a requirements specification. The overview should be a page or less that reviews the goals of the site. If the goals were detailed in another document, make that document available. It is important to preserve the thought that went into the project at each phase. The requirements build on the goals, and in turn the design will build on the requirements. By being able to refer to the original goals of the system will be helpful to the designer and even the implementer.

| Table 21-1. Properties of Requirements Specifications |
| Only specifies external system behavior |
| Specifies constraints on the implementation |
| Allows easy modification |
| Serves as a reference tool for system maintainers |
| Records forethought about the life cycle of the system |
| Characterizes acceptable responses to undesired events |

| Table 21-2. Requirements Specification Document Structure |
| Overview of System Goals |
| Operating and Development Environments |
| External Interfaces and Data Flow |
| Functional Requirements |