
# The standard definition today (Canetti 2000) following previous studies (Goldreich et al. 1987; Goldwasser and Levin 1991; Beaver 1992; Micali and Rogaway 1992) therefore formalizes security in the following general way.

As a mental experiment, consider an “ideal world” in which an external trusted (and incorruptible) party is willing to help the parties carry out their computation. In such a world, the parties can simply send their inputs to the trusted party, who then computes the desired function and passes each party its prescribed output. Since the only action carried out by a party is that of sending its input to the trusted party, the only freedom given to the adversary is in choosing the corrupted parties’ inputs. Note that all of the above-described security properties (and more) hold in this ideal computation. For example, privacy holds because the only message ever received by a party is its output (and so it cannot learn any more than this). Likewise, correctness holds since the trusted party cannot be corrupted and so will always compute the function correctly.

Of course, in the “real world”, there is no external party that can be trusted by all parties. Rather, the parties run some protocol among themselves without any help, and some of them are corrupted and colluding. Despite this, a secure protocol should emulate the so-called “ideal world”. That is, a real protocol that is run by the parties (in a world where no trusted party exists) is said to be secure, if no adversary can do more harm in a real execution that in an execution that takes place in the ideal world. This can be formulated by saying that for any adversary carrying out a successful attack in the real world, there exists an adversary that successfully carries out an attack with the same effect in the ideal world. However, successful adversarial attacks *cannot* be carried out in the ideal world. We therefore conclude that all adversarial attacks on protocol executions in the real world must also fail.

More formally, the security of a protocol is established by comparing the outcome of a real protocol execution to the outcome of an ideal computation. That is, for any adversary attacking a real protocol execution, there exists an adversary attacking an ideal execution (with a trusted party) such that the input/output distributions of the adversary and the participating parties in the real and ideal executions are essentially the same. Thus, a real protocol execution “emulates” the ideal world. This formulation of security is called the ideal/real simulation paradigm. In order to motivate the usefulness of this definition, we describe why all the properties described above are implied. Privacy follows from the fact that the adversary’s output is the same in the real and ideal executions. Since the adversary learns nothing beyond the corrupted party’s outputs in an ideal execution, the same must be true for a real execution. Correctness follows from the fact that the honest parties’ outputs are the same in the real and ideal executions, and from the fact that in an ideal execution, the honest parties all receive correct outputs as computed by the trusted party. Regarding independence of inputs, notice that in an ideal execution, all inputs are sent to the trusted party before any output is received. Therefore, the corrupted parties know nothing of the honest parties’ inputs at the time that they send their inputs. In other words, the corrupted parties’ inputs are chosen independently of the honest parties’ inputs, as required. Finally, guaranteed output delivery and fairness hold in the ideal world because the trusted party always returns all outputs. The fact that it also holds in the real world again follows from the fact that the honest parties’ outputs are the same in the real and ideal executions.

We remark that in some cases, the definition is relaxed to exclude fairness and guaranteed output delivery. The level of security achieved when these are excluded is called “security with abort”, and the result is that the adversary may be able to obtain output while the honest parties do not. There are two main reasons why this relaxation is used. First, in some cases, it is impossible to achieve fairness; it is impossible to achieve fair coin tossing for two parties (Cleve 1986). Second, in some cases, more efficient protocols are known when fairness is not guaranteed. Thus, if the application does not require fairness (and in particular in cases where only one party receives output), this relaxation is helpful.

## 4.2.2. Additional definitional parameters

## 4.2.3. Adversarial power

The above informal definition of security omits one very important issue: the power of the adversary that attacks a protocol execution. As we have mentioned, the adversary controls a subset of the participating parties in the protocol. However, we have not defined what power such an adversary has. We describe the two main parameters defining the adversary: its allowed adversarial behavior (i.e. does the adversary just passively gather information or can it instruct the corrupted parties to act maliciously) and its corruption strategy (i.e. when or how parties come under the “control” of the adversary):

### 1) Allowed adversarial behavior

The most important parameter that must be defined relates to the actions that corrupted parties are allowed to take. There are three main types of adversaries:

#### a) Semi-honest adversaries

In the semi-honest adversarial model, even corrupted parties correctly follow the protocol specification. However, the adversary obtains the internal state of all the corrupted parties (including the transcript of all the messages received), and attempts to use this to learn information that should remain private. This is a rather weak adversarial model, but a protocol with this level of security does guarantee that there is no inadvertent data leakage. In some cases, this is sufficient, although in today’s adversarial environment, it is often insufficient. Semi-honest adversaries are also called “honest-but-curious” and “passive”. (Sometimes, fail-stop adversaries are also considered; these are essentially semi-honest adversaries who may also halt the protocol execution early.)

#### b) Malicious adversaries

In this adversarial model, the corrupted parties can *arbitrarily* deviate from the protocol specification, according to the adversary’s instructions. In general, providing security in the presence of malicious adversaries is preferred, as it ensures that no adversarial attack can succeed. Malicious adversaries are also called “active”.

#### c) Covert adversaries (Aumann and Lindell 2010)

This type of adversary may behave maliciously in an attempt to break the protocol. However, the security guarantee provided is that if it does attempt such an attack, then it will be detected with some specified probability that can be tuned to the application. We stress that unlike in the malicious model, if the adversary is not detected then it may successfully cheat (e.g. learn an honest party’s input). This model is suited to settings where some real-world penalty can be associated with an adversary being detected, and the adversary’s expectation is to lose overall if it attempts an attack.

### 2) Corruption strategy

The corruption strategy deals with the question of when and how parties are corrupted. There are three main models:

#### a) Static corruption model

In this model, the set of parties controlled by the adversary is fixed before the protocol begins. Honest parties remain honest throughout and corrupted parties remain corrupted.
