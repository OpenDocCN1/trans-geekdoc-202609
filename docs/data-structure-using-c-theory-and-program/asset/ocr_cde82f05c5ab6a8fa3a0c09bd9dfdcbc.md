# Chapter 7 Graphs

| Node | Destination | Precedence | Status |
| --- | --- | --- | --- |
| V5 | ∞ | 0 | Temporary |
| V6 | ∞ | 0 | Temporary |
| V7 | ∞ | 0 | Temporary |
| V8 | ∞ | 0 | Temporary |

Now from all the temporary nodes find out the node that has the smallest distance from source i.e. smallest value of distance. V3 has the smallest value of distance in all temporary nodes make it permanent and V3 is our current working node.

![](bbox=[0.296, 0.273, 0.703, 0.426])

Adjacent nodes of V3, V4, V7 both are temporary. V4.distance > V3.distance + distance (V3,V4) 7 > 2 + 7 relabel V4 V7.distance > V3.distance + distance (V3,V7) ∞ > 2 + 3 label V3 Now we change the precedence and distance of V4 and V7.

| Node | Destination | Precedence | Status |
| --- | --- | --- | --- |
| V1 | 0 | 0 | Permanent |
| V2 | 8 | V1 | Temporary |
| V3 | 2 | V1 | Permanent |
| V4 | 6 | V3 | Temporary |
| V5 | ∞ | 0 | Temporary |
| V6 | ∞ | 0 | Temporary |
| V7 | 5 | V3 | Temporary |
| V8 | ∞ | 0 | Temporary |

Now from all the temporary nodes V7 has smallest value of distance so make it permanent and now V7 is our current working node.

![](bbox=[0.296, 0.78, 0.703, 0.923])