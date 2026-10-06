The procedure is as:

+   Initially make source permanent and make it the current working node. All other nodes are made temporary.

+   Examine all the temporary neighbours of the current working node and after checking the condition for minimum weight, relabel the required nodes.

+   From all the temporary nodes, find out the node which has minimum value of distance, make this node permanent and now is our current working node.

+   Repeat steps 2 and 3 until destination node is made permanent. Suppose the source node is V1

V1 is the current working node.

| Node | Destination | Precedence | Status |
| V1 | 0 | 0 | Permanent |
| V2 | ∞ | 0 | Temporary |
| V3 | ∞ | 0 | Temporary |
| V4 | ∞ | 0 | Temporary |
| V5 | ∞ | 0 | Temporary |
| V6 | ∞ | 0 | Temporary |
| V7 | ∞ | 0 | Temporary |
| V8 | ∞ | 0 | Temporary |

![](bbox=[0.301, 0.526, 0.693, 0.686])

Now we will check the adjacent nodes of V1, which are temporary also.
Here,V2,V3,V4 are adjacent to V1 and are temporary.
V2.distance > V1.distance + distance (V1,V2) ∞ > 0 + 8 relabel V2
V3.distance > V1.distance + distance (V1,V3) ∞ > 0 + 2 relabel V3
V4.distance > V1.distance + distance (V1,V4) ∞ > 0 + 7 relabel V4
Now we will change the precedence and distance of V2, V3, V4

| Node | Destination | Precedence | Status |
| V1 | 0 | 0 | Permanent |
| V2 | 8 | V1 | Temporary |
| V3 | 2 | V1 | Temporary |
| V4 | 7 | V1 | Temporary |