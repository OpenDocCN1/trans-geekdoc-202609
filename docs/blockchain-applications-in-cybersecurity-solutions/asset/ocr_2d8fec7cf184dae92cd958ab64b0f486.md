# # PERFORMANCE AND SECURITY ANALYSIS

# ## Security Analysis

With the encryption mechanism, we are able to get rid of the privacy risks caused by the traditional IPFS implementation. By querying the blacklist, only the data that is protected from the users we blacklisted is able to be downloaded from IPFS. This IPFS implementation will be able to serve as the backbone for the new DDoS mitigation solution.

In the second experiment, we used smart contract-based access control to verify the user’s identity before giving them permission to download a file on IPFS. When we downloaded a file from IPFS, we were required to enter an email address for the smart contract to validate. For experimental purposes, we created a blacklist of email addresses, which should be blocked from accessing our data on IPFS. When the entered email address passed the verification, we showed a success message to the user and started downloading the file from IPFS. When we deliberately put an email address, which is in the email blacklist, it would fail the verification by the smart contract. We showed a failure message to the user and did not allow them to download the file.

We have migrated the web application from the local host to a remote IPFS network, so the web application can be accessed even though the local server is not running. We also set up an SSL connection and a custom URL https://sjsu-cs298.on.fleek.co for secure and easy access to the application.

# ## Performance Analysis

Our tests included uploading and downloading files of various sizes, to see how long it takes to get data from IPFS without the cache and with it. Every file was run ten times, and the average latency was calculated. The results are shown in Fig. (6).

We can see that without the cache, the average latency fluctuates from 300 ms to 400 ms. In our experiment, sometimes it can take up to a few seconds to get the root file node because it depends on when the lookup algorithm finds the node.

We also measure the download latency for different file sizes, shown in Fig. (7). With the cache, it only takes about 10 ms to get the root file node, and the latency is pretty consistent. The latency the user observes when downloading a file from the application will be higher due to the Internet latency to transfer the data. With the Internet download speed of about 90 Mbps in our experiments, the Internet