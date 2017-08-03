# Contact Notes

A user can create notes for a contact they are assigned to. They notes are private and only viewable by the user who created them.

## Fields


Field | Description | Notes
----- | ----------- | -----
description<br> *text* | Note text | Required
contact_id<br> *integer* | Contact the note belongs to | Read-only
author_id<br> *integer* | User who created note | Read-only
team_id<br> *integer* | Team the note was created in | Read-only
private_note<br> *boolean* | Whether note is private. Default true | Read-only
created_at<br> *datetime* | When the note was created | Read-only
updated_at<br> *datetime* | When the note was last updated | Read-only

## List Notes
```shell
curl https://adhubapi.adventistchurch.com/api/contacts/11/notes
-H "Authorization: Bearer team_token"
-H "Accept: application/vnd.adhub.v1+json"
```
```json
{
  "data": [
    {
      "data": {
        "id": "34",
        "type": "notes",
        "attributes": {
          "contact_id": 11,
          "team_id": 2,
          "author_id": 1,
          "description": "noted",
          "private_note": true,
          "created_at": "2017-01-16T17:22:48.363+11:00",
          "updated_at": "2017-01-16T17:22:48.363+11:00"
        }
      }
    }
  ]
}
```

`GET /api/contact/{contact-id}/notes`

An array of a notes created by the user for the contact.

## Show Note
```shell
curl https://adhubapi.adventistchurch.com/api/contacts/11/notes/34
-H "Authorization: Bearer team_token"
-H "Accept: application/vnd.adhub.v1+json"
```
```json
{
  "data": {
    "id": "34",
    "type": "notes",
    "attributes": {
      "contact_id": 11,
      "team_id": 2,
      "author_id": 1,
      "description": "noted",
      "private_note": true,
      "created_at": "2017-01-16T17:22:48.363+11:00",
      "updated_at": "2017-01-16T17:22:48.363+11:00"
    }
  }
}
```

`GET /api/contacts/{contact-id}/notes/{note-id}`

Show a contacts note.

## Create Note

```shell
curl -X POST https://adhubapi.adventistchurch.com/api/contacts/11/notes
-H "Authorization: Bearer team_token"
-H "Content-type: application/json"
-H "Accept: application/vnd.adhub.v1+json"
-d '{"note": {"description": "noted thanks"}}'
```
```json
{
  "data": {
    "id": "35",
    "type": "notes",
    "attributes": {
      "contact_id": "11",
      "team_id": "2",
      "author_id": "1",
      "description": "noted thanks",
      "private_note": true,
      "created_at": "2017-01-16T17:22:48.363+11:00",
      "updated_at": "2017-01-16T17:22:48.363+11:00"
    }
  }
}
```

`POST /api/contact/{contact-id}/notes`

## Update Note

```shell
curl -X PATCH https://adhubapi.adventistchurch.com/api/contacts/11/notes/35
-H "Authorization: Bearer team_token"
-H "Content-type: application/json"
-H "Accept: application/vnd.adhub.v1+json"
-d '{"note": {"description": "noted"}}'
```
```json
{
  "data": {
    "id": "35",
    "type": "notes",
    "attributes": {
      "contact_id": "11",
      "team_id": "2",
      "author_id": "1",
      "description": "noted",
      "private_note": true,
      "created_at": "2017-01-16T17:22:48.363+11:00",
      "updated_at": "2017-01-16T17:22:48.363+11:00"
    }
  }
}
```

`PATCH /api/contacts/{contact-id}/notes/{note-id}`

## Delete Note

```shell
curl -X DELETE https://adhubapi.adventistchurch.com/api/contact/11/notes/35
-H "Authorization: Bearer team_token"
-H "Accept: application/vnd.adhub.v1+json"
```
```json
{
  "data": {
    "id": "35",
    "type": "notes",
    "attributes": {
      "contact_id": "11",
      "team_id": "2",
      "author_id": "1",
      "description": "noted",
      "private_note": true,
      "created_at": "2017-01-16T17:22:48.363+11:00",
      "updated_at": "2017-01-16T17:22:48.363+11:00"
    }
  }
}
```

`DELETE /api/contact/{contact-id}/notes/{note-id}`