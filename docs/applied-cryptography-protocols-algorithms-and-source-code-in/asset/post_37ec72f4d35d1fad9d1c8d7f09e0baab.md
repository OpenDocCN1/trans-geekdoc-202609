
## 5.1 Zero-Knowledge Proofs

- (1) Peggy uses her information and n random numbers to transform the hard problem into n isomorphic problems. She then uses her information and the random numbers to solve the n new hard problems.
- (2) Peggy commits to the solution of the n new hard problems.
- (3) Peggy uses all of these commitments together as a single input to a one-way hash function. (After all, the commitments are nothing more than bits) She then saves the first n bits of the output of this one-way hash function.
- (4) Peggy takes the n bits generated in step (3). For each ith hard problem in turn, she takes the ith bit of n bits and:
    - (a) if it is a 0, she proves that the all is isomorphic, or
    - (b) if it is a 1, she opens the solution she committed to in step (2) and proves it is a solution to the new problem.
- (5) Peggy publishes all the commitments from step (2) as well as the solutions in step (4).
- (6) Victor or Carol whoever is interested, verifies that steps (1) through (5) were executed properly.

This is amazing: Peggy can publish some data that contains no information about her secret, but convince anyone of her existence. The protocol can also be used for digital signature schemes, if the challenge is a one-way hash of the initial messages and the message to be signed.

