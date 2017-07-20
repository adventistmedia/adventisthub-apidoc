# Partner

The users partner. A partner can only be set by team managers.

A partner if set, is alerted when the user has not followed up a contact after a set period of time.

## Fields

Field | Description | Notes
----- | ----------- | -----
name<br> *string* | Partners name | Required
email<br> *boolean* | Partners email | Required
created_at<br> *datetime* | When the partner was created | Read-only
updated_at<br> *datetime* | When the partner was last updated | Read-only

## Show Partner

```shell
curl https://adhubapi.adventistchurch.com/api/account/partner
-H "Authorization: Bearer contact_token"
-H "Accept: application/vnd.adventisthub.v1+json"
```
```json
{
  "data": {
    "id": "7",
    "type": "partners",
    "attributes": {
      "name": "Sam Beagul",
      "email": "sam@email.com",
      "created_at": "2017-01-17T11:27:14.335+11:00",
      "updated_at": "2017-01-17T11:28:26.207+11:00"
    }
  }
}
```

> Response if partner does not already exist:

```json
{
  "errors": [
    {
      "source": {
        "pointer": "/data/attributes/id"
      },
      "detail": "ID does not exist"
    }
  ]
}
```

`GET /api/account/partner`

Read the current users partner

## Create Partner
```shell
curl -X POST https://adhubapi.adventistchurch.com/api/account/partner
-H "Authorization: Bearer contact_token"
-H "Content-type: application/json"
-H "Accept: application/vnd.adventisthub.v1+json"
-d '{"partner": {"name": "Sam Beagul", "email": "sam@email.com"}}'
```
```json
{
  "data": {
    "id": "7",
    "type": "partners",
    "attributes": {
      "name": "Sam Beagul",
      "email": "sam@email.com",
      "created_at": "2017-01-17T11:27:14.335+11:00",
      "updated_at": "2017-01-17T11:27:14.335+11:00"
    }
  }
}
```

`POST /api/account/partner`

## Update Partner

```shell
curl -X PATCH https://adhubapi.adventistchurch.com/api/account/partner
-H "Authorization: Bearer contact_token"
-H "Content-type: application/json"
-H "Accept: application/vnd.adventisthub.v1+json"
-d '{"partner": {"name": "John Backster"}}'
```
```json
{
  "data": {
    "id": "7",
    "type": "partners",
    "attributes": {
      "name": "John Backster",
      "email": "sam@email.com",
      "created_at": "2017-01-17T11:27:14.335+11:00",
      "updated_at": "2017-01-17T11:28:26.207+11:00"
    }
  }
}
```

`PATCH /api/account/partner`

## Delete Partner
```shell
curl -X DELETE https://adhubapi.adventistchurch.com/api/account/partner
-H "Authorization: Bearer contact_token"
-H "Accept: application/vnd.adventisthub.v1+json"
```
```json
{
  "data": {
    "id": "7",
    "type": "partners",
    "attributes": {
      "name": "John Backster",
      "email": "sam@email.com",
      "created_at": "2017-01-17T11:27:14.335+11:00",
      "updated_at": "2017-01-17T11:28:26.207+11:00"
    }
  }
}
```

`DELETE /api/account/partner`