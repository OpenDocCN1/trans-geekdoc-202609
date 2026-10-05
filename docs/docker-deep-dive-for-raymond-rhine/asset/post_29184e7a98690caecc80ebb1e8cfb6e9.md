
| Term | Definition (according to Nigel) |
| --- | --- |
| Push | Upload an image to a registry |
| Pull | Download an image from a registry |
| Reconciliation | The process of watching the state of an application and ensuring observed state matches desired state. Docker Swarm runs reconciliation loops, ensuring applications run how you want them to |
| Registry | Central place for storing and retrieving images. We sometimes call them OCI registries, container registries, or Docker registries. |

| Term | Definition (according to Nigel) |
| --- | --- |
| Repository | An area of a registry where you store related container images. You can set access controls per repository. |
| Seccomp | Secure computing Linux kernel feature used by Docker to restrict the syscalls available to a container. |
| Secret | The way Docker Swarm lets you inject sensitive data into a container at runtime. |

| Term | Definition (according to Nigel) |
| --- | --- |
| Service | Capital “S” is a Docker Swarm feature that augments containers with self-healing, scaling, rollouts, and rollbacks. |
| Spin | Framework that makes it easy to build, deploy, and run Wasm apps. Docker Desktop ships with the spin runtime. Created by Fermyon Technologies, Inc. |
| Swarm (also known as Docker Swarm) | Docker’s native orchestration platform. A lightweight and easy alternative to Kubernetes. |

| Term | Definition (according to Nigel) |
| --- | --- |
| Volume | Where containers store important data they need to keep. You can create and delete volumes independently from containers. |
| Wasm | See WebAssembly. |
| WebAssembly | Also known as Wasm. New virtual machine architecture that is smaller, faster, more portable, and more secure than traditional containers. Wasm apps run anywhere with a Wasm runtime. |

| Term | Definition (according to Nigel) |
| --- | --- |
| YAML | Yet Another Markup Language. You write Compose files in YAML. It's a superset of JSON. |

# More from Nigel - @nigelpoulton

## QUICK START KUBERNETES

Nigel Poulton

![](img/aae0230bf8529bd80767c4c780dca8d3_490_0.png)

```
$ kubectl get pod jump-pod -o yaml
apiVersion: v1
kind: Pod
metadata:
  name: jump-pod
  namespace: default
spec:
  containers:
    - image: nigel-poulton/curl:1.0
      imagePullPolicy: IfNotPresent
      name: jump-ctr
      stdin: true
      tty: true
  volumeMounts:
    - mountPath: /var/run/secrets/kubernetes.io/serviceaccount
      name: default-token-2g29h
      readOnly: true
dnsPolicy: ClusterFirst
```

# THE KUBERNETES BOOK

Nigel Poulton & Pushkar Joglekar

## GETTING STARTED WITH DOCKER

By Docker Captain
Nigel Poulton™

![](img/aae0230bf8529bd80767c4c780dca8d3_494_0.png)

# Show some love!

Enjoyed the book!
Head over to Amazon and give it some stars and a review.

![](img/aae0230bf8529bd80767c4c780dca8d3_496_0.png)

Writing books is incredibly hard, and I spent many late nights and early mornings making this book as amazing as possible for you. Taking a couple of minutes to leave a review would be great.
Thanks!
