# TABLE 11.1 Function calls structured as a stack in memory

| Function | Counter | Address |
|---|---|---|
| countDown | 9 | 82994EE80 |
| countDown | 8 | 82994EF00 |
| countDown | 7 | 82994EF80 |
| countDown | 6 | 829948100 |
| countDown | 5 | 829948180 |
| countDown | 4 | 829948200 |
| countDown | 3 | 829948280 |
| countDown | 2 | 829948300 |
| countDown | 1 | 829948380 |

Each recursive call generates an activation record until the counter is 1. Generating activation records as such entails more memory than an iterative or non-recursive function.

Unlike an iterative algorithm, which re-executes its statements within each cycle, recursion generally puts the operational elements from all successive recursive calls on the stack, ahead