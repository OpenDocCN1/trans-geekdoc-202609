```
0: kd> dt _DISPATCHER_HEADER 89b87770
nt!_DISPATCHER_HEADER
   +0x000 Type             : 0xb0 ""
   +0x001 Absolute         : 0xb0 ""
   +0x001 NpxIrql          : 0xb0 ""
   +0x002 Size             : 0xd0 ""
   +0x002 Hand             : 0xd0 ""
   +0x003 Inserted         : 0xba ""
   +0x003 DebugActive      : 0xba ""
   +0x000 Lock             : -1160728400
   +0x004 SignalState      : 0
   +0x008 WaitListHead     : _LIST_ENTRY [ 0x0 - 0x0 ]
```

Now comes some counterfactual thinking. One possible scenario for a bugcheck: after `KeWaitForMultipleObjects` was called to wait for both objects to become signalled (3rd WAIT_TYPE parameter) the free pool slot was allocated or coalesced with `SignalState` becoming nonzero by coincidence and other members becoming random values and then the second normal object becomes signalled when another thread sets the notification event.