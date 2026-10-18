
```
- hosts: network
  connection: network_cli
  gather_facts: no
  tasks:
    - name: Run command and parse with pyats
      ansible.utils.cli_parse:
        command: "show version"
        parser:
            name: ansible.netcommon.pyats
      register: parser_output

    - debug:
        msg: >-
          Software Version
          {{ parser_output.parsed.version.version }}
```

When run, this playbook produces output like the this:

[Click here to view code image](Images/ch06_images.xhtml#ppg142-2)

```
TASK [debug]*********************************************
ok: [hq-rtr1] => {
    "msg": "Software Version 17.6.1a"
}
```

Note that we printed the value of the software version from the member of a data structure (`parser_output.parsed.version.version`). Although this is a simple example for illustrative purposes, this same mechanism can be used for more complex data. After we have this data, we can then validate it with a JSON Schema. As with the validation data, we also use definition files within the MDD data hierarchy to define the state checking that we want to do. For example, the file `{{ mdd_root }}/org/check-bgp-neighbor-status.yml` defines the following state check:

[Click here to view code image](Images/ch06_images.xhtml#ppg143-1)

```
---
mdd_tags:
  - bgp
mdd_checks:
  - name: BGP Neighbor Status
    command: 'show bgp neighbors'
    schema: 'pyats/bgp-neighbor-state.yml'
    method: cli_parse
```

As with both the OC data and data validation definition files, we can use metadata to limit the devices on which this test is executed. In this case, we run the BGP Neighbor Status test on all devices that have the bgp tag. The command attribute is the specific command to be run, and the schema attribute defines the schema that should be used to validate the data that results from the command. Finally, the method attribute specifies how we are going to collect and parse this data. In this case, we are specifying that we want to get the information directly from the device. There is also an `nso_parse` method that will collect unstructured data and parse it with PyATS, but it executes the command through the NSO server mapped to the device so that all communication with the end device can be done through a single point.

In either case, the data is validated with the following schema from `{{ mdd_schema_root }}/'pyats/bgp-neighbor-state.yml`:

[Click here to view code image](Images/ch06_images.xhtml#ppg143-2)

```
title: BGP Neighbor Check
type: object
required:
  - vrf
properties:
  vrf:
    type: object
    required:
      - default
    properties:
      default:
        type: object
        required:
          - neighbor
        properties:
          neighbor:
            type: object
            additionalProperties:
              type: object
              required:
                - session_state
                - shutdown
              if:
                properties:
                  shutdown:
                    type: boolean
                    const: false
              then:
                properties:
                  session_state:
                    type: string
                    const: Established
```

Again, we are rendering the JSON Schema in YAML for readability. The schema is anchored at the root of the relatively flat data structure provided by PyATS. It first enumerates the properties that need to exist in the provided data for this test to work as written: `session_state` and `shutdown`. Because the PyATS parser returns a list of objects that represent the state data from a neighbor relationship in the configuration, this one parser checks all BGP neighbors and will fail if any one of the neighbor sessions does not have the `session_state` set to Established. For this reason, we include `shutdown` so that there is a way for the operator to indicate when a certain BGP peering should be down (that is, by shutting it down specifically with the shutdown directive).

On some occasions, an operator might want to check the state data for a specific device in part of the hierarchy or devices with a certain tag while pulling in specific data to be used in that check that is relevant to the specified devices. To accommodate this level of granularity, we process the JSON Schema as a Jinja template and provide the data to pass into that template for checking. For example, the definition file `{{ mdd_root }}/org/check-site-routes.yml` checks to make sure that certain routes exist at each of the sites:

[Click here to view code image](Images/ch06_images.xhtml#ppg144-1)

```
---
mdd_tags:
  - router
mdd_checks:
  - name: Check Network-wide Routes
    command: 'show ip route'
    schema: 'pyats/show_ip_route.yml.j2'
    method: nso_parse
    check_vars:
      routes:
        - 172.16.0.0/16
        - 192.168.1.0/24
        - 192.168.2.0/24
```

In this case, we are applying it at the org level to all devices tagged as routers and checking to see whether the provided routes exist. We do that by running the command `show ip route` and validating it against the following schema:

[Click here to view code image](Images/ch06_images.xhtml#ppg145-1)

```
type: object
properties:
  vrf:
    type: object
    properties:
      default:
        type: object
        properties:
          address_family:
            type: object
            properties:
              ipv4:
                type: object
                required:
                  - routes
                properties:
                  routes:
                    type: object
                    required: {{ check_vars.routes }}
```

This schema is applied to the structured data provided by PyATS. The check role processes the file as a Jinja template expanding `check_vars.routes` into the routes specified in the definition file. Using this method, we can use the same schema to check for different routes depending on location and role of a particular device.

## Hands-on Code: State Checking

Go to “State Checking” exercise at the following URL:

[https://github.com/model-driven-devops/mdd#exercises](https://github.com/model-driven-devops/mdd#exercises)

In this exercise, we show you the files that specify the state checks to be done in the network, where they get the state data, and the schemas with which the state is validated. Depending on your environment, you might also be able to run these playbooks to see them in action.

### Restore

The last item in the workflow is to restore the test network to the state that it was in before we pushed out the change. As mentioned previously, we use NSO’s rollback capability to restore the network to a previous state. The only peculiarity is that we do not simply want to execute the rollback file referenced by the ID that we stored earlier in the workflow. Doing so would result in rolling back the last device of the last batch of changes. Instead, we list the available rollbacks from NSO; then we pick the one that immediately follows the ID that we stored in the file. That way, we are rolling back the changes on the first device (and every subsequent device by default) of the batch of changes that we made for this test.

### Continuous Integration Workflow Summary
