# NPI Endpoint

This endpoint returns pharmacy prices for drugs and pharmacies, filtered optionally by quantity.

Since pharmacy NPIs are required, it is assumed you already know the details of the pharmacy and so these are omitted.

**URL**: https://pharmacylocationservices.procarerx.com/Pharmacy/PharmacyPricingNPI

## Pharmacy Collection [/PharmacyPricingNPI/{?ndclist,npilist,qtylist,clientId}]

### List Pharmacies [GET]

+ Parameters
      + ndclist (required, string, `49999046730,35356089430`) ... A comma-separated list of drug NDCs (normalized 11-digit form) to search pharmacies for.
      + npilist (required, string, `1154473718,1326147562`) ... A comma-separated list of pharmacy NPIs to search for.
      + qtylist = 1 (optional, string, `1,30`) ... The quantities to search for. If unspecified, results for one (1) unit will be displayed. For example, to price a unit containing 30 caplets, enter 30 in this field.
      + clientId (required, string, `secret-credentials`) ... The Procare-distributed API credentials.

+ Response 200 (application/json)

      + Headers

            X-Total-Count: 1

      + Body

            {
             "DrugPricingNPI":  [
                {
                  "npi": "1154473718",
                  "ndc": "35356089430",
                  "quantity": 30,
                  "price": 17.318,
                  "RouteOfAdministration": "ORAL",
                  "DosageForm": "TABLET",
                  "Strength": "20 MG",
                  "PackageSize": 30,
                  "DosageFormDescription": "EA",
                  "LabelName": "ATORVASTATIN 20 MG TABLET"
                },
                {
                  "npi": "1154473718",
                  "ndc": "49999046730",
                  "quantity": 1,
                  "price": 6.8606,
                  "RouteOfAdministration": "ORAL",
                  "DosageForm": "TABLET",
                  "Strength": "20 MG",
                  "PackageSize": 30,
                  "DosageFormDescription": "EA",
                  "LabelName": "LIPITOR 20 MG TABLET"
                }
              ]
            }

      + Schema

            {
              "type": "object",
              "$schema": "http://json-schema.org/draft-03/schema",
              "required": true,
              "properties":{
                "DrugPricingNPI": {
                  "type": "array",
                  "required": true,
                  "items": {
                    "type": "object",
                    "required": true,
                    "properties":{
                      "npi": {
                        "type": "string",
                        "required": true
                      },
                      "ndc": {
                        "type": "string",
                        "required": true
                      },
                      "price": {
                        "type": "string",
                        "required": true
                      },
                      "RouteOfAdministration": {
                        "type": "string",
                        "required": false
                      },
                      "DosageForm": {
                        "type": "string",
                        "required": false
                      },
                      "Strength": {
                        "type": "string",
                        "required": false
                      },
                      "PackageSize": {
                        "type": "string",
                        "required": false
                      },
                      "DosageFormDescription": {
                        "type": "string",
                        "required": false
                      },
                      "LabelName": {
                        "type": "string",
                        "required": false
                      }
                    }
                  }
                }
              }
            }
