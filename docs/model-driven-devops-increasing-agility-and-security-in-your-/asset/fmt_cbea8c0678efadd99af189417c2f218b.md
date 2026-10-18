
# CI

```yaml
---
name: CI
on:
  workflow_dispatch:
  pull_request:
    branches:
      - main
    paths:
      - 'mdd-data/**.yml'
      - 'mdd-data/**.yaml'
 
jobs:
  test:
    runs-on: self-hosted
    environment: mdd-dev
    concurrency: mdd-dev
    steps:
      - name: Checkout Inventory
        uses: actions/checkout@v2
      - name: Run YAMLLINT
        run: yamllint mdd-data
      - name: Save Rollback
        run: ansible-playbook ciscops.mdd.save_rollback
      - name: Validate Data
        run: ansible-playbook ciscops.mdd.validate
      - name: Deploy Changes
        run: ansible-playbook ciscops.mdd.update -e dry_run=no
 
      - name: Run Checks
        run: ansible-playbook ciscops.mdd.check
      - name: Load Rollback
        run: ansible-playbook ciscops.mdd.load_rollback
```

When a system user submits a PR, they are asking that a certain change be pushed out to the network. This action starts the CI process to validate the data and test the change. The workflow file specifies that the pipeline should be run when a PR is submitted that changes any file ending in `.yml` or `.yaml` in the `mdd-data` directory of the `main` branch (where we keep the production version of our source of truth). That is, we are specifically testing changes to the source of truth. We might have other workflows that test the actual automation code. If this is the only workflow file in the repo, then the pipeline would not be started for changes made outside of these criteria. It would be common, however, to have many workflows for most operations.

Under the `jobs` sections, we then specify the specific GitHub runners. GitHub provides cloud-based runners, but they typically do not have access to an organization’s internal resources. Because the CML servers used in the reference implementation are within an organization boundary, a GitHub “self-hosted” runner is used. Because it is logically internal to the organization boundary, the self-hosted runner has access to the CML servers and other resources needed for the pipeline (see [Figure 6-8](#ch06.xhtml#ch6fig8)). The `self-hosted` directive means the workflow will be run on one of the self-hosted runners that are made available to that repo or to the organization.

![FIGURE 6-8 GitHub Self-Hosted Runner](Images/06fig08.jpg)

FIGURE 6-8 GitHub Self-Hosted Runner

Next, the `environment` directive tells GitHub Actions which of the available environments to use. An environment defines the information needed to differentiate between test environments. In our case, it includes the CML server, source of truth, credentials for accessing resources, and so on, and allows us to have several different test environments for different scenarios. Closely related is the `concurrency` directive, which allows us to define whether more than one test run can be done in the same environment at the same time. Having two operations running at once could taint the results, so the reference implementation is configured to limit concurrency. Concurrency can also be more granularly applied to different types of operations. For example, you could limit jobs that change a particular part of the model (for example, system, BGP, VLAN) but allow several jobs overall that would not conflict with each other. It is possible to spin up a new test network in CML for every test cycle, but doing so could add a nontrivial amount of overhead for large architectures. Furthermore, test environments are often augmented with physical devices, which are more difficult to provision and return to a known state than virtual resources.

The rest of the `jobs` section executes each phase of the pipeline as visually depicted in [Figure 6-9](#ch06.xhtml#ch6fig9).

![FIGURE 6-9 CI Pipeline](Images/06fig09.jpg)

FIGURE 6-9 CI Pipeline

The pipeline begins by taking a snapshot of the current test environment. Many organizations have long-lived test environments because of the use of physical hardware; therefore, there is a need to maintain the test network in a state that is the same or as close to the production network as possible. Because a PR contains changes that might or might not work, or that might even be rejected by other operators, you do not want to commit it to the test network completely until the change is merged with the `main` branch. By snapshotting the environment, you have a way to go back to the point in time before the change was pushed out.

With the current state of the network saved, the pipeline executes the Ansible Collection roles `data` and `validate` described previously for the next two phases of the pipeline. After the data is validated, it is pushed out to the network. At this point, let’s take a small diversion and talk about the platform that we are using in the environment, Cisco Network Services Orchestrator.

## Hands-on Code: Exercising the Runner

Go to “Exercising the Runner” exercise at the following URL:

[https://github.com/model-driven-devops/mdd#exercises](https://github.com/model-driven-devops/mdd#exercises)

In this exercise, we show you the files that specify the GitHub Actions configuration for the workflows. If your GitHub account supports it, you can also fork the repository and exercise these runners in your own environment.

## Cisco Network Services Orchestrator

It is the main premise of this book that standardizing on a single data model greatly simplifies automation. It does not really matter which model you standardize on so long as it is the same for all devices, irrespective of the model or vendor. When we surveyed the landscape for the best model to use, OpenConfig was the obvious choice because of its comprehensiveness and support across vendors. Although most vendors do support it, each vendor’s comprehensiveness of support is different and almost always incomplete. So, in deciding to use OpenConfig, we knew that we would need to put something in between the automation and the devices themselves. We called this a “platform” in earlier chapters. Our primary reason for using a platform is to give us control over the implementation of the OpenConfig model across different vendors and models of equipment. If the vendor did not implement OpenConfig, we can do it and make sure that it meets our requirements.

We chose Cisco Network Services Orchestrator (NSO) as the platform for our reference implementation. The primary reason is that Cisco, at the time of writing, is the dominant networking vendor in both the enterprise and service provider spaces. So, it makes sense that, because we are predominantly automating Cisco devices, we would use a Cisco product as a platform. Another reason that we chose NSO is that it has rich support for third-party vendors. In fact, a large part of its userbase deploys it for Juniper. There were other options for the platform. For example, OpenDaylight is an open-sourced SDN controller, and Juniper Contrail is an SDN controller from Juniper networks. These solutions would have been viable choices, although they were more oriented toward a more active SDN controller function (for example, active in routing protocols or analytics). We merely wanted something to present a northbound API abstraction that translates to the native device-specific southbound API or CLI. Although NSO can do more than just API abstraction, it also won out in the areas of simplicity, capability, and applicability to infrastructure.
