# Right-Sizing Microservices

Organizations on the path to microservices often struggle with finding the right size for microservices. Teams often ask, “What is the maximum allowable size for a microservice?” A better question would be, “What is the right size for this microservice based on what is needed today?

Microservices are not frozen in time. Instead, they grow and become more complex. Over time, a microservice may need to be split. At other times, two microservices may become codependent and benefit from being combined into a single service. Therefore, the size of a microservice will change over time.

It is also important to note that services grow over time, requiring that the boundaries of a microservice be reevaluated often. This can only be done efficiently if service ownership resides with a single team. Services shared across teams require further coordination meetings.

Right-sizing microservices requires a continuous process of design and reevaluation:

+   1. Identify where transactional boundaries exist to find candidate service boundaries. Defining boundaries helps to reduce the chances of spreading transactions across services.

+   2. Design two or a few course-grained microservices based on the identified boundaries. This step ensures your microservice operations retain integrity within a transactional boundary and avoids the challenges of rolling back transactions across multiple microservice calls over the network.

+   3. Keep splitting services as they grow, being guided by the needs of transactional boundaries while keeping team coordination costs low.

> Tip
It is best to focus on the size of the microservice and more on the purpose of the service. Microservices should seek to make future change easier, even if that the service is more course-grained at the start.

# Decomposing APIs into Microservices

If the team has determined that decomposing the API into two or more microservices would be beneficial, then there are a few additional steps needed when starting the delivery phase: extending previously created API sequence diagrams with more detail, identifying candidate services, and capturing the service design details.