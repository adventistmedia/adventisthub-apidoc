# Membership

Memberships to Hub teams.

It's important to know the users team role after they've signed in to avoid calling endpoints the user doesn't have access to or showing the UI components that are not applicable.

## Fields

Field | Description | Notes
----- | ----------- | -----
contact_id<br> *integer* | ID of the user the membership belongs too | Read-only
team_id<br> *integer* | ID of the team the membership belongs too | Read-only
role<br> *enum*{team_member, leader, owner} | Role within the team the user has been given | Read-only
created_at<br> *datetime* | When the membership was created | Read-only
updated_at<br> *datetime* | When the membership was last updated | Read-only

## List Memberships
```shell
curl https://hubapi.adventistchurch.com/api/memberships
-H "Authorization: Bearer team_token"
-H "Accept: application/vnd.adventisthub.v1+json"
```
```json
{
  "data": [
    {
      "id": "20",
      "type": "memberships",
      "attributes": {
        "contact_id": 5,
        "team_id": 3,
        "role": "team_member",
        "created_at": "2016-10-24T08:26:36.690+11:00",
        "updated_at": "2016-10-24T08:26:36.690+11:00"
      }
    }
  ]
}
```

`GET /api/memberships`

An array of all team memberships.

## Show Membership
```shell
curl https://hubapi.adventistchurch.com/api/memberships/20
-H "Authorization: Bearer team_token"
-H "Accept: application/vnd.adventisthub.v1+json"
```
```json
{
  "data": {
    "id": "20",
    "type": "memberships",
    "attributes": {
      "contact_id": 5,
      "team_id": 3,
      "role": "team_member",
      "created_at": "2016-10-24T08:26:36.690+11:00",
      "updated_at": "2016-10-24T08:26:36.690+11:00"
    }
  }
}
```

`GET /api/memberships/{membership-id}`

A team membership