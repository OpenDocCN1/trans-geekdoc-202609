
# It’s easier to move from Serf to a stand‑alone service than to move from a stand‑alone service to Serf, so we still have both options open.

# Our service will be easier and more flexible to deploy, making our service more accessible.

So for our service, we’ll use Serf to build service discovery.

Now that we’ve seen the benefits of using Serf, let’s quickly discuss how Serf does its thing.

## Discover Services with Serf

Serf maintains cluster membership by using an efficient, lightweight gossip protocol to communicate between the service’s nodes. Unlike service registry projects like ZooKeeper and Consul, Serf doesn’t have a central‑registry architectural style. Instead, each instance of your service in the cluster runs as a Serf node. These nodes exchange messages with each other in the same way a zombie apocalypse might occur: one infected zombie soon spreads to infect everyone else. With Serf, instead of a spreading zombie virus, you’re spreading information about the nodes in your cluster. You listen to Serf for messages about changes in the cluster and then handle them accordingly.

To implement service discovery with Serf we need to:

1. Create a Serf node on each server.

2. Configure each Serf node with an address to listen on and accept connections from other Serf nodes.

3. Configure each Serf node with addresses of other Serf nodes and join their cluster.

4. Handle Serf’s cluster discovery events, such as when a node joins or fails in the cluster.

Let’s get coding.

Serf is a lightweight tool that you can use for infinite use cases, but its API can be verbose when you have a specific problem to solve. The specific job we want our discovery layer to solve is to tell us when a server joined or left the cluster and what its ID and address are with as little API as possible. So let’s make a discovery package our server will use.

To get started, install the Serf package by running this command:

| ​  || $ go get github.com/hashicorp/serf@v0.8.5 |
| --- | --- |
| ​  || |

Then create an internal/discovery directory and inside it create a membership.go file, beginning with this code:

[ServerSideServiceDiscovery/internal/discovery/membership.go](http://media.pragprog.com/titles/tjgo/code/ServerSideServiceDiscovery/internal/discovery/membership.go) 

| ​1:  || ​**package**​ discovery |
| --- | --- |
| ​  ||  |
| ​  || ​**import**​ ( |
| ​  || ​*"net"*​ |
| ​  ||  |
| ​  || ​*"go.uber.org/zap"*​ |
| ​  ||  |
| ​  || ​*"github.com/hashicorp/serf/serf"*​ |
| ​  || ) |
| ​  ||  |
| ​  || ​**type**​ Membership ​**struct**​ { |
| ​  || Config |
| ​  || handler Handler |
| ​  || serf \*serf.Serf |
| ​  || events ​**chan**​ serf.Event |
| ​  || logger \*zap.Logger |
| ​  || } |
| ​  ||  |
| ​  || ​**func**​ New(handler Handler, config Config) (\*Membership, ​**error**​) { |
| ​  || c := &Membership{ |
| ​  || Config: config, |
| ​  || handler: handler, |
| ​  || logger: zap.L().Named(​*"membership"*​), |
| ​  || } |
| ​  || ​**if**​ err := c.setupSerf(); err != nil { |
| ​  || ​**return**​ nil, err |
| ​  || } |
| ​  || ​**return**​ c, nil |
| ​  || } |
| ​  ||  |
| ​  || ​**type**​ Config ​**struct**​ { |
| --- | --- |
| ​\-  || NodeName ​**string**​ |
| ​\-  || BindAddr ​**string**​ |
| ​\-  || Tags ​**map**​\[​**string**​\]​**string**​ |
| ​5:  || StartJoinAddrs \[\]​**string**​ |
| ​\-  || } |
| ​\-  ||  |
| ​\-  || ​**func**​ (m \*Membership) setupSerf() (err ​**error**​) { |
| ​\-  || addr, err := net.ResolveTCPAddr(​*"tcp"*​, m.BindAddr) |
| ​10:  || ​**if**​ err != nil { |
| ​\-  || ​**return**​ err |
| ​\-  || } |
| ​\-  || config := serf.DefaultConfig() |
| ​\-  || config.Init() |
| ​15:  || config.MemberlistConfig.BindAddr = addr.IP.String() |
| ​\-  || config.MemberlistConfig.BindPort = addr.Port |
| ​\-  || m.events = make(​**chan**​ serf.Event) |
| ​\-  || config.EventCh = m.events |
| ​\-  || config.Tags = m.Tags |
| ​20:  || config.NodeName = m.Config.NodeName |
| ​\-  || m.serf, err = serf.Create(config) |
| ​\-  || ​**if**​ err != nil { |
| ​\-  || ​**return**​ err |
| ​\-  || } |
| ​25:  || ​**go**​ m.eventHandler() |
| ​\-  || ​**if**​ m.StartJoinAddrs != nil { |
| ​\-  || \_, err = m.serf.Join(m.StartJoinAddrs, true) |
| ​\-  || ​**if**​ err != nil { |
| ​\-  || ​**return**​ err |
| ​30:  || } |
| ​\-  || } |
| ​\-  || ​**return**​ nil |
| ​\-  || } |
| ​  ||  |
| ​  || ​**type**​ Handler ​**interface**​ { |
| --- | --- |
| ​  || Join(name, addr ​**string**​) ​**error**​ |
| ​  || Leave(name ​**string**​) ​**error**​ |
| ​  || } |
| ​  ||  |
| ​  || ​**func**​ (m \*Membership) eventHandler() { |
| --- | --- |
