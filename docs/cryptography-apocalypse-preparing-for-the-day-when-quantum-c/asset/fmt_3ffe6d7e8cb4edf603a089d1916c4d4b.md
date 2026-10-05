
You can buy working QRNGs in all sorts of form factors from multiple vendors, ranging from a small original equipment manufacturer (OEM) chip to servers starting at prices under a thousand dollars. They are certified to work with many operating systems, including Windows, Linux, BSD, Solaris, and Apple. They have code libraries, APIs, and interfaces to several programming languages. Companies needing the services of QRNG have been buying and using them for a long time. QRNGs are in use in banking, science, lotteries, telecoms, finance, and the military.

Swiss company ID Quantique (`www.idquantique.com/random-number-generation/overview/`) was the first company to have a real-world working QRNG way back in 2001. They have released many ever-maturing products since. [Figure 7.2](#c07.xhtml#c07-fig-0002) shows three different ID Quantique QRNG products built to be plugged into a computer's internal interface slot.

Other companies with QRNGs for sale include Australia's Quintessence Labs (`www.quintessencelabs.com/`), U.S.-based ComScire (`https://comscire.com`), and Canada's Quantum Numbers Corp (`www.quantumnumberscorp.com`). You'll find a good summary article on these companies and their products here: `www.nanalyze.com/2017/02/quantum-random-number-generator-qrng/`. You can even generate and use your own quantum-generated random number on several free places on the Internet, including `https://qrng.anu.edu.au`.

### NIST QRNG Public Beacon

NIST created a QRNG in 2018 (`www.nist.gov/news-events/news/2018/04/nists-new-quantum-method-generates-really-random-numbers`) by shining a high-intensity laser into a crystal to create entangled photons. The randomness was proven to be to “within one trillionth of 1 percent,” which is about as good as it gets. The goal of NIST's project is to create a public randomness beacon that anyone and any program can use (`https://csrc.nist.gov/projects/interoperable-randomness-beacons`). Initially NIST was going to develop a private service but decided that the world could benefit by having a trusted public QRNG source of truth.

![Figure 7.2: Example ID Quantique QRNGs ¶ Courtesy of ID Quantique](images/c07f002.png)

[**Figure 7.2**](#c07.xhtml#R_c07-fig-0002)**:** Example ID Quantique QRNGs ¶ Courtesy of ID Quantique

### QRNG Disadvantages

Disadvantages of QRNGs include cost and interoperability. You can buy relatively cheap QRNGs (starting around several hundred dollars), but PRNGs are free or nearly free. Every computer already has one or more built in. To use a QRNG, you have to buy, install, interface, and use it. Currently, very few applications work with QRNGs, and no super popular off-the-shelf software works by default with QRNGs. The QRNG vendors have created software and drivers to allow existing applications to interface with their products, but most applications don't yet have the necessary “hooks.” They can be fairly easily added by a developer, but they just don't exist for the vast majority of RNG-relying applications. Contrast that with traditional RNGs, which are already currently used by every existing device and relying application.

QRNGs are welcomed devices for even the pre-quantum world because they give us provably random numbers and can only improve all dependent cryptographic operations, classical and quantum.

## Quantum Hashes and Signatures

This section discusses quantum-based hashes and digital signatures.

### Quantum Hashes

As previously covered, hashes are one-way cryptographic functions that create/output a unique representative set of characters or bits (known as the hash, hash result, digital signature, or message digest) for examined unique content. Hashes are required and used in many other cryptographic processes such as encryption and digital signing. Traditional hashes are quantum-susceptible to pre-image attacks (although not collisions per `https://cr.yp.to/hash/collisioncost-20090517.pdf`). Accordingly, quantum-based hashes are needed.

Quantum-based hashes can take either traditional binary inputs or quantum inputs and return a hash based on quantum states. Quantum hashes that take binary content and return a quantum hash are known as *classical-quantum*. Like any other hash, traditional or quantum, it should be resistant to pre-image attacks, second pre-image attacks, and collisions. Quantum hashes naturally lead to quantum-based digital signatures.

A number of quantum-based hashes meet these conditions, although most have not been well tested over time. Although some quantum hashes have been implemented in real working devices, most are simply thought experiments to prove that quantum hashing is possible and can be implemented at scale when desired. Many scientific research papers are available regarding quantum hashes.

As an example, in 2013 Russians Farid Ablayev and Alexander Vasiliev proposed a theoretical classical-quantum hash (`https://arxiv.org/pdf/1310.4922v1.pdf`). Their quantum-hash algorithm (see [Figure 7.3](#c07.xhtml#c07-fig-0003)) is mathematically complex, containing enough advanced math that it is probably off-putting to most non–math majors. In a nutshell, using math proofs they both propose and prove all the necessary required hash properties as represented by quantum properties.

![Figure 7.3: Mathematical representation of Ablayev and Vasiliev's quantum-hash algorithm](images/c07f003.png)

[**Figure 7.3**](#c07.xhtml#R_c07-fig-0003)**:** Mathematical representation of Ablayev and Vasiliev's quantum-hash algorithm

Their crucial argument is that their algorithm allows qubits to accurately and uniquely represent any message *n* bits long with no more than `O(log n)` qubits. Without getting into the details, `O(log n)` essentially means less than *n* qubits required for each bit of the hashed message, which theoretically means the original message cannot ever be obtained from the smaller resulting hash.

> **NOTE**  If you are interested in learning more about what `O(log n)` mathematically represents, see `www.quora.com/How-can-we-check-for-the-complexity-log-n-and-n-log-n-for-an-algorithm`, and `www.quora.com/How-would-you-explain-O-log-n-in-algorithms-to-1st-year-undergrad-student-Can-any-one-explain-it-with-mathematical-proof-for-log-n-complexity-by-taking-a-simple-example-like-Binary-search-and-simple-to-understand`.

#### Holevo's Bound

Ablayev and Vasiliev's algorithm relies on another quantum theorem known as *Holevo's Bound* (`https://en.wikipedia.org/wiki/Holevo%27s_theorem`). This theorem says that a qubit can be one of two states, but when it is measured (decohered), it must break down into a measurement represented by only one of two states—one state of information is lost in each qubit measurement (i.e., a bit with only two states cannot accurately measure a property with three possible states). To accurately represent a single qubit (which can be three possible states) would require at least two binary bits (2 bits = 2² = 4, meaning they can represent 4 possible states).

They end their paper by creating a quantum-based digital fingerprint algorithm based on their hash. The paper and their research was funded by a Russian Foundation for Basic Research grant. Both hash creators went on to define even more quantum hashes and even discovered and proved even more complex math that could be used to base any quantum hash on.

For more information on quantum hashes, see `www.bjmc.lu.lv/fileadmin/user_upload/lu_portal/projekti/bjmc/Contents/4_4_17_Ablayev.pdf`.

### Quantum Digital Signatures
