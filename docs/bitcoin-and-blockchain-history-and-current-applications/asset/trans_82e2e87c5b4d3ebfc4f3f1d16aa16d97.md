
![](img/115a7d47166d21dfa1d1dc5986da244b_224_0.png)

图 12.7 网络中向对等节点提供排序服务。

![](img/115a7d47166d21dfa1d1dc5986da244b_224_1.png)

图 12.8 提交。

将交易更新到账本。最后，提交对等节点异步通知客户端应用程序交易的成功或失败。每个提交对等节点都会通知应用程序。

除了交易背书、系统有效性和版本控制之外，身份验证在交易流程的每一步都在后台运行。交易的输入和输出会被反复认证，即当交易提案通过网络中的不同组件时，会进行签名和验证。

## 12.4 Hyperledger Fabric 实战

### 12.4.1 Hyperledger Fabric 网络演示

在本节中，我们将介绍在 Hyperledger Fabric 实战中要构建的网络。

本节将为你提供模板，帮助你构建一个包含三个组织、两个通道和一个排序节点的 Hyperledger Fabric 网络。每个组织将有一个对等节点，该对等节点将加入通道。对等节点还将有一个 CouchDB 容器来保存账本的世界状态。Fabric 网络将有两个通道。Org-3 和 Org-2 的对等节点可以加入 channel1，Org-1 和 Org-3 的对等节点可以加入 channel2。我们还将为 channel1 和 channel2 构建链码（智能合约），并使用 Fabric SDK 构建 REST API 与 Fabric 网络交互。

图 12.9 描绘了 Fabric 网络的架构。我们将首先了解先决条件，然后查看 docker-compose 文件中特定于组织的容器定义所需的配置，我们还将查看 docker-compose 文件的排序节点配置。然后，我们将查看 configtx.yaml 配置文件和 crypto-config.yaml 配置文件。完成配置文件后，我们将为两个通道开发一个基本的链码。接下来，我们将看到用于使用 crypto-config 配置文件创建证书、生成创世区块、生成通道交易、生成锚节点通道交易文件、创建通道、加入通道、更新锚节点、安装链码、实例化链码的各种命令。最后，我们将使用 Fabric Node SDK 编写 REST API 与 Hyperledger Fabric 网络交互。

![](img/115a7d47166d21dfa1d1dc5986da244b_225_0.png)

**图 12.9** 网络架构。

```
1 ca.org1.hnetwork.com:
2   container_name: ca.org1.hnetwork.com
3   image: Hyperledger/fabric-ca
4   environment:
5     - FABRIC_CA_HOME=/etc/Hyperledger/fabric-ca-server
6     - FABRIC_CA_SERVER_CA_NAME=ca.org1.hnetwork.com
7   ports:
8     - "7054:7054"
9   command: sh -c 'fabric-ca-server start --ca.certfile /etc/Hyperledger/fabric-ca-server-config/*.org1.hnetwork.com-cert.pem --ca.keyfile /etc/Hyperledger/fabric-ca-server-config/*.org1.hnetwork.com-key.pem --b admin:adminpw -d'
10  volumes:
11    - ./crypto-config/peerOrganizations/org1.hnetwork.com/ca:/etc/Hyperledger/fabric-ca-server-config
12
13  networks:
14    - basic
```

图 12.11 docker-compose 文件中的 CA docker 服务定义。

最后一行定义了该服务运行所使用的网络。

如图 12.12 所示，第一行 `peer0.org1.hnetwork.com` 是 docker-compose 文件中的服务名称，第二行给出启动 compose 时的容器名称，第三行是用于运行容器的镜像。

```
1 peer0.org1.hnetwork.com:
2   container_name: peer0.org1.hnetwork.com
3   image: Hyperledger/fabric-peer
4   environment:
5     - CORE_VM_ENDPOINT=unix:///host/var/run/docker.sock
6     - CORE_PEER_ID=peer0.org1.hnetwork.com
7     - FABRIC_LOGGING_SPEC=debug
8     - CORE_CHAINCODE_LOGGING_LEVEL=DEBUG
9     - CORE_PEER_LOCALMSPID=Org1MSP
10    - CORE_PEER_MSPCONFIGPATH=/etc/Hyperledger/msp/peer/
11    - CORE_PEER_ADDRESS=peer0.org1.hnetwork.com:7051
12    - CORE_VM_DOCKER_HOSTCONFIG_NETWORKMODE=${COMPOSE_PROJECT_NAME}_basic
13    - CORE_LEDGER_STATE_STATEDATABASE=CouchDB
14    - CORE_LEDGER_STATE_COUCHDBCONFIG_COUCHDBADDRESS=couchdb:5984
15    - CORE_LEDGER_STATE_COUCHDBCONFIG_USERNAME=
16    - CORE_LEDGER_STATE_COUCHDBCONFIG_PASSWORD=
17    - CORE_PEER_GOSSIP_BOOTSTRAP=peer0.org1.hnetwork.com:7051
18    - CORE_PEER_GOSSIP_EXTERNALENDPOINT=peer0.org1.hnetwork.com:7051
19  working_dir: /opt/gopath/src/github.com/Hyperledger/fabric
20  command: peer node start
21  ports:
22    - 7051:7051
23    - 7053:7053
24  volumes:
25    - /var/run/:/host/var/run/
26    - ../chaincode:/etc/Hyperledger/chaincode
27    - ./crypto-config/peerOrganizations/org1.hnetwork.com/peers/peer0.org1.hnetwork.com/msp:/etc/Hyperledger/msp/peer
28    - ./crypto-config/peerOrganizations/org1.hnetwork.com/users:/etc/Hyperledger/msp/users
29    - ./config:/etc/Hyperledger/configtx
30  depends_on:
31    - orderer.hnetwork.com
32    - couchdb
33  networks:
34    - basic
```

