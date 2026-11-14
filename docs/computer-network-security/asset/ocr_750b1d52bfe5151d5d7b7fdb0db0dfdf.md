# 3.3.2. How Syslog works

# 3.3.2.1. Syslog severity levels

A severity level indicates the nature of an error message. There are eight severity levels, from 0 to 7, with 0 (zero) being the most critical and 7 being the least critical. These levels are described below:

| Code | Severity | Description |
|---|---|---|
| 0 | Emergencies | System inoperable. |
| 1 | Alerts | An immediate intervention is required. |
| 2 | Critical | Critical system error. |
| 3 | Errors | Operating errors. |
| 4 | Warnings | Warning (an error may occur if no action is taken). |
| 5 | Notifications | Normal event that must be reported. |
| 6 | Informative | For information. |
| 7 | Debug | Debugging message. |

# 3.3.2.2. The format of a Syslog message

+   - A log in Syslog format provides the following information, in order: Seq num:timestamp%FACILITY-SEVERITY-MNEMONIC: message:

+   - Seq num: this indicates the serial number of an event. This information only appears if the service sequence-numbers command has been executed.

+   - timestamp: indicates the date and time at which the event took place. This information only appears if the service timestamps command has been run. It must be noted that this command is activated by default;

+   - FACILITY: indicates the component, protocol or process that generated the message. For instance, SYS for the operating system, IF for an interface, etc.;

+   - SEVERITY: a number, between 0 and 7, indicating the severity of the reported event;

+   - MNEMONIC: a code identifying the Syslog message;

+   - message: a description of the event that triggered the Syslog message.

+   - Example: the Syslog message to be analyzed is as follows.