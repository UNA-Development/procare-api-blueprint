# Pharmacies Endpoint

This endpoint returns pharmacies filtered by location, company, and/or drug.

## Pharmacy Collection [/pharmacies/{?company,radius,zipCode,latitude,longitude,drug,updatedSince,page,perPage}]

### List Pharmacies [GET]

+ Parameters
      + company (optional, string, `CVS Pharmacy`) ... A particular company to filter pharmacies by.
      + radius (optional, number, `3.5`) ... A decimal number of miles to search from a zipcode. Must be paired with the `zipCode` or `latitude`/`longitude` parameters if used.
      + zipCode (optional, integer, `70809`) ... A zipcode epicenter of the search. Must be paired with the `radius` parameter if used.
      + latitude (optional, number, `3.5`) ... A latitude point to search from. Must be paired with the `longitude` and `radius` parameters if used.
      + longitude (optional, integer, `70809`) ... A longitude point to search from. Must be paired with the `latitude` and `radius` parameters if used.
      + drug (optional, string, `1011626`) ... An <??id: NDC, rxcui, string search??> of a drug. Only pharmacies that offer this drug will be returned in the results.
      + updatedSince (optional, string, '2014-09-18T10:32:59+00:00') ... A UTC GMT timestamp that optionally filters out pharmacies whose drugs have not been updated since the given time.
      + page = `1` (optional, number, `1`) ... The page to retrieve.
      + perPage = `10` (optional, number, `10`) ... The number of results per page.

+ Response 200 (application/json)

      + Headers

            X-Total-Count: 1

      + Body

            {
             "pharmacies":  [
                {
                  "id": "<<??someUniqueIdentifier??>>",
                  "uri": "/pharmacies/<<??someUniqueIdentifier??>>/",
                  "url": "https://api.procarerx.com/pharmacies/<<??someUniqueIdentifier??>>/",
                  "display": "A Human-readable Display Name for This Pharmacy",
                  "photo": "<??url: to avatar or image of this pharmacy or pharmacy company??>",
                  "company": "CVS Pharmacy",
                  "phoneNumber": "(555) 555-5555",
                  "street": "Mayfair Blvd Suite 225",
                  "city": "El Dorado",
                  "state": "GA",
                  "zipCode": "55555",
                  "latitude": 29.943453,
                  "longitude": -90.129776
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
                      "id": {
                        "type": "string",
                        "required": true
                      },
                      "uri": {
                        "type": "string",
                        "required": true
                      },
                      "url": {
                        "type": "string",
                        "required": false
                      },
                      "display": {
                        "type": "string",
                        "required": true
                      },
                      "photo": {
                        "type": "string",
                        "required": true
                      },
                      "company": {
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
                      "latitude": {
                        "type": "number",
                        "required": true
                      },
                      "longitude": {
                        "type": "number",
                        "required": true
                      }
                    }
                  }
                }
              }
            }

## Pharmacies [/pharmacies/{pharmacyId}/]

+ Parameters
    + pharmacyId (string, `<<??someUniqueIdentifier??>>`) ... The id of the pharmacy

### Get a Pharmacy [GET]

+ Response 200 (application/json; charset=utf-8)

    + Body

            {
              "id": "<<??someUniqueIdentifier??>>",
              "uri": "/pharmacies/<<??someUniqueIdentifier??>>/",
              "url": "https://api.procarerx.com/pharmacies/<<??someUniqueIdentifier??>>/",
              "display": "A Human-readable Display Name for This Pharmacy",
              "photo": "<??url: to avatar or image of this pharmacy or pharmacy company??>",
              "company": "CVS Pharmacy",
              "phoneNumber": "(555) 555-5555",
              "street": "Mayfair Blvd Suite 225",
              "city": "El Dorado",
              "state": "GA",
              "zipCode": "55555",
              "latitude": 29.943453,
              "longitude": -90.129776,
              "drugs": [
                 {
                  "id": "<<??someUniqueIdentifier??>>",
                  "uri": "/drugs/<<??someUniqueIdentifier??>>/",
                  "url": "https://api.procarerx.com/drugs/<<??someUniqueIdentifier??>>/",
                  "display": "A Human-readable Display Name for This Drug",
                  "marketPrice": "22.00",
                  "discountPrice": "17.00",
                  "unit": "syringe",
                  "capacity": "5",
                  "lastUpdated": "2014-09-18T10:32:59+00:00"
                }
              ]
            }

    + Schema

            {
              "type": "object",
              "$schema": "http://json-schema.org/draft-03/schema",
              "required": true,
              "properties":{
                "id": {
                  "type": "string",
                  "required": true
                },
                "uri": {
                  "type": "string",
                  "required": true
                },
                "url": {
                  "type": "string",
                  "required": false
                },
                "display": {
                  "type": "string",
                  "required": true
                },
                "photo": {
                  "type": "string",
                  "required": true
                },
                "company": {
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
                "latitude": {
                  "type": "number",
                  "required": true
                },
                "longitude": {
                  "type": "number",
                  "required": true
                },
                "drugs": {
                  "type":"array",
                  "required":true,
                  "items": {
                    "type":"object",
                    "required":true,
                    "properties":{
                      "id": {
                        "type":"string",
                        "required":true
                      },
                      "uri": {
                        "type":"string",
                        "required":true
                      },
                      "url": {
                        "type": "string",
                        "required": false
                      },
                      "display": {
                        "type":"string",
                        "required":true
                      },
                      "marketPrice": {
                        "type":"string",
                        "required":true
                      },
                      "discountPrice": {
                        "type":"string",
                        "required":true
                      },
                      "unit": {
                        "type":"string",
                        "required":true
                      },
                      "capacity": {
                        "type":"string",
                        "required":true
                      },
                      "lastUpdated": {
                        "type": "string",
                        "required":true
                      }
                    }
                  }
                }
              }
            }
