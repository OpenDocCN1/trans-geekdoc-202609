specific systems should be used. As noted, intrusion prevention relies first on intrusion detection strategies; thus, the differentiators will be highlighted as appropriate.

# 27.2.1 Process Structure.

Intrusion detection is defined as a monitoring and alarm generation process, and, as such, it can be described using a simple process model. This model is outlined here and will be used to illustrate the fundamental concepts of intrusion detection.

# 27.2.1.1 Information Sources.

The first stage of the intrusion detection process comprises one or more information sources, also known as event generators. Information sources for intrusion detection may be categorized by location: network, host, or application.

# 27.2.1.2 Analysis Engine.

Once event information is collected, it is passed to the next stage of the intrusion detection process, in which it is analyzed for symptoms of attack or other security problems.

# 27.2.1.3 Response.

When the analysis engine diagnoses attacks or security problems, information about these results is revealed via the response stage of the intrusion detection process. Responses span a wide spectrum of possibilities, ranging from simple reports or logs to automated responses that disrupt attacks in progress. The presence of these automated responses defines an intrusion prevention system.

# 27.2.2 Monitoring Approach.

The first major classifier used to distinguish intrusion detection systems is the monitoring approach of the system. Monitoring is the action of collecting event data from an information source and then conveying that data to the analysis engine.

The monitoring approach describes the perspective from which intrusion detection monitoring is performed. The primary monitoring approaches found in intrusion detection systems today are *network based, host based, and application based.*

# 27.2.3 Intrusion Detection Architecture.

Even in the early days of manual security audit, researchers noted that in order for audit information to be trusted, it should be stored and processed in an environment separate from the one monitored. This requirement has evolved to include most intrusion detection approaches, for three reasons:

+   1. To keep an intruder from blocking or nullifying the intrusion detection system by deleting information sources
+   2. To keep an intruder from corrupting the operation of the intrusion detector in order to mask the presence of the intruder
+   3. To manage the performance and storage load that might result from running intrusion detection tasks on an operational system

In this architecture, the system running the intrusion detection system is called the *host*. The system or network being monitored is called the *target.*

# 27.2.4 Monitoring Frequency.

Another common descriptor for intrusion detection approaches is the timing of the collection and analysis of event data. This is