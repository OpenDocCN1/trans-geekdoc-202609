
Users with access to the SAP HANA OS can potentially access unencrypted data hosted in the data or log volumes. Most organizations vigorously restrict access to the OS of on-premise implementations of SAP HANA, but organizations leveraging hosted or cloud-based SAP HANA implementations might have limited control over users with OS-level access or physical access to the storage drives. When access to the OS can’t be properly validated, we highly recommend that backup, data, and log volume encryption be used. The same is true when individuals with physical access to the disk drives aren’t properly managed.

Now, let’s review how SAP HANA manages the root keys used for encryption.

### 13.3.1 Server-Side Data Encryption

SAP HANA has a built-in encryption service to help you manage the encryption of data hosted in the data and log volumes. This service uses a secure store in the file system (SSFS) to protect the encryption root keys. Encryption root keys are the basis for all public or private keys used to encrypt data or communications within the SAP HANA system. SAP HANA has two SSFSs. The first SSFS is the SAP HANA instance SSFS, which protects the root keys used to encrypt information stored in the data and log volumes. The second SSFS is the system PKI SSFS, which protects root certificates used to secure internal communications.

The instance SSFS key is stored on the OS in the following location by default:

`/usr/sap/<SID>/SYS/global/hdb/security/ssfs`

Replace the `<SID>` variable in the example with the SID of your SAP HANA system. Within the folder location, you’ll find two files: `SSFS_<SID>.DAT` and `SSFS_<SID>.KEY`.

The system PKI SSFS key is stored on the OS in the following location by default:

`/usr/sap/<SID>/SYS/global/security/rsecssfs/data`

Replace the `<SID>` variable in the example with the SID of your SAP HANA system. Within the folder location, you’ll find two files: `SSFS_<SID>.DAT` and `SSFS_<SID>.KEY`.

Given their importance, these keys should be backed up and stored in a root key backup file. This backup file and its location must be accessible by the administrator during a recovery situation for a new SAP HANA host or a host with a new key generated after the backup file’s creation date. When data or log volume encryption is enabled, the SSFS will need to be restored from a backup prior to a database recovery. However, if you’re restoring a backup to the same SAP HANA database used to generate the backup files and the SSFS keys weren’t changed following the backup, SSFS key recovery is not necessary. The backup media can be restored because the SSFS on the target match the SSFS keys active during backup.

Next, we’ll provide more details about the processes used to back up and restore SSFS keys. Your organization must maintain backups of your SSFS keys each time they’re changed and prior to enabling backup, data, or log volume encryption. If you lose your SSFS keys and SAP HANA system, you won’t be able to recover the database to another SAP HANA instance.

### 13.3.2 Managing Root Keys within the SSFS

A unique root key is generated during the standard installation or upgrade of each SAP HANA instance. A standard installation is one in which a documented SAP HANA installation method is followed. However, because SAP HANA is often delivered as an appliance, the appliance vendor may have used a copy of the same encryption root keys within each of its appliance builds. For example, the vendor might deploy a copied image of the SAP HANA appliance’s file system. Using an image provides for the quick and consistent deployment of the SAP HANA software, but each default instance ends up using the same root keys and SSFSs. Organizations also must consider the security of the SSFS and its keys during installation. SAP HANA currently must be deployed by a certified vendor or certified individual. That individual could make a copy of the root keys and store them insecurely outside of the organization’s control. As a result, no guarantee can be made that a copy of the encryption root keys doesn’t exist outside the organization. These keys should therefore be changed after the vendor has completed the installation.

Therefore, often an organization will need to generate new encryption root keys following the initial deployment of the SAP HANA system. Starting with SAP HANA 2.0, when new root keys are generated, the SSFS should be backed up. To generate new keys, organizations can execute a series of SQL statements. To perform a backup of the SSFS, command line access to the operating system is required. The process used to generate new root keys in SAP HANA 2.0 is as follows:

1. Generate new root keys using SQL commands.
2. Back up the new keys and store them in a secure file location.
3. Activate the new keys using SQL commands.

To properly perform these activities, grantees will need the `<sid>adm` operating system credentials to execute the command line utility `hdbnsutil`. The grantee will need the ENCRYPTION ROOT KEY ADMIN system privilege. You also need to establish a password for the root key backup file. To establish this password, execute the following SQL statement:

```
ALTER SYSTEM SET ENCRYPTION ROOT KEYS BACKUP PASSWORD "<Password>";
```

To generate new root keys for the SAP HANA data volume, execute the following SQL command:

```
ALTER SYSTEM PERSISTENCE ENCRYPTION CREATE NEW ROOT KEY WITHOUT ACTIVATE;
```

To generate new root keys for the SAP HANA log volume, execute the following SQL command:

```
ALTER SYSTEM LOG ENCRYPTION CREATE NEW ROOT KEY WITHOUT ACTIVATE;
```

To generate new root keys for SAP HANA’s internal application encryption, execute the following SQL command:

```
ALTER SYSTEM APPLICATION ENCRYPTION CREATE NEW ROOT KEY WITHOUT ACTIVATE;
```

With all three of these SQL statements, notice that the `WITHOUT ACTIVATE` option was specified. This option allows new keys to be generated without making them active within the system. You must back up the root keys prior to their activation but just after their creation. To do so, you can use the `hdbnsutil` command line utility. To use this utility, log on to the SAP HANA operating system with the `<sid>adm` credentials. Alternately, you can execute a SQL statement that returns a CLOB field containing an encrypted text message. You can copy the text message to a file and save it with the `.rkb` extension.

To use the `hdbnsutil` command line utility, log on to the SAP HANA system using your Secure Shell (SSH) service of choice. Log on to the shell using the `<sid>adm` credentials. This utility is stored in `/usr/sap/<sid>/HDB<instance_number>/exe`. Execute the following command to back up the root keys:

```
./hdbnsutil -backupRootKeys <file path and name>.rkb --dbid=<dbid> --type='ALL'
```

If SAP HANA is a single-container system, you can omit the `–dbid=<dbid>` portion of the command. The variable `<dbid>` should be replaced with the tenant database ID.

If you don’t have access to the operating system shell, you can also execute a SQL statement to return a CLOB field containing the contents of the RKB file. Copy and save the contents of the CLOB field to a file with the `.rkb` extension. To return the CLOB field, execute the following SQL:

```
SELECT ENCRYPTION_ROOT_KEYS_EXTRACT_KEYS 
('PERSISTENCE, APPLICATION, LOG') FROM DUMMY
```

Before activating the new root keys, you must validate that you have the correct password required to restore the root keys. To do so, execute the following command from the SAP HANA OS shell:

```
./hdbnsutil -validateRootKeysBackup <path to filename> --password="<password>"
```
