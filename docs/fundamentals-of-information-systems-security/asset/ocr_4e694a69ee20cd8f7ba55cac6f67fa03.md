+   - **Cross-site scripting (XSS)**—This is an attack in which an attacker inputs client-side script code to a web application. The code would then be viewed by other users, and their client software would execute the script instructions. The XSS attack exploits the trust users have for a server.

+   - **Cross-site request forgery (XSRF)**—Similar to the XSS attack, an attacker provides script code that causes a trusted user who views the input script to send malicious commands to a web server. The XSRF attack exploits the trust a server has in a user.

+   - **Structured Query Language (SQL) injection**—An attack technique in which an attacker provides malicious SQL statements to access unauthorized data or carry out unauthorized commands.

+   - Defines secure configuration baselines. When you release your application to end users, provide a documented set of configuration settings that define a secure baseline, or starting point.

+   - Provides guidance on hardening your application. In addition to providing a secure baseline, offer guidance on changing configuration settings that will keep your application secure. It should also provide guidance on further configuration settings or the addition of external controls that will increase your application’s security.

+   - Provides and applies frequent patches. Ensure that you apply the latest security patches for your environment. It should also provide frequent security patches to the users of your application, along with a convenient method of applying patches and managing the patching process.

Software developed in-house will have source code, object code, and runtime executables. You need to manage and protect these with policies, standards, and procedures. For example:

+   - You should protect source code from access by unauthorized users.

+   - You should track changes to source code by version control systems so that rollback to a previous version is error free.

+   - Programmers should not be able to update production systems directly (programmers to test, then test to production).

# ## Software Development Models

Secure software development requires a formal model for creating and modifying software. This process is known as the software development life cycle, or SDLC, which uses industry best practices to guide software development activities as projects with specific start and end dates and a set of required deliverables. At this time, the two most widely accepted models for software development include:

+   - The waterfall model. Based on traditional project management practices in which extensive planning precedes any development. Progress through a project moves forward along a well-defined path.

+   - Agile development method. A newer family of project management approaches that depend on very short sprints of activity. Agile works well in very dynamic environments where requirements change and are often revisited.