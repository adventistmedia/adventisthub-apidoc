# Contact

Represents a contact.

## Fields

Field | Description | Notes
--------- | ------- | -------
first_name<br> *string* | First name | Required
last_name<br> *string* | Last name | Required
name<br> *string* | First and last name | Read-only
email<br> *string* | Email address
status<br> *enum* {non_member, member, deceased, deleted} | Status of contact. Defaults to non_member
mobile_number<br> *string* | Mobile phone number in E. 164 format
other_number<br> *string* | Any phone number in E. 164 format
mobile_number_local<br> *string* | Mobile phone number in localized format | Read-only
other_number_local<br> *string* | Any phone number in localized format | Read-only
created_at<br>*datetime* | When the contact was created | Read-only
updated_at<br>*datetime* | When the contact was last updated | Read-only
lat<br> *float* | Latitude of home address | Read-only
lng<br> *float* | Longitude of home address | Read-only
language_id<br>*integer* | ID of the language (primarily spoken) by the contact
last_visit<br>*date* | Date the contact last had a completed activity of type visit, call or
available<br> *boolean* | the availability of the contact to accept requests and more
unavailable_until<br> *date* | if available is false, a date may be set to indicate when the contact will become available again
date_of_birth<br>*date* | Date of birth
gender<br> *enum* {gender_unknown, female, male} | Gender. Defaults to gender_unknown
religion_id<br>*integer* | ID of the religion the contact belongs too bible_study | Read-only
campaign_id<br>*integer* | ID of the campaign the contact belongs too
approach_id<br>*integer* | ID of the approach the contact belongs too
brand_id<br>*integer* | ID of the brand the contact belongs too
avatar_url<br>*string* | Avatar image URL for contact | Read-only

The following nested attributes can optionally be set on a contact. See contact addresses for fields.

Field | Description | Notes
--------- | ------- | -------
home_address_attributes<br>*JSON object* | Home address attributes. Set to nil to delete home_address
mailing_address_attributes<br>*JSON object* | Mailing address attributes. Set to nil to delete mailing_address

## List Contacts
```shell
curl https://adhubapi.adventistchurch.com/api/contacts
-H "Authorization: Bearer team_token"
-H "Accept: application/vnd.adhub.v1+json"
```

```json
{
  "data": [
    {
      "id": "33",
      "type": "contacts",
      "attributes": {
        "first_name": "Sally",
        "last_name": "Page",
        "name": "Sally Page",
        "email": "sallypage@gmail.com",
        "status": "active",
        "mobile_number": "+61450123456",
        "other_number": "+61298471122",
        "mobile_number_local": "0450 123 456",
        "other_number_local": "(02) 9847 1122",
        "created_at": "2017-06-14T16:53:52.738+10:00",
        "updated_at": "2017-07-19T14:21:59.189+10:00",
        "created_by_id": "1",
        "lat": null,
        "lng": null,
        "language_id": "1",
        "last_visit": null,
        "available": true,
        "available_until": null,
        "date_of_birth": "1950-02-10",
        "gender": "female",
        "religion_id": null,
        "campaign_id": null,
        "approach_id": null,
        "brand_id": null,
        "avatar_url": "https://res-1.cloudinary.com/image/avatar-33.jpg"
      },
      "relationships": {
        "home_address": {
          "data": {
            "id": "13",
            "type": "addresses"
          }
        },
        "mailing_address": {
          "data": null
        }
      },
      "links": {
        "self": "/api/contacts/33"
      }
    },
  ],
  "included": [
    {
      "id": "13",
      "type": "addresses",
      "attributes": {
          "attention": null,
          "address1": "120 Fox Valley Rd",
          "address2": "",
          "address3": "",
          "city": "Wahroonga",
          "region": "NSW",
          "postcode": "2076",
          "country_code": "AU",
          "country": "Australia",
          "full_address": "120 Fox Valley Rd, Wahroonga NSW 2076, Australia",
          "status": "active",
          "lat": -33.731041,
          "lng": 151.1052291,
          "location": "home",
          "created_at": "2017-06-07T12:45:35.187+10:00",
          "updated_at": "2017-06-07T12:45:35.187+10:00"
      }
    },
  ]
}
```
`GET /api/contacts`

