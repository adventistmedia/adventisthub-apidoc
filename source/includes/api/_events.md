# Event

Represents an event.

## Fields

Field | Description | Notes
--------- | ------- | -------
name<br> *string* | Event name | Required
summary<br> *string* | Summary of the event
location<br> *string* | Where the event is happening
event_type<br>*enum* {bible_study, seminar} | The type of the event | Required
start_time<br>*datetime* | Start time | Required
end_time<br>*datetime* | End time
event_series_id<br>*integer* | ID of the Event Series the event belongs too
approach_id<br>*integer* | ID of the approach the event belongs too
brand_id<br>*integer* | ID of the brand the event belongs too
campaign_id<br>*integer* | ID of the campaign the event belongs too
category_id<br>*integer* | ID of the category the event belongs too | Required
created_at<br>*datetime* | When the event was created | Read-only
updated_at<br>*datetime* | When the event was last updated | Read-only
event_sessions_count<br>*integer* | The number of Event Sessions the event has | Read-only
shared<br>*boolean* | true if the event is viewable with other team members
## List Events
```shell
curl https://adhubapi.adventistchurch.com/api/contacts
-H "Authorization: Bearer team_token"
-H "Accept: application/vnd.adhub.v1+json"
```

```json

{
  "data": [
    {
      "id": "1",
      "type": "events",
      "attributes": {
        "event_type": "bible_study",
        "summary": "studying the bible",
        "start_time": "2017-01-23T09:42:48.244+11:00",
        "end_time": "2017-01-23T10:42:48.244+11:00",
        "category_id": null,
        "name": "Weekly Bible Study 1",
        "location": "Wahroonga, NSW",
        "event_series_id": null,
        "created_at": "2017-01-16T09:42:49.261+11:00",
        "updated_at": "2017-01-16T09:42:49.261+11:00",
        "campaign_id": null,
        "approach_id": null,
        "brand_id": null,
        "event_sessions_count": 1,
        "shared": true
      },
      "relationships": {
        "event_sessions": {
          "data": [
            {
              "id": "1",
              "type": "event_sessions"
            }
          ]
        }
      },
      "links": {
        "self": "/api/events/1"
      }
    }
  ]
}
```
`GET /api/events`

An array of event objects accessible to the user based on the tokens team.

## Show Event

```shell
curl https://adhubapi.adventistchurch.com/api/events/1
-H "Authorization: Bearer team_token"
-H "Accept: application/vnd.adhub.v1+json"
```
```json
{
  "data": {
    "id": "1",
    "type": "events",
    "attributes": {
      "event_type": "bible_study",
      "summary": "studying the bible",
      "start_time": "2017-01-23T09:42:48.244+11:00",
      "end_time": "2017-01-23T10:42:48.244+11:00",
      "category_id": null,
      "name": "Weekly Bible Study 1",
      "location": "Wahroonga, NSW",
      "event_series_id": null,
      "created_at": "2017-01-16T09:42:49.261+11:00",
      "updated_at": "2017-01-16T09:42:49.261+11:00",
      "campaign_id": null,
      "approach_id": null,
      "brand_id": null,
      "event_sessions_count": 1,
      "shared": true
    },
    "relationships": {
      "event_sessions": {
        "data": [
          {
            "id": "1",
            "type": "event_sessions"
          }
        ]
      }
    },
    "links": {
      "self": "/api/events/1"
    }
  }
}
```

`GET /api/events/{event-id}`

Read an event.

## Create Event
```shell
curl -X POST https://adhubapi.adventistchurch.com/api/events
-H "Authorization: Bearer team_token"
-H "Content-type: application/json"
-H "Accept: application/vnd.adhub.v1+json"
-d '{"event": {"event_type": "bible_study", "name": "Weekly Study", "start_time": "2017-01-16T09:00"}}'
```
```json
{
  "data": {
    "id": "2",
    "type": "events",
    "attributes": {
      "event_type": "bible_study",
      "summary": null,
      "start_time": "2017-01-16T09:00:00.000+11:00",
      "end_time": null,
      "category_id": null,
      "name": "Weekly Study",
      "location": null,
      "event_series_id": null,
      "created_at": "2017-01-16T09:42:49.261+11:00",
      "updated_at": "2017-01-16T09:42:49.261+11:00",
      "campaign_id": null,
      "approach_id": null,
      "brand_id": null,
      "event_sessions_count": 1,
      "shared": false
    },
    "relationships": {
      "event_sessions": {
        "data": [
          {
            "id": "2",
            "type": "event_sessions"
          }
        ]
      }
    },
    "links": {
      "self": "/api/events/2"
    }
  }
}
```

`POST /api/events`

## Update Event
```shell
curl -X PATCH https://adhubapi.adventistchurch.com/api/events/2
-H "Authorization: Bearer team_token"
-H "Content-type: application/json"
-H "Accept: application/vnd.adhub.v1+json"
-d '{"event": {"name": "Weekly Study Jan"}}'
```
```json
{
  "data": {
    "id": "2",
    "type": "events",
    "attributes": {
      "event_type": "bible_study",
      "summary": null,
      "start_time": "2017-01-16T09:00:00.000+11:00",
      "end_time": null,
      "category_id": null,
      "name": "Weekly Study Jan",
      "location": null,
      "event_series_id": null,
      "created_at": "2017-01-16T09:42:49.261+11:00",
      "updated_at": "2017-01-16T09:45:00.000+11:00",
      "campaign_id": null,
      "approach_id": null,
      "brand_id": null,
      "event_sessions_count": 1,
      "shared": false
    },
    "relationships": {
      "event_sessions": {
        "data": [
          {
            "id": "2",
            "type": "event_sessions"
          }
        ]
      }
    },
    "links": {
      "self": "/api/events/2"
    }
  }
}
```

`PATCH /api/events/{event-id}`

## Delete Event
```shell
curl -X DELETE https://adhubapi.adventistchurch.com/api/events/2
-H "Authorization: Bearer team_token"
-H "Accept: application/vnd.adhub.v1+json"
```
```json
{
  "data": {
    "id": "2",
    "type": "events",
    "attributes": {
      "event_type": "bible_study",
      "summary": null,
      "start_time": "2017-01-16T09:00:00.000+11:00",
      "end_time": null,
      "category_id": null,
      "name": "Weekly Study Jan",
      "location": null,
      "event_series_id": null,
      "created_at": "2017-01-16T09:42:49.261+11:00",
      "updated_at": "2017-01-16T09:45:00.000+11:00",
      "campaign_id": null,
      "approach_id": null,
      "brand_id": null,
      "event_sessions_count": 1,
      "shared": false
    },
    "relationships": {
      "event_sessions": {
        "data": [
          {
            "id": "2",
            "type": "event_sessions"
          }
        ]
      }
    },
    "links": {
      "self": "/api/events/2"
    }
  }
}
```

`DELETE /api/events/{event-id}`