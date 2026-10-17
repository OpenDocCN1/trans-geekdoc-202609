
*   **`NodePort`**: `NodePort` opens a specific port on all the worker nodes, and any traffic sent to this port on the IP address of any of the nodes is forwarded to the service behind the port. The nodes’ IP addresses need to be routable from external sources. The following figure shows the communication flow using `NodePort`:

    ![](OEBPS/Images/B20836_06_07.png)

    Figure 6.7: Accessing a Kubernetes Service via NodePort

    `NodePort` is simple to use, but it has some limitations, such as one service per `NodePort`, a fixed port range to use (`3000` to `32767`), and you need to know the IP addresses of individual worker nodes.

*   **`Load balancer`**: A load balancer is a way to expose services to the internet when you use a cloud provider such as AWS. With a load balancer, you get a public IP address that’s accessible to the internet, and all traffic sent to the IP address will be forwarded to the service behind the load balancer. A load balancer is not part of Kubernetes and it is provided by whatever cloud infrastructure a Kubernetes cluster resides on (for example, AWS). The following figure shows the communication flow from a load balancer to services and Pods:

    ![](OEBPS/Images/B20836_06_08.png)

    Figure 6.8: Accessing a Kubernetes Service via a load balancer

    A load balancer allows you to choose the exact port to use and can support multiple ports per service. However, it does require a separate load balancer per service.

*   **`Ingress`**: An Ingress gateway is the entry point to a cluster. It acts as a load balancer and routes incoming traffic to the different services based on routing rules.

    ![](OEBPS/Images/B20836_06_09.png)

    Figure 6.9: Accessing a Kubernetes Service via Ingress

An Ingress is different from a load balancer and `NodePort` in that it acts as a proxy to manage traffic to clusters. It works with the `NodePort` and load balancer and routes the traffic to the different services. The Ingress way is becoming more commonly used, especially in combination with a load balancer.

In addition to network traffic management from outside of the cluster, another important aspect of Kubernetes network management is to control the traffic flow between different Pods and services within a cluster. For example, you might want to allow certain traffic to access a Pod or service while denying traffic from other sources. This is especially important for applications built on microservices architecture, as there could be many services or Pods that need to work together. Such a network of microservices is also called a `service mesh`. As the number of services grows larger, it becomes challenging to understand and manage the networking requirements, such as `service discovery`, `network routing`, `network metrics`, and `failure recovery`. `Istio` is an open-source service mesh management software that makes it easy to manage a large service mesh on Kubernetes, and it provides the following core functions:

*   **`Ingress`**: Istio provides an Ingress gateway that can be used to expose Pods and services inside a service mesh to the internet. It acts as a load balancer that manages the inbound and outbound traffic for the service mesh. A gateway only allows traffic to come in/out of a mesh – it does not do routing of the traffic. To route traffic from the gateway to the service inside the service mesh, you create an object called `VirtualService` to provide routing rules to route incoming traffic to different destinations inside a cluster, and you create a binding between virtual services and the gateway object to connect the two.

*   **`Network traffic management`**: Istio provides easy rule-based network routing to control the flow of traffic and API calls between different services. When Istio is installed, it automatically detects services and endpoints in a cluster. Istio uses an object called `VirtualService` to provide routing rules to route incoming traffic to different destinations inside a cluster. Istio uses a load balancer called `gateway` to manage the inbound and outbound traffic for the network mesh. The `gateway` load balancer only allows traffic to come in/out of a mesh – it does not do routing of the traffic. To route traffic from the gateway, you create a binding between virtual services and the `gateway` object.

    In order to manage the traffic in and out of a Pod, an Envoy proxy component (aka `sidecar`) is injected into a Pod, and it intercepts and decides how to route all traffic. The Istio component that manages the traffic configurations of the sidecars and service discovery is called the `Pilot`. The `Citadel` component manages authentication for service to service and end user. The `Gallery` component is responsible for insulating other Istio components from the underlying Kubernetes infrastructure. The following figure shows the architecture of Istio on Kubernetes:

    ![](OEBPS/Images/B20836_06_10.png)

    Figure 6.10: Istio architecture

Istio also has support for security and observability, which are critical for building production systems:

*   **`Security`**: Istio provides authentication and authorization for inter-service communications.

*   **`Observability`**: Istio captures metrics, logs, and traces of all service communications within a cluster. Examples of metrics include network latency, errors, and saturation. Examples of traces include call flows and service dependencies within a mesh.

Istio can handle a wide range of Deployment needs, such as load balancing and service-to-service authentication. It can even extend to other clusters.

# Security and access management

Security is a critical consideration for building production-grade systems on Kubernetes. As a practitioner planning to use Kubernetes as the foundational platform for ML, it is important to become familiar with the various security aspects of Kubernetes.

Kubernetes has many built-in security features. These security features allow you to implement fine-grained network traffic control and access control to different Kubernetes APIs and services. In this section, we will discuss network security, authentication, and authorization.

## API authentication and authorization

Access to Kubernetes APIs can be authenticated and authorized for both users and Kubernetes `service accounts` (a service account provides an identity for processes running in a Pod).

Users are handled outside of Kubernetes, and there are a number of user authentication strategies for Kubernetes:

*   **`X.509 client certificate`**: A signed certificate is sent to the API server for authentication. The API server verifies this with the certificate authority to validate the user.

*   **`Single sign-on with OpenID Connect`** (`OIDC`): The user authenticates with the OIDC provider and receives a bearer token (`JSON Web Token` (`JWT`)) that contains information about the user. The user passes the bearer token to the API server, which verifies the validity of the token by checking the certificate in the token.

*   **`HTTP basic authentication`**: HTTP basic authentication requires a user ID and password to be sent as part of the API request, and it validates the user ID and password against a password file associated with the API server.

*   **`Authentication proxy`**: The API server extracts the user identity in the HTTP header and verifies the user with the certificate authority.

*   **`Authentication webhook`**: An external service is used for handling the authentication for the API server.
