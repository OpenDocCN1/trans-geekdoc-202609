problem of immutability is solved. In the next section, a statistical analysis is performed to understand if this approach is feasible or not.

# Evaluation

As previously discussed, the GDPR poses a significant challenge toward assuring DApps are compliant with it, mainly due to the right to be forgotten. In this section, a statistical analysis is performed to understand whether encrypting personal data (or files) is feasible or not before sending them to the IPFS node. This way, encrypted files persist for as long as the node serves them, but their content is still inaccessible to third parties, on par with file deletion.

In Ethereum, there is the concept of “gas”:

> the execution fee that senders of transactions need to pay for every operation made on an Ethereum blockchain. The name gas is inspired by the view that this fee acts as cryptofuel, driving the motion of smart contracts. Gas is purchased for ether from the miners that execute the code. (Ethereum Foundation, 2016)

There are four important aspects related to gas:

+   - **Gas limit**: the maximum amount of gas to be paid in a transaction;
+   - **Gas used by transaction**: total gas that is consumed by the transaction;
+   - **Gas price**: price (in Ether) of one unit of gas specified in the transaction; and
+   - **Total transaction cost**: gas used * gas price.

Two versions of the DFiles DApp were developed: one without user authentication and file encryption, and another with both user authentication and file encryption/decryption. All upcoming statistical data is available at Bitbucket.⁸ First and foremost, 100 random files were selected with various extensions: .pdf, .docx, .xlsx and .pptx, although it was not possible to use them all due to hardware limitations. They were then divided into four different groups: small (1 KB–1 MB), medium (1 MB–20 MB), large (20 MB–200 MB) and extra large (200 MB–2 GB). In addition to this, for the same files and both versions of DFiles, the elapsed time from when the user clicks the “upload file” button, the file gets sent to the local IPFS node (encrypted or unencrypted) and the user clicks the button to accept the transaction is measured in addition to the total transaction cost in Ether (provided by MetaMask; it varies depending on the gas limit and gas price). Appendix A shows some of this collected data.

However, due to hardware limitations with file encryption, only files up to 14.2 MB were considered for the following statistical analysis. The total transaction cost and upload elapsed times were still recorded for comparison in the overall conclusion between files with and without encryption.