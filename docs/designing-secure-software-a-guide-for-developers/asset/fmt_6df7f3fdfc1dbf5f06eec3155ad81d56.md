
Even if your regex is correctly constructed it can cause security issues, as some regular expressions are prone to excessive execution times, and if attackers can trigger these they can cause a serious DoS. Specifically, execution time can balloon if the regex incurs *backtracking*—that is, when it scans forward a long way, then needs to go back and rescan over and over to find a match. The security danger generally results from allowing untrusted inputs to specify the regex; or, if the code already contains a backtracking regex, from an untrusted input that supplies a long worst-case string that maximizes the computational effort.

A backtracking regex can look innocuous, as an example will demonstrate. The following Python code takes more than three seconds to run on my modest Raspberry Pi Model 4B. Your processor is likely much faster, but since each `D` added to the 24 in the example doubles the running time, it isn’t hard to lock up any processor with a slightly longer string:

```
import re
print(re.match(r'(D+)+$', 'DDDDDDDDDDDDDDDDDDDDDDDD!')) 
```

The danger of excessive runtime exists with any kind of parsing of untrusted inputs, in cases where backtracking or other nonlinear computations can blow up. In the next section you’ll see an XML entity example along these lines, and there are many more.

The best way to mitigate these issues depends on the specific computation, but there are several general approaches to countering these attacks. Avoid letting untrusted inputs influence computations that have the potential to blow up. In the case of regular expressions, don’t let untrusted inputs define the regex, avoid backtracking if possible, and limit the length of the string that the regex matches against. Figure out what the worst-case computation could be, and then test it to ensure that it’s not excessively slow.

### Dangers of XML

XML is one of the most popular ways to represent structured data, as it is powerful as well as human-readable. However, you should be aware that the power of XML can also be weaponized. There are two major ways that untrusted XML can cause harm using XML entities.

*XML entity declarations* are a relatively obscure feature, and unfortunately, attackers have been creative in finding ways of abusing these. In the example that follows, a named entity `big1` is defined as a four-character string. Another named entity, `big2`, is defined as eight instances of `big1` (a total of 32 characters), and `big3` is eight more of those, and so on. By the time you get up to `big7`, you’re dealing with a megabyte of data, and it’s easy to go on up from there. This example concocts an 8-megabyte chunk of XML. As you can see, you would need to add only a few lines to go into the gigabytes:

```
<!DOCTYPE dtd[
  <!ENTITY big1 "big!">
  <!ENTITY big2 "&big1;&big1;&big1;&big1;&big1;&big1;&big1;&big1;">
  <!ENTITY big3 "&big2;&big2;&big2;&big2;&big2;&big2;&big2;&big2;">
  <!ENTITY big4 "&big3;&big3;&big3;&big3;&big3;&big3;&big3;&big3;">
  <!ENTITY big5 "&big4;&big4;&big4;&big4;&big4;&big4;&big4;&big4;">
  <!ENTITY big6 "&big5;&big5;&big5;&big5;&big5;&big5;&big5;&big5;">
  <!ENTITY big7 "&big6;&big6;&big6;&big6;&big6;&big6;&big6;&big6;">
]>
<mega>&big7;&big7;&big7;&big7;&big7;&big7;&big7;&big7;</mega>
```

More tricks are possible with external entity declarations. Consider the following:

```
  <!ENTITY snoop SYSTEM "file:///etc/passwd>" >
```

This does exactly what you would think: reads the password file and makes its contents available wherever `&snoop;` appears in the XML henceforth. If the attacker can present this as XML and then see the result of the entity expansion, they can disclose the contents of any file they can name.

Your first line of defense against these sorts of problems will be keeping untrusted inputs out of any XML that your code processes. Some modern libraries check for just this kind of attack, but you should check to be sure if you need to rely on it. If you don’t need XML external entities, then protect against this sort of attack by excluding them from inputs, or by disabling the processing of such declarations.

## Mitigating Injection Attacks

Just as various kinds of injection attacks rely on the common trick of using untrusted inputs to influence statements or commands that execute in the context of the application, mitigations for these issues also have common threads, though the details do vary. Input validation is always a good first line of defense, but depending on what allowable inputs may consist of, that alone is not necessarily enough.

Avoid attempting to insert untrusted data into constructed strings for execution, for instance as commands. Modern libraries for SQL and other functionality susceptible to injection attacks should provide helper functions that allow you to pass in data separately from the command. These functions handle quoting, escaping, or whatever it takes to safely perform the intended operation for all inputs. I recommend checking for a specific note about security in the library’s documentation, as there do exist slipshod implementations that just slap strings together and will be liable to injection attacks under the facade of the API. When in doubt, a security test case (see Chapter 12) is a good way to sanity-check this.

If you cannot, or will not, use a secure library—although, again, I caution against the slippery slope of “what could possibly go wrong?” thinking—first consider finding an alternative way to avoid the risk of injection. Instead of constructing a \*nix `ls` command to enumerate the contents of a directory, use a system call. The reasoning behind this is clear: all that `readdir(3)` can possibly do is return directory entry information; by contrast, invoking a shell command could potentially do just about anything.

Using the filesystem as a homemade datastore may be the quickest solution in some cases, but I can hardly recommend it as a secure approach. If you insist on doing it the risky way, don’t underestimate the work required to anticipate and then block all potential attacks in order to fully secure it. Input validation is your friend here; if you can constrain the string to a safe character set (for example, names consisting only of ASCII alphanumerics), then you may be all right. As an additional layer of defense, study the syntax of the command or statement you are forming and be sure to apply all the necessary quoting or escaping to ensure nothing goes wrong. It’s worth reading the applicable specifications carefully, as there may be obscure forms you are unaware of.

The good news is that the dangerous operations where injections become a risk are often easy to scan for in source code. Check that SQL commands are safely constructed using parameters, rather than as ad hoc strings. For shell command injections, watch for uses of `exec(3)` and its variants, and be sure to properly quote command arguments (Python provides `shlex.quote` for exactly this purpose). In JavaScript, review uses of `eval` and either safely restrict them or consider not using it when untrusted inputs could possibly influence the constructed expression.

This chapter covered a number of injection attacks and related common vulnerabilities, but injection is a very flexible method that can appear in many guises. In the following chapter we will see it again (twice), in the context of web vulnerabilities.

# 11 Web Security

> When the words appeared, everyone said they were a miracle. But nobody pointed out that the web itself is a miracle.
>
> —E. B. White (from *Charlotte’s Web*)

![](Images/chapterart.png)
