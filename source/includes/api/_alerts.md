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
created_at<br>*datetime* | When the alert was created | Read-only
updated_at<br>*datetime* | When the alert was last updated | Read-only

## List Alerts
```shell
curl https://hubapi.adventistchurch.com/api/account/alerts
-H "Authorization: Bearer contact_token"
-H "Accept: application/vnd.adventisthub.v1+json"
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
        "created_at": "2016-11-22T09:15:40.236+11:00",
        "updated_at": "2016-11-22T12:20:53.619+11:00"
      }
    },
    {
      "id": "31",
      "type": "alerts",
      "attributes": {
        "title": "Contact transfer request",
        "summary": "Dan Underwood would like to transfer their contact Jasmine Fondu to you",
        "url": "https://hub.adventistchurch.com/assignment_requests?tid=4",
        "read": false,
        "expires_at": null,
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
curl https://hubapi.adventistchurch.com/api/account/alerts/48
-H "Authorization: Bearer contact_token"
-H "Accept: application/vnd.adventisthub.v1+json"
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
curl -X PATCH https://hubapi.adventistchurch.com/api/account/alerts/31/accept
-H "Authorization: Bearer contact_token"
-H "Accept: application/vnd.adventisthub.v1+json"
```
```json
{
  "id": "31",
  "type": "alerts",
  "attributes": {
    "title": "Contact transfer request",
    "summary": "Dan Underwood would like to transfer their contact Jasmine Fondu to you",
    "url": null,
    "read": false,
    "expires_at": null,
    "created_at": "2016-11-22T09:05:34.421+11:00",
    "updated_at": "2016-11-22T09:06:41.240+11:00"
  }
}
```

`PATCH /api/account/alerts/{alert-id}/accept`

Accept an alert that has an accept callback.

## Decline Alert
```shell
curl -X PATCH https://hubapi.adventistchurch.com/api/account/alerts/31/decline
-H "Authorization: Bearer contact_token"
-H "Accept: application/vnd.adventisthub.v1+json"
```
```json
{
  "id": "31",
  "type": "alerts",
  "attributes": {
    "title": "Contact transfer request",
    "summary": "Dan Underwood would like to transfer their contact Jasmine Fondu to you",
    "url": null,
    "read": false,
    "expires_at": null,
    "created_at": "2016-11-22T09:05:34.421+11:00",
    "updated_at": "2016-11-22T09:06:41.240+11:00"
  }
}
```

`PATCH /api/account/alerts/{alert-id}/decline`

Accept an alert that has an decline callback.

## Delete Alert
```shell
curl -X DELETE https://hubapi.adventistchurch.com/api/account/alerts/48
-H "Authorization: Bearer contact_token"
-H "Accept: application/vnd.adventisthub.v1+json"
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
      "created_at": "2016-11-29T15:33:07.224+11:00",
      "updated_at": "2016-11-29T15:33:07.224+11:00"
    }
  }
}
```

`DELETE /api/account/alerts/{alert-id}`