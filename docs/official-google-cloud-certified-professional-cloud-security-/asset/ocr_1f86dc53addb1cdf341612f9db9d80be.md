# Securing a CI/CD pipeline

![](bbox=[0.145, 0.107, 0.854, 0.153])

Figure 13.4 – Artifact trust

As illustrated in the preceding diagram, trust is seen as follows:

+   * When feature development is complete, trust is implicit.
* When security tools are complete, trust is stated explicitly.
* When DEV members accept the DEV environment, trust is implicit.
* When QA approves one or more releases, trust is stated explicitly.
* When stakeholders accept the staging environment, trust is stated explicitly.

Next, we will look at binary authorization, which is a security control that enables organizations to verify the integrity of their container images prior to deployment. It is an important security measure that allows organizations to ensure that only trusted, approved images are being used in their production environments.

# Binary authorization

Attestations of successful events can be combined to show the quality, security, and functionality of the artifact. The Binary Authorization service from Google is a security control that can be used when a program is being deployed in Google Kubernetes Engine (GKE). It helps ensure that only trusted container images are used.

The Binary Authorization is made up of a GKE cluster, an admission controller, a structured policy document protocol, and programmatic access to the digital attestations that go with a given container.

Policies can be developed to allow or reject deployment based on the presence or lack of attestations. Diverse policies can be developed for different contexts because policies are applied at the cluster level. As environments come closer to production, each cluster can carry a higher level of attestation.

CI/CD pipelines automate the process, codify trust, and increase confidence, but they are not risk-free. Because artifacts are pulled from a repository outside the pipeline, a hacked item could be sent out without any more security checks. The goal of binary permission policies is to reduce this risk. They should be used to restrict deployments to fleets from a known set of repositories.

Establishing confidence with attestations in the items traveling through pipelines is important to pipeline security. Docker image attestation is the process used for verifying the provenance and integrity of Docker images in the pipeline. It is a secure process to confirm the contents of a Docker image. It works by verifying the contents of the image are approved and safe to use. The process begins by