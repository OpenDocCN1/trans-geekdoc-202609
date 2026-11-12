

standard JSON object was used. On top of this, IPFS clearly has a long way to go for DApps to become mainstream. For starters, it has a growing problem of storing very large files, as demonstrated by DFiles. If encryption is required, then the maximum file size possible is much lower. It was proved that, due to hardware limitations and the current state of both Ethereum and IPFS, encryption was only possible for small to medium files. Ethereum, IPFS and data protection techniques will evolve significantly in the future, which will theoretically allow for either better encryption techniques or other privacy ones, thus shining a bright light for future DApps that require data privacy and protection.

As previously discussed, DFiles aims to demonstrate whether by encrypting personal data, GDPR compliance can be achieved. However, there are other problems associated with this approach, such as weak encryption algorithms that previously have proved to be highly secure. Examples of these include the MD5 and SHA1 ones (The Open Web Application Security Project (OWASP), 2018). For this reason, there is a slight possibility that the algorithms used in the most popular blockchains become obsolete for short periods of time – where data can be easily decrypted – before being replaced by another, more secure one.

In addition to this, quantum computing could very soon become a reality, and for a substantial period of time, all data encrypted in most blockchains such as Ethereum as well as all the encrypted files stored in the IPFS via the DFiles DApp could be easily decrypted. This is, in the authors’ opinion, the biggest threat to blockchain technology in the not-so-distant future.

As for future work in DFiles, instead of using a local IPFS node, the Infura node could be used. This brings several advantages, as hardware limitations are minimized, but it brings a new set of problems, such as that files stored in the Infura IPFS node have no incentive to be kept for long.

Another aspect to improve is to deploy the DFiles smart contract to a test network such as Rinkeby and update the DFiles DApp to use this deployed smart contract instead of the local Ganache private Ethereum Blockchain. An early deployment has been done, but further testing is required. The smart contract is available in the Rinkeby test network.

In short, in this section, the limitations of both IPFS and Ethereum were discussed, including DFiles’ future work. However, there are some general conclusions that can be taken:

- IPFS file encryption is in its infancy; therefore, there are significant hardware and technology limitations preventing its mass adoption.
- Ethereum is a public ledger, and therefore it provides little to no privacy. The only possible approach is to encrypt data using other decentralized technologies such as the IPFS. Ethereum also has a substantial level of limitations – such as no JSON support and the discouragement of some computing loop instructions (for, while, for instance) due to high total transaction costs – that impact its worldwide adoption.
- Encrypting personal data for GDPR compliance purposes is severely limited and possibly discouraged. Both the IPFS and Ethereum should be considered special cases of the GDPR to avoid issues with data encryption.

## Conclusion

In this chapter, first the most important GDPR concepts, in addition to the several lawful bases for processing personal data and the several individual rights, were presented. Its right to erasure interferes with blockchain immutability. On top of this, three scenarios were discussed concerning whether this right can or cannot be complied with, followed by a GDPR compliance guideline for Ethereum DApps.

To test this guideline, a case study was developed: DFiles. It is an Ethereum DApp built with a mixture of centralized and decentralized technologies such as Ethereum and IPFS. Its main objectives are to understand whether Ethereum (Homestead) DApps can comply with this regulation and if protecting personal data by encrypting it is feasible or not.

DFiles also adheres to the principles of blockchain software engineering by following the software development life cycle, albeit adapted for DApps. Its core smart contract is also explained, from the design patterns implemented to the main data structures and functions, in addition to a short presentation of its core features. In short, DFiles allows a user to upload and view his submitted files.

A statistical analysis to assert the feasibility of encryption in compliance with the right to erasure was then performed, albeit only for some files because of hardware limitations. Two variants of the DApp were created: one with file encryption and one without. Uploaded files were divided into four categories: small (1 KB–1 MB), medium (1 MB–20 MB), large (20 MB–200 MB) and extra large (200 MB–2 GB).

