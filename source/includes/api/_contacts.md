# Contact

Represents a contact.

## Fields

Field | Description | Notes
--------- | ------- | -------
first_name<br> *string* | First name | Required
last_name<br> *string* | Last name | Required
name<br> *string* | First and last name | Read-only
email<br> *string* | Email address
status<br> *enum* {active, unavailable, baptized, do_not_contact, deleted} | Status of contact. Defaults to active
hub_team_id<br> *integer* | ID of the hub team the contact belongs to. Defaults to tokens team
user_id<br>*integer* | ID of the user the contact belongs to | Read-only
lat<br> *float* | Latitude of home address | Read-only
lng<br> *float* | Longitude of home address | Read-only
language_id<br>*integer* | ID of the language (primarily spoken) by the contact
date_of_birth<br>*date* | Date of birth
gender<br> *enum* {gender_unknown, female, male} | Gender. Defaults to gender_unknown
religion_id<br>*integer* | ID of the religion the contact belongs too
activities_count<br>*integer* | Number of activities associated with the contact | Read-only
visit_frequency<br>*integer* | The number of weeks between visits. Defaults to the users default visit frequency
next_visit<br>*date* | Scheduled date for the next visit/interaction with the contact | Read-only
approach_id<br>*integer* | ID of the approach the contact belongs too
brand_id<br>*integer* | ID of the brand the contact belongs too
campaign_id<br>*integer* | ID of the campaign the contact belongs too
created_at<br>*datetime* | When the contact was created | Read-only
updated_at<br>*datetime* | When the contact was last updated | Read-only

## List Contacts
```shell
curl https://hubapi.adventistchurch.com/api/contacts
-H "Authorization: Bearer token"
-H "Accept: application/vnd.adventisthub.v1+json"
```

```json
{
  "data": [
    {
      "id": "33",
      "type": "contacts",
      "attributes": {
        "first_name": "Sally",
        "last_name": "Page",
        "name": "Sally Page",
        "email": "sallypage@gmail.com",
        "status": "active",
        "created_at": "2016-11-30T11:10:00.891+11:00",
        "updated_at": "2016-11-30T11:16:34.988+11:00",
        "hub_team_id": 6,
        "user_id": 5,
        "lat": null,
        "lng": null,
        "language_id": 1,
        "date_of_birth": "1950-02-01",
        "gender": "female",
        "religion_id": 7,
        "activities_count": 14,
        "visit_frequency": 1,
        "next_visit": "2016-12-05",
        "campaign_id": null,
        "approach_id": null,
        "brand_id": null
      },
      "links": {
        "self": "/api/contacts/33"
      }
    }
  ]
}
```
`GET /api/contacts`

An array of contacts the user has assigned to them.

## Show Event

```shell
curl https://hubapi.adventistchurch.com/api/contacts/33
-H "Authorization: Bearer token"
-H "Accept: application/vnd.adventisthub.v1+json"
```
```json
{
  "data": {
    "id": "33",
    "type": "contacts",
    "attributes": {
      "first_name": "Sally",
      "last_name": "Page",
      "name": "Sally Page",
      "email": "sallypage@gmail.com",
      "status": "active",
      "created_at": "2016-11-30T11:10:00.891+11:00",
      "updated_at": "2016-11-30T11:16:34.988+11:00",
      "hub_team_id": 6,
      "user_id": 5,
      "lat": null,
      "lng": null,
      "language_id": 1,
      "date_of_birth": "1950-02-01",
      "gender": "female",
      "religion_id": 7,
      "activities_count": 14,
      "visit_frequency": 1,
      "next_visit": "2016-12-05",
      "campaign_id": null,
      "approach_id": null,
      "brand_id": null
    },
    "links": {
      "self": "/api/contacts/33"
    }
  }
}
```

`GET /api/contacts/{contact-id}`

Show a contact.

## Create Contact
```shell
curl -X POST https://hubapi.adventistchurch.com/api/contacts
-H "Authorization: Bearer token"
-H "Content-type: application/json"
-H "Accept: application/vnd.adventisthub.v1+json"
-d '{"contact": {"first_name": "Roger", "last_name": "Fox", "gender":"male"}}'
```
```json
{
  "data": {
    "id": "46",
    "type": "contacts",
    "attributes": {
      "first_name": "Roger",
      "last_name": "Fox",
      "name": "Roger Fox",
      "email": null,
      "status": "active",
      "created_at": "2017-01-17T08:53:13.492+11:00",
      "updated_at": "2017-01-17T08:53:13.492+11:00",
      "hub_team_id": 6,
      "user_id": 5,
      "lat": null,
      "lng": null,
      "language_id": 1,
      "date_of_birth": null,
      "gender": "male",
      "religion_id": null,
      "activities_count": 0,
      "visit_frequency": 1,
      "next_visit": "2017-01-24",
      "support_alert_id": null,
      "campaign_id": null,
      "approach_id": null,
      "brand_id": null
    },
    "links": {
      "self": "/api/contacts/46"
    }
  }
}
```

`POST /api/contacts`

## Update Contact
```shell
curl -X PATCH https://hubapi.adventistchurch.com/api/contacts/46
-H "Authorization: Bearer token"
-H "Content-type: application/json"
-H "Accept: application/vnd.adventisthub.v1+json"
-d '{"contact": {"date_of_birth": "1991-08-06"}}'
```
```json
{
  "data": {
    "id": "46",
    "type": "contacts",
    "attributes": {
      "first_name": "Roger",
      "last_name": "Fox",
      "name": "Roger Fox",
      "email": null,
      "status": "active",
      "created_at": "2017-01-17T08:53:13.492+11:00",
      "updated_at": "2017-01-17T08:59:03.970+11:00",
      "hub_team_id": 6,
      "user_id": 5,
      "lat": null,
      "lng": null,
      "language_id": 1,
      "date_of_birth": "1991-08-06",
      "gender": "male",
      "religion_id": null,
      "activities_count": 0,
      "visit_frequency": 1,
      "next_visit": "2017-01-24",
      "support_alert_id": null,
      "campaign_id": null,
      "approach_id": null,
      "brand_id": null
    },
    "links": {
      "self": "/api/contacts/46"
    }
  }
}
```

`PATCH /api/contacts/{contact-id}`
