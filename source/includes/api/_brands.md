# Brand

The brands available for selection to a user.

## Fields

Field | Description | Notes
----- | ----------- | -----
name<br> *string* | Name of brand | Read-only
created_at<br> *datetime* | When the brand was created | Read-only
updated_at<br> *datetime* | When the brand was last updated | Read-only

## List Brands
```shell
curl https://adhubapi.adventistchurch.com/api/brands
-H "Authorization: Bearer team_token"
-H "Accept: application/vnd.adhub.v1+json"
```
```json
{
  "data": [
    {
      "id": "1",
      "type": "brands",
      "attributes": {
        "name": "HopeChannel",
        "created_at": "2016-10-24T09:10:49.298+11:00",
        "updated_at": "2016-10-24T09:11:03.291+11:00"
      }
    },
    {
      "id": "2",
      "type": "brands",
      "attributes": {
        "name": "Discovery",
        "created_at": "2016-10-25T12:15:38.925+11:00",
        "updated_at": "2016-10-25T12:15:38.925+11:00"
      }
    }
  ]
}
```

`GET /api/brands`

An array of all brands.