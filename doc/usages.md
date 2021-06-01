# Platform Usage
(For the Postman Collection and Envoirment variables please contact [us](mailto:harpreet.singh@fiware.org))

Here a example set of options given, for more please follow the documentation of used components and generic enablers.

## Creating an Identity in KeyRock
you can create user, application and oauth from the keyrock panel.

![keyrock](https://raw.githubusercontent.com/CattleChain/Docs/master/images/keyrock.png)

## Getting TOKEN from the IDM  

**Request**

```sh
curl --location --request POST 'http://localhost:3005/oauth2/token' \
--header 'Authorization: Basic MzlmZTFlZTAtNGRjOS00YmFjLTlmMDMtZjhkYzkyZjUxMzgyOmVmNzJiNjNjLWM3ZmUtNDRhOS1iZGZhLTIxZDhkZTE4MTYyMw==' \
--header 'Content-Type: application/x-www-form-urlencoded' \
--header 'Accept: application/json' \
--header 'Cookie: session=eyJyZWRpciI6Ii8ifQ==; session.sig=HX0gTNYqa01FJdR9Uxe4s1mNPEA' \
--data-raw 'username=admin@test.com&password=1234&grant_type=password'
```

**Response**

```json
{
    "access_token": "861ccaaf2ffd6c4a2050549706db63c88f46eded",
    "token_type": "bearer",
    "expires_in": 3599,
    "refresh_token": "2cb4167b30ed10a8995f6906c6b414f36f6e3553",
    "scope": [
        "bearer"
    ]
}
```

***User generated access_token for the 'X-Auth-Token'**

## Blockchain Accounts
For the development set of Blockchain Account (public/private keys) are generated using ganache-cli.

**User the base64(public_key:private_key) as 'DLT-Token' in header for the request**

**If the DLT-Token is missing or incorrect then request will not be consider by canis major adaptor**


## Creating an entity (PEP_PROXY)

```sh
curl --location --request POST 'http://localhost:1027/ngsi-ld/v1/entities/' \
--header 'X-Auth-Token: f227d2745e35ed04ebceccaa44095420dd25d0e5' \
--header 'Content-Type: application/ld+json' \
--header 'DLT-Token: MHg0Qzk2MkE5NjhGRjhDYzVDOTk2ODg2MDI5NjlBZGE1Q0FhM0E5MmNCOjB4ZmExYjFlM2NlZWMzNDEzNjM2YjA1MjdiOTMwNWE3MGVjMDA1NTNkM2U4MDliYWUwMDExYzYwOWY2MTg0MjUzNQ' \
--header 'Cookie: session=eyJyZWRpciI6Ii8ifQ==; session.sig=HX0gTNYqa01FJdR9Uxe4s1mNPEA' \
--data-raw '{
  "id": "urn:ngsi-ld:Animal:2",
  "type": "Animal",
  "modifiedAt": "2017-05-04T12:30:00Z",
  "species": {
    "type": "Property",
    "value": "sheep"
  },
  "relatedSource": {
    "type": "Property",
    "value": [
      {
        "application": "urn:ngsi-ld:AgriApp:72d9fb43-53f8-4ec8-a33c-fa931360259a",
        "applicationEntityId": "app:sheep1"
      }
    ]
  },
  "legalId": {
    "type": "Property",
    "value": "ES142589652140"
  },
  "birthdate": {
    "type": "Property",
    "value": {
      "@type": "DateTime",
      "@value": "2017-01-01T01:20:00Z"
    }
  },
  "sex": {
    "type": "Property",
    "value": "female"
  },
  "breed": {
    "type": "Property",
    "value": "Merina"
  },
  "calvedBy": {
    "type": "Relationship",
    "object": "urn:ngsi-ld:Animal:aa9f1295-425c-8ba3-b745-b653097d5a87"
  },
  "siredBy": {
    "type": "Relationship",
    "object": "urn:ngsi-ld:Animal:aa9f1295-425c-8ba3-b745-b653097d5a87"
  },
  "location": {
    "type": "GeoProperty",
    "value": {
      "type": "Point",
      "coordinates": [
        -4.754444444,
        41.640833333
      ]
    }
  },
  "weight": {
    "type": "Property",
    "value": 65.3
  },
  "ownedBy": {
    "type": "Relationship",
    "object": "http://person.org/leon"
  },
  "locatedAt": {
    "type": "Relationship",
    "object": "urn:ngsi-ld:AgriParcel:1ea0f120-4474-11e8-9919-672036642081"
  },
  "phenologicalCondition": {
    "type": "Property",
    "value": "adult"
  },
  "reproductiveCondition": {
    "type": "Property",
    "value": "inCalf"
  },
  "healthCondition": {
    "type": "Property",
    "value": "healthy"
  },
  "fedWith": {
    "type": "Relationship",
    "object": "urn:ngsi-ld:FEED:1ea0f120-4474-11e8-9919-0000000081"
  },
  "welfareCondition": {
    "type": "Property",
    "value": "adequate"
  },
  "@context": [
    "https://smartdatamodels.org/context.jsonld",
    "https://uri.etsi.org/ngsi-ld/v1/ngsi-ld-core-context.jsonld"
  ]
}'
```

## Get an Entity

```sh
curl --location --request GET 'http://localhost:1027/ngsi-ld/v1/entities/urn:ngsi-ld:Building:store339' \
--header 'X-Auth-Token: 7ca19ac956f1612c53bc78669cd79688db9d33d4' \
--header 'Content-Type: application/json' \
--data-raw '{
    "id": "urn:ngsi-ld:Building:store355",
    "type": "AgriProductType",
    "category": {
    	"type": "Property",
        "value": ["commercial"]
    },
    "address": {
        "type": "Property",
        "value": {
            "streetAddress": "Bornholmer Straße 65",
            "addressRegion": "Berlin",
            "addressLocality": "Prenzlauer Berg",
            "postalCode": "10439"
        },
        "verified": {
			"type": "Property",
			"value": true
		}
    },
    "@context": [
        "https://fiware.github.io/data-models/context.jsonld",
        "https://uri.etsi.org/ngsi-ld/v1/ngsi-ld-core-context.jsonld"
    ]
}'
```

## Updating an entity 

```sh
curl --location --request PATCH 'http://localhost:1027/ngsi-ld/v1/entities/urn:ngsi-ld:Animal:20/attrs' \
--header 'X-Auth-Token: 861ccaaf2ffd6c4a2050549706db63c88f46eded' \
--header 'Content-Type: application/ld+json' \
--header 'DLT-Token: MHg0Qzk2MkE5NjhGRjhDYzVDOTk2ODg2MDI5NjlBZGE1Q0FhM0E5MmNCOjB4ZmExYjFlM2NlZWMzNDEzNjM2YjA1MjdiOTMwNWE3MGVjMDA1NTNkM2U4MDliYWUwMDExYzYwOWY2MTg0MjUzNQ' \
--header 'Cookie: session=eyJyZWRpciI6Ii8ifQ==; session.sig=HX0gTNYqa01FJdR9Uxe4s1mNPEA' \
--data-raw '{ 
    "@context": [
        "https://schema.lab.fiware.org/ld/context",
        "http://uri.etsi.org/ngsi-ld/v1/ngsi-ld-core-context.jsonld"
    ],
    "species": {
    "type": "Property",
    "value": "cow"
  }
}'
```


## Get Blockchain Transaction Recipt (from canis major)

**Request**

```sh
curl --location --request GET 'http://localhost:4000/entity?entityId=urn:ngsi-ld:Animal:21'
```

**Response**

```json
{
    "offset": 0,
    "limit": 25,
    "count": 2,
    "records": [
        {
            "id": 4,
            "entityId": "urn:ngsi-ld:Animal:21",
            "txDetails": {
                "to": "0xcd125237903865f39caf6443209c89ba70a4a385",
                "from": "0x3423f4d100f8646aaf6829ce32cf801996f7007b",
                "keys": [
                    "id",
                    "type",
                    "modifiedAt",
                    "species",
                    "relatedSource",
                    "legalId",
                    "birthdate",
                    "sex",
                    "breed",
                    "calvedBy",
                    "siredBy",
                    "location",
                    "weight",
                    "ownedBy",
                    "locatedAt",
                    "phenologicalCondition",
                    "reproductiveCondition",
                    "healthCondition",
                    "fedWith",
                    "welfareCondition",
                    "@context"
                ],
                "logs": [
                    {
                        "id": "log_7b54619e",
                        "data": "0x0000000000000000000000003423f4d100f8646aaf6829ce32cf801996f7007b75726e3a6e6773692d6c643a416e696d616c3a323100000000000000000000000000000000000000000000000000000000000000000000000000000060b654c7000000000000000000000000000000000000000000000000000000000000008000000000000000000000000000000000000000000000000000000000000000317a647075416b5a684d436e3531437473414e67536e58614e6e476e65764570736e7743756f696a7a466a716a3257335251000000000000000000000000000000",
                        "type": "mined",
                        "topics": [
                            "0x117ef0a3887baaa508b007da020a6dc877e9f3e78883d885d11e272070e45175"
                        ],
                        "address": "0xcd125237903865f39caf6443209c89bA70a4A385",
                        "removed": false,
                        "logIndex": 0,
                        "blockHash": "0x3038007f150f19e239ed325d6035ad0798393f072d94e58c228bb4d1585b28a4",
                        "blockNumber": 6,
                        "transactionHash": "0xe3af2a382682f5a2ed4a6b15fde00eaeeccd94e838814dc4a567dcd15807602b",
                        "transactionIndex": 0
                    }
                ],
                "status": true,
                "dltType": "eth",
                "gasUsed": 110100,
                "version": "ngsi-ld",
                "blockHash": "0x3038007f150f19e239ed325d6035ad0798393f072d94e58c228bb4d1585b28a4",
                "logsBloom": "0x00000000000000000000000000000000000000000002000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000400000000000200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000100000000000000000000000000000000040000000000000000000000000000000000000000000000000000000000000000000000000000000000002000000000000000000000000000000000000000000000000000000000",
                "objectType": "asset",
                "txSignMode": false,
                "blockNumber": 6,
                "storageType": "ipfs",
                "encyptionMode": false,
                "contractAddress": "0xcd125237903865f39caf6443209c89bA70a4A385",
                "transactionHash": "0xe3af2a382682f5a2ed4a6b15fde00eaeeccd94e838814dc4a567dcd15807602b",
                "transactionIndex": 0,
                "cumulativeGasUsed": 110100
            },
            "createdAt": "2021-06-01T15:39:51.000Z",
            "updatedAt": "2021-06-01T15:39:51.000Z"
        },
        {
            "id": 5,
            "entityId": "urn:ngsi-ld:Animal:21",
            "txDetails": {
                "to": "0xcd125237903865f39caf6443209c89ba70a4a385",
                "from": "0x3423f4d100f8646aaf6829ce32cf801996f7007b",
                "keys": [
                    "@context",
                    "species"
                ],
                "logs": [
                    {
                        "id": "log_9aec53ac",
                        "data": "0x0000000000000000000000003423f4d100f8646aaf6829ce32cf801996f7007b75726e3a6e6773692d6c643a416e696d616c3a323100000000000000000000000000000000000000000000000000000000000000000000000000000060b654f2000000000000000000000000000000000000000000000000000000000000008000000000000000000000000000000000000000000000000000000000000000317a64707542335a53506777735352313232717a39504378534d786e4e5778774e717064794e456e5673366b314d62314231000000000000000000000000000000",
                        "type": "mined",
                        "topics": [
                            "0x829d21df03bcaa7394716da182142e158a58f007643bf885a86c3b6c0b8047eb"
                        ],
                        "address": "0xcd125237903865f39caf6443209c89bA70a4A385",
                        "removed": false,
                        "logIndex": 0,
                        "blockHash": "0xd69e695c40951547d3d4469fa5d7f7efb0493cca6f255968b1c105d2040f0111",
                        "blockNumber": 7,
                        "transactionHash": "0x6098e7bfab2911e99812b7997044943a61ea5d81906b6745608131ec75b8c380",
                        "transactionIndex": 0
                    }
                ],
                "status": true,
                "dltType": "eth",
                "gasUsed": 109301,
                "version": "ngsi-ld",
                "blockHash": "0xd69e695c40951547d3d4469fa5d7f7efb0493cca6f255968b1c105d2040f0111",
                "logsBloom": "0x00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000400000000000200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000040000000000000000000000000000000000000200000000000000000000000000000000000000000040000000000000000000000000000000000000000010000000000000000000",
                "objectType": "metadata",
                "txSignMode": false,
                "blockNumber": 7,
                "storageType": "ipfs",
                "encyptionMode": false,
                "contractAddress": "0xcd125237903865f39caf6443209c89bA70a4A385",
                "transactionHash": "0x6098e7bfab2911e99812b7997044943a61ea5d81906b6745608131ec75b8c380",
                "transactionIndex": 0,
                "cumulativeGasUsed": 109301
            },
            "createdAt": "2021-06-01T15:40:35.000Z",
            "updatedAt": "2021-06-01T15:40:35.000Z"
        }
    ]
}
```


## Get Data from Blockchain (Canis Major)

**Request**

```sh
curl --location --request GET 'http://localhost:4000/entity/5/dlt'
```

**Response**

```json
[
    "zdpuB3ZSPgwsSR122qz9PCxSMxnNWxwNqpdyNEnVs6k1Mb1B1"
]
```




## Verify Data from Blockchain (verifying from IPFS (IOTAMaM and MerkleTree also works here))

**Request**

```sh
curl --location --request GET 'http://localhost:4000/ipfs/zdpuB3ZSPgwsSR122qz9PCxSMxnNWxwNqpdyNEnVs6k1Mb1B1'
```

**Response**

```sh
{
    "species": {
        "type": "Property",
        "value": "cow"
    },
    "@context": [
        "https://schema.lab.fiware.org/ld/context",
        "http://uri.etsi.org/ngsi-ld/v1/ngsi-ld-core-context.jsonld"
    ]
}
```