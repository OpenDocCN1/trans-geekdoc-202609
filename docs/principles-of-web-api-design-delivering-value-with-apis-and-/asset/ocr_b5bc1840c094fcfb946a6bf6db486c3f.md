API CONTRACT TESTING 227

Design-time and development-time testing often comprise policies and tools that are designed to prevent leaking sensitive data through design reviews that identify potential concerns. It also includes authorization policies for each API operation to ensure proper access is enforced.

An API management layer may be employed to apply runtime monitoring and enforcement. Authorization enforcement is managed through configuration, avoiding the need to implement access restrictions within the API implementation. Log analysis may be used to detect and block malicious attacks. More details on security protection are offered in Chapter 15, “Protecting APIs.”

# Operational Monitoring

APIs can and often provide the primary interface for applications to interact with a system. Because the API service plays the role of a dependency, it is critical for the service to be available, whether other services are internal to an organization or to external partners and customers. In addition, there may be service-level agreements (SLAs) that the company has agreed to undertake with customers and partners regarding the performance and uptime of an API. Failing to meet an SLA could yield a negative financial result as well as angry or upset customers.

Operational monitoring answers the following questions:

+   - Is the API available and performing as expected?
- Is the API staying within expected SLAs?
- Is there a need to provision more infrastructure to meet performance goals?

Monitoring and analytics solutions are an important component to API operational monitoring. Analytics verify that real-world usage matches what was seen in testing for both correctness and performance. Analytics measurements can be as simple as logging of performance counters or as complex as integrating third-party libraries with extensive monitoring and visualization support.

# API Contract Testing

API contract testing, sometimes referred to as functional testing, is used to verify that each API operation meets the expected behavior and honors the API’s defined contract for the consumer.