# Platform Usage


## Creating an Identity 
```sh
```

## Getting TOKEN from the IDM  
```sh
curl --location --request POST 'http://localhost:3005/oauth2/token' \
--header 'Authorization: Basic MzlmZTFlZTAtNGRjOS00YmFjLTlmMDMtZjhkYzkyZjUxMzgyOmVmNzJiNjNjLWM3ZmUtNDRhOS1iZGZhLTIxZDhkZTE4MTYyMw==' \
--header 'Content-Type: application/x-www-form-urlencoded' \
--header 'Accept: application/json' \
--header 'Cookie: session=eyJyZWRpciI6Ii8ifQ==; session.sig=HX0gTNYqa01FJdR9Uxe4s1mNPEA' \
--data-raw 'username=admin@test.com&password=1234&grant_type=password'
```

## Creating an entity 

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



## Get Blockchain Transaction Recipt


## Get Data from Blockchain


## Verify Data from Blockchain