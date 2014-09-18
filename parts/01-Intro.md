FORMAT: X-1A

# Procare API Documentation

## Making a Request

### Versioning

All responses include an `X-Api-Version` header with current version of the API, which is currently 0.1.


### Content Type

###### Requests

All POST, PATCH, and PUT methods accept the standard `application/x-www-form-urlencoded` content type (or `multipart/form-data` for uploads). In addition you can send the data as JSON, but don't forget to set the `Content-Type` header correctly:

    Content-Type: application/json


###### Responses

Response content types are specified using the `Accept` header. Currently we only support the JSON format:

    Accept: application/json


### Encryption

We require all requests are done over SSL.

### Encoding

UTF-8, *always*. Every string passed to and from the API needs to be encoded in UTF-8.

### Casing

All JSON keys and querystring parameters should use Pascal case, *always*, both in responses and requests.

### Trailing Slash

All request paths should end in a trailing slash. If the requested path doesn't end in a slash, an HTTP redirect is issued to the same URL with a slash appended. Note that the redirect may cause any data submitted in a POST request to be lost.

### Example Request

    $ curl --header 'X-Api-Key: ######' --header 'Accept: application/json' https://api.procarerx.com/pharmacies/?within=5&zip=70809

## API Keys

The api key should be included in every request in the X-Api-Key header.


    GET /pharmacies/?within=5&zip=70809
      X-Api-Key=#######

## Pagination

Resources that return multiple records will usually be paginated.

Pagination takes place through the use of the Link header as defined by RFC5988.

An example Link header for pagination:

    Link: <https://api.github.com/user/repos?page=1&per_page=100>; rel="prev"
    <https://api.github.com/user/repos?page=3&per_page=100>; rel="next"

For pagination, we only use `prev`, `next`, `first`, and `last` rel types. Total number of records will be transmitted in the `X-Total-Count` header, even if there is only one page.
