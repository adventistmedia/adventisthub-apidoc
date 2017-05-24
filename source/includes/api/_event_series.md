# Event Series

An event series/re-occurring event template for creating new events.

## Fields

Field | Description | Notes
--------- | ------- | -------
name<br> *string* | Name of Event | Required
summary<br> *string* | Summary of the event
location<br> *string* | Where the event is happening
event_type<br>*enum* {bible_study, seminar} | The type of the event | Required
team_id<br>*integer* | ID of the Hub or HQ team the event belongs too | Read-only
contact_id<br>*integer* | ID of the contact who owns the event | Read-only
category_id<br>*integer* | ID of the category the event belongs too | Required
events_count<br>*integer* | Number of events associated with the event series | Read-only
approach_id<br>*integer* | ID of the approach the event belongs too
brand_id<br>*integer* | ID of the brand the event belongs too
campaign_id<br>*integer* | ID of the campaign the event belongs too
status<br>*enum* {published, archived} | Status. Defaults to published
shared<br>*boolean* | Whether the event series should be viewable with other members of the same team. Defaults to false.
created_at<br>*datetime* | When the event series was created | Read-only
updated_at<br>*datetime* | When the event series was last updated | Read-only

## List Event Series
```shell
curl https://hubapi.adventistchurch.com/api/event_series
-H "Authorization: Bearer token"
-H "Accept: application/vnd.adventisthub.v1+json"
```

```json
{
  "data": [
    {
      "id": "5",
      "type": "event_series",
      "attributes": {
        "name": "Sydney Insights",
        "summary": "Insights into the world of underground trafficking",
        "location": "Locations throughout Sydney",
        "event_type": "seminar",
        "team_id": 1,
        "contact_id": 9,
        "category_id": 10,
        "events_count": 0,
        "campaign_id": null,
        "brand_id": null,
        "approach_id": null,
        "status": "published",
        "shared": true,
        "created_at": "2016-11-23T15:00:32.744+11:00",
        "updated_at": "2016-12-01T09:01:47.016+11:00"
      },
      "links": {
        "self": "/api/event_series/5"
      }
    },
    {
      "id": "3",
      "type": "event_series",
      "attributes": {
        "name": "Westmead Bible Study Group",
        "summary": "",
        "location": null,
        "event_type": "bible_study",
        "team_id": 6,
        "contact_id": 5,
        "category_id": 4,
        "events_count": 4,
        "campaign_id": null,
        "brand_id": null,
        "approach_id": null,
        "status": "published",
        "shared": false,
        "created_at": "2016-11-17T08:04:44.076+11:00",
        "updated_at": "2016-11-28T12:42:02.283+11:00"
      },
      "links": {
        "self": "/api/event_series/3"
      }
    }
  ]
}
```
`GET /api/event_series`

An array of event series accessible to the user based on the tokens team.

## Show Event Series

```shell
curl https://hubapi.adventistchurch.com/api/event_series/3
-H "Authorization: Bearer token"
-H "Accept: application/vnd.adventisthub.v1+json"
```
```json
{
  "data": {
    "id": "3",
    "type": "event_series",
    "attributes": {
      "name": "Westmead Bible Study Group",
      "summary": "",
      "location": null,
      "event_type": "bible_study",
      "team_id": 6,
      "contact_id": 5,
      "category_id": 4,
      "events_count": 4,
      "campaign_id": null,
      "brand_id": null,
      "approach_id": null,
      "status": "published",
      "shared": false,
      "created_at": "2016-11-17T08:04:44.076+11:00",
      "updated_at": "2016-11-28T12:42:02.283+11:00"
    },
    "links": {
      "self": "/api/event_series/3"
    }
  }
}
```

`GET /api/event_series/{event-series-id}`

Read an event series.

## Create Event Series
```shell
curl -X POST https://hubapi.adventistchurch.com/api/event_series
-H "Authorization: Bearer token"
-H "Content-type: application/json"
-H "Accept: application/vnd.adventisthub.v1+json"
-d '{"event_series": {"name": "Youth Bible Study", "event_type": "bible_study", "category_id":20, "summary": "Weekly Wednesday Study"}}'
```
```json
{
  "data": {
    "id": "11",
    "type": "event_series",
    "attributes": {
      "name": "Youth Bible Study",
      "summary": "Weekly Wednesday Study",
      "location": null,
      "event_type": "bible_study",
      "team_id": 6,
      "contact_id": 5,
      "category_id": 20,
      "events_count": 0,
      "campaign_id": null,
      "brand_id": null,
      "approach_id": null,
      "status": "published",
      "shared": false,
      "created_at": "2017-01-17T09:31:25.000+11:00",
      "updated_at": "2017-01-17T09:31:25.000+11:00"
    },
    "links": {
      "self": "/api/event_series/11"
    }
  }
}
```

`POST /api/event_series`

## Update Event Series
```shell
curl -X PATCH https://hubapi.adventistchurch.com/api/event_series/11
-H "Authorization: Bearer token"
-H "Content-type: application/json"
-H "Accept: application/vnd.adventisthub.v1+json"
-d '{"event_series": {"shared": true}}'
```
```json
{
  "data": {
    "id": "11",
    "type": "event_series",
    "attributes": {
      "name": "Youth Bible Study",
      "summary": "Weekly Wednesday Study",
      "location": null,
      "event_type": "bible_study",
      "team_id": 6,
      "contact_id": 5,
      "category_id": 20,
      "events_count": 0,
      "campaign_id": null,
      "brand_id": null,
      "approach_id": null,
      "status": "published",
      "shared": true,
      "created_at": "2017-01-17T09:31:25.000+11:00",
      "updated_at": "2017-01-17T09:36:02.419+11:00"
    },
    "links": {
      "self": "/api/event_series/11"
    }
  }
}
```

`PATCH /api/event_series/{event-series-id}`

## Delete Event Series
```shell
curl -X DELETE https://hubapi.adventistchurch.com/api/event_series/11
-H "Authorization: Bearer token"
-H "Accept: application/vnd.adventisthub.v1+json"
```
```json
{
  "data": {
    "id": "11",
    "type": "event_series",
    "attributes": {
      "name": "Youth Bible Study",
      "summary": "Weekly Wednesday Study",
      "location": null,
      "event_type": "bible_study",
      "team_id": 6,
      "contact_id": 5,
      "category_id": 20,
      "events_count": 0,
      "campaign_id": null,
      "brand_id": null,
      "approach_id": null,
      "status": "published",
      "shared": true,
      "created_at": "2017-01-17T09:31:25.000+11:00",
      "updated_at": "2017-01-17T09:36:02.419+11:00"
    },
    "links": {
      "self": "/api/event_series/11"
    }
  }
}
```

`DELETE /api/event_series/{event-series-id}`