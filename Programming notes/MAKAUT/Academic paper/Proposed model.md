In a cloud computing environment, a significant volume of operations occurs every second, necessitating a robust system for maintaining a trustworthy record of these activities. To achieve this, we propose the implementation of a permissioned blockchain at the first layer. This blockchain will serve as a decentralized ledger to store all operation logs generated within the federated cloud environment.

The members of the cloud federation, (cloud service providers (CSPs)) will actively participate in the blockchain network. Each member actively engages as a node within the blockchain network, playing a crucial role in maintaining the decentralization and distribution of the blockchain's infrastructure. These nodes collectively collaborate to reach consensus, where they validate and record transactions, ensuring the integrity of the operations recorded in the permissioned blockchain. By involving all relevant entities as nodes, the framework fosters a collaborative and trust-based environment, enhancing the overall security and transparency of the cloud computing ecosystem.


Each operation performed within the Cloud Computing environment is recorded as a transaction by the cloud service provider. Each transaction is digitally signed by the corresponding cloud service provider using his private key. when sufficient number of transactions are accumulated, The cloud service provider creates a block containing the transactions and adds them to the local copy of the blockchain. After that the CSP broadcasts the block to other nodes within the blockchain. 
To verify the block other nodes first matches the previous block hash in the received block to the previous block hash of the latest block within the local copy of the blockchain. 


In the Cloud Computing environment, each operation conducted is meticulously recorded as a transaction by the cloud service provider (CSP). Subsequently, every transaction undergoes digital signing by the respective CSP using its private key. When sufficient number of transactions are accumulated, The cloud service provider creates a block containing the transactions and adds them to the local copy of the blockchain. Then the CSP broadcasts the block to other nodes within the blockchain network. To verify the block other nodes first matches the previous block hash in the received block to the previous block hash of the latest block within the local copy of the blockchain. Then the CSPs verify the digital signature of each transaction within the blockchain by using the public key of the CSP which created the transaction. If the block passes the validation process, it is added to the local copy of the blockchain other wise the block is discarded. 




Furthermore, to ensure the authenticity of each transaction within the blockchain, nodes verify the digital signature associated with each transaction. This verification process employs the public key of the corresponding CSP responsible for generating the transaction.

#### Implementation
To Implement the proposed model we have developed a file upload system using the proposed model.
In the implementation multiple CSPs are running from different ports within a single machine. Following are different modules of the implementation.
##### 1. Key generation
At first when a cloud service provider joins the blockchain network. It   generates a pair of public and private keys and stores them locally. The private key will be used to digitally sign the transaction. The public key will be used as an identity to the cloud service provider. By using the public key other CSPs will be able to Identify this cloud service provider. The public key will also be used by other CSPs to verify the digital signature of this CSP.
##### 2. Requesting blockchain from other CSPs
When a cloud service provider joins the blockchain network It need to first get the existing blockchain. It requests the blockchain from one of the existing cloud service providers. After receiving the blockchain it verifies previous block hash of every blockchain. The previous block hash stored in every block must be equal to to the hash of the previous block. In case of genesis block the hash of the previous block should be empty string. After that it verifies the digital signature of every transaction in each block. If the blockchain passes the verification process It is stored locally by the newly joined cloud service provider.

```kotlin
function joinBlockchainNetwork() {
    // Step 1: Request existing blockchain
    blockchain = requestBlockchainFromExistingProvider();

    // Step 2: Verify previous block hash for each block
    for each block in blockchain {
        if block.isGenesisBlock() {
            if block.previousBlockHash != emptyString {
                return "Invalid blockchain: Genesis block previous block hash must be empty";
            }
        } else {
            previousBlock = blockchain.getPreviousBlock(block);
            if (previousBlock == null) {
                return "Invalid blockchain: Previous block not found";
            }
            if (block.previousBlockHash != calculateHash(previousBlock)) {
                return "Invalid blockchain: Previous block hash mismatch";
            }
        }
    }

    // Step 3: Verify digital signature of every transaction in each block
    for each block in blockchain {
        for each transaction in block.transactions {
            if (!verifyDigitalSignature(transaction)) {
                return "Invalid blockchain: Digital signature verification failed";
            }
        }
    }

    // Step 4: Store blockchain locally
    storeBlockchainLocally(blockchain);

    return "Blockchain successfully joined and verified";
}

```


##### 3. File upload 
Every CSP has an http endpoint for uploading a file. If an user want to upload a file It makes a post request to appropriate http endpoint. CSP first validates the file then it stores the file locally. 

```php
public function store(Request $request)
    {
        $request->validate([
            'file' => 'required|file'
        ]);
        // validates the request

  

        $file = $request->file('file');
        //extracts the file from the http request

        $path = $file->store('/tests', 'public');
        // Stores the file locally.


        $fileContent = $file->getContent();
        //get the contents of the file in form of string

        $fileHash = Hash::make($fileContent);
        // calculate hash digest for the file

        $transaction = Transaction::createTransaction([
            'uploaded_file_path' => url('storage/' . $path),
            'file_uploaded_by' => 'sagnik',
            'file_stored_by' => file_get_contents(base_path() . '/.block_chain_keys/public'),
            'file_hash' => $fileHash,
        ]);
        // Create a transaction which will be stored inside a blockchain 
        // The transaction contains the uploaded file path, the public key of the csp which stores the transaction. Hash digest of the file.


        return $transaction;
        // returns contents of the transaction in a json format.
  

    }
```

