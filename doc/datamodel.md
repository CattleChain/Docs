# Data Model

CattleChain Project using set of standard data model developed under the FIWARE Smart Data Model Initiative.
Smart Data Models. This is a collaborative initiative impulsed by FIWARE Foundation, TMForum and IUDX, and many other people and organizations contributing to the data models.
These data models are open-licensed allowing free use, free modification, and free sharing of modifications. 

To know more about the Smart Data Model follow [here](https://smartdatamodels.org/), [github](https://github.com/smart-data-models).


## CattleChain DataModels 

### Animal

It is the main entity of the system. It stores all the status information of the animal as its data and its states. The model is valid for dairy and meat.

**Example Payload**
```json
{
  "@context": [
    "https://smartdatamodels.org/context.jsonld",
    "https://uri.etsi.org/ngsi-ld/v1/ngsi-ld-core-context.jsonld"
  ],
  "birthdate": {
    "@type": "DateTime",
    "@value": "2017-01-01T01:20:00Z"
  },
  "breed": "Merina",
  "calvedBy": "urn:ngsi-ld:Animal:aa9f1295-425c-8ba3-b745-b653097d5a87",
  "fedWith": "urn:ngsi-ld:FEED:1ea0f120-4474-11e8-9919-0000000081",
  "healthCondition": "healthy",
  "id": "urn:ngsi-ld:Animal:ca3f1295-500c-4aa3-b745-d143097d5c01",
  "legalId": "ES142589652140",
  "locatedAt": "urn:ngsi-ld:AgriParcel:1ea0f120-4474-11e8-9919-672036642081",
  "location": {
    "coordinates": [
      -4.754444444,
      41.640833333
    ],
    "type": "Point"
  },
  "modifiedAt": "2017-05-04T12:30:00Z",
  "ownedBy": "http://person.org/leon",
  "phenologicalCondition": "adult",
  "relatedSource": [
    {
      "application": "urn:ngsi-ld:AgriApp:72d9fb43-53f8-4ec8-a33c-fa931360259a",
      "applicationEntityId": "app:sheep1"
    }
  ],
  "reproductiveCondition": "inCalf",
  "sex": "female",
  "siredBy": "urn:ngsi-ld:Animal:aa9f1295-425c-8ba3-b745-b653097d5a87",
  "species": "sheep",
  "type": "Animal",
  "weight": 65.3,
  "welfareCondition": "adequate"
}
```

**Important Links**
[Animal Data Model Github](https://github.com/smart-data-models/dataModel.Agrifood/tree/master/Animal)
[Animal Data Model Schema](https://github.com/smart-data-models/dataModel.Agrifood/tree/master/Animal/schema.json)
[Animal Data Model Description](https://github.com/smart-data-models/dataModel.Agrifood/tree/master/Animal/doc/spec.md)


### Farm

It is the main entity of the system. It stores all the status information of the animal as its data and its states.

**Example Payload**
```json
{
  "@context": [
    "https://smartdatamodels.org/context.jsonld",
    "https://uri.etsi.org/ngsi-ld/v1/ngsi-ld-core-context.jsonld"
  ],
  "address": {
    "addressCountry": "ES",
    "addressLocality": "Valdepe\u00f1as",
    "streetAddress": "Camino de Membrilla 17",
    "type": "PostalAddress"
  },
  "contactPoint": {
    "email": "wheatfarm@email.com",
    "telephone": "00349674532",
    "type": "ContactPoint"
  },
  "createdAt": "2017-01-01T01:20:00Z",
  "description": "A farm producing wheat",
  "hasAgriParcel": [
    "urn:ngsi-ld:AgriParcel:26ba4be0-4474-11e8-8ec1-ab9e0ea93835",
    "urn:ngsi-ld:AgriParcel:2d5b8874-4474-11e8-8d6b-dbe14425b5e4"
  ],
  "hasBuilding": [
    "urn:ngsi-ld:Building:a6ba44e0-4474-11e8-8ed1-ab9e0ea93827",
    "urn:ngsi-ld:Building:d95b8874-4474-11e8-8d6b-dbe144258354"
  ],
  "id": "urn:ngsi-ld:AgriFarm:72d9fb43-53f8-4ec8-a33c-fa931360259a",
  "landLocation": {
    "coordinates": [
      [
        [
          100,
          0
        ],
        [
          101,
          0
        ],
        [
          101,
          1
        ],
        [
          100,
          1
        ],
        [
          100,
          0
        ]
      ]
    ],
    "type": "Polygon"
  },
  "location": {
    "coordinates": [
      100,
      0
    ],
    "type": "Point"
  },
  "modifiedAt": "2017-05-04T12:30:00Z",
  "name": "Wheat farm",
  "ownedBy": "urn:ngsi-ld:Person:fce9dcbc-4479-11e8-9de1-cb228de7a15c",
  "relatedSource": [
    {
      "application": "urn:ngsi-ld:AgriApp:72d9fb43-53f8-4ec8-a33c-fa931360259a",
      "applicationEntityId": "app:farm1"
    }
  ],
  "seeAlso": [
    "https://example.org/concept/farm",
    "https://datamodel.org/example/farm"
  ],
  "type": "AgriFarm"
}
```

**Important Links**
[Farm Data Model Github](https://github.com/smart-data-models/dataModel.Agrifood/tree/master/AgriFarm)
[Farm Data Model Schema](https://github.com/smart-data-models/dataModel.Agrifood/tree/master/AgriFarm/schema.json)
[Farm Data Model Description](https://github.com/smart-data-models/dataModel.Agrifood/tree/master/AgriFarm/doc/spec.md)


### Parcel

It corresponds to the internal divisions of the farm.

**Example Payload**
```json
{
  "@context": [
    "https://smartdatamodels.org/context.jsonld",
    "https://uri.etsi.org/ngsi-ld/v1/ngsi-ld-core-context.jsonld"
  ],
  "area": 200,
  "belongsTo": "urn:ngsi-ld:AgriFarm:f67adcbc-4479-22bc-9de1-cb228de7a765",
  "category": "arable",
  "createdAt": "2017-01-01T01:20:00Z",
  "cropStatus": "seeded",
  "description": "Spring wheat",
  "hasAgriCrop": "urn:ngsi-ld:AgriCrop:36021150-4474-11e8-a721-af07c5fae7c8",
  "hasAgriParcelChildren": [
    "urn:ngsi-ld:AgriParcel:26ba4be0-4474-11e8-8ec1-ab9e0ea93835",
    "urn:ngsi-ld:AgriParcel:2d5b8874-4474-11e8-8d6b-dbe14425b5e4"
  ],
  "hasAgriParcelParent": "urn:ngsi-ld:AgriParcel:1ea0f120-4474-11e8-9919-672036642081",
  "hasAgriSoil": "urn:ngsi-ld:AgriSoil:429d1338-4474-11e8-b90a-d3e34ceb73df",
  "hasDevice": [
    "urn:ngsi-ld:Device:4a40aeba-4474-11e8-86bf-03d82e958ce6",
    "urn:ngsi-ld:Device:63217d24-4474-11e8-9da2-c3dd3c36891b",
    "urn:ngsi-ld:Device:68e091dc-4474-11e8-a398-df010c53b416",
    "urn:ngsi-ld:6f44b54e-4474-11e8-8577-d7ff6a8ef551"
  ],
  "id": "urn:ngsi-ld:AgriParcel:72d9fb43-53f8-4ec8-a33c-fa931360259a",
  "lastPlantedAt": {
    "@type": "DateTime",
    "@value": "2016-08-22T10:18:16Z"
  },
  "location": {
    "coordinates": [
      [
        100,
        0
      ],
      [
        101,
        0
      ],
      [
        101,
        1
      ],
      [
        100,
        1
      ],
      [
        100,
        0
      ]
    ],
    "type": "Polygon"
  },
  "modifiedAt": "2017-05-04T12:30:00Z",
  "ownedBy": "urn:ngsi-ld:Person:fce9dcbc-4479-11e8-9de1-cb228de7a15c",
  "relatedSource": [
    {
      "application": "urn:ngsi-ld:AgriApp:72d9fb43-53f8-4ec8-a33c-fa931360259a",
      "applicationEntityId": "app:parcel1"
    }
  ],
  "seeAlso": [
    "https://example.org/concept/agriparcel",
    "https://datamodel.org/example/agriparcel"
  ],
  "type": "AgriParcel"
}
```

**Important Links**
[Parcel Data Model Github](https://github.com/smart-data-models/dataModel.Agrifood/tree/master/AgriParcel)
[Parcel Data Model Schema](https://github.com/smart-data-models/dataModel.Agrifood/blob/master/AgriParcel/schema.json)
[Parcel Data Model Description](https://github.com/smart-data-models/dataModel.Agrifood/blob/master/AgriParcel/doc/spec.md)



### Parcel Operation

It corresponds Parcel Operation.

**Example Payload**
```json
{
  "@context": [
    "https://smartdatamodels.org/context.jsonld",
    "https://uri.etsi.org/ngsi-ld/v1/ngsi-ld-core-context.jsonld"
  ],
  "createdAt": "2017-01-01T01:20:00Z",
  "description": "Monthly fertiliser application",
  "endedAt": {
    "@type": "DateTime",
    "@value": "2016-08-22T10:18:16Z"
  },
  "hasAgriParcel": "urn:ngsi-ld:AgriParcel:318366a9-7643-4d8e-9a11-c76a8c29d8eb",
  "hasAgriProductType": "urn:ngsi-ld:AgriProductType:a8f616b8-13fb-473a-8e61-b7a80c6c93ec",
  "hasOperator": "urn:ngsi-ld:Person:fce9dcbc-4479-11e8-9de1-cb228de7a15c",
  "id": "urn:ngsi-ld:AgriParcelOperation:e1e9d3a3-074f-46f1-9375-52000d05a62b",
  "irrigationRecord": "https://example.com/agriparcelrecords/irrigationrecord1",
  "modifiedAt": "2017-05-04T12:30:00Z",
  "operationType": "fertiliser",
  "plannedEndAt": {
    "@type": "DateTime",
    "@value": "2016-08-22T10:18:16Z"
  },
  "plannedStartAt": {
    "@type": "DateTime",
    "@value": "2016-08-22T10:18:16Z"
  },
  "quantity": 40,
  "relatedSource": [
    {
      "application": "urn:ngsi-ld:AgriApp:72d9fb43-53f8-4ec8-a33c-fa931360259a",
      "applicationEntityId": "app:parcelop1"
    }
  ],
  "reportedAt": {
    "@type": "DateTime",
    "@value": "2016-08-22T10:18:16Z"
  },
  "result": "ok",
  "seeAlso": [
    "https://example.org/concept/agriparcelop",
    "https://datamodel.org/example/agriparcelop"
  ],
  "startedAt": {
    "@type": "DateTime",
    "@value": "2016-08-22T10:18:16Z"
  },
  "status": "finished",
  "type": "AgriParcelOperation",
  "waterSource": "rainwater capture",
  "workOrder": "https://example.com/agriparcelrecords/workorder1",
  "workRecord": "https://example.com/agriparcelrecords/workrecord1"
}
```

**Important Links**
[Parcel Data Model Github](https://github.com/smart-data-models/dataModel.Agrifood/tree/master/AgriParcelOperation)
[Parcel Data Model Schema](https://github.com/smart-data-models/dataModel.Agrifood/blob/master/AgriParcelOperation/schema.json)
[Parcel Data Model Description](https://github.com/smart-data-models/dataModel.Agrifood/blob/master/AgriParcelOperation/doc/spec.md)


### Parcel Records

It corresponds Parcel Operation records.

**Example Payload**
```json
{
  "@context": [
    "https://smartdatamodels.org/context.jsonld",
    "https://uri.etsi.org/ngsi-ld/v1/ngsi-ld-core-context.jsonld"
  ],
  "airTemperature": 20,
  "atmosphericPressure": 1013.25,
  "createdAt": "2017-01-01T01:20:00Z",
  "description": "Monthly fertiliser application",
  "hasAgriParcel": "urn:ngsi-ld:AgriParcel:d3676010-d815-468c-9e01-25739c5a25ed",
  "hasDevice": [
    "urn:ngsi-ld:Device:4a40aeba-4474-11e8-86bf-03d82e958ce6",
    "urn:ngsi-ld:Device:63217d24-4474-11e8-9da2-c3dd3c36891b",
    "urn:ngsi-ld:Device:68e091dc-4474-11e8-a398-df010c53b416",
    "urn:ngsi-ld:6f44b54e-4474-11e8-8577-d7ff6a8ef551"
  ],
  "id": "urn:ngsi-ld:AgriParcelRecord:8f5445e6-f49b-496e-833b-e65fc97fcab7",
  "leafRelativeHumidity": 0.25,
  "leafTemperature": 25.1,
  "leafWetness": 1.0,
  "location": {
    "coordinates": [
      [
        100,
        0
      ],
      [
        101,
        0
      ],
      [
        101,
        1
      ],
      [
        100,
        1
      ],
      [
        100,
        0
      ]
    ],
    "type": "Polygon"
  },
  "modifiedAt": "2017-05-04T12:30:00Z",
  "observedAt": {
    "@type": "DateTime",
    "@value": "2017-05-04T12:30:00Z"
  },
  "relatedSource": [
    {
      "application": "urn:ngsi-ld:AgriApp:72d9fb43-53f8-4ec8-a33c-fa931360259a",
      "applicationEntityId": "app:parcelrec1"
    }
  ],
  "relativeHumidity": 0.15,
  "seeAlso": [
    "https://example.org/concept/agriparcelrec",
    "https://datamodel.org/example/agriparcelrec"
  ],
  "soilMoistureEc": 17,
  "soilMoistureVwc": 0.08,
  "soilSalinity": 1198.11,
  "soilTemperature": 27,
  "solarRadiation": 15,
  "type": "AgriParcelRecord"
}
```

**Important Links**
[Parcel Data Model Github](https://github.com/smart-data-models/dataModel.Agrifood/tree/master/AgriParcelRecord)
[Parcel Data Model Schema](https://github.com/smart-data-models/dataModel.Agrifood/blob/master/AgriParcelRecord/schema.json)
[Parcel Data Model Description](https://github.com/smart-data-models/dataModel.Agrifood/blob/master/AgriParcelRecord/doc/spec.md)



### Blockchain Transaction Receipt

Blockchain trasaction receipt for the any of transaction happend in the blockchain.
In this project we are using Alastria Network, which is a ethereum client.
Currently transaction receipts are store in key-values but in future this payload will be used.

**Example Payload**
```json
{
    "id":"urn:ngsi-ld:dataModel:id:VINF:36225393",
    "type":"DLTtxReceipt",
    "refEntity":{
        "type":"Relationship",
        "object":"urn:ngsi-ld:Animal:1"
    },
    "TxReceipts":{
        "type":"Property",
        "value":{
            "to":"0x9a3dbca554e9f6b9257aaa24010da8377c57c17e",
            "from":"0x4c962a968ff8cc5c99688602969ada5caa3a92cb",
            "keys":[
                "id",
                "type",
                "species",
                "legalId",
                "birthdate",
                "@context"
            ],
            "logs":{
                "id":"log_e04a3da4",
                "data":"0x0000000000000000000000004c962a968ff8cc5c99688602969ada5caa3a92cb75726e3a6e6773692d6c643a416e696d616c3a310000000000000000000000000000000000000000000000000000000000000000000000000000000060802b30000000000000000000000000000000000000000000000000000000000000008000000000000000000000000000000000000000000000000000000000000000317a6470754171367250624133745a6b694441396d425355337a3872355a37544739716970754a4c45413570384145714c58000000000000000000000000000000",
                "topics":[
                    "0x117ef0a3887baaa508b007da020a6dc877e9f3e78883d885d11e272070e45175"
                ],
                "logAddress":"0x9a3DBCa554e9f6b9257aAa24010DA8377C57c17e",
                "removed":false,
                "logIndex":0,
                "blockHash":"0xce0a88fa83d6b928f65f5eca653e98e81ed67702be1d4253c43b1ccb30d51f56",
                "blockNumber":345522,
                "transactionHash":"0x935dc16fa0b2000e609d6cc366c4fe2cb9557ec47ee94455e135af4259105517",
                "transactionIndex":0
            },
            "status":false,
            "dltType":"eth",
            "gasUsed":112188,
            "blockHash":"0xce0a88fa83d6b928f65f5eca653e98e81ed67702be1d4253c43b1ccb30d51f56",
            "logsBloom":"0x00000000000000000000000000000000000000000002000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000080000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000020000000000000000000000000100000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000080000000000000000002000000000000000000000000000000000000000000000000000000000",
            "objectType":"asset",
            "blockNumber":345522,
            "storageType":"merkletree",
            "transactionHash":"0x935dc16fa0b2000e609d6cc366c4fe2cb9557ec47ee94455e135af4259105517",
            "contractAddress":"0x9a3DBCa554e9f6b9257aAa24010DA8377C57c17e",
            "transactionIndex":0,
            "cumulativeGasUsed":112188
        }
    },
    "dateCreated":{
        "type":"Property",
        "value":{
            "@type":"DateTime",
            "@value":"1970-03-25T22:57:25Z"
        }
    },
    "dateModified":{
        "type":"Property",
        "value":{
            "@type":"DateTime",
            "@value":"2019-03-15T08:10:09Z"
        }
    },
    "@context":[
        "https://smartdatamodels.org/context.jsonld"
    ]
}
```

**Important Links**
[Parcel Data Model Github](https://github.com/smart-data-models/dataModel.DistributedLedgerTech/tree/master/DLTtxReceipt)
[Parcel Data Model Schema](https://github.com/smart-data-models/dataModel.DistributedLedgerTech/blob/master/DLTtxReceipt/schema.json)
[Parcel Data Model Description](https://github.com/smart-data-models/dataModel.DistributedLedgerTech/blob/master/DLTtxReceipt/doc/spec.md)

