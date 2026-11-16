use of ASLR.

Other defenses for buffer overflows include code reviews, using safe programming languages, and applying patches and updates in a timely manner. Finally, because all data should be suspect by default, data being input, processed, or output should be checked to make sure it matches the correct parameters.

# # Backdoors

Backdoors are potential threats to the security of systems and software. Programmers use backdoors, which are also sometimes referred to as maintenance hooks, during development to allow easy access to a piece of software. Often these backdoors are undocumented. A backdoor can be used when software is developed in sections and developers want a means of accessing certain parts of the program without having to run through all the code. If backdoors are not removed before the release of the software, they can allow an attacker to bypass security mechanisms and access the program.

# # State Attacks

A state attack is a form of attack that typically targets timing. The objective is to exploit the delay between the time of check (TOC) and the time of use (TOU). These attacks are sometimes called asynchronous attacks or race conditions because the attacker races to make a change to the object after it has been checked but before the system uses it.

For example, if a program creates a date file to hold the amount a customer owes, and the attacker can race to replace this value before the program reads it, he can successfully manipulate the program. In reality, it can be difficult to exploit a race condition because a hacker might have to attempt to exploit the race condition many times before succeeding.

# # Covert Channels

Covert channels provide a means of moving information in a manner that was not intended. Covert channels are a favorite of attackers because they know that you cannot deny what you must permit. The term was originally used in TCSEC documentation to refer to ways of transferring information