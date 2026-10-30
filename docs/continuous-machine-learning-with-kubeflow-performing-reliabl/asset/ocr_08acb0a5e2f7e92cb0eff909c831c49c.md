![](bbox=[0.11, 0.07, 0.9, 0.52])

Figure 1.15: Ingress yaml file

# Namespace:

# WHEN TO USE MULTIPLE NAMESPACES?

Namespaces are intended for use in environments with many users spread across multiple teams, or projects. For clusters with a few to tens of users, you should not need to create or think about namespaces at all. Start using namespaces when you need the features they provide. Namespaces provide a scope for the names. The names of resources need to be unique within a namespace, but not across namespaces. Namespaces cannot be