This works because the one-way hash function acts as an unbiased random-bit hash function. For Peggy to cheat, she has to predict the output of the one-way hash function. (Remember, if she doesn't know the solution to the hard problem, she can either [a] or [b] of step [4], but not!) If she somehow knew the one-way hash function would ask her to, then she could cheat. However, there is no way for Peggy to force the one-way function to produce certain bits or guess which bits it will produce. The one-way function is, in effect, Victor's surrogate in the protocol—randomly choosing one of two proofs in step (4).

In a noninteractive protocol, there must be many iterations of the challenge/reply sequence. Peggy, Victor, picks the hard problems using random numbers. She can pick different problems, different commitment vectors, till iterations—in an interactive protocol, a probability of 1 in 2^10 (1 in 1024) that Peggy can cheat—may be. However, that's not enough for noninteractive zero-knowledge proofs. Remember that Mallory can always cheat [a] or [b] of step [4]. He can try to guess what he will be asked to, go through steps [1] through [3], and see if he guessed right. If he can't cheat—repeatedly. 1024 guesses is easy on a computer. To prevent this brute-force attack, noninteractive protocols need 64 iterations, or even 128 iterations, to be valid.

This is the whole point of using a one-way hash function: Peggy cannot predict the output of the whole hash function because she cannot predict it. The commitments which are used as the input are only known after she solves the new problems.

## CHAPTER 5 Advanced Protocols

### Generalities

Blum proved that any mathematical theorem can be converted into a graph such that the proof of theorem is equivalent to proving a Hamiltonian cycle in the graph. The general case that any NP statement has a zero-knowledge proof, assuming one-way functions and therefore good encryption algorithms, was proved in [620]. Any mathematical proof can be converted into a zero-knowledge proof. Using this technique, a researcher can prove to the world he knows the proof of a particular theorem without revealing what the solution is. Blum could have published these results without revealing them.

There are also minimum-disclosure proofs [590]. In a minimum-disclosure proof, the following properties hold:

- Peggy cannot cheat Victor. If Peggy does not know the proof, her chances of convincing Victor that she knows the proof are negligible.
- Victor cannot cheat Peggy. He doesn't get the slightest hint of the proof, apart from the fact that Peggy knows the proof. In particular, Victor cannot demonstrate the proof to anyone else without proving it himself from scratch.

Zero-knowledge proofs have an additional condition:

- Victor learns nothing from Peggy that he could not learn by himself without Peggy, apart from the fact that Peggy knows the proof.

There is considerable mathematical difference between proofs that are only minimum-disclosure and that are zero-knowledge. That distinction is beyond the scope of this book, but sophisticated readers are welcome to peruse the references. The concepts were introduced in [626, 619]. Further elaboration on their ideas, based on different mathematical assumptions, were developed in [240, 319].

There are different kinds of zero-knowledge proofs:

- Perfect. There is a simulator that gives transcripts identically distributed to real transcripts (the Hamiltonian cycle and graph examples).
- Statistical. There is a simulator that gives transcripts identically distributed to real transcripts, except for some constant number of exceptions.
- Computational. There is a simulator that gives transcripts indistinguishable from real transcripts.
- No use. A simulator may not exist, but we can prove that Victor will not learn any amount of information from the proof.

### Zero-Knowledge Proofs of Identity

Over the years, extensive work, both theoretical and applied, has been done on minimum-disclosure and zero-knowledge proofs. Manuel Blum and Charlesi Rackoff invented interactive proofs, where one prover can broadcast an interactive proof to a large group of verifiers. Cryptographers proved that everything that can be proven with an interactive proof can also be proven with a zero-knowledge interactive proof [753]. A good survey on the topic is [548].

In the real world, we use physical tokens as proofs of identity: passports, driver's licenses, credit cards, and so on. The token contains something that links it to a person: a picture, a signature, a thumbprint, a retinal scan, or an x-ray. Zero-knowledge proofs of identity were first proposed by Uriel Feige, Amos Micali, and Adi Shamir [566, 567]. This idea allows a person to prove their identity without any physical token. However, it's not perfect. Algorithms for this can be found in Section 23.

### The Chessmaster Problem

Here's how Alice, who doesn't know the rules of chess, can defeat a grandmaster (This is sometimes called the Chessmaster Problem.). She challenges Gary Kasparov and Anatoly Karpov to a game, at the same time and in separate rooms. She plays white against Kasparov and black against Karpov. Neither grandmaster knows the other. Karpov, as white, Alice records the moves and walks into the room with Kasparov. Playing white, she makes the move against Kasparov. Kasparov makes his first move as black. Alice records the moves, walks into the room with Karpov, and makes the same move. This continues, until one wins the game or both end in a draw. In reality, Karpov is playing Karpov and Alice is simply mimicking the moves of each grandmaster on the other's board. if neither Karpov nor Kasparov knows about the other's presence, each will be impressed with Alice's play. This kind of fraud can be used against zero-knowledge proofs of identity [485, 120]. While Alice is proving her identity to Mallory, Mallory can simultaneously prove that he is Alice.

### The Mafia Fraud

When discussing his zero-knowledge identification protocol, Adi Shamir [424] said: "I could go to a Mafia-owned store million successive times and they will still not be able to misrepresent me." Here is how the Mafia can: Alice is eating at Bob's Diner, a Mafia-owned restaurant. Carol is shopping at Dave's Emporium, an expensive jewelry store. Bob and Carol are both members of the Mafia and are communicating by a secret radio link. Alice and Dave are unaware of the fraud.

At the end of Alice's meal, when she is ready to pay and prove her identity to Bob, Bob signals Carol that the fraud is ready to begin. Carol chooses some diamonds, gets ready to prove her identity to Dave. Now, as Alice proves her identity to Bob, Bob and Carol perform the same protocol with Dave. When Dave asks a question in the protocol, Carol radios the question back to Bob, and asks it of Alice. When Alice answers, Bob radios the correct answer to Carol. Actually, Alice is proving her identity to Dave, and Carol are simply sitting in the middle of the protocol passing messages back and forth. When the protocol finishes, Alice has proved herself to Dave and has purchased some expensive diamonds (which Carol displays).

### The Terrorist Fraud

If Alice is willing with Carol, they can also defraud Dave. In this protocol, Carol is a well-known terrorist. Alice is helping her into the country. Dave is the immigration officer. Alice and Carol are connected by a secret radio link. When Dave asks questions as part of the zero-knowledge protocol, Carol radios them back to Alice, who answers herself. Carol recites these answers to Dave. In reality, Alice is proving her identity to Dave, with Carol acting as a communications path. When the protocol finishes, Dave thinks that Carol is Alice and lets her into the country. Three days later, Carol shows up at some government building with a minivan full of explosives.

### Suggested Solutions

Both the Mafia and Terrorist frauds are possible because the conspirators communicate via a secret radio. One way to this requires all identifications to take place inside Faraday cages, which block all electromagnetic radiation. In the terrorist example, this assures immigration officer Dave that Carol was not receiving answers from Alice. In the Mafia example, Bob could build a simple Faraday cage in his house, but Dave and Carol would not be able to communicate. To solve the Chessmaster Problem, Bob and Carol would be forced to sit in their seats until the end of a game. Thomas Beth and Yvo Desmed proposed another solution, using accurate clocks [148]. If each step in the protocol must take a place at a time, one would be available for the conspirators to communicate.
