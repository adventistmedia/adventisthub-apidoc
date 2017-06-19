# Contact Notifications

The contacts notifications.

## Fields

Field | Description | Notes
----- | ----------- | -----
name<br> *string* | Notification Name | Read-only
subscribed<br> *boolean* | Whether they are subscribed or not | Read-only
created_at<br> *datetime* | When the notification was created | Read-only
updated_at<br> *datetime* | When the notification was last updated | Read-only


## List Notifications
```shell
curl https://hubapi.adventistchurch.com/api/contacts/45/notifications
-H "Authorization: Bearer team_token"
-H "Accept: application/vnd.adventisthub.v1+json"
```
```json
{
  "data": [
    {
      "id": "2",
      "type": "notifications",
      "attributes": {
        "name": "Visit",
        "created_at": "2016-10-25T16:06:54.810+11:00",
        "updated_at": "2016-10-25T16:06:54.810+11:00",
        "subscribed": true
      }
    },
    {
      "id": "3",
      "type": "notifications",
      "attributes": {
        "name": "SMS Marketing",
        "created_at": "2016-10-25T16:10:34.643+11:00",
        "updated_at": "2016-11-07T08:34:14.844+11:00",
        "subscribed": false
      }
    },
    {
      "id": "1",
      "type": "notifications",
      "attributes": {
        "name": "Call",
        "created_at": "2016-10-25T16:04:38.427+11:00",
        "updated_at": "2016-11-22T07:46:32.047+11:00",
        "subscribed": true
      }
    }
  ]
}
```

`GET /api/contacts/{contact-id}/notifications`

An array of all notifications for a contact.

## Subscribe

```shell
curl -X PATCH https://hubapi.adventistchurch.com/api/contacts/45/notifications/5/subscribe
-H "Authorization: Bearer team_token"
-H "Accept: application/vnd.adventisthub.v1+json"
```
```json
{
  "data": {
    "id": "1",
    "type": "notifications",
    "attributes": {
      "name": "Call",
      "created_at": "2016-10-25T16:04:38.427+11:00",
      "updated_at": "2016-11-22T07:50:30.000+11:00",
      "subscribed": true
    }
  }
}
```

`PATCH /api/contacts/{contact-id}/notifications/{notification-id}/subscribe`

Subscribe to a notification

## Unsubscribe

```shell
curl -X PATCH https://hubapi.adventistchurch.com/api/contacts/45/notifications/5/unsubscribe
-H "Authorization: Bearer team_token"
-H "Accept: application/vnd.adventisthub.v1+json"
```
```json
{
  "data": {
    "id": "1",
    "type": "notifications",
    "attributes": {
      "name": "Call",
      "created_at": "2016-10-25T16:04:38.427+11:00",
      "updated_at": "2016-11-22T07:50:30.000+11:00",
      "subscribed": false
    }
  }
}
```
`PATCH /api/contacts/{contact-id}/notifications/{notification-id}/unsubscribe`

Unsubscribe from a notification