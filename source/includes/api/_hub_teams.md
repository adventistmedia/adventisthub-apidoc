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
avatar_url<br>*string* | Image URL for team | Read-only
created_at<br>*datetime* | When the event was created | Read-only
updated_at<br>*datetime* | When the event was last updated | Read-only

## Search Hub Teams
```shell
curl https://hubapi.adventistchurch.com/api/hub_teams/search
-H "Authorization: Bearer team_token"
-H "Accept: application/vnd.adventisthub.v1+json"
-d '{"q": "Bay"}'
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
        "avatar_url": "https://res-1.cloudinary.com/image/avatar.jpg",
        "created_at": "2016-10-24T17:35:22.819+11:00",
        "updated_at": "2017-01-12T11:53:07.578+11:00"
      }
    },
    {
      "id": "6",
      "type": "hub_teams",
      "attributes": {
        "name": "Chad Bay Church",
        "time_zone": "Sydney",
        "country_code": "AU",
        "country": "Australia",
        "language_id": 1,
        "status": "active",
        "lat": null,
        "lng": null,
        "avatar_url": "https://res-1.cloudinary.com/image/avatar.jpg",
        "created_at": "2016-10-24T17:32:18.298+11:00",
        "updated_at": "2017-01-12T11:53:07.578+11:00"
      }
    }
  ]
}
```
`GET /api/hub_teams/search`

Search for any team on Adventist Hub using fuzzy search to compensate for misspellings such as letters around the wrong way. The 10 best matches will be returned.

Parameter | Description | Notes
--------- | ------- | -------
q<br> *string* | Any query string | Required
exclude_ids<br> *string* | A comma seperated list of the team ids to exclude from search e.g. 3,4,5 |


## Show Hub Team

```shell
curl https://hubapi.adventistchurch.com/api/hub_teams/2
-H "Authorization: Bearer team_token"
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
      "avatar_url": "https://res-1.cloudinary.com/image/team-avatar-6.jpg",
      "created_at": "2016-10-24T17:32:18.298+11:00",
      "updated_at": "2017-01-12T11:53:07.578+11:00"
    }
  }
}
```

`GET /api/hub_teams/{team-id}`

Read the current Hub team based on the users token.