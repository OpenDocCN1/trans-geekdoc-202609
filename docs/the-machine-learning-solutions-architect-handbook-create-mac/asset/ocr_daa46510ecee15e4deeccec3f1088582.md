A load balancer allows you to choose the exact port to use and can support multiple ports per service. However, it does require a separate load balancer per service.

+   - Ingress: An Ingress gateway is the entry point to a cluster. It acts as a load balancer and routes incoming traffic to the different services based on routing rules.

![](bbox=[0.123, 0.196, 0.876, 0.703])

Figure 6.9 – Accessing a Kubernetes service via Ingress

An Ingress is different from a load balancer and NodePort in that it acts as a proxy to manage traffic to clusters. It works with the NodePort and load balancer and routes the traffic to the different services. The Ingress way is becoming more commonly used, especially in combination with a load balancer.