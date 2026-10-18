
When configuring an ODBC data source name (`DSN`) on the Windows OS, you’ll find options for configuring an SSL-based connection. Just like in SAP HANA Studio, you can choose to bypass the validation of the SSL certificate.

For example, on a Windows OS with the SAP HANA client installed, you can use the ODBC data source administrator to configure an SAP HANA ODBC DNS. Search for the ODBC manager within the Windows Start menu. With the ODBC manager open, select the System DNS tab. Click Add to set up a new DSN. In the popup window, scroll through the list of data source drivers installed on your system. Look for the driver named `HDBODBC32` or `HDBODBC` (depending on the version of the DSN you’re configuring). Select the driver and click Finish. A new window will appear, allowing you to define the Data Source Name and SAP HANA Server and Port. To configure SSL, click the Settings button at the bottom right. The SAP HDB Advanced Setup window will now appear, as shown in [Figure 13.13](#13_002.html#f13.13).

[![Configuring Windows ODBC DNS for SSL Communications](bilderklein/klein13_013.png)](img-f13.13.html)

**Figure 13.13** Configuring Windows ODBC DNS for SSL Communications

To enable SSL communications, select the Connect using SSL checkbox. If you’re using an SSL certificate that isn’t automatically trusted, leave the Validate the SSL certificate checkbox deselected. If you need to override the common name of the host listed in the SSL certificate, enter the alternative host name in the Override the Hostname in the Certificate field. Click OK to save the advanced settings and then click OK again to save the DSN.

Most JDBC connection strings will provide similar options. JDBC drivers can’t be used in the Windows ODBC manager. Most Java-based applications will provide their own SAP HANA JDBC connection configuration interfaces. Given its proprietary nature, we won’t provide a step-by-step configuration example for the JDBC driver, but note that the same SSL options available for ODBC drivers are also available for JDBC drivers. Application vendors have the API available, even if they choose not to incorporate SSL options into their configuration GUIs. For example, the code shown in [Listing 13.2](#13_002.html#l13.2) was taken from the Java-based SAP HANA Studio trace file. In the connection string, you’ll see that the `encrypt=true` and `validateCertificate=false` options were listed in the trace file results.

```
new Connection 'jdbc:sap://w3-hanan01.e-corp.internal.root:30015; 
10.54.240.31:30015'
locale=en_US
user=SYSTEM
password=***
reconnect=true
timeout=0
encrypt=true
validateCertificate=false
```

**Listing 13.2** SAP HANA Studio Trace File Showing a Secure JDBC Connection to SAP HANA

Enabling SSL communications for the JDBC or ODBC connection layers is a good practice that ensures that the information exchanged with the client and server is well protected from unauthorized access. However, configuring this setting is optional unless the SAP HANA system itself requires an SSL connection. Fortunately, SAP HANA offers an option to force clients to use an SSL secured connection, found in the Configuration tab under the path `global.ini • communication • sslenforce`. [Figure 13.14](#13_002.html#f13.14) shows an overview of this option in the SAP HANA cockpit INI configuration interface.

This option defaults to False, meaning that clients can choose how to configure the connection. When the option is set to True, clients must enable the Connect Using SSL option. Instead of using SAP HANA cockpit’s INI file editor, you can also issue the following SQL statement to enable the option:

```
ALTER SYSTEM ALTER CONFIGURATION 
('global.ini','SYSTEM')
SET ('communication','sslenforce') ='true' WITH RECONFIGURE;
```

[![Communication Setting for global.ini to Force SSL Client Connections](bilderklein/klein13_014.png)](img-f13.14.html)

**Figure 13.14** Communication Setting for global.ini to Force SSL Client Connections

To disable the option, issue the following SQL statement:

```
ALTER SYSTEM ALTER CONFIGURATION 
('global.ini','SYSTEM')
SET ('communication','sslenforce') ='false' WITH RECONFIGURE;
```

### 13.2.4 SAP HANA Cockpit

When registering systems in the SAP HANA cockpit, you can also choose to encrypt the communication. When registering the system, the option to use an encrypted connection are established in the Connection section. A series of checkboxes are available under the message Use of encryption (TLS/SSL) through an imported trusted certificate. Let’s review each checkbox, as follows:

*   `Encrypt SAP Control connection`

    This option forces the SAP HANA cockpit to communicate with the SAP control subsystem over SSL. Selecting this checkbox is good practice because credentials communicated over this channel are that of a user on the operating system.

*   `Encrypt the database connection`

    This option forces the SAP HANA cockpit to communicate with the database over SSL. Again, database level credentials are communicated over this channel and encrypting that communication helps avoid man-in-the-middle attacks.

*   `Validate the certificate`

    Deselect this checkbox if you’re using the default installation certificate or a self-signed SSL certificate. Only select this option if the installed certificate is from a trusted certificate authority that the SAP HANA extended application services, advanced model engine (XSA engine), has been configured to trust. Otherwise, the connection will fail.

*   `Override hostname in certificate`

    Select this checkbox when using a trusted certificate and the certificate common name is different from the fully qualified SAP HANA server host name used in the definition of the connection. This mismatch sometimes occurs when using DNS aliases to support SAP HANA database connections. Place the certificate’s common name in the text box because the SAP HANA cockpit will assume that host name has been defined in the connection.

SAP HANA offers several options for managing certificates and encrypting communications between clients and the SAP HANA server. In the next section, we’ll review how to use encryption to secure SAP HANA persistent storage layers.

## 13.3 Encrypting Data

Encrypting communications with SAP HANA is crucial. However, encryption can also be used to secure the data stored on the SAP HANA server’s persistent layers. Although SAP HANA is an in-memory database, its data is not exclusively stored in-memory. SAP HANA will periodically create savepoints to mirror the in-memory data to disk. The savepoint process saves the data to the `/hana/data/<SID>` volume hosted on each SAP HANA server node.

In addition to these data savepoints, each committed transaction is simultaneously written to the `/hana/log/<SID>` volumes and memory on each SAP HANA server node. In the event of a power failure, the SAP HANA system will recreate the in-memory data using a combination of the persistent data snapshots stored in the `/data` volume and the transaction redo logs stored in the `/log` volume of each SAP HANA server node. Because these storage areas contain binary versions of the data hosted in SAP HANA, you should encrypt this data.

The same is true if you back up the database to a disk of an NFS location. In addition to data and log encryption, SAP HANA also support backup media encryption. Once enabled, the backup file will be encrypted with the same root keys used to encrypt the data and log partitions. Once enabled, the encrypted backup files cannot be restored or accessed with an SAP HANA database unless that database has the exact same root keys.
