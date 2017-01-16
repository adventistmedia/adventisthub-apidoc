# Alert

An alert/notification message for the user.

## Fields

Field | Description | Notes
--------- | ------- | -------
id<br> *integer* | Unique ID | Read-only
title<br> *string* | Title | Read-only
summary<br> *string* | Alert message | Read-only
url<br> *string* | External URL link associated with the alert message | Read-only
read<br>*boolean* | Whether the alert has been read previously by the user | Read-only
expires_at<br>*datetime* | The future time at which alert is no longer valid and will be deleted automatically | Read-only
decision<br>*enum* {undecided, accepted, declined}| The decision (if one was required) the user made | Read-only
callback<br>*boolean* | Whether a callback is required | Read-only
accept_callback<br>*boolean* | Whether an accept callback can be made | Read-only
decline_callback<br>*boolean* | Whether a decline callback can be made | Read-only
created_at<br>*datetime* | When the alert was created | Read-only
updated_at<br>*datetime* | When the alert was last updated | Read-only

## List Alerts
```shell
curl http://api.adventisthub.com/api/account/alerts
-H "Authorization: Bearer token"
-H "Accept: application/vnd.adventisthub.v1"
```

```json
{
  "data": [
    {
      "id": "32",
      "type": "alerts",
      "attributes": {
        "title": "2016 Bible worker Survey",
        "summary": "We encourage all bible workers to complete this survey to help us understand your needs.",
        "url": "http://www.survey.com/1234",
        "read": true,
        "expires_at": null,
        "decision": "undecided",
        "callback": false,
        "accept_callback": false,
        "decline_callback": false,
        "created_at": "2016-11-22T09:15:40.236+11:00",
        "updated_at": "2016-11-22T12:20:53.619+11:00"
      }
    },
    {
      "id": "31",
      "type": "alerts",
      "attributes": {
        "title": "Contact transfer request",
        "summary": "Dan Ratherbe would like to transfer their contact Jasmine Fondu to you",
        "url": null,
        "read": false,
        "expires_at": null,
        "decision": "undecided",
        "callback": true,
        "accept_callback": true,
        "decline_callback": true,
        "created_at": "2016-11-22T09:05:34.421+11:00",
        "updated_at": "2016-11-22T09:06:41.240+11:00"
      }
    }
  ]
}
```
`GET /api/account/alerts`

An array of alert objects.

## Show Alert

```shell
curl http://api.adventisthub.com/api/account/alerts/48
-H "Authorization: Bearer token"
-H "Accept: application/vnd.adventisthub.v1"
```
```json
{
  "data": {
    "id": "48",
    "type": "alerts",
    "attributes": {
      "title": "New contact assigned",
      "summary": "NNSW has assigned you the contact Steven Davies",
      "url": null,
      "read": false,
      "expires_at": null,
      "decision": "undecided",
      "callback": false,
      "accept_callback": false,
      "decline_callback": false,
      "created_at": "2016-11-29T15:33:07.224+11:00",
      "updated_at": "2016-11-29T15:33:07.224+11:00"
    }
  }
}
```

`GET /api/account/alerts/{alert-id}`

Show an alert.

## Accept Alert
```shell
curl -X PATCH http://api.adventisthub.com/api/account/alerts/31/accept
-H "Authorization: Bearer token"
-H "Accept: application/vnd.adventisthub.v1"
```
```json
{
  "id": "31",
  "type": "alerts",
  "attributes": {
    "title": "Contact transfer request",
    "summary": "Dan Ratherbe would like to transfer their contact Jasmine Fondu to you",
    "url": null,
    "read": false,
    "expires_at": null,
    "decision": "accepted",
    "callback": true,
    "accept_callback": true,
    "decline_callback": true,
    "created_at": "2016-11-22T09:05:34.421+11:00",
    "updated_at": "2016-11-22T09:06:41.240+11:00"
  }
}
```

`PATCH /api/account/alerts/{alert-id}/accept`

Accept an alert that has an accept callback.

## Decline Alert
```shell
curl -X PATCH http://api.adventisthub.com/api/account/alerts/31/decline
-H "Authorization: Bearer token"
-H "Accept: application/vnd.adventisthub.v1"
```
```json
{
  "id": "31",
  "type": "alerts",
  "attributes": {
    "title": "Contact transfer request",
    "summary": "Dan Ratherbe would like to transfer their contact Jasmine Fondu to you",
    "url": null,
    "read": false,
    "expires_at": null,
    "decision": "declined",
    "callback": true,
    "accept_callback": true,
    "decline_callback": true,
    "created_at": "2016-11-22T09:05:34.421+11:00",
    "updated_at": "2016-11-22T09:06:41.240+11:00"
  }
}
```

`PATCH /api/account/alerts/{alert-id}/decline`

Accept an alert that has an decline callback.

## Delete Alert
```shell
curl -X DELETE http://api.adventisthub.com/api/account/alerts/48
-H "Authorization: Bearer token"
-H "Accept: application/vnd.adventisthub.v1"
```
```json
{
  "data": {
    "id": "48",
    "type": "alerts",
    "attributes": {
      "title": "New contact assigned",
      "summary": "NNSW has assigned you the contact Steven Davies",
      "url": null,
      "read": false,
      "expires_at": null,
      "decision": "undecided",
      "callback": false,
      "accept_callback": false,
      "decline_callback": false,
      "created_at": "2016-11-29T15:33:07.224+11:00",
      "updated_at": "2016-11-29T15:33:07.224+11:00"
    }
  }
}
```

`DELETE /api/account/alerts/{alert-id}`