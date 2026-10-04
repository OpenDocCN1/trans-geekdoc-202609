As you can see in Figure 4-38, there is only one medium-severity recommendation for this Azure function—Function App should only be accessible over HTTPS. The intent of this recommendation is to warn that you currently have an Azure function that is accessible via clear text (HTTP). To protect the data in transit, the recommendation is to enable HTTPS on this function.

# Containers

In Azure Security Center, the Containers tab displays all virtual machines deployed with Docker. Security Center provides additional information related to the containers on the machine, such as Docker version and the number of images running on the host. Security Center scans your Docker configurations and provides visibility into misconfigurations by providing a list of recommendations based on the Center for Information Security (CIS) benchmark for Docker.

> NOTE For more information about the Center for Information Security (CIS) benchmark for Docker, see https://www.cisecurity.org/benchmark/docker/

See to see the Containers recommendation, on the Computer & Apps option, under Resource Security Hygiene, click the Containers tab, and you will see the relevant recommendations as shown in Figure 4-39.

![](bbox=[0.063, 0.535, 0.831, 0.706])

FIGURE 4-39 Containers tab showing the available recommendations

To get more information about a container or to remediate the recommendation, click the container. When the container shown in Figure 4-39 is clicked, the Remediate Vulnerabilities In Container Security Configurations recommendation appears, as shown in Figure 4-40.