图 12.12 docker-compose 文件中的 Peer docker 服务定义。

第五行到第十六行是传递给 peer 容器的环境变量。第七行的环境变量值“FABRIC_LOGGING_SPEC=debug”可以是 FATAL|PANIC|ERROR|WARNING|INFO|DEBUG 中的任意一个。第十五和第十六行是 peer 连接到 CouchDB 实例所需的凭据。

工作目录设置了 peer 容器的工作目录路径。下一行定义了运行容器的命令，再下一行定义了暴露的端口。

第 30 行的 `depends_on` 数组用于定义在此服务启动之前应该启动并运行的容器。最后一行定义了该服务运行所使用的桥接网络。

组织的 CouchDB Docker 服务定义。第一行是服务名称，如图 12.13 所示，第二行是容器名称，下一行是服务使用的镜像。传递的环境变量是 CouchDB 实例的用户名和密码。端口将暴露给主机，最后一行定义了该服务运行所使用的桥接网络。

### 12.4.3.1 排序节点

Hyperledger Fabric 提供了几种排序机制，其中包括 SOLO、Kafka、RAFT。

使用 Fabric 进行开发的开发人员通常使用 SOLO 排序方法。在生产阶段，可以使用 Kafka 作为排序系统，它基于 Apache Kafka。该系统提供了一种能够抵抗崩溃故障的排序解决方案。RAFT 排序系统同时提供崩溃容错和拜占庭容错，确保即使存在不稳定或恶意的节点，也能达成共识。

我们将在 Hyperledger Fabric 网络中使用 Kafka 排序系统。

![](img/115a7d47166d21dfa1d1dc5986da244b_229_0.png)

图 12.13 docker-compose 文件中的 CouchDB docker 服务定义。

crypto-config.yaml 和 configtx.yaml 配置文件将在本节后面解释。在这里，我们将了解如何为组织设置 docker-compose.yaml 文件。以下配置是运行组织容器的模板。

图 12.14 展示了 docker-compose 文件中的 Orderer Docker 服务定义。如图 12.14 所示，第一行是服务名称，接下来两行是容器名称和容器使用的镜像。第四行设置容器的工作目录，下一行是用于启动容器的命令。环境变量定义了排序节点必须使用的排序服务类型、创世区块的位置以及其他一些变量。

端口映射为 7050:7050，冒号左侧的值是暴露给主机的端口，右侧是容器映射到的端口。映射的持久卷是通道工件文件夹和排序节点的 MSP 证书。排序节点依赖于 kafka 代理。最后一行定义了该服务运行所使用的桥接网络。

在图 12.15 中，第一行是服务名称，然后是容器名称和用于运行容器的镜像。定义的环境变量包括 `KAFKA_DEFAULT_REPLICATION_FACTOR`（定义默认复制因子）和 `KAFKA_MIN_INSYNC_REPLICAS`（定义 Kafka 必须同步的最小副本数）（见图 12.16）。

```
orderer.fnetwork.com:
  container_name: orderer.fnetwork.com
  image: Hyperledger/fabric-orderer:latest
  working_dir: /opt/gopath/src/github.com/Hyperledger/fabric
  command: orderer
  environment:
    - CONFIGTX_ORDERER_ORDERERTYPE=kafka
    - CONFIGTX_ORDERER_KAFKA_BROKERS=
      [kafka0:9092,kafka1:9092,kafka2:9092,kafka3:9092]
    - ORDERER_KAFKA_RETRY_SHORTINTERVAL=1s
    - ORDERER_KAFKA_RETRY_SHORTTOTAL=30s
    - ORDERER_KAFKA_VERBOSE=true
    - ORDERER_GENERAL_LOGLEVEL=debug
    - ORDERER_GENERAL_LISTENADDRESS=0.0.0.0
    - ORDERER_GENERAL_GENESISMETHOD=file
    - ORDERER_GENERAL_GENESISFILE=/etc/Hyperledger/configtx/genesis.block
    - ORDERER_GENERAL_LOCALMSPID=OrdererMSP
    - ORDERER_GENERAL_LOCALMSPDIR=/etc/Hyperledger/msp/orderer/msp
  ports:
    - 7050:7050
  volumes:
    - ./channel-artifacts:/etc/Hyperledger/configtx
    - ./crypto-config/organizations/fnetwork.com/orderers/orderer.fnetwork.com/msp:/etc/Hyperledger/msp/orderer/msp
  depends_on:
    - kafka0
    - kafka1
    - kafka2
    - kafka3
  networks:
    - basic
```

图 12.14 docker-compose 文件中的 Orderer docker 服务定义。
