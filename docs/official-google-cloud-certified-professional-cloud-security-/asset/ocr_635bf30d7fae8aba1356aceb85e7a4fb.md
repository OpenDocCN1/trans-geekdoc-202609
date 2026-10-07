# Cloud Data Loss Prevention

Now let us go over each deidification configuration.

# replaceConfig

replaceConfig will replace any sensitive data with a string you specify.

# redactConfig

redactConfig redacts a value by removing it completely.

# characterMaskConfig

Setting characterMaskConfig to a CharacterMaskConfig object partially masks a string by replacing a given number of characters with a fixed character. Masking can start from the beginning or end of the string.

# cryptoHashConfig

Setting cryptoHashConfig to a CryptoHashConfig object performs pseudonymization on an input value by generating a surrogate value using cryptographic hashing.

This method replaces the input value with an encrypted digest, or hash value. The digest is computed by the SHA-256 hash of the input value. The method outputs a base64-encoded representation of the hashed output. Currently, only string and integer values can be.

# dateShiftConfig

Setting dateShiftConfig to a DateShiftConfig object performs date shifting on input value by shifting the dates by a random number of days.

Date-shifting techniques randomly shift a set of dates but preserve the sequence and duration of a period of time. Shifting dates is usually done in relation to an individual or an entity. You might want to shift all of the dates for a specific individual using the same shift difference or use a separate differential for each individual.

Now that you have understood different methods of de-identification, let us go over a tutorial on how to do this in practice. Make sure you have a Google Cloud project ready to execute the steps covered next.

# Tutorial: How to identify and tokenize sensitive data

Cloud DLP supports both reversible and non-reversible cryptographic methods. In order to re-identify content, you need to use a reversible method. The cryptographic method described here is called deterministic encryption using Advanced Encryption Standard in Synthetic Initialization Vector mode (AES-SIV). We recommend this among all reversible cryptographic methods that Cloud DLP supports because it provides the highest level of security.