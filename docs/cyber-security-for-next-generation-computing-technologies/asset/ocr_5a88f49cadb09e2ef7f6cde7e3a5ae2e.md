# Cyber Security for Next-Generation Computing Technologies

is determined as a solitary link between both the hosts and maybe another piece of equipment.

+   **Intrusion Prevention System**: An intrusion detection system with the capacity to stop intrusions is known as an intrusion prevention system (IPS/IDPS) [39]. Although it is preferable, IDS doesn't necessarily have to be capable of recognizing intrusions as they are taking place. Because an IPS must be capable of preventing accidents from occurring, it must also be capable of detecting them in legitimately preventative measures that the network cyber attack might include cutting off the link, restricting an IP address, or restricting the transmission rate.

Some techniques used to identify cyber attacks may be significantly impacted by the requirement that attacks be recognized instantaneously. For instance, an IDS may provide an alert even if it is sure that the occurrence for which it is issuing the warning is indeed an abnormality. Before acting, an IPS must be confident about the situation. If not, the IPS could take steps that the company using the IPS doesn't desire [40].

+   **Detection**: There are several ways to identify breaches. Some of the techniques are anomaly based and signature based.

Algorithms that rely on signatures verify asserted signatures against a collection of known signatures [41, 42]. Transformed elements from a packet or stream data are put together to form a signature. An inbound stream or packet is marked malvolent if its signature matched one in the database. Since signature-based approaches simply attempt to correlate attack patterns in the database, they have little cost in terms of calculation and preprocessing. Since all it does is analyze signatures, network deployment is simple. The system is not required to become familiar with how network traffic appears. Techniques that rely on signatures are highly successful against well-known cyber attacks [43]. Without updating the databases with current signatures, it is impossible to identify emerging risks.

Taking anomaly-based approaches, also known as behavior-based techniques, can predict the behavior of network activity. A warning is given and the incoming packet is caught as malvolent when it differs from such a model. These approaches employ a statistical method of typical behavior, which they ought to be able to spot such anomalies in this pattern. As a consequence, new cyber attacks that go too far from customary behavior are also discovered.

It is impossible to install the system onto an infrastructure and expect it to function because because [44]. The system must become familiar with the behavior of the network activity, as shown in Figure 7.2. When training data contains errors, including such classifications, issues might occur, including the generation of false positive notifications.

As like anomaly-based approach, machine learning techniques can be applied. Methods utilizing machine learning do have the ability to extract information from data and determine whether fresh data is malignant [45].