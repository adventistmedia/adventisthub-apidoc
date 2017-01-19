# Hub Team

Represents a Hub team.

## Fields

Field | Description | Notes
--------- | ------- | -------
name<br> *string* | Team name | Read-only
time_zone<br> *string* | Time zone of team | Read-only
country_code<br> *string* | Two letter uppercase country code | Read-only
country<br> *string* | Teams country name | Read-only
language_id<br>*integer* | ID of the language (primarily spoken) by team members | Read-only
status<br>*enum* {active, archived} | Status of team. Archived teams are not accessible | Read-only
lat<br> *float* | Address latitude | Read-only
lng<br> *float* | Address longitude | Read-only
created_at<br>*datetime* | When the event was created | Read-only
updated_at<br>*datetime* | When the event was last updated | Read-only

## List Hub Teams
```shell
curl https://hubapi.adventistchurch.com/api/hub_teams/all
-H "Authorization: Bearer token"
-H "Accept: application/vnd.adventisthub.v1+json"
```

```json
{
  "data": [
    {
      "id": "7",
      "type": "hub_teams",
      "attributes": {
        "name": "Bonnells Bays Church",
        "time_zone": "Sydney",
        "country_code": "AU",
        "country": "Australia",
        "language_id": 1,
        "status": "active",
        "lat": null,
        "lng": null,
        "created_at": "2016-10-24T17:35:22.819+11:00",
        "updated_at": "2017-01-12T11:53:07.578+11:00"
      }
    },
    {
      "id": "6",
      "type": "hub_teams",
      "attributes": {
        "name": "3am Church",
        "time_zone": "Sydney",
        "country_code": "AU",
        "country": "Australia",
        "language_id": 1,
        "status": "active",
        "lat": null,
        "lng": null,
        "created_at": "2016-10-24T17:32:18.298+11:00",
        "updated_at": "2017-01-12T11:53:07.578+11:00"
      }
    }
  ]
}
```
`GET /api/hub_teams/all`

An array of Hub teams the user has membership too.

## Show Hub Team

```shell
curl https://hubapi.adventistchurch.com/api/hub_teams
-H "Authorization: Bearer token"
-H "Accept: application/vnd.adventisthub.v1+json"
```
```json
{
  "data": {
    "id": "6",
    "type": "hub_teams",
    "attributes": {
      "name": "3am Church",
      "time_zone": "Sydney",
      "country_code": "AU",
      "country": "Australia",
      "language_id": 1,
      "status": "active",
      "lat": null,
      "lng": null,
      "created_at": "2016-10-24T17:32:18.298+11:00",
      "updated_at": "2017-01-12T11:53:07.578+11:00"
    }
  }
}
```

`GET /api/hub_teams`

Read the current Hub team based on the users token.