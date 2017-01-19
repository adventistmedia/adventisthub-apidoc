# Attendee

An attendee is a contact who has attended an event session.

## Fields

Field | Description | Notes
----- | ----------- | -----
contact_id<br> *string* | Name of attendee | Required
event_id<br> *integer* | ID of the event the attendee belongs to | Required
event_session_id<br> *integer* | ID of the event session the attendee belongs to | Required
created_at<br> *datetime* | When the attendee was created | Read-only
updated_at<br> *datetime* | When the attendee was last updated | Read-only

## List Attendees
```shell
curl https://api.adventisthub.com/api/event_sessions/13/attendees
-H "Authorization: Bearer token"
-H "Accept: application/vnd.adventisthub.v1+json"
```
```json
{
  "data": [
    {
      "id": "60",
      "type": "attendees",
      "attributes": {
        "contact_id": 12,
        "event_id": 24,
        "event_session_id": 13,
        "created_at": "2017-01-12T16:08:27.659+11:00",
        "updated_at": "2017-01-12T16:08:27.659+11:00"
      }
    },
    {
      "id": "61",
      "type": "attendees",
      "attributes": {
        "contact_id": 17,
        "event_id": 24,
        "event_session_id": 13,
        "created_at": "2017-01-12T16:08:29.528+11:00",
        "updated_at": "2017-01-12T16:08:29.528+11:00"
      }
    }
  ]
}
```

`GET /api/event_sessions/{event-session-id}/attendees`

An array of all attendees for an event session.

## Create Attendee
```shell
curl -X POST https://api.adventisthub.com/api/event_sessions/13/attendees
-H "Authorization: Bearer token"
-H "Content-type: application/json"
-H "Accept: application/vnd.adventisthub.v1+json"
-d '{"attendee": {"contact_id": 2}}'
```
```json
{
  "data": {
    "id": "90",
    "type": "attendees",
    "attributes": {
      "contact_id": 2,
      "event_id": 24,
      "event_session_id": 13,
      "created_at": "2017-01-12T16:08:27.659+11:00",
      "updated_at": "2017-01-12T16:08:27.659+11:00"
    }
  }
}
```

`POST /api/event_sessions/{event-session-id}/attendees`

Add a new attendee to the event session.

## Delete Attendee
```shell
curl -X DELETE https://api.adventisthub.com/api/event_sessions/13/attendees/90
-H "Authorization: Bearer token"
-H "Accept: application/vnd.adventisthub.v1+json"
```
```json
{
  "data": {
    "id": "90",
    "type": "attendees",
    "attributes": {
      "contact_id": 2,
      "event_id": 24,
      "event_session_id": 13,
      "created_at": "2017-01-12T16:08:27.659+11:00",
      "updated_at": "2017-01-12T16:08:27.659+11:00"
    }
  }
}
```

`DELETE /api/event_sessions/{event-session-id}/attendees/{attendee-id}`

Delete an attendee from the event session.