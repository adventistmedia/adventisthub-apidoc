# Religion

Religions for selection

## Fields

Field | Description | Notes
----- | ----------- | -----
name<br> *string* | Name of religion | Read-only
parent_id<br>*integer* | Parent religion object | Read-only
created_at<br> *datetime* | When the religion was created | Read-only
updated_at<br> *datetime* | When the religion was last updated | Read-only

## List Religions
```shell
curl http://api.adventisthub.com/api/religions
-H "Authorization: Bearer token"
-H "Accept: application/vnd.adventisthub.v1"
```
```json
{
  "data": [
    {
      "id": "2",
      "type": "religions",
      "attributes": {
        "name": "Christianity",
        "parent_id": null,
        "created_at": "2016-10-24T08:26:36.690+11:00",
        "updated_at": "2016-10-24T08:26:36.690+11:00"
      }
    },
    {
      "id": "1",
      "type": "religions",
      "attributes": {
        "name": "Seventh-day Adventist Church",
        "parent_id": 2,
        "created_at": "2016-10-24T08:25:43.025+11:00",
        "updated_at": "2016-10-24T08:26:43.682+11:00"
      }
    }
  ]
}
```

`GET /api/religions`

An array of all religions.