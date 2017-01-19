# Account Address

The users home and mailing address.

## Fields


Field | Description | Notes
----- | ----------- | -----
location<br> *enum* {home, mailing} | Address type | Required
status<br> *enum* {active, deleted} | Status | Read-only
attention<br> *string* | Attention
address1<br> *string* | Address line 1 | Required
address2<br> *string* | Address line 2
address3<br> *string* | Address line 3
locality<br> *string* | Locality/Suburb | *Required
city<br> *string* | City | *Required
region<br> *string* | Region/State/Province | *Required
postcode<br> *string* | Postcode/Zipcode | *Required
country_code<br> *string* | 2 letter upper case country code | Required
country<br> *string* | Country name | Read-only
full_address<br> *string* | Full address | Read-only
lat<br> *float* | Latitude of address | Read-only
lng<br> *float* | Longitude of address | Read-only
created_at<br> *datetime* | When the address was created | Read-only
updated_at<br> *datetime* | When the address was last updated | Read-only

\* Field requirement is dependent on the country of the address

## List Addresses
```shell
curl https://api.adventisthub.com/api/account/addresses
-H "Authorization: Bearer token"
-H "Accept: application/vnd.adventisthub.v1+json"
```
```json
{
  "data": [
    {
      "id": "9",
      "type": "addresses",
      "attributes": {
        "attention": null,
        "address1": "130 Fox Valley Rd",
        "address2": "",
        "address3": "",
        "locality": null,
        "city": "Denham Court",
        "region": "NSW",
        "postcode": "2565",
        "country_code": "AU",
        "country": "Australia",
        "full_address": "130 Fox Valley Rd, DENHAM COURT NSW 2565, Australia",
        "status": "active",
        "lat": -33.9650276,
        "lng": 150.828411,
        "location": "home",
        "created_at": "2016-11-16T16:20:39.205+11:00",
        "updated_at": "2016-11-16T16:20:39.205+11:00"
      }
    }
  ]
}
```

`GET /api/account/addresses`

An array of a users home and mailing addresses.

## Show Address
```shell
curl https://api.adventisthub.com/api/account/addresses/9
-H "Authorization: Bearer token"
-H "Accept: application/vnd.adventisthub.v1+json"
```
```json
{
  "data": {
    "id": "9",
    "type": "addresses",
    "attributes": {
      "attention": null,
      "address1": "130 Fox Valley Rd",
      "address2": "",
      "address3": "",
      "locality": null,
      "city": "Denham Court",
      "region": "NSW",
      "postcode": "2565",
      "country_code": "AU",
      "country": "Australia",
      "full_address": "130 Fox Valley Rd, DENHAM COURT NSW 2565, Australia",
      "status": "active",
      "lat": -33.9650276,
      "lng": 150.828411,
      "location": "home",
      "created_at": "2016-11-16T16:20:39.205+11:00",
      "updated_at": "2016-11-16T16:20:39.205+11:00"
    }
  }
}
```

`GET /api/account/addresses/{address-id}`

Show a user address.


## Create Address

```shell
curl -X POST https://api.adventisthub.com/api/account/addresses
-H "Authorization: Bearer token"
-H "Content-type: application/json"
-H "Accept: application/vnd.adventisthub.v1+json"
-d '{"address": {"location": "mailing", "country_code": "AU", "address1": "150 Fox Valley Road", "city": "Wahroonga", "region": "NSW", "postcode": "2076"}}'
```
```json
{
  "data": {
    "id": "33",
    "type": "addresses",
    "attributes": {
      "attention": null,
      "address1": "150 Fox Valley Road",
      "address2": null,
      "address3": null,
      "locality": null,
      "city": "Wahroonga",
      "region": "NSW",
      "postcode": "2076",
      "country_code": "AU",
      "country": "Australia",
      "full_address": "150 Fox Valley Road, WAHROONGA NSW 2076, Australia",
      "status": "active",
      "lat": -33.7309681,
      "lng": 151.1042531,
      "location": "mailing",
      "created_at": "2017-01-16T17:08:52.732+11:00",
      "updated_at": "2017-01-16T17:08:52.732+11:00"
    }
  }
}
```

`POST /api/account/addresses`

## Update Address

```shell
curl -X PATCH https://api.adventisthub.com/api/account/addresses/33
-H "Authorization: Bearer token"
-H "Content-type: application/json"
-H "Accept: application/vnd.adventisthub.v1+json"
-d '{"address": {"attention": "Adventist Media"}}'
```
```json
{
  "data": {
    "id": "33",
    "type": "addresses",
    "attributes": {
      "attention": "Adventist Media",
      "address1": "150 Fox Valley Road",
      "address2": null,
      "address3": null,
      "locality": null,
      "city": "Wahroonga",
      "region": "NSW",
      "postcode": "2076",
      "country_code": "AU",
      "country": "Australia",
      "full_address": "150 Fox Valley Road, WAHROONGA NSW 2076, Australia",
      "status": "active",
      "lat": -33.7309681,
      "lng": 151.1042531,
      "location": "mailing",
      "created_at": "2017-01-16T17:08:52.732+11:00",
      "updated_at": "2017-01-16T17:09:50.000+11:00"
    }
  }
}
```

`PATCH /api/account/addresses/{address-id}`

## Delete Address

```shell
curl -X DELETE https://api.adventisthub.com/api/account/addresses/33
-H "Authorization: Bearer token"
-H "Accept: application/vnd.adventisthub.v1+json"
```
```json
{
  "data": {
    "id": "33",
    "type": "addresses",
    "attributes": {
      "attention": "Adventist Media",
      "address1": "150 Fox Valley Road",
      "address2": null,
      "address3": null,
      "locality": null,
      "city": "Wahroonga",
      "region": "NSW",
      "postcode": "2076",
      "country_code": "AU",
      "country": "Australia",
      "full_address": "150 Fox Valley Road, WAHROONGA NSW 2076, Australia",
      "status": "deleted",
      "lat": -33.7309681,
      "lng": 151.1042531,
      "location": "mailing",
      "created_at": "2017-01-16T17:08:52.732+11:00",
      "updated_at": "2017-01-16T17:09:50.000+11:00"
    }
  }
}
```

`DELETE /api/account/addresses/{address-id}`