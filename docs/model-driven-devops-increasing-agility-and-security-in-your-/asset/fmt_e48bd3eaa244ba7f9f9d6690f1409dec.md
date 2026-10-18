
[Click here to view code image](Images/ch05_images.xhtml#plist5-13)

```
"$schema": "http://json-schema.org/draft-07/schema#",
"title": "Traceroute validation",
"type": "object",
"required": ["traceroute"],
"properties": {
  "traceroute": {
    "type": "object",
    "required": ["192.168.180.1"],
    "properties": {
      "192.168.180.1": {
        "type": "object",
        "required": ["hops"],
        "properties": {
          "hops": {
            "type": "object",
            "required": ["1"],
            "properties": {
              "1": {
                "type": "object",
                "required": ["paths"],
                "properties": {
                  "paths": {
                    "type": "object",
                    "required": ["1"],
                    "properties": {
                      "1": {
                        "type": "object",
                        "required": ["address"],
                        "properties": {
                          "address": {
                            "type": "string",
                            "const": "192.168.4.1"
                          }
...
}
```

Considering all the work that goes into a typical document for network validation, the preceding JSON Schema should not look too onerous. Instead of writing instructions fit only for a human to follow and then somehow duplicating those in automation, we now have a human- and machine-readable schema that can be version-controlled and used to validate traceroute for `every` change in the environment with machine speed and accuracy. Also, we can leverage Jinja templates to dynamically populate parts of the schema (the first-hop IP address, for instance) with device-specific values to make the schema itself more generic.

## Test and Validation Summary

This section focused on a methodical approach to testing and validation using linting for syntax validation, JSON Schema for data validation, and various techniques for functional testing. The order of this approach is important because, as we move from linting and data validation into functional testing, the resource intensity of each operation grows quickly. If we can catch errors with linting and data validation, we can avoid the resource-intensive step of instantiating a network simulation and running all the functional tests. Remember the goal: `fail faster` and increase efficiency.

## Continuous Deployment

Now that you have the tools to apply continuous integration to network infrastructure, you can implement the second part of CI/CD, continuous deployment. As the name implies, continuous deployment is the practice of introducing changes into your network in a continuous manner. That is, pushing changes frequently and without downtime. A requirement for doing so is a robust and thorough CI process. Without CI, CD would not be possible. That said, we basically get CD for free. Consider what it means to have effective CI:

1. We are already using IaC to describe our infrastructure.

2. We have our IaC version-controlled in an SCM.

3. We have an automated CI process.

4. We have complete test and validation coverage (for example, linting, data validation, functional testing).

[Figure 5-9](#ch05.xhtml#ch5fig9) shows one way that we can leverage the existing toolset to add CD to the familiar branch-commit-merge workflow. In this example, after the developer has made their change and the change has passed CI testing and validation, they can then request to merge the change with the main branch. After the merge is approved, we trigger a CD workflow that deploys the configuration from the main branch to the production network.

![FIGURE 5-9 SCM Workflow with CD](Images/05fig09.jpg)

FIGURE 5-9 SCM Workflow with CD

Another common way to implement CD is via a `release` in the SCM. Typically, a release is a snapshot of the current main branch tagged with a version number (for example, v1.2). [Figure 5-10](#ch05.xhtml#ch5fig10) shows how this allows us to batch several changes into a single release and deploy them at one time. In this method, each change is continuously integrated into the main branch but gets deployed to production only when the approver tags it for release (in this case, v1.2).

![FIGURE 5-10 SCM Workflow with CD on Release](Images/05fig10.jpg)

FIGURE 5-10 SCM Workflow with CD on Release

Whereas the two previous examples have focused on a developer or network engineer making changes to IaC using the DevOps toolset, one of the more common ways that a routine change will be automated is via an ITSM platform such as ServiceNow or BMC. Just because we might trigger the change from an ITSM instead of an SCM does not mean that we cannot do proper CI/CD in this scenario. Because most SCMs have a way to trigger actions via API, we can write a workflow in the ITSM that updates the source of truth (either in Git or external database) and then triggers a merge in the SCM via API. This way, we can leverage all the benefits of a customer facing ITSM while still maintaining the rigor of CI/CD.

## Continuous Monitoring

Any discussion of DevOps automation would be incomplete without addressing monitoring; however, there are entire books covering all aspects of monitoring and metrics, so our discussion here is brief and focused on monitoring in the context of model-driven DevOps.

Network monitoring software (NMS) solutions such as Nagios, Datadog, and Zabbix provide important insights into production networks. In addition to providing notifications of problems in your network, they can also be used to gather metrics and, in some cases, use those metrics to predict problems. You might be wondering how this relates to model-driven DevOps. Traditionally, an NMS monitors two types of devices: devices it is explicitly instructed to monitor and devices it has discovered on the network. Each of these approaches has weaknesses. In the explicit approach, network admins frequently forget to add new devices or remove old devices. This neglect can lead to issues such as missing problems or getting spurious alerts on devices that are no longer present on the network.

A discovery-based approach can also be problematic. If your devices are not concentrated in specific IP ranges, have credentials that differ from your standards, or are down at the time of discovery, they can be missed, again leading to devices that are unmonitored and problems that are undetected. However, if we use a model-driven DevOps approach to monitoring our networks, we can leverage our source of truth to drive monitoring configuration in addition to network device configuration. Just as network devices provide APIs for configuration, many NMSs are configurable via an API. Because we can configure our switches and routers using a CI/CD pipeline, we can simply integrate configuration of the NMS into that same process. Our source of truth may even already have all the required data to configure the NMS! Even if it does not, modifying it to carry the required data is generally a simple task. It is not difficult to imagine a scenario where our NMS is continuously running some of the same tests as our CI pipeline, like the earlier traceroute example.

## Summary
