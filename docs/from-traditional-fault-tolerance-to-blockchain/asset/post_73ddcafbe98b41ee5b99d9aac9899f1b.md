
fail-stop faults can be quickly detected using mechanisms such as timeouts, most application level faults are more subtle (at least revealed by their symptoms during early stages) and much harder to detect and in general, even harder to localize. As reported in [13, 14, 22], for some Internet service providers, up to 75% of the recovery time is spent on application-level fault detection.

Although fault detection and localization have long been an active area of research [2, 12, 19, 29], the approaches employed in recovery-oriented computing are unique in that they target the application-level fault detection and localization based on application-agnostic machine-learning techniques. These approaches have several advantages: (1) they may be applied to many distributed systems with minimum development cost because they are not tied to any specific application and they do not depend on any specific application semantics, and (2) they can cope with unforeseen faults, which is very useful for large complex systems because it is impossible to develop fault models a priori for traditional fault diagnosis methods.

Once a failed component is located, the cheapest method to recover the component is to restart it, which is referred to as microreboot [11]. Microreboot is different from regular reboot in that only the suspected component is restarted instead of the entire server application. As such, microreboot is much faster than a typical reboot. According to [7, 11], restarting an Enterprise JavaBean (EJB) typically takes less than 0.6 seconds, while restarting the entire application server would take about 20 seconds. Microreboot is best at handling transient software bugs (often referred to as Heisenbugs) and resource (such as memory and file descriptors) leaks.

When microreboot is not capable of fixing the problem, such as in the presence of persistent software bugs and the corruption of persistent data, and in case of operator errors, more heavy-weight method must be used to recover the system. A system-level undo/redo methodology was developed to handle these difficult cases. Different from checkpointing and logging introduced in the previous chapter, the system-level undo/redo provides a more comprehensive recovery solution for several reasons: When resetting the state of a process (i.e., undo), the operating system state is also reset. This is especially useful to handle operator error because any persistent effect on the operating system (e.g., files modified, deleted, or created) due to the error must be reversed in order to correct the error. It aims to preserve the application’s intent while performing replay. When replaying an operation, the system behavior might not be consistent with the view of an external user. Such paradoxes will have to be detected and properly addressed by using application-specific consistency rules and compensation methods.

## 3.1 System Model

An important step in failure recovery is to reconstruct the state of the recovering component or process so that it is consistent with other parts of the system and ready to provide services to its clients. For faster recovery, the best practice is to separate data management from application logic. The three-tier architecture [30], which is pervasively used in Internet-based applications, is a good example of this strategy.

![](img/7320b1480d74f1d65f74659cab456782_96_0.png)

Figure 3.1 The three-tier architecture.

As shown in Figure 3.1, in this architecture, persistent state of an application is stored separately at the backend tier (typically a database server) while the middle-tier server (typically an application server) is responsible to handle clients’ requests according to the application logic. As such, the application server at the middle-tier maintains only session state, which typically consists of temporary state that lasts only for the session (e.g., between when a user logs in and when the user logs out). Examples of the session state include the user’s shopping cart and the list of products that the user has viewed. The presentation tier consists of the client software that enables the users of the application to interact with the application via a graphic user interface. Sometimes, the Web server, which interacts with the client software directly and is stateless, is regarded as part of the presentation tier.

When an application server fails, only the session state is lost, which would impact the users of the active sessions this particular server was engaged in. To minimize the negative impact of a failed application server even further, the session state can be separated to a dedicated session state store, as did in [11]. The recovery-oriented computing techniques would work best for applications using the three-tier architecture. This is especially the case for employing the microrebooting technique because the architecture enables the rebooting of components of an application server with minimum impact to the system performance and availability.

As indicated in Figure 3.1, an application using the three-tier architecture is usually implemented using some middleware platform. The dominating platform for Internet-based applications is the Java Platform, Enterprise Edition (Java EE). Java EE facilitates component-based software development. A key component construct is the Enterprise JavaBean (EJB). An EJB implements a specific business function. Java EE also enables the separation of mechanisms and policies [32]. Mechanisms in accomplishing application logic are programmed in EJBs, while the policies on how they are used are specified in terms of Java annotations and/or descriptor files at deployment time.

Java EE is still an evolving middleware platform. At the time when several of the seminal works in recovery-oriented computing [13, 22, 11] were published, the platform was referred to as J2EE and it was selected as the middleware platform of choice for recovery-oriented computing. Since then, the platform has evolved to be less complicated and more efficient.

As shown in Figure 3.2, in Java EE, the components are managed by containers. On the server side, there are two types of containers:

![](img/7320b1480d74f1d65f74659cab456782_98_0.png)

Figure 3.2 The Java EE architecture.

- Web container. This container manages Web components that are responsible to interact directly with clients and to generate Web pages for the clients. Example Web components include Java servlets and user interface objects produced by the Java Server Faces framework.
- EJB container. This container manages EJBs.

At deployment time, the components are installed in their respective containers. A container provides a set of system-level services to the components it manages. Some services are configurable, such as security, transaction management, and remote connectivity. Other services are not configurable, such as the life cycle management, data persistence, and database connection resource pooling. The container mechanism makes EJBs more portable and reusable. It also alleviates the burden of the component developers from writing code for the services provided to the component.

There are several types of EJBs:

- Session beans. A session bean represents an interactive session initiated by a single client (e.g., by logging into an account) inside the application server. All clients' interactions with the application server are done through remote invocation with the session bean. The session bean executes business tasks on behalf of the client. The state of the session bean is not saved automatically to the backend database server. There are three types of session beans:
  - Stateless session beans. A stateless session bean does not maintain state for the client beyond the current invocation, similar to a stateless Web server.
  - Stateful session beans. A stateful session bean does maintain state on behalf of the client across all invocations within the duration of the session.
  - Singleton session beans. As the name suggests, a singleton session bean is instantiated only once during the life cycle of an application (that is, there is only a single instance for each singleton session bean). This is different from stateful and stateless session beans, which allow multiple instances being created. A singleton session bean typically represents a piece of state that is shared across the application.
- Message-driven beans. A message-driven bean is used in conjunction with the Java Message Service to enable J2EE applications to process messages asynchronously.
- Entity beans. Entity beans were introduced in J2EE and have been deprecated and replaced by the Java persistence application programming interface (API). An entity bean represents a business object (such as a customer or a product) whose state should be made persistent at the database server. The state persistency can be managed by the bean itself (which means the developer must explicitly write code for the database access), or by the container. Different entity beans might have relationships as they are defined in the database schema.

It is worth noting that an EJB is always executed within a single thread of control under the container.

## 3.2 Fault Detection and Localization

Much of the theory of fault detection in distributed systems has been focused on the detection of fail-stop faults. To detect a fail-stop fault, a fault detector relies on the use of timeouts, even though it may not be reliable in asynchronous systems. Nevertheless,
