# Blockchain for Cybersecurity and Privacy

The composable tokens’ CNFT smart contract is created by each manufacturer. The CNFT smart contract is an extended version of the ERC-721, with two main functions added, which perform the functions of (de)composition of composite asset. Algorithm 2 show the NFT batch transfer function. The CNFT smart contract adds many variables such as rootOwner and childTokens to allow traversing the ownership of composable tokens in top-down and bottom-up directions. Listings 11.3 and 11.4 show the details of the create token function and batch transfer function.

# Algorithm 2: NFT Batch Transfer Function

```
**Input:** [tokenIds..], fromAddr, toAddr
**Result:** Updated list of childTokens in original and destination CNFTs
if fromAddr isAllowed(requestSender) **then**
 for i ← 0 to tokenIds.length
tokens[fromAddr] ← [tokens[fromAddr], pop(tokenId)];
tokens[toAddr] ← [tokens[toAddr], tokenId];
tokens[tokenId][addr].rootOwner = fromAddr;
end
else
Ignore;
```

# LISTING 11.3 CREATE TOKEN FUNCTION

```
function createToken(bytes32 cdn, bytes16 lotNumber,
uint32 expiryDate) public returns
(uint256) {
 require(msg.sender == adminAddress);
tokenCount++;ntokenId = keccak256(cdn, lotNumber, expiryDate,
block.timestamp);
tokenIdToTokenOwner[tokenCount] = msg.sender;
tokenOwnerToTokenCount[msg.sender]++;
emit (tokenId, cdn, lotNumber, msg.sender);
 return tokenId;
}
```