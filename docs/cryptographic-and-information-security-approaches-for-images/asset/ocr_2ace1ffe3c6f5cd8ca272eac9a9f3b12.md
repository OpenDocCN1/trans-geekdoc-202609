The basic watermarking scheme for document watermarking is explained by Cox [4]; it is a spread-spectrum scheme in which host document size is greater than the watermark size. In this scheme the watermark data is spread all over the host data. The watermark data is inserted into every important text of host document data using a modification function. This scheme is known as additive watermarking where a pseudo-random noise sequence is inserted as a watermark pattern, and watermark data is extracted by correlation of this noise sequence.

The text line in the document is considered as a text character D = {D₁, D₂… Dₘ} and watermark is considered as a watermark bit w = {w₁, w₂… wₙ}, where N ≥ M. The modification function modifies or shuffles watermark bits before inserting them into the text of host document. This function also provides security to watermark bits before they are embedded into the host document D. The modified watermark bits are inserted into the text of the host document using linear embedding operations such as XOR, as given in Equations 12.3 and 12.4. The other linear embedding operations may be additive operation and multiplicative operation. In additive operation, the watermark data is added to the host data in order to generate watermarked data. In multiplication operation, the watermark data is multiplied with host data to generate watermarked data.

σ(w) = {w₁', w₂', …, wₙ'}  (12.3)

D' = D ⊕ K × σ(w) = {D₁ ⊕ K w₁', D₂ ⊕ K w₂', …, Dₙ ⊕ K wₙ'}  (12.4)

The watermark extraction extracts a watermark w from the piece of the watermarked documents D' in two ways: non-blind scheme and blind scheme. In the non-blind scheme, extraction requires knowledge of the text of the original document D. In the blind scheme, extraction do not required knowledge of the text of the original document D.

Y(D, D', w, K, σ) = Authenticated if w is extracted from D'  (12.5)

Y(D, D', w, K, σ) ≠ Unauthenticated if w is extracted from D'  (12.6)

In any document watermarking scheme, the secret key plays an important role in providing the security. As per Kerckhoffs’ principle [25,26], a programmer assumes that the impostor knows every information except secret key. All document watermarking techniques create its own secret key from random number generator. This secret key is needed at the embedding side as well as at the extraction side. The secret key is a discrete random number and is uniformly distributed. The secret key can be public or private. The public key is transmitted over open network for extraction of watermark data from the watermarked document file. The private key is only transmitted to authorized user who has rights to access watermark information from the watermarked document file. The basic methods use symmetric key