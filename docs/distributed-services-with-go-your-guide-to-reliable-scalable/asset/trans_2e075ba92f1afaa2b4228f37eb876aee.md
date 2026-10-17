
|​  || ​**service**​ Log { |
| --- | --- |
|​  || ​**rpc**​ Produce(ProduceRequest) ​**returns**​ (ProduceResponse) {} |
|​  || ​**rpc**​ GetServers(GetServersRequest) ​**returns**​ (GetServersResponse) {} |
|​
|​  || } |
|​  || |
|​  || **message**​ GetServersRequest {} |
|​  || **message**​ GetServersResponse { |
|​  || ​**repeated**​ ServerInfo servers = 1;
|​  || } |
|​  || |
|​  || **message**​ ServerInfo { |
|​  || ​**string**​ address = 1;
|​  || ​**bool**​ isLeader = 2;
|​  || } |
