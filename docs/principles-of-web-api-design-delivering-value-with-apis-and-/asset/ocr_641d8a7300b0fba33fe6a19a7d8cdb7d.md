As teams move from the modeling to the design phase, they are faced with a variety of decisions. Some of these will resolve easily, while others will take time and deliberation. Just know that it is difficult to get an API design right the first time. There, teams are encouraged to spend time designing and prototyping their APIs to get feedback from early adopters before coding.

This chapter presents an overview of REST, along with a step-by-step process for migrating an API profile, created during the API modeling phase, into a REST-based API design. Along the way, various decisions and common design patterns are explored. The result will be a high-level API design (Figure 7.1) that applies REST-based principles.

# Principle 3: Select the API design elements that match the need

Trying to find the perfect API style is a fruitless endeavor. Instead, seek to understand and apply the API elements appropriate for the need, whether that is REST, GraphQL, gRPC, or an emerging style just entering the industry. The next three chapters provide insights into popular API styles to help teams select the right style or styles that fit the need. The chapters discuss when to apply each style, when to select synchronous or asynchronous interaction models, and whether to offer SDK libraries.

# What Is a REST-Based API?

Representative State Transfer (REST) is an architectural style for distributed multimedia systems. Unlike HTTP, REST is not a specification that is managed by a standards group. The term was coined by Roy Thomas Fielding in his PhD dissertation, "Architectural Styles and the Design of Network-based Software Architectures."1 This paper outlines the core concepts and constraints for understanding an architectural style and how these constraints were applied in varying degrees to architect the World Wide Web.

When discussing REST APIs or REST-based APIs, many people reference Fielding’s work without realizing that it extends beyond Web-based APIs. The paper seeks to establish fundamental constraints for designing evolvable and scalable distributed systems. Those interested in software architecture, particularly distributed software, should read Fielding’s paper as part of their studies.

> 1 Roy Thomas Fielding, "Architectural Styles and the Design of Network-based Software Architectures" (PhD diss., University of California, 2000), https://www.ics.uci.edu/~fielding/pubs/dissertation/top.htm.