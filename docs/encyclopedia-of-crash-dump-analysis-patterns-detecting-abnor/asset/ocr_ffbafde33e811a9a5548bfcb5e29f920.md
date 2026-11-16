# Mac OS X

This pattern was introduced in *Accelerated Mac OS X Core Dump Analysis* training. Basically, it is a thread that is not waiting or suspended (most threads are). However, from a memory dump it is not possible to find out whether it was **Spiking Thread** (page 885) at the dump generation time (unless we have a set of memory snapshots and in each one we have the same or similar backtrace) and we don't have any **Paratext** (page 780) with CPU consumption stats for threads. For example, in one core dump we have these threads:

```
(gdb) info threads
12 0x98c450e0 in __workq_kernreturn ()
11 0x98c428e0 in semaphore_wait_trap ()
10 0x98c448e2 in __psynch_cvwait ()
9 0x00110171 in std::??_R?btreeint, std::pair<int const, _iCapture*>, std::_Select1st<std::pair<int const, _iCapture*> >, std::less<int>, std::allocator<std::pair<int const, _iCapture*> > >::find ()
8 0x98c428e6 in mach_wait_until ()
7 0x98c448e2 in __psynch_cvwait ()
6 0x98c427d2 in mach_msg_trap ()
5 0x98c427d2 in mach_msg_trap ()
4 0x98c428e6 in mach_wait_until ()
3 0x98c427d2 in mach_msg_trap ()
2 0x98c459ae in kevent ()
* 1 0x014bcee0 in cgGLGetLatestProfile ()
```

Threads #9 and #1 are not waiting so we inspect their back traces:

```
(gdb) bt
#0 0x014bcee0 in cgGLGetLatestProfile ()
#1 0x99060dd5 in exit ()
#2 0x001ef859 in os_exit ()
#3 0x001dc873 in luad_precall ()
#4 0x001e7d9e in luaV_execute ()
#5 0x001dc18b in luaD_rawrunprotected ()
#6 0x001dced4 in lua_resume ()
#7 0x0058a526 in ticluaManager::executeProgram ()
#8 0x005aa9af in ticluaScript::execute ()
#9 0x003a6480 in darcScript::execute ()
#10 0x003af4d8 in darcTimeline::execute ()
#11 0x0034a2ba in darcSequenceur::executeAll ()
#12 0x0036904b in darcEventManager::ExecuteEventHandler ()
#13 0x003a37d2 in darcScene::process ()
#14 0x0034a2ba in darcSequenceur::executeAll ()
#15 0x0036904b in darcEventManager::ExecuteEventHandler ()
#16 0x00343ec0 in darcContext::process ()
#17 0x00347339 in darcContext::main ()
#18 0x003cf73d in darcPlayerImpl::renderOneFrame ()
#19 0x003cf078 in darcPlayerImpl::render ()
#20 0x000b1f6f in Run ()
```