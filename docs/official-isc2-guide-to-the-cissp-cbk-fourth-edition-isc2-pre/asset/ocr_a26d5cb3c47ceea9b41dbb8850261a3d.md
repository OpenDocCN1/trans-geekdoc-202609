that material can contain features quite apart from the content and meaning.

It may seem strange to use meaningless features as evidence. However, Richard Forsyth reported on studies and experiments that found that short substrings of letter sequences can be effective in identifying authors. Even a relative count of the use of single letters can be characteristic of authors.

Certain message formats may provide additional information. A number of Microsoft email systems include a data block with every message that is sent. To most readers, this block contains meaningless garbage. However, it may include a variety of information, such as part of the structure of the file system on the sender’s machine, the sender’s registered identity, programs in use, and so forth.

Other programs may add information that can be used. Microsoft’s word processing program, Word, for example, is frequently used to create documents sent by email. Word documents include information about file system structure, the author’s name (and possibly company), and a global user ID. This ID was analyzed as evidence in the case of the Melissa virus. MS Word can provide even more data. Comments and "deleted" sections of text may be retained in Word files and simply marked as hidden to prevent them from being displayed. Simple utility tools can recover this information from the file itself.

# Mobile Code Controls

The concept of attaching programs to webpages has very real security implications. However, through the use of appropriate technical controls, the user does not have to consider the security consequences of viewing the page. Rather, the controls determine if the user can view the page. Secured systems should limit mobile code (applets) access to system resources such as the file system, the CPU, the network, the graphics display, and the browser’s internal state. Additionally, the system should garbage-collect memory to prevent both malicious and accidental memory leakage. The system must manage system calls and other methods that allow applets to affect each other as well as the environment beyond the browser.

Fundamentally, the issue of safe execution of code comes down to a concern with access to system resources. Any running program has to access system resources to perform its task. Traditionally, that access has been given to all normal user resources. Mobile code must have restricted access to resources for safety. However, it must be allowed some access to perform its required functions.

It is important to identify the resources the program needs and then provide certain