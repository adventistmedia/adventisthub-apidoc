# Contact Address

The contacts home and mailing address.

## Fields


Field | Description | Notes
----- | ----------- | -----
location<br> *enum* {home, mailing} | Address type | Required
status<br> *enum* {active, deleted} | Status | Read-only
attention<br> *string* | Attention
address1<br> *string* | Address line 1 | Required
address2<br> *string* | Address line 2
address3<br> *string* | Address line 3
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
curl https://adhubapi.adventistchurch.com/api/contacts/11/addresses
-H "Authorization: Bearer team_token"
-H "Accept: application/vnd.adhub.v1+json"
```
```json
{
  "data": [
    {
      "id": "34",
      "type": "addresses",
      "attributes": {
        "attention": null,
        "address1": "150 Fox Valley Road",
        "address2": null,
        "address3": null,
        "city": "Wahroonga",
        "region": "NSW",
        "postcode": "2076",
        "country_code": "AU",
        "country": "Australia",
        "full_address": "150 Fox Valley Road, WAHROONGA NSW 2076, Australia",
        "status": "active",
        "lat": -33.7309681,
        "lng": 151.1042531,
        "location": "home",
        "created_at": "2017-01-16T17:19:33.177+11:00",
        "updated_at": "2017-01-16T17:19:33.177+11:00"
      }
    }
  ]
}
```

`GET /api/contact/{contact-id}/addresses`

An array of a contacts home and mailing addresses.

## Show Address
```shell
curl https://adhubapi.adventistchurch.com/api/contacts/11/addresses/34
-H "Authorization: Bearer team_token"
-H "Accept: application/vnd.adhub.v1+json"
```
```json
{
  "data": {
    "id": "34",
    "type": "addresses",
    "attributes": {
      "attention": null,
      "address1": "150 Fox Valley Road",
      "address2": null,
      "address3": null,
      "city": "Wahroonga",
      "region": "NSW",
      "postcode": "2076",
      "country_code": "AU",
      "country": "Australia",
      "full_address": "150 Fox Valley Road, WAHROONGA NSW 2076, Australia",
      "status": "active",
      "lat": -33.7309681,
      "lng": 151.1042531,
      "location": "home",
      "created_at": "2017-01-16T17:19:33.177+11:00",
      "updated_at": "2017-01-16T17:19:33.177+11:00"
    }
  }
}
```

`GET /api/contacts/{contact-id}/addresses/{address-id}`

Show a contacts address.

## Create Address

```shell
curl -X POST https://adhubapi.adventistchurch.com/api/contacts/11/addresses
-H "Authorization: Bearer team_token"
-H "Content-type: application/json"
-H "Accept: application/vnd.adhub.v1+json"
-d '{"address": {"location": "mailing", "country_code": "AU", "address1": "148 Fox Valley Road", "city": "Wahroonga", "region": "NSW", "postcode": "2076"}}'
```
```json
{
  "data": {
    "id": "35",
    "type": "addresses",
    "attributes": {
      "attention": null,
      "address1": "148 Fox Valley Road",
      "address2": null,
      "address3": null,
      "city": "Wahroonga",
      "region": "NSW",
      "postcode": "2076",
      "country_code": "AU",
      "country": "Australia",
      "full_address": "148 Fox Valley Road, WAHROONGA NSW 2076, Australia",
      "status": "active",
      "lat": -33.7323472,
      "lng": 151.1018849,
      "location": "mailing",
      "created_at": "2017-01-16T17:22:48.363+11:00",
      "updated_at": "2017-01-16T17:22:48.363+11:00"
    }
  }
}
```

`POST /api/contact/{contact-id}/addresses`

## Update Address

```shell
curl -X PATCH https://adhubapi.adventistchurch.com/api/contacts/11/addresses/35
-H "Authorization: Bearer team_token"
-H "Content-type: application/json"
-H "Accept: application/vnd.adhub.v1+json"
-d '{"address": {"attention": "Adventist Media"}}'
```
```json
{
  "data": {
    "id": "35",
    "type": "addresses",
    "attributes": {
      "attention": "Adventist Media",
      "address1": "148 Fox Valley Road",
      "address2": null,
      "address3": null,
      "city": "Wahroonga",
      "region": "NSW",
      "postcode": "2076",
      "country_code": "AU",
      "country": "Australia",
      "full_address": "148 Fox Valley Road, WAHROONGA NSW 2076, Australia",
      "status": "active",
      "lat": -33.7323472,
      "lng": 151.1018849,
      "location": "mailing",
      "created_at": "2017-01-16T17:22:48.363+11:00",
      "updated_at": "2017-01-16T17:22:48.363+11:00"
    }
  }
}
```

`PATCH /api/contacts/{contact-id}/addresses/{address-id}`

## Delete Address

```shell
curl -X DELETE https://adhubapi.adventistchurch.com/api/contact/11/addresses/35
-H "Authorization: Bearer team_token"
-H "Accept: application/vnd.adhub.v1+json"
```
```json
{
  "data": {
    "id": "35",
    "type": "addresses",
    "attributes": {
      "attention": "Adventist Media",
      "address1": "148 Fox Valley Road",
      "address2": null,
      "address3": null,
      "city": "Wahroonga",
      "region": "NSW",
      "postcode": "2076",
      "country_code": "AU",
      "country": "Australia",
      "full_address": "148 Fox Valley Road, WAHROONGA NSW 2076, Australia",
      "status": "deleted",
      "lat": -33.7323472,
      "lng": 151.1018849,
      "location": "mailing",
      "created_at": "2017-01-16T17:22:48.363+11:00",
      "updated_at": "2017-01-16T17:22:48.363+11:00"
    }
  }
}
```

`DELETE /api/contact/{contact-id}/addresses/{address-id}`