# Calendar

Upcoming dates on the users calendars.

## Fields

A calendar is an array of calendar events objects. The objects themselves have a source_id and source_type which can be used to reference the original object.

Field | Description | Notes
----- | ----------- | -----
title<br> *string* | Title | Read-only
description<br> *string* | Description | Read-only
location<br> *string* | Where the calendar event is happening | Read-only
start_time<br>*datetime* | Start time | Read-only
end_time<br>*datetime* | End time | Read-only
source_id<br>*integer* | The source objects ID | Read-only
source_type<br>*string* | The source objects class name | Read-only
created_at<br>*datetime* | When the source object was created | Read-only
updated_at<br>*datetime* | When the source object was last updated | Read-only

## Calendar Listing
```shell
curl https://hubapi.adventistchurch.com/api/calendars
-H "Authorization: Bearer team_token"
-H "Accept: application/vnd.adventisthub.v1+json"
```
```json
{
  "data": [
    {
      "id": "contact_10",
      "type": "calendar_events",
      "attributes": {
        "title": "Contact Visit: Jasmine Fondu",
        "description": null,
        "location": "1232421 Hetton St, BELLBIRD NSW 2325, Australia",
        "start_time": "2016-10-26T09:00:00.000+00:00",
        "end_time": "2016-10-26T10:00:00.000+00:00",
        "source_id": 10,
        "source_type": "contact",
        "created_at": "2016-11-16T10:22:42.593+11:00",
        "updated_at": "2016-11-29T10:04:54.189+11:00"
      },
      "links": {
        "self":"/api/contacts/10"
      }
    }
  ]
}
```

`GET /api/calendars`

An array of calendar event objects.