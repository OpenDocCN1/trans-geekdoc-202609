![](bbox=[0.13, 0.14, 0.88, 0.46])

# Figure 12.5 Zero watermarking based document watermarking approach.

identification of the document. Figure 12.5 shows the basic flow of the zero watermarking based document watermarking approach.

In a figure, first, the watermark is generated using text information and a secret key. This generated watermark and secret key can be certified by CA. The watermark extractor extracts watermark information from the watermarked text using the blind-extraction approach. Finally, a comparison of the extracted watermark with the original watermark is made for the decision about tampering of the document.

# 12.3 Attacks on Document Watermarking

The watermarking attacks play an important role in checking performance and comparison of different watermarking techniques. The standard watermarking attacks used for any watermarking scheme are given by Voloshynovskiy [34]. These attacks are divided into various types: removal attacks, geometric attacks, cryptographic attacks and protocol attacks. The watermarking attacks such as noise addition, filtering, compression, and geometric attacks can be applied on watermarked text image. The attacks modeled [35] for document watermarking is given below:

# 12.3.1 Collusion Attacks

If an impostor has obtained multiple watermarked documents copies, the impostor tries to extract watermark data, even if impostor knows nothing about the algorithm.