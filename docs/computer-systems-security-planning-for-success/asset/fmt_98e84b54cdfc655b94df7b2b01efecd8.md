
Public cloud infrastructure consists of providers like AWS who host huge data centers throughout the world and welcome anyone who can afford it to use their resources. Public cloud providers claim to be secure and may even allow for audits (typically through a third party) to meet compliance requests. Ultimately the security of the underlying public cloud infrastructure lies in the hands of the provider, something that not all companies are comfortable with.

### 10.2.2. Private

Private cloud takes the virtualization and automation technologies used by public cloud providers and hosts them internally. By utilizing technologies like [OpenStack](https://www.redhat.com/en/topics/openstack) a company can take full control of their deployment and run their own cloud. This has some disadvantages for companies that may lack the servers, space, and utilities, but for companies that were already self-hosted, migrated to the public cloud, and now would like more control, private cloud is an excellent choice.

### 10.2.3. Hybrid

Hybrid cloud uses both models, public and private, and hosts some things on public IaaS services and other on internal, private IaaS services. This can be the best of both worlds, assuming the applications being supported leverage the full advantages of their environment.

### 10.2.4. Multi-Cloud

Multi-cloud typically refers to utilizing more than one cloud provider. This may be required for applications that wish to remain available even if their cloud provider fails. Multi-cloud also avoids the issue of vendor lock-in, where the application is only set up to run on one provider.

From a security standpoint, multi-cloud likely increases the attack surface of an application. You now have to be concerned with the vulnerabilities of two providers instead of just one. This must be weighed against the benefits of redundancy when deciding whether or not to utilize more than one cloud provider.

## 10.3. Serverless Solutions

One interesting outcome of the move to virtualized technologies is the advent of `serverless` solutions. A cloud user might not want to have to admin an entire Linux server, or even a Linux container just to run their application. They may be willing to design the application to work directly within a system that the cloud provider creates.

[Amazon Lambda](https://aws.amazon.com/lambda/) is an example of such a system. Users create functions which run seemingly on their own, without worrying about the underlying systems supporting them. From a security standpoint, this places a lot of trust in the provider.

## 10.4. 4C’s of Cloud Native Security

When reflecting on how to secure an application running in the cloud, a common tactic is to look at the four Cs involved:

Code 

: How secure is the code of the application? Is it configured correctly? Is it subject to buffer overflows or other issues? If the code isn’t secure, the application never will be 

Container 

: How secure is the container itself? Are there limits to what the container has access to? Does the Linux distribution on the container have known vulnerabilities? Is the code running as a privileged user on the container? 

Cluster 

: The container orchestration system is going to run on a cluster, how secure is this cluster? Has the container orchestration system been configured correctly? Is the virtual network being used secure? Are its ingress and egress points mapped and monitored? 

Cloud 

: Is the cloud provider you are using secure? If they have are compromised everything within them is compromised. Can you trust this computing base? 

## 10.5. Lab: Malicious Containers

While containers have made it much easier to deploy software, they have also made it easier to deploy `malicious` software. Imagine that we have an internal company website, written in PHP and deployed in a Docker container. Given the layered nature of the Docker build system, this application is `trusting` that the images it is building from are secure. Take a look at the following `Dockerfile` to see just how easy it is to slip something malicious into the image:

```
FROM php:apache
COPY shell.php /var/www/html/shell.php
COPY index.php /var/www/html/index.php
```

`shell.php` is a shell written in PHP that will execute with the permissions of the web server. This means it will be able to read and write (but not overwrite) in the `/var/www/html` directory.

Let’s download, build, and run this image. Download [the malicious.zip file](https://github.com/rxt1077/it230/raw/main/labs/malicious.zip), unzip it in a directory where you have write access, and navigate to that directory in your shell.
