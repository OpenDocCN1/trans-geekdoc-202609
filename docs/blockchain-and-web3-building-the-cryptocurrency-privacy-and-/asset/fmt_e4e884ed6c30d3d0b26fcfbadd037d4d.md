
# Minimization

Individuals' data collection, use, and sharing should be done in accordance with their consent choices, ensuring they are strictly relevant and adequate for a specific purpose. Metaverse platform participants enable the necessary tracing and audit capabilities for operators to ensure compliance.

## Individual Understanding

This group focuses on educating individuals and positioning them to make informed choices on how data is collected, used, and shared through a metaverse platform. The following four attributes are defined for individual understanding:

*   **Transparency.** Individuals can access clear information in due time and with ongoing visibility on how an entity collects, uses, and shares their data, the potential risks and benefits of the service, the availability of source code, the rules and standards upon which it is based, their rights and obligations, and the governance structure of the metaverse platform.
*   **Clarity.** Individuals are enabled to have a clear understanding of how and why data is collected, used, and shared. Consent choices are presented in a coherent and intelligible way. No dark-pattern behavior is permitted.
*   **Consistency.** Consent mechanisms are presented to individuals in the same format across all user interactions in the data exchange (e.g., terminology, icons, structure).
*   **Standardization.** Consent choices are presented to individuals, across use cases and participants, in a common, digestible format. Participants enable the necessary technology to read, interpret, and implement consent choices received in the standard format. Operators enforce these standards.

## Individual Control

This group addresses supporting the tools and interfaces for individuals to exercise their informed choices on how their data is collected, used, and shared through a metaverse platform. The following five attributes are defined for the individual control:

*   **Interoperability.** Transfer capabilities for individuals' data, along with the associated rights and permissions, from one operator or participant to another operator or participant, are in a common machine-readable format that is interpretable and understood across participants in a metaverse platform.
*   **Usability.** Individuals are able to control how their data is used, collected, or shared. They are enabled, through the data exchange consent mechanisms, to act to control the collection, use, and sharing of personally identifiable data as well as de-identified data of personal origin.
*   **Accessibility.** Individuals are able to control how data is collected, used, and shared through a simple consent-mechanism interface that is available at relevant interaction points. Access should be available for all individuals, including minorities, those with disabilities, and individuals of low socioeconomic status.
*   **Adoptability.** The governance approach for individuals' interactions with consent mechanisms should be implementable and manageable by both operators and participants in a metaverse platform.
*   **Flexibility.** Consent interfaces allow for easy modification to respond to the altered circumstances of operators, participants, or individuals, as well as governance rules, regulatory policy, or technology developments.

# Zero-Knowledge Proof and Secure Multiparty Computation

To protect users' privacy in terms of data, identity, digital assets, and transactions, there are a few privacy preserving technologies currently under active research. The following two sections will introduce four of the privacy technologies that can be heavily leveraged by metaverse platforms (see [Figure 7.3](#c07.xhtml#c07-fig-0003)).

## Zero-Knowledge Proof

### What Is Zero-Knowledge Proof?

Is it possible to show that something is true without revealing the data that proves it? This is what zero-knowledge proof (ZKP) technology proposes – a method for one party to cryptographically prove to another that they possess knowledge about a piece of information without revealing the actual underlying information. In the context of blockchain networks, the only information revealed on-chain by a ZKP is that some piece of hidden information is valid and known by the prover.

![Figure 7.3 Leading Privacy-Preserving Computing Methodologies](images/c07f003.png)

[Figure 7.3](#c07.xhtml#R_c07-fig-0003) Leading Privacy-Preserving Computing Methodologies

ZKPs were first described in a 1985 MIT paper from Shafi Goldwasser and Silvio Micali called "The Knowledge Complexity of Interactive Proof-Systems." In this paper, the authors demonstrate that it is possible for a prover to convince a verifier that a specific statement about a data point is true without disclosing any additional information about the data.

### How Does Zero-Knowledge Proof Work?

ZKPs can either be interactive—where a prover convinces a specific verifier but needs to repeat this process for each individual verifier—or non-interactive—where a prover generates a proof that can be verified by anyone using the same proof. Additionally, there are now various implementations of ZKPs including `zk-SNARKS`, `zk-STARKS`, `PLONK`, and `Bulletproofs`, with each having their own tradeoffs of proof size, prover time, verification time, and more.

The three fundamental characteristics that define a ZKP include:

*   **Completeness.** If a statement is true, then an honest verifier can be convinced by an honest prover that they possess knowledge about the correct input.
*   **Soundness.** If a statement is false, then no dishonest prover can unilaterally convince an honest verifier that they possess knowledge about the correct input.
*   **Zero-knowledge.** If the state is true, then the verifier learns nothing more from the prover other than that the statement is true.

At a high level, the creation of a ZKP involves a verifier asking the prover to perform a series of actions that can only be performed accurately if the prover knows the underlying information. If the prover is only guessing as to the result of these actions, then they will eventually be proven wrong by the verifier's test with a high degree of probability.

![Figure 7.4 Zero-Knowledge Proof Algorithm Illustration](images/c07f004.png)

[Figure 7.4](#c07.xhtml#R_c07-fig-0004) Zero-Knowledge Proof Algorithm Illustration

### How ZKP Works to Prove Knowledge about Data Without Revealing the Data to Another Party

A conceptual example to intuitively understand proving data in zero-knowledge is to imagine a cave with a single entrance but two pathways (path A and B, as shown in [Figure 7.4](#c07.xhtml#c07-fig-0004) – you may recall Bob and Alice appeared in [Chapter 2](#c02.xhtml) earlier for a bitcoin transaction, see [Figure 2.2](#c02.xhtml#c02-fig-0002)) that connect at a common door locked by a passphrase. Alice wants to prove to Bob she knows the passcode to the door but without revealing the code to Bob. To do this, Bob stands outside of the cave and Alice walks inside the cave, taking one of the two paths (without Bob knowing which path was taken). Bob then asks Alice to take one of the two paths back to the entrance of the cave (chosen at random).

If Alice originally chose to take *path A* to the door, but then Bob asks her to take *path B* back, the only way to complete the puzzle is for Alice to have knowledge of the passcode for the locked door. This process can be repeated multiple times to prove Alice has knowledge of the door's passcode and did not happen to choose the right path to take initially with a high degree of probability. After this process is completed, Bob has a high degree of confidence that Alice knows the door's passcode without revealing the passcode to Bob.
