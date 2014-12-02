# Pharmacies Endpoint

This endpoint returns pharmacies filtered by location, company, and/or drug.

## Pharmacy Collection [/pharmacies/{?radius,zipCode,drug,page,perPage}]

### List Pharmacies [GET]

+ Parameters
      + radius (required, number, `3.5`) ... A decimal number of miles to search from a zipcode.
      + zipCode (required, integer, `70809`) ... A zipcode epicenter of the search.
      + drug (required, string, `"00002751001`) ... An NDC to search pharmacies by. May be passed multiple times in the querystring parameters (i.e. `drug="00002751001&drug="00002751017`). Only pharmacies that offer these drugs will be returned in the results.
      + quantity = 1 (optional, number, `1`) ... The quantity to search for.
      + page = `1` (optional, number, `1`) ... The page to retrieve. Defaults to `1`.
      + perPage = `10` (optional, number, `10`) ... The number of results per page. Defaults to `10`.
      + cliendId (required, string, `secret-credentials`) ... The Procare-distributed API credentials.

+ Response 200 (application/json)

      + Headers

            X-Total-Count: 1

      + Body

            {
             "pharmacies":  [
                {
                  "npi": "Pharmacy NPI",
                  "name": "CVS Pharmacy #2506",
                  "pharmacy": "CVS Pharmacy",
                  "phoneNumber": "(555) 555-5555",
                  "street": "1234 Mayfair Blvd",
                  "street2": "Suite 225",
                  "city": "El Dorado",
                  "state": "GA",
                  "zipCode": "55555",
                  "drugs": [
                     {
                      "ndc": "0002-7510-01",
                      "price": "17.00"
                    }
                  ]
                }
              ]
            }

      + Schema

            {
              "type": "object",
              "$schema": "http://json-schema.org/draft-03/schema",
              "required": true,
              "properties":{
                "pharmacies": {
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
                      "name": {
                        "type": "string",
                        "required": true
                      },
                      "pharmacy": {
                        "type": "string",
                        "required": true
                      },
                      "phoneNumber": {
                        "type": "string",
                        "required": true
                      },
                      "street": {
                        "type": "string",
                        "required": true
                      },
                      "street2": {
                        "type": "string",
                        "required": false
                      },
                      "city": {
                        "type": "string",
                        "required": true
                      },
                      "state": {
                        "type": "string",
                        "required": true
                      },
                      "zipCode": {
                        "type": "string",
                        "required": true
                      },
                      "drugs": {
                        "type":"array",
                        "required":true,
                        "items": {
                          "type":"object",
                          "required":true,
                          "properties":{
                            "ndc": {
                              "type":"string",
                              "required":true
                            },
                            "price": {
                              "type":"string",
                              "required":true
                            }
                          }
                        }
                      }
                    }
                  }
                }
              }
            }
