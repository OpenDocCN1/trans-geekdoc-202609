varying times and loads will assist in creating a better picture of overall network performance.

# Example 17-8 Extended traceroute Command on R1

```
R1# traceroute
Protocol [ip]:
Target IP address: 10.1.1.10
Ingress traceroute [n]:
Source address: 192.168.10.1
DSCP Value [0]:
Numeric display [n]:
Timeout in seconds [3]:
Probe count [3]:
Minimum Time to Live [1]:
Maximum Time to Live [30]:
Port Number [33434]:
Loose, Strict, Record, Timestamp, Verbose [none]:
Type escape sequence to abort.
Tracing the route to 192.168.10.10
VRF info: (vrf in name/id, vrf out name/id)
  1 209.165.200.226 1 msec 1 msec 1 msec
  2 209.165.200.230 0 msec 1 msec 0 msec
  3 *
      10.1.1.10 2 msec 2 msec
R1#
```

The output derived from network commands contributes data to the network baseline. One method for starting a baseline is to copy and paste the results from an executed ping, traceroute, or other relevant commands into a text file. Such a text file can be timestamped with the date and saved into an archive for later retrieval and comparison with other similar files.

Among items to consider are error messages and the response times from host to host. If there is a considerable increase in response times, there may be a latency issue to address.

For example, the ping output in Example 17-9 was captured and pasted into a text file.