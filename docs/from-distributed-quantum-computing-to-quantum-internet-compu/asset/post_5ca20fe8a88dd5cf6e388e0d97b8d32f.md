
ii) the Networking Layer realizes quantum networking services used by the programs at the Distributed Quantum Computing Layer, supported by the classical Internet, including preparation of quantum entanglement and transmission of qubits; at least for the foreseeable future, the quantum Internet is expected to coexist with the classical Internet.

Later in the book, we will come back to discussing this architecture in further detail, but here, it suffices to convey the idea of quantum Internet computing.

## 1.3 Aim and Scope of the Book

As mentioned, Internet computing, where one does distributed computing but over Internet scale distances and distributed systems involve nodes connected via the Internet, is at the intersection of work in (classical) distributed computing and the (classical) Internet. By an analogy to Internet computing, one could ask the question of what would be at the intersection of distributed quantum computing and the quantum Internet. This book provides an introductory overview of selected topics in distributed quantum computing and the quantum Internet, and then attempts to answer this question, proposing the notion of quantum Internet computing, a proposed “umbrella paradigm” for a collection of topics (listed below), from an analogy to (classical) Internet computing:

- distributed quantum computing, including theoretical studies of quantum protocols which are often quantum versions of classical quantum distributed computing protocols, and perspectives on communication complexity including gains from the use of entanglement,
- distributed quantum computing using non-local (or distributed) quantum gates and circuits, where we focus on how large quantum computation represented by a quantum circuit can be distributed over multiple nodes,
- delegating quantum computations to a server, including delegating in such a way that the server has limited or no knowledge of the computations for the purposes of privacy of the client (who is delegating the computations to the server) or sometimes called blind quantum computing, and verifying delegated quantum computations so that the client is assured that the server did do the required computations; delegating quantum computations (on a pay-per-use basis) might come under what has been called quantum cloud computing given the cloud model of providing computing-as-a-service (typically, in classical cloud computing, including software, computer servers, memory and so on, provided on a pay-as-you-use service over the Internet), and
- quantum Internet, where we introduce the concept, key ideas such as quantum entanglement distillation, and entanglement swapping, and possible architectures.

With respect to Figure 1.2, the first three topics might be considered as falling within the Distributed Quantum Computing Layer, while the last topic, clearly, is in the Networking layer. In a way, “quantum Internet computing” is yet another label, but the label aims to (i) capture the scale of distributed quantum computing envisioned, and the associated challenges with that, as well as (ii) attempts to “bundle” the topics above with the issues they address, at least for the purposes of this book. There are a number of topics mentioned in Section 1.2.1, which we do not cover in detail in this book – some are covered in the books we will mention later in Section 1.5 and others are perhaps left to other books to come! The range of topics under quantum Internet computing may yet grow and evolve in the coming years.

## 1.4 Outline of this Book

The rest of this book is organized as follows.

Chapter 2 discusses the mathematical and quantum computing background required for the rest of the book, including a brief introduction to quantum computing and related concepts, including qubit and qubit states, measurement, quantum gates and circuits, entanglement, and teleportation.

Chapter 3 discusses a selection of distributed quantum computing problems and quantum protocols, many which have their origins in classical distributed computing. The chapter first discusses the distributed three-party product problem, the distributed Deutsch–Jozsa promise problem, and the distributed intersection problem, demonstrating how, for some problems, quantum information can enable fewer bits of communication to be used for a solution. We also look at how certain distributed computation problems can be solved with quantum information, but not possible classically. The second part of the chapter discusses quantum protocols, including quantum coin flipping, quantum leader election, QKD, quantum anonymous broadcasting, quantum voting, quantum Byzantine Generals, quantum secret sharing, and quantum oblivious transfer.

Chapter 4 discusses non-local gates, or quantum gates, for computations over several nodes. The chapter discusses the distributed CNOT gate, different ways for its implementation, and distributed control of gates beyond the CNOT gate. The chapter also briefly reviews work on distributed quantum circuits, distributed quantum computing algorithms using such non-local gates, and control and management for distributed quantum computers.

