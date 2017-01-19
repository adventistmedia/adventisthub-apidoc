# Account

The current token users account.

## Fields

Field | Description | Notes
----- | ----------- | -----
first_name<br> *string* | First name
last_name<br> *string* | Last name
name<br> *string* | First and last name combined
email<br> *string* | Email address
status<br> *enum* {pending, active, disabled}| Account status | Read-only
job<br> *enum* {member, assistant_pastor, bible_worker, chaplain, pastor} | Job within church organisation
dashboard_language<br> *string* | Preferred language code to see the dashboard in. By default this is en (English)
available<br> *boolean* | the availability of the user to accept requests and more
unavailable_until<br> *date* | if available is false, a date may be set to indicate when the user will become available again
created_at<br> *datetime* | When the account was created | Read-only
updated_at<br> *datetime* | When account or a relationship was last updated | Read-only
time_zone<br> *string* | Time zone
country_code<br> *string* | Two letter uppercase country code for users residence
country<br> *string* | Official country name for users residence
hub_teams_count<br> *integer* | Number of Hub Teams the user is a member of | Read-only
lat<br> *float* | Home address latitude | Read-only
lng<br> *float* | Home address longitude | Read-only
visit_frequency<br> *integer* | the default number of weeks between visiting a contact
mentorships_count<br> *integer* | If the user is a mentor, the number of mentorships they have | Read-only
calendar_url<br> *string* | The unique private iCal URL for the users calendar to subscribe to | Read-only

## Show Account
```shell
curl https://hubapi.adventistchurch.com/api/account
-H "Authorization: Bearer token"
-H "Accept: application/vnd.adventisthub.v1+json"
```
```json
{
  "data": {
    "id": "5",
    "type": "users",
    "attributes": {
      "first_name": "Dan",
      "last_name": "Ratherbe",
      "name": "Dan Ratherbe",
      "email": "dan@email.com",
      "status": "active",
      "job": "bible_worker",
      "dashboard_language": "en",
      "available": true,
      "unavailable_until": null,
      "created_at": "2016-11-02T10:13:58.246+11:00",
      "updated_at": "2017-01-12T09:32:15.632+11:00",
      "time_zone": "Sydney",
      "country_code": "AU",
      "country": "Australia",
      "hub_teams_count": 2,
      "lat": -33.000000,
      "lng": 150.000000,
      "visit_frequency": 1,
      "mentorships_count": 1,
      "calendar_url": "webcal://hub.adventistchurch.com/calendars/user/5/gQ4ttSQcN94mv9xeDbiddzXg/feed.ics"
    },
    "links": {
      "self": "/api/account"
    }
  }
}
```

`GET /api/account`

Show the users account.

## Update Account

```shell
curl -X PATCH https://hubapi.adventistchurch.com/api/account
-H "Authorization: Bearer token"
-H "Content-type: application/json"
-H "Accept: application/vnd.adventisthub.v1+json"
-d '{"user": {"first_name": "Wallaby"}}'
```
```json
{
  "data": {
    "id": "5",
    "type": "users",
    "attributes": {
      "first_name": "Wallaby",
      "last_name": "Ratherbe",
      "name": "Wallaby Ratherbe",
      "email": "dan@email.com",
      "status": "active",
      "job": "bible_worker",
      "dashboard_language": "en",
      "available": true,
      "unavailable_until": null,
      "created_at": "2016-11-02T10:13:58.246+11:00",
      "updated_at": "2017-01-12T09:32:15.632+11:00",
      "time_zone": "Sydney",
      "country_code": "AU",
      "country": "Australia",
      "hub_teams_count": 2,
      "lat": -33.000000,
      "lng": 150.000000,
      "visit_frequency": 1,
      "mentorships_count": 1,
      "calendar_url": "webcal://hub.adventistchurch.com/calendars/user/5/gQ4ttSQcN94mv9xeDbiddzXg/feed.ics"
    },
    "links": {
      "self": "/api/account"
    }
  }
}
```

`PATCH /api/account`

Update the users account.