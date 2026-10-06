# API Design Process AntipatTERNS 19

recommendation engine. The leaking of internal implementation details to API consumers resulted in the need to become Apache Lucene experts rather than experts in using the recommendation engine API.

There is value in prototyping APIs or producing evolutionary API design through a mixture of code and design. However, this approach requires a focused effort to find the right balance of prototyping, followed by an outside-in design effort that incorporates the lessons learned. An effective API design process supports this iterative learning approach.

# The Next Release Design Fix Antipattern

Teams without an API design process may find themselves already planning the next release, perhaps before the current version has been pushed to production. This is a result of API design decisions that become unchanging with the current release. Design improvements that would result in breaking changes get moved technical debt to the backlog.

This antipattern starts as an innocent design decision due to the complexity of the underlying code change. Perhaps the code change will take too long. Teams are forced to push an inadequate API design into production and support it for the foreseeable fatale. The needed change can be as small as a spelling mistake or a minor typo that has to remain part of the API to avoid introducing a breaking change to a large number of developers.

An API design process, combined with an API stability contract, as discussed in Chapter 14, “Designing for Change,” can mitigate this kind of problem.

# The Heroic Design Effort Antipattern

Those more familiar with the business domain incorporate their understanding of customer and market need to deliver an API that meets the needs of their target market. This approach may work well for small teams with a deep understanding of the customer and the market.

However, it does not offer a predictable way to engage in emerging areas where matter expertise is in short supply, resulting in the need for heroic API design efforts. Long days of chaotic development are filled with multiple design changes per day during market to production are the signs of the heroic design effort antipatern. Last-minute calls with pilot customers that result in discovering significant design flaws are commonplace. Teams scramble to find a design solution that addresses the flaws before the release. Code is quickly patched to “make it work” with the limited time available.