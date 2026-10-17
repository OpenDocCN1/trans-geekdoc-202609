
-   [你可以通过运行以下命令来验证 Kind 已创建你的集群并配置 `kubectl` 使用它：]

| ​  || $ kubectl cluster-info |

| --- | --- |

| ​  || > Kubernetes master is running at https://127.0.0.1:46023 |

| ​  || KubeDNS is running at \\ |

| ​  || https://127.0.0.1:46023/api/v1/namespaces/kube-system/services/kube-dns:dns/proxy |

[/content]

[content]
-   为了进一步调试和诊断集群问题，请使用 `kubectl cluster-info dump`。

Kind 会在集群中运行一个 Docker 容器来代表一个 Kubernetes 节点。默认情况下，Kind 会启动一个包含所有功能的单节点集群。你可以通过运行以下命令查看节点容器：

| ​  || $ docker ps |

| --- | --- |

| ​  || CONTAINER ID IMAGE COMMAND CREATED ... |

| ​  || 033de99b1e53 kindest/node:v1.18.2 "/usr/local/bin/entr…" 2 minutes... |

[/content]

[content]
-   我们现在拥有一个运行中的 Kubernetes 集群——让我们在上面运行我们的服务！在 Kubernetes 中运行服务需要一个 Docker 镜像，而我们的 Docker 镜像需要一个可执行的入口点。让我们编写一个代理 CLI，它将作为我们服务的可执行文件。

## 编写代理命令行界面

我们的代理 CLI 仅提供足够的功能，可作为 Docker 镜像的入口点运行我们的服务，解析参数，然后配置并运行代理。

