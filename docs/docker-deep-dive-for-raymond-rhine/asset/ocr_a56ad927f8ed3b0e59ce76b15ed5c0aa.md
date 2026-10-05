Let’s switch tack and see how to manage swarm stacks.

# Managing the app

There are two ways to manage Docker stacks:

+   - Imperatively
- Declaratively

The imperative *method* is where you run Docker commands to make changes to the stack. For example, using the **docker service scale** command to increase and decrease the number of service replicas.

The declarative *method* is where you make all changes via the stack file. For example, if you want to change the number of service replicas, you edit the stack file with the desired replica count and run another `docker stack deploy` command.

The declarative method is the preferred method.

Consider the following example that demonstrates why you should manage stacks declaratively.

Imagine you've deployed an app from a stack file that includes **reporting** service and a **catalog** service. The stack file includes other services that are part of the app, but we’re only interested