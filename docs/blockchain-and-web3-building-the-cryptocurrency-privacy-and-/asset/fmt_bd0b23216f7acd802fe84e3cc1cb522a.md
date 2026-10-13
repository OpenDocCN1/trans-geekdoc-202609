
While the above is only a conceptual example, ZKPs deploy this same strategy but use cryptography to prove knowledge about a data point without revealing the data point. With this cave example, there is an input, a path, and an output. In computing there are similar circuit systems, which take some input, pass the input signal through a path of electrical gates, and generate an output. ZKP leverages circuits like these to prove statements.

Imagine a computational circuit that outputs a value on a curve, for a given input. If a user can consistently provide the correct answer to a point on the curve, one can be assured that the user possesses some knowledge about the curve since it becomes increasingly improbable to guess the correct answer with each successive challenge round. One can think of the circuit like the path that Alice walks in the cave; if she is able to traverse the circuit with her input, she proves she holds some knowledge, the "passcode" to the circuit, with a high degree of probability.

#### Benefits of ZKPs

Being able to prove knowledge about a data point without revealing any additional information besides knowledge of data provides several key benefits, especially within the context of blockchain networks. The primary benefit of ZKP is the ability to leverage privacy-preserving datasets within transparent systems such as public blockchain networks like Ethereum.

While blockchains are designed to be highly transparent, where anyone running their own blockchain node can see and download all data stored on the ledger, the addition of ZKP technology allows users and businesses alike to leverage their private datasets in the execution of smart contracts without revealing the underlying data. Ensuring privacy within blockchain networks is crucial for preserving privacy in various metaverse applications.

### Secure Multiparty Computation

#### What Is Secure Multiparty Computation?

Secure multiparty computation (also called multiparty computation, SMPC, or MPC) is a cryptographic technique that enables different parties to carry out a computation using their private data without revealing their private data to each other. Secure multiparty computation is a method that can help businesses and individuals ensure the privacy of their sensitive data without undermining their ability to gain insights from it.

#### How Does Secure Multiparty Computation Work?

A popular example to illustrate the basic idea behind SMPC is as follows: Suppose a group of employees wants to learn their average salary in order to find out whether they are underpaid. However, they don't want to disclose their individual salary information. An SMPC method can solve this problem with the following steps:

1.  Each employee is numbered from first to last.
2.  The first employee chooses an arbitrarily large number and adds their salary to the number and tells the second employee the result.
3.  The second employee adds his or her number to the value and tells the result to the third employee, and so on until the last employee.
4.  After adding their salary to the result, the last employee tells the result to the first employee.
5.  The first employee subtracts the large number they started with and divides the result by the number of employees in the group to obtain the average salary.

In this example, the large number chosen by the first employee hides his/her salary from the others. At the same time, the final result that the first employee receives from the last employee provides no information to the first employee about the others' salaries. As a result, the group, consisting of multiple parties, could securely compute the average salary without disclosing their salaries.

This is, of course, a simple example to illustrate how SMPC works. In real-world use cases, SMPC enables complex computations such as machine learning models using privately held data without the need of sharing it.

#### What Are the Properties of Secure Multiparty Computation?

SMPC aims to ensure two basic properties against adversarial attacks:

1.  **Input privacy.** No party can infer information about private inputs from the output.
2.  **Correctness.** An adversarial party must not be able to prevent other parties from receiving their correct outputs.

An adversary in this context refers to the parties that attack the computation process. The attack may be for the purpose of learning private information of other parties or for causing the output of the computation to be incorrect.

#### What Are the Benefits of Secure Multiparty Computation?

*   **Promotes privacy and data utility.** SMPC can eliminate the tradeoff between data privacy and data utility since private or encrypted data does not need to be shared with third parties or model owners to be utilized. As a result, it also eliminates the risks of data breaches and misuses stemming from data collection.
*   **Reveals only the final result.** SMPC only reveals the final result and does not reveal intermediate information during the computation.

#### What Are the Challenges to Secure Multiparty Computation?

*   **Communication overhead.** As illustrated in the example above, the SMPC method requires communication between parties, which can lead to high communication costs.
*   **Vulnerable to attacks from colluding parties.** For instance, the second employee and the fourth employee can collude to learn the third employee's salary by subtracting the value sent by second to third from the value sent by the third to fourth.

## Homomorphic Encryption and Federated Learning

Homomorphic encryption (HE) and federated learning (FL) are two different but related technologies that aim to solve the same problem: How can computation tasks such as machine learning and blockchain transactions be performed more privately and securely? In other words, how can an IT system use data without seeing the data?

### Homomorphic Encryption

#### What Is Homomorphic Encryption?

Homomorphic encryption (HE) is a type of encryption method that allows computations to be performed on encrypted data without first decrypting it with a secret key. The results of the computations also remain encrypted and can only be decrypted by the owner of the private key. Homomorphic encryption enables metaverse platforms to process and transact on user's encrypted data without decryption of the data.

#### How Does It Work?

The process starts with data in its decrypted form (i.e., plain text). The data owner wants another party (such as cloud or metaverse service provider) to perform a mathematical operation (e.g., some function, or a machine learning model) on it without revealing its content.

As show in [Figure 7.5](#c07.xhtml#c07-fig-0005), the data owner (or the client of the cloud) encrypts the data and sends it to the other party (the cloud server). The cloud server receives encrypted data, performs operations on it, and sends the encrypted result to the owner. The owner of the data decrypts it with a private key and reveals the result of the intended mathematical operation on the data.

There are three main types of homomorphic encryption:

1.  **Partially Homomorphic Encryption (PHE).** PHE only allows selected mathematical functions to be performed on encrypted data.
2.  **Somewhat Homomorphic Encryption (SHE).** SHE allows a limited number of mathematical operations up to a certain complexity to be performed, for a limited number of times.
3.  **Fully Homomorphic Encryption (FHE).** FHE allows any kind of mathematical operation to be performed for an unlimited number of times.

![Figure 7.5 How Homomorphic Encryption Works](images/c07f005.png)

**[Figure 7.5](#c07.xhtml#R_c07-fig-0005) How Homomorphic Encryption Works**

#### Why Is Homomorphic Encryption Important Now?
