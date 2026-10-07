# CCSP Certified Cloud Security Professional All-in-one Exam Guide
388

B. Injection involves sending invalid commands through input fields in an application with the intent of getting the application to execute the code and bypass many security controls that are in place. If an application does not properly validate input fields to ensure they are in the correct format and do not contain extraneous code or commands, the application may expose data or configuration information to a malicious actor.

A is incorrect because cross-site scripting involves attempts to have the user's client or browser execute commands against a site. Because it is executed against the client side or browser, it is not a direct attempt to inject commands into the application. It is intended to have the user's browser access the application with their own credentials and bypass common security tactics as same-origin policies.

C is incorrect because insecure direct object references involve the exposure of internal information or configurations that affect the code and are view on the client side. This can include directory structures, filenames, configuration items, information about service accounts or credentials, or any other type of information that should not be exposed outside of the actual system hosting the application or services.

D is incorrect because cross-site forgery requests involve having a trusted client of an application or trusted user send unauthorized commands over their own credentials. They essentially involve leveraging a valid, trusted user's session and credentials to attack a site or application.

+   93. Which of the key aspects of security is concerned with ensuring information and data is in its intended format and has not been altered?

+   A. Integrity

+   B. Confidentiality

+   C. Availability

+   D. Privacy

A. Integrity is the main security principle concerned with data being in its intended form and accurate. This allows the data to be considered trustworthy throughout its entire lifecycle, ensuring that it has not been altered in an unauthorized manner or by an unauthorized party.

B is incorrect because confidentiality is concerned with ensuring that no one authorized users are able to access or read data. It is not concerned with the content of the data in regards to the editing or manipulation of it.

C is incorrect because availability is the main security principle concerned with data being available to authorized parties as needed and in the form needed. It is not focused on the content of the data or the protection of it from unauthorized altering.