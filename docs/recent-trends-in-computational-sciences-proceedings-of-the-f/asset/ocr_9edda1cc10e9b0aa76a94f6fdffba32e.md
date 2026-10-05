methods are not user friendly as they are complex and difficult to be combined with a user interface which is easily understood by the general public without any technical knowledge of the working of the blockchain technology, as through these methods the users first have to create their crypto wallets which are used to hold the cryptrencies in the crypto marketplace. These wallets are linked with the blockchain (for example the ethereum blockchain) which they want their record After blocks are mined and NFTs are minted by cryptographically recording the digital assets on chain of blocks. However the proposed method is extremely user friendly in this the users are not required to have any prior knowledge of blockchain technology. The algorithm is implemented through the MOTOK language which is used to write smart programs on the ICP blockchain. Each NFT contains three fields including the name of the NFT (a specific text under), the unique token id is different for different NFTs and the Owner id which is basically principal id the main canister and the NFT data. The minting of NFTs is done through smart contracts of ICP blockchain. Each class serves as a separate canister which represents an individual NFT. All these canisters are managed through a single canister (or the main canister) which links all the NFTs for a single user and the functions for displaying the NFT. This main canister is different for different users.

# 4 ALGORTITHM

+   * Create the main actor class which contains the NFT classes.
* To mint the NFT create a class for storing the NFT information.
* Pass the values of the name entered by the user, the principal id for them canister (the actor class), the NFT data in the form of an array of natural numbers.
* Initialize the variables:
  a) itemName: Name of NFT
  b) nftOwner: principal id of main class
  c) tokenId: principal id of the nft class
* Each time a new NFT is created a separate NFT class is formed.Create a function to return the NFT name.
* Create a function to return the NFT data.

# 5 RESULT

The proposed algorithm is incorporated with a frontend (Figure 1) to provide a user active platform for minting the NFTs and can be given as form of web application or an ecommerce website. The MOTOK language is used to obtain the smart contracts on ICP block chain which are basically the computer programs that are tamperproof. The features of these smart contracts can be enumerated as:
* The smart contracts are general purpose i.e any possible computation can be performed through the blockchain.
* They are tamperproof as they run on blockchain thus the programs can not be tampered.
* They are autonomous as the network automatically executes the contracts and the user does not have to perform any action.
* They are decentralized that they are not controlled by a particular individual or an organisation.

The MOTOK program runs at the back and interacts with the frontend through IDL, which stands for Interface description language. The idl just acts as a translator