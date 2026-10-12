
*   Step 3: Patient inputs her password and biometric hash to the mobile device. Then, the mobile device computes `h(PW∥R[U])` and verifies it with `P[1]`. If the verification holds, mobile device retrieves `A[2] = P[1] ⊕ P[2]`, `kp = PK[i] ⊕ A[2]`. Then, the patient retrieves `M[D]` from the received `E[D]` using the key `kp`. Then, verifies `D[6]`. If the verification holds, the patient trusts the received diagnosis report from the doctor `M[D]`. Then, computes `P[8] = h(M[D]∥PW∥SID[P])`. Finally, stores `P[8]` with the corresponding `E[D]` in CS for future reference.

## 5: Security analysis

Using both formal security analysis and informal security analysis, in this section, we demonstrate that our proposed protocol is secure and prevents various known attacks.

### 5.1: Formal security analysis using real-or-random model

In this section, we show the formal security analysis of our protocol applying the widely accepted real-or-random (ROR) model [[261]](#fn261).

#### 5.1.1: Security model

This section describes the ROR security model. According to the security model, various queries and oracles are defined as follows:

*   **Participants**: Let `Π` be the set of all participants, `D` be the set of all doctors, `C` is the set of all cloud servers, and `H` is the set of healthcare centers. The symbol `Π^i` denotes the ith instance of a participant `Π`. Any instance of a participant is called an oracle.
*   **Partnering**: Partnering is expressed by the unique session ID of the participants involved in a communication. Two instances `Π^i` and `Π^j` are partnered if they have the same session ID in a session.
*   **Adversary**: In this model, it is assumed that the adversary `A` runs in polynomial time. `A` has complete control on the network and can eavesdrop, block, alter, and replay the messages. The capabilities of `A` is defined by the queries discussed here:
    *   **Execute(Π^i, Π^j)**: In response to this query, the adversary `A` obtains all the messages communicated between two authorized participants `Π^i` and `Π^j`. It models the eavesdropping attack of `A`.
    *   **Send(Π^i, msg)**: Through this query, `A` can transmit a message `msg` to an authorized participate instance `Π^i` and also receives a corresponding reply from the participant. It models the replay attack, impersonation attack, and modification attack.
    *   **CorruptMD(P)**: Through this query, the adversary `A` extracts the information stored in the patient’s mobile device. It models the mobile device lost attack.
    *   **Test(Π^i)**: This query represents the semantic security of the session key established by the participant `Π^i`. The response of `Π^i` in this test query depends on the result of an unbiased coin flip, `c`. `A` is unaware about flipped result, `c`. If `c = 1`, `Π^i` returns the actual session key to adversary `A`; else if `c = 0`, `Π^i` returns a random number in the same domain.
*   **Hash(x, k)**: Hash oracle represents the hash operation `h()` and provides output `k = h(x)` when queried with `x`. When someone queries for `h(x)`, it searches the table `(x, k)` and returns `k` if `x` appears in the table. Otherwise, it returns a uniformly random string `k` and inserts `(x, k)` to the table.
*   **Biohash(x, k′)**: Biohash oracle represents the biohash operation `h_Bio()` and provides output `k′ = h_Bio(x)` for the input `x`. When someone queries for `h_Bio(x)`, it returns `k′` if `x` matches with an existing value within a threshold. Otherwise, it returns a uniformly random string `k′` and inserts `(x, k′)` into the table.

Semantic security of the session key: Providing the earlier-discussed queries, the adversary `A` is challenged to determine the value of flipped result `c`, that is, the session key is real or random. If `A` distinguishes the real key and random key successfully, then the protocol fails to deliver semantic security. Let `Succ` represents the event in which `A` wins, that is, correctly distinguishes the real key and random key. The advantage of `A` in cracking the semantic security of protocol `P` is `Adv_P^(ake) = |2 ⋅ Pr[Succ] − 1|`. The protocol `P` is secure in ROR model if `Adv_P^(ake)` is negligible.

**Theorem 1.**

In random oracle model, an adversary `A` runs against our protocol `P` in polynomial time `t`. Let `A` executes `q_h` number of hash queries, `q_s` number of send queries, `q_b` number of biohash queries, and `q_e` number of execute queries to damage `P`. Then, the advantage of `A` in compromising the security of protocol `P` is as follows:

```
Adv_P^ake(A) ≤ q_b^2 / H_1 + q_h^2 / H_2 + 2q_s / |D_1 ∥ D_2|
```

where `|H_1|`, `|H_2|`, `|D_1|`, and `|D_2|` represents the range space of the biohash function, the range space of the hash function, the size of the uniformly distributed password dictionary, and the size of the uniformly distributed biometric template, respectively.

**Proof.**

A sequence of games from `G_0` to `G_3` is defined for this proof. In each game `G_i`, adversary `A` tries to predict the correct value of `c`. Let `Succ_i` denotes this event and `Pr[Succ_i]` represents the corresponding probability.

*   **Game G_0**: It models the actual attack of adversary `A` on our protocol `P`. Initially, the bit `c` is randomly selected. Hence, as per the definition we have
    ```
    Adv_P^ake = 2 ⋅ Pr[Succ_0] - 1.
    ```
*   **Game G_1**: To improve the winning advantage, the adversary `A` instigates eavesdropping attack using the `Execute(Π^i, Π^j)` query. Then, in the `Test(Π^i)` oracle, `A` has to determine the value of `c`. Since `SK` is computed from `R_1` and `R_2`, `A` tries to retrieve both `R_1` and `R_2` from `M_1`, `M_2`. We know that `R_1 = P_5 ⊕ A_3`. So, to extract `R_1`, `A` needs the patient’s password and biometric along with the mobile device. It is not possible to extract `R_2` without `R_1`. Thus, the eavesdropping attack does not improve the winning advantage, and we have
    ```
    Pr[Succ_1] = Pr[Succ_0].
    ```
*   **Game G_2**: In this game, the adversary `A` tries to mislead a participant instance to accept a counterfeit message with the help of `Send()`, `Hash` oracle, and `Biohash` oracle. It considers all the collisions that may arise in `P`. The adversary will not be able to find any collision because each message contains some random factors like timestamp, random number. So, according to the birthday paradox, we get
    ```
    |Pr[Succ_2] - Pr[Succ_1]| ≤ q_b^2 / (2|H_1|) + q_b^2 / (2|H_2|).
    ```
*   **Game G_3**: This game models the risks associated with the patient’s mobile device loss. By querying the `CorruptMD()` oracle `A` retrieves the stored credentials such as `P_1`, `P_2`, `P_3`. Then, `A` tries to guess both the password and biometric hash. Since, the password dictionary and biometric template are of size `|D_1|` and `|D_2|`, respectively, we have
    ```
    |Pr[Succ_3] - Pr[Succ_2]| ≤ q_s / (|D_1||D_2|).
    ```