Chapter 5 discusses the idea of a client, with limited resources, delegating quantum computations to a more powerful quantum computer or server, in the style of what we see with cloud computing today. However, security and privacy are key considerations when delegating computations. We look at how to delegate quantum computations to a quantum server in such a way as to protect the privacy of the client's inputs, that is, the server cannot know the client's inputs while still being able to perform the computations for the client. The chapter looks at how the client can verify the server's computations, or at least detect if the server really performed the delegated computations correctly. The chapter also looks briefly at the idea of quantum computing as a service (QaaS).

Chapter 6 discusses some of the key concepts and ideas of the quantum Internet, including the central role that entanglement plays, quantum Internet architecture, and the concepts of entanglement swapping and entanglement purification, and briefly reviews the notion of quantum repeaters.

Chapter 7 brings the whole book together by connecting the topics discussed in the previous chapters and explaining how they would underlie the emerging area of quantum Internet computing, complementary to classical Internet computing.

## 1.5 Related Books and Resources

For readers interested in learning further, we mention books and Web resources specifically related to the topics of this book, i.e. the quantum Internet, and mention briefly how they are different from but complement this book.

This book is different from other excellent books on the quantum Internet such as

- Rodney van Meter's *Quantum Networking* (2014), Wiley, which is likely the earliest (or one of the earliest) books on the quantum Internet, captures a range of concepts and ideas which we will go in depth in Chapter 6 of this book; this book does not cover all the topics on the quantum Internet covered in van Meter's book but, for some of the concepts and ideas, we go deeper, including calculations.
- Peter Rohde's *The Quantum Internet: The Second Quantum Revolution* (2021), Cambridge University Press (CUP), which provides an excellent up-to-date comprehensive overview of the developments in the quantum Internet, covering many of the topics mentioned in this proposed book, but different from Rohde's book, this book will also cover distributed quantum computing and goes in depth into the calculations, in a pedagogical style, for some of the key protocols and concepts.

And there have been several books on the quantum Internet intended for general non-technical readers (which differs from this book which is for the technical reader) such as

- (The late) Jonathan Dowling's *Schrödinger's Web: Race to Build the Quantum Internet* (2020), CRC Press, which provides an excellent overview of related Physics concepts and ideas, and how the quantum Internet might develop in the years to come.
- Gösta Fürnkranz's *The Quantum Internet: Ultrafast and Safe from Hackers* (2020), Springer, which is also a readable introduction to the background in Physics and concepts for the quantum Internet, and also discusses recent developments.

This book focuses on “high-level” quantum distributed computing and protocols, but there are excellent books on quantum communications and quantum information theory such as

- Gianfranco Cariolaro's *Quantum Communications* (2015), Springer, which is one of the earliest (if not the earliest) book on quantum communications, on the differences between classical and quantum communications and foundational theory from a telecommunications perspective.
- Riccardo Bassoli, Holger Boche, Christian Deppe, Roberto Ferrara, Frank H. P. Fitzek, Gisbert Janssen, and Sajad Saeidinaeni's *Quantum Communication Networks* (2021), Springer, which provides a recent tutorial on quantum networking, quantum information theory, quantum computing, and quantum network simulation tools.
- Ivan Djordjevic's *Quantum Communication, Quantum Networks, and Quantum Sensing* (2022), Elsevier, which provides an introduction to quantum communication, quantum error correction, quantum networks, and quantum sensing.

While this book will discuss QKD protocols, among many other topics, other books have focused primarily on quantum cryptography, in particular, with extensive discussions focusing on QKD and quantum key agreement (QKA) such as

- Ramona Wolf's *Quantum Key Distribution: An Introduction with Exercises* (2021), Springer, which is an excellent introduction to the large area of QKD with mathematical and technical depth.
- Federico Grasselli's *Quantum Cryptography: From Key Distribution to Conference Key Agreement* (2021), Springer, which covers QKD and QKA in a mathematically rigorous way.
- Miralem Mehic, Stefan Rass, Peppino Fazio, and Miroslav Voznak's book *Quantum Key Distribution Networks: A Quality of Service Perspective* (2022), Springer, which discusses practical aspects of deploying QKD over the Internet.

For those interested in quantum information theory, four books are:

- Benjamin Schumacher (who coined the term *qubit* in 1995) and Michael Westmoreland's *Quantum Processes Systems, and Information* (2010), CUP,
