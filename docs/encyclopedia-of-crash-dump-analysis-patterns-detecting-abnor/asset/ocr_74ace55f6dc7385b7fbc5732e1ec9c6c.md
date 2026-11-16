# Double Free

# Kernel Pool

In contrast to **Double Free** pattern (page 267) in a user mode process heap double free in a kernel mode pool results in an immediate bugcheck in order to identify the driver causing the problem (BAD_POOL_CALLER bugcheck with Arg1 = = 7):

```
2: kd> !analyze -v
...
...
...
BAD_POOL_CALLER (c2)
The current thread is making a bad pool request. Typically this is at a bad IRQL level or double freeing the same allocation, etc.
Arguments:
Arg1: 00000007, Attempt to free pool which was already freed
Arg2: 0000121a, (reserved)
Arg3: 02140001, Memory contents of the pool block
Arg4: 89ba74f0, Address of the block of pool being deallocated
```

If we look at the block being deallocated we would see that it was marked as “Free” block:

```
2: kd> !pool 89ba74f0
Pool page 89ba74f0 region is Nonpaged pool
89ba7000 size: 270 previous size: 0 (Allocated) Thre (Protected)
89ba7270 size: 8 previous size: 270 (Free) ...
89ba7278 size: 18 previous size: 8 (Allocated) ReEv
89ba7290 size: 80 previous size: 18 (Allocated) Mdl
89ba7310 size: 80 previous size: 80 (Allocated) Mdl
89ba7390 size: 30 previous size: 80 (Allocated) Vad
89ba73c0 size: 98 previous size: 30 (Allocated) File (Protected)
89ba7458 size: 8 previous size: 98 (Free) Wait
89ba7460 size: 28 previous size: 8 (Allocated) FSfm
89ba74a0 size: 40 previous size: 18 (Allocated) Ntfr
89ba74e0 size: 8 previous size: 40 (Free) File
*89ba74e8 size: a0 previous size: 40 (Free ) *ABCD
Owning component : Unknown (update pooltag.txt)
89ba7588 size: 38 previous size: a0 (Allocated) Sema (Protected)
89ba75c0 size: 38 previous size: 38 (Allocated) Sema (Protected)
89ba75f8 size: 10 previous size: 38 (Free) Nbtl
89ba7608 size: 98 previous size: 10 (Allocated) File (Protected)
89ba76a0 size: 28 previous size: 98 (Allocated) Ntfn
89ba76c8 size: 40 previous size: 28 (Allocated) Ntfr
89ba7708 size: 28 previous size: 40 (Allocated) Ntfs
89ba7730 size: 40 previous size: 28 (Allocated) Ntfr
89ba7770 size: 40 previous size: 40 (Allocated) Ntfr
89ba7a10 size: 270 previous size: 260 (Allocated) Thre (Protected)
89ba7c80 size: 20 previous size: 270 (Allocated) VadS
```

The pool tag is a 4-byte character sequence used to associate drivers with pool blocks and is useful to identify a driver allocated or freed a block. In our case, the pool tag is ABCD, and it is associated with the