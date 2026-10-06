# FIGURE 20.7

Using to
view the IPv6
routing table

| Type | Name | Prefix | Idx | Gateway/Interface Name |
|---|---|---|---|---|n| System | | ::/128 | 1 | Loopback Pendo-Interface |
| System | | 2001::/32 | 15 | Tunnel Pendo-Interface |
| Interface | | 2001:db85:7f48:304f:c3a6:83c4/64 | 15 | Tunnel Pendo-Interface |
| Interface | | 2001:db86/64 | 28 | fe80::f18:d662:32c:31e6:236 |
| Interface | | 2001:db87/64 | 28 | fe80::f18:d662:32c:31e6:236 |
| Interface | | 2001:db88/64 | 28 | fe80::f18:d662:32c:31e6:236 |
| Interface | | 2001:db89/64 | 28 | IPHTPS-Interface |
| Interface | | 2001:db8a/64 | 28 | IPHTPS-Interface |
| Interface | | 2001:db8b/64 | 28 | IPHTPS-Interface |
| Interface | | 2001:db8c/64 | 28 | IPHTPS-Interface |
| Interface | | 2001:db8d:0000:0000/64 | 28 | IPHTPS-Interface |
| Interface | | 2001:db8e:4000:606f:ce25/128 | 28 | |
| Interface | | fe80::fada:dad2::40 | 28 | IPHTPS-Interface |
| Interface | | fe80::fada:dad3::v6 | 28 | Bluetooth Connect |
| Interface | | fe80::fe64/64 | 12 | Wi-Fi |
| Interface | | fe80::fe65/64 | 15 | Tunnel Pendo-Interface |
| Interface | | fe80::fe66/64 | 28 | IPHTPS-Interface |
| Interface | | 192.168.1.1/32 | 28 | Tunnel Pendo-Interface |
| Interface | | fe80::304f:c3a6:83c4/64 | 15 | Tunnel Pendo-Interface |
| Interface | | fe80::253a:11b8:am6c/64 | 28 | IPHTPS-Interface |
| Interface | | fe80::15c5:ff77:d801:x7v | 12 | Wi-Fi |
| System | | ff00::/8 | 16 | Tunnel Pendo-Interface |
| System | | ff00::/8 | 16 | Bluetooth Connect |
| System | | ff00::/8 | 12 | Wi-Fi |

```
> C:\Users\John>
```

As you can see, that's a lot of confusion to understand. Let's pick one of those outputs and analyze it. Because it's new to everyone, let's go with the netsh output. This output has six columns—Publish, Type, Met, Prefix, Idx, and Gateway/Interface Name. Here is what each column represents.

**Publish** Is this entry sent out in router advertisements to computers? This will be a No on anything acting as a router—only routers should be being advertised that they are routers!

**Type** This should show Manual 1 for routes that have been statically added either by hand or by applications and show routes that are added automatically by the IP layer. We have to see Autoconf in any of your routing routes.

**Met** is an abbreviation for "metric." The metric is an arbitrary number that indicates the relative cost of using this route over another that will get to the same destination. When several routes reach the same destination criteria, the one with the lowest metric is always used. We will look at this in a bit of a moment.

**Prefix** is the network prefix that will be matched against the destination address to find the shortest matching prefix.

**Idx** is another abbreviation, this for "interface index." This is a numbering indicating which interface this route refers to for outgoing traffic. The interface index can often be used in netsh commands to specify an interface without remembering its name.