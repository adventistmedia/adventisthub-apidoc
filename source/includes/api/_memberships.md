# Membership

Memberships to the users teams.

It's important to know the users team role after they've signed in to avoid calling endpoints the user doesn't have access too or showing the UI components that are not applicable.

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
curl https://adhubapi.adventistchurch.com/api/acccount/memberships
-H "Authorization: Bearer contact_token"
-H "Accept: application/vnd.adhub.v1+json"
```
```json
{
  "data": [
    {
      "id": "20",
      "type": "memberships",
      "attributes": {
        "contact_id": "5",
        "team_id": "3",
        "role": "team_member",
        "created_at": "2016-10-24T08:26:36.690+11:00",
        "updated_at": "2016-10-24T08:26:36.690+11:00"
      }
    }
  ]
}
```

`GET /api/account/memberships`

An array of all team memberships.

## Show Membership
```shell
curl https://adhubapi.adventistchurch.com/api/account/memberships/20
-H "Authorization: Bearer contact_token"
-H "Accept: application/vnd.adhub.v1+json"
```
```json
{
  "data": {
    "id": "20",
    "type": "memberships",
    "attributes": {
      "contact_id": "5",
      "team_id": "3",
      "role": "team_member",
      "created_at": "2016-10-24T08:26:36.690+11:00",
      "updated_at": "2016-10-24T08:26:36.690+11:00"
    }
  }
}
```

`GET /api/account/memberships/{membership-id}`

A team membership