
## Next Steps

1.  Go to the program and select `Send Using Certificate Pinning` under `Network Layer Security`.

2.  Note that data can be intercepted by avoiding SSL Pinning. Refer to *[Figure 11.20](#c11.xhtml#fig11_20)*:

    ![](images/Figure-11.20.jpg)

    **Figure 11.20:** Proxy settings

The following list includes a variety of tools that can be used to avoid jailbreak detection:

*   **Frida**: <https://codeshare.frida.re/>
*   **SSLKillSwitch2**: <https://github.com/nabla-c0d3/ssl-kill-switch2>

# Bypassing Biometric (Local) Authentication

Let us now see how we can bypass biometric (local) authentication using various methods.

## Using Objection

1.  Run the following commands on your system, as shown in *[Figure 11.21](#c11.xhtml#fig11_21)*:

    ```
    objection -g DVIA-v2 explore
    ios ui biometrics_bypass exit
    ```

    ![](images/Figure-11.21.jpg)

    **Figure 11.21:** Bypassing biometric using objection

2.  Next, open the app and select `Touch/Face ID Bypass` | `Start Challenge` | `Swift Implementation`, as shown in *[Figure 11.22](#c11.xhtml#fig11_22)*:

    ![](images/Figure-11.22.jpg)

    **Figure 11.22:** Face not recognized

3.  When the application prompts you with `Face Not Recognized`, select `Cancel` to avoid authentication, as shown in *[Figure 11.23](#c11.xhtml#fig11_23)*:

    ![](images/Figure-11.23.jpg)

    **Figure 11.23:** Authentication successful

# Checking for Sensitive Data Exposure in Local Storage

The sensitive data is kept in local storage in a number of different locations. The different locations where you can locate sensitive data and how to launch an attack are listed as follows.

Open the DVIA-v2 application, then select `Local Data Storage`. Save some data using each of the available choices.

## Sensitive Data in Plist

**Case 1: Store sensitive data in Plist.**

Follow the given steps:

1.  Run the following commands:

    ```
    objection -g DVIA-v2 explore
    env
    cd /var/mobile/Containers/Data/Application/<app-id>/Documents
    ios plist cat userInfo.plist
    ```

2.  Keep in mind that the sensitive data is kept as plain text, as shown in *[Figure 11.24](#c11.xhtml#fig11_24)*:

    ![](images/Figure-11.24.jpg)

    **Figure 11.24:** iOS plist cat userInfo.plist command

## Sensitive Data in UserDefaults

**Case 2: Store Sensitive Data in UserDefaults**

Follow the given steps:

1.  Run the following commands:

    ```
    objection -g DVIA-v2 explore
    ios nsuserdefaults get
    ```

2.  You can see that the sensitive data is contained in the `DemoValue` parameter as plain text, as shown in *[Figure 11.25](#c11.xhtml#fig11_25)*:

    ![](images/Figure-11.25.jpg)

    **Figure 11.25:** iOS “nsuserdefaults get” command

## Sensitive Data in Keychain

**Case 3: Store sensitive data in keychain**

Follow the given steps:

1.  Run the following commands:

    ```
    objection -g DVIA-v2 explore
    ios keychain dump
    ```

2.  Take note that the password is saved in plain text as sensitive data (Super Secure Password), as shown in *[Figure 11.26](#c11.xhtml#fig11_26)*:

    ![](images/Figure-11.26.jpg)

    **Figure 11.26:** iOS keychain dump command

For the remaining attacks, we will employ the Grapefruit tool (<https://github.com/ChiChou/grapefruit>). Installing, starting, and connecting your iPhone to the application.

## Sensitive Data in Core Data

**Case 4: Store sensitive data in core data**

Follow the given steps:

1.  Open Grapefruit and load the DVIA-v2 application. Go to the following: `Data` | `Library` | `Application Support`.

2.  Open `Model.sqlite`.

3.  Be aware that private data is reachable. Refer to *[Figure 11.27](#c11.xhtml#fig11_27)*:

    ![](images/Figure-11.27.jpg)

    **Figure 11.27:** Sensitive data in core data

## Sensitive Data in Couchbase Lite

**Case 5: Store sensitive data in couchbase lite**

Follow the given steps:

1.  Load the DVIA-v2 application with Grapefruit and navigate to the following: `Data` | `Library` | `Application Support` | `CouchbaseLite` | `dvcouchbasedb.cblite2`.

2.  Download `db.sqlite3`, open it, and you will be able to see the sensitive information.

## Sensitive Data in YapDatabase

**Case 6: Store sensitive data in YapDatabase**

Follow the given steps:

1.  Load the DVIA-v2 application with Grapefruit and navigate to the following: `Data` | `Library` | `Application Support`.

2.  Download `YapDatabase.sqlite` and open it with SQLite Viewer.

3.  You will be able to access sensitive data.

# OWASP Mobile Top 10

The OWASP mobile top 10 is a ranking of the security threats that mobile applications face, compiled from research and user feedback.

## M1: Improper Platform Usage

The first OWASP mobile top 10 category focuses on the areas where an attacker may abuse the security features offered by the iOS platform. Additionally, several security vulnerabilities may occasionally develop as a result of improper platform feature implementation.

Under this area, a number of components, including Biometric Authentication, Keychain, Platform Permission, and so on, must be examined.

## M2: Insecure Data Storage

Many times, iOS applications save certain data locally in various parts. If an attacker gains access to the user’s physical device, there is a potential that sensitive data will be saved locally and could be used against the user.

Here are a few examples of the general dangers that fall into this category:

*   Sensitive data stored in Plist
*   Sensitive data stored in UserDefaults
*   Sensitive data stored in Keychain
*   Sensitive data stored in Core Data
*   Sensitive data stored in Webkit Caching
*   Sensitive data stored in Realm
*   Sensitive data stored in Couchbase Lite
*   Sensitive data stored in YapDatabase
*   URL caching (both request and response)
*   Keyboard press caching
*   Copy/paste buffer caching
*   Insecure logging
*   Background screen caching
*   Analytics data sent to third parties

## M3: Insecure Communication

Client-server architecture is used for communication in the iOS application. An attacker can try to steal critical information over unencrypted checks, perform Man-in-the-Middle attacks, or try to study the request and answer by capturing them using proxy tools like Burp Suite due to faulty or inadequate implementation of communication standards like communication over HTTP.

Here are a few examples of the general dangers that fall into this category:

*   Lack/bypass-able SSL pinning
*   Communication over HTTP [unencrypted communication]
*   Plain-text submission of sensitive information
*   Logging sensitive information in the logs

## M4: Insecure Authentication

Applications are typically categorized as having insecure authentication when they either improperly handle authentication checks or permit attackers to modify login/authentication requests in order to access the target user’s account.

Here are a few examples of the general dangers that fall into this category:

*   Guessable/weak/default credentials
*   Authentication bypass using attacks such as injection attacks

## M5: Insufficient Cryptography

The user data is frequently stored by iOS applications or used in various client-server queries. An attacker may try to access data that is encrypted using a weak cryptographic approach due to a lack of strong cryptography and obtain sensitive data in this way.

Here are a few examples of the general dangers that fall into this category:

*   Stealing app and user data
*   Accessing encrypted files
*   Accessing encrypted client-server request endpoints

## M6: Insecure Authorization
