
6. What is the CDDL specification identifier for the required signers of a transaction?

# Key Terms

*   **Auxiliary Data:** Metadata about the transaction where only the metadata hash is stored on-chain.
*   **Blake2b:** A hash algorithm that generates a hash based on an input of bytes.
*   **Blueprint:** An Aiken-generated file that contains Plutus script metadata and type definitions.
*   `Blockfrost`: An API Provider for blockchain data.
*   `ByteArray`: An array of bytes encoded using a hexadecimal format.
*   **Contract Parameter:** A variable on-chain that can be updated during compilation or at run-time.
*   `Enum`: A data type that can be enumerated and used in a switch/case statement.
*   `ScriptContext`: Contains all information about the current transaction being evaluated except for Auxiliary Data.
*   `Spending` **script:** Type of validator for spending UTXO locked at a script address.
*   `Switch` **Statement:** Used to evaluate different Enum combinations.
*   `VerificationKey`: The public key of the corresponding private key.

---

[¹](#c06.xhtml#ftn1a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_06/helios/vesting/contracts/vesting.hl](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_06/helios/vesting/contracts/vesting.hl)

[²](#c06.xhtml#ftn2a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_06/helios/vesting/contracts/vesting.hl](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_06/helios/vesting/contracts/vesting.hl)

[³](#c06.xhtml#ftn3a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_06/helios/vesting/components/Unlock.tsx](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_06/helios/vesting/components/Unlock.tsx)

[⁴](#c06.xhtml#ftn4a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_06/helios/vesting/pages/index.tsx](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_06/helios/vesting/pages/index.tsx)

[⁵](#c06.xhtml#ftn5a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_06/helios/vesting/pages/index.tsx](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_06/helios/vesting/pages/index.tsx)

[⁶](#c06.xhtml#ftn6a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_06/helios/vesting/pages/api/vestingUtxo.ts](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_06/helios/vesting/pages/api/vestingUtxo.ts)

[⁷](#c06.xhtml#ftn7a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_06/helios/vesting/pages/index.tsx](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_06/helios/vesting/pages/index.tsx)

[⁸](#c06.xhtml#ftn8a) [https://preprod.cexplorer.io/address/addr_test1wp4gwgtnyp8grwhzjj47qy7k60hxfv9p2wymjcwkzgw6r9cp0ctvs/tx#data](https://preprod.cexplorer.io/address/addr_test1wp4gwgtnyp8grwhzjj47qy7k60hxfv9p2wymjcwkzgw6r9cp0ctvs/tx#data)

[⁹](#c06.xhtml#ftn9a) [https://aiken-lang.org/installation-instructions](https://aiken-lang.org/installation-instructions)

[^(10)](#c06.xhtml#ftn10a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_06/aiken/vesting/contracts/validators/vesting.ak](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_06/aiken/vesting/contracts/validators/vesting.ak)

[^(11)](#c06.xhtml#ftn11a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_06/aiken/vesting/contracts/validators/vesting.ak](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_06/aiken/vesting/contracts/validators/vesting.ak)

[^(12)](#c06.xhtml#ftn12a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_06/aiken/vesting/pages/index.tsx](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_06/aiken/vesting/pages/index.tsx)

[^(13)](#c06.xhtml#ftn13a) [https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_06/aiken/vesting/pages/index.tsx](https://github.com/ava-orange-education/Mastering-Cardano-Smart-Contracts/blob/main/chapter_06/aiken/vesting/pages/index.tsx)

# CHAPTER 7

# Minting

# Introduction

In this chapter, we will examine Cardano native assets and how they are different from tokens on Ethereum created using the ERC-20 and ERC-721 standards. We will discuss the concept of token bundles and how to optimize coin selection. Next, we will deep dive into how Cardano native tokens are minted and the differences between Non-Fungible Tokens (NFTs) and Fungible Tokens (FTs). We will also review the NFT and FT metadata standards CIP-25 and CIP-68 and how to implement them when minting. Finally, we will introduce the Cardano Token Registry and explore its benefits for the end-user wallet experience. We will put this all together with a working minting policy use case and demo.

# Structure

In this chapter, we will discuss the following topics:

*   Tokens
    *   Native Assets
    *   Token Bundles
*   Minting Policy
    *   Fungible Tokens
    *   Non-Fungible Tokens
    *   Token Registry
    *   NFT Metadata Standards
        *   CIP-25
        *   CIP-68
*   Coin Selection
    *   Minting Policy Use Case

# Tokens

On March 1st, 2021, as part of the Mary hard fork, Cardano was upgraded to a multi-asset ledger. This was a significant event because custom native tokens can now leverage the secure, peer-reviewed, ledger rules used for Ada, Cardano’s native currency. This is much different than in Ethereum, which requires a custom ledger code for each token following either the ERC-20 or ERC-721 standards. Additionally, there are no requirements for special fees or additional event-handling logic to track transactions associated with a Cardano native asset.[¹](#c07.xhtml#ftn1)

# Native Assets

A Native asset is a custom token on Cardano that operates in the same manner as the base layer currency, Ada. The only requirement is that a native asset must always have a minimum amount of Ada included. CIP-55[²](#c07.xhtml#ftn2) simplified the minimum Ada calculation and used the number of CBOR bytes of a UTXO, which includes all of the native assets locked in a particular UTXO.

Assets represent value such as 1 Ada (1,000,000 lovelace) or 100 gold coins. Each asset token is always made of three components^(\*):

*   **Policy Identifier (ID):** A unique identifier that is the hash of the Minting Policy Plutus script.
*   **Asset Name:** An immutable token name on-chain for a specific minting policy.
*   **Quantity**: The accounting unit.

^(\*) Ada is the only asset token where the Policy ID is an empty string.

# Token Bundles

A token bundle is a collection of tokens that may be the same or different from each other. Token bundles organize tokens into a particular structure that properly defines the Minting Policy ID, Token Name, and quantity of each of the tokens in a **collection**. Let’s look at the following example:

```
{
  "lovelace": "1646420",
  "assets": {
    "Game Monetary Policy ID": {
      "Gold": "100",
      "Silver": "1,000",
      "Bronze": "10,000"
    },
    "Game Character Policy ID": {
      "Dracula": "1"
    }
  }
}
```
