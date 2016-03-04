# Pharmacies Endpoint

This endpoint returns pharmacy prices filtered by location, drug, and optionally pharmacy.

## Pharmacy Collection [/pharmacies/{?radius,zipCode,quantity,ndclist,npilist,page,perPage}]

### List Pharmacies [GET]

+ Parameters
      + radius (required, number, `3.5`) ... A decimal number of miles to search from a zipcode.
      + zipCode (required, integer, `70809`) ... A zipcode epicenter of the search.
      + ndclist (required, string, `00003421511,00003421521,00003421531`) ... A comma-separated list of drug NDCs to search pharmacies for.
      + npilist (optional, string, `1679941827,1841467594`) ... A comma-separated list of pharmacy NPIs to filter by.
      + quantity = 1 (optional, number, `1`) ... The quantity to search for. Multiplies the returned prices by this amount.
      + page = `1` (optional, number, `1`) ... The page to retrieve. Defaults to `1`.
      + perPage = `10` (optional, number, `10`) ... The number of results per page. Defaults to `10`.
      + clientId (required, string, `secret-credentials`) ... The Procare-distributed API credentials.

+ Response 200 (application/json)

      + Headers

            X-Total-Count: 1

      + Body

            {
             "DrugPricing":  [
                {
                  "npi": "Pharmacy NPI",
                  "name": "CVS Pharmacy #2506",
                  "pharmacy": "CVS Pharmacy",
                  "phoneNumber": "(555) 555-5555",
                  "street1": "1234 Mayfair Blvd",
                  "street2": "Suite 225",
                  "city": "El Dorado",
                  "state": "GA",
                  "zipCode": "55555",
                  "ndc": "00003421511",
                  "price": "17.00",
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
                      "street1": {
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
                      "ndc": {
                        "type": "string",
                        "required": true
                      },
                      "price": {
                        "type": "string",
                        "required": true
                      },
                      "RowID": {
                        "type": "string",
                        "required": false
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
