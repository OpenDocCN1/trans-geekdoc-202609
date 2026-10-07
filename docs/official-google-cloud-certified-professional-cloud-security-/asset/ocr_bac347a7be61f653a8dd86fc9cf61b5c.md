# Key management options

+   - If you are performing a composition operation on objects encrypted by CSEKs, the component objects must be encrypted by the same key, and you need to provide the key with the compose request. The resulting composite object is encrypted by the same key.

Now that you understand the restrictions of CSEKs with Google Cloud Storage, here is how you can use CSEKs with gsutil.

# CSEKs with gsutil

To use a CSE with gsutil, add the encryption_key parameter to the [GSUtil] section of your boto configuration file. encryption_key is an RFC 6848 Base64-encoded string of your AES-256 encryption key.

You can optionally specify one or more decryption keys, up to 100. While the encryption_key option is used by gsutil as both an encryption and decryption key, any decryption_key options you specify are used only to decrypt objects. Multiple decryption keys must be listed in the boto configuration file as follows:

```
decryption_key1 = ...
dryption_key2 = ...
dryption_key3 = ...
```

If you have encryption or decryption keys in your boto configuration file, they are used for all gsutil commands. When decrypting, gsutil calculates the SHA256 hash of the supplied encryption and decryption keys and selects the correct key to use for a particular object by matching the SHA256 hash in the object's metadata.

Objects encrypted with CSEKs require the matching decryption key during encryption key rotation. If an object is encrypted using a CSEK, you can rotate the object's key by rewriting the object. Rewrites are supported through the JSON API, but not the XML API.

Now that we have seen how CSEKs are used with Cloud Storage, let us see how they can be used with Compute Engine.

# CSEKs with Compute Engine

Compute Engine encrypts all data at rest on the persistent disks using Google default encryption keys. You can bring your own encryption key if you want to control and manage this encryption yourself.

If you provide your own encryption key, Compute Engine uses your key to protect the Google-generated keys used to encrypt and decrypt your data. Only users who can provide the correct key can use resources protected by a CSEK.