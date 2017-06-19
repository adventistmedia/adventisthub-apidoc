# Study

Represents a study.

By default the application has a global set of baptismal and baptismal supplementary studies. A user can additional add their own studies viewable only by them.

## Fields

Field | Description | Notes
--------- | ------- | -------
name<br>*string* | Event name | Required
contact_id<br> *integer* | ID of the contact the study belongs too | Read-only
study_type<br>*enum*{baptismal, baptismal_supplementary, user_study} |  Type of study. Studies created by contacts will be set to user_study | Read-only
created_at<br>*datetime* | When the study was created | Read-only
updated_at<br>*datetime* | When the study was last updated | Read-only

## List Studies
```shell
curl https://hubapi.adventistchurch.com/api/account/studies
-H "Authorization: Bearer contact_token"
-H "Accept: application/vnd.adventisthub.v1+json"
```

```json
{
  "data": [
    {
      "id": "33",
      "type": "studies",
      "attributes": {
        "name": "32. Revelation 17",
        "contact_id": null,
        "study_type": "baptismal",
        "created_at": "2017-01-04T14:47:04.448+11:00",
        "updated_at": "2017-01-04T14:47:04.448+11:00"
      }
    },
    {
      "id": "39",
      "type": "studies",
      "attributes": {
        "name": "06. Gifts of Spirit",
        "contact_id": null,
        "study_type": "baptismal_supplementary",
        "created_at": "2017-01-04T14:47:04.448+11:00",
        "updated_at": "2017-01-04T14:47:04.448+11:00"
      }
    }
  ]
}
```
`GET /api/account/studies`

An array of studies available to the user. Studies are combination of global and user created studies.


## Create Study
```shell
curl -X POST https://hubapi.adventistchurch.com/api/account/studies
-H "Authorization: Bearer contact_token"
-H "Content-type: application/json"
-H "Accept: application/vnd.adventisthub.v1+json"
-d '{"study": {"name": "Where did all the sheep go?"}}'
```
```json
{
  "data": {
    "id": "52",
    "type": "studies",
    "attributes": {
      "name": "Where did all the sheep go?",
      "contact_id": 5,
      "study_type": "user_study",
      "created_at": "2017-01-17T12:05:15.817+11:00",
      "updated_at": "2017-01-17T12:05:15.817+11:00"
    }
  }
}
```

`POST /api/account/studies`

## Update Study

```shell
curl -X PATCH https://hubapi.adventistchurch.com/api/account/studies/52
-H "Authorization: Bearer contact_token"
-H "Content-type: application/json"
-H "Accept: application/vnd.adventisthub.v1+json"
-d '{"study": {"name": "Finding the sheep"}}'
```
```json
{
  "data": {
    "id": "52",
    "type": "studies",
    "attributes": {
      "name": "Finding the sheep",
      "contact_id": 5,
      "study_type": "user_study",
      "created_at": "2017-01-17T12:05:15.817+11:00",
      "updated_at": "2017-01-17T12:09:44.464+11:00"
    }
  }
}
```

`PATCH /api/account/studies/{study-id}`

## Delete Study
```shell
curl -X DELETE https://hubapi.adventistchurch.com/api/account/studies/52
-H "Authorization: Bearer contact_token"
-H "Accept: application/vnd.adventisthub.v1+json"
```
```json
{
  "data": {
    "id": "52",
    "type": "studies",
    "attributes": {
      "name": "Finding the sheep",
      "contact_id": 5,
      "study_type": "user_study",
      "created_at": "2017-01-17T12:05:15.817+11:00",
      "updated_at": "2017-01-17T12:09:44.464+11:00"
    }
  }
}
```

`DELETE /api/account/studies/{study-id}`