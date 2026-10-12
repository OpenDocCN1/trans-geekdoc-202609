
# Format-Preserving Encryption (FPE)

**Format-Preserving Encryption**, or **FPE**, is an encryption algorithm that preserves the format of information while it is being encrypted. It is the process of encrypting data in such a way that the output (ciphertext) remains in the same format as the input (plain text). See `https://en.wikipedia.org/wiki/Format-preserving_encryption` for more information.

Two use cases for this are as follows:

*   **Payment Card Verification:** In the retail and e-commerce sector, payment card data must be collected and stored to make payments. Additionally, employees may need to see and verify the last four digits of a customer's payment card information. FPE makes it easier to expose only the required information to employees while leaving the other 12 digits protected.
*   **Legacy Databases:** A telecommunications system may have a multitude of legacy systems that require the use of encrypted data for security. However, it might not be an option for the organization to restructure its databases to store encrypted data. With FPE, the structure of the databases can remain unchanged. (For more information, see `www.ubiqsecurity.com/what-is-format-preserving-encryption-fpe-and-its-benefits`.)

## Tokenization

**Tokenization** refers to a process by which a piece of sensitive data, such as a credit card number, is replaced by a surrogate value known as a token. The sensitive data still generally needs to be stored securely at one centralized location for subsequent reference and requires strong protections around it. The security of a tokenization approach depends on the security of the sensitive values and the algorithm and process used to create the surrogate value and map it back to the original value.

FPE obfuscates sensitive information, while tokenization removes it entirely (to another location).

# Privacy Implications of Data Usage and Collection

In the following sections, we will cover **personally identifiable information (PII)** and **protected health information (PHI)** in the data and how Google Cloud recommends strategies to deal with sensitive data.

PII is a type of data that allows for an individual to be identified. It includes any information relating to a specific individual, such as name, address, Social Security number (SSN), date of birth, financial information, passport number, telephone numbers, and email addresses.

The Health Insurance Portability and Accountability Act (HIPAA) Privacy Rule provides federal protections for PHI held by covered entities and gives patients an array of rights with respect to that information. At the same time, the Privacy Rule is balanced so that it permits the disclosure of personal health information needed for patient care and other important purposes.

## Google Cloud Data Loss Prevention

The **Google Cloud Data Loss Prevention (DLP) API** can de-identify sensitive data in text content, including text stored in container structures such as tables. **De-identification** is the process of removing identifying information from data. The API detects sensitive data such as PII and then uses a de-identification transformation to mask, delete, or otherwise obscure the data.

The de-identification techniques used are as follows:

*   Masking sensitive data by partially or fully replacing characters with a symbol, such as an asterisk (`*`) or hash (`#`)
*   Replacing each instance of sensitive data with a token using a technique such as cryptographic hashing
*   Encrypting and replacing sensitive data using a randomly generated or predetermined key
*   Using bucketing, which replaces a more identifiable value with a less distinguishing value

The following are some of the key concepts associated with DLP:

*   **Data profiles:** The data profiler lets you protect data across your organization by identifying where sensitive and high-risk data reside. When you turn on data profiling, Cloud DLP automatically scans all BigQuery tables and columns across the entire organization, individual folders, and projects. It then creates data profiles at the table, column, and project levels.
*   **Risk analysis:** You can use risk analysis methods before de-identification to help determine an effective de-identification strategy or after de-identification to monitor for any changes or outliers. Cloud DLP can compute four re-identification risk metrics: `k`-anonymity, `l`-diversity, `k`-map, and `δ`-presence. (For more information, see `https://cloud.google.com/dlp/docs/concepts-risk-analysis`.)
*   **Inspection (jobs and triggers):** A **job** is an action that Cloud Data Loss Prevention runs to either scan content for sensitive data or calculate the risk of re-identification. Cloud DLP creates and runs a job resource whenever you tell it to inspect your data. You can schedule when Cloud DLP runs jobs by creating job triggers. A **job trigger** is an event that automates the creation of DLP jobs to scan Google Cloud Storage repositories, including Cloud Storage buckets, BigQuery tables, and Datastore. You can also trigger a DLP scan job by using Cloud Functions every time a file is uploaded to Cloud Storage.

DLP provides templates that are configurations to help you set up DLP jobs; see [Figure 6.5](#c06.xhtml#c06-fig-0004).

![FIGURE 6.5 Architecture for de-identification of PII on large datasets using DLP](images/c06f005.png)

**[FIGURE 6.5](#c06.xhtml#R_c06-fig-0004)** Architecture for de-identification of PII on large datasets using DLP

The architecture consists of the following:

*   **Data de-identification streaming pipeline:** De-identifies sensitive data in text using Dataflow. If you have streaming data coming, you can use Dataflow to trigger a DLP job to de-identify data and store it in Google Cloud Storage or populate the de-identified data in a BigQuery table. You can also run a DLP job on batch data stored in Cloud Storage.
*   **Configuration (DLP template and key) management:** You can manage the templates and configuration for your DLP jobs with a small group of people as security admins and use Cloud KMS (key management service) to avoid exposing de-identification methods and encryption keys.
*   **Data validation and re-identification pipeline:** You can have batch and streaming data de-identified and stored in BigQuery as a DLP job output. You can also choose to store this in other types of storage. You can validate copies of the de-identified data and use a Dataflow pipeline to re-identify data at a large scale.

## Google Cloud Healthcare API for PHI Identification

Under the U.S. Health Insurance Portability and Accountability Act (HIPAA), PHI that is linked based on the list of 18 identifiers such as name, medical record number, Social Security number, IP address, and so on must be treated with special care. For the complete list of identifiers, refer to this Wikipedia page: `https://en.wikipedia.org/wiki/Protected_health_information`.

The **Google Cloud Healthcare API** has the de-identify operation, which removes PHI or otherwise sensitive information from healthcare data. The healthcare API's de-identification is highly configurable and redacts PHI from text, images, Fast Healthcare Interoperability Resources (FHIR), and Digital Imaging and Communications in Medicine (DICOM) data. Source `https://cloud.google.com/healthcare-api/docs/concepts/de-identification` The Cloud Healthcare API also detects sensitive data in DICOM instances and FHIR data, such as protected PHI, and then uses a de-identification transformation to mask, delete, or otherwise obscure the data.

The PHI targeted by the de-identify command includes the 18 identifiers described in the HIPAA Privacy Rule de-identification standard. The HIPAA Privacy Rule does not restrict the use or disclosure of de-identified health information, as it is no longer considered protected health information.
