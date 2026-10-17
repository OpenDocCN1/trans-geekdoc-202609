

This is not the only type of fuzzing, though. Local vulnerabilities may not work on network services. Instead, they may require files to trigger. Peach will work with file‑based fuzzing as well. In this case, you would need a sample file that could be used to manipulate as needed to trigger a crash. Peach would repeatedly open the file with altered data. The monitoring required for this would occur on the same system where the testing was being executed, which is not necessarily the same for network‑based testing.

One of the advantages of a tool like Peach is that you can create your own test plans for protocols you may not have run across, as in the case of performing application testing. However, often, you are working with well‑known protocols. For something like that, you can use Peach and Peach pits that are available or you can use something that may be a little simpler and also already available in Kali Linux. One of these tools is `sfuzz`. There are a handful of template files that are available. One example is the `basic.smtp` file that can be used to test an email server. This is some of the output from running `sfuzz` against a Postfix mail server.

```
===========================================================

[18:01:03] attempting fuzz - 61 (len: 50057).

[18:01:03] info: tx fuzz - (50057 bytes) - scanning for reply.

[18:01:04] read:

220 badmilo.washere.com ESMTP Postfix (Debian/GNU)

250 badmilo.washere.com

===========================================================

[18:01:04] attempting fuzz - 62 (len: 10).

[18:01:04] info: tx fuzz - (10 bytes) - scanning for reply.

[18:01:04] read:

220 badmilo.washere.com ESMTP Postfix (Debian/GNU)

250‑badmilo.washere.com

250‑PIPELINING

250‑SIZE 10240000

250‑VRFY

250‑ETRN

250‑STARTTLS

250‑ENHANCEDSTATUSCODES

250‑8BITMIME

250‑DSN

250‑SMTPUTF8

250‑CHUNKING
```

This shows the responses from the server to mutated input from the fuzzing tool. You can see the differences in output from the server. Without knowing exactly what the input is, it's hard to know why the output has changed. This is one of the challenges with any sort of fuzzing and highlights the challenges that can come from performing fuzzing as a testing strategy.

While you can use tools like Peach and `sfuzz` for remote application fuzzing over the network, you can also use a tool like American fuzzy lop (AFL) to fuzz file formats. This can manipulate file formats to try to cause local crashes. Once you have a local crash, you can identify where the crash occurs in the code as well as the input data that caused the crash. This may allow you to manipulate the input to change the execution path. The program `afl-fuzz`, available in Kali Linux, will automatically assess normal input data to generate test cases based on that.

[/content]

[content]

下面是一个对 PDF 查看器应用程序运行 `afl-fuzz` 的示例。

通常，`afl-fuzz` 要求应用程序在构建时启用插桩（instrumentation），以便在程序执行过程中对其进行管理。如果你无法获取源代码，或者无法构建带有插桩的二进制文件，可以添加 `-n` 标志，这会跳过测试中的该部分，但会导致结果的可靠性降低。

```
kilroy@cutterjohn:~ $ afl-fuzz -t 100000 -n -i pdfs -o pdf-results /usr/local/bin/atril

afl-fuzz++4.04c based on afl by Michal Zalewski and a large online community

[+] afl++ is maintained by Marc "van Hauser" Heuse, Heiko "hexcoder" Eißfeldt, Andrea Fioraldi and Dominik Maier

[+] afl++ is open source, get it at https://github.com/AFLplusplus/AFLplusplus

[+] NOTE: This is v3.x which changes defaults and behaviours - see README.md

[*] Getting to work…

[+] Using exponential power schedule (FAST)

[+] Enabled testcache with 50 MB

[+] Generating fuzz data with a length of min=1 max=1048576

[*] Checking core_pattern…

[!] WARNING: Could not check CPU scaling governor

[+] You have 2 CPU cores and 2 runnable tasks (utilization: 100%).

[*] Setting up output directories…

[+] Output directory exists but deemed OK to reuse.

[*] Deleting old session data…

[+] Output dir cleanup successful.

[*] Checking CPU core loadout…

[+] Found a free CPU core, try binding to #0.

[*] Scanning 'pdfs'…

[*] Scanning 'pdfs/Downloads'…

[+] Loaded a total of 3 seeds.

[*] Creating hard links for all input files…

[*] Validating target binary…

[*] No auto-generated dictionary tokens to reuse.

[*] Attempting dry run with 'id:000000,time:0,execs:0,orig:keyboard-shortcuts-linux.pdf'…

[*] Spinning up the fork server…

[*] Using AFL++ faux forkserver…

[+] All right - fork server is up.
```
