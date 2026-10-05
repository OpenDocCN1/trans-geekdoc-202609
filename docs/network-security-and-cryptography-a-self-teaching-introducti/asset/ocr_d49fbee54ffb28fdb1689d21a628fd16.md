# CHAPTER 3

# OVERVIEW OF CRYPTOGRAPHY

Chapter Outline

+   - Introduction
- Basic Terms Related to Cryptography
- Requirements of Secure Communication
- OSI Security Architecture X.800
- Categories of Cryptographic Systems
- Symmetric (or Conventional) Encryption Model
- Exercises

# 3.1 INTRODUCTION

In the old days, Cryptography was used for converting plain messages (called *plaintext*) to an unintelligible form (called *Cipher-text*). The idea was to render the messages incomprehensible. The messages, in such an unintelligible form, were communicated to the intended recipients. The recipients, with the prior knowledge of the decryption key, could decrypt the messages.

The process of transforming the messages from a plaintext form to a cipher-text is called *Encryption*, and the process of transforming the cipher-text to plaintext is called *Decryption*. This description is possible only with the use of a *Decryption Key*, which has to be communicated to the recipients prior to the transmission of encrypted messages. Then the recipients will be able to extract the original plaintexts from the received