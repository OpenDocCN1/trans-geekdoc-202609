# Internal Controls/Auditing

+   * All security policies should be enforced using appropriate, documented, and communicated controls.
+   * Controls should be audited every six months.
+   * Controls should be risk-ranked for the threats they mitigate.
+   * Missing or weak critical controls must be resolved within two weeks.

# Event Log Management

+   * Security logs must be enabled on each system and application (where applicable).
+   * System time and date of all systems with security logs should be accurate and reported in UTC time.
+   * Critical security events from log files must be copied to a centralized event log collection system and reviewed for critical events. Critical security events should automatically generate alerts to the appropriate incident response team members.
+   * Security logs should never be proactively erased by users or administrators, but logs are allowed to overwrite older events (on a first-in, first-out basis) as needed for operational concerns.

# Endpoint Protection

+   * All endpoints should have up-to-date anti-malware installed and running.
+   * All endpoints capable of receiving communications (e.g., email, text messaging, Slack, etc.) should have anti-phishing and anti-spam content filtering installed.