# Account Phone Number

The users phone numbers

## Fields

Field | Description | Notes
----- | ----------- | -----
name<br> *enum* {mobile, home, work, fax} | Type of number | Required
country_code<br> *string* | Two letter uppercase country code | Required
local_number<br> *string* | Local phone number including area code and excluding country code digits | Required
full_number<br> *string* | Full phone number formatted to include country code digits | Read-only
created_at<br> *datetime* | When the phone number was created | Read-only
updated_at<br> *datetime* | When the phone number was last updated | Read-only

## List Phone Numbers
```shell
curl https://hubapi.adventistchurch.com/api/account/phone_numbers
-H "Authorization: Bearer contact_token"
-H "Accept: application/vnd.adventisthub.v1+json"
```
```json
{
  "data": [
    {
      "id": "4",
      "type": "phone_numbers",
      "attributes": {
        "name": "mobile",
        "country_code": "AU",
        "local_number": "0421000123",
        "full_number": "+61421000123",
        "created_at": "2017-01-04T18:09:45.584+11:00",
        "updated_at": "2017-01-04T18:09:45.590+11:00"
      }
    },
    {
      "id": "5",
      "type": "phone_numbers",
      "attributes": {
        "name": "home",
        "country_code": "AU",
        "local_number": "0298471234",
        "full_number": "+61298471234",
        "created_at": "2017-01-04T18:09:45.584+11:00",
        "updated_at": "2017-01-04T18:09:45.590+11:00"
      }
    }
  ]
}
```

`GET /api/account/phone_numbers`

An array of all phone numbers for an account.

## Show Phone Number
```shell
curl https://hubapi.adventistchurch.com/api/account/phone_numbers/5
-H "Authorization: Bearer contact_token"
-H "Accept: application/vnd.adventisthub.v1+json"
```
```json
{
  "data": {
    "id": "5",
    "type": "phone_numbers",
    "attributes": {
      "name": "home",
      "country_code": "AU",
      "local_number": "0298471234",
      "full_number": "+61298471234",
      "created_at": "2017-01-04T18:09:45.584+11:00",
      "updated_at": "2017-01-04T18:09:45.590+11:00"
    }
  }
}
```

`GET /api/account/phone_numbers/{phone-number-id}`

Show an account phone number.

## Create Phone Number

```shell
curl -X POST https://hubapi.adventistchurch.com/api/account/phone_numbers
-H "Authorization: Bearer contact_token"
-H "Content-type: application/json"
-H "Accept: application/vnd.adventisthub.v1+json"
-d '{"phone_number": {"country_code": "AU", "name": "work", "local_number": "0233331111"}}'
```
```json
{
  "data": {
    "id": "19",
    "type": "phone_numbers",
    "attributes": {
      "name": "work",
      "country_code": "AU",
      "local_number": "0233331111",
      "full_number": "+61233331111",
      "created_at": "2017-01-16T16:18:03.000+11:00",
      "updated_at": "2017-01-16T16:18:03.000+11:00"
    }
  }
}
```

`POST /api/account/phone_numbers`

## Update Phone Number

```shell
curl -X PATCH https://hubapi.adventistchurch.com/api/account/phone_numbers/19
-H "Authorization: Bearer contact_token"
-H "Content-type: application/json"
-H "Accept: application/vnd.adventisthub.v1+json"
-d '{"phone_number": {"local_number": "0233337777"}}'
```
```json
{
  "data": {
    "id": "19",
    "type": "phone_numbers",
    "attributes": {
      "name": "work",
      "country_code": "AU",
      "local_number": "0233337777",
      "full_number": "+61233337777",
      "created_at": "2017-01-16T16:18:03.000+11:00",
      "updated_at": "2017-01-16T16:20:00.692+11:00"
    }
  }
}
```

`PATCH /api/account/phone_numbers/{phone-number-id}`

## Delete Phone Number

```shell
curl -X DELETE https://hubapi.adventistchurch.com/api/account/phone_numbers/19
-H "Authorization: Bearer contact_token"
-H "Accept: application/vnd.adventisthub.v1+json"
```
```json
{
  "data": {
    "id": "19",
    "type": "phone_numbers",
    "attributes": {
      "name": "work",
      "country_code": "AU",
      "local_number": "0233337777",
      "full_number": "+61233337777",
      "created_at": "2017-01-16T16:18:03.000+11:00",
      "updated_at": "2017-01-16T16:20:00.692+11:00"
    }
  }
}
```

`DELETE /api/account/phone_numbers/{phone-number-id}`