我使用 Cobra^([\[57\]](#f_0083.xhtml#FOOTNOTE-57)) 库来处理命令和参数，因为它非常适合创建既简单又复杂的 CLI。它在 Go 社区中被 Kubernetes、Docker、Helm、Etcd、Hugo 等项目使用。Cobra 还与名为 Viper^([\[58\]](#f_0083.xhtml#FOOTNOTE-58)) 的库集成，这是一个用于 Go 应用程序的完整配置解决方案。

第一步是创建 `cmd/proglog/main.go` 文件，并以以下代码开头：

[DeployLocally/cmd/proglog/main.go](http://media.pragprog.com/titles/tjgo/code/DeployLocally/cmd/proglog/main.go) 

| ​  || ​**package**​ main |

| --- | --- |

| ​  ||  |

| ​  || ​**import**​ ( |

| ​  || ​*"log"*​ |

| ​  || ​*"os"*​ |

| ​  || ​*"os/signal"*​ |

| ​  || ​*"path"*​ |

| ​  || ​*"syscall"*​ |

| ​  ||  |

| ​  || ​*"github.com/spf13/cobra"*​ |

| ​  || ​*"github.com/spf13/viper"*​ |

| ​  || ​*"github.com/travisjeffery/proglog/internal/agent"*​ |

| ​  || ​*"github.com/travisjeffery/proglog/internal/config"*​ |

| ​  || ) |

| ​  ||  |

| ​  || ​**func**​ main() { |

| ​  || cli := &cli{} |

| ​  ||  |

| » || cmd := &cobra.Command{ |

| » || Use: ​*"proglog"*​, |

| » || PreRunE: cli.setupConfig, |

| » || RunE: cli.run, |

| » || } |

| ​  ||  |

| ​  || ​**if**​ err := setupFlags(cmd); err != nil { |

| ​  || log.Fatal(err) |

| ​  || } |

| ​  ||  |

| ​  || ​**if**​ err := cmd.Execute(); err != nil { |

| ​  || log.Fatal(err) |

| ​  || } |

| ​  || } |

[/content]

[content]
-   以上代码定义了我们唯一的命令。我们的 CLI 非常简单。在更复杂的应用中，此命令将作为根命令，用于管理子命令。Cobra 会在命令运行时调用你在命令上设置的 RunE 函数。将或调用命令的主要逻辑放在该函数中。Cobra 允许你运行在 RunE 之前和之后的钩子函数。

Cobra 为具有多个子命令的应用程序提供持久标志和钩子（因此我们在此程序中未使用它们）—持久标志和钩子适用于当前命令和所有子命令。持久标志的常见用例是在包装 API 的 CLI 中，每个子命令都需要一个用于 API 端点地址的标志。在这种情况下，你可以在根命令上声明一次 `--api-addr` 持久标志，然后让所有子命令继承该标志。

要定义我们的 cli 和 cfg 类型，添加以下代码：

[DeployLocally/cmd/proglog/main.go](http://media.pragprog.com/titles/tjgo/code/DeployLocally/cmd/proglog/main.go) 

| ​  || ​**type**​ cli ​**struct**​ { |

| --- | --- |

| ​  || cfg cfg |

| ​  || } |

| ​  ||  |

| ​  || ​**type**​ cfg ​**struct**​ { |

| ​  || agent.Config |

| ​  || ServerTLSConfig config.TLSConfig |

| ​  || PeerTLSConfig config.TLSConfig |

| ​  || } |

[/content]

[content]
-   我通常会创建一个 cli 结构体，其中包含所有命令共享的逻辑和数据。我为那些需要特殊处理的字段（如 \*net.TCPAddr 和 \*tls.Config）创建了单独的 cfg 结构体。

现在，让我们设置 CLI 的标志。

### 暴露标志

在前面的代码片段下方，添加以下代码来声明我们 CLI 的标志：

[DeployLocally/cmd/proglog/main.go](http://media.pragprog.com/titles/tjgo/code/DeployLocally/cmd/proglog/main.go) 

| ​  || ​**func**​ setupFlags(cmd \*cobra.Command) ​**error**​ { |

| --- | --- |

| ​  || hostname, err := os.Hostname() |

| ​  || ​**if**​ err != nil { |

| ​  || log.Fatal(err) |

| ​  || } |

| ​  ||  |

| ​  || cmd.Flags().String(​*"config-file"*​, ​*""*​, ​*"Path to config file."*​) |

| ​  ||  |

| ​  || dataDir := path.Join(os.TempDir(), ​*"proglog"*​) |

| ​  || cmd.Flags().String(​*"data-dir"*​, |

| ​  || dataDir, |

| ​  || ​*"Directory to store log and Raft data."*​) |

| ​  ||  |

| ​  || cmd.Flags().String(​*"node-name"*​, hostname, ​*"Unique server ID."*​) |

| ​  ||  |

| ​  || cmd.Flags().String(​*"bind-addr"*​, |

| ​  || ​*"127.0.0.1:8401"*​, |

| ​  || ​*"Address to bind Serf on."*​) |

| ​  || cmd.Flags().Int(​*"rpc-port"*​, |

| ​  || 8400, |

| ​  || ​*"Port for RPC clients (and Raft) connections."*​) |

| ​  || cmd.Flags().StringSlice(​*"start-join-addrs"*​, |

| ​  || nil, |

| ​  || ​*"Serf addresses to join."*​) |

| ​  || cmd.Flags().Bool(​*"bootstrap"*​, false, ​*"Bootstrap the cluster."*​) |

| ​  ||  |

| ​  || cmd.Flags().String(​*"acl-model-file"*​, ​*""*​, ​*"Path to ACL model."*​) |

| ​  || cmd.Flags().String(​*"acl-policy-file"*​, ​*""*​, ​*"Path to ACL policy."*​) |

| ​  ||  |

| ​  || cmd.Flags().String(​*"server-tls-cert-file"*​, ​*""*​, ​*"Path to server tls cert."*​) |

| ​  || cmd.Flags().String(​*"server-tls-key-file"*​, ​*""*​, ​*"Path to server tls key."*​) |

| ​  || cmd.Flags().String(​*"server-tls-ca-file"*​, |

| ​  || ​*""*​, |

| ​  || ​*"Path to server certificate authority."*​) |

| ​  ||  |

| ​  || cmd.Flags().String(​*"peer-tls-cert-file"*​, ​*""*​, ​*"Path to peer tls cert."*​) |

| ​  || cmd.Flags().String(​*"peer-tls-key-file"*​, ​*""*​, ​*"Path to peer tls key."*​) |

| ​  || cmd.Flags().String(​*"peer-tls-ca-file"*​, |

| ​  || ​*""*​, |

| ​  || ​*"Path to peer certificate authority."*​) |

| ​  ||  |

| ​  || ​**return**​ viper.BindPFlags(cmd.Flags()) |

| ​  || } |

[/content]

[content]
-   这些标志允许用户通过命令行参数配置代理，或者了解默认配置。

使用 pflag.FlagSet.{{type}}Var 方法，我们可以直接设置配置的值。但问题是，并非所有类型都有默认的解析 API。例如，我们的 BindAddr 配置是 \*net.TCPAddr，需要从字符串中解析。你可以在有足够数量的相同类型标志时定义自定义标志值，或者使用中间值。

但如果我们想通过文件配置服务，而不仅仅是通过标志，我们需要查看如何从文件加载配置，以支持动态配置。

### 管理你的配置

Viper 提供了一个集中式配置注册系统，多个配置源可以设置配置，但你可以在一个地方读取结果。你可以让用户通过标志、文件或从 Consul 等服务加载动态配置来设置配置——Viper 支持所有这些。

