+   3. Controlling Keys: A public-private key pair will be created to control the record.

+   4. The last step will be determining either of the following options

+   1. Create a Master Record

In this scenario, the local client will initiate the creation of a Master Record according to the steps highlighted in the Master Record section. Once this is done, the public key along with the identifier will be registered on the Record Chain under the Master Record.

+   ii. Link to an existing Master Record

This is the case when a user wants to access their record from multiple machines. This requires two things, a) authorising the new device record b) copying the local data from an existing device record. These steps will require the use of an existing device record. The chain of steps are as follows:

+   1. The new device record creates a QR code containing its public key and identifier.

+   2. This is scanned using the existing device record. It then forms an encrypted communication channel with the new device record and sends the data encrypted with its public key.

+   3. The existing device then adds the identifier and public key of the new device on the Record Chain under their common Master Record thus authorizing the new device record.

Maintaining consistency between multiple device records without decrypting the data stored in the Cloud can present some problems. Though the consideration of storing a private key for the Master Record in every device wallet is very viable from deployment, ease of construction, and operational purposes, the security is far less than the proposed model. Methods of consistency maintenance similar to versioning software can provide some insight on how to approach this problem.

A few other important things to note here is that a single patient can create more than one record for greater security. Although managing identifiers across various records can prove to be cumbersome. Also, the user can also discard the option to store their backups in Cloud Storage and take the responsibility for backup and recovery.