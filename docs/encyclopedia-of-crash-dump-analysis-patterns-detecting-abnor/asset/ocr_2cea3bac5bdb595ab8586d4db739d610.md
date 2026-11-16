# Stack Trace Signature

Stack traces resemble functions: they have prolog, body, and epilog. Frame trace is also similar to trace Partition analysis pattern^202. Bottom stack subtrace plays the role of prolog, for example, thread initialization and RPC call stub dispatch. Middle stack subtrace plays the role of body or core, for example, application specific function calls invoked by RPC. Top stack subtrace plays the role of epilog, for example, system calls. Such stack trace partition is useful for stack trace matching, especially when symbols are not available. In such a case Stack Trace Signature of module names and their frame counts may help (together with Crash Signature where appropriate, page 153):

![](bbox=[0.19, 0.265, 0.515, 0.745])

```
T<name_i, p>

M<name_i, p>
M<name_j, r>
M<name_k, s>
...

B<name_i, p>
B<name_j, r>
...
```