An array of contacts the user has assigned to them.

## Show Contact

```shell
curl https://adhubapi.adventistchurch.com/api/contacts/38
-H "Authorization: Bearer team_token"
-H "Accept: application/vnd.adhub.v1+json"
```
```json
{
    "data": {
        "id": "38",
        "type": "contacts",
        "attributes": {
            "first_name": "Roger",
            "last_name": "Fox",
            "name": "Roger Fox",
            "email": null,
            "status": "non_member",
            "mobile_number": "+61450123456",
            "other_number": "+61298711234",
            "mobile_number_local": "0450 123 456",
            "other_number_local": "(02) 9871 1234",
            "created_at": "2017-07-20T10:10:01.491+10:00",
            "updated_at": "2017-07-20T10:10:01.688+10:00",
            "created_by_id": "1",
            "lat": -33.7330045,
            "lng": 151.1010431,
            "language_id": "1",
            "last_visit": null,
            "available": true,
            "available_until": null,
            "date_of_birth": null,
            "gender": "male",
            "religion_id": null,
            "campaign_id": null,
            "approach_id": null,
            "brand_id": null,
            "avatar_url": "https://res-1.cloudinary.com/amn-dev/image/upload/w_200,h_200/l_text:Arial_50_bold:RF,co_white/avatar_blue.jpg"
        },
        "relationships": {
            "home_address": {
                "data": {
                    "id": "19",
                    "type": "addresses"
                }
            }
        },
        "links": {
            "self": "/api/contacts/38"
        }
    },
    "included": [
        {
            "id": "19",
            "type": "addresses",
            "attributes": {
                "attention": null,
                "address1": "150 Fox Valley Road",
                "address2": null,
                "address3": null,
                "city": "Wahroonga",
                "region": "NSW",
                "postcode": "2076",
                "country_code": "AU",
                "country": "Australia",
                "full_address": "150 Fox Valley Road, Wahroonga NSW 2076, Australia",
                "status": "active",
                "lat": -33.7330045,
                "lng": 151.1010431,
                "location": "home",
                "created_at": "2017-07-20T10:10:01.508+10:00",
                "updated_at": "2017-07-20T10:10:01.508+10:00"
            }
        }
    ]
}
```

`GET /api/contacts/{contact-id}`

Show a contact.

## Create Contact
```shell
curl -X POST https://adhubapi.adventistchurch.com/api/contacts
-H "Authorization: Bearer team_token"
-H "Content-type: application/json"
-H "Accept: application/vnd.adhub.v1+json"
-d '{"contact": {
"first_name": "Roger",
"last_name": "Fox",
"gender":"male",
"mobile_number": "0450123456",
"other_number": "0298711234",
"home_address_attributes": {"address1": "150 Fox Valley Road","city": "Wahroonga","region": "NSW","postcode": 2076,"country_code": "AU","lat": "-33.7330045,"lng": 151.1010431"},
"mailing_address_attributes": {"address1": "PO BOX 3","city": "Wahroonga","postcode": 2076,"region": "NSW","country_code": "AU"}
}}'
```
```json
{
    "data": {
        "id": "38",
        "type": "contacts",
        "attributes": {
            "first_name": "Roger",
            "last_name": "Fox",
            "name": "Roger Fox",
            "email": null,
            "status": "non_member",
            "mobile_number": "+61450123456",
            "other_number": "+61298711234",
            "mobile_number_local": "0450 123 456",
            "other_number_local": "(02) 9871 1234",
            "created_at": "2017-07-20T10:10:01.491+10:00",
            "updated_at": "2017-07-20T10:10:01.688+10:00",
            "created_by_id": "1",
            "lat": null,
            "lng": null,
            "language_id": "1",
            "last_visit": null,
            "available": true,
            "available_until": null,
            "date_of_birth": null,
            "gender": "male",
            "religion_id": null,
            "campaign_id": null,
            "approach_id": null,
            "brand_id": null,
            "avatar_url": "https://res-1.cloudinary.com/amn-dev/image/upload/w_200,h_200/l_text:Arial_50_bold:RF,co_white/avatar_blue.jpg"
        },
        "relationships": {
            "home_address": {
                "data": {
                    "id": "19",
                    "type": "addresses"
                }
            },
            "mailing_address": {
                "data": {
                    "id": "20",
                    "type": "addresses"
                }
            }
        },
        "links": {
            "self": "/api/contacts/38"
        }
    },
    "included": [
      {
        "id": "19",
        "type": "addresses",
        "attributes": {
            "attention": null,
            "address1": "150 Fox Valley Road",
            "address2": null,
            "address3": null,
            "city": "Wahroonga",
            "region": "NSW",
            "postcode": "2076",
            "country_code": "AU",
            "country": "Australia",
            "full_address": "150 Fox Valley Road, Wahroonga NSW 2076, Australia",
            "status": "active",
            "lat": -33.7330045,
            "lng": 151.1010431,
            "location": "home",
            "created_at": "2017-07-20T10:10:01.508+10:00",
            "updated_at": "2017-07-20T10:10:01.508+10:00"
          }
        },
        {
            "id": "20",
            "type": "addresses",
            "attributes": {
                "attention": null,
                "address1": "PO BOX 3",
                "address2": null,
                "address3": null,
                "city": "Wahroonga",
                "region": "NSW",
                "postcode": "2076",
                "country_code": "AU",
                "country": "Australia",
                "full_address": "PO BOX 3, Wahroonga NSW 2076, Australia",
                "status": "active",
                "lat": -33.7183,
                "lng": 151.1187,
                "location": "mailing",
                "created_at": "2017-07-20T10:10:01.535+10:00",
                "updated_at": "2017-07-20T10:10:01.535+10:00"
            }
        }
    ]
}
```

