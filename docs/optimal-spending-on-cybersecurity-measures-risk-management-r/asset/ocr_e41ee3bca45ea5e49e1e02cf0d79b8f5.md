# Patch auditing

The technology group should have a patch audit process in place to identify any failed or pending patches, including continuous monitoring for any unexpected incompatibility or performance issues.

# Reporting

The technology group should have a mechanism in place to produce a patch compliance report when required. This includes documenting risk acceptance and any exceptions that may occur.

# Review, improve and repeat

The technology group should have an established cadence for repeating and optimizing the patch management process, including the following:

+   - Phasing out or isolating any outdated or unsupported machines.
+   - Reviewing applicable policies.
+   - Revisiting exceptions to verify whether they still apply or are necessary.

# Verify vulnerability remediation through network and host vulnerability scanning

The technology group and system administrators should verify that they have successfully remediated or mitigated vulnerabilities as intended.

The technology group should confirm that the remediations have been conducted appropriately to avoid a security incident or unplanned downtime. This can be accomplished by several methods:

+   - Verify that the files or configuration settings that the remediation was intended to correct have been changed as stated in the vendor’s documentation.
+   - Scan the host with a vulnerability scanner to detect known vulnerabilities.
+   - Review patch logs to verify that the recommended patches were installed properly.
+   - Employ exploitation procedures or code to attempt to exploit the vulnerability—that is, perform a penetration test.

Generally, exploitation tests involve launching actual attacks within a network or on a host, and this type of testing should be performed only on non-production equipment for certain vulnerabilities.