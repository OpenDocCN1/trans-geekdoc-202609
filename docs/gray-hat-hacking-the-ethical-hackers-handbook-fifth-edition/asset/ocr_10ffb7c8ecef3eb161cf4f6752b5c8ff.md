![](bbox=[0.126, 0.085, 0.876, 0.492])

Figure 5-3 Captured signal

# Replay

Now that we have captured signals, it is time to attempt to replay the data. Although the inability to successfully replay the data does not necessarily mean that we failed to capture the data correctly, the ability to successfully replay the data does indicate a potential communication flaw. For systems where security is of concern, anti-replay mitigations should be in place to prevent unauthorized access. The general use case of a device like this is to simply turn on or off a light, fan, or some other simple device. Therefore, I would suspect that replay attacks are likely not mitigated. The main goal of the replay attack is to successfully exercise the device with minimal understanding of the actual protocol.

The flow graph of the Replay phase will look like the Capture phase, with the exception that we now use a file as the source and an osmocom as the sink. We have to reuse the same sample rate and frequency in order for the signal to be reproduced as it was received. Additionally, Multiply Const, QT GUI Time Sink, and Throttle blocks have been added to the graph in Figure 5-4 to facilitate adjustments that may be required. Throttle is added to keep the CPU utilization down if we do not have an external sink to effectively rate-limit the data. Essentially, if the osmocom sink is disabled and the throttle is missing, the data being read from the file is not rate-limited and CPU utilization may be high.