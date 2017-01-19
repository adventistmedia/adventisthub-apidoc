# Approach

The approaches available for selection to a user.

## Fields

Field | Description | Notes
----- | ----------- | -----
name<br> *string* | Name of approach | Read-only
created_at<br> *datetime* | When the approach was created | Read-only
updated_at<br> *datetime* | When the approach was last updated | Read-only

## List Approaches
```shell
curl https://hubapi.adventistchurch.com/api/approaches
-H "Authorization: Bearer token"
-H "Accept: application/vnd.adventisthub.v1+json"
```
```json
{
  "data": [
    {
      "id": "2",
      "type": "approaches",
      "attributes": {
        "name": "Letterbox Card",
        "created_at": "2016-10-24T09:08:13.127+11:00",
        "updated_at": "2016-10-24T09:08:13.127+11:00"
      }
    }
  ]
}
```

`GET /api/approaches`

An array of all approaches.