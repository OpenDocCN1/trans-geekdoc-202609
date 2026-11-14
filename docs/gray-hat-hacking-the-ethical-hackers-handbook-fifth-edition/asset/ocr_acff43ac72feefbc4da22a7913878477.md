Here is an example of naming the variable CryptAcquireContextA:

```
.data:1000D93C ; BOOL __stdcall CryptAcquireContextA(
 HCRYPTPROV *phProv, LPCSTR pszContainer, LPCSTR pszProvider,
 DWORD dwProvType, DWORD dwFlags)
.data:1000D93C CryptAcquireContextA dd 0
```

Although this prototype might look correct, it won't allow IDA to propagate argument names in the disassembly and will result in a somewhat messy decompiler representation.
The issue here is that the automatic type assigned to the variable by IDA is a function declaration instead of a function pointer. To fix the variable's type, remember to change it to a function pointer by wrapping the function name in curly braces and adding a pointer (*) in front of the name, as follows:

```
(*CryptAcquireContextA)
```

To identify the CSP, we continue with looking at cross-references of
CryptAcquireContextA and will analyze a function at .text:10003A80. Having annotated
the function pointer, we can easily identify the names of arguments and find the value of
the pszProvider argument:

```
.text:10003A92      push 18h              ; dwProvType

.text:10003A94      ; "Microsoft Enhanced RSA and AES Cryptographic Provider"
.text:10003A94      and eax, offset aMicrosoftEnhan
.text:10003A99      push eax              ; pszProvider
.text:10003A9A      push 0                ; pszContainer
.text:10003A9C      push edi              ; phProv
.text:10003A9D      call CryptAcquireContextA
```

The CSP used by malware supports the AES and RSA algorithms. We already identified
AES constants in the sample, so this is just another confirmation that this algorithm is used
in some form, either for encryption, decryption, or both. The usage of RSA hasn't been
confirmed yet, so the next step is to understand how this cryptographic provider is used.
We continue by analyzing XREFs of the current function and will look at sub_10003AC0.
Because this function likely contains crypto-related logic, we need to understand the code
and all surrounding functions.

In situations like this where an in-depth understanding of a function is necessary, a top-
down approach makes the most sense. In this case, all functions are very simple wrappers
around APIs, so we won't go into many details. Shown next is an IDA proximity view of
the functions called from sub_10003AC0, which has been renamed InitializeKeys.