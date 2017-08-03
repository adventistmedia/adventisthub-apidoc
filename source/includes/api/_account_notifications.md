# Account Notification

The users notifications.

## Fields

Field | Description | Notes
----- | ----------- | -----
name<br> *string* | Notification Name | Read-only
subscribed<br> *boolean* | Whether they are subscribed or not | Read-only
created_at<br> *datetime* | When the notification was created | Read-only
updated_at<br> *datetime* | When the notification was last updated | Read-only

## List Notifications
```shell
curl https://adhubapi.adventistchurch.com/api/account/notifications
-H "Authorization: Bearer contact_token"
-H "Accept: application/vnd.adhub.v1+json"
```
```json
{
  "data": [
    {
      "id": "5",
      "type": "notifications",
      "attributes": {
        "name": "Feature Announcements",
        "created_at": "2016-10-25T16:12:01.354+11:00",
        "updated_at": "2016-11-22T07:21:21.124+11:00",
        "subscribed": true
      }
    }
  ]
}
```

`GET /api/account/notifications`

An array of all notifications for an account.

## Subscribe

Subscribe to a notification

```shell
curl -X PATCH https://adhubapi.adventistchurch.com/api/account/notifications/5/subscribe
-H "Authorization: Bearer contact_token"
-H "Accept: application/vnd.adhub.v1+json"
```
```json
{
  "data": {
    "id": "5",
    "type": "notifications",
    "attributes": {
      "name": "Feature Announcements",
      "created_at": "2016-10-25T16:12:01.354+11:00",
      "updated_at": "2016-11-22T07:21:21.124+11:00",
      "subscribed": true
    }
  }
}
```

`PATCH /api/account/notifications/{notification-id}/subscribe`

## Unsubscribe

Unsubscribe from a notification

```shell
curl -X PATCH https://adhubapi.adventistchurch.com/api/account/notifications/5/unsubscribe
-H "Authorization: Bearer contact_token"
-H "Accept: application/vnd.adhub.v1+json"
```
```json
{
  "data": {
    "id": "5",
    "type": "notifications",
    "attributes": {
      "name": "Feature Announcements",
      "created_at": "2016-10-25T16:12:01.354+11:00",
      "updated_at": "2016-11-22T07:22:21.124+11:00",
      "subscribed": false
    }
  }
}
```

`PATCH /api/account/notifications/{notification-id}/unsubscribe`