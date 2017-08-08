# Contact Assignments

Manage who is assigned to a contact.

These endpoints are restricted to contacts with the role of leader or owner.

## Assignable

```shell
curl https://adhubapi.adventistchurch.com/api/contacts/27/assignments/assignable
-H "Authorization: Bearer team_token"
-H "Content-type: application/json"
-H "Accept: application/vnd.adhub.v1+json"
```
```json
{
  "data": [
    {
      "id": "1",
      "type": "contacts",
      "attributes":{
        "name": "James Green",
        "avatar_url": "https://res-1.cloudinary.com/amn-dev/image/upload/w_200,h_200/l_text:Arial_50_bold:SS,co_white/avatar_green.jpg",
        "commonality": [],
        "score":0
      }
    },
    {
      "id": "4",
      "type": "contacts",
      "attributes":{
        "name": "Sally Rogers",
        "avatar_url": "https://res-1.cloudinary.com/amn-dev/image/upload/w_200,h_200/l_text:Arial_50_bold:SS,co_white/avatar_green.jpg",
        "commonality": ["0km away"],
        "score": 1
      }
    }
  ]
}

```

`GET /api/contacts/{contact-id}/assignments/assignable`

A list of team contacts who can be assigned to a contact.

A higher score indicates a better match based on commonalities between the two contacts.


## Batch Manage

```shell
curl -X POST https://adhubapi.adventistchurch.com/api/contacts/27/assignments/batch
-H "Authorization: Bearer team_token"
-H "Content-type: application/json"
-H "Accept: application/vnd.adhub.v1+json"
-d '{"assignor_ids": [3,14]}'
```
```json
{
  "data": {
      "id": "27",
      "type": "contacts",
      "attributes": {
          "first_name": "Blue",
          "last_name": "Haven",
          "name": "Blue Haven",
          "email": "bluehave@adventistmedia.org.au",
          "status": "non_member",
          "mobile_number": null,
          "other_number": "+61298472252",
          "mobile_number_local": null,
          "other_number_local": "(02) 9847 2252",
          "created_at": "2017-06-19T09:51:16.107+10:00",
          "updated_at": "2017-07-19T14:21:59.202+10:00",
          "created_by_id": "1",
          "lat": -33.7309925,
          "lng": 151.1042444,
          "language_id": "1",
          "last_visit": "2017-06-19",
          "available": true,
          "available_until": null,
          "date_of_birth": "2017-05-30",
          "gender": "gender_unknown",
          "religion_id": "24",
          "campaign_id": null,
          "approach_id": null,
          "brand_id": null,
          "avatar_url": "https://res-4.cloudinary.com/amn-dev/image/upload/c_fill,f_auto,h_200,w_200/avatar-27.png",
          "assignor_ids": ["3", "14"]
      },
      "relationships": {
          "home_address": {
              "data": {
                  "id": "6",
                  "type": "addresses"
              }
          },
          "mailing_address": {
              "data": null
          }
        },
      "links": {
          "self": "/api/contacts/27"
      }
  }
}
```

`POST /api/contacts/{contact-id}/assignments/batch`

Batch set the zero or more contacts that have the status of member to be assigned to have access to the contact.