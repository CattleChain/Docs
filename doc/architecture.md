# Cattlechain Architecture

CattleChain core platform is consist of various FIWARE Generic Enablers. Figure present the architecture of the CattleChain platform.

![Architecture](https://raw.githubusercontent.com/CattleChain/Docs/master/images/architecture.png)


## Generic Enablers

A Context Broker Generic Enabler is the core and mandatory component of any  “Powered by FIWARE” platform or solution. It enables to manage context information in a highly decentralized and large-scale manner.

In the CattleChain Project there are the generic enablers has been used:

### KeyRock

Keyrock is the FIWARE component responsible for Identity Management. Using Keyrock (in conjunction with other security components such as PEP Proxy and Authzforce) enables you to add OAuth2-based authentication and authorization security to your services and applications.
The main identity management concepts within Keyrock are:

* Users:

	* Have a registered account in Keyrock.
	* Can manage organizations and register applications.	

* Organizations:

	* Are group of users that share resources of an application (roles and permissions).
	*	Users can be members or owners (manage the organization).

* Applications:

	* has the client role in the OAuth 2.0 architecture and will request protected user data.
	* Are able to authenticate users using their Oauth credentials (ID and secret) which unequivocally identify the application
	* Define roles and permissions to manage authorization of users and organizations
	* Can register Pep Proxy to protect backends.
	* Can register IoT Agents.

Keyrock provides both a GUI and an API interface.

to know more about keyrock please follow keyrock [documentation](https://fiware-idm.readthedocs.io/en/latest/).


### PEP Proxy- Wilma

Wilma is a PEP Proxy - it can be combined with other security components such as Keyrock and Authzforce to enforce access control to your backend applications. This means that only permitted users will be able to access your Generic Enablers or REST services. Identity Management allows you to manage specific permissions and policies to resources allowing different access levels for your users.

to know more about wilma please follow Wilma [documentation](https://fiware-pep-proxy.readthedocs.io/en/latest/).

**important: to enable the Canis Major integration please use the fork version of PEP Proxy source code can be found in FIWARE-BLOCKCHAIN [github](https://github.com/FIWARE-Blockchain/fiware-pep-proxy)**


### Orion-LD (Core)

Orion-LD is an alternative NGSI-LD Context Broker written in C/C++. It is a standalone executable and therefore small, fast, lightweight and easy to handle. Context brokers allow for the management and requesting context of information in a structured manner based on linked data standards following the NGSI-LD specification. Orion-LD is more suitable for smaller installations or possibly in embedded environments - it currentlys supports only a subset of the standard NGSI-LD endpoints.

(Documentation)[https://github.com/FIWARE/context.Orion-LD/tree/develop/doc/manuals-ld]


### Quantumleap

QuantumLeap is a REST service for storing, querying and retrieving NGSI v2 and NGSI-LD (experimental support) spatial-temporal data. QuantumLeap converts NGSI semi-structured data into tabular format and stores it in a time-series database, associating each database record with a time index and, if present in the NGSI data, a location on Earth. REST clients can then retrieve NGSI entities by filtering entity sets through time ranges and spatial operators. Note that, from the client's stand point, these queries are defined on NGSI entities as opposed to database tables. However, the query functionality available through the REST interface is quite basic and most complex queries typically require clients to use the database directly.


(Documentation)[https://quantumleap.readthedocs.io/en/latest/]

### Cosmos

The Cosmos BigData Analysis GE is a set of tools that help achieving the tasks of Streaming and Batch processing over context data.

(Documentation)[https://fiware-cosmos-spark.readthedocs.io/en/latest/#what-is-cosmos]

#### Cosmos ORION-SPARK Connector:

The Cosmos Generic Enabler enables easier BigData analysis over context, integrated with some of the most popular BigData platforms.
(Documentation)[https://fiware-cosmos-spark.readthedocs.io/en/latest/]


### CanisMajor - Blockchain Adaptor

**Under Development**

CanisMajor is a blockchain adaptor that supports various DLTs, the adaptor aims to submit the data to DLT and works with NGSI-LD and NGSI-V2 as well.
CanisMajor Adaptor recommend using AEI contract Model for the Ethereum Clients. AEI (Asset,Event, Identity) Smart Contract is written in Solidity using ERC721 standard (NFT).


to know more about CanisMajor please follow CanisMajor [documentation](https://fiware-blockchain.github.io/CanisMajor/).


Canis Major recommend to use the [AEI Contract Model](https://github.com/FIWARE-Blockchain/AEIContract).

AEI Smart Contract is written in Solidity using ERC721 standard (NFT) and can be use with Ethereum Clients. It is compatible with FIWARE-Canis Major Adaptor to store the data in blockchain. AEI, asset, events (metadata), relationship, is designed to store the NGSI-LD model with the help of Canis Major Adaptor.


### Taurus - LedgerSync

**Under Development**

Taurus is a blockchain listener that supports various DLT, and the listener aims to listen to Blockchain Events and store data in FIWARE. This component compliments FIWARE as an OffChainDB.

(Link)[https://github.com/FIWARE-Blockchain/Taurus]
