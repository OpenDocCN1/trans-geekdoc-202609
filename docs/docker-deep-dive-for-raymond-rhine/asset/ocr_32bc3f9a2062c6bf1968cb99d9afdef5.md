The long number returned by the command is the network's ID and you'll need it in the next step.

As expected, the command creates a new Docker bridge network called localnet that you can list and inspect with the usual docker commands. However, behind the scenes, it also creates a new Linux bridge in the host's kernel.

Run another brctl show command to see it.

| brctl show | bridge id | STP enabled | interf |
|---|---|---|--|
| bridge name | | | |
| br-f918f1bb0602 | 8000.0242372a886b | no | |
| docker0 | 8000.02425ee84bc | no | |
| docker_gwbridge | 8000.02427abba76b | no | |

The example in the book shows a new bridge called br-f918f1bb0602 with no devices connected. If you look closely at the name, you'll recognize f918f1bb0602 as the first 12 characters from the ID of the new localnet network you just created.

At this point, the bridge configuration on the host looks like Figure 13.9, with three Docker networks and three associated bridges in the host's kernel.