# Windows

After looking at one dump where all thread environment blocks were zeroed, import table was corrupt and recalling some similar cases encountered previously we came up with the next pattern: Lateral Damage.

When this problem happens, we don’t have much choice, and our first temptation is to apply **Alien Component** anti-pattern<sup>124</sup> unless our module list is corrupt and we have a manifestation of another common pattern **Corrupt Dump** (page 137).

An anti-pattern is not always a bad solution if complemented by subsequent verification and backed by experience. If we get a damaged process and thread structures, we can point to a suspicious component (supported by some evidence from the raw stack analysis and educated guess) and then request additional crash dumps in hope to get less damaged process space or see that component again. At the very end, if removing suspicious component stabilizes the customer environment it proves that we were right.

# Comments

Sometimes we get some vital information missing for default or usual analysis techniques, and we need to seek other ways to look at memory dump data - this is the essence of **Lateral Damage** pattern.

In the case of process memory dumps where `.ecxr` doesn’t work we may try `.exr -1` to display the last exception record which may show an exception address, code, and parameters (such as a write or read address).

```
```
0: ???> ~0s
...
WARNING: Many commands will not work
...
0:000>.ecxr
Unable to get exception context, HRESULT 0x80004005

0:000>.exr -1
ExceptionAddress: ...(ModuleA!func+offset)
```
```