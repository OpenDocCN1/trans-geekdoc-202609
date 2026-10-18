
3.  Decode fingerprinting constraint corresponding to digits `A` and `B` that will help to resolve operation conflict during scheduling phase.

4.  Initiate DFG scheduling based on the given resource configuration.

5.  In case of operation conflict during scheduling, apply decoded fingerprint constraints (in step 3) to resolve the conflict. `Note`: `When there are no fingerprinting constraints available, conflict is broken based on sorted ordering`.

6.  Allocate storage variables in the partially fingerprinting constraints embedded scheduling and construct a CIG to identify the least number of registers compulsory for assignment.

7.  Sort the allocated storage variables in increasing order based on their number.

8.  Construct a timing table for register allocation based on the generated CIG.

9.  Generate a list of extra edge pairs conforming to `C` digit(s) by traversing the sorted storage variables in step 7.

10.  Inject the extra edges in the CIG based on decoded fingerprint constraints and perform re-allocation of register if necessary.

After executing the aforesaid steps, a buyer fingerprint implanted IP design is produced. This buyer fingerprint implanted IP design acts as an input for implanting the seller watermark next.

Process of implanting watermark

**Broad steps:**

1.  Choose seller signature.

2.  Decode the signature to obtain equivalent watermarking constraints.

3.  Construct the CIG from the fingerprint constraints embedded scheduling.

4.  Perform re-allocation of register if necessary while inserting extra edges in CIG based on watermarking constraints.

**Detailed steps:**

1.  Accept fingerprint constraints implanted IP design as an input.

2.  Sort the allocated storage variables in increasing order based on their number.

3.  Admit a chosen signature as random blend of `i`, `I`, `T`, and `!` from seller where each character carries a unique value of additional edges to be inserted.

4.  Create a list of additional edge pairs corresponding to its encoded values by scanning the sorted nodes.

5.  Inject the extra edges in the CIG of fingerprint implanted design as watermark constraints.

6.  Alter the timing table design of register allocation based on generated watermark.

Post-execution of the aforesaid steps, an IP design with seller watermark is also produced. Therefore, the IP design contains signature of the dual entities.

#### 5.3.7 Signature detection process

This process is obligatory for any encoded signature embedding scheme. As evident, in this phase, the implanted signature constraints are detected from an IP core. It is a crucial process to resolve ownership conflict. Signature detection presented in Roy and Sengupta ([2017](#Chapter5.html#c05_bib32)) is a two-step process:

*   `Design inspection`: Design inspection step collects the pertinent evidence in terms of specification, structural feature, etc., from a signature implanted IP core design. The objective is to rebuild the controller and the datapath.

*   `Signature verification`: Signature verification step performs validation of the signatures in the received IP core. The existences of signature constraints are corroborated in the controller and datapath design to determine the seller’s and buyer’s right.

#### 5.3.8 Desirable properties of signature

The signatures embedded into the symmetrically protected IP core design contain the properties below:

*   `Lower embedding cost`: An ideal signature should incur marginal design overhead with respect to hardware area and latency. In Roy and Sengupta ([2017](#Chapter5.html#c05_bib32)), both fingerprint and watermark imposes low design overhead.

*   `Resiliency against attacks`: An ideal signature must be so strong and robust that it cannot be removed or tampered easily by an attacker. In Roy and Sengupta ([2017](#Chapter5.html#c05_bib32)), both fingerprint and watermark are equipped with strong protection. In the absence of comprehensive information of both encoding rules, it is extremely challenging to eliminate or meddle the fingerprint and watermark. Additionally, it is also difficult to identify in which HLS step the signatures are embedded. Besides, the signatures’ constraints are distributed all over the IP design which renders it more resistant against attacks.

*   `Fault tolerance ability`: An ideal signature must be distributed enough throughout the design so that partial removal of the signature constraints does not prevent the proof of ownership. As in Roy and Sengupta ([2017](#Chapter5.html#c05_bib32)), the signature scheme dispenses the constraints all over the design; therefore, ownership remains intact even after fractional elimination of the signature constraints.

*   `Adaptability to modern CAD tool`: An ideal signature must be easily adaptable into any modern CAD tool. In the approach ([Roy and Sengupta, 2017](#Chapter5.html#c05_bib32)), both the signature inserting procedure is well-suited to any CAD software. It can be incorporated effortlessly.

*   `Lower time`: An ideal signature creation process must not be very composite to generate a signature. In Roy and Sengupta ([2017](#Chapter5.html#c05_bib32)), the signature creation time for both fingerprint and watermark are significantly low. Additionally, for an authentic entity (who has the comprehensive cognizance of encoding rules), the signature detection methodology is straightforward.

### 5.4 Case study of symmetrical IP core protection

This section is divided into two subsections: the first subsection demonstrates the fingerprint formation and embedding process while next portion demonstrates the watermark formation and embedding scheme of Roy and Sengupta ([2017](#Chapter5.html#c05_bib32)). As stated earlier, fingerprint constraints of `A` and `B` have been implanted during scheduling phase by allocating particular operations to particular CS, during schedule conflict resolution mechanism. On the other hand, variable `C` injects extra edges in register allocation phase by forcing specific storage variables to implement in distinctive registers. On the contrary, watermarking constraints (as a mix of `i`, `I`, `T` and `!`) are implanted in the register allocation step by forcing specific storage variables to implement in diverse registers.

#### 5.4.1 Demonstration of fingerprinting constraints embedding process
