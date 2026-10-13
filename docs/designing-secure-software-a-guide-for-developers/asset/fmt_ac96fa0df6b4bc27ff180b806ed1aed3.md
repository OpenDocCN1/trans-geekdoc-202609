
# Section 1 – Product Description

This document describes a logging component (herein called Logger) that provides standard software event logging facilities to support auditing, system monitoring, and debugging, designed to mitigate risks of inadvertent information disclosure. **Logger will explicitly handle private data within logs so that non-private data can be freely accessed for routine uses. In rare cases when this access level is insufficient, limited access to protected, private log data can be provided, subject to explicit approval and with restrictions to minimize potential exposure.**

*The notion of explicitly handling private data separately within the context of a logging system is an example of security-centric design thinking. Adding this feature to an existing system would be less efficient and require considerable code churn, compared to designing it in from the start.*

# Section 2 – Overview

For baseline project design assumptions, see the documents listed in Section 10.

## 2.1 Purpose

All applications in the datacenter need to log details of important software events, and since these logs potentially contain private data, careful access control needs to be enforced. Logger provides standard components to generate logs, store logs, and enforce appropriate access to authorized staff while maintaining a reliable and **non-repudiable** record of what access does occur. Since the logging, access, and retention requirements of systems vary, Logger operates based on a simple policy configuration that specifies an access policy.

## 2.2 Scope

This document explains the design of the software components of Logger without mandating the choice of implementation language, deployment, or operational considerations.

## 2.3 Concepts

The notion of a filtered view of logs is core to the design. The idea is to allow relatively free inspection of the logs with any private details filtered out, an access level which should suffice for most uses. Additionally, when needed, sensitive data that is logged can be inspected, subject to additional authorization. The access event is logged too, making the fact of inspection auditable. This graduated access lets applications log important private details while still minimizing how that data is exposed for legitimate uses by internal staff. Data so sensitive that it should never appear in logs simply should not be logged in the first place.

For example, web applications routinely log HTTPS requests as a record of system usage and for many other reasons. Often these logs contain private information (including IP addresses, cookies, and much more) that must be captured but is rarely needed. For example, IP addresses are useful when investigating malicious attacks (to identify the origin of an attack), but for other uses are immaterial. A filtered view of logs hides, or “wraps,” private data while showing nonsensitive data. Designated pseudonyms in a filtered view can show that, for instance, the IP addresses of all events labeled “IP7” are identical without disclosing the actual address. Such a filtered view often provides sufficient information for the purposes of monitoring, gathering statistics, or debugging. When that is the case, it’s advantageous to have avoided exposing any private data at all. The logs still contain the full data, and in rare cases when the protected information is required, the unfiltered view is available in a controlled manner with proper authorization.

Suppose that a web application receives a user login attempt which triggers a bug that causes the process to crash. Here is a simplified example of what the log might contain:

```
2022/10/19 08:09:10 66.77.88.99 POST login.htm {user: "SAM", password: ">1<}2{]3[\4/"}
```

The items in this log are: timestamp (not sensitive), IP address (sensitive), HTTP verb and URL (not sensitive), username (sensitive), and password (very sensitive). An investigation potentially needs to consider all this information in order to reproduce the bug, but you don’t want to display this data in plaintext unless absolutely necessary, and then only to authorized agents.

To address the security needs of a wide range of systems, the sensitivity of various kinds of log data should be configurable, and the logging system should only selectively reveal confidential data. For example, as a best practice URLs should not contain sensitive information, but a legacy system might be known to violate this rule of thumb and require protection not usually necessary—which makes the filtered view less useful for some debugging. In the case of a URL, regular expressions could facilitate configuring certain URLs as more sensitive than others.

A filtered view of the previous example log that omits or wraps the sensitive data might look like this:

```
2022/10/19 08:09:10 US1(v4) POST login.htm {user: USER1(3), password: PW1(12)} 
```

The IP address, username, and password are all wrapped as identifiers to hide the data, but the substituted identifiers could be used in context to query other requests with matching values. In this example, `US1` designates an IP address in the US; `USER1` designates the username associated with the event without divulging it specifically; and `PW1` stands for the password submitted. The suffixes in parentheses indicate the format or length of the actual data, adding a hint without revealing specific details: we can see that it’s an IPv4 address, the username has 3 characters, and the password has 12. **For example, if an excessively long password caused a problem, this fact would be apparent from its surprising length alone. Knowing the length of the password leaks a little information but should not be compromising in practice.**

When the filtered view is insufficient for the task at hand, an additional request to unwrap an identifier such as `US1` can be made. This makes seeing the sensitive data an explicit choice, and allows a graduated revealing of data. For example, if only the IP address is needed, the username and password values remain undisclosed.

## 2.4 Requirements

Logs are reliably stored, immediately accessible with authorization, and destroyed after the required retention period. To support high volumes of use, the log capture interface must be fast, and once it reports success, the generating application is rightly assured that the log is stored.

Logs can be monitored without knowledge of private details, so a filtered log view can be made widely available for most uses, with special authorization needed to see the full data (including private data) only when strictly necessary.

An important goal of this design is to allow the logging of very sensitive private data that can be made available for investigating possible security incidents or, in rare cases, debugging issues that only occur in production. Complete mitigation against an insider attack is an impractical goal, but it’s important to take all reasonable precautions and preserve a reliable audit trail as a deterrent.

Storage for logs is encrypted to protect against leaks if the physical media is stolen.

Software generating logs is fully trusted; it must correctly identify private data in order for Logger to handle it correctly.

## 2.5 Non-Goals

As Logger is intended for use by admins, a slick UI is unnecessary.

**Insider attacks such as code tampering or abuse of admin root privilege are out of scope.**

**To be effective, Logger requires careful configuration and oversight. How this is implemented must be defined by system management but should include a review process and auditing with checks and balances.**

## 2.6 Outstanding Issues

# Section 3 – 6.3 Event Log Request

# Section 4 – 6.4 Goodbye Request

# Section 5 – Section 7 – User Interface Design

# Section 6 – Section 8 – Technical Design

# Section 7 – Section 9 – Configuration

# Section 8 – Section 10 – References