`POST /api/contacts`

## Update Contact
```shell
curl -X PATCH https://adhubapi.adventistchurch.com/api/contacts/46
-H "Authorization: Bearer team_token"
-H "Content-type: application/json"
-H "Accept: application/vnd.adhub.v1+json"
-d '{"contact":{
"first_name": "James",
"home_address_attributes": {"address1": "12 Fox Valley Road", "city": "Wahroonga", "region": "NSW", "postcode": 2076, "country_code":"AU"},
"mailing_address_attributes": null
}}'
```
```json
{
    "data": {
        "id": "40",
        "type": "contacts",
        "attributes": {
            "first_name": "James",
            "last_name": "Fox",
            "name": "James Fox",
            "email": null,
            "status": "non_member",
            "mobile_number": "+61450123456",
            "other_number": "+61298711234",
            "mobile_number_local": "0450 123 456",
            "other_number_local": "(02) 9871 1234",
            "created_at": "2017-07-20T11:00:00.157+10:00",
            "updated_at": "2017-07-20T11:01:03.566+10:00",
            "created_by_id": "1",
            "lat": -33.7278971,
            "lng": 151.1184259,
            "language_id": "1",
            "last_visit": null,
            "available": true,
            "available_until": null,
            "date_of_birth": null,
            "gender": "male",
            "religion_id": null,
            "campaign_id": null,
            "approach_id": null,
            "brand_id": null,
            "avatar_url": "https://res-1.cloudinary.com/amn-dev/image/upload/w_200,h_200/l_text:Arial_50_bold:JF,co_white/avatar_blue.jpg"
        },
        "relationships": {
            "home_address": {
                "data": {
                    "id": "27",
                    "type": "addresses"
                }
            },
            "mailing_address": {
                "data": null
            }
        },
        "links": {
            "self": "/api/contacts/40"
        }
    },
    "included": [
        {
            "id": "27",
            "type": "addresses",
            "attributes": {
                "attention": null,
                "address1": "12 Fox Valley Road",
                "address2": null,
                "address3": null,
                "city": "Wahroonga",
                "region": "NSW",
                "postcode": "2076",
                "country_code": "AU",
                "country": "Australia",
                "full_address": "12 Fox Valley Road, Wahroonga NSW 2076, Australia",
                "status": "active",
                "lat": -33.7278971,
                "lng": 151.1184259,
                "location": "home",
                "created_at": "2017-07-20T11:00:00.173+10:00",
                "updated_at": "2017-07-20T11:01:03.556+10:00"
            }
        }
    ]
}
```

`PATCH /api/contacts/{contact-id}`

In this example we updating the contacts name, deleting the mailing address and editing the home addresses address1 attribute.