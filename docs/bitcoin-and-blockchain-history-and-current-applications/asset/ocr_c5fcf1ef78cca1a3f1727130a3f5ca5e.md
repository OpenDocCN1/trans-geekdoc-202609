```
1 OrdererOrgs:
2   - Name: Orderer
3     Domain: fnetwork.com
4     Specs:
5       - Hostname: orderer
6 PeerOrgs:
7   - Name: org1
8     Domain: org1.fnetwork.com
9     Template:
10      Count: 1
11    Users:
12      Count: 3
13  - Name: org2
14    Domain: org2.fnetwork.com
15    Template:
16      Count: 1
17    Users:
18      Count: 3
19  - Name: org3
20    Domain: org3.fnetwork.com
21    Template:
22      Count: 1
23    Users:
24      Count: 3
```

FIGURE 12.17 Crypto config configuration file.

Cryptogen tool binary

Command to generate the certificates

passing the crypto-config file location

```
./bin/cryptogen generate --config=./crypto-config.yaml
```

FIGURE 12.18 Cypto files generation command.