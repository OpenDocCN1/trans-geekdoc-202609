processed (data in use), while in storage (data at rest), or while being communicated through the networks (data in transit).

An example of cyberattacks on a processing subsystem occurred in 2018, with mas-implications to the hardware [93, 94]. The two types of cyberattacks were

+   - Meltdown: Designed to exploit side effects in the hardware’s out-of-order execution, enabling access to memory and thus enabling the stealing of personal data and passwords
- Spectre: Exploited the processor’s speculative execution

Both examples were attacks on CPUs, affecting millions of computers worldwide. It is worth reemphasizing that DSAs, as discussed earlier, do not employ these hardward features (e.g., out-of-order and speculative executions). However, AI systems use CPUs to control other parts of the hardware within a computing system. Therefore, AI systems can also be compromised.

Another area that continues to be very concerning to computing system manufacturers is the dependency on a trusted supply chain. The cyber-supply chain has been studied in detail by the US Defense Science Board [95]. The limited number of microprocessor foundries also present vulnerabilities, potentially disrupting the development and deployment of trusted computing systems.

Supply chain vulnerabilities are also concerning; they can affect both hardware and software. Software supply vulnerabilities can damage AI systems since the code comes from reusing open-source models. Enck and Williams reported a dramatic increase in malware, where attackers implanted malware directly into open-source software. The Open-Source Security Foundation, with governing members from large commercial software providers, is addressing several of these key challenges. Our systems engineering approach, discussed in chapter 2, is very consistent with some of their recommendations of employing rigorous testing, verification, and validation to making AI systems more robust.

The report from the US NSTC mentioned earlier recommended four research areas to advance the state of the art in securing AI systems (Sec4AI) [92]:

+   1. Develop techniques supporting AI system specifications and verification through standards, tools, and metrics to tractably and compliantly answer about the correctness of a system. The goal is to provide a level of security guarantees.
2. Ascertain trustworthy decision-making, especially in high-stakes applications, including the ability to provide explainability and accountability.
3. Make ML methods robust, for example, by limiting adversarial manipulations and ensuring data privacy and model fairness.