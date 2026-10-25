Although traditional requirements-based testing is important for the correctness and adequacy of security functions implemented by software, no amount of testing can fully demonstrate that software is free from vulnerabilities; any such testing can only provide a small-scale view of what is needed to verify the security of the software. Even the most robustly specified security requirements are not likely to address all possible conditions under which the software may be forced to operate in the real world, including the behavior of software under anomalous and hostile conditions.

Generally, the shortcomings of requirements-based over risk-based software security testing can be summarized as follows:

+   - The changing nature of threats to the software you have in development may result in new attack methodologies, both pre- and post-release.
+   - Your software may change its position as a functional component of an SaaS- or cloud-based solution, which changes the attack surface, thus requiring new security fixes or mitigations.
+   - In today's competitive and rapidly changing environment, the design assumptions on which the requirements were based may be obsolete by the time the software is ready for testing.
+   - Other factors change frequently and likely more rapidly than your specification can keep up.
+   - If the software is going to use components acquired from a third party, the original architecture may not account for future versions that were not planned for in the initial implementation.
+   - The original design assumptions may not account for vulnerability susceptibilities due to design changes or new external attacker capabilities or exploits that may occur during the time taken to develop later versions of the software.

This list highlights why software risk-based security testing as described in this section should always augment traditional requirements-based testing.

As mentioned previously and used as a continuing theme throughout this book, problems found early in the software life cycle by “building security in” are significantly easier and less costly to correct than problems discovered post-implementation or, worse, post-deployment. This is why it is imperative that a disciplined approach to security reviews and tests begin early in the software development life cycle (SDLC) process and continue post-release until the software reaches end of life.

Software security testing takes the perspective that the tester is the attacker. Test scenarios should be based on misuse and abuse possibilities developed through the methodologies and threat modeling described in Chapter 4 and should incorporate both known attack patterns as well as anomalous interactions that seek to invalidate assumptions made by and about the software and its environment. Comprehensive test scenarios, test cases, and test oracles should be derived. Be sure that all that misuse cases developed in the previous stage are executed and thoroughly tested. The testing of each development iteration, use case, and misuse case will identify major design flaws early in the SDL and should catch up to 95 percent of defects well before the last phase.1

The test environment should duplicate as closely as possible the anticipated execution environment in which the software will be deployed, and it should be kept entirely separate