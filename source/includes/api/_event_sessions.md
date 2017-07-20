# Event Session

An event session represents a single session at an event which needs to track attendees.

## Fields

Field | Description | Notes
--------- | ------- | -------
name<br> *string* | Name of Event | Required
start_time<br>*datetime* | Start time | Required
event_id<br>*integer* | ID of the event the event session belongs too | Read-only
created_at<br>*datetime* | When the event sessions was created | Read-only
updated_at<br>*datetime* | When the event sessions was last updated | Read-only

## List Event Sessions
```shell
curl https://adhubapi.adventistchurch.com/api/events/24/event_sessions
-H "Authorization: Bearer team_token"
-H "Accept: application/vnd.adventisthub.v1+json"
```

```json
{
  "data": [
    {
      "id": "13",
      "type": "event_sessions",
      "attributes": {
        "name": "Session 1",
        "start_time": "2017-01-12T15:30:00.356+11:00",
        "event_id": 24,
        "attendees_count": 3,
        "created_at": "2017-01-12T15:22:17.372+11:00",
        "updated_at": "2017-01-12T15:22:17.372+11:00"
      },
      "links": {
        "self": "/api/events/24/event_sessions/13"
      }
    }
  ]
}
```
`GET /api/events/{event-id}/event_sessions`

An array of event sessions for an event.

## Show Event Session

```shell
curl https://adhubapi.adventistchurch.com/api/events/24/event_sessions/13
-H "Authorization: Bearer team_token"
-H "Accept: application/vnd.adventisthub.v1+json"
```
```json
{
  "data": {
    "id": "13",
    "type": "event_sessions",
    "attributes": {
      "name": "Session 1",
      "start_time": "2017-01-12T15:30:00.356+11:00",
      "event_id": 24,
      "attendees_count": 3,
      "created_at": "2017-01-12T15:22:17.372+11:00",
      "updated_at": "2017-01-12T15:22:17.372+11:00"
    },
    "links": {
      "self": "/api/events/24/event_sessions/13"
    }
  }
}
```

`GET /api/events/{event-id}/event_sessions/{event-session-id}`

Read an event session.

## Create Event Session
```shell
curl -X POST https://adhubapi.adventistchurch.com/api/events/24/event_sessions
-H "Authorization: Bearer team_token"
-H "Content-type: application/json"
-H "Accept: application/vnd.adventisthub.v1+json"
-d '{"event_session": {"name": "Walking North", "start_time": "2017-01-05T18:30"}}'
```
```json
{
  "data": {
    "id": "15",
    "type": "event_sessions",
    "attributes": {
      "name": "Walking North",
      "start_time": "2017-01-05T18:30:00.000+11:00",
      "event_id": 24,
      "attendees_count": 0,
      "created_at": "2017-01-17T10:05:33.835+11:00",
      "updated_at": "2017-01-17T10:05:33.835+11:00"
    },
    "links": {
      "self": "/api/events/24/event_sessions/15"
    }
  }
}
```

`POST /api/events/{event-id}/event_sessions`

## Update Event Sessions

```shell
curl -X PATCH https://adhubapi.adventistchurch.com/api/events/24/event_sessions/15
-H "Authorization: Bearer team_token"
-H "Content-type: application/json"
-H "Accept: application/vnd.adventisthub.v1+json"
-d '{"event_session": {"name": "The Great Walk"}}'

```
```json
{
  "data": {
    "id": "15",
    "type": "event_sessions",
    "attributes": {
      "name": "The Great Walk",
      "start_time": "2017-01-05T18:30:00.000+11:00",
      "event_id": 24,
      "attendees_count": 0,
      "created_at": "2017-01-17T10:05:33.835+11:00",
      "updated_at": "2017-01-17T10:08:25.168+11:00"
    },
    "links": {
      "self": "/api/events/24/event_sessions/15"
    }
  }
}
```

`PATCH /api/events/{event-id}/event_sessions/{event-session-id}`

## Delete Event Session
```shell
curl -X DELETE https://adhubapi.adventistchurch.com/api/events/24/event_sessions/15
-H "Authorization: Bearer team_token"
-H "Accept: application/vnd.adventisthub.v1+json"
```
```json
{
  "data": {
    "id": "15",
    "type": "event_sessions",
    "attributes": {
      "name": "The Great Walk",
      "start_time": "2017-01-05T18:30:00.000+11:00",
      "event_id": 24,
      "attendees_count": 0,
      "created_at": "2017-01-17T10:05:33.835+11:00",
      "updated_at": "2017-01-17T10:08:25.168+11:00"
    },
    "links": {
      "self": "/api/events/24/event_sessions/15"
    }
  }
}
```

`DELETE /api/events/{event-id}/event_sessions/{event-session-id}`