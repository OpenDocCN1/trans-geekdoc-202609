
Finally, we need a way to merge data at various levels and generate data appropriate to the OpenConfig data model. Although Ansible can merge overlapping data structures in inventory, it is not a recommended setting, and its behavior is not conducive to OpenConfig because of the way it handles precedence. We still leverage the Ansible inventory system, but the primary source of truth for MDD is a collection of files in a directory hierarchy organized in the same way that our network is structured. The following directory hierarchy is used in the reference implementation:

[Click here to view code image](Images/ch06_images.xhtml#ppg125-1)

```
.
└── org
    ├── region1
    │   ├── hq
    │   │   ├── hq-rtr1
    │   │   ├── hq-rtr2
    │   │   ├── hq-sw1
    │   │   └── hq-sw2
    │   └── site1
    │       ├── site1-rtr1
    │       └── site1-sw1
    └── region2
        └── site2
            ├── site2-rtr1
            └── site2-sw1
```

This hierarchy gives you a single authoritative structure where each device is in one and only one set of groups. For example, only the groups `org`, `region1`, and `hq` are searched for data that applies to the device `hq-rtr1`. To find the applicable data for a particular device, all directories in the direct path from the highest level (for example, `org`) to the device itself would be searched for files with names of a particular pattern (for example, `oc-\*.yml`). In the case of `hq-rtr1`, that directory list would be (rooted in the filesystem at `mdd_root`):

[Click here to view code image](Images/ch06_images.xhtml#ppg125-2)

```
{{ mdd_root }}/org
{{ mdd_root }}/org/region1
{{ mdd_root }}/org/region1/hq
{{ mdd_root }}/org/region1/hq/hq-rtr1
```

Data found in the files at the lower level would override data found in files at the upper level, providing the required data precedence. Let’s examine how to do this with the NTP service example. To define the organization-level defaults, create the file `{{ mdd_root }}/org/oc-ntp.yml` with the following data:

[Click here to view code image](Images/ch06_images.xhtml#ppg126-1)

```
---
mdd_data:
  openconfig-system:system:
    clock:
      config:
        timezone-name: 'EDT -8 0'
    ntp:
      config:
        enabled: true
      servers:
        server:
          - address: '1.us.pool.ntp.org'
            config:
              address: '1.us.pool.ntp.org'
              association-type: SERVER
              iburst: true
          - address: '2.us.pool.ntp.org'
            config:
              address: '2.us.pool.ntp.org'
              association-type: SERVER
              iburst: true
```

Notice that the previous OpenConfig data was put into a different root, `mdd_data`. Placing the data in a higher-level data structure makes handling it a little bit easier in the code in addition to allowing the specification of metadata (for example, tags). Because this data is specified at the org level, it applies to all devices in our network. To override the time zone for region2, we create the file `{{ mdd_root }}/org/region2/oc-ntp.yml` with the following data:

[Click here to view code image](Images/ch06_images.xhtml#ppg126-2)

```
---
mdd_data:
  openconfig-system:system:
    clock:
      config:
        timezone-name: 'EST -5 0
```

We do not specify the NTP server information again because it is inherited from the org-level data. When the data for a device in region2 is constructed (for example, `site2-rtr1`), the clock element in the data structure will be overridden and the rest of the data preserved. This is done with a derivative of the Ansible combine filter named `mdd_combine` that we developed that combines the data in a way that is conducive to the OpenConfig data model. When you use `mdd_combine` on the data contained in `mdd_data` in these two files, it will override `timezone-name` and generate the following for any device in region2:

[Click here to view code image](Images/ch06_images.xhtml#ppg127-1)

```
---
mdd_data:
  openconfig-system:system:
    clock:
      config:
        timezone-name: 'EDT -5 0'
    ntp:
      config:
        enabled: true
      servers:
        server:
          - address: '1.us.pool.ntp.org'
            config:
              address: '1.us.pool.ntp.org'
              association-type: SERVER
              iburst: true
          - address: '2.us.pool.ntp.org'
            config:
              address: '2.us.pool.ntp.org'
              association-type: SERVER
              iburst: true
```

In addition to applying data relevant to a device’s physical location, we also want to apply data based on a device’s role. For this, we implement a tagging system. If a device has a particular tag, then it applies all data to that device relevant to that device’s tags. To demonstrate this, here is an example of applying data to only devices that have a specific role. The file `{{ mdd_root }}/org/oc-vlan.yml` specifies all of the VLANs that are in the organization (only two for brevity). Specifying the VLAN data at the org level provides consistency across the organization without having to use any protocols to distribute VLANs. Let’s look at the contents of `oc-vlan.yml`:

[Click here to view code image](Images/ch06_images.xhtml#ppg127-2)

```
---
mdd_tags:
  - switch
mdd_data:
  openconfig-network-instance:network-instances:
    network-instance:
      - name: 'default'
        config:
          name: 'default'
          type: 'DEFAULT_INSTANCE'
          enabled: true
        vlans:
          vlan:
            - vlan-id: 100
              config:
                vlan-id: 100
                name: 'Corporate'
                status: 'ACTIVE'
            - vlan-id: 101
              config:
                vlan-id: 101
                name: 'Guest'
                status: 'ACTIVE'
```

Of note is the addition of the metadata `mdd_tags` that allows us to specify that this data should apply only to devices with the `switch` tag.

## Hands-on Code: Exploring the Data

Go to “Exploring the Data” exercise at the following URL:

[https://github.com/model-driven-devops/mdd#exercises](https://github.com/model-driven-devops/mdd#exercises)

This exercise shows you the files that contain the configuration for the data, how they are structured in the data hierarchy, and how they are combined to create the configuration data for a specific device. In addition, you can run these playbooks in your environment and modify them to get a better idea of how they work.

## Automation Tooling

The reference implementation uses Ansible structured as an Ansible collection for all the tooling. Using Ansible collections helps maintain a consistent, versioned codebase that can be leveraged across many different applications of MDD to different organizations. When a particular feature or functionality is added for one organization, other organizations will inherit it (after proper testing, of course).

The Ansible Collection is structured as roles that execute the various phases of the pipeline along with various Ansible plug-ins that implement some of the specific functionality. The three roles that line up with the phases of the pipeline presented are `data`, `validate`, and `check`.

### The data Role

The `ciscops.mdd.data` role implements the logic presented to construct the configuration data from the source of truth. This data is then made available in a variable in the device’s context. The role is designed to be called at the beginning of the playbook so that the data is available to tasks in that playbook. For example, here is a simple playbook that shows the device’s configuration:

[Click here to view code image](Images/ch06_images.xhtml#ppg129-1)

```
- hosts: network
  connection: local
  gather_facts: no
  roles:
    - ciscops.mdd.data
  tasks:
    - debug:
        var: mdd_data
```
