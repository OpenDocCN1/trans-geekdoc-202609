
`/path/to/xxx` 

| ​ || ​*"github.com/travisjeffery/proglog/internal/loadbalance"*​ |

| --- | --- |

Then update the client function to use your resolver and picker:

| ​ || ​**func**​ client( |

| --- | --- |

| ​ || t \*testing.T, |

| ​ || agent \*agent.Agent, |

| ​ || tlsConfig \*tls.Config, |

| ​ || ) api.LogClient { |

| ​ || tlsCreds := credentials.NewTLS(tlsConfig) |

| ​ || opts := \[\]grpc.DialOption{ |

| ​ || grpc.WithTransportCredentials(tlsCreds), |

| ​ || } |

| ​ || rpcAddr, err := agent.Config.RPCAddr() |

| ​ || require.NoError(t, err) |

| ​ || conn, err := grpc.Dial(fmt.Sprintf( |

| ​ || ​*"%s:///%s"*​, |

| ​ || loadbalance.Name, |

| ​ || rpcAddr, |

| ​ || ), opts...) |

| ​ || require.NoError(t, err) |

| ​ || client := api.NewLogClient(conn) |

| ​ || ​**return**​ client |

| ​ || } |

The highlighted lines specify our scheme in the URL so gRPC knows to use our resolver.

Run the agent’s tests by running $ go run ./internal/agent, and you’ll see that the leader client consume call fails now. Why? Before, each client connected to one server. So the leader client connected to the leader. When we produced records, they were immediately available for consuming with the leader client because it consumed from the leader server—we didn’t have to wait for the leader to replicate the record. Now, each client connects to every server and produces to the leader and consumes from the followers, so we must wait for the leader to replicate the record to the followers.

Update your test to wait for the servers to replicate the record before consuming with the leader client. Move time.Sleep that appears before line 14 to appear before line 4:

| 1: ​ || ​*// wait until replication has finished*​ |

| --- | --- |

| ​-  || time.Sleep(3 \* time.Second) |

| ​-  ||  |

| ​-  || consumeResponse, err := leaderClient.Consume( |

| ​5: ​ || context.Background(), |

| ​-  || &api.ConsumeRequest{ |

| ​-  || Offset: produceResponse.Offset, |

| ​-  || }, |

| ​-  || ) |

| ​10: ​ || require.NoError(t, err) |

| ​-  || require.Equal(t, consumeResponse.Record.Value, \[\]​**byte**​(​*"foo"*​)) |

| ​-  ||  |

| ​-  || followerClient := client(t, agents\[1\], peerTLSConfig) |

| ​-  || consumeResponse, err = followerClient.Consume( |

| ​15: ​ || context.Background(), |

| ​-  || &api.ConsumeRequest{ |

| ​-  || Offset: produceResponse.Offset, |

| ​-  || }, |

| ​-  || ) |

| ​20: ​ || require.NoError(t, err) |

| ​-  || require.Equal(t, consumeResponse.Record.Value, \[\]​**byte**​(​*"foo"*​)) |

Run your tests again with $ make test and watch them pass!

## Resolve the Servers

The gRPC resolver we’ll write in this section will call the GetServers endpoint we made and pass its information to gRPC so that the picker knows what servers it can route requests to.

To start, create a new package for our resolver and picker code by running $ mkdir internal/loadbalance.

gRPC uses the builder pattern for resolvers and pickers, so each has a builder interface and an implementation interface. Because the builder interfaces have one simple method—Build—we’ll implement both interfaces with one type. Create a file named resolver.go in internal/loadbalance that begins with this code:

| ​ || ​**package**​ loadbalance |

| --- | --- |

| ​ ||  |

| ​ || ​**import**​ ( |

| ​ || ​*"context"*​ |

| ​ || ​*"fmt"*​ |

| ​ || ​*"sync"*​ |

| ​ ||  |

| ​ || ​*"go.uber.org/zap"*​ |

| ​ || ​*"google.golang.org/grpc"*​ |

| ​ || ​*"google.golang.org/grpc/attributes"*​ |

| ​ || ​*"google.golang.org/grpc/resolver"*​ |

| ​ || ​*"google.golang.org/grpc/serviceconfig"*​ |

| ​ ||  |

| ​ || api ​*"github.com/travisjeffery/proglog/api/v1"*​ |

| ​ || ) |

