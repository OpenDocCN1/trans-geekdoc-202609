
## Cookies

Cookies are text files that are stored on a user’s hard drive or in a user’s memory. These files store information on the user’s Internet habits, including browsing and spending information. Because a website’s servers actually determine how cookies are used, malicious sites can use cookies to discover a large amount of information about a user. While the information retained in cookies on a hard drive usually does not include any confidential information, attackers can use those cookies to obtain information about users that can help them develop better-targeted attacks. For example, if the cookies reveal to an attacker that a user accesses a particular bank’s public website on a daily basis, that action can indicate that a user has an account at that bank, and the attacker may attempt a phishing attack using an email that appears to come from the user’s legitimate bank.

Many antivirus and anti-malware applications include functionality that allows you to limit the type of cookies downloaded and to hide `personally identifiable information` (`PII`), such as email addresses. Often these types of safeguards end up being more trouble than they are worth because they often affect legitimate Internet communication. When creating web applications, thought should be given to the secure storage of cookies. Cookies should be encrypted. Also, cookies to be stored on the client should not contain essential information. Any cookie that does should be stored on the server, and a pointer should be provided on the client to the cookie on the server.

## Buffer overflow

Buffers are portions of system memory that are used to store information. A buffer overflow is an attack that occurs when the amount of data that is submitted to data is larger than the buffer can handle. Typically, this type of attack is possible because of poorly written application or operating system code. This can result in an injection of malicious code, primarily either a `denial-of-service` (`DoS`) attack or an SQL injection. To protect against this issue, organizations should ensure that all operating systems and applications are updated with the latest service packs and patches. In addition, programmers should properly test all applications to check for overflow conditions.

Hackers can take advantage of this phenomenon by submitting too much data, which can cause an error or, in some cases, execute commands on the machine if the hacker can locate an area where commands can be executed. Not all attacks are designed to execute commands. An attack may just lock the computer as a DoS attack. A packet containing a long string of `no-operation` (`NOP`) instructions followed by a command usually indicates a type of buffer overflow attack called an NOP slide. The purpose of this type of attack is to get the CPU to locate where a command can be executed.

With proper input validation, a buffer overflow attack causes an access violation. Without proper input validation, the allocated space is exceeded, and the data at the bottom of the memory stack is overwritten. The key to preventing many buffer overflow attacks is input validation, in which any input is checked for format and length before it is used. Buffer overflows and boundary errors (when input exceeds the boundaries allotted for the input) are a family of error conditions called `input validation errors`.

## Memory leaks

Applications use memory to store resources, objects, and variables. When an application mismanages the memory it has been assigned by the operating system, several things can occur. One is that over time, by not returning the allocated memory to the operating system, memory is exhausted. In addition, objects that have been stored in memory may become inaccessible to the application. Fixing a memory leak usually involves adding or replacing some code to free the memory in the questionable code path.

## Integer overflows

Integer overflow occurs when math operations try to create a numeric value that is too large for the available space. The register width of a processor determines the range of values that can be represented. Moreover, a program may assume that a variable always contains a positive value. If the variable has a signed integer type, an overflow can cause its value to wrap and become negative. This may lead to unintended behavior. Similarly, subtracting from a small unsigned value may cause it to wrap to a large positive value, which may also be an unexpected behavior. Mitigate integer overflow attacks by implementing the following:

*   Using strict input validation.
*   Using a language or compiler that performs automatic bounds checks.
*   Choosing an integer type that contains all possible values of a calculation. This reduces the need for integer type casting (changing an entity of one data type into another), which is a major source of defects.

## Race conditions

A race condition is an attack in which the hacker inserts himself between instructions, introduces changes, and alters the order of execution of the instructions, thereby altering the outcome.

## Time of check/time of use

A type of race condition is time of check to time of use. In this attack, a system is changed between a condition check and the display of the check’s results. For example, consider the following scenario:

At 10:00 a.m., a hacker was able to obtain a valid authentication token that allowed read/write access to the database. At 10:15 a.m., the security administrator received alerts from the `intrusion detection system` (`IDS`) about a database administrator performing unusual transactions. At 10:25 a.m., the security administrator reset the database administrator’s password. At 11:30 a.m., the security administrator was still receiving alerts from the IDS about unusual transactions from the same user. In this case, a race condition was created by the hacker disturbing the normal process of authentication. The hacker remained logged in with the old password and was still able to change data. Countermeasures to these attacks include the following:

*   Make critical sets of instructions to either execute in order and in entirety or roll back or prevent the changes.
*   Have the system lock access to certain items it will access when carrying out these sets of instructions.

## Resource exhaustion

Resource exhaustion occurs when a computer is out of memory or CPU cycles. Memory leaks are an example of resource exhaustion, in that, eventually memory is insufficient to perform tasks. Resource exhaustion is also the goal of DoS attacks. In these attacks, the target is asked to perform some function so many times that it is overwhelmed and has no memory or CPU cycles left to perform normal activities. To prevent or minimize the effects of attacks that attempt to exhaust resources, the following must be implemented:

*   Harden client machines that may be recruited for attacks that exhaust resources (for example, `distributed DoS` [`DDoS`] attacks).
*   Ensure that all machines are up-to-date on security patches.
*   Regularly scan machines to detect anomalous behavior.

## Geotagging

Geotagging is the process of adding geographic metadata to various media, including photographs, videos, websites, SMS messages, or RSS feeds. This data usually consists of latitude and longitude coordinates, though it can also include altitude, bearing, distance, accuracy data, and place names. Some consider geotagging a security risk because of the information it can disclose when geotagged files are uploaded, especially to social media. In some cases, information such as the location, time of day, and where you live may be included. Measures you can take to reduce the security risk of geotagging are as follows:

*   Disable geotagging on smartphones.