##### 4. Transaction
After that it creates a hash digest of the file. The hash digest of the file is required to verify the data integrity of the file. After that a transaction is created for the file upload operation. The transaction contains file upload path. the public key of the csp where file is uploaded. and the hash digest of the file. The transaction is stored locally. 

##### 5. Blockchain
Once sufficient number of transactions are accumulated a block is created containing the transactions which are not yet stored in the blockchain. Then the block is broadcasted to other members of the cloud federation. Other members verify the previous block hash of the block and then they verify the digital signature of every transaction. The the block passes the verification process then the block is added to the local copy of blockchain.

```js
function handleBlockCreation(transactions) {
    // Step 1: Create a new block containing the accumulated transactions
    newBlock = createBlock(transactions);

    // Step 2: Broadcast the new block to other members of the cloud federation
    broadcastBlock(newBlock);

    
   // Step 3: Add the verified block to the local copy of the blockchain
        addToLocalBlockchain(newBlock);
        return "Block added to the blockchain";
    
}

function createBlock(transactions) {
    // Create a new block with the provided transactions
    // Return the new block
}

function broadcastBlock(block) {
    // Broadcast the provided block to other members of the cloud federation
}


function addToLocalBlockchain(block) {
    // Add the provided block to the local copy of the blockchain
}


```
##### 6. To Verify The Integrity of a file
To verify the integrity of a file, the file can be requested from the cloud service provider which stores the file. Then the hash digest of the file is fetched from blockchain. We store the file hash during the file upload operation in a transaction. And since the hash digest of of the file is stored in a blockchain it is preictally impossible to tamper. Since hash function is a one way function it is impossible to reverse engineer the file from the hash value. So if the data integrity is compromised it will be known to the end user.  

```js
function verifyFileIntegrity(fileId) {
    // Step 1: Request the file from the cloud service provider
    file = requestFileFromCSP(fileId);
    
    // Step 2: Fetch the hash digest of the file from the blockchain
    fileHash = fetchFileHashFromBlockchain(fileId);

    // Step 3: Calculate the hash digest of the retrieved file
    calculatedHash = calculateHash(file);

    // Step 4: Compare the fetched hash digest with the calculated hash digest
    if (fileHash == calculatedHash) {
        return "File integrity verified: The hash digests match";
    } else {
        return "File integrity compromised: The hash digests do not match";
    }
}

function requestFileFromCSP(fileId) {
    // Request the file with the specified ID from the cloud service provider
    // Return the retrieved file
}

function fetchFileHashFromBlockchain(fileId) {
    // Fetch the hash digest of the file with the specified ID from the blockchain
    // Return the fetched hash digest
}

function calculateHash(file) {
    // Calculate the hash digest of the provided file
    // Return the calculated hash digest
}
```
##### Transaction verification
To verify a transaction we need to verify the digital signature of the transaction. Every transaction contains the public key of the signer. The CSP which needs to verify the transaction can verify the transaction using the transaction data and the senders public key. 
```php

function verify(transaction)
{
        try {
            publicKey = transaction.file_uploaded_by;
            // public key of the csp which was responsible for storing the file.
            signature = transaction.digital_signature;
            // digital signature of the csp which stored the file.
           
            return verifyTransaction(json_encode({
                'uploaded_file_path' => transaction.uploaded_file_path,
                'file_uploaded_by' => transaction.file_uploaded_by,
                'file_stored_by' => $transaction.file_stored_by,
                'file_hash' => $transaction.file_hash,
            }), publicKey,signature);
        } catch {
            return false;
 }
function json_encode(array){
// Converts an object or array to srting
}

function verifyTransaction(jsonString, publicKey, signature){
// verifies the transaction using the transaction metadata , public key of the sender, and digital signature of the sender on the transation.

if(
the signature is valid
) return true;
return false;
}

```

##### blockchain verification
To verify the blockchain at first in every  lock the stored previous block hash is matched with actual calculated previous block hash. If they do not match then data integrity has been compromised. If the the block passes this verification then Every transaction in every block is verified using the above mentioned transaction verification method.
```js
function verifyBlockchain(blockchain) {
    // Step 1: Iterate through each block in the blockchain
    for each block in blockchain {
        // Step 2: Verify the previous block hash of the current block
        if (!verifyPreviousBlockHash(block)) {
            return "Blockchain verification failed: Previous block hash mismatch";
        }
        
        // Step 3: Verify every transaction in the current block
        for each transaction in block.transactions {
            if (!verifyTransaction(transaction)) {
                return "Blockchain verification failed: Transaction verification failed";
            }
        }
    }
    
    // Blockchain verification passed
    return "Blockchain verification successful";
}

function verifyPreviousBlockHash(block) {
    // Verify the previous block hash of the provided block
    // Return true if verification succeeds, false otherwise
}

function verifyTransaction(transaction) {
    // Verify the provided transaction using the transaction verification method
    // Return true if verification succeeds, false otherwise
}

```

