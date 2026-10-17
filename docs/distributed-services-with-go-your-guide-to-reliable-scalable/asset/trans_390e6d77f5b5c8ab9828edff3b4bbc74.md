
我们设置 Raft 的快照存储。Raft 快照用于在必要时高效恢复和恢复数据，例如当你的服务器的 EC2 实例失败，自动扩展组会启动另一个用于 Raft 服务器的实例。与从 Raft 领导节点流式传输所有数据不同，新节点会从快照（你可以将其存储在 S3 或类似的存储服务中）恢复数据，然后从领导节点获取最新的变更。这样更高效，也更不给领导节点造成负担。你需要频繁快照，以减少快照中的数据与领导节点上的数据之间的差异。 retain 变量指定我们将保留一个快照。

我们创建我们的传输层，它包装了一个流层——一个低级别的流层抽象（我们将在 `Stream Layer` 中自行实现流层）：

[CoordinateWithConsensus/internal/log/distributed.go](http://media.pragprog.com/titles/tjgo/code/CoordinateWithConsensus/internal/log/distributed.go) 

| ​  || config := raft.DefaultConfig() |

| --- | --- |

| ​  || config.LocalID = l.config.Raft.LocalID |

| ​  || ​**if**​ l.config.Raft.HeartbeatTimeout != 0 { |

| ​  || config.HeartbeatTimeout = l.config.Raft.HeartbeatTimeout |

| ​  || } |

| ​  || ​**if**​ l.config.Raft.ElectionTimeout != 0 { |

| ​  || config.ElectionTimeout = l.config.Raft.ElectionTimeout |

| ​  || } |

| ​  || ​**if**​ l.config.Raft.LeaderLeaseTimeout != 0 { |

| ​  || config.LeaderLeaseTimeout = l.config.Raft.LeaderLeaseTimeout |

| ​  || } |

| ​  || ​**if**​ l.config.Raft.CommitTimeout != 0 { |

| ​  || config.CommitTimeout = l.config.Raft.CommitTimeout |

| ​  || } |

The config’s LocalID field is the unique ID for this server, and it’s the only config field we must set; the rest are optional, and in normal operation the default config should be fine.

To make our tests faster, we support overriding a handful of timeout configs to speed up Raft. For example, when we shut down the leader, we want the election to finish within a second, whereas in production you’d need a longer timeout to handle networking latency.

Add the following code to create the Raft instance and bootstrap the cluster:

[CoordinateWithConsensus/internal/log/distributed.go](http://media.pragprog.com/titles/tjgo/code/CoordinateWithConsensus/internal/log/distributed.go) 

| ​  || l.raft, err = raft.NewRaft( |

| --- | --- |

| ​  || config, |

| ​  || fsm, |

| ​  || logStore, |

| ​  || stableStore, |

| ​  || snapshotStore, |

| ​  || transport, |

| ​  || ) |

| ​  || ​**if**​ err != nil { |

| ​  || ​**return**​ err |

| ​  || } |

| ​  || hasState, err := raft.HasExistingState( |

| ​  || logStore, |

| ​  || stableStore, |

| ​  || snapshotStore, |

| ​  || ) |

| ​  || ​**if**​ err != nil { |

| ​  || ​**return**​ err |

| ​  || } |

| ​  || ​**if**​ l.config.Raft.Bootstrap && !hasState { |

| ​  || config := raft.Configuration{ |

| ​  || Servers: [​]raft.Server{{ |

| ​  || ID: config.LocalID, |

| ​  || Address: transport.LocalAddr(), |

| ​  || }}, |

| ​  || } |

| ​  || err = l.raft.BootstrapCluster(config).Error() |

| ​  || } |

| ​  || ​**return**​ err |

| ​  || } |

To support configuring Raft, add these highlighted lines to your log’s Config struct in internal/log/config.go:

[CoordinateWithConsensus/internal/log/config.go](http://media.pragprog.com/titles/tjgo/code/CoordinateWithConsensus/internal/log/config.go) 

| ​  || ​**package**​ log |

| --- | --- |

| ​  ||  |

| » || ​**import**​ ( |

| » || ​*"github.com/hashicorp/raft"*​ |

| » || ) |

| ​  ||  |

| ​  || ​**type**​ Config ​**struct**​ { |

| » || Raft ​**struct**​ { |

| » || raft.Config |

| » || StreamLayer \*StreamLayer |

| » || Bootstrap ​**bool**​ |

| » || } |

| ​  || Segment ​**struct**​ { |

| ​  || MaxStoreBytes ​**uint64**​ |

| ​  || MaxIndexBytes ​**uint64**​ |

| ​  || InitialOffset ​**uint64**​ |

| ​  || } |

| ​  || } |

Generally you’ll bootstrap a server configured with itself as the only voter, wait until it becomes the leader, and then tell the leader to add more servers to the cluster. The subsequently added servers don’t bootstrap. That concludes our Raft setup. Let’s continue building our DistributedLog.

### Log API

We’ve written the code to set up a DistributedLog; next we’ll write its public APIs that append records to and read records from the log and wrap Raft. The DistributedLog will have the same API as the Log type to make them interchangeable.

Add this Append method below setupRaft:

[CoordinateWithConsensus/internal/log/distributed.go](http://media.pragprog.com/titles/tjgo/code/CoordinateWithConsensus/internal/log/distributed.go) 

| ​  || ​**func**​ (l \*DistributedLog) Append(record \*api.Record) (​**uint64**​, ​**error**​) { |

| --- | --- |

| ​  || res, err := l.apply( |

| ​  || AppendRequestType, |

| ​  || &api.ProduceRequest{Record: record}, |

| ​  || ) |

| ​  || ​**if**​ err != nil { |

| ​  || ​**return**​ 0, err |

| ​  || } |

| ​  || ​**return**​ res.(\*api.ProduceResponse).Offset, nil |

| ​  || } |

Append(record \*api.Record) appends the record to the log. Unlike in [​*Code the Store*​](#f_0028.xhtml#logcode), where we appended the record directly to this server’s log, we tell Raft to apply a command (we’ve reused for the ProduceRequest for the command) that tells the FSM to append the record to the log. Raft runs the process described in [​*Log Replication*​](#f_0061.xhtml#replication), to replicate the command to a majority of the Raft servers and ultimately append the record to a majority of Raft servers.

Put this apply method below Apply:

[CoordinateWithConsensus/internal/log/distributed.go](http://media.pragprog.com/titles/tjgo/code/CoordinateWithConsensus/internal/log/distributed.go) 

| ​  || ​**func**​ (l \*DistributedLog) apply(reqType RequestType, req proto.Message) ( |

| --- | --- |

| ​  || ​**interface**​{}, |

| ​  || ​**error**​, |

| ​  || ) { |

| ​  || ​**var**​ buf bytes.Buffer |

| ​  || \_, err := buf.Write(\[​**byte**​{​**byte**​(reqType)}) |

| ​  || ​**if**​ err != nil { |

| ​  || ​**return**​ nil, err |

| ​  || } |

| ​  || b, err := proto.Marshal(req) |

| ​  || ​**if**​ err != nil { |

| ​  || ​**return**​ nil, err |

| ​  || } |

| ​  || \_, err = buf.Write(b) |

| ​  || ​**if**​ err != nil { |

| ​  || ​**return**​ nil, err |

| ​  || } |

| ​  || timeout := 10 \* time.Second |

| ​  || future := l.raft.Apply(buf.Bytes(), timeout) |

| ​  || ​**if**​ future.Error() != nil { |

| ​  || ​**return**​ nil, future.Error() |

| ​  || } |

| ​  || res := future.Response() |

| ​  || ​**if**​ err, ok := res.(​**error**​); ok { |

