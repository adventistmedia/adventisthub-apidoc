# Category

The categories available for selection to a user.

## Fields

Field | Description | Notes
----- | ----------- | -----
name<br> *string* | Name of category | Read-only
created_at<br> *datetime* | When the category was created | Read-only
updated_at<br> *datetime* | When the category was last updated | Read-only

## List Categories
```shell
curl http://api.adventisthub.com/api/categories
-H "Authorization: Bearer token"
-H "Accept: application/vnd.adventisthub.v1"
```
```json
{
  "data": [
    {
      "id": "10",
      "type": "categories",
      "attributes": {
        "name": "Aid & Human Rights",
        "created_at": "2016-11-22T08:23:01.911+11:00",
        "updated_at": "2016-11-22T08:23:01.911+11:00"
      }
    },
    {
      "id": "9",
      "type": "categories",
      "attributes": {
        "name": "Arts & Entertainment",
        "created_at": "2016-11-22T08:23:00.310+11:00",
        "updated_at": "2016-11-22T08:23:00.310+11:00"
      }
    }
  ]
}
```

`GET /api/categories`

An array of all categories.