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
Every CSP has an http endpoint for uploading a file. 
