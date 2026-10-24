Internet-based applications (to handle large number of concurrent users).

Given a system with n component classes, the interaction model for a component instance consists of a set of n – 1 weighted links between the component instance and all the other n – 1 component classes (one for each component class). Here we assume that the component instances of the same component class do not interact with each other. We also assume that the interaction between two components are symmetric in that the interaction is either a local method invocation, or a remote method invocation with a request being sent and the corresponding reply received).

The weight assigned to each link is the probability of the component instance interacting with the linked component class. The sum of the weight on all the links should be equal to 1 (i.e., the component instance has probability of 1 to interact with one or more other component classes).

# EXAMPLE 3.3

![](bbox=[0.19, 0.5, 0.8, 0.64])

Figure 3.4 Component class and component instances.

Consider the example system shown in Figure 3.4. The system consists of 5 component classes:

+   - A Web component class A. Its instances (a1 through a4) handle requests from the end-user.
+   - An application logic component class B. It consists of several stateful session bean instances (b1, b2, b3), which are used to handle the conversations with the end-users.
+   - Application logic component classes C and D. Each class has only a single instance (i.e., singleton session bean instance), representing the state to be shared, such as the inventory of a product, in the system.