# Blockchain Operations

## Introduction

The blockchain interaction in CattleChain project is really staright forward, earlier the development was happening using Hyperledger Sawtooth, as sawtooth lack in various aspect and we decided to use the stable/proven blockchain technology.

To do so we are currenlty using Alastria Network, a non-profit association that promotes the digital economy through the development of decentralised ledger technologies/Blockchain and also a member of FIWARE.

Alastria partners have two operational networks (Network T and Network B) on which nodes can be deployed (either regular nodes or critical: validators and bootnodes).

The first of Alastria’s partner node networks (Red T) is built on Quorum technology,an open-source Ethereum client developed under the LGPL license and written in Go. GoQuorum is an Ethereum-based protocol that runs private, permissioned networks.

To know more about it follow here:

[Alastria Network](https://github.com/alastria/alastria-node)
[Quorum Technology](https://docs.goquorum.consensys.net/en/stable/)


## Use of AEI Contract

CattleChain project using AEI (Asset, Event, Identity) Standard Contract. AEI Smart Contract is written in Solidity using ERC721 standard (NFT) and can be use with Ethereum Clients. It is compatible with FIWARE-Canis Major Adaptor to store the data in blockchain. AEI, asset, events (metadata), identity, is designed to store the NGSI-LD model with the help of Canis Major Adaptor.

ERC 721 Contract is follow OpenZepplin standards, security audits are trusted by leading organizations building decentralized systems.

### ERC 721
ERC 721 A standard interface for non-fungible tokens, also known as deeds.
The following standard allows for the implementation of a standard API for NFTs within smart contracts. This standard provides basic functionality to track and transfer NFTs.

We considered use cases of NFTs being owned and transacted by individuals as well as consignment to third party brokers/wallets/auctioneers (“operators”). NFTs can represent ownership over digital or physical assets. We considered a diverse universe of assets, and we know you will dream up many more:

Physical property — houses, unique artwork
Virtual collectables — unique pictures of kittens, collectable cards
“Negative value” assets — loans, burdens and other responsibilities
In general, all houses are distinct and no two kittens are alike. NFTs are distinguishable and you must track the ownership of each one separately.

to know more follow here: 

[ERC 721](https://eips.ethereum.org/EIPS/eip-721)
[OpenZepplin ERC721](https://docs.openzeppelin.com/contracts/2.x/api/token/erc721)

### AEI Contract Design

AEI contract is cosist of 3 aspects (see the figure below):

* Entity/Asset with a unique identity will be a new asset (1:1 mapping of asset to an identity).
* Event or Metadata of the asset/entity has a 1:n mapping.
* An Asset can have a 1:n relationship with any other asset.

![AEI Contract Design](https://raw.githubusercontent.com/FIWARE-Blockchain/AEIContract/master/docs/images/1.png)

#### Example
![Example](https://raw.githubusercontent.com/FIWARE-Blockchain/AEIContract/master/docs/images/2.png)

To Store the NGSI-LD model there are few possibilities with the help of some supported storage type:

1. IPFS
2. IOTA MaM
3. MerkleRoot

![Example](https://raw.githubusercontent.com/FIWARE-Blockchain/AEIContract/master/docs/images/3.png)

### Methods

```sh
- createAsset(bytes32 uuid, string memory _newHash)
- getAsset(bytes32 uuid)
- updateAsset(bytes32 uuid, string memory _newHash)
- removeAsset (bytes32 uuid)
- isValidAsset(bytes32 uuid, bytes32[] memory _proof, bytes32 _leaf)
- isValidAssetEthMessage(bytes32 uuid, bytes32 _messageHash, bytes memory _signature)
- addRelation(bytes32 uuid, bytes32 reluuid)
- getRelations(bytes32 uuid)
- removeRelation(bytes32 uuid, uint index)
- isValidRelation(bytes32 uuid, uint index, bytes32[] memory _proof, bytes32 _leaf)
- addMetadata(bytes32 uuid, string memory _metadatahash)
- getMetadatas(bytes32 uuid) public view returns (string[] memory)
- removeMetadata(bytes32 uuid, uint index)
- isValidMetadata(bytes32 uuid, uint index, bytes32[] memory _proof, bytes32 _leaf)
```
Apart from that ERC721, Ownable, MerkleProof, ECDSA methods are supported.

### Dependencies
_This project uses:_
 - truffle
 - NodeJS
 - Ganache-CLI (testrpc)
 - OpenZeppelin

 to know more follow here: 

[GitHub Source](https://github.com/FIWARE-Blockchain/AEIContract)


## Use of Canis Major

CanisMajor is a blockchain adaptor that supports various DLT.


### Canis Major Design
![CanisMajor Design](https://raw.githubusercontent.com/CattleChain/Docs/master/images/cm.png)


The way Canis Major work's in 'Powered By FIWARE' architecture as follows:

1. Request from the user is consist of the Payload, Header with token and DLT_ID (base64 of public key and private key of the blockchain).
2. Wilma PEP Proxy validate the token and check with the KeyRock IDM and validate the user, permission (Authentication and Autherisation).
3. Once the user is validate Wilma forward the request to the Context Broker and persist it.
4. Once the Payload stored in Context Broker Wilma notify to Canis Major with the configuration such as what attribute of the payload should be store, Blockchain Identity of the user.
5. Futher Canis Major persist the data in blockchain using AEI contract (will be explained futher in this chapter).


[Github Souce](https://github.com/FIWARE-Blockchain/CanisMajor)
[Documentation](https://fiware-blockchain.github.io/CanisMajor/architecture.html)


## Usages

### Creation of an Entity (Animal, Farm etc)

![Creation of an entity](https://raw.githubusercontent.com/CattleChain/Docs/master/images/createentity.png)

### Adding Metadata (eventy) on an Entity (Animal, Farm etc)

![Adding Metadata](https://raw.githubusercontent.com/CattleChain/Docs/master/images/addattr.png)

### Qyery

![Query](https://raw.githubusercontent.com/CattleChain/Docs/master/images/query.png)