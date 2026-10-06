# CHAPTER 11 IMPROVING THE DEVELOPER EXPERIENCE

Offering a CLI tool expands the reach of an API beyond full-time developers to automation engineers who are better equipped to write shell scripts rather than applications to integrate with APIs. CLI tools may offer human-friendly output, in addition to JSON, CSV, or other output formats that support better automation and tool chaining.

Designing a CLI tool that wraps an API is no different than designing the API itself. It requires understanding the desired outcomes, activities, and steps required to accomplish the jobs to be done (JTBD). Then, design the CLI interface to meet these outcomes. The following code block shows how a CLI interface could be designed to support the Shopping API designed in previous chapters:

```
$ bookcli books search "DDD"
```

| Title | Authors | Book ID |
| --- | --- | --- |
| Implementing Domain-Driven | Vaughn Vernon | 12345 |

```
$ bookcli cart add 40321834577

Success!

$ bookcli cart show
```

Cart Summary:

| Total | Estimated Sales Tax |
| --- | --- ----
| $42.99 USD | $3.44 USD | |

Cart Items:

| Title | Price | Qty | Book ID |
| --- | --- | --- | --- |
| Implementing Domain-Driven | $42.99 USD | 1 | 12345 |

```
$ ...
```