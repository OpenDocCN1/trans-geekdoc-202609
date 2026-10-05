| Term | Definition (according to Nigel) |
| --- | --- |
| Container Network | Pluggable interface enabling different network topologies and architectures. |
| Model | Third parties provide CNM plugins for overlay networks and BGP networks, as well as various implementations of each. |

Software running on every Docker node responsible for pulling container images, starting containers, stopping containers, and other low-level container operations. Docker uses two runtimes that work together: **containerd** is Docker's high-level runtime that manages lifecycle events such as starting and stopping containers, whereas **runc** is Docker's low-level runtime that interfaces with kernel constructs such as namespaces and cgroups.