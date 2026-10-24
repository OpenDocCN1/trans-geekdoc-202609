bean is not saved automatically to the backend database server. There are three types of session beans:

+   - Stateless session beans. A stateless session bean does not maintain state for the client beyond the current invocation, similar to a stateless Web server.

+   - Stateful session beans. A stateful session bean does maintain state on behalf of the client across all invocations within the duration of the session.

+   - Singleton session beans. As the name suggests, a singleton session bean is instantiated only once during the life cycle of an application (that is, there is only a single instance for each singleton session bean). This is different from stateful and stateless sessions beans, which allow multiple instances being created. A singleton session bean typically represents a piece of state that is shared across the application.

+   • Message-driven beans. A message-driven bean is used in conjunction with the Java Message Service to enable J2EE applications to process messages asynchronously.

+   • Entity beans. Entity beans were introduced in J2EE and have been deprecated and replaced by the Java persistence application programming interface (API). An entity bean represents a business object (such as a customer or a product) whose state should be made persistent at the database server. The state persistency can be managed by the bean itself (which means the developer must explicitly write code for the database access), or by the container. Different entity beans might have relationships as they are defined in the database schema.

It is worth noting that an EJB is always executed within a single thread of control under the container.

# 3.2 Fault Detection and Localization

Much of the theory of fault detection in distributed systems has been focused on the detection of fail-stop faults. To detect a fail-stop fault, a fault detector relies on the use of timeouts, even though it may not be reliable in asynchronous systems. Nevertheless,