# CHAPTER 21 GETTING FROM THE OFFICE TO THE ROAD: VPNS

+   e. Enter a password in the Password and Confirm Password text boxes on the Password page, and click Next.

+   f. Click Browse, and browse to the C:\C folder (create it if needed).

+   g. Name the file VPNIPsec, and click Save.

+   h. Click Next, click Finish, and click OK.

+   8. Back in the MMC, import the certificate using these steps:

+   a. Browse to the Certificates (Local Computer)\Personal\Certificates container.

+   b. Right-click Certificates, and select All Tasks > Import.

+   c. Click Next on the Welcome page.

+   d. Click Browse, and browse to C:\Certs.

+   e. Change the extension to All Files (**) so that the file you exported appears.

+   f. Select your certificate, and click Open.

+   g. Click Next on the Import page.

+   h. Enter the password you used to protect the certificate, and click Next.

+   i. Click Next to accept the default location of the certificate store, and click Next.

+   9. Using the following steps to generate a root certificate on the VPN server:

+   a. Launch Internet Explorer using Run As Administrator.

+   b. Enter http://localhost/certsrv

+   c. Click "Download a CA certificate, certificate chain, or CRL."

+   d. When the ActiveX warning appears, click Yes.

+   e. Click Yes on the confirmation dialog pop-up.

+   f. Select "Download CA certificate," and click Save. Notice that the name is certnew.

+   g. Browse to the C:\Certs folder, click Save, and then click Close.

You will install this root certificate on the client.

# Step 6: Install the CA Certificate on the Client

When the client connects to the VPN server, the VPN server will pass the certificate to use to establish the session. However, the client won't trust this certificate as valid by default. Instead, the root CA certificate needs to be installed on the client so that the server's certificate is trusted. The following steps will install the root certificate on the client:

+   1. Copy the new certificate created in the previous steps from the server to the client in a folder named C:\Certs.

+   2. On the Windows 8 client, at the Start screen, type MMC, click the MMC.exe icon, and then press Enter.

+   3. If a User Account Control dialog box appears, click Yes to allow the action.