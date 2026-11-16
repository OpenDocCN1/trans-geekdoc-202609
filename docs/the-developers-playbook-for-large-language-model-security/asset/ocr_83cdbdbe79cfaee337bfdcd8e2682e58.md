# Watch for Excessive Agency

While developing the OWASP Top 10 for LLM Applications list, one of the most hotly debated topics was excessive agency. This concept hadn't previously been discussed in this way in application security circles and it felt substantially different from typical security vulnerabilities in other Top 10 lists. The fact that the expert group selected this concept as a top-ten-level risk speaks volumes.

Excessive agency exists when a developer gives an LLM-based system more capabilities or access than it safely should have. Typically, excessive agency can manifest as excessive functionality, excessive permissions, or excessive autonomy. Excessive agency goes beyond bugs, like hallucinations or confabulations, in LLM output; it represents a structural vulnerability in how the system is designed and deployed.

Let's examine three versions of this vulnerability to better understand the issues related to excessive agency. We'll use hypothetical, but very believable, scenarios to examine how an application starts with reasonable goals, expands unsafely, and then suffers the consequences of excessive agency.

![](bbox=[0.176, 0.418, 0.251, 0.485])

Many attacks start with prompt injection, but the exploits are much worse when chained with another vulnerability, such as excessive agency. Expect to see multiple vulnerabilities linked together in the real world.

# Excessive permissions

Think about your LLM as another system user. Then, consider what permissions you will give it and how to limit that to the minimum required set. Failure to do so opens up your application to excessive agency vulnerabilities. Let's look at an example:

# *Where it started*

A development team uses the RAG pattern discussed in Chapter 5 to improve response and reduce hallucinations in a medical diagnosis application, giving the application access to a database filled with patient records to solidify the LLM's knowledge base.

# *Where it went wrong*

As the application evolves, the team adds a feature that enables the LLM to write to the database to add notes for the physician caring for the patient. To facilitate this, the team expands the LLM app's database permissions from READ permissions only to add UPDATE, INSERT, and DELETE permissions.

# *What happened*

A malicious insider takes advantage of this unrestricted access to trick the LLM into modifying patient records and deleting billing information.