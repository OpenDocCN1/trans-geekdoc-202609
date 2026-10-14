
![](img/f4c3bcc9f5332d57a8ec85a75075f8da_356_0.png)

### Figure 12.4 Syntactic sentence based document watermarking approach.

sentences in the document. The language processing algorithms are used to find syntax structures of the text while changing the watermark bits [23]. Figure 12.4 shows the syntactic based document watermarking approach. The syntactic tree can be constructed using various tools such as syntactic tool, wordnet, and dictionary.

### 12.2.4 Semantic Based Approach

The semantic structures of text in the document are used for embedding watermarks in this approach. The text information contents have various characteristics (e.g., verbs, spelling, different grammar rules and structure of sentences, etc.), which are used for embedding the watermark data in the text of the document. This approach depends on the language and has limited applicability for document watermarking. The scheme based on this approach uses natural language processing schemes to analyze text formation and to perform a transformation on it.

### 12.2.5 Structure Based Approach

This approach is recently used for document watermarking. In this approach, the text structure is used to embed the watermark data. A document watermarking scheme, which is based on double letter occurrences in text information, is chosen for watermark data embedding [33]. The algorithm in [33] uses a combination of encryption, steganography and watermarking for the protection of text in the document file.

### 12.2.6 Zero Watermarking Based Approach

The original text in documents can be modified by advanced techniques on the computer so that researchers can develop new watermarking approaches with higher imperceptibility capacity. This watermarking approach is known as a Zero Watermarking approach where no watermark bit is embedded into the text of the document. The approach is to find bit stream from the text's features to generate watermark information. This approach does not modify the text in the document but generates watermark information from the document texts which is to be registered by a Certifying Authority (CA). This approach is mainly used for tamper

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_357_0.png)

### Figure 12.5 Zero watermarking based document watermarking approach.

identification of the document. Figure 12.5 shows the basic flow of the zero watermarking based document watermarking approach.

In a figure, first, the watermark is generated using text information and a secret key. This generated watermark and secret key can be certified by CA. The watermark extractor extracts watermark information from the watermarked text using the blind-extraction approach. Finally, a comparison of the extracted watermark with the original watermark is made for the decision about tampering of the document.

## 12.3 Attacks on Document Watermarking

The watermarking attacks play an important role in checking performance and comparison of different watermarking techniques. The standard watermarking attacks used for any watermarking scheme are given by Voloshynovskiy [34]. These attacks are divided into various types: removal attacks, geometric attacks, cryptographic attacks and protocol attacks. The watermarking attacks such as noise addition, filtering, compression, and geometric attacks can be applied on watermarked text image. The attacks modeled [35] for document watermarking is given below:

### 12.3.1 Collusion Attacks

If an impostor has obtained multiple watermarked documents copies, the impostor tries to extract watermark data, even if impostor knows nothing about the algorithm.

Usually, these attacks that rely on possession of many watermarked documents are known as collusion attacks.

### 12.3.2 Removal Attacks

There are two scenarios in dealing with these attacks. In the first scenario, an impostor who has knowledge about watermark inserting steps and private key explores the weakness of the inserting algorithm without the knowledge of watermark extraction. An imposter identifies the distortions occurring in the text of documents which the extractor cannot compensate and then applies a masking attack to remove the watermark data from the watermarked content. In the second scenario, an impostor has no knowledge of watermark embedding but tries to get watermark by exploring the knowledge of watermark extraction. An imposter may apply iterative modifications on a watermarked document in the attempt to gain the watermark data.

### 12.3.3 Syn Attack and Birthday Attack

These attacks depend on the structure of the sentence and are a synonym substitution for destroying text watermark information in watermarked content.

### 12.3.4 Holliman-Memon and Parity Attack

Holliman and Memon [30] defined counterfeiting attacks for watermark techniques that operates block independently. One can transfer a watermark from one watermark image to another image irrespective of the knowledge of detection algorithms and secret keys.

## 12.4 Document Watermarking Schemes

The document watermarking started around 1993. After that, many watermarking schemes are designed and proposed for text protection in documents. The description of various watermarking schemes is given below.

### 12.4.1 Image Based Document Watermarking Schemes

The algorithms are designed for hiding the watermarks in scanned documents. The text which is in the form of an image is used as watermark, and hence is called “image based” document watermarking. Often, the spatial properties of text image are modified by watermark data. Alternately, transform domains, additive noise, and other techniques can be used to the text image modification.

The scheme based on text document images is proposed by Kim et al. [36]. They used space statistics of interword to insert watermark information based on the preprocessing system which relies on white spaces between cover document texts. The shifting of the text character was conducted to insert a watermark bit (0 or 1) in this scheme. Wan et al. [37] proposed a document watermarking scheme with high payload capacity. The interword spaces are used in this scheme to embed watermark data. This approach maximized embedding payload capacity. Huang and Yan [38] implemented a different scheme for text as a binary image. The sine wave characteristics of spaces of interword in the line texts are used to insert the watermark bit. The sampling points of interword spaces are used in construction of sine watermark, and this watermark data is inserted in terms of sine wave with in-phase sampled sine wave of the line text. Puhan et al. [39] have proposed text authentication scheme using binary document images. In this scheme, the document image is divided into nonoverlapping blocks and then is inserted with the hash value of watermark in each block of image. The watermark bits which are extracted pixel-wise provide robustness against various text attacks such as Holliman-Memon parity.

In Afrakhteh et al. [40] scheme, the watermark data is inserted into partitions of the host image. The embedding of a watermark image is performed by multiplying with a gain factor which ranges from 0 to 1. The watermark extraction is performed using normalization for achieving better accuracy. In this scheme, watermark data could be extracted by an impostor. This scheme is not applicable for text image which is prone to attacks such as Rotation, Scaling and Cropping (RSC). Du and Zhao [41] developed a scheme using Human Visual System (HVS) for color text documents. In this scheme, the lower four bits of each character of RGB components are used for inserting watermark bits. The watermark data is converted into an encrypted vector by using Huffman encoding and is then segmented into 12 bits for embedding 4 bits. The watermark insertion process is performed in a repetition manner for the whole text in the document. The average capacity of this scheme is around 8.6 bit rate.

Xia et al. [42] proposed two Chinese documents watermarking schemes. In the first scheme, spacing of the text character is used to insert bit 1 or 0. The spacing of text characters is calculated using pixel numbers between the characters and is grouped into two groups. If the length of group space is greater than average space of character bit 1 is embedded; otherwise, bit 0 is embedded. In the second scheme, boundary of each character is used for calculation of character height with respect to horizontal reference line. Watermark bits are inserted by shifting position of characters upper or lower than the reference line. This scheme provides more payload capacity but less robust against copy attacks. Yazdani et al. [43] designed a scheme for watermarking Persian text documents. In this scheme, the Persian letters like ‘ع, て, ع’ which have curved characteristics is taken from the document file. The watermark bits are embedding by shifting specific pixels in the selected text for embedding watermark bit 1 while shifting of text is not performed for