| ​ ||  |

| ​ || ​**type**​ Resolver ​**struct**​ { |

| ​ || mu sync.Mutex |

| ​ || clientConn resolver.ClientConn |

| ​ || resolverConn \*grpc.ClientConn |

| ​ || serviceConfig \*serviceconfig.ParseResult |

| ​ || logger \*zap.Logger |

| ​ || } |

Resolver is the type we’ll implement into gRPC’s resolver.Builder and resolver.Resolver interfaces. The clientConn connection is the user’s client connection and gRPC passes it to the resolver for the resolver to update with the servers it discovers. The resolverConn is the resolver’s own client connection to the server so it can call GetServers and get the servers.

Add this snippet below the Resolver type to implement gRPC’s resolver.Builder interface:

| ​ || ​**var**​ \_ resolver.Builder = (\*Resolver)(nil) |

| --- | --- |

| ​ ||  |

| ​ || ​**func**​ (r \*Resolver) Build( |

| ​ || target resolver.Target, |

| ​ || cc resolver.ClientConn, |

| ​ || opts resolver.BuildOptions, |

| ​ || ) (resolver.Resolver, ​**error**​) { |

| ​ || r.logger = zap.L().Named(​*"resolver"*​) |

| ​ || r.clientConn = cc |

| ​ || ​**var**​ dialOpts \[\]grpc.DialOption |

| ​ || ​**if**​ opts.DialCreds != nil { |

| ​ || dialOpts = append( |

| ​ || dialOpts, |

| ​ || grpc.WithTransportCredentials(opts.DialCreds), |

| ​ || ) |

| ​ || } |

| ​ || r.serviceConfig = r.clientConn.ParseServiceConfig( |

| ​ || fmt.Sprintf(​*\`{"loadBalancingConfig":\[{"%s":{}}\]}\`*​, Name), |

| ​ || ) |

| ​ || ​**var**​ err ​**error**​ |

| ​ || r.resolverConn, err = grpc.Dial(target.Endpoint, dialOpts...) |

| ​ || ​**if**​ err != nil { |

| ​ || ​**return**​ nil, err |

| ​ || } |

| ​ || r.ResolveNow(resolver.ResolveNowOptions{}) |

| ​ || ​**return**​ r, nil |

| ​ || } |

| ​ ||  |

| ​ || ​**const**​ Name = ​*"proglog"*​ |

| ​ ||  |

| ​ || ​**func**​ (r \*Resolver) Scheme() ​**string**​ { |

| ​ || ​**return**​ Name |

| ​ || } |

| ​ ||  |

| ​ || ​**func**​ init() { |

| ​ || resolver.Register(&Resolver{}) |

| ​ || } |

resolver.Builder comprises two methods—Build and Scheme:

*   Build receives the data needed to build a resolver that can discover the servers (like the target address) and the client connection the resolver will update with the servers it discovers. Build sets up a client connection to our server so the resolver can call the GetServers API.

*   Scheme returns the resolver’s scheme identifier. When you call grpc.Dial, gRPC parses out the scheme from the target address you gave it and tries to find a resolver that matches, defaulting to its DNS resolver. For our resolver, you’ll format the target address like this: proglog://your-service-address.

We register this resolver with gRPC in init so gRPC knows about this resolver when it’s looking for resolvers that match the target’s scheme.

Put this snippet below init to implement gRPC’s resolver.Resolver interface:

| ​ || ​**var**​ \_ resolver.Resolver = (\*Resolver)(nil) |

| --- | --- |

| ​ ||  |

| ​ || ​**func**​ (r \*Resolver) ResolveNow(resolver.ResolveNowOptions) { |

| ​ || r.mu.Lock() |

| ​ || ​**defer**​ r.mu.Unlock() |

| ​ || client := api.NewLogClient(r.resolverConn) |

| ​ || ​*// get cluster and then set on cc attributes*​ |
