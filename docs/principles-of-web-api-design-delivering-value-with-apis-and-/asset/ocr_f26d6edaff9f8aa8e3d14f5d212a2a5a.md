# Resiliency, Failover, and Distributed Transactions

With more microservices comes greater complexity when calls between services are required. Synchronous microservices require call chaining across a network and are therefore susceptible to network failure.

Resiliency must be built into each microservice to ensure retries and failover occur in the event of a temporary network outage. The concept of a service mesh, discussed in Chapter 15, "Protecting APIs," was introduced to address these crosscutting concerns, but a service mesh introduces further deployment and operational complexity that may be unnecessary for simple solutions.

Another side of synchronous call chaining is that failures beyond the first call require previous service calls to roll back transactions. During the height of service-oriented architecture (SOA), transaction managers were used to create distributed transactions, usually through the use of two-phase commit (2PC) transactions. This isn't an option with a highly distributed microservice architecture.

Instead, distributed transactions are often implemented using the Saga pattern. A transactional context is applied within each service call, with compensating transactions used to perform the opposite operation when a rollback is required for each resource involved. Event sourcing is often used alongside the Saga pattern to ensure that all operations are atomic transactions backed by a ledger for auditing and troubleshooting purposes.

# Refactoring and Code Sharing Challenges

Refactoring code is more challenging with microservices, as integrated development environments (IDEs) and other refactoring tools can only refactor within a single codebase. Refactoring code across multiple microservice codebases becomes more error prone.

When microservices use the same programming language, the tendency is to utilize a shared codebase for common code. Sharing code between services can create coordination coupling, requiring more meetings to ensure a change to code shared across microservices doesn't negatively impact others. When sharing code between services, all changes must be optional to avoid forcing other teams to be in lockstep.

> 4. Chris Richardson, "Pattern: Saga," Microservice Architecture, accessed August 19, 2021, https://microservices.io/patterns/data/saga.html.