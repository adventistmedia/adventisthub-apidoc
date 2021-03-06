# Account

The current token users account.

## Fields

Field | Description | Notes
----- | ----------- | -----
first_name<br> *string* | First name
last_name<br> *string* | Last name
name<br> *string* | First and last name combined
email<br> *string* | Email address
status<br> *enum* {non_member, member, deceased}| Membership status | Read-only
available<br> *boolean* | the availability of the user to accept requests and more
unavailable_until<br> *date* | if available is false, a date may be set to indicate when the user will become available again
created_at<br> *datetime* | When the account was created | Read-only
updated_at<br> *datetime* | When account or a relationship was last updated | Read-only
time_zone<br> *string* | Time zone
country_code<br> *string* | Two letter uppercase country code for users residence
country<br> *string* | Official country name for users residence
memberships_count<br> *integer* | Number of Teams the user has membership too | Read-only
lat<br> *float* | Home address latitude | Read-only
lng<br> *float* | Home address longitude | Read-only
avatar_url<br>*string* | Avatar image URL for account | Read-only
calendar_url<br> *string* | The unique private iCal URL for the users calendar to subscribe to | Read-only

## Show Account
```shell
curl https://adhubapi.adventistchurch.com/api/account
-H "Authorization: Bearer contact_token"
-H "Accept: application/vnd.adhub.v1+json"
```
```json
{
  "data": {
    "id": "1",
    "type": "contacts",
    "attributes": {
      "first_name": "Dan",
      "last_name": "Underwood",
      "name": "Dan Underwood",
      "email": "danunderwood@email.com",
      "status": "member",
      "available": true,
      "unavailable_until": null,
      "created_at": "2017-05-22T16:57:46.956+10:00",
      "updated_at": "2017-05-24T10:39:50.119+10:00",
      "time_zone": "Sydney",
      "country_code": "AU",
      "country": "Australia",
      "memberships_count": 2,
      "lat": null,
      "lng": null,
      "avatar_url": "https://res-1.cloudinary.com/image/avatar-1.jpg",
      "calendar_url": "webcal://hub.adventistchurch.com/contacts/1/calendars/kaQaKqcMHX63ScxrA9gJhk91/feed.ics"
    },
    "links": {
      "self": "/api/account"
    }
  }
}
```

`GET /api/account`

Show the users account.

## Update Account

```shell
curl -X PATCH https://adhubapi.adventistchurch.com/api/account
-H "Authorization: Bearer contact_token"
-H "Content-type: application/json"
-H "Accept: application/vnd.adhub.v1+json"
-d '{"contact": {"first_name": "Wallaby"}}'
```
```json
{
  "data": {
    "id": "1",
    "type": "contacts",
    "attributes": {
      "first_name": "Wallaby",
      "last_name": "Underwood",
      "name": "Wallaby Underwood",
      "email": "danunderwood@email.com",
      "status": "member",
      "available": true,
      "unavailable_until": null,
      "created_at": "2017-05-22T16:57:46.956+10:00",
      "updated_at": "2017-05-24T10:48:08.220+10:00",
      "time_zone": "Sydney",
      "country_code": "AU",
      "country": "Australia",
      "memberships_count": 2,
      "lat": null,
      "lng": null,
      "avatar_url": "https://res-1.cloudinary.com/image/avatar-1.jpg",
      "calendar_url": "webcal://hub.adventistchurch.com/contacts/1/calendars/kaQaKqcMHX63ScxrA9gJhk91/feed.ics"
    },
    "links": {
      "self": "/api/account"
    }
  }
}
```

`PATCH /api/account`

Update the users account.