The total transaction cost in Ether plus the total elapsed time between the user clicking the upload button and it being uploaded were then measured in both versions. Its conclusions are then presented. In short, complying with the GDPR and its right to erasure is only feasible for encrypted files up to 14.2 MB.

Finally, the limitations of the case study and its future work were explained.

## Notes

- 1 Accessed from https://bitbucket.org/duarte_1110199/dfiles-ethereum-dapp/src/master/.
- 2 Accessed from https://trufflesframework.com/.
- 3 Accessed from https://github.com/ethereum/wiki/wiki/JavaScript-API.
- 4 Accessed from https://github.com/OpenZeppelin/openzeppelin-solidity
- 5 https://bitbucket.org/duarte_1110199/dfiles-ethereum-dapp/src/master/contracts/Files.sol.
- 6 Accessed from https://trufflesframework.com/docs/truffle/testing/writing-tests-in-javascript.
- 7. Accessed from https://github.com/brix/crypto-js.
- 8. Accessed from https://bitbucket.org/duarte_1110199/dfiles-r-statistical-data/src/master/.
- 9. Accessed from https://infura.io/.
- 10. Accessed from https://rinkeby.etherscan.io/address/0x09C5b627354eF29c3B6507aABa7386Ce240fFf9C.

## References

- Bitcoin Project. (2018). Bitcoin – Open source p2p money. Retrieved from https://bitcoin.org/en/
- Consensys. (2018a). Ganache. Retrieved from https://truffleframework.com/docs/ganache/overview
- Consensys. (2018b). Metamask. Retrieved from http://metamask.io/
- Destefanis, G., Marchesi, M., Ortu, M., Tonelli, R., Bracciali, A., and Hierons, R. 2018. Smart contracts vulnerabilities: A call for blockchain software engineering? Blockchain oriented software engineering (IWBOSE), International Workshop. Campobasso: IEEE.
- Ethereum Foundation. (2014). Solidity, the contract-oriented programming language. Retrieved from https://github.com/ethereum/solidity
- Ethereum Foundation. (2016). Account types, gas, and transactions. Retrieved from www.ethdocs.org/en/latest/contracts-and-transactions/account-types-gas-and-transactions.html
- Ethereum Foundation. (2018). Ethereum blockchain app platform. Retrieved from www.ethereum.org/
- EU GDPR Compliant. (2018). What is a data subject? Retrieved from https://eugdprcompliant.com/what-is-data-subject/
- European Data Protection Supervisor. (2018). The history of the general data protection regulation. Retrieved from https://edps.europa.eu/data-protection/data-protection/legislation/history-general-data-protection-regulation_en
- European Union. (2016). Regulation (EU) 2016/679 of the European Parliament and of the council of 27 April 2016 on the protection of natural persons with regard to the processing of personal data and on the free movement of such data. Official Journal of the European Union, 1–88.
- Falkon, S. (2017, December 24). The story of the DAO – Its history and consequences. Retrieved from https://medium.com/swlh/the-story-of-the-dao-its-history-and-consequences-71e6a84a551ee
- ICO. (2018, August 2). Guide to the general data protection regulation (GDPR). Retrieved from https://ico.org.uk/media/for-organisations/guide-to-the-general-data-protection-regulation-gdpr-1-0.pdf
- Parity Technologies. (2017, July 20). The multi-sig hack: A postmortem. Retrieved from https://paritytech.io/the-multi-sig-hack-a-postmortem/
- Petrov, S. (2017, November 7). Another parity wallet hack explained. Retrieved from https://medium.com/@Pr0Ger/another-parity-wallet-hack-explained-847ca46a2e1c
- Protocol Labs. (2018). IPFS is the distributed web. Retrieved from https://ipfs.io/
- Szabo, N. (1996). Smart contracts: Building blocks for digital markets. Retrieved from www.fon.hum.uva.nl/rob/Courses/InformationInSpeech/CDROM/Literature/LOTwinterschool2006/szabo.best.vwh.net/smart_contracts_2.html

