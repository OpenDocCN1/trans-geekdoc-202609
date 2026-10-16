```
class Block:

    def __init__(self,ts, record,prevHash):
        self.pHash = prevHash
        self.record = record
        self.ts = ts
        self.hash = self.compute_Hash()

        self.nonce = 0;
```

Step 2: Create a proof_of_work() method that receives block as a parameter and the required difficulty is set as a value and iteratively generates the hash value until the hash value prefixes with enough number of zeros.

```
diff = 3

def proof_of_work(self, block):
    block.nonce =
    calculated_Hash = block.compute_Hash()
    while not calculated_Hash.startswith('0' * Blockchain.diff):
        block.nonce += 1
        calculated_Hash = block.compute_Hash()
    return calculated_Hash
```

Step 3: Incorporate nonce into the calculate hash function.

```
def calculateHash:
    newhash = self.index+ self.previousHash+ self.tmstamp+ str(data)+ self.nonce
    return hashlib.sha256(new_hash).hexdigest()
```