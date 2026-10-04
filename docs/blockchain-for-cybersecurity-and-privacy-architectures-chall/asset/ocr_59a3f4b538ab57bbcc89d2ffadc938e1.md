# Secure Anti-Counterfeiting Pharmaceuticals Supply Chain System

enable multiple actors to have access to the tokens and perform the certain supply chain processes assigned. Listing 11.1 shows the details of the ownership functions and how they are implemented.

# LISTING 11.1 NFT TOKEN OWNERSHIP FUNCTIONS

```
mapping(uint256 => address) private tokenOwners;
mapping(uint256 => bool) private tokenExists;
// Query Token Ownership
function ownerOf(uint256 _tokenId)
    constant returns (address owner) {
    require(tokenExists[_tokenId]);
    return tokenOwners[_tokenId];
}
// Transfer of token ownership
function transfer(address _to, uint256 _tokenId) {
    address currentOwner = msg.sender;
    address newOwner = _to;
    // Perform assertion before transfer
    require(tokenExists[_tokenId]);
    require(currentOwner == ownerOf(_tokenId));
    require(currentOwner != newOwner);
    require(newOwner != address(0));
    // Perform actions
    removeFromList(_tokenId);
    balances[oldOwner] -= 1;
    tokenOwners[_tokenId] = newOwner;
    balances[newOwner] += 1;
    // Record transfer event in Blockchain for auditing
    Transfer(_oldOwner, newOwner, _tokenId);
}
```

```
// Delegate authority of invoking transfer actions
function approve(address _to, uint256 _tokenId) {
    // Perform assertion before delegating
    require(msg.sender == ownerOf(_tokenId));
    require(msg.sender != _to);
    // Add delegation
    allowed[msg.sender][_to] = _tokenId;
    // Record approve event for auditing and tracing
    Approval(msg.sender, _to, _tokenId);
}
```

# 11.4.1.2 Operations of Composable NFTs

Composable NFTs provide a simple way to form composite assets on the Ethereum blockchain; those assets are still utilizing the same concept of ERC-721 but with the capability to link between parent and child tokens. The targeted use case in