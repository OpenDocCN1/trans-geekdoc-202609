residing in temporary memory is referred to as *data at rest*. Failure to properly protect data at rest can lead to attacks such as the following:

+   > Various forms of USB (Universal Serial Bus) malware, including USB Rubber Ducky
+   
+   > Pod slurping, a technique for illicitly downloading or copying data from a computer, which is typically used for data exfiltration
+   
+   > Other forms of malicious software, including viruses, worms, Trojans, and various types of key loggers

Data at rest can be protected via different technical and physical hardware or software controls that should be defined in your security policy. Some hardware offers the ability to build in encryption. A relatively new hardware security device for computers is called a *Trusted Platform Module* (TPM) chip. A TPM chip is a “slow” cryptographic hardware processor that can be used to provide a greater level of security than software encryption. A TPM chip installed on the motherboard of a client computer can also be used for system state authentication. A TPM chip can also be used to store encryption keys.

A TPM chip measures the system and stores the measurements as it traverses the boot sequence. When queried, the TPM chip returns these values, signed by a local private key. These values can be used to discover the status of a platform. The recognition of the state and validation of these values is referred to as *attestation*. Attestation allows you to confirm, authenticate, or prove a system to be in a specific state. Data can also be encrypted using these values. This process is referred to as *sealing a configuration*. In short, a TPM chip is a tamper-resistant cryptographic module that can provide a means to report the system configuration to a policy enforcer or health monitor.

A TPM chip also provides the ability to encrypt information to a specific platform configuration by calculating hashed values based on the system’s firmware, configuration details, or core components of the operating system as it boots. These values, along with a secret key stored in the TPM chip, can be used to encrypt information and allow it to become usable only in a specific machine configuration. This process is called *sealing*.