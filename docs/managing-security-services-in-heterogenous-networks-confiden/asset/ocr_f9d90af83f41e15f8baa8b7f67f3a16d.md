![](bbox=[0.219, 0.078, 0.781, 0.205])

Figure 3.11 CF Computation.

+   3. After receiving the RREQ packet, each intermediate node evaluates \(\mu\). It forwards the RREQ packet if \(\mu > \tau\). Otherwise, it drops the request.
+   4. In traveling, the RREQ packet multiplies the DOTs for all nodes through which it has come across.
+   5. The destination node accepts the RREQ packet with the highest DOT and gives a reply.

# QTFPN routing with an example topology:

In Figure 3.12(a), the example MANET topology is shown with eight nodes, where 1, 8 are source and destination nodes. In Figure 3.12(b), the same MANET is modeled as a DFPN. Here, the source has five alternative paths to the destination node, i.e. 1-2-5-8, 1-3-5-8, 1-3-6-8, 1-4-6-8 and 1-4-7-8. But the route 1-4-6-8 is not valid due to \(\mu < \tau\). Next, the DoT value of route 1-2-5-8 is evaluated as.

```
(1 x 0.8) > 0.3 => 0.8
(0.8 x 0.7) > 0.4 => 0.56
(0.56 x 0.8) > 0.3 => 0.448
```

Likewise, we can evaluate the DoT values for the remaining three paths as 0.576, 0.567, and 0.448, respectively. Here, the path 1-3-5-8 has the maximum DoT; hence, the destination chooses this path.

# 3.4.3 Dempster-Shafer Theory

Dempster-Shafer theory [3] is the mathematical aggregation function. A node uses DST to aggregate multiple trust recommendations