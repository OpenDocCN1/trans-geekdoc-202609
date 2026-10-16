
After `a`'s return address is placed on the stack, the processor stores `b`'s local data there. [Table 7.7](#c07.xhtml#c07-tbl-0007) shows the state of the stack before the processor executes the first instruction in `b`.

[**Table 7.7**](#c07.xhtml#R_c07-tbl-0007): Program stack after calling *`b`*

| **STACK** |

| --- |

|   |

|   |

|   |

| `b'local data` |

| `a's return address` |

| `a's local data` |

|   |

Like `a`, `b` will declare its local variables and then make a call to another function, `c`. When executing this call, a return address for `b` will be placed on the stack as well as the local variables of the called function. Once this setup for `c` is complete, the stack will resemble [Table 7.8](#c07.xhtml#c07-tbl-0008).

[**Table 7.8**](#c07.xhtml#R_c07-tbl-0008): Program stack after calling *c*

| **STACK** |

| --- |

|   |

| `c' local data` |

| `b'sreturn address` |

| `b's local data` |

| `a's return address` |

| `a's local data` |

|   |

In `c`, the local variable *`x`* is declared, and then the function terminates. When the processor is done in `c`, code flow needs to `return` to the calling function `b`.

At this point, `c`'s local data is at the top of the stack but is no longer needed. The processor can pop this data from the stack, changing the stack pointer to indicate `b`'s return address.

The processor can then pop this return address off of the stack, storing it in *`eip`* and updating the stack pointer through the *`ret`* instruction. This enables the program to `return` to `b` and resume executing any code following its call to `c`. At this point, the stack returns to the state shown in [Table 7.7](#c07.xhtml#c07-tbl-0007).

The call to `c` is the last instruction in `b`, so it will immediately `return` as well. Like the `return` from `c`, this involves popping local variables off of the stack and updating *`eip`* by popping `a`'s return address off of the stack and into *`eip`* (via *`ret`* ). Once this is complete, the stack will resemble [Table 7.6](#c07.xhtml#c07-tbl-0006).

After this return from `b`, `a` will also return. `a`'s local data will be popped off of the stack. Then, the *`eip`* register will be updated based on the return address of the calling function, which occurred prior to our analysis and is not shown in [Table 7.6](#c07.xhtml#c07-tbl-0006), and execution will resume within that function.

### Stack Analysis

As functions are called and return from calls, they have an impact on the program stack. For example, consider the following code:

```
void a() { }
void b() { }
void c() { a(); b(); }
```

This code defines three functions, `a`, `b`, and `c`, and `c` calls both of the other two.

When a function is running or is within the call stack of the running function, its return address is in the stack. For example, when `a` is running, the return addresses for `a` and `c` are on the stack. Similarly, when `b` is running, the return addresses for `b` and `c` are on the stack.

Examination of the return addresses stored on the stack provides visibility into how a particular point in the program was reached. Each function in the call stack will have its return address local variables and scratch data visible in the stack.

This practice is called *unwinding* the stack. In `gdb`, the `info stack` command will show the current state of the stack.

### Calling Conventions

The `call` and `ret` instructions make it possible to create functions in assembly. However, with only `call` and `ret`, these functions must be self-contained without the ability to pass data between functions.

In higher-level programming languages, functions commonly have parameters or arguments, which are variables that are passed to a function by the calling function. However, machine code doesn't have the concept of parameters; there are only registers and memory.

x86 has all of the tools necessary to create parameters. Higher-level programming languages that use parameters are translated into assembly. It's the responsibility of the programmer or the compiler to choose how to use these tools.

#### *Why Conventions Are Necessary*

With registers, the stack, and even memory locations, x86 has the ability to pass values from one function to another. Parameters can be stored in registers or pushed and popped from the stack.

However, communication or agreements between functions is necessary if they plan to use parameters, registers, or the stack in a consistent way. If the calling function is using certain locations to pass parameters, the callee needs to know which locations are used for which values. The same is true if the callee is returning data to the caller.

```
void caller() {   … callee()} //nomenclature definition
```

Also, if the caller is using a register to store its internal values, the callee needs to know not to overwrite those values. This is especially a concern if the callee uses operations like `mul` that modify registers but are easy to miss.

Within a small program, the developer could design their code to contain that knowledge. If function `a` takes three parameters, the developer could create a scheme that passes them via registers or the stack. Similarly, the struct needed by function `b` could be passed by allocating a particular location in memory.

However, while this approach may work on a small scale, it is unscalable and prone to error. An oversight could result in vital data being accidentally clobbered by a `mul` operation. Also, such an ad hoc scheme makes it more difficult to work with teams of developers.

#### *Introduction to Calling Conventions*

*Calling conventions* are designed to make it easier to pass data between functions by defining the rules of engagement between functions. They are part of the application binary interface (ABI), which is the lowest-level definition of how pieces of code interact.

A calling convention must define a few rules, including the following:

*   **Parameter location:** Where will parameters be passed from the caller to the callee (stack versus registers)?

*   **Parameter ordering:** How will parameters be organized, on the stack or into registers?

*   **Stack cleanup:** If the stack is used, which function is responsible for removing values from the stack (caller versus callee cleanup)?

*   **Register access:** Which registers can the callee use without needing to back up their previous values and restore them before returning?

*   **Return values:** Where and how will values be returned from the callee to the caller?

Calling conventions can vary based on different factors, including the following:

*   Architecture (x86 versus ARM)

*   Operating system (UN\*X versus Windows)

*   Programming language (C versus Java)

*   Even compiler (GCC versus Microsoft)

In the early days of programming, standards didn't really exist. As a result, programs couldn't work together if their developers didn't agree on a calling convention.

Initially, there were many different companies, each with its own conventions. Over time, these have been whittled down to a handful of popular standards, including the following:

*   `cdecl`

*   `syscall`

*   `optlink`

*   `pascall`

*   `register`

*   `stdcall`

*   `fastcall`

*   `safecall`

*   `thiscall`

### cdecl

`cdecl` (“see deckel”) is short for “C declaration” and is one of the most common calling conventions on the x86 architecture. While it originated with C, `cdecl` is used for a variety of different programming languages and architectures. It is also a useful standard when writing assembly by hand.

`cdecl` defines the following rules:

*   **Stack-based parameters:** Arguments are pushed from right to left onto the stack to be passed to the callee.

*   **Caller cleanup:** The calling function is responsible for removing arguments from the stack once the callee returns.

*   **Return value:** The *`eax`* register is used to hold a function's return value.
