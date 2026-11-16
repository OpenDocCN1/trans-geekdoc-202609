+   - **Guidelines:** Point to statements in policies or procedures by which to determine a course of action
+   - **Procedures:** The lowest level in a policy that provides step-by-step instructions to achieve a certain task

# Security Engineering and Architecture

17. The trusted computing base (TCB) is a combination of protection mechanisms, including hardware, software, and firmware, to maintain security within a computer system.

18. The reference monitor is an access control concept referring to an abstract machine that mediates all accesses to objects by subjects.

+   19. The security kernel implements the reference monitor concept. The reference monitor concept has the following properties:
+   - Provides isolation
+   - Is invoked for every access attempt
+   - Is impossible to circumvent and is not foolproof
+   - Is complete, verified, and tested

20. Resource isolation is a process of segmentation so that memory is separated physically, not just logically.

+   21. Rings of protection are used to isolate processes:
+   - Layer 0: OS
+   - Layer 1: Remaining parts of the OS
+   - Layer 2: Utilities and I/O
+   - Layer 3: Applications and programs
+   Lower numbers have higher levels of privileges.

+   22. A security model defines the structure by which data structures and systems are designed to enforce security policy. Well-known security models include:
+   - **Bell-LaPadula:** Enforces confidentiality and uses rules: the simple security rule (no read up) and the * property (no write down).