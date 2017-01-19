# Affiliation

A contacts affiliations to a place.

## Fields

Field | Description | Notes
----- | ----------- | -----
name<br> *string* | Name of affiliation | Required
place_type<br> *enum* {other_place, prison, retirement_village, school} | Type of place | Required
identifier<br> *string* | A unique identifier for the contact at the place
contact_id<br> *integer* | ID of contact | Read-only
created_at<br> *datetime* | When the affiliation was created | Read-only
updated_at<br> *datetime* | When the affiliation was last updated | Read-only

## List Affiliations
```shell
curl https://api.adventisthub.com/api/contacts/17/affiliations
-H "Authorization: Bearer token"
-H "Accept: application/vnd.adventisthub.v1+json"
```
```json
{
  "data": [
    {
      "id": "12",
      "type": "affiliations",
      "attributes": {
        "name": "Wahroonga Primary School",
        "place_type": "school",
        "identifier": "",
        "contact_id": 17,
        "created_at": "2016-11-29T11:38:26.945+11:00",
        "updated_at": "2016-11-29T11:38:26.945+11:00"
      }
    }
  ]
}
```

`GET /api/contacts/{contact-id}/affiliations`

An array of all affiliations for the contact.

## Show Affiliation
```shell
curl https://api.adventisthub.com/api/contacts/17/affiliations/12
-H "Authorization: Bearer token"
-H "Accept: application/vnd.adventisthub.v1+json"
```
```json
{
  "data": {
    "id": "12",
    "type": "affiliations",
    "attributes": {
      "name": "Wahroonga Primary School",
      "place_type": "school",
      "identifier": "",
      "contact_id": 17,
      "created_at": "2016-11-29T11:38:26.945+11:00",
      "updated_at": "2016-11-29T11:38:26.945+11:00"
    }
  }
}
```

`GET /api/contacts/{contact-id}/affiliations/{affiliation-id}`

Show a contacts affiliation.

## Create Affiliation
```shell
curl -X POST https://api.adventisthub.com/api/contacts/17/affiliations
-H "Authorization: Bearer token"
-H "Content-type: application/json"
-H "Accept: application/vnd.adventisthub.v1+json"
-d '{"affiliation": {"name": "Wahroonga Prison", "place_type": "prison"}}'
```
```json
{
  "data": {
    "id": "13",
    "type": "affiliations",
    "attributes": {
      "name": "Wahroonga Prison",
      "place_type": "prison",
      "identifier": null,
      "contact_id": 17,
      "created_at": "2017-01-16T14:45:59.067+11:00",
      "updated_at": "2017-01-16T14:45:59.067+11:00"
    }
  }
}
```

`POST /api/contacts/{contact-id}/affiliations`

## Update Affiliation
```shell
curl -X PATCH https://api.adventisthub.com/api/contacts/17/affiliations/13
-H "Authorization: Bearer token"
-H "Content-type: application/json"
-H "Accept: application/vnd.adventisthub.v1+json"
-d '{"affiliation": {"name": "Wyee Prison", "identifier": "PN555891"}}'
```
```json
{
  "data": {
    "id": "13",
    "type": "affiliations",
    "attributes": {
      "name": "Wyee Prison",
      "place_type": "prison",
      "identifier": "PN555891",
      "contact_id": 17,
      "created_at": "2017-01-16T14:45:59.067+11:00",
      "updated_at": "2017-01-16T14:49:47.067+11:00"
    }
  }
}
```

`PATCH /api/contacts/{contact-id}/affiliations/{affiliation-id}`

## Delete Affiliation
```shell
curl -X DELETE https://api.adventisthub.com/api/contacts/17/affiliations/13
-H "Authorization: Bearer token"
-H "Accept: application/vnd.adventisthub.v1+json"
```
```json
{
  "data": {
    "id": "13",
    "type": "affiliations",
    "attributes": {
      "name": "Wyee Prison",
      "place_type": "prison",
      "identifier": "PN555891",
      "contact_id": 17,
      "created_at": "2017-01-16T14:45:59.067+11:00",
      "updated_at": "2017-01-16T14:49:47.067+11:00"
    }
  }
}
```

`DELETE /api/contacts/{contact-id}/affiliations/{affiliation-id}`