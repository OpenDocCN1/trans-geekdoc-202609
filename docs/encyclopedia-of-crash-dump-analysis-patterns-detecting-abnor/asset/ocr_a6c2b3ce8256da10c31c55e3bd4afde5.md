```
6 fffffff000eb92a180 fffffff000eb9363c0 ( 0) fffffff000eb9363c0 ................

Child-SP                RetAdr           Call Site
fffffd000`eb935f60 ffffff8001`e5c69e01 nt!KiCheckStall+0x75
fffffd000`eb935f90 ffffff8001`e5c6aa8f nt!KiFreezeTargetExecution+0x231
fffffd000`eb9360a0 ffffff8001`e5bddec2 nt!KiProcessNMI+0x3b
fffffd000`eb9360f0 ffffff8001`e5bdbb36 nt!KxNmiInterrupt+0x82
fffffd000`eb936230 ffffff8001`e5ad2d2f nt!KiNmiInterrupt+0x176
fffffd000`eb93f8e8 ffffff8001`e5bb91a2 hal!HalProcessorIdle+0xf
fffffd000`eb93f8f0 ffffff8001`e5ad7848 nt!PpmIdleDefaultExecute+0xa
fffffd000`eb93f920 ffffff8001`e5ad72a6 nt!PpmIdleExecuteTransition+0x3e8
fffffd000`eb93fb10 ffffff8001`e5bd64bc nt!PoIdle+0x2f6
fffffd000`eb93fc60 00000000`00000000 nt!KiIdleLoop+0x2c
```

```
7 fffffff000eb967180 fffffff000eb9733c0 ( 0) fffffff000eb9733c0 ................

Child-SP                RetAdr           Call Site
fffffd000`eb972f60 ffffff8001`e5c69e01 nt!KiCheckStall+0x75
fffffd000`eb972f90 ffffff8001`e5c6aa8f nt!KiFreezeTargetExecution+0x231
fffffd000`eb9730a0 ffffff8001`e5bddec2 nt!KiProcessNMI+0x3b
fffffd000`eb9730f0 ffffff8001`e5bdbb36 nt!KxNmiInterrupt+0x82
fffffd000`eb973230 ffffff8001`e5ad2d2f nt!KiNmiInterrupt+0x176
fffffd000`eb97c8e8 ffffff8001`e5bb91a2 hal!HalProcessorIdle+0xf
fffffd000`eb97c8f0 ffffff8001`e5ad7848 nt!PpmIdleDefaultExecute+0xa
fffffd000`eb97c920 ffffff8001`e5ad72a6 nt!PpmIdleExecuteTransition+0x3e8
fffffd000`eb97cb10 ffffff8001`e5bd64bc nt!PoIdle+0x2f6
fffffd000`eb97cc60 00000000`00000000 nt!KiIdleLoop+0x2c
```

This command is obviously faster than repeatedly switching to subsequent CPUs using “~s command and then checking the corresponding stack trace (k). It also helps in diagnosing Spiking Threads (page 888) in the kernel and complete memory dumps.