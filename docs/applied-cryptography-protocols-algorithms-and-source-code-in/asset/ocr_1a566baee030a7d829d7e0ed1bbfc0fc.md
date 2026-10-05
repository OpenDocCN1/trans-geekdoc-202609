# 280 CHAPTER 12 Data Encryption Standard (DES)

criteria at the request of the NSA. ... “The NSA told us we had inately reinvented some of the deep secrets to make its own algorithms,” explains Tuchman.

Later in the article, Tuchman is quoted: “We developed the DES algorithm entirely within IBM using IBMers. The NSA did not dictate a single wire!” Tuchman reaffirmed when he spoke on the history of DES at the 1992 National Computer Security Conference.

On the other hand, Copersham wrote [373,374]: “The National Security Agency [NSA] provided technical advice to IBM.” And Konheim has been quoted as saying—“We sent the S-boxes to Washington. They came back and were all different. We ran our tests and passed.” People have pointed to this as evidence that the NSA put a trapdoor in DES.

NSA, when questioned regarding any proposed weakness in DES, said [363]:

Regarding the Data Encryption Standard [DES], we believe that the public record from the Senate Committee for Intelligence's investigation in 1978 into NSA's role in the development of the DES is responsive to your question. Committee report indicates that NSA did not tamper with the design of the algorithm in any way and that the security afforded by the DES was more adequate for at least a 5–10 year span for the unclassified data for which it was intended. NSA did not impose or attempt to impose any weakness on the DES.

Then why did they modify the S-boxes? Perhaps it was to ensure that IBM did no reason to trust IBM's researchers, and would be in their duty if they did not make sure that DES was free of trapdoors. Dictating the S-boxes is one way they could make sure.

Very recently new cryptanalysis results have shown some light on this issue, but for many years this has been the subject of much speculation.

# Weak Keys

Because of the initial key is modified to generate a subkey for each round of the algorithm, initial keys are weak keys [721,427]. Remember that the key is split into two halves, and half is split independently. If all the bits in each half are either 0 or 1, then the key used for any cycle of the algorithm is the same for all cycles of the algorithm. This can occur if the key is entirely 1s, entirely 0s, or if one of the half is entirely 1s and the other half is entirely 0s. Also, two of the weak keys have other properties that make them less secure [427].

The four weak keys are shown in hexadecimal notation in Table 12.11. [Remark that every bit is a parity bit.]

Additionally, some pairs of keys encrypt plaintext the identical ciphertext. In other words, one key in the pair can decrypt messages encrypted with the other key This is due to the way that DES generates subkeys; instead of generating 16 different subkeys, these keys generate only two different subkeys. Each of these subkeys is used eight times in the algorithm. These keys are called semiweak keys, and are shown in hexadecimal notation in Table 12.12.