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

##### 3. File upload workflow
Every CSP has an http endpoint for uploading a file. If an user want to upload a file It makes a post request to appropriate http endpoint. CSP first validates the file then it stores the file locally. 

##### 4. Transaction
After that it creates a hash digest of the file. The hash digest of the file is required to verify the data integrity of the file. After that a transaction is created for the file upload operation. The transaction contains file upload path. the public key of the csp where file is uploaded. and the hash digest of the file. The transaction is stored locally. 

##### 5. Blockchain
Once sufficient number of transactions are accumulated a block is created containing the transactions which are not yet stored in the blockchain. Then the block is broadcasted to other members of the cloud federation. Other members verify the previous block hash of the block and then they verify the digital signature of every transaction. The the block passes the verification process then the block is added to the local copy of blockchain.
##### 6. To Verify The Integrity of a file
To verify the integrity of a file, the file can be requested from the cloud service provider which stores the file. Then the hash digest of the file is fetched from blockchain. We store the file hash during the file upload operation in a transaction. And since the hash digest of of the file is stored in a blockchain it is preictally impossible to tamper. Since hash function is a one way function it is impossible to reverse engineer the file from the hash value. So if the data integrity is compromised it will be known to the end user.  

##### Transaction verification
To verify a transaction we need to verify the digital signature of the transaction. Every transaction contains the public key of the signer. The CSP which needs to verify the transaction can verify the transaction using the transaction data and the senders public key. 

##### How to verify the blockchain
To verify the blockchain at first in every  lock the stored previous block hash is matched with actual calculated previous block hash. If they do not match then data integrity has been compromised. If the the block passes this verification then Every transaction in every block is verified using the above mentioned transaction